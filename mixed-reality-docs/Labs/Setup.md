# <a name="setting-up"></a><span data-ttu-id="2a048-101">Configurar</span><span class="sxs-lookup"><span data-stu-id="2a048-101">Setting Up</span></span>

<span data-ttu-id="2a048-102">¿Introducción a la API de DK Kinect de Azure?</span><span class="sxs-lookup"><span data-stu-id="2a048-102">Getting started with the Azure Kinect DK API?</span></span> <span data-ttu-id="2a048-103">No busque más.</span><span class="sxs-lookup"><span data-stu-id="2a048-103">Look no further!</span></span> <span data-ttu-id="2a048-104">Este documento obtendrá en marcha con acceso al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2a048-104">This document will get you up and running with access to the device!</span></span>

<span data-ttu-id="2a048-105">En primer lugar, descargue e instale el [API de Azure Kinect DK](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) desde Github.</span><span class="sxs-lookup"><span data-stu-id="2a048-105">First, download and install the [Azure Kinect DK API](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) from Github.</span></span>

<span data-ttu-id="2a048-106">**Contenido**</span><span class="sxs-lookup"><span data-stu-id="2a048-106">**Contents**</span></span>  
[<span data-ttu-id="2a048-107">Encabezados</span><span class="sxs-lookup"><span data-stu-id="2a048-107">Headers</span></span>](#Headers)  
[<span data-ttu-id="2a048-108">Buscar un dispositivo de Kinect</span><span class="sxs-lookup"><span data-stu-id="2a048-108">Finding a Kinect Device</span></span>](#Finding-a-Kinect-Device)  
[<span data-ttu-id="2a048-109">A partir de las cámaras</span><span class="sxs-lookup"><span data-stu-id="2a048-109">Starting the Cameras</span></span>](#Starting-the-Cameras)  
[<span data-ttu-id="2a048-110">Control de errores</span><span class="sxs-lookup"><span data-stu-id="2a048-110">Error Handling</span></span>](#Error-Handling)  
[<span data-ttu-id="2a048-111">Código fuente completo</span><span class="sxs-lookup"><span data-stu-id="2a048-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="2a048-112">**Estas son las funciones que vamos a usar:**</span><span class="sxs-lookup"><span data-stu-id="2a048-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a><span data-ttu-id="2a048-113">Encabezados</span><span class="sxs-lookup"><span data-stu-id="2a048-113">Headers</span></span>
<span data-ttu-id="2a048-114">Hay solo un encabezado que necesitará, y eso es k4a.h!</span><span class="sxs-lookup"><span data-stu-id="2a048-114">There's only one header that you'll need, and that's k4a.h!</span></span> <span data-ttu-id="2a048-115">Asegúrese de que el compilador de elección se configura con lib del SDK e incluyen las carpetas.</span><span class="sxs-lookup"><span data-stu-id="2a048-115">Make sure your compiler of choice is set up with the SDK's lib and include folders.</span></span> <span data-ttu-id="2a048-116">También necesitará los archivos k4a.lib y k4a.dll vinculados.</span><span class="sxs-lookup"><span data-stu-id="2a048-116">You'll also need the k4a.lib and k4a.dll files linked up.</span></span>
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a><span data-ttu-id="2a048-117">Buscar un dispositivo de Kinect</span><span class="sxs-lookup"><span data-stu-id="2a048-117">Finding a Kinect Device</span></span>

![](img/Serial.png)

<span data-ttu-id="2a048-118">¡En el equipo se pueden conectar varios dispositivos de Azure Kinect DK!</span><span class="sxs-lookup"><span data-stu-id="2a048-118">Multiple Azure Kinect DK devices can be connected to your computer!</span></span> <span data-ttu-id="2a048-119">Primero comenzaremos por buscar out cuántos, o si ninguno se conectan en absoluto con el [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) función.</span><span class="sxs-lookup"><span data-stu-id="2a048-119">We'll first start by finding out how many, or if any are connected at all using the [`k4a_device_get_installed_count`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) function.</span></span> <span data-ttu-id="2a048-120">Esta función debería funcionar de inmediato, sin ninguna configuración adicional.</span><span class="sxs-lookup"><span data-stu-id="2a048-120">This function should work right away, without any additional setup!</span></span>

```C
uint32_t count = k4a_device_get_installed_count();
```

<span data-ttu-id="2a048-121">Una vez se haya determinado es realmente un dispositivo conectado al equipo, puede abrirlo con [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span><span class="sxs-lookup"><span data-stu-id="2a048-121">Once you've determined there is actually a device connected to the computer, you can open it using [`k4a_device_open`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open).</span></span> <span data-ttu-id="2a048-122">Puede proporcionar el índice del dispositivo que desea abrir o, simplemente puede usar [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) para la primera de ellas.</span><span class="sxs-lookup"><span data-stu-id="2a048-122">You can provide the index of the device you want to open, or you can just use [`K4A_DEVICE_DEFAULT`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) for the first one.</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
<span data-ttu-id="2a048-123">Como con la mayoría de las cosas en la API k4a, al abrir un documento, debe también debe cerrarse cuando haya terminado con él!</span><span class="sxs-lookup"><span data-stu-id="2a048-123">As with most things in the k4a API, when you open something, you should also close it when you're finished with it!</span></span> <span data-ttu-id="2a048-124">Cuando se está cerrando, no olvide hacer una llamada a [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span><span class="sxs-lookup"><span data-stu-id="2a048-124">When you're shutting down, remember to make a call to [`k4a_device_close`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).</span></span>

```C
k4a_device_close(device);
```

<span data-ttu-id="2a048-125">Una vez que el dispositivo está abierto, podemos realizar una prueba muy sencilla para asegurarse de que todo está bien.</span><span class="sxs-lookup"><span data-stu-id="2a048-125">Once the device is open, we can make a really simple test to ensure it's all good.</span></span> <span data-ttu-id="2a048-126">Así que vamos a leer el número de serie del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2a048-126">So let's read the device's serial number!</span></span>

```C
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = static_cast<char*>(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

## <a name="starting-the-cameras"></a><span data-ttu-id="2a048-127">A partir de las cámaras</span><span class="sxs-lookup"><span data-stu-id="2a048-127">Starting the Cameras</span></span>

<span data-ttu-id="2a048-128">Una vez que haya abierto el dispositivo, deberá configurar la cámara con un [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) objeto!</span><span class="sxs-lookup"><span data-stu-id="2a048-128">Once you've opened the device, you'll need to configure the camera with a [`k4a_device_configuration_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) object!</span></span> <span data-ttu-id="2a048-129">Configuración de la cámara tiene varias opciones diferentes, y deberá elegir la configuración que mejor se adapten a su propio escenario.</span><span class="sxs-lookup"><span data-stu-id="2a048-129">Camera configuration has a number of different options, and you'll need to choose the settings that best fit your own scenario.</span></span>

```C
// Configure a stream of 4096x3072 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config)

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

<span data-ttu-id="2a048-130">Para obtener más detalles sobre la __color__ cámara, [desproteger este documento]()!</span><span class="sxs-lookup"><span data-stu-id="2a048-130">For configuration details about the __color__ camera, [check out this document]()!</span></span>  
<span data-ttu-id="2a048-131">Para obtener más detalles sobre la __profundidad__ cámara, [desproteger este documento]()!</span><span class="sxs-lookup"><span data-stu-id="2a048-131">For configuration details about the __depth__ camera, [check out this document]()!</span></span>

## <a name="error-handling"></a><span data-ttu-id="2a048-132">Control de errores</span><span class="sxs-lookup"><span data-stu-id="2a048-132">Error Handling</span></span>

<span data-ttu-id="2a048-133">Por motivos de brevedad y claridad, nos no mostrar el control de errores en algunos ejemplos en línea.</span><span class="sxs-lookup"><span data-stu-id="2a048-133">For the sake of brevity and clarity, we don't show error handling in some inline examples.</span></span> <span data-ttu-id="2a048-134">Sin embargo, el control de errores siempre es importante.</span><span class="sxs-lookup"><span data-stu-id="2a048-134">However, error handling is always important!</span></span> <span data-ttu-id="2a048-135">Muchas funciones devolverá un tipo de éxito/error general [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), o una variante más específica con obtener información detallada, como [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span><span class="sxs-lookup"><span data-stu-id="2a048-135">Many functions will return a general success/failure type [`k4a_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), or a more specific variant with detailed information such as [`k4a_wait_result_t`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t).</span></span> <span data-ttu-id="2a048-136">No olvide consultar a los documentos o intellisense de una función concreta para ver qué mensajes de error que es posible que espera ver desde él.</span><span class="sxs-lookup"><span data-stu-id="2a048-136">Be sure to check the docs or intellisense of a specific function to see what error messages you might expect to see from it!</span></span>

<span data-ttu-id="2a048-137">Junto con los tipos de error, también hay la [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) y [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros que puede usar con ellos.</span><span class="sxs-lookup"><span data-stu-id="2a048-137">Along with the error types, there's also the [`K4A_SUCCEEDED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) and [`K4A_FAILED`](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros that you can use with them.</span></span> <span data-ttu-id="2a048-138">Por lo que en lugar de simplemente abrir un dispositivo k4a, nos podríamos protegerse, similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="2a048-138">So instead of just opening a k4a device, we might guard it like this:</span></span>

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a><span data-ttu-id="2a048-139">Código fuente completo</span><span class="sxs-lookup"><span data-stu-id="2a048-139">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

int main()
{
    uint32_t count = k4a_device_get_installed_count();
    if (count == 0)
    {
        printf("No k4a devices attached!\n");
        return 0;
    }

    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device)))
    {
        printf("Failed to open k4a device!\n");
        return 0;
    }

    // Get the size of the serial number
    size_t serial_size = 0;
    k4a_device_get_serialnum(device, NULL, &serial_size);

    // Allocate memory for the serial, then acquire it
    char* serial = static_cast<char*>(malloc(serial_size));
    k4a_device_get_serialnum(device, serial, &serial_size);
    printf("Opened device: %s\n", serial);
    free(serial);

    // Configure a stream of 4096x3072 BRGA color data at 15 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps = K4A_FRAMES_PER_SECOND_15;
    config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_3072P;

    // Start the camera with the given configuration
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
    {
        printf("Failed to start cameras!\n");
        k4a_device_close(device);
        return 0;
    }

    // ...Camera capture and application specific code would go here...

    // Shut down the camera when finished with application logic
    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}
```

## <a name="next-lab---reading-depth-datareaddepthmd"></a><span data-ttu-id="2a048-140">La práctica siguiente - [leer los datos de profundidad](ReadDepth.md)</span><span class="sxs-lookup"><span data-stu-id="2a048-140">Next Lab - [Reading Depth Data](ReadDepth.md)</span></span>
