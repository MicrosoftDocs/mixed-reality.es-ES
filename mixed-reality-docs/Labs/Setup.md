# <a name="setting-up"></a>Configurar

¿Introducción a la API de DK Kinect de Azure? No busque más. Este documento obtendrá en marcha con acceso al dispositivo.

En primer lugar, descargue e instale el [API de Azure Kinect DK](https://github.com/Microsoft/Azure-Kinect-Sensor-SDK) desde Github.

**Contenido**  
[Encabezados](#Headers)  
[Buscar un dispositivo de Kinect](#Finding-a-Kinect-Device)  
[A partir de las cámaras](#Starting-the-Cameras)  
[Control de errores](#Error-Handling)  
[Código fuente completo](#Full-Source)  

**Estas son las funciones que vamos a usar:**  
[`k4a_device_get_installed_count()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count)  
[`k4a_device_open()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open)  
[`k4a_device_get_serialnum()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-serialnum)  
[`k4a_device_start_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-start-cameras)  
[`k4a_device_stop_cameras()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-stop-cameras)  
[`k4a_device_close()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close)

## <a name="headers"></a>Encabezados
Hay solo un encabezado que necesitará, y eso es k4a.h! Asegúrese de que el compilador de elección se configura con lib del SDK e incluyen las carpetas. También necesitará los archivos k4a.lib y k4a.dll vinculados.
```C
#include <k4a/k4a.h>
```

## <a name="finding-a-kinect-device"></a>Buscar un dispositivo de Kinect

![](img/Serial.png)

¡En el equipo se pueden conectar varios dispositivos de Azure Kinect DK! Primero comenzaremos por buscar out cuántos, o si ninguno se conectan en absoluto con el [ `k4a_device_get_installed_count` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-installed-count) función. Esta función debería funcionar de inmediato, sin ninguna configuración adicional.

```C
uint32_t count = k4a_device_get_installed_count();
```

Una vez se haya determinado es realmente un dispositivo conectado al equipo, puede abrirlo con [ `k4a_device_open` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-open). Puede proporcionar el índice del dispositivo que desea abrir o, simplemente puede usar [ `K4A_DEVICE_DEFAULT` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-DEVICE-DEFAULT) para la primera de ellas.

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```
Como con la mayoría de las cosas en la API k4a, al abrir un documento, debe también debe cerrarse cuando haya terminado con él! Cuando se está cerrando, no olvide hacer una llamada a [ `k4a_device_close` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-close).

```C
k4a_device_close(device);
```

Una vez que el dispositivo está abierto, podemos realizar una prueba muy sencilla para asegurarse de que todo está bien. Así que vamos a leer el número de serie del dispositivo.

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

## <a name="starting-the-cameras"></a>A partir de las cámaras

Una vez que haya abierto el dispositivo, deberá configurar la cámara con un [ `k4a_device_configuration_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-configuration-t) objeto! Configuración de la cámara tiene varias opciones diferentes, y deberá elegir la configuración que mejor se adapten a su propio escenario.

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

Para obtener más detalles sobre la __color__ cámara, [desproteger este documento]()!  
Para obtener más detalles sobre la __profundidad__ cámara, [desproteger este documento]()!

## <a name="error-handling"></a>Control de errores

Por motivos de brevedad y claridad, nos no mostrar el control de errores en algunos ejemplos en línea. Sin embargo, el control de errores siempre es importante. Muchas funciones devolverá un tipo de éxito/error general [ `k4a_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-result-t), o una variante más específica con obtener información detallada, como [ `k4a_wait_result_t` ](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-wait-result-t). No olvide consultar a los documentos o intellisense de una función concreta para ver qué mensajes de error que es posible que espera ver desde él.

Junto con los tipos de error, también hay la [ `K4A_SUCCEEDED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-SUCCEEDED) y [ `K4A_FAILED` ](https://review.docs.microsoft.com/en-us/azurekinect/api/K4A-FAILED) macros que puede usar con ellos. Por lo que en lugar de simplemente abrir un dispositivo k4a, nos podríamos protegerse, similar al siguiente:

```C
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
    printf("Failed to open k4a device!\n");
    return;
}
```

# <a name="full-source"></a>Código fuente completo

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

## <a name="next-lab---reading-depth-datareaddepthmd"></a>La práctica siguiente - [leer los datos de profundidad](ReadDepth.md)
