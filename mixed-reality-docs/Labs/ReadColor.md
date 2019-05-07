# <a name="reading-rgb-data"></a>Leer datos RGB

**Contenido**  
[Configurar el dispositivo](#Configuring-the-Device)  
[Obtención de un marco de Color](#Getting-a-Color-Frame)  
[Limpiar](#Cleaning-Up)  
[Código fuente completo](#Full-Source)  

**Estas son las funciones que vamos a usar:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a>Configurar el dispositivo

Después de [abrir un dispositivo k4a](), necesitamos configurar las cámaras para tomar datos de color. Hay muchas opciones aquí también, por lo que iremos a través de ellos. Este es un ejemplo rápido de su aspecto en iniciarse una cámara de color básico realmente.

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

El `color_format` nos permite decir cómo queremos que nuestra información de color almacenada en el búfer de imagen. `K4A_IMAGE_FORMAT_COLOR_BGRA32` sería 32 bits por píxel, que se almacena como 8 bits para cada uno de alfa, rojo, verde y azul. Usamos este formato en los ejemplos debido a su conveniencia, pero si desea ser concious de uso de memoria, otros formatos pueden ser opciones superiores!

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|Color datos estarán en [formato JPEG de movimiento](https://en.wikipedia.org/wiki/Motion_JPEG)|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|[YUV](https://en.wikipedia.org/wiki/YUV) color espacio 4:2:0 formato, NV12, solo está disponible en la resolución de 720 p.|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|[YUV](https://en.wikipedia.org/wiki/YUV) color espacio 4:2:2 formato YUY2, solo está disponible en la resolución de 720 p.|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|Ordenan datos de color sin formato, 32 bits por píxel, como azul, verde, rojo, alfa|

Al escribir su propia conversión YUV puede ser bastante fácil, una biblioteca rápida y sólida para la conversión YUV puede encontrarse en [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).

El `color_resolution` también tiene un par de opciones.

|`color_resolution`|Resolución|Aspecto|campo de visión| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | 1280 x 720  | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1080P` | 1920 x 1080 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1440P` | 2560 x 1440 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_2160P` | 3840 x 2160 | 16:9 | 90x59
|`K4A_COLOR_RESOLUTION_1536P` | 2048 x 1536 | 4:3  | 90x74.3 
|`K4A_COLOR_RESOLUTION_3072P` | 4096 x 3072 | 4:3  | 90x74.3 | Velocidad de fotogramas máximo 15.

Y por supuesto, la `camera_fps` también.

|camera_fps||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a>Obtención de un marco de Color

Obtener datos para un marco de color y un marco de profundidad es un proceso muy similar. En primer lugar, obtenemos una captura desde el dispositivo, a continuación, se extraiga la imagen de color de él y, a continuación, se extraen los datos sin procesar fuera de esa imagen.

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the color data and information from the current capture
k4a_image_t colors      = k4a_capture_get_color_image(capture);
uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
int width  = k4a_image_get_width_pixels (colors);
int height = k4a_image_get_height_pixels(colors);

// Write this capture to file
tga_write("out.tga", width, height, colorDataBGRA, 4, 3);
```

Los datos se almacenan ahora en `colorDataBRGA` depende en el formato que se indica en la configuración. Puesto que se le pedirán `K4A_IMAGE_FORMAT_COLOR_BGRA32`, tenemos una matriz completa de los valores de color de 32 bits almacenados en BGRA order!

¡En este caso, los archivos .tga almacenan los colores de BGR ya! Y dado que nuestra función guardando puede omitir el canal alfa con estos argumentos, simplemente podemos pasar los datos de la imagen tal cual.

## <a name="cleaning-up"></a>Limpiar

Y como siempre, recuerde que liberar los recursos cuando haya terminado con ellos.
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a>Código fuente completo

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main() {
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure a stream of 1280x720 BRGA data at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the color data and information from the current capture
    k4a_image_t colors      = k4a_capture_get_color_image(capture);
    uint8_t    *colors_bgra = k4a_image_get_buffer(colors);
    int width  = k4a_image_get_width_pixels (colors);
    int height = k4a_image_get_height_pixels(colors);
    printf("Captured RGB image, %dx%d\n", width, height);

    // Write this capture to file
    tga_write("out.tga", width, height, colors_bgra, 4, 3);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(colors);
    k4a_capture_release(capture);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width % 256, (uint8_t)(width / 256), height % 256, (uint8_t)(height / 256), file_channels * 8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a>La práctica siguiente - [mezclar el Color y los datos de profundidad](MixDepthAndRGB.md)