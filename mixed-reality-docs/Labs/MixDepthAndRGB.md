# <a name="mixing-color-and-depth-data"></a><span data-ttu-id="981df-101">Combinación de colores y datos de profundidad</span><span class="sxs-lookup"><span data-stu-id="981df-101">Mixing Color and Depth Data</span></span>

<span data-ttu-id="981df-102">Los recursos que obtiene de la cámara de color y la cámara de profundidad tienen diferentes formas y tamaños.</span><span class="sxs-lookup"><span data-stu-id="981df-102">The resources you get from the color camera and the depth camera have different shapes and sizes!</span></span> <span data-ttu-id="981df-103">Si desea combinar los dos, hay varias cosas que puede hacer para alinearlos entre sí.</span><span class="sxs-lookup"><span data-stu-id="981df-103">If you want to combine the two, there's a number of things you can do to align them to each other.</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="981df-104">**Contenido:**</span><span class="sxs-lookup"><span data-stu-id="981df-104">**Contents:**</span></span>  
[<span data-ttu-id="981df-105">Instalación y configuración</span><span class="sxs-lookup"><span data-stu-id="981df-105">Configuration and Setup</span></span>](#Configuration-and-Setup)  
[<span data-ttu-id="981df-106">Obtención de datos</span><span class="sxs-lookup"><span data-stu-id="981df-106">Getting Data</span></span>](#Getting-Data)  
[<span data-ttu-id="981df-107">Transformación de datos</span><span class="sxs-lookup"><span data-stu-id="981df-107">Transforming Data</span></span>](#Transforming-Data)  
[<span data-ttu-id="981df-108">Creación de una malla de la nube de punto</span><span class="sxs-lookup"><span data-stu-id="981df-108">Creating a Mesh From the Point Cloud</span></span>](#Creating-a-Mesh-From-the-Point-Cloud)  
[<span data-ttu-id="981df-109">Creación de una imagen de Color y profundidad</span><span class="sxs-lookup"><span data-stu-id="981df-109">Creating an Image From Depth and Color</span></span>](#Creating-an-Image-From-Depth-and-Color)  
[<span data-ttu-id="981df-110">Limpiar</span><span class="sxs-lookup"><span data-stu-id="981df-110">Cleaning Up</span></span>](#Cleaning-Up)  
[<span data-ttu-id="981df-111">Código fuente completo</span><span class="sxs-lookup"><span data-stu-id="981df-111">Full Source</span></span>](#Full-Source)  

<span data-ttu-id="981df-112">**Estas son las funciones que vamos a usar:**</span><span class="sxs-lookup"><span data-stu-id="981df-112">**Here are the functions we'll use:**</span></span>  
[`k4a_device_get_calibration()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-device-get-calibration)  
[`k4a_transformation_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-create)  
[`k4a_image_create()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-image-create)  
[`k4a_transformation_depth_image_to_color_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-color-camera)  
[`k4a_transformation_color_image_to_depth_camera()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-color-image-to-depth-camera)  
[`k4a_transformation_depth_image_to_point_cloud()`](https://review.docs.microsoft.com/en-us/azurekinect/api/k4a-transformation-depth-image-to-point-cloud)  

## <a name="configuration-and-setup"></a><span data-ttu-id="981df-113">Instalación y configuración</span><span class="sxs-lookup"><span data-stu-id="981df-113">Configuration and Setup</span></span>

<span data-ttu-id="981df-114">Aunque podríamos usar cualquier configuración que queríamos aquí, nos estamos quede a resoluciones más bajas puesto que nos a escribir datos sin comprimir al archivo.</span><span class="sxs-lookup"><span data-stu-id="981df-114">While we could use just about any configuration we wanted here, we're sticking to smaller resolutions since we'll be writing uncompressed data to file.</span></span> <span data-ttu-id="981df-115">Consulte los documentos de lectura desde el [cámara color]() y [cámara profundidad]() para obtener más información acerca de las configuraciones!</span><span class="sxs-lookup"><span data-stu-id="981df-115">Check the documents on reading from the [color camera]() and [depth camera]() for more information about configurations!</span></span>

<span data-ttu-id="981df-116">Un elemento adicional es la `synchronized_images_only` opción!</span><span class="sxs-lookup"><span data-stu-id="981df-116">One additional element here is the `synchronized_images_only` option!</span></span> <span data-ttu-id="981df-117">Si se establece en `true` especifica que sólo se toman capturas que tienen ambos color <i>y</i> profundidad rellena.</span><span class="sxs-lookup"><span data-stu-id="981df-117">Setting it to `true` specifies that we only want captures that have both color <i>and</i> depth populated.</span></span> <span data-ttu-id="981df-118">Si no usamos esto, las primeras captura desde `k4a_device_get_capture` carecen de cualquier profundidad o imágenes de color.</span><span class="sxs-lookup"><span data-stu-id="981df-118">If we don't use this, the first few captures from `k4a_device_get_capture` may lack either depth, or color images.</span></span>

```C
// Configure the Kinect to open a stream of 512x512 wide field of view
// 16 bit depth data + 1280x720 BRGA color at 5 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_720P;
config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
config.synchronized_images_only = true;

k4a_device_start_cameras(device, &config);
```

<span data-ttu-id="981df-119">Ahora que tenemos nuestra información de configuración, necesitamos configurar un objeto de calibración que se pasarán a todas nuestras funciones de transformación.</span><span class="sxs-lookup"><span data-stu-id="981df-119">Now that we have our configuration information, we need to set up a calibration object that will be passed into all of our transformation functions!</span></span> <span data-ttu-id="981df-120">Este objeto contiene recursos precalculados utilizados para transformar las coordenadas hacia y desde el espacio de la cámara de color a profundidad, espacio y visa.</span><span class="sxs-lookup"><span data-stu-id="981df-120">This object contains precalculated resources used for transforming coordinates to and from color camera space to depth space and visa versa.</span></span> <span data-ttu-id="981df-121">Hacer que uno es bastante sencillo:</span><span class="sxs-lookup"><span data-stu-id="981df-121">Making one is pretty simple:</span></span>

```C
k4a_calibration_t calibration;
k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration);
k4a_transformation_t transform = k4a_transformation_create(&calibration);
```

## <a name="getting-data"></a><span data-ttu-id="981df-122">Obtención de datos</span><span class="sxs-lookup"><span data-stu-id="981df-122">Getting Data</span></span>

<span data-ttu-id="981df-123">Ahora necesitamos adquirir una imagen de color tanto una imagen de profundidad.</span><span class="sxs-lookup"><span data-stu-id="981df-123">Now we need to acquire both a color image, and a depth image!</span></span> <span data-ttu-id="981df-124">Aquí es tomar un solo fotograma y los datos pertinentes de él.</span><span class="sxs-lookup"><span data-stu-id="981df-124">So here's grabbing a single frame and the relevant data from it.</span></span> <span data-ttu-id="981df-125">Si una de las imágenes se transmite nula, asegúrese de que utilizado `synchronized_images_only` en la configuración.</span><span class="sxs-lookup"><span data-stu-id="981df-125">If one of your images is coming back null, ensure you used `synchronized_images_only` in your configuration!</span></span>

```C
// Wait until the first capture is available to us
k4a_capture_t capture;
k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE);

// Grab image data from the Kinect
k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
int32_t color_w = k4a_image_get_width_pixels (raw_colors);
int32_t color_h = k4a_image_get_height_pixels(raw_colors);
printf("Captured depth image, %dx%d\n", depth_w, depth_h);
printf("Captured rgb image, %dx%d\n", color_w, color_h);
```

## <a name="transforming-data"></a><span data-ttu-id="981df-126">Transformación de datos</span><span class="sxs-lookup"><span data-stu-id="981df-126">Transforming Data</span></span>

<span data-ttu-id="981df-127">El `k4a_transform_` funciones transformará los datos de imagen del espacio de una cámara a otro.</span><span class="sxs-lookup"><span data-stu-id="981df-127">The `k4a_transform_` functions will transform your image data from one camera space to another!</span></span> <span data-ttu-id="981df-128">Las imágenes resultantes coincidirá con la distorsión y la resolución del espacio de la cámara de destino, por lo que puede poner en correlación la información de color y la profundidad juntos con facilidad.</span><span class="sxs-lookup"><span data-stu-id="981df-128">Resulting images will match the distortion and resolution of the target camera space, so you can correlate color and depth information together easily.</span></span>

<span data-ttu-id="981df-129">¡Por ejemplo!</span><span class="sxs-lookup"><span data-stu-id="981df-129">For example!</span></span> <span data-ttu-id="981df-130">Con bastante frecuencia, es posible que quiera una imagen de color de la cámara, con una profundidad correspondiente para cada píxel de color!</span><span class="sxs-lookup"><span data-stu-id="981df-130">Quite often, you might want a color image from the camera, with a corresponding depth for each color pixel!</span></span> <span data-ttu-id="981df-131">Para ello, podría transformar los datos de profundidad en el espacio de color de cámara.</span><span class="sxs-lookup"><span data-stu-id="981df-131">For this, you would transform the depth data into color camera space.</span></span>

<span data-ttu-id="981df-132">Como alternativa, puede crear una nube de datos de puntos 3D de la cámara de profundidad, y saber qué color de cada punto es.</span><span class="sxs-lookup"><span data-stu-id="981df-132">Alternatively, you might want to create a cloud of 3D point data from the depth camera, and know what color each point is.</span></span> <span data-ttu-id="981df-133">Para ello, podemos transformar los datos de profundidad en una nube de punto y transformar la imagen de color en el espacio de la cámara de profundidad.</span><span class="sxs-lookup"><span data-stu-id="981df-133">For this, we can transform the depth data into a point cloud, and transform the color image into depth camera space!</span></span> <span data-ttu-id="981df-134">A continuación, tendrá un búfer de los valores XYZ y un búfer correspondiente de colores.</span><span class="sxs-lookup"><span data-stu-id="981df-134">Then you'll have a buffer of XYZ values, and a corresponding buffer of colors.</span></span>

### <a name="depth-data-in-color-space"></a><span data-ttu-id="981df-135">Datos de profundidad en el espacio de colores</span><span class="sxs-lookup"><span data-stu-id="981df-135">Depth Data in Color Space</span></span>

<span data-ttu-id="981df-136">Esto transforma los datos de profundidad para coincidir con salida de la cámara de color.</span><span class="sxs-lookup"><span data-stu-id="981df-136">This transforms depth data to match the color camera's output!</span></span> <span data-ttu-id="981df-137">El búfer resultante tendrá un valor de profundidad de 16 bits para cada píxel de la imagen en color.</span><span class="sxs-lookup"><span data-stu-id="981df-137">The resulting buffer will have a 16 bit depth value for each pixel in the color image.</span></span>
 
```C
k4a_image_t depth_color_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_DEPTH16, 
    color_w, color_h, color_w * sizeof(uint16_t), 
    &depth_color_space))
k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

uint16_t *depth_data = reinterpret_cast<uint16_t*>(k4a_image_get_buffer(depth_color_space));
```

### <a name="creating-a-point-cloud"></a><span data-ttu-id="981df-138">Creación de una nube de punto</span><span class="sxs-lookup"><span data-stu-id="981df-138">Creating a Point Cloud</span></span>

<span data-ttu-id="981df-139">Punto nubes también se almacenan en los recursos de imagen.</span><span class="sxs-lookup"><span data-stu-id="981df-139">Point clouds are also stored in image resources!</span></span> <span data-ttu-id="981df-140">En este caso, creamos una imagen de formato `K4A_IMAGE_FORMAT_CUSTOM`, ya que una nube de punto no es exactamente una imagen.</span><span class="sxs-lookup"><span data-stu-id="981df-140">Here, we create an image of format `K4A_IMAGE_FORMAT_CUSTOM`, since a point cloud is not exactly an image.</span></span> <span data-ttu-id="981df-141">Cada píxel' ' en la imagen se compone de 3 `int16_t` valores que representan coordenadas XYZ, por lo que también especificamos el tamaño correcto para eso.</span><span class="sxs-lookup"><span data-stu-id="981df-141">Each 'pixel' in the image will be composed of 3 `int16_t` values representing XYZ coordinates, so we also specify the correct size for that.</span></span>

```C
k4a_image_t point_cloud_xyz;
k4a_image_create(
    K4A_IMAGE_FORMAT_CUSTOM, 
    depth_w, depth_h, depth_w * 3 * sizeof(int16_t), 
    &point_cloud_xyz);
k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

int16_t *xyz_data = reinterpret_cast<int16_t*>(k4a_image_get_buffer(point_cloud_xyz))
```

### <a name="color-data-in-depth-space"></a><span data-ttu-id="981df-142">Datos de color en el espacio de profundidad</span><span class="sxs-lookup"><span data-stu-id="981df-142">Color Data in Depth Space</span></span>

<span data-ttu-id="981df-143">¡Esto transforma los datos de color para coincidir con la salida de la cámara de profundidad!</span><span class="sxs-lookup"><span data-stu-id="981df-143">This transforms color data to match the output from the depth camera!</span></span> <span data-ttu-id="981df-144">Cada valor de color desde el búfer resultante se corresponderá con un valor de la imagen de profundidad.</span><span class="sxs-lookup"><span data-stu-id="981df-144">Each color value from the resulting buffer will correspond with a value from the depth image.</span></span>

```C
k4a_image_t color_depth_space;
k4a_image_create(
    K4A_IMAGE_FORMAT_COLOR_BGRA32, 
    depth_w, depth_h, depth_w * sizeof(uint32_t), 
    &color_depth_space);
k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

uint8_t *color_data = static_cast<uint8_t*>(k4a_image_get_buffer(color_depth_space));
```

## <a name="creating-a-mesh-from-the-point-cloud"></a><span data-ttu-id="981df-145">Creación de una malla de la nube de punto</span><span class="sxs-lookup"><span data-stu-id="981df-145">Creating a Mesh From the Point Cloud</span></span>

![](img/ColorandDepthMeshSmall.png)

<span data-ttu-id="981df-146">Comenzaremos convirtiendo los datos en la nube del punto en un formato que sea un poco más familiarizado.</span><span class="sxs-lookup"><span data-stu-id="981df-146">We'll start by converting the point cloud data into a format that's a little more familiar.</span></span> <span data-ttu-id="981df-147">Se podrá convertir desde milímetros metros y moverla a valores de punto flotante.</span><span class="sxs-lookup"><span data-stu-id="981df-147">We'll convert it from millimeters to meters, and move it over to floats.</span></span>

```C
// Convert the point cloud from millimeters to meters
float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
for (int32_t i = 0; i < depth_w*depth_h; i++)
{
    vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
    vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
    vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
}
```

<span data-ttu-id="981df-148">¡Ahora podrá debe combinar estos vértices con cierta información de cara superiores!</span><span class="sxs-lookup"><span data-stu-id="981df-148">Now we'll stitch up these vertices with some face information!</span></span> <span data-ttu-id="981df-149">Puesto que todo está diseñado como una cuadrícula, este es un proceso sencillo de vinculación de las esquinas de cada celda.</span><span class="sxs-lookup"><span data-stu-id="981df-149">Since everything is laid out as a grid, this is a straightforward process of linking up the corners of each cell.</span></span> <span data-ttu-id="981df-150">Omite cualquier cara que contiene datos vacíos adicional solo lo que estamos haciendo aquí.</span><span class="sxs-lookup"><span data-stu-id="981df-150">The only additional thing we're doing here is skipping any face that contains empty data.</span></span> <span data-ttu-id="981df-151">Si el Kinect no encontró datos de profundidad de un punto en la nube de punto, lo ubica en < 0,0,0 >!</span><span class="sxs-lookup"><span data-stu-id="981df-151">If the Kinect couldn't find depth data for a point in the point cloud, it places it at <0,0,0>!</span></span> <span data-ttu-id="981df-152">Se convierte en bastante el hedgehog si agregarlos a la lista de índice.</span><span class="sxs-lookup"><span data-stu-id="981df-152">It turns into quite the hedgehog if you add those to the index list.</span></span>

```C
// Make mesh faces as quads across the image. Skip the 
// face if any part of its data is empty.
vector<uint32_t> indices;
for (int32_t y = 0; y < depth_h; y++)
{
    for (int32_t x = 0; x < depth_w; x++)
    {
        int32_t row1 = x +       y * depth_w;
        int32_t row2 = x + (y + 1) * depth_w;

        // If all corners of this quad have depth data
        if (xyz_data[ row1      * 3 + 1] != 0 && 
            xyz_data[(row1 + 1) * 3 + 1] != 0 && 
            xyz_data[ row2      * 3 + 1] != 0 && 
            xyz_data[(row2 + 1) * 3 + 1] != 0)
        {
            // ..then add indices for this quad
            indices.push_back(row2);
            indices.push_back(row2+1);
            indices.push_back(row1+1);
            indices.push_back(row1);
        }
    }
}
```

<span data-ttu-id="981df-153">¡A continuación, podemos escribir esta información al archivo!</span><span class="sxs-lookup"><span data-stu-id="981df-153">Then we can just write this information to file!</span></span> <span data-ttu-id="981df-154">Lo que no quita los colores sin usar o posiciones debido al mayor complejidad en la creación de índices, por lo que podemos simplemente pasamos en los búferes que hasta ahora hemos creado.</span><span class="sxs-lookup"><span data-stu-id="981df-154">We aren't removing unused colors or positions due to added complexity in creating indices, so we can just pass in the buffers we've created so far.</span></span>

```C
// Write geometry data to a .PLY, and clean up
ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, indices.size() / 4, &indices[0]);
free(vertex_positions);
```

## <a name="creating-an-image-from-depth-and-color"></a><span data-ttu-id="981df-155">Creación de una imagen de Color y profundidad</span><span class="sxs-lookup"><span data-stu-id="981df-155">Creating an Image From Depth and Color</span></span>

![](img/ColorandDepthSmall.png)

<span data-ttu-id="981df-156">¡Con los colores, esto es mucho más fácil hacer!</span><span class="sxs-lookup"><span data-stu-id="981df-156">With colors, this is much easier to do!</span></span> <span data-ttu-id="981df-157">En este caso, haremos una transición sencilla a negro en la distancia, pero podría hacer a todo tipo de cosas interesantes, como recorte horizontal determinados intervalos de profundidad, o el almacenamiento de profundidad en el canal alfa para su uso como una máscara en una herramienta de manipulación de fotografías.</span><span class="sxs-lookup"><span data-stu-id="981df-157">Here, we'll do a simple fade to black in the distance, but you could do all sorts of interesting things, like clipping out certain depth ranges, or storing depth in the alpha channel for use as a mask in a photo manipulation tool!</span></span>

```C
// Create an RGB image where we fade color values to black as they recede into the distance
uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
for (int32_t i = 0; i < color_w*color_h; i++)
{
    // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
    float depth = 1 - depth_data[i]/4000.0f;
    depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

    // Fade this pixel, and assign it to our new buffer
    mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
    mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
    mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
}
// Write the image to file
tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
free(mixed_colors);
```

## <a name="cleaning-up"></a><span data-ttu-id="981df-158">Limpiar</span><span class="sxs-lookup"><span data-stu-id="981df-158">Cleaning Up</span></span>

<span data-ttu-id="981df-159">Y como siempre, liberar todo cuando haya terminado :)</span><span class="sxs-lookup"><span data-stu-id="981df-159">And as always, release everything when you're finished :)</span></span>

```C
// Release all allocated resources, and shut down the Kinect
k4a_image_release(point_cloud_xyz);
k4a_image_release(depth_color_space);
k4a_image_release(color_depth_space);
k4a_image_release(raw_colors);
k4a_image_release(raw_depth);
k4a_capture_release(capture);
k4a_transformation_destroy(transform);

k4a_device_stop_cameras(device);
k4a_device_close(device);
```

# <a name="full-source"></a><span data-ttu-id="981df-160">Código fuente completo</span><span class="sxs-lookup"><span data-stu-id="981df-160">Full Source</span></span>

```C
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>

#include <stdio.h>
#include <stdlib.h>

#include <vector>
using namespace std;

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices);
void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels);

int main()
{
    // Open the first plugged in Kinect device
    k4a_device_t device = NULL;
    k4a_device_open(K4A_DEVICE_DEFAULT, &device);

    // Configure the Kinect to open a stream of 512x512 wide field of view
    // 16 bit depth data + 1280x720 BRGA color at 5 frames per second
    k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
    config.camera_fps       = K4A_FRAMES_PER_SECOND_5;
    config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
    config.color_resolution = K4A_COLOR_RESOLUTION_720P;
    config.depth_mode       = K4A_DEPTH_MODE_WFOV_2X2BINNED;
    config.synchronized_images_only = true;
    if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
        printf("Failed to start cameras!\n");

    // Prep data for transforming depth information to color camera space
    k4a_calibration_t calibration;
    if (K4A_FAILED(k4a_device_get_calibration(device, config.depth_mode, config.color_resolution, &calibration)))
        printf("Failed to get calibration!\n");
    k4a_transformation_t transform = k4a_transformation_create(&calibration);

    // Wait until the first capture is available to us
    k4a_capture_t capture;
    if (K4A_FAILED(k4a_device_get_capture(device, &capture, K4A_WAIT_INFINITE)))
        printf("Failed to capture image!\n");

    // Grab image data from the Kinect
    k4a_image_t raw_depth  = k4a_capture_get_depth_image(capture);
    k4a_image_t raw_colors = k4a_capture_get_color_image(capture);
    int32_t depth_w = k4a_image_get_width_pixels (raw_depth);
    int32_t depth_h = k4a_image_get_height_pixels(raw_depth);
    int32_t color_w = k4a_image_get_width_pixels (raw_colors);
    int32_t color_h = k4a_image_get_height_pixels(raw_colors);
    printf("Captured depth image, %dx%d\n", depth_w, depth_h);
    printf("Captured rgb image, %dx%d\n", color_w, color_h);

    // Transform the raw depth data into color camera space
    k4a_image_t depth_color_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_DEPTH16, color_w, color_h, color_w * sizeof(uint16_t), &depth_color_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_depth_image_to_color_camera(transform, raw_depth, depth_color_space);

    // Get the point cloud
    k4a_image_t point_cloud_xyz;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_CUSTOM, depth_w, depth_h, depth_w * 3 * sizeof(int16_t), &point_cloud_xyz)))
        printf("Failed to create a point cloud image resource!\n");
    k4a_transformation_depth_image_to_point_cloud(transform, raw_depth, K4A_CALIBRATION_TYPE_DEPTH, point_cloud_xyz);

    // Transform the raw color data into depth camera space
    k4a_image_t color_depth_space;
    if (K4A_FAILED(k4a_image_create(K4A_IMAGE_FORMAT_COLOR_BGRA32, depth_w, depth_h, depth_w * sizeof(uint32_t), &color_depth_space)))
        printf("Failed to create an image resource!\n");
    k4a_transformation_color_image_to_depth_camera(transform, raw_depth, raw_colors, color_depth_space);

    // Get access to the raw color and point cloud data.
    uint8_t  *raw_color_data = static_cast     <uint8_t  *>(k4a_image_get_buffer(raw_colors));
    uint8_t  *color_data     = static_cast     <uint8_t  *>(k4a_image_get_buffer(color_depth_space));
    uint16_t *depth_data     = reinterpret_cast<uint16_t *>(k4a_image_get_buffer(depth_color_space));
    int16_t  *xyz_data       = reinterpret_cast<int16_t  *>(k4a_image_get_buffer(point_cloud_xyz));

    // Turn the point cloud into a mesh, and write it to file!

    // Convert the point cloud from millimeters to meters
    float *vertex_positions = static_cast<float*>(malloc(sizeof(float) * 3 * depth_w*depth_h));
    for (int32_t i = 0; i < depth_w*depth_h; i++)
    {
        vertex_positions[i*3  ] = xyz_data[i*3  ] / 1000.0f;
        vertex_positions[i*3+1] = xyz_data[i*3+1] / 1000.0f;
        vertex_positions[i*3+2] = xyz_data[i*3+2] / 1000.0f;
    }

    // Make mesh faces as quads across the image. Skip the
    // face if any part of its data is empty.
    vector<uint32_t> indices;
    for (int32_t y = 0; y < depth_h; y++)
    {
        for (int32_t x = 0; x < depth_w; x++)
        {
            int32_t row1 = x +       y * depth_w;
            int32_t row2 = x + (y + 1) * depth_w;

            // If all corners of this quad have depth data
            if (xyz_data[ row1      * 3 + 1] != 0 && 
                xyz_data[(row1 + 1) * 3 + 1] != 0 && 
                xyz_data[ row2      * 3 + 1] != 0 && 
                xyz_data[(row2 + 1) * 3 + 1] != 0)
            {
                // ..then add indices for this quad
                indices.push_back(row2);
                indices.push_back(row2+1);
                indices.push_back(row1+1);
                indices.push_back(row1);
            }
        }
    }

    // Write geometry data to a .PLY, and clean up
    ply_write("mesh.ply", depth_w * depth_h, vertex_positions, color_data, static_cast<uint32_t>(indices.size()) / 4, &indices[0]);
    free(vertex_positions);
    
    // Create an RGB image where we fade color values to black as they recede into the distance
    uint8_t *mixed_colors = static_cast<uint8_t *>(malloc(sizeof(uint8_t) * 3 * color_w * color_h));
    for (int32_t i = 0; i < color_w*color_h; i++)
    {
        // Find a percentage between 4m and 0m, no depth (depth==0) gets set to black
        float depth = 1 - depth_data[i]/4000.0f;
        depth = depth < 0 || depth_data[i] == 0 ? 0.0f : depth;

        // Fade this pixel, and assign it to our new buffer
        mixed_colors[i*3  ] = static_cast<uint8_t>(raw_color_data[i*4  ] * depth);
        mixed_colors[i*3+1] = static_cast<uint8_t>(raw_color_data[i*4+1] * depth);
        mixed_colors[i*3+2] = static_cast<uint8_t>(raw_color_data[i*4+2] * depth);
    }
    // Write the image to file
    tga_write("colorTex.tga", color_w, color_h, mixed_colors, 3, 3);
    free(mixed_colors);

    // Release all allocated resources, and shut down the Kinect
    k4a_image_release(point_cloud_xyz);
    k4a_image_release(depth_color_space);
    k4a_image_release(color_depth_space);
    k4a_image_release(raw_colors);
    k4a_image_release(raw_depth);
    k4a_capture_release(capture);
    k4a_transformation_destroy(transform);

    k4a_device_stop_cameras(device);
    k4a_device_close(device);

    return 0;
}

void ply_write(const char *filename, uint32_t vertex_count, float *vertex_positions, uint8_t *vertex_colors_bgra, uint32_t index_quad_count, uint32_t *quad_indices)
{
    FILE *fp = nullptr;
    fopen_s(&fp, filename, "w");

    // Write the .PLY header information
    fprintf(fp, "ply\nformat ascii 1.0\n");
    fprintf(fp, "element vertex %d\nproperty float x\nproperty float y\nproperty float z\nproperty uchar red\nproperty uchar green\nproperty uchar blue\n", vertex_count);
    fprintf(fp, "element face %d\nproperty list uchar int vertex_index\n", index_quad_count);
    fprintf(fp, "end_header\n");

    // Write each vertex with color information!
    for (uint32_t i = 0; i < vertex_count; i++)
    {
        fprintf(fp, "%g %g %g %d %d %d\n", 
            vertex_positions[i*3    ],
            vertex_positions[i*3 + 1],
            vertex_positions[i*3 + 2], 
            vertex_colors_bgra[i*4 + 2], 
            vertex_colors_bgra[i*4 + 1], 
            vertex_colors_bgra[i*4    ]);
    }

    // Write faces as quads.
    for (size_t i = 0; i < index_quad_count; i++)
    {
        fprintf(fp, "4 %d %d %d %d\n", quad_indices[i*4], quad_indices[i*4 + 1], quad_indices[i*4 + 2], quad_indices[i*4 + 3]);
    }
    fclose(fp);
}

void tga_write(const char *filename, uint32_t width, uint32_t height, uint8_t *data_bgra, uint8_t data_channels, uint8_t file_channels)
{
    FILE *fp = NULL;
    fopen_s(&fp, filename, "wb");
    if (fp == NULL) return;

    uint8_t header[18] = { 0,0,2,0,0,0,0,0,0,0,0,0, width%256, (uint8_t)(width/256), height%256, (uint8_t)(height/256), file_channels*8u, 0x20 };
    fwrite(&header, 18, 1, fp);
    for (uint32_t i = 0; i < width*height; i++)
        for (uint32_t b = 0; b < file_channels; b++)
            fputc(data_bgra[(i*data_channels) + (b%data_channels)], fp);
    fclose(fp);
}
```

## <a name="next-lab---accessing-the-imuusingimumd"></a><span data-ttu-id="981df-161">La práctica siguiente - [acceso a la IMU](UsingIMU.md)</span><span class="sxs-lookup"><span data-stu-id="981df-161">Next Lab - [Accessing the IMU](UsingIMU.md)</span></span>