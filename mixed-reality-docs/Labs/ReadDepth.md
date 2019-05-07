# <a name="reading-depth-data"></a>Leer datos de profundidad

¿Necesita leer datos de profundidad desde el dispositivo? ¡Es fácil!

**Contenido**  
[Configurar el dispositivo](#Configuring-the-Device)  
[Profundidad de acceso a datos](#Acessing-Depth-Data)  
[Limpiar](#Cleaning-Up)  
[Código fuente completo](#Full-Source)  

**Estas son las funciones que vamos a usar:**  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_depth_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-depth-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release)  

## <a name="configuring-the-device"></a>Configurar el dispositivo

Después de [abriendo una interfaz]() al dispositivo DK Kinect de Azure, debe configurar la cámara para capturar datos de profundidad. Hay un único elemento realmente necesita conocer al configurar la profundidad, y que la `depth_mode`!

```C
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.depth_mode = K4A_DEPTH_MODE_NFOV_UNBINNED;

k4a_device_start_cameras(device, &config);
```

Aquí el `depth_mode` tiene dos opciones. Dependiendo del contexto de nuestra aplicación, podemos solicitamos nuestros datos de profundidad en formatos diferentes.

¿Ejecuta algoritmos de tiempo limitada en los datos de profundidad? Es posible elegir un modo 2X2BINNED por lo que hay menos datos para operar en! ¿Preocupa más por lo que es el momento out directamente anticipada, en lugar de lo que está cerca y en la periferia? ¡Usar un campo de visión estrecha con los modos de NFOV!
| [`depth_mode`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-depth-mode-t) | description |
|------------|-------------|
|`K4A_DEPTH_MODE_WFOV_UNBINNED`|Vista gran angular (120 x 120), profundidad superficial (0.25-2.21 m), datos alta resolución (1024 x 1024). Tiene una velocidad de fotogramas máxima de 15.|
|`K4A_DEPTH_MODE_WFOV_2X2BINNED`|Vista gran angular (120 x 120), profundidad superficial (0.25-2,88 m), datos baja resolución (512 x 512).|
|`K4A_DEPTH_MODE_NFOV_UNBINNED`|Vista estrecha ángulo (75 x 65), profundidad lejano (0,5-3.86 m), resolución (640 x 576) de datos alta.|
|`K4A_DEPTH_MODE_NFOV_2X2BINNED`|Vista estrecha ángulo (75 x 65), profundidad lejano (0,5-5,46 m), datos baja resolución (320 x 288).|
|`K4A_DEPTH_MODE_PASSIVE_IR`|Materias primas de la cámara de infrarrojos (1024 x 1024)|
||Se proporcionará profundidad fuera del intervalo indicado en función de reflexión de objeto.|

## <a name="acessing-depth-data"></a>Profundidad de acceso a datos

![](img/Depth.png)

Cuando se captura un marco desde el dispositivo, podemos usar `k4a_capture_get_depth_image` y `k4a_image_get_buffer` para obtener los datos sin procesar de profundidad.

```C
// Capture a frame
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Get the depth data and information from the current capture
k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
int32_t width  = k4a_image_get_width_pixels (depth_image);
int32_t height = k4a_image_get_height_pixels(depth_image);
```

Se proporciona información detallada como una matriz de enteros de 16 bits sin signo, que representan milímetros desde la cámara. La matriz contendrá un cero si el valor de profundidad no está presente para que un píxel determinado.

En este ejemplo, solo se podrá convertir los datos de profundidad en una imagen de escala de grises y guardarlo en el archivo!

```C
// Write this depth capture to an image file

// Allocate memory for an 8-bit grayscale image
uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

// Convert each depth value to a shade of gray!
for (int32_t i = 0; i < width*height; i++)
{
    // Make a gray from the depth, white up close, black at 3 meters in the distance
    float depth_gray = 1-(depth_buffer[i] / 3000.0f);
    // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
    depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

    file_color[i] = static_cast<uint8_t>(depth_gray * 255);
}
tga_write("outDepth.tga", width, height, file_color, 1, 3);
free(file_color);
```

## <a name="cleaning-up"></a>Limpiar

¡No olvide cerrar y liberar todo lo que ha asignado o capturó! Recuerde que las capturas de marco se deberían liberar cuando haya terminado con ellos y antes de tomar otro marco.

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(depth_image);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a>Código fuente completo

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 1024x1024 wide FOV at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_5;
    config.depth_mode = K4A_DEPTH_MODE_WFOV_UNBINNED;

    k4a_device_start_cameras(device, &config);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

    // Get the depth data and information from the current capture
    k4a_image_t depth_image  = k4a_capture_get_depth_image(capture);
    uint16_t   *depth_buffer = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_image));
    int32_t width  = k4a_image_get_width_pixels (depth_image);
    int32_t height = k4a_image_get_height_pixels(depth_image);
    printf("Captured depth image, %dx%d\n", width, height);

    // Write this depth capture to an image file

    // Allocate memory for an 8-bit grayscale image
    uint8_t *file_color = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * width*height));

    // Convert each depth value to a shade of gray!
    for (int32_t i = 0; i < width*height; i++)
    {
        // Make a gray from the depth, white up close, black at 3 meters in the distance
        float depth_gray = 1-(depth_buffer[i] / 3000.0f);
        // Cap at 1.0, any higher and our uint8_t will overflow and wrap around
        depth_gray = depth_gray > 1.0f ? 1.0f : depth_gray;

        file_color[i] = static_cast<uint8_t>(depth_gray * 255);
    }
    tga_write("outDepth.tga", width, height, file_color, 1, 3);
    free(file_color);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(depth_image);
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

## <a name="next-lab---reading-rgb-datareadcolormd"></a>La práctica siguiente - [leer los datos RGB](ReadColor.md)