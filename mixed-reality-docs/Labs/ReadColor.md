# <a name="reading-rgb-data"></a><span data-ttu-id="c8544-101">Leer datos RGB</span><span class="sxs-lookup"><span data-stu-id="c8544-101">Reading RGB Data</span></span>

<span data-ttu-id="c8544-102">**Contenido**</span><span class="sxs-lookup"><span data-stu-id="c8544-102">**Contents**</span></span>  
[<span data-ttu-id="c8544-103">Configurar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="c8544-103">Configuring the Device</span></span>](#Configuring-the-Device)  
[<span data-ttu-id="c8544-104">Obtención de un marco de Color</span><span class="sxs-lookup"><span data-stu-id="c8544-104">Getting a Color Frame</span></span>](#Getting-a-Color-Frame)  
[<span data-ttu-id="c8544-105">Limpiar</span><span class="sxs-lookup"><span data-stu-id="c8544-105">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="c8544-106">Código fuente completo</span><span class="sxs-lookup"><span data-stu-id="c8544-106">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="c8544-107">**Estas son las funciones que vamos a usar:**</span><span class="sxs-lookup"><span data-stu-id="c8544-107">**Here are the functions we'll use:**</span></span>  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_capture_get_color_image()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-capture-get-color-image)  
[`k4a_image_get_buffer()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-buffer)  
[`k4a_image_get_width_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-width-pixels)  
[`k4a_image_get_height_pixels()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-get-height-pixels)  
[`k4a_image_release()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-release) 

## <a name="configuring-the-device"></a><span data-ttu-id="c8544-108">Configurar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="c8544-108">Configuring the Device</span></span>

<span data-ttu-id="c8544-109">Después de [abrir un dispositivo k4a](), necesitamos configurar las cámaras para tomar datos de color.</span><span class="sxs-lookup"><span data-stu-id="c8544-109">After [opening a k4a device](), we'll need to set up the cameras to grab color data!</span></span> <span data-ttu-id="c8544-110">Hay muchas opciones aquí también, por lo que iremos a través de ellos.</span><span class="sxs-lookup"><span data-stu-id="c8544-110">There's a lot of options here as well, so we'll go through them.</span></span> <span data-ttu-id="c8544-111">Este es un ejemplo rápido de su aspecto en iniciarse una cámara de color básico realmente.</span><span class="sxs-lookup"><span data-stu-id="c8544-111">Here's a quick example of what it looks like to start up a really basic color camera.</span></span>

```C
// Configure a stream of 1280x720 BGRA color data at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="c8544-112">El `color_format` nos permite decir cómo queremos que nuestra información de color almacenada en el búfer de imagen.</span><span class="sxs-lookup"><span data-stu-id="c8544-112">The `color_format` allows us to say how we want our color information stored in the image buffer!</span></span> <span data-ttu-id="c8544-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` sería 32 bits por píxel, que se almacena como 8 bits para cada uno de alfa, rojo, verde y azul.</span><span class="sxs-lookup"><span data-stu-id="c8544-113">`K4A_IMAGE_FORMAT_COLOR_BGRA32` would be 32 bits per pixel, stored as 8 bits each for Blue, Green, Red, and Alpha.</span></span> <span data-ttu-id="c8544-114">Usamos este formato en los ejemplos debido a su conveniencia, pero si desea ser concious de uso de memoria, otros formatos pueden ser opciones superiores!</span><span class="sxs-lookup"><span data-stu-id="c8544-114">We use this format in the examples due to its convenience, but if you want to be concious of memory usage, other formats may be superior choices!</span></span>

|`color_format`||
|--------------|-----------|
|`K4A_IMAGE_FORMAT_COLOR_MJPG`|<span data-ttu-id="c8544-115">Color datos estarán en [formato JPEG de movimiento](https://en.wikipedia.org/wiki/Motion_JPEG)</span><span class="sxs-lookup"><span data-stu-id="c8544-115">Color data will be in [Motion JPEG format](https://en.wikipedia.org/wiki/Motion_JPEG)</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_NV12`|<span data-ttu-id="c8544-116">[YUV](https://en.wikipedia.org/wiki/YUV) color espacio 4:2:0 formato, NV12, solo está disponible en la resolución de 720 p.</span><span class="sxs-lookup"><span data-stu-id="c8544-116">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:0 format, NV12, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_YUY2`|<span data-ttu-id="c8544-117">[YUV](https://en.wikipedia.org/wiki/YUV) color espacio 4:2:2 formato YUY2, solo está disponible en la resolución de 720 p.</span><span class="sxs-lookup"><span data-stu-id="c8544-117">[YUV](https://en.wikipedia.org/wiki/YUV) color space 4:2:2 format, YUY2, only available at 720p resolution.</span></span>|
|`K4A_IMAGE_FORMAT_COLOR_BGRA32`|<span data-ttu-id="c8544-118">Ordenan datos de color sin formato, 32 bits por píxel, como azul, verde, rojo, alfa</span><span class="sxs-lookup"><span data-stu-id="c8544-118">Raw color data, 32 bits per pixel, ordered as Blue, Green, Red, Alpha</span></span>|

<span data-ttu-id="c8544-119">Al escribir su propia conversión YUV puede ser bastante fácil, una biblioteca rápida y sólida para la conversión YUV puede encontrarse en [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span><span class="sxs-lookup"><span data-stu-id="c8544-119">While writing your own YUV conversion may be easy enough, a fast, robust library for YUV conversion can be found at [libyuv](https://chromium.googlesource.com/libyuv/libyuv/).</span></span>

<span data-ttu-id="c8544-120">El `color_resolution` también tiene un par de opciones.</span><span class="sxs-lookup"><span data-stu-id="c8544-120">The `color_resolution` also has a couple of options!</span></span>

|`color_resolution`|<span data-ttu-id="c8544-121">Resolución</span><span class="sxs-lookup"><span data-stu-id="c8544-121">resolution</span></span>|<span data-ttu-id="c8544-122">Aspecto</span><span class="sxs-lookup"><span data-stu-id="c8544-122">aspect</span></span>|<span data-ttu-id="c8544-123">campo de visión</span><span class="sxs-lookup"><span data-stu-id="c8544-123">field of view</span></span>| |
|------------------|----------|------|-------------|-|
|`K4A_COLOR_RESOLUTION_720P`  | <span data-ttu-id="c8544-124">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="c8544-124">1280 x 720</span></span>  | <span data-ttu-id="c8544-125">16:9</span><span class="sxs-lookup"><span data-stu-id="c8544-125">16:9</span></span> | <span data-ttu-id="c8544-126">90x59</span><span class="sxs-lookup"><span data-stu-id="c8544-126">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1080P` | <span data-ttu-id="c8544-127">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="c8544-127">1920 x 1080</span></span> | <span data-ttu-id="c8544-128">16:9</span><span class="sxs-lookup"><span data-stu-id="c8544-128">16:9</span></span> | <span data-ttu-id="c8544-129">90x59</span><span class="sxs-lookup"><span data-stu-id="c8544-129">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1440P` | <span data-ttu-id="c8544-130">2560 x 1440</span><span class="sxs-lookup"><span data-stu-id="c8544-130">2560 x 1440</span></span> | <span data-ttu-id="c8544-131">16:9</span><span class="sxs-lookup"><span data-stu-id="c8544-131">16:9</span></span> | <span data-ttu-id="c8544-132">90x59</span><span class="sxs-lookup"><span data-stu-id="c8544-132">90x59</span></span>
|`K4A_COLOR_RESOLUTION_2160P` | <span data-ttu-id="c8544-133">3840 x 2160</span><span class="sxs-lookup"><span data-stu-id="c8544-133">3840 x 2160</span></span> | <span data-ttu-id="c8544-134">16:9</span><span class="sxs-lookup"><span data-stu-id="c8544-134">16:9</span></span> | <span data-ttu-id="c8544-135">90x59</span><span class="sxs-lookup"><span data-stu-id="c8544-135">90x59</span></span>
|`K4A_COLOR_RESOLUTION_1536P` | <span data-ttu-id="c8544-136">2048 x 1536</span><span class="sxs-lookup"><span data-stu-id="c8544-136">2048 x 1536</span></span> | <span data-ttu-id="c8544-137">4:3</span><span class="sxs-lookup"><span data-stu-id="c8544-137">4:3</span></span>  | <span data-ttu-id="c8544-138">90x74.3</span><span class="sxs-lookup"><span data-stu-id="c8544-138">90x74.3</span></span> 
|`K4A_COLOR_RESOLUTION_3072P` | <span data-ttu-id="c8544-139">4096 x 3072</span><span class="sxs-lookup"><span data-stu-id="c8544-139">4096 x 3072</span></span> | <span data-ttu-id="c8544-140">4:3</span><span class="sxs-lookup"><span data-stu-id="c8544-140">4:3</span></span>  | <span data-ttu-id="c8544-141">90x74.3</span><span class="sxs-lookup"><span data-stu-id="c8544-141">90x74.3</span></span> | <span data-ttu-id="c8544-142">Velocidad de fotogramas máximo 15.</span><span class="sxs-lookup"><span data-stu-id="c8544-142">Max framerate 15.</span></span>

<span data-ttu-id="c8544-143">Y por supuesto, la `camera_fps` también.</span><span class="sxs-lookup"><span data-stu-id="c8544-143">And of course, the `camera_fps` as well.</span></span>

|<span data-ttu-id="c8544-144">camera_fps</span><span class="sxs-lookup"><span data-stu-id="c8544-144">camera_fps</span></span>||
|--|--|
|`K4A_FRAMES_PER_SECOND_5`
|`K4A_FRAMES_PER_SECOND_15`
|`K4A_FRAMES_PER_SECOND_30`

## <a name="getting-a-color-frame"></a><span data-ttu-id="c8544-145">Obtención de un marco de Color</span><span class="sxs-lookup"><span data-stu-id="c8544-145">Getting a Color Frame</span></span>

<span data-ttu-id="c8544-146">Obtener datos para un marco de color y un marco de profundidad es un proceso muy similar.</span><span class="sxs-lookup"><span data-stu-id="c8544-146">Getting data for a color frame and a depth frame is a very similar process!</span></span> <span data-ttu-id="c8544-147">En primer lugar, obtenemos una captura desde el dispositivo, a continuación, se extraiga la imagen de color de él y, a continuación, se extraen los datos sin procesar fuera de esa imagen.</span><span class="sxs-lookup"><span data-stu-id="c8544-147">First we get a capture from the device, then we extract the color image from it, and then we pull the raw data out of that image.</span></span>

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

<span data-ttu-id="c8544-148">Los datos se almacenan ahora en `colorDataBRGA` depende en el formato que se indica en la configuración.</span><span class="sxs-lookup"><span data-stu-id="c8544-148">The data now stored in `colorDataBRGA` is dependant on the format we indicated in configuration.</span></span> <span data-ttu-id="c8544-149">Puesto que se le pedirán `K4A_IMAGE_FORMAT_COLOR_BGRA32`, tenemos una matriz completa de los valores de color de 32 bits almacenados en BGRA order!</span><span class="sxs-lookup"><span data-stu-id="c8544-149">Since we asked for `K4A_IMAGE_FORMAT_COLOR_BGRA32`, we have an array full of 32 bit color values stored in BGRA order!</span></span>

<span data-ttu-id="c8544-150">¡En este caso, los archivos .tga almacenan los colores de BGR ya!</span><span class="sxs-lookup"><span data-stu-id="c8544-150">In this case, .tga files store colors in BGR order already!</span></span> <span data-ttu-id="c8544-151">Y dado que nuestra función guardando puede omitir el canal alfa con estos argumentos, simplemente podemos pasar los datos de la imagen tal cual.</span><span class="sxs-lookup"><span data-stu-id="c8544-151">And since our saving function can skip the alpha channel with these arguments, we can just pass the image data as is!</span></span>

## <a name="cleaning-up"></a><span data-ttu-id="c8544-152">Limpiar</span><span class="sxs-lookup"><span data-stu-id="c8544-152">Cleaning Up</span></span>

<span data-ttu-id="c8544-153">Y como siempre, recuerde que liberar los recursos cuando haya terminado con ellos.</span><span class="sxs-lookup"><span data-stu-id="c8544-153">And as always, remember to release your resources when you're done with them!</span></span>
```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(colors);
k4a_capture_release(capture);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

## <a name="full-source"></a><span data-ttu-id="c8544-154">Código fuente completo</span><span class="sxs-lookup"><span data-stu-id="c8544-154">Full Source</span></span>

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

## <a name="next-lab---mixing-color-and-depth-datamixdepthandrgbmd"></a><span data-ttu-id="c8544-155">La práctica siguiente - [mezclar el Color y los datos de profundidad](MixDepthAndRGB.md)</span><span class="sxs-lookup"><span data-stu-id="c8544-155">Next Lab - [Mixing Color and Depth Data](MixDepthAndRGB.md)</span></span>