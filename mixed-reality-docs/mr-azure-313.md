---
title: MR y Azure 313-IoT Hub servicio
description: Complete este curso para aprender a implementar Azure IoT Hub servicio en una máquina virtual que ejecuta Ubuntu 16,4 y, a continuación, visualice los datos de los mensajes mediante Microsoft HoloLens o un casco envolvente (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, realidad mixta, Academia, Edge, IOT Edge, tutorial, API, notificación, funciones, tablas, hololens, inmersivo, VR, IOT, máquina virtual, Ubuntu, Python
ms.openlocfilehash: 7f56c7931bb036d14ab3aa9156706b1f6247195c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437967"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

# <a name="mr-and-azure-313-iot-hub-service"></a>MR y Azure 313: servicio de IoT Hub

![resultado del curso](images/AzureLabs-Lab313-00.png)

En este curso, aprenderá a implementar un servicio de **Azure IOT Hub** en una máquina virtual que ejecuta el sistema operativo Ubuntu 16,4. A continuación, se usará una **function App de Azure** para recibir mensajes de la máquina virtual de Ubuntu y almacenar el resultado en un **servicio tabla de Azure**. A continuación, podrá ver estos datos con **Power BI** en el casco de Microsoft HoloLens o envolvente (VR).

El contenido de este curso *es aplicable* a los dispositivos IOT Edge, aunque para este curso, el foco estará en un entorno de máquina virtual, de modo que el acceso a un dispositivo perimetral físico no sea necesario.

Al completar este curso, aprenderá a:

- Implemente un **módulo de IOT Edge** en una máquina virtual (sistema operativo Ubuntu 16), que representará el dispositivo de IOT.
- Agregue un **modelo Tensorflow de Azure Custom Vision** al módulo Edge, con código que analizará las imágenes almacenadas en el contenedor.
- Configure el módulo para enviar el mensaje de resultado del análisis de vuelta a su **servicio de IOT Hub**.
- Use una **function App de Azure** para almacenar el mensaje en una **tabla de Azure**.
- Configure **Power BI** para recopilar el mensaje almacenado y crear un informe.
- Visualice los datos de los mensajes de IoT en **Power BI**.

Los servicios que usará incluyen:

- **Azure IOT Hub** es un servicio de Microsoft Azure que permite a los desarrolladores conectarse, supervisar y administrar recursos de IOT. Para obtener más información, visite la [página **servicio de Azure IOT Hub** ](https://azure.microsoft.com/services/iot-hub/).

- **Azure Container Registry** es un servicio de Microsoft Azure que permite a los desarrolladores almacenar imágenes de contenedor para varios tipos de contenedores. Para obtener más información, visite la [página **servicio de Azure Container Registry** ](https://azure.microsoft.com/services/container-registry/).

- **Azure function App** es un servicio Microsoft Azure, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure. Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas. **Azure Functions** admite varios lenguajes de desarrollo, como C\#, F\#, node. js, Java y php. Para obtener más información, visite la [página **Azure Functions** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Azure Storage: tables** es un servicio de Microsoft Azure, que permite a los desarrolladores almacenar datos estructurados que no son de SQL en la nube, lo que hace que sea fácilmente accesible en cualquier lugar. El servicio ofrece un diseño sin esquemas, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible. Para obtener más información, visite la [página **tablas de Azure** .](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Este curso le enseñará cómo configurar y usar el servicio de IoT Hub y, a continuación, visualizar una respuesta proporcionada por un dispositivo. Dependerá de que aplique estos conceptos a una configuración personalizada del servicio de IoT Hub, que podría estar compilando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 313: servicio de IoT Hub</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

Para obtener los requisitos previos más actualizados para el desarrollo con la realidad mixta, incluido con Microsoft HoloLens, visite el artículo [instalar las herramientas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Python. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio). Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.

Se requiere el siguiente hardware y software:

- Windows 10 Fall Creators Update (o posterior), **modo de desarrollador habilitado**

    > [!WARNING]
    > No se puede ejecutar una máquina virtual con Hyper-V en Windows 10 Home Edition.

- SDK de Windows 10 (versión más reciente)
- HoloLens, **modo de desarrollador habilitado**
- Visual Studio 2017.15.4 (solo se usa para acceder a Azure Cloud Explorer)
- Acceso a Internet para Azure y para el servicio de IoT Hub. Para obtener más información, siga este [vínculo a IOT Hub página de servicio](https://azure.microsoft.com/services/iot-hub/) .
- Un modelo de aprendizaje automático. Si no tiene su propio modelo listo para usar, [puede usar el modelo que se proporciona con este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- Software de **Hyper-V** habilitado en la máquina de desarrollo de Windows 10.
- Una máquina virtual que ejecuta Ubuntu (16,4 o 18,4), que se ejecuta en el equipo de desarrollo o, como alternativa, puede usar un equipo independiente que ejecute Linux (Ubuntu 16,4 o 18,4). Puede encontrar más información sobre cómo crear una máquina virtual en Windows con Hyper-V en el [capítulo "antes de empezar"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Antes de empezar

1. Configure y pruebe su HoloLens. Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup).
2. Es una buena idea realizar la **calibración** y el **ajuste del sensor** al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).

3. Configure la **máquina virtual de Ubuntu** con **Hyper-V**. Los siguientes recursos le ayudarán en el proceso.
    1.  En primer lugar, siga este vínculo para [descargar el ISO de Ubuntu 16.04.4 lts (Xenial Xerus)](https://au.releases.ubuntu.com/16.04/). Seleccione la **imagen de escritorio de PC de 64 bits (amd64)** .
    2.  Asegúrese de que **Hyper-V** está habilitado en el equipo con Windows 10. Puede seguir este vínculo para obtener instrucciones sobre la [instalación y habilitación de Hyper-V en Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Inicie Hyper-V y cree una nueva máquina virtual de Ubuntu. Puede seguir este vínculo para obtener una [Guía paso a paso sobre cómo crear una máquina virtual con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Cuando se le solicite **"instalar un sistema operativo desde un archivo de imagen de arranque"** , seleccione el **ISO de Ubuntu** que ha descargado anteriormente.

    > [!NOTE]
    > No se sugiere el uso de **creación rápida de Hyper-V** .  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capítulo 1: recuperar el modelo de Custom Vision

Con este curso, tendrá acceso a un [modelo de Custom Vision](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) predefinido que detecta teclados y ratones de las imágenes. Si usa esto, continúe con el [capítulo 2](#chapter-2---the-container-registry-service).

Sin embargo, puede seguir estos pasos si desea usar su propio modelo de Custom Vision:

1. En el **proyecto de Custom Vision** , vaya a la pestaña **rendimiento** .

    > [!WARNING]
    > El modelo debe usar un dominio *compacto* para exportar el modelo. Puede cambiar el dominio de modelos en la configuración del proyecto.

    ![pestaña rendimiento](images/AzureLabs-Lab313-01.png)

2. Seleccione la **iteración** que desea exportar y haga clic en **exportar**. Aparecerá una hoja.

    ![exportar hoja](images/AzureLabs-Lab313-02.png)

3. En la hoja, haga clic en **archivo de Docker**.

    ![seleccionar Docker](images/AzureLabs-Lab313-03.png)

4. Haga clic en **Linux** en el menú desplegable y, a continuación, haga clic en **Descargar**.

    ![Haga clic en descargar](images/AzureLabs-Lab313-04.png)

5. Descomprima el contenido. La usará más adelante en este curso.

## <a name="chapter-2---the-container-registry-service"></a>Capítulo 2: servicio de Container Registry

El **servicio Container Registry** es el repositorio que se usa para hospedar los contenedores.

El **servicio IOT Hub** que se va a compilar y usar en este curso hace referencia a **Container Registry servicio** para obtener los contenedores que se van a implementar en el dispositivo perimetral.

1. En primer lugar, siga este [vínculo a Azure portal](https://portal.azure.com/)e inicie sesión con sus credenciales.

2. Vaya a **crear un recurso** y busque **Container Registry**.

    ![registro de contenedor](images/AzureLabs-Lab313-05.png)

3. Haga clic en **crear**.

    ![](images/AzureLabs-Lab313-06.png)

4. Establezca los parámetros de instalación del servicio:

    1. Inserte un nombre para el proyecto, en este ejemplo, llamado **IoTCRegistry**.

    2. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

    3. Establezca la ubicación del servicio.

    4. Establezca el **usuario administrador** en **Habilitar**.

    5. Establezca **SKU** en **básico**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Haga clic en **crear** y espere a que se creen los servicios. 

6. Cuando aparezca la notificación que le informa de la creación correcta de la *Container Registry*, haga clic en **ir al recurso** para redirigirlo a la página del servicio.

    ![](images/AzureLabs-Lab313-08.png)

7. En la página servicio de *Container Registry* , haga clic en **claves de acceso**.

8. Tome nota (puede utilizar el Bloc de notas) de los siguientes parámetros:
    1. **Servidor de inicio de sesión**
    2. **Nombre**
    3. **Contraseña**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capítulo 3: servicio de IoT Hub

Ahora comenzará la creación y configuración del servicio de **IOT Hub**.

1. Si aún no ha iniciado sesión, inicie sesión en [Azure portal](https://portal.azure.com).

2.  Una vez iniciada la sesión, haga clic en **crear un recurso** en la esquina superior izquierda y busque **IOT Hub**y haga clic en **entrar**.

 ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab313-10.png)

3.  La nueva página proporcionará una descripción del servicio de la **cuenta de almacenamiento** . En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una instancia de este servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-11.png)

4.  Una vez que haya hecho clic en **crear**, aparecerá un panel:

    1. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

        > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Seleccione una **Ubicación** adecuada (use la misma ubicación en todos los servicios que cree en este curso).

    3. Inserte el **nombre** que desee para esta instancia de servicio.    

5.  En la parte inferior de la página, haga clic en **siguiente: tamaño y escala**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-12.png)

6.  En esta página, seleccione el **nivel de precios y de escala** (si se trata de la primera instancia de servicio de IOT Hub, debe estar disponible un nivel gratis).  

7.  Haga clic en **revisar y crear**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-13.png)

8.  Revise la configuración y haga clic en **crear**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-14.png)

9. Cuando aparezca la notificación que le informa de la creación correcta del servicio de *IOT Hub* , haga clic en **ir al recurso** para redirigirlo a la página del servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-15.png)

10. Desplácese por el panel lateral de la izquierda hasta que vea *Administración automática de dispositivos*, haga clic en **IOT Edge**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-16.png)

11. En la ventana que aparece a la derecha, haga clic en **agregar IOT Edge dispositivo**. Aparecerá una hoja a la derecha.

12. En la hoja, proporcione a su nuevo dispositivo un **identificador de dispositivo** (el nombre que prefiera). A continuación, haga clic en **Guardar**. Las claves *principal* y *secundaria* se generarán automáticamente, si se ha **generado automáticamente** una marca.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-17.png)

13. Volverá a la sección *dispositivos IOT Edge* , donde se mostrará el nuevo dispositivo. Haga clic en el nuevo dispositivo (descrito en rojo en la siguiente imagen). 

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-18.png)

14. En la página *detalles del dispositivo* que aparece, realice una copia de la cadena de **conexión** (clave principal).

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-19.png)

15. Vuelva al panel de la izquierda y haga clic en *directivas de acceso compartido*para abrirlo. 

16. En la página que aparece, haga clic en **iothubowner**y aparecerá una hoja a la derecha de la pantalla. 

17. Tome nota (en el Bloc de notas) de la **cadena de conexión** (clave principal), para usarla más adelante al establecer la *cadena de conexión* en el dispositivo.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capítulo 4: configurar el entorno de desarrollo

Para crear e implementar módulos para *IOT Hub Edge*, necesitará los siguientes componentes instalados en el equipo de desarrollo que ejecuta Windows 10:

1.  [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), le pedirá que cree una cuenta para poder descargar. 

    [![descargar Docker para Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker requiere *Windows 10 Pro*, *Enterprise 14393*o *Windows Server 2016 RTM*para ejecutarse. Si está ejecutando otras versiones de Windows 10, puede intentar instalar Docker con el cuadro de [herramientas de Docker](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3,6](https://www.python.org/downloads/).

    [![descargar Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (también conocido como vs Code)](https://code.visualstudio.com/download).

    [![descargar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Después de instalar el software mencionado anteriormente, deberá reiniciar el equipo.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capítulo 5: configuración del entorno de Ubuntu

Ahora puede continuar con la configuración del dispositivo **que ejecuta el sistema operativo Ubuntu**. Siga los pasos que se indican a continuación para instalar el software necesario para implementar los contenedores en el panel:

> [!IMPORTANT]
> Siempre debe preceder los comandos de terminal con **sudo** para que se ejecute como usuario administrador. es decir,
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Abra el **terminal Ubuntu**y use el siguiente comando para instalar **PIP**:

    > [! SUGERENCIA] puede abrir *terminal* fácilmente mediante el método abreviado de teclado: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  En este capítulo, es posible que el *terminal*le solicite permiso para usar el almacenamiento del dispositivo y que escriba y **/n** (sí o no), escriba **' y '** y, a continuación, presione la tecla **entrar** para aceptar.

3.  Una vez que se haya completado el comando, use el siguiente comando para instalar **rizo**:

    ```bash
        sudo apt install curl
    ```

4.  Una vez instalados **PIP** y **doblez** , use el siguiente comando para instalar el **IOT Edge en tiempo de ejecución**, que es necesario para implementar y controlar los módulos en el panel:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. En este momento se le pedirá que abra el archivo de *configuración en tiempo de ejecución*para insertar **la cadena de conexión del dispositivo**que anotó (en el Bloc de notas), al crear el servicio de **IOT Hub** ([en el paso 14, del capítulo 3](#chapter-3---the-iot-hub-service)). Ejecute la siguiente línea en el terminal para abrir el archivo:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. El archivo **config. yaml** se mostrará, listo para su edición:

    > [!WARNING]
    > Cuando se abre este archivo, puede ser algo confuso. Modificará el texto de este archivo, dentro del propio *terminal* . 

    1.  Use las teclas de flecha del teclado para desplazarse hacia abajo (tendrá que desplazarse hacia abajo) para llegar a la línea que contiene ":

        " **\<agregar la cadena de conexión del dispositivo aquí >** ".

    2. Línea de sustitución, **incluidos los corchetes**, con la **cadena de conexión del dispositivo** que anotó anteriormente.

7. Con la cadena de conexión en su lugar, en el teclado, presione las teclas **Ctrl + X** para guardar el archivo. Le pedirá que confirme si escribe **Y**. A continuación, presione la tecla **entrar** para confirmar. Regresará al *terminal*normal. 

8. Una vez que estos comandos se ejecuten correctamente, habrá instalado el **tiempo de ejecución de IOT Edge**. Una vez inicializado, el tiempo de ejecución se iniciará por sí mismo cada vez que se encienda el dispositivo y permanecerá en segundo plano, esperando a que los módulos se implementen desde el **servicio de IOT Hub**.

9.  Ejecute la siguiente línea de comandos para inicializar el *tiempo de ejecución de IOT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Si realiza cambios en el archivo. yaml o en la configuración anterior, deberá volver a ejecutar la línea de reinicio anterior en *terminal*.

10. Para comprobar el estado del *tiempo de ejecución de IOT Edge* , ejecute la siguiente línea de comandos. El tiempo de ejecución debe aparecer con el estado **activo (en ejecución)** en texto verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Presione las teclas **Ctrl + C** para salir de la página Estado. Para comprobar que el *tiempo de ejecución de IOT Edge* está extrayendo los contenedores, escriba el comando siguiente:

    ```bash
        sudo docker ps
    ```

12. Debe aparecer una lista con dos (2) contenedores. Estos son los módulos predeterminados que crea automáticamente el servicio IoT Hub (edgeAgent y edgeHub). Una vez que cree e implemente sus propios módulos, aparecerán en esta lista, debajo de los valores predeterminados.

## <a name="chapter-6---install-the-extensions"></a>Capítulo 6: instalación de las extensiones

> [!IMPORTANT]
> Los siguientes capítulos (6-9) se realizarán en el equipo con Windows 10.

1. Abra **vs Code**.

2. Haga clic en el botón **extensiones** (cuadrado) de la barra izquierda de vs code para abrir el **Panel extensiones**.

3. Busque e instale las extensiones siguientes (como se muestra en la imagen siguiente):

    1. Azure IoT Edge
    2. Kit de herramientas de IoT de Azure
    3. Docker   

    ![Creación de un contenedor](images/AzureLabs-Lab313-24.png)

4. Una vez instaladas las extensiones, cierre y vuelva a abrir VS Code.

5. Con VS Code abierto una vez más, vaya a **ver** > **terminal integrado**.

6. Ahora va a instalar **Cookiecutter**. En el terminal, ejecute el siguiente comando de Bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! SUGERENCIA] Si tiene problemas con este comando: 
    >1. Reinicie VS Code y/o el equipo.
    >2. Puede que sea necesario cambiar el **terminal de vs Code** por el que ha estado usando para instalar Python, es decir, **PowerShell** (especialmente en caso de que el entorno de Python ya esté instalado en el equipo). Con el terminal abierto, encontrará el menú desplegable en el lado derecho del terminal.
     ![crear el contenedor](images/AzureLabs-Lab313-24b.png) 
    >3. Asegúrese de que la ruta de instalación de **Python** se agrega como **variable de entorno** en la máquina. Cookiecutter debe formar parte de la misma ruta de acceso de ubicación. Siga este [vínculo para obtener más información sobre las variables de entorno](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx). 

7. Una vez que **Cookiecutter** haya finalizado la instalación, debe reiniciar el equipo para que **Cookiecutter** se reconozca como un comando, dentro del entorno del sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capítulo 7: creación de la solución de contenedor

En este punto, debe crear el contenedor, con el módulo, que se va a insertar en el *Container Registry*. Una vez que haya insertado el contenedor, usará el servicio *IOT Hub Edge* para implementarlo en el dispositivo, que ejecuta el *tiempo de ejecución de IOT Edge*.

1. En VS Code, haga clic en **ver** > **paleta de comandos**.

2. En la paleta, busque y ejecute **Azure IOT Edge: nueva solución de IOT Edge**.

3. Vaya a la ubicación en la que desea crear la solución. Presione la tecla **entrar** para aceptar la ubicación.

4. Asigne un nombre a la solución. Presione la tecla **entrar** para confirmar el nombre proporcionado.

5. Ahora se le pedirá que elija el marco de trabajo de la plantilla de la solución. Haga clic en **módulo de Python**. Presione la tecla **entrar** para confirmar esta opción.

6. Asigne un nombre al módulo. Presione la tecla **entrar** para confirmar el nombre del módulo. Asegúrese de tomar nota (con el Bloc de notas) del nombre del módulo, tal y como se usa más adelante.

7. Observará que aparecerá una dirección de *repositorio de imagen de Docker* pregenerada en la paleta. Tendrá el siguiente aspecto:

    **localhost: 5000/-el nombre del módulo:** . 

8. Elimine **localhost: 5000**y, en su lugar, inserte la *Container Registry* dirección del **servidor de inicio de sesión** , que anotó al crear el **servicio Container Registry** ([en el paso 8 del capítulo 2](#chapter-2---the-container-registry-service)). Presione la tecla **entrar** para confirmar la dirección.

9. En este momento, se creará la solución que contiene la plantilla para el módulo de Python y su estructura se mostrará en la **pestaña explorar**, de vs Code, en el lado izquierdo de la pantalla. Si la **pestaña explorar** no está abierta, puede abrirla haciendo clic en el botón de nivel superior, en la barra de la izquierda.

    ![Creación de un contenedor](images/AzureLabs-Lab313-25.png)

10. El último paso de este capítulo es hacer clic y abrir el **archivo. env**, desde la **pestaña explorar**, y agregar el **nombre de usuario** y la **contraseña**de *Container Registry* . Git omite este archivo, pero al compilar el contenedor, establecerá las credenciales para tener acceso al **servicio Container Registry**.

    ![Creación de un contenedor](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capítulo 8: edición de la solución de contenedor

Ahora completará la solución de contenedor mediante la actualización de los siguientes archivos:

- script de Python *<span></span>Main. py* .
- *requirements. txt*.
- *Deployment. template. JSON*.
- *Dockerfile. AMD64*

A continuación, creará la carpeta *images* , usada por el script de Python para comprobar que las imágenes coinciden con el *modelo de Custom Vision*. Por último, agregará el archivo *Labels. txt* , que le ayudará a leer el modelo y el archivo *Model. PB* , que es el modelo.

1. Con VS Code abierto, vaya a la carpeta del módulo y busque el script denominado **<span></span>Main. py**. Haga doble clic para abrirlo.

2. Elimine el contenido del archivo e inserte el código siguiente:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Abra el archivo denominado **requirements. txt**y sustituya su contenido por lo siguiente:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Abra el archivo denominado **Deployment. template. JSON**y sustituya su contenido por la siguiente directriz:

    1. Dado que tendrá su propia estructura JSON, única, tendrá que editarla manualmente (en lugar de copiar un ejemplo). Para facilitar esta tarea, use la imagen siguiente como guía.
    2. Las áreas que tendrán un aspecto distinto al suyo, pero que **no debe cambiar, se resaltan en amarillo**.
    3. **Las secciones que debe eliminar se resaltan en rojo.**
    4. Tenga cuidado de eliminar los corchetes correctos y, además, quite las comas.

        ![Creación de un contenedor](images/AzureLabs-Lab313-27.png)

    5. El JSON completado debe parecerse a la imagen siguiente (sin embargo, con las diferencias únicas: *nombre de usuario/contraseña/nombre de módulo/referencias de módulo*):

        ![Creación de un contenedor](images/AzureLabs-Lab313-28.png)

5.  Abra el archivo denominado **Dockerfile. AMD64**y sustituya su contenido por lo siguiente:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Haga clic con el botón secundario en la carpeta situada debajo de **módulos** (tendrá el nombre que proporcionó anteriormente; en el ejemplo más abajo, se denomina *pythonmodule*) y haga clic en **nueva carpeta**. Asigne a la carpeta el nombre **images**.

7.  Dentro de la carpeta, agregue algunas imágenes que contengan el mouse o el teclado. Serán las imágenes que se van a analizar con el modelo Tensorflow.

    > [!WARNING]
    > Si usa su propio modelo, tendrá que cambiarlo para reflejar sus propios datos de modelos.

8.  Ahora deberá recuperar los archivos **Labels. txt** y **Model. PB** de la carpeta del modelo, que antes descargó (o creó a partir de su propio **Custom Vision Service**), en el [capítulo 1](#chapter-1---retrieve-the-custom-vision-model). Una vez que tenga los archivos, colóquelos dentro de la solución, junto con los demás archivos. El resultado final debe ser similar a la imagen siguiente:

    ![Creación de un contenedor](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capítulo 9: empaquetar la solución como un contenedor

1.  Ahora está listo para "empaquetar" los archivos como un contenedor e insertarlos en el **Azure Container Registry**. En VS Code, abra el *terminal integrado* (**Ver** > **terminal integrado** o **Ctrl**+ **\`** ) y use la siguiente línea para iniciar sesión en **Docker** (sustituya los valores del comando por las credenciales de la **Azure Container Registry (ACR)** ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Haga clic con el botón derecho en el archivo **Deployment. template. JSON**y haga clic en **compilar IOT Edge solución**. Este proceso de compilación tarda bastante tiempo (dependiendo del dispositivo), por lo que debe estar preparado para esperar. Una vez finalizado el proceso de compilación, se creará un archivo **Deployment. JSON** en una nueva carpeta denominada **config**.

    ![crear implementación](images/AzureLabs-Lab313-30.png)

3. Vuelva a abrir la **paleta de comandos** y busque **Azure: Sign in**. Siga las indicaciones con las credenciales de su cuenta de Azure. VS Code le proporcionará una opción para *copiar y abrir*, que copiará el código del dispositivo que necesitará pronto y abrirá el explorador Web predeterminado. Cuando se le solicite, pegue el código del dispositivo para autenticar el equipo.

    ![copiar y abrir](images/AzureLabs-Lab313-31.png)

4. Una vez que haya iniciado sesión, observará que, en la parte inferior del panel de *exploración* , se trata de una nueva sección denominada **Azure IOT Hub dispositivos**. Haga clic en esta sección para expandirla.

    ![dispositivo perimetral](images/AzureLabs-Lab313-32.png)

5. Si el dispositivo no está aquí, tendrá que hacer clic con el botón derecho en *Azure IOT Hub dispositivos*y, a continuación, hacer clic en **establecer cadena de conexión de IOT Hub**. Después verá que la paleta de **comandos** (en la parte superior de vs Code) le pedirá que escriba la *cadena de conexión*. Esta es la *cadena de conexión* que anotó al final del [capítulo 3](#chapter-3---the-iot-hub-service). Presione la tecla **entrar** cuando haya copiado la cadena en.    

6. El dispositivo debe cargarse y aparecer. Haga clic con el botón derecho en el nombre del dispositivo y, a continuación, haga clic en **crear implementación para un único dispositivo**.

    ![crear implementación](images/AzureLabs-Lab313-33b.png)

7. Obtendrá un mensaje del *Explorador de archivos* , donde puede ir a la carpeta **config** y, a continuación, seleccionar el archivo **Deployment. JSON** . Con ese archivo seleccionado, haga clic en el botón **seleccionar manifiesto de implementación perimetral** .

    ![crear implementación](images/AzureLabs-Lab313-34.png)

8. Llegados a este punto, ha proporcionado su **servicio de IOT Hub** con el manifiesto para que implemente el contenedor, como un módulo, desde su **Azure Container Registry**, y lo implemente de forma eficaz en el dispositivo.

9. Para ver los mensajes enviados desde el dispositivo a la IoT Hub, vuelva a hacer clic con el botón derecho en el nombre del dispositivo en la sección **dispositivos Azure IOT Hub** , en el panel **Explorador** y haga clic en **iniciar supervisión del mensaje de D2C**. Los mensajes enviados desde el dispositivo deben aparecer en el terminal de VS. Sea paciente, ya que esto puede tardar algún tiempo. Vea el capítulo siguiente para la depuración y comprobar si la implementación se realizó correctamente.

Este módulo iterará ahora entre las imágenes de la carpeta **images** y las analizará con cada iteración. Obviamente, esto es solo una demostración de cómo obtener el modelo de aprendizaje automático básico para trabajar en un entorno de dispositivo IoT Edge. 

Para expandir la funcionalidad de este ejemplo, puede continuar de varias maneras. Una manera podría incluir código en el contenedor, que capture fotografías de una cámara web conectada al dispositivo y las guarde en la carpeta images. 

Otra manera podría ser copiar las imágenes del dispositivo IoT en el contenedor. Una manera práctica de hacerlo es ejecutar el siguiente comando en el terminal del dispositivo IoT (quizás una aplicación pequeña podría hacer el trabajo, si desea automatizar el proceso). Puede probar este comando si lo ejecuta manualmente desde la ubicación de la carpeta donde se almacenan los archivos:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capítulo 10: depurar el tiempo de ejecución de IoT Edge

A continuación se muestra una lista de líneas de comandos y sugerencias que le ayudarán a supervisar y depurar la actividad de mensajería del *tiempo de ejecución de IOT Edge*desde el **dispositivo Ubuntu**. 

- Para comprobar el estado del *tiempo de ejecución de IOT Edge* , ejecute la siguiente línea de comandos:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Recuerde presionar **Ctrl + C**para terminar de ver el estado.

- Enumerar los contenedores que están implementados actualmente. Si el *servicio IOT Hub* ha implementado los contenedores correctamente, se mostrarán ejecutando la siguiente línea de comandos:

    ```bash
        sudo iotedge list
    ```

    O bien

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Lo anterior es una buena manera de comprobar si el módulo se ha implementado correctamente, tal y como aparecerá en la lista. de lo contrario, **solo** verá *edgeHub* y *edgeAgent*.

- Para mostrar los registros de código de un contenedor, ejecute la siguiente línea de comandos:

    ```bash
        journalctl -u iotedge
    ```

**Comandos útiles para administrar el tiempo de ejecución de IoT Edge:**

-  Para eliminar todos los contenedores del host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Para detener el *tiempo de ejecución de IOT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capítulo 11: creación de un servicio tabla 

Vuelva a Azure portal, donde creará un servicio de tablas de Azure, mediante la creación de un recurso de almacenamiento.

1. Si aún no ha iniciado sesión, inicie sesión en [Azure portal](https://portal.azure.com).

2. Una vez que haya iniciado sesión, haga clic en **crear un recurso**, en la esquina superior izquierda, busque la **cuenta de almacenamiento**y presione la tecla **entrar** para iniciar la búsqueda.

3. Una vez que haya aparecido, haga clic en **cuenta de almacenamiento: BLOB, archivo, tabla, cola** en la lista.

    ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab313-35.png)

4. La nueva página proporcionará una descripción del servicio de la **cuenta de almacenamiento** . En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una instancia de este servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-36.png)

5. Una vez que haya hecho clic en **crear**, aparecerá un panel:

    1. Inserte el **nombre** que desee para esta instancia de servicio (*debe estar todo en minúsculas*).

    2. En **modelo de implementación**, haga clic en **Administrador de recursos**.

    3. En **tipo de cuenta**, en el menú desplegable, haga clic en **almacenamiento (uso general V1)** .

    4. Haga clic en una **Ubicación**adecuada.
    
    5. En el menú desplegable **replicación** , haga clic en **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .

    6. En **rendimiento**, haga clic en **estándar**.

    7. Dentro de la sección **transferencia segura requerida** , haga clic en **deshabilitado**.

    8. En el menú desplegable **suscripción** , haga clic en una suscripción adecuada.

    9. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

        > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deje **redes virtuales** como **deshabilitadas**si se trata de una opción.

    11. Haz clic en **Crear**.

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab313-37.png)

6. Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

7. Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal. Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab313-38.png)

8. Haga clic en el botón **ir a recurso** de la notificación y se le dirigirá a la página de información general de la nueva instancia del servicio de almacenamiento.

    ![ir al recurso](images/AzureLabs-Lab313-39.png)

9. En la página información general, en la parte derecha, haga clic en **tablas**.
    
    ![Tablas](images/AzureLabs-Lab313-40.png)

10. El panel de la derecha cambiará para mostrar la información del **servicio tabla** , en la que es necesario agregar una nueva tabla. Para ello, haga clic en el botón **+ tabla** en la esquina superior izquierda.

    ![abrir tablas](images/AzureLabs-Lab313-41.png)

11. Se mostrará una nueva página, en la que es necesario escribir un **nombre de tabla**. Este es el nombre que usará para hacer referencia a los datos de la aplicación en capítulos posteriores (creación de Function App y Power BI). Inserte **IoTMessages** como nombre (puede elegir el suyo propio, simplemente Recuerde que cuando se usa más adelante en este documento) y haga clic en **Aceptar**. 

12. Una vez creada la nueva tabla, podrá verla en la página **Table Service** (en la parte inferior).

    ![nueva tabla creada](images/AzureLabs-Lab313-42.png)  

13. Ahora, haga clic en **claves de acceso** y tome una copia del nombre y la **clave** de la **cuenta de almacenamiento** (con el Bloc de notas). estos valores se usarán más adelante en este curso, al crear el function App de **Azure**.

    ![nueva tabla creada](images/AzureLabs-Lab313-43.png) 

14. Vuelva a usar el panel de la izquierda, desplácese hasta la sección *Table Service* y haga clic en **tables** ( **examinar tablas**, en portales más recientes) y realice una copia de la **dirección URL** de la tabla (con el Bloc de notas). Usará este valor más adelante en este curso, al vincular la tabla a la aplicación **Power BI** .

    ![nueva tabla creada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capítulo 12: completar la tabla de Azure

Ahora que se ha configurado la cuenta de almacenamiento de **Table Service** , es el momento de agregar datos a ella, que se usará para almacenar y recuperar información. La edición de las tablas se puede realizar a través de **Visual Studio**.

1. Abra **Visual Studio** (**no** Visual Studio Code).

2. En el menú, haga clic en **ver** > **Cloud Explorer**.

    ![Abra Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. El **Cloud Explorer** se abrirá como un elemento acoplado (sea paciente, ya que la carga puede tardar tiempo).

    > [!WARNING] 
    > Si la suscripción que usó para crear las *cuentas de almacenamiento* no es visible, asegúrese de que tiene: 
    > - Ha iniciado sesión en la misma cuenta que la que usó para Azure portal.
    > - Seleccionó su suscripción desde la página de administración de cuentas (puede que tenga que aplicar un filtro de la configuración de la cuenta):  
    >
    >   ![buscar suscripción](images/AzureLabs-Lab313-46.png)

4. Se mostrarán los servicios en la nube de Azure. Busque **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de ella para expandir sus cuentas.

    ![abrir cuentas de almacenamiento](images/AzureLabs-Lab313-47.png)

5. Una vez expandida, la **cuenta de almacenamiento** recién creada debe estar disponible. Haga clic en la flecha situada a la izquierda de su almacenamiento y, después, una vez expandida, busque **tablas** y haga clic en la flecha situada junto a ella para mostrar la **tabla** que ha creado en el último capítulo. Haga doble clic en la **tabla**.

6. La tabla se abrirá en el centro de la ventana de Visual Studio. Haga clic en el icono de la tabla con la **+** (más).

    ![Agregar nueva tabla](images/AzureLabs-Lab313-48.png)

7. Aparecerá una ventana que le solicitará que *agregue la entidad*. Solo creará una entidad, aunque tendrá tres propiedades. Observará que *PartitionKey* y *RowKey* ya se han proporcionado, ya que se usan en la tabla para buscar los datos. 

    ![partición y clave de fila](images/AzureLabs-Lab313-49.png)

8. Actualice los siguientes valores:

    - Nombre: **PartitionKey**, valor: **PK_IoTMessages** 

    - Nombre: **RowKey**, valor: **RK_1_IoTMessages** 

9. A continuación, haga clic en **Agregar propiedad** (en la esquina inferior izquierda de la ventana *Agregar entidad* ) y agregue la siguiente propiedad:

    - **MessageContent**, como una *cadena*, deje el valor vacío.

10. La tabla debe coincidir con la de la imagen siguiente:

    ![agregar valores correctos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > La razón por la que la entidad tiene el número 1 en la clave de fila, es que es posible que desee agregar más mensajes, en caso de que desee experimentar con este curso.

11. Cuando haya terminado, haga clic en **Aceptar** . La tabla ya está lista para usarse.

## <a name="chapter-13---create-an-azure-function-app"></a>Capítulo 13: creación de una Function App de Azure 

Ahora es el momento de crear una *function App de Azure*, a la que llamará *el servicio IOT Hub* para almacenar los mensajes de dispositivo *IOT Edge* en el servicio **tabla** , que creó en el capítulo anterior.

En primer lugar, debe crear un archivo que permita que la función de Azure cargue las bibliotecas que necesita.

1.  Abra el **Bloc de notas** (Presione la *tecla Windows*y escriba *Notepad*).

    ![abrir el Bloc de notas](images/AzureLabs-Lab313-51.png)

2.  Con el Bloc de notas abierto, inserte la siguiente estructura JSON en él. Una vez hecho esto, guárdelo en el escritorio como **Project. JSON**. Este archivo define las bibliotecas que utilizará la función. Si ha usado NuGet, le resultará familiar.
    
    > [!WARNING]
    > Es importante que la nomenclatura sea correcta; Asegúrese de que **no tiene una extensión de archivo. txt** . Vea la siguiente referencia:
    >
    > ![Guardado de JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

4.  Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda y busque **function App**y presione la tecla **entrar** para buscar. Haga clic en *function App* de los resultados para abrir un nuevo panel.

    ![búsqueda de function App](images/AzureLabs-Lab313-53.png)

5.  El nuevo panel proporcionará una descripción del servicio **function App** . En la parte inferior izquierda de este panel, haga clic en el botón **crear** para crear una asociación con este servicio.

    ![instancia de la aplicación de función](images/AzureLabs-Lab313-54.png)

6.  Una vez que haya hecho clic en **crear**, rellene lo siguiente:

    1. En **nombre**de la aplicación, inserte el nombre que desee para esta instancia de servicio.

    2. Seleccione una **suscripción**.

    3. Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un **servicio de function App**, debe estar disponible un nivel gratis.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).

        > Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. En el caso de **sistemas operativos**, haga clic en Windows, ya que es la plataforma prevista.

    6. Seleccione un **plan de hospedaje** (este tutorial usa un **plan de consumo**.

    7. Seleccione una **Ubicación** (elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)

    8. En la sección **almacenamiento** , **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.

    9. No necesitará *Application Insights* en esta aplicación, así que no dude en dejarlo **fuera**de servicio.

    10. Haz clic en **Crear**.

        ![crear nueva instancia](images/AzureLabs-Lab313-55.png)

7.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

8.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación](images/AzureLabs-Lab313-56.png)

9.  Haga clic en la notificación, una vez que la implementación sea correcta (ha finalizado).

10. Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio. 

    ![ir al recurso](images/AzureLabs-Lab313-57.png)

11. En el lado izquierdo del nuevo panel, haga clic en el icono de **+** (más) situado junto a *funciones*para crear una nueva función.

    ![Agregar nueva función](images/AzureLabs-Lab313-58.png)

12. En el panel central, aparecerá la ventana de creación de la **función** . Desplácese hacia abajo y haga clic en **función personalizada**.

    ![función personalizada](images/AzureLabs-Lab313-59.png)

13. Desplácese hacia abajo en la página siguiente hasta que encuentre **IOT Hub (centro de eventos)** y haga clic en él.

    ![función personalizada](images/AzureLabs-Lab313-60.png)

14. En la hoja **IOT Hub (centro de eventos)** , establezca el **idioma** en **C#** y, a continuación, haga clic en **nuevo**.

    ![función personalizada](images/AzureLabs-Lab313-61.png)

15. En la ventana que aparecerá, asegúrese de que está seleccionado **IOT Hub** y de que el nombre del campo de *IOT Hub* corresponde al nombre del *servicio de IOT Hub* que ha creado anteriormente (en el[paso 8, del capítulo 3](#chapter-3---the-iot-hub-service)). A continuación, haga clic en el botón **seleccionar** .

    ![función personalizada](images/AzureLabs-Lab313-62.png)

16. De nuevo en la hoja **IOT Hub (centro de eventos)** , haga clic en **crear**.

    ![función personalizada](images/AzureLabs-Lab313-63.png)

17. Se le redirigirá al editor de funciones.

    ![función personalizada](images/AzureLabs-Lab313-64.png)

18. Elimine todo el código que contiene y reemplácelo por lo siguiente:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Cambie las siguientes variables para que se correspondan con los valores adecuados (valores de**tabla** y **almacenamiento** , del [paso 11 y 13, respectivamente, del capítulo 11](#chapter-11---create-table-service)), que encontrará en la **cuenta de almacenamiento**:

    - **TableName**, con el nombre de la **tabla** que se encuentra en la **cuenta de almacenamiento**.
    - **tableURL**, con la dirección URL de la **tabla** que se encuentra en la **cuenta de almacenamiento**.
    - **storageAccountName**, con el nombre del valor que corresponde al nombre de su **cuenta de almacenamiento** .
    - **storageAccountKey**, con la clave que ha obtenido en el servicio de almacenamiento que ha creado anteriormente.

    ![función personalizada](images/AzureLabs-Lab313-65.png)

20. Con el código en su lugar, haga clic en **Guardar**.

21. A continuación, haga clic en el icono de **\<** (flecha) situado en el lado derecho de la página.

    ![función personalizada](images/AzureLabs-Lab313-66.png)

22. Un panel se deslizará hacia la derecha. En ese panel, haga clic en **cargar**y aparecerá un *Explorador de archivos* .

23. Vaya a y haga clic en el archivo **Project. JSON** , que ha creado anteriormente en el **Bloc de notas** y, a continuación, haga clic en el botón **abrir** . Este archivo define las bibliotecas que utilizará la función.

    ![función personalizada](images/AzureLabs-Lab313-67.png)

24. Cuando se haya cargado el archivo, aparecerá en el panel de la derecha. Al hacer clic en él se abrirá en el editor de **funciones** . Debe tener **exactamente** el mismo aspecto que la siguiente imagen.

    ![función personalizada](images/AzureLabs-Lab313-68.png)

25. En este momento, sería conveniente probar la funcionalidad de la función para almacenar el mensaje en la *tabla*. En el lado superior derecho de la ventana, haga clic en **prueba**.

    ![función personalizada](images/AzureLabs-Lab313-69.png)

26. Inserte un mensaje en el **cuerpo**de la solicitud, tal como se muestra en la imagen anterior, y haga clic en **Ejecutar**. 

27. La función se ejecutará y mostrará el estado del resultado (verá el **estado verde 202 aceptado**, encima de la ventana de *salida* , lo que significa que se trata de una llamada correcta):

    ![resultado de salida](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capítulo 14: ver los mensajes activos

Si ahora abre Visual Studio (**no** Visual Studio Code), puede visualizar el resultado del mensaje de prueba, ya que se almacenará en el área de la cadena *MessageContent* .

![función personalizada](images/AzureLabs-Lab313-71.png)

Con el servicio tabla y Function App en su lugar, los mensajes del dispositivo Ubuntu aparecerán en la tabla *IoTMessages* . Si aún no se está ejecutando, vuelva a iniciar el dispositivo y podrá ver los mensajes de resultado desde el dispositivo, y el módulo, dentro de la tabla, mediante el uso de Visual Studio *Cloud Explorer*.

![visualizar datos](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capítulo 15: configuración de Power BI

Para visualizar los datos del dispositivo IOT, configurará **Power BI** (versión de escritorio) para recopilar los datos del servicio *tabla* , que acaba de crear. La versión de *HoloLens* de Power BI usará los datos para visualizar el resultado.

1.  Abra el Microsoft Store en Windows 10 y busque **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Descargue la aplicación. Una vez finalizada la descarga, ábrala.

3.  Inicie sesión en *Power BI* con su **cuenta de Microsoft 365**. Puede que se le redirija a un explorador para suscribirse. Una vez que se haya registrado, vuelva a la aplicación Power BI e inicie sesión de nuevo.

4.  Haga clic en **obtener datos** y, a continuación, haga clic en **más..** ..

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Haga clic en **Azure**, **Azure Table Storage**y, a continuación, haga clic en **conectar**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Se le pedirá que inserte la **dirección URL** de la tabla que recopiló anteriormente ([en el paso 13 del capítulo 11](#chapter-11---create-table-service)) al crear el servicio tabla. Después de insertar la dirección URL, elimine la parte de la ruta de acceso que hace referencia a la tabla "subcarpeta" (que se IoTMessages en este curso). El resultado final debe ser como se muestra en la imagen siguiente. A continuación, haga clic en **Aceptar**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Se le pedirá que inserte la **clave de almacenamiento** que anotó (en el[paso 11 del capítulo 11](#chapter-11---create-table-service)) antes de crear el Table Storage. A continuación, haga clic en **conectar**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Se mostrará un **Panel de navegación** , marque el cuadro situado junto a la tabla y haga clic en **cargar**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. La tabla ya se ha cargado en Power BI, pero requiere una consulta para mostrar los valores en ella. Para ello, haga clic con el botón secundario en el nombre de la tabla que se encuentra en el **Panel campos** , en el lado derecho de la pantalla. A continuación, haga clic en **Editar consulta**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Se abrirá un **Editor de Power Query** como una nueva ventana que muestra la tabla. Haga clic en el **registro** de palabra dentro de la columna *contenido* de la tabla para visualizar el contenido almacenado.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Haga clic en en la **tabla**, en la parte superior izquierda de la ventana. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Haga clic en **cerrar & aplicar**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Una vez que haya finalizado la carga de la consulta, en el **Panel campos**, en el lado derecho de la pantalla, marque las casillas correspondientes al **nombre** y el **valor**de los parámetros para visualizar el contenido de la columna **MessageContent** .

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Haga clic en el **icono de disco azul** situado en la parte superior izquierda de la ventana para guardar el trabajo en una carpeta de su elección.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Ahora puede hacer clic en el botón publicar para cargar la tabla en el área de trabajo. Cuando se le solicite, haga clic en **mi área de trabajo** y haga clic en *seleccionar*. Espere a que se muestre el resultado correcto del envío.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> El siguiente capítulo es específico de HoloLens. Power BI no está disponible actualmente como aplicación envolvente, pero puede ejecutar la versión de escritorio en el portal de Windows Mixed Reality (también conocido como acantilado House) a través de la aplicación de escritorio.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capítulo 16: visualización de datos de Power BI en HoloLens

1. En HoloLens, inicie sesión en el **Microsoft Store**; para ello, puntee en su icono en la lista de aplicaciones.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Busque y, a continuación, descargue la aplicación **Power BI** .

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Inicie **Power BI** desde la lista de aplicaciones. 

4. **Power BI** podría pedirle que inicie sesión en su **cuenta de Microsoft 365**.

5. Una vez dentro de la aplicación, el área de trabajo se debe mostrar de forma predeterminada, tal como se muestra en la imagen siguiente. Si esto no ocurre, simplemente haga clic en el icono del área de trabajo en el lado izquierdo de la ventana.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Su aplicación IoT Hub finalizada

Enhorabuena, ha creado correctamente un servicio IoT Hub con un dispositivo perimetral de máquina virtual simulado. El dispositivo puede comunicar los resultados de un modelo de machine learning a un servicio tabla de Azure, facilitado por una Function App de Azure, que se lee en Power BI y se visualiza en una de Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonus

### <a name="exercise-1"></a>Ejercicio 1

Expanda la estructura de mensajería almacenada en la tabla y mostrarla como un gráfico. Es posible que desee recopilar más datos y almacenarlos en la misma tabla para que se muestren más adelante.

### <a name="exercise-2"></a>Ejercicio 2

Cree un módulo de "captura de cámara" adicional para implementarlo en el panel de IoT, de modo que pueda capturar imágenes a través de la cámara para su análisis.
