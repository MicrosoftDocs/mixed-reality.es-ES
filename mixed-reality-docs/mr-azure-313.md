---
title: El Sr. y 313 - servicio IoT Hub de Azure
description: Complete este curso para obtener información sobre cómo implementar el servicio Azure IoT Hub en una máquina virtual con Ubuntu 16.4 y, a continuación, visualizar los datos del mensaje utilizando Microsoft HoloLens o auriculares para envolventes (VR).
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, edge, iot edge, tutorial, api, notificaciones, funciones, tablas, envolventes, hololens, vr, iot, máquina virtual, ubuntu, python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597568"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

# <a name="mr-and-azure-313-iot-hub-service"></a>El Sr. y Azure 313: Servicio IoT Hub

![resultado del curso](images/AzureLabs-Lab313-00.png)

En este curso, obtendrá información sobre cómo implementar un **servicio Azure IoT Hub** en una máquina virtual ejecuta el sistema operativo Ubuntu 16.4. Un **Azure Function App** , a continuación, se utilizará para recibir mensajes de la VM de Ubuntu y almacenar el resultado dentro de un **Azure Table Service**. A continuación, podrá ver estos datos mediante **Power BI** en Microsoft HoloLens o envolventes auriculares (VR).

El contenido de este curso *es aplicable* en dispositivos de IoT Edge, aunque con el propósito de este curso, el foco estará en un entorno de máquina virtual, por lo que no es necesario el acceso a un dispositivo físico de Edge.

Al terminar este curso, obtendrá información sobre cómo:

- Implementar un **módulo IoT Edge** a una máquina Virtual (Ubuntu 16 SO), que representa el dispositivo de IoT.
- Agregar un **modelo de Tensorflow Azure Custom Vision** para el módulo de Edge con código que analizará las imágenes almacenadas en el contenedor.
- Configurar el módulo para enviar el mensaje de resultado del análisis a su **servicio IoT Hub**.
- Use un **Azure Function App** para almacenar el mensaje dentro de un **Azure Table**.
- Configurar **Power BI** para recopilar el mensaje almacenado y crear un informe.
- Visualizar los datos de mensajes de IoT en **Power BI**.

Los servicios que se va a utilizar incluyen:

- **Azure IoT Hub** es un servicio de Azure de Microsoft que permite a los desarrolladores a conectar, supervisar y administrar recursos de IoT. Para obtener más información, visite la [ **servicio Azure IoT Hub** página](https://azure.microsoft.com/en-au/services/iot-hub/).

- **Azure Container Registry** es un servicio de Azure de Microsoft que permite a los desarrolladores almacenar imágenes de contenedor, para varios tipos de contenedores. Para obtener más información, visite la [ **del registro de Azure Container Service** página](https://azure.microsoft.com/en-au/services/container-registry/).

- **Azure Function App** es un servicio de Microsoft Azure, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure. Esto proporciona una manera para delegar el trabajo a la nube, en lugar de la aplicación local, lo que puede tener muchas ventajas. **Las funciones de Azure** admite varios lenguajes de desarrollo, incluidos C\#, F\#, Node.js, Java y PHP. Para obtener más información, visite la [ **Azure Functions** página](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Almacenamiento de Azure: Las tablas** es una Microsoft Azure Service que permite a los desarrolladores almacenar estructurado, que no sea de SQL, los datos en la nube, lo que sea fácilmente accesible en cualquier lugar. El servicio cuenta con un diseño sin esquema, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible. Para obtener más información, visite la [ **Azure Tables** página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Este curso le mostrará cómo configurar y usar el servicio IoT Hub y, a continuación, visualizar una respuesta de un dispositivo. Será quien decide estos conceptos se aplican a una configuración personalizada del servicio IoT Hub, que puede que esté creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 313: Servicio IoT Hub</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

Para los requisitos previos más recientes para el desarrollo con la realidad mixta, incluidos con el Microsoft HoloLens, visite la [instalar las herramientas de](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) artículo.

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica en Python. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente de la que figura a continuación.

Se requiere el siguiente hardware y software:

- Windows 10 Fall Creators Update (o posterior), **habilitado el modo de programador**

    > [!WARNING]
    > No se puede ejecutar una máquina Virtual mediante Hyper-V en Windows 10 Home Edition.

- Windows 10 SDK (última versión)
- A HoloLens, **habilitado el modo de programador**
- Visual Studio 2017.15.4 (sólo se utiliza para tener acceso al explorador en la nube de Azure)
- Acceso a Internet para Azure y para el servicio IoT Hub. Para obtener más información, siga este [vínculo a la página de servicio IoT Hub](https://azure.microsoft.com/en-au/services/iot-hub/)
- Un modelo de aprendizaje automático. Si no tiene sus propias listas para usar el modelo, [puede usar el modelo proporcionado con este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Hyper-V** software habilitado en el equipo de desarrollo de Windows 10.
- Una máquina Virtual con Ubuntu (16.4 o 18.4), en ejecución en el equipo de desarrollo o de forma alternativa puede usar un equipo independiente que ejecuta Linux (Ubuntu 16.4 o 18.4). Puede encontrar más información sobre cómo crear una máquina virtual en Windows con Hyper-V en el ["Antes de empezar" capítulo](#before-you-start). () https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Antes de empezar

1. Configurar y probar su HoloLens. Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).
2. Es una buena idea realizar **calibración** y **optimización Sensor** cuando comienza a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar dichas tareas para cada usuario).

Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).

Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).

3. Configurar su **Máquina Virtual Ubuntu** mediante **Hyper-V**. Los siguientes recursos le ayudará con el proceso.
    1.  En primer lugar, siga este vínculo para [Descargue el archivo ISO (Xenial Xerus) LTS de Ubuntu 16.04.4](http://au.releases.ubuntu.com/16.04/). Seleccione el **imagen de escritorio de PC (AMD64) de 64 bits**.
    2.  Asegúrese de que **Hyper-V** está habilitada en el equipo de Windows 10. Puede seguir este vínculo para obtener instrucciones sobre [instalar y habilitar Hyper-V en Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Inicie Hyper-V y crear una nueva VM de Ubuntu. Puede seguir este vínculo para ver un [guía paso a paso sobre cómo crear una máquina virtual con Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Cuando se solicita a **"Instalar un sistema operativo desde un archivo de imagen de arranque"**, seleccione el **ISO de Ubuntu** tiene descarga anterior.

    > [!NOTE]
    > Uso de **creación rápida de Hyper-V** no se recomienda.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capítulo 1: recuperar el modelo de Custom Vision

Con este curso tendrá acceso a un [pregenerado modelo Custom Vision](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) que detecta teclados y mouse a partir de imágenes. Si utiliza esto, continúe con [capítulo 2](#chapter-2---the-container-registry-service).

Sin embargo, puede seguir estos pasos si desea utilizar su propio modelo de visión personalizada:

1. En su **Custom Vision proyecto** vaya a la **rendimiento** ficha.

    > [!WARNING]
    > Debe usar el modelo un *compact* dominio, para exportar el modelo. Puede cambiar el dominio de los modelos en la configuración del proyecto.

    ![pestaña rendimiento](images/AzureLabs-Lab313-01.png)

2. Seleccione el **iteración** que desea exportar y haga clic en **exportar**. Aparecerá una hoja.

    ![hoja de exportación](images/AzureLabs-Lab313-02.png)

3. En la hoja, haga clic en **Docker archivo**.

    ![Seleccione docker](images/AzureLabs-Lab313-03.png)

4. Haga clic en **Linux** en el menú desplegable y, a continuación, haga clic en **descargar**.

    ![Haga clic en descargar](images/AzureLabs-Lab313-04.png)

5. Descomprima el contenido. La usará más adelante en este curso.

## <a name="chapter-2---the-container-registry-service"></a>Capítulo 2: el servicio de registro de contenedor

El **servicio de registro de contenedor** es el repositorio que se utiliza para hospedar los contenedores.

El **servicio IoT Hub** que va a crear y usar en este curso, se refiere a **servicio de registro de contenedor** para obtener los contenedores para implementar en el dispositivo de Edge.

1. En primer lugar, siga este [vínculo al Portal de Azure](https://portal.azure.com/)e inicie sesión con sus credenciales.

2. Vaya a **crear un recurso** y busque **Container Registry**.

    ![registro de contenedor](images/AzureLabs-Lab313-05.png)

3. Haga clic en **crear**.

    ![](images/AzureLabs-Lab313-06.png)

4. Establecer el servicio de los parámetros de instalación:

    1. Insertar un nombre para el proyecto, en este ejemplo se llama **IoTCRegistry**.

    2. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionamiento y administrar, de facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

    3. Establezca la ubicación del servicio.

    4. Establecer **usuario Admin** a **habilitar**.

    5. Establecer **SKU** a **básica**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Haga clic en **crear** y espere a que los servicios que se va a crearse. 

6. Una vez que la notificación emergente que le informa de la creación correcta de la *Container Registry*, haga clic en **ir al recurso** se redirijan a la página del servicio.

    ![](images/AzureLabs-Lab313-08.png)

7. En el *Container Registry* página de servicios, haga clic en **claves de acceso**.

8. Tenga en cuenta (podría usar el Bloc de notas) de los parámetros siguientes:
    1. **Servidor de inicio de sesión**
    2. **Nombre de usuario**
    3. **Contraseña**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capítulo 3: el servicio IoT Hub

Ahora se iniciará la creación y configuración de su **servicio IoT Hub**.

1. Si no ha iniciado sesión, inicie sesión en el [Portal de Azure](https://portal.azure.com).

2.  Una vez iniciada la sesión, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque **IoT Hub**y haga clic en **ENTRAR**.

 ![Busque la cuenta de almacenamiento](images/AzureLabs-Lab313-10.png)

3.  La nueva página proporcionará una descripción de la **cuenta de almacenamiento** Service. En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una instancia de este servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-11.png)

4.  Una vez que ha hecho clic **crear**, aparecerá un panel:

    1. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Seleccione un **ubicación** (usar la misma ubicación para todos los servicios que cree en este curso).

    3. Insertar el elemento **nombre** para esta instancia de servicio.    

5.  En la parte inferior de la página, haga clic en **siguiente: Tamaño y escala**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-12.png)

6.  En esta página, seleccione su **nivel de precios y escala** (si se trata de la primera instancia de servicio IoT Hub, un nivel gratuito debe estar disponible para usted).  

7.  Haga clic en **revisar y crear**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-13.png)

8.  Revise la configuración y haga clic en **crear**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-14.png)

9. Una vez que la notificación emergente que le informa de la creación correcta de la *IoT Hub* servicio, haga clic en **ir al recurso** se redirijan a la página del servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-15.png)

10. Desplácese al panel lateral de la izquierda hasta que vea *administración automática de dispositivos*, haga clic en **IoT Edge**.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-16.png)

11. En la ventana que aparece a la derecha, haga clic en **Agregar dispositivo de IoT Edge**. Aparecerá una hoja a la derecha.

12. En la hoja, proporcione el nuevo dispositivo un **Id. de dispositivo** (un nombre de su elección). A continuación, haga clic en **guardar**. El *principal* y *claves secundarias* automática generará, si tiene **Autogenerar** activada.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-17.png)

13. Se desplazará hasta el *dispositivos de IoT Edge* sección, donde se mostrará el nuevo dispositivo. Haga clic en el nuevo dispositivo (destacados en rojo en la imagen siguiente). 

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-18.png)

14. En el *detalles del dispositivo* página que aparece, realice una copia de la **cadena de conexión** (clave principal).

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-19.png)

15. Vuelva al panel de la izquierda y haga clic en *directivas de acceso compartido*, para abrirlo. 

16. En la página que aparece, haga clic en **iothubowner**, y aparecerá una hoja a la derecha de la pantalla. 

17. Tome nota (en el Bloc de notas) de la **cadena de conexión** (clave principal), para su uso posterior cuando se establece la *cadena de conexión* al dispositivo.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capítulo 4: configurar el entorno de desarrollo

Para crear e implementar los módulos para *centro de IoT Edge*, necesita los siguientes componentes instalados en el equipo de desarrollo que ejecutan Windows 10:

1.  [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), le pedirá que cree una cuenta para poder descargar. 

    [![descarga de docker para windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Requiere docker *Windows 10 PRO*, *Enterprise 14393*, o *Windows Server 2016 RTM*, para ejecutar. Si está ejecutando otras versiones de Windows 10, puede intentar instalar Docker mediante el [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3.6](https://www.python.org/downloads/).

    [![Descargar python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Código de Visual Studio (también conocido como VS Code)](https://code.visualstudio.com/download).

    [![Descargar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Después de instalar el software que se mencionó anteriormente, deberá reiniciar el equipo.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capítulo 5: configurar el entorno de Ubuntu

Ahora puede pasar a la configuración del dispositivo **con el sistema operativo Ubuntu**. Siga los pasos siguientes para instalar el software necesario para implementar los contenedores en el panel:

> [!IMPORTANT]
> Siempre debe preceder a los comandos de terminales por **sudo** para ejecutarse como usuario administrador. i.e:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Abra el **Ubuntu Terminal**y use el siguiente comando para instalar **pip**:

    > [! Sugerencia] puede abrir *Terminal* muy fácilmente a través del uso el método abreviado de teclado: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  A lo largo de este capítulo, se le pedirá, por *Terminal*, permiso usar el almacenamiento del dispositivo y para que escriba **y/n** (Sí o no), tipo **'y'** y, a continuación, presione el **ENTRAR** clave, para Aceptar.

3.  Una vez que se haya completado ese comando, use el siguiente comando para instalar **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Una vez **pip** y **curl** están instaladas, use el siguiente comando para instalar el **en tiempo de ejecución de IoT Edge**, esto es necesario para implementar y los módulos en el panel de control:

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

5. En este momento se le indicará que abrirán la *archivo de configuración en tiempo de ejecución*, para insertar el **Device Connection String**, que ha anotado (en el Bloc de notas), al crear el **servicio IoT Hub**  ([en el paso 14, del capítulo 3](#chapter-3---the-iot-hub-service)). Ejecute la siguiente línea en el terminal para abrir el archivo:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. El **config.yaml** archivo será mostrado, listo para editar:

    > [!WARNING]
    > Cuando se abre este archivo, puede ser un poco confusa. Puede editar este archivo, dentro del texto del *Terminal* propio. 

    1.  Use las teclas de flecha del teclado para desplazarse hacia abajo (deberá desplazarse un poco hacia abajo), para llegar a la línea que contiene ":

        "**\<AGREGUE AQUÍ LA CADENA DE CONEXIÓN DE DISPOSITIVO &GT;**".

    2. Sustituya la línea, **incluidos los corchetes**, con el **Device Connection String** haya anotado anteriormente.

7. Con la cadena de conexión en su lugar, en el teclado, presione el **Ctrl-X** claves para guardar el archivo. Se le pedirá que confirme escribiendo **Y**. A continuación, presione el **ENTRAR** clave, para confirmar. Volverá a la normal *Terminal*. 

8. Una vez que estos comandos todos ejecutaron correctamente, habrá instalado el **en tiempo de ejecución de IoT Edge**. Una vez inicializado, el tiempo de ejecución se iniciará en su propio cada vez que el dispositivo está encendido y se asienta en segundo plano, esperando módulos implementarse desde el **servicio IoT Hub**.

9.  Ejecute la siguiente línea de comandos para inicializar el *en tiempo de ejecución de IoT Edge*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Si realiza cambios en el archivo .yaml o la configuración anterior, necesitará volver a ejecutar la línea anterior de reinicio, dentro de *Terminal*.

10. Compruebe el *en tiempo de ejecución de IoT Edge* estado ejecutando la siguiente línea de comandos. El tiempo de ejecución debe aparecer con el estado **activas (en ejecución)** en texto verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Presione el **Ctrl-C** claves, para salir de la página de estado. Puede comprobar que la *en tiempo de ejecución de IoT Edge* está extrayendo los contenedores correctamente escribiendo el comando siguiente:

    ```bash
        sudo docker ps
    ```

12. Debe aparecer una lista con los contenedores de dos (2). Estos son los módulos predeterminados que se crean automáticamente por el servicio IoT Hub (edgeAgent y edgeHub). Una vez que cree e implemente sus propios módulos, aparecen en esta lista, debajo de los valores predeterminados.

## <a name="chapter-6---install-the-extensions"></a>Capítulo 6: instalar las extensiones

> [!IMPORTANT]
> Los capítulos siguientes (6-9) que se van a realizar en el equipo de Windows 10.

1. Abra **Vscode**.

2. Haga clic en el **extensiones** botón (cuadrado) en el izquierdo barra de VS Code, para abrir el **panel extensiones**.

3. Busque e instale, las siguientes extensiones (como se muestra en la imagen siguiente):

    1. Azure IoT Edge
    2. El Kit de herramientas de Azure IoT
    3. Docker   

    ![Creación del contenedor](images/AzureLabs-Lab313-24.png)

4. Una vez que se instalan las extensiones, cierre y vuelva a abrir VS Code.

5. Con VS Code, abra una vez más, vaya a **Ver > terminal integrado**.

6. Ahora instalará **Cookiecutter**. En el terminal, ejecute el siguiente comando de bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Sugerencia] Si tienes algún problema con este comando: 
    >1. Reinicie VS Code, o el equipo.
    >2. Podría ser necesario cambiar el **Terminal de VS Code** a la que se ha usado para instalar Python, es decir, **Powershell** (especialmente si el entorno de Python instalado en el equipo). Con el Terminal abierto, encontrará el menú desplegable en el lado derecho de la Terminal.
     ![Creación del contenedor](images/AzureLabs-Lab313-24b.png) 
    >3. Asegúrese de que el **Python** ruta de instalación se agrega como **Variable de entorno** en su equipo. Cookiecutter debe formar parte de la misma ruta de acceso de ubicación. Siga esta [vínculo para obtener más información sobre las Variables de entorno](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), 

7. Una vez **Cookiecutter** ha finalizado la instalación, debe reiniciar el equipo, por lo que **Cookiecutter** se reconoce como un comando dentro del entorno del sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capítulo 7: crear la solución de contenedor

En este momento, deberá crear el contenedor, con el módulo, se inserte en el *Container Registry*. Una vez que haya insertado el contenedor, usará el *centro de IoT Edge* servicio implementarlo en el dispositivo, que se está ejecutando el *en tiempo de ejecución de IoT Edge*.

1. En VS Code, haga clic en **Vista > Paleta de comandos**.

2. En la paleta, buscar y ejecutar **Azure IoT Edge: Nueva solución de Iot Edge**.

3. Examinar en una ubicación donde desea crear la solución. Presione el **ENTRAR** clave, para aceptar la ubicación.

4. Asigne un nombre a la solución. Presione el **ENTRAR** clave, para confirmar el nombre proporcionado.

5. Ahora se le pedirá elegir el marco de trabajo de la plantilla para su solución. Haga clic en **módulo de Python**. Presione el **ENTRAR** clave, para confirmar esta opción.

6. Asigne un nombre al módulo. Presione el **ENTRAR** clave, para confirmar el nombre de su módulo. Asegúrese de anotar (con el Bloc de notas) el nombre del módulo, ya que se usará más adelante.

7. Observará un pregenerados *repositorio de imágenes de Docker* dirección aparecerá en la paleta. Tendrá el siguiente aspecto:

    **localhost: 5000 /, el nombre del módulo -**. 

8. Eliminar **localhost: 5000**y en su lugar de insertar el *Container Registry* **servidor de inicio de sesión** dirección, que anotó al crear el **contenedor Servicio de registro** ([en el paso 8 de capítulo 2](#chapter-2---the-container-registry-service)). Presione el **ENTRAR** clave, para confirmar la dirección.

9. En este momento, se creará la solución que contiene la plantilla para el módulo de Python y su estructura se mostrará en el **ficha explorar**, de VS Code, en el lado izquierdo de la pantalla. Si el **ficha explorar** es no está abierto, puede abrirlo haciendo clic en el botón de más arriba, en la barra de la izquierda.

    ![Creación del contenedor](images/AzureLabs-Lab313-25.png)

10. Es el último paso de este capítulo, haga clic en y abra el **archivo .env**, desde el **ficha explorar**y agregue su *Container Registry* **denombredeusuario** y **contraseña**. Este archivo se pasa por alto por git, pero en la creación del contenedor, establecerá las credenciales para tener acceso a la **servicio de registro de contenedor**.

    ![Creación del contenedor](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capítulo 8: edición de la solución de contenedor

Ahora se completará la solución de contenedor, mediante la actualización de los siguientes archivos:

- *principales<span></span>.py* script de python.
- *requirements.txt*.
- *deployment.template.json*.
- *Dockerfile.amd64*

A continuación, creará el *imágenes* carpeta, utilizada por el script de python para comprobar si las imágenes que debe coincidir con su *modelo Custom Vision*. Por último, agregará el *labels.txt* archivo, para ayudar a leer el modelo y el *model.pb* archivo, que es el modelo.

1. Con VS Code abra, navegue a la carpeta de módulo y busque la secuencia de comandos denominada **principal<span></span>.py**. Haga doble clic en él para abrirlo.

2. Eliminar el contenido del archivo e inserte el código siguiente:

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

3.  Abra el archivo denominado **requirements.txt**y sustituya su contenido por lo siguiente:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Abra el archivo denominado **deployment.template.json**y sustituya su contenido siguiente la siguiente directriz:

    1. Ya que tendrá su propia, único, estructura JSON, deberá editarlo manualmente (en lugar de copiar un ejemplo). Para facilitar este proceso, utilice el debajo de la imagen como guía.
    2. Las áreas que tendrá un aspecto diferentes a la suya, pero que **no debería cambiar está resaltado en amarillo**.
    3. **Las secciones que deba eliminar, están resaltadas en rojo.**
    4. Tenga cuidado al eliminar los corchetes correctos y también quitar las comas.

        ![Creación del contenedor](images/AzureLabs-Lab313-27.png)

    5. El JSON completado debería ser similar a la siguiente imagen (sin embargo, con sus diferencias únicas: *referencias de nombre de usuario/contraseña/nombre/módulo*):

        ![Creación del contenedor](images/AzureLabs-Lab313-28.png)

5.  Abra el archivo denominado **Dockerfile.amd64**y sustituya su contenido por lo siguiente:

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

6.  Haga doble clic en la carpeta en **módulos** (tendrá el nombre que proporcionó anteriormente; en el ejemplo más abajo, lo que se denomina *pythonmodule*) y haga clic en **nueva carpeta**. Nombre de la carpeta **imágenes**.

7.  Dentro de la carpeta, agregue algunas imágenes con el mouse o teclado. Serán las imágenes que se va a analizar el modelo de Tensorflow.

    > [!WARNING]
    > Si usa su propio modelo, deberá cambiar este comportamiento para reflejar sus propios datos de modelos.

8.  Ahora deberá recuperar el **labels.txt** y **model.pb** desde la carpeta de modelos anteriores descargó los archivos (o creado a partir de su propio **Custom Vision Service** ), en [capítulo 1](#chapter-1---retrieve-the-custom-vision-model). Una vez que los archivos, colocarlos dentro de la solución, junto con los demás archivos. El resultado final debe parecerse a la imagen siguiente:

    ![Creación del contenedor](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capítulo 9 - paquete de la solución como un contenedor

1.  Ahora está listo para "paquete" los archivos como un contenedor y los insertará en sus **Azure Container Registry**. Dentro de VS Code, abra el *Terminal integrado* (**Ver > Terminal integrado / CTRL + '**) y utilice la siguiente línea para iniciar sesión en **Docker** (sustituya los valores de la comando con las credenciales de su **Azure Container Registry (ACR)**):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Haga doble clic en el archivo **deployment.template.json**y haga clic en **compilar solución de IoT Edge**. Este proceso de compilación tarda bastante tiempo (según el dispositivo), así que Prepárese esperar. Al finalizar el proceso de compilación, un **deployment.json** archivo se habrá creado dentro de una nueva carpeta denominada **config**.

    ![Crear implementación](images/AzureLabs-Lab313-30.png)

3. Abra el **paleta de comandos** nuevo y busque **Azure: Inicie sesión en**. Siga las indicaciones con sus credenciales de cuenta de Azure; VS Code le proporcionará una opción para *copiar y abrir*, que se copiará el código del dispositivo en breve necesitará y abra el explorador web predeterminado. Cuando se le solicite, pegue el código de dispositivo, para autenticar el equipo.

    ![copiar y abrir](images/AzureLabs-Lab313-31.png)

4. Una vez firmados en observará, en el lado inferior de la *explorar* panel una nueva sección denominada **dispositivos de Azure IoT Hub**. Haga clic en esta sección para expandirlo.

    ![dispositivo de Edge](images/AzureLabs-Lab313-32.png)

5. Si el dispositivo no está aquí, deberá haga *dispositivos de Azure IoT Hub*y, a continuación, haga clic en **establece IoT Hub Connection String**. A continuación, verá que el **paleta de comandos** (en la parte superior de VS Code), le pedirá que escriba su *cadena de conexión*. Se trata de la *cadena de conexión* que anotó al final de [capítulo 3](#chapter-3---the-iot-hub-service). Presione el **ENTRAR** clave, una vez que ha copiado la cadena.    

6. El dispositivo debe cargar y aparecen. Haga doble clic en el nombre del dispositivo y, a continuación, haga clic en **Crear implementación para dispositivo único**.

    ![Crear implementación](images/AzureLabs-Lab313-33b.png)

7. Obtendrá un *Explorador de archivos* símbolo del sistema, donde puede navegar a la **config** carpeta y, a continuación, seleccione el **deployment.json** archivo. Con ese archivo seleccionado, haga clic en el **Seleccionar manifiesto de implementación de Edge** botón.

    ![Crear implementación](images/AzureLabs-Lab313-34.png)

8. En este momento ha proporcionado su **servicio IoT Hub** con el manifiesto para que pueda implementar el contenedor, como un módulo, desde su **Azure Container Registry**, eficaz implementarla en su dispositivo.

9. Para ver los mensajes enviados desde el dispositivo a IoT Hub, haga clic en nuevo en el nombre de dispositivo en el **dispositivos de Azure IoT Hub** sección la **Explorer** panel y haga clic en **iniciar supervisión Mensaje de D2C**. Los mensajes enviados desde el dispositivo deben aparecer en el Terminal de VS. Sea paciente, esta operación puede tardar algún tiempo. Consulte el capítulo siguiente para la depuración y comprobación de si la implementación fue correcta.

Ahora creará una iteración de este módulo entre las imágenes en el **imágenes** carpeta y analizarlos, con cada iteración. Esto es obviamente sólo una demostración de cómo obtener el modelo de aprendizaje automático básico para trabajar en un entorno de dispositivo IoT Edge. 

Para expandir la funcionalidad de este ejemplo, podría proceder de varias maneras. Una manera de estar podría incluir algo de código en el contenedor, que captura fotos desde una cámara Web que está conectado al dispositivo y guarda las imágenes en la carpeta imágenes. 

Otra manera puede copiarse las imágenes desde el dispositivo de IoT en el contenedor. Una forma práctica de hacerlo es ejecutar el comando siguiente en el dispositivo de IoT Terminal (quizás una pequeña aplicación podría hacer el trabajo, si se deseaba automatizar el proceso). Para probar este comando, puede ejecutarlo manualmente desde la ubicación de la carpeta donde se almacenan los archivos:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capítulo 10 - depuración el Runtime de IoT Edge

Los siguientes son una lista de líneas de comandos y sugerencias para ayudarle a supervisar y depurar la actividad de mensajería de la *en tiempo de ejecución de IoT Edge*, desde su **dispositivo Ubuntu ejecutando**. 

- Compruebe el *en tiempo de ejecución de IoT Edge* estado mediante la ejecución de la línea de comandos siguiente:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Recuerde que debe presionar **Ctrl + C**, para finalizar la visualización del estado.

- Enumerar los contenedores que están implementados actualmente. Si el *servicio IoT Hub* ha implementado correctamente, los contenedores se mostrarán mediante la ejecución de la línea de comandos siguiente:

    ```bash
        sudo iotedge list
    ```

    O bien

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > El ejemplo anterior es una buena forma de comprobar si el módulo se ha implementado correctamente, tal y como aparecerá en la lista. en caso contrario, podrá **sólo** vea el *edgeHub* y *edgeAgent*.

- Para mostrar los registros de código de un contenedor, ejecute la siguiente línea de comandos:

    ```bash
        journalctl -u iotedge
    ```

**Comandos útiles para administrar el tiempo de ejecución de IoT Edge:**

-  Para eliminar todos los contenedores en el host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Para detener el *en tiempo de ejecución de IoT Edge*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capítulo 11: crear el servicio de tabla 

Desplácese hasta el Portal de Azure, donde creará un servicio de tablas de Azure, mediante la creación de un recurso de almacenamiento.

1. Si no ha iniciado sesión, inicie sesión en el [Portal de Azure](https://portal.azure.com).

2. Una vez iniciada la sesión, haga clic en **crear un recurso**, en la esquina superior izquierda esquina y busque **cuenta de almacenamiento**y presione la **ENTRAR** clave, para iniciar la búsqueda.

3. Una vez que ha aparecido, haga clic en **cuenta de almacenamiento: blob, archivo, tabla, cola** en la lista.

    ![Busque la cuenta de almacenamiento](images/AzureLabs-Lab313-35.png)

4. La nueva página proporcionará una descripción de la **cuenta de almacenamiento** Service. En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una instancia de este servicio.

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab313-36.png)

5. Una vez que ha hecho clic **crear**, aparecerá un panel:

    1. Insertar el elemento **nombre** para esta instancia de servicio (*debe estar en minúsculas*).

    2. Para **modelo de implementación**, haga clic en **Administrador de recursos**.

    3. Para **tipo de cuenta**, mediante el menú desplegable, haga clic en **almacenamiento (uso general v1)**.

    4. Haga clic en un adecuado **ubicación**.
    
    5. Para el **replicación** menú desplegable, haga clic en **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)**.

    6. Para **rendimiento**, haga clic en **estándar**.

    7. Dentro de la **se requiere transferencia segura** sección, haga clic en **deshabilitado**.

    8. Desde el **suscripción** menú desplegable, haga clic en una suscripción adecuada.

    9. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionamiento y administrar, de facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Deje **redes virtuales** como **deshabilitado**, si se trata de una opción para usted.

    11. Haga clic en **Crear**.

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab313-37.png)

6. Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

7. Una vez creada la instancia de servicio, aparecerá una notificación en el Portal. Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab313-38.png)

8. Haga clic en el **ir al recurso** botón en la notificación y se le dirigirá a la nueva página de información general de instancia de servicio de almacenamiento.

    ![Ir al recurso](images/AzureLabs-Lab313-39.png)

9. En la página de información general, en el lado derecho, haga clic en **tablas**.
    
    ![Tablas](images/AzureLabs-Lab313-40.png)

10. El panel de la derecha cambiará para mostrar el **Table Service** información, en la que deberá agregar una nueva tabla. Haga clic en el **+ tabla** botón a la esquina superior izquierda.

    ![abrir tablas](images/AzureLabs-Lab313-41.png)

11. Se mostrará una página nueva, en la que tiene que introducir un **nombre de la tabla**. Este es el nombre que usará para hacer referencia a los datos en la aplicación en los capítulos posteriores (creación de Function App y Power BI). Insertar **IoTMessages** como el nombre (solo puede elegir su propio, recuerde que cuando se usa más adelante en este documento) y haga clic en **Aceptar**. 

12. Una vez creada la nueva tabla, podrá verlo en el **Table Service** página (en la parte inferior).

    ![nueva tabla creada](images/AzureLabs-Lab313-42.png)  

13. Ahora haga clic en **claves de acceso** y realice una copia de la **nombredecuentadealmacenamiento** y **clave** (mediante el Bloc de notas), se usará estos valores más adelante en este curso, al crear el **Aplicación de azure Function**.

    ![nueva tabla creada](images/AzureLabs-Lab313-43.png) 

14. Mediante el panel de la izquierda de nuevo, desplácese hasta la *Table Service* sección y haga clic en **tablas** (o **Examinar tablas**, en los portales más reciente) y realice una copia de la  **Dirección URL de la tabla** (mediante el Bloc de notas). Usará este valor más adelante en este curso, al vincular la tabla a su **Power BI** aplicación.

    ![nueva tabla creada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capítulo 12: finalización de la tabla de Azure

Ahora que su **Table Service** cuenta de almacenamiento ha sido el programa de instalación, es momento de agregar datos a él, que se usará para almacenar y recuperar información. La edición de las tablas puede realizarse a través de **Visual Studio**.

1. Abra **Visual Studio** (**no** código de Visual Studio).

2. En el menú, haga clic en **Ver > Cloud Explorer**.

    ![Abra cloud explorer](images/AzureLabs-Lab313-45.png)

3. El **Cloud Explorer** se abrirá como un elemento acoplado (tenga paciencia, como la carga puede tardar tiempo).

    > [!WARNING] 
    > Si la suscripción que usó para crear su *cuentas de almacenamiento* no está visible, asegúrese de que tiene: 
    > - Iniciar sesión en la misma cuenta que usan para el Portal de Azure.
    > - Seleccionar la suscripción desde la página de administración de cuentas (es posible que deba aplicar un filtro de la configuración de su cuenta):  
    >
    >   ![encuentra la suscripción](images/AzureLabs-Lab313-46.png)

4. Se mostrarán los servicios de nube de Azure. Buscar **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de la que se va a expandir sus cuentas.

    ![Abra cuentas de almacenamiento](images/AzureLabs-Lab313-47.png)

5. Una vez que se expande el recién creado **cuenta de almacenamiento** debe estar disponible. Haga clic en la flecha situada a la izquierda de su almacenamiento y, a continuación, una vez que se expande, encontrar **tablas** y haga clic en la flecha situada junto a la que, para que se muestre el **tabla** que creó en el último capítulo. Haga doble clic en su **tabla**.

6. La tabla se abrirá en el centro de la ventana de Visual Studio. Haga clic en el icono de tabla con el **+** (más) en él.

    ![Agregar nueva tabla](images/AzureLabs-Lab313-48.png)

7. Se mostrará una ventana, se le pide para permitirle *Agregar entidad*. Se creará una sola entidad, aunque tendrá tres propiedades. Observará que *PartitionKey* y *RowKey* ya se proporcionan, ya que se usan para buscar los datos en la tabla. 

    ![clave de partición y fila](images/AzureLabs-Lab313-49.png)

8. Actualice los valores siguientes:

    - Nombre: **PartitionKey**, valor: **PK_IoTMessages** 

    - Nombre: **RowKey**, valor: **RK_1_IoTMessages** 

9. A continuación, haga clic en **Agregar propiedad** (en la parte inferior izquierda de la *Agregar entidad* ventana) y agregue la siguiente propiedad:

    - **El elemento MessageContent**, como un *cadena*, deje el valor en blanco.

10. La tabla debe coincidir con el que aparece en la imagen siguiente:

    ![Agregue los valores correctos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > La razón por la entidad tiene el número 1 en la clave de fila, es porque puede ser conveniente agregar más de los mensajes que desee experimentar con este curso.

11. Haga clic en **Aceptar** cuando haya terminado. La tabla ya está lista para usarse.

## <a name="chapter-13---create-an-azure-function-app"></a>Capítulo 13 - creación de una aplicación de función de Azure 

Es el momento ahora para crear un *Azure Function App*, que será llamado por el *servicio IoT Hub* para almacenar el *IoT Edge* los mensajes de dispositivo en el **tabla** Servicio que creó en el capítulo anterior.

En primer lugar, deberá crear un archivo que permitirá que la función de Azure cargar las bibliotecas que necesarias.

1.  Abra **el Bloc de notas** (presione el *Windows clave*y el tipo de *el Bloc de notas*).

    ![Abra el Bloc de notas](images/AzureLabs-Lab313-51.png)

2.  Con el Bloc de notas abierto, inserte la siguiente estructura JSON en ella. Una vez que lo haya hecho, guárdelo en el escritorio como **project.json**. Este archivo define las bibliotecas que se va a usar la función. Si ha usado NuGet, le resultarán familiares.
    
    > [!WARNING]
    > Es importante que la denominación es correcta. Asegúrese de que lo hace **no tienen un .txt** la extensión de archivo. Consulte la referencia a continuación:
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

3.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

4.  Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque **Function App**y presione la **ENTRAR** clave para buscar. Haga clic en *Function App* en los resultados, para abrir un nuevo panel.

    ![Busque la aplicación de función](images/AzureLabs-Lab313-53.png)

5.  El nuevo panel ofrecerá una descripción de la **Function App** Service. En la parte inferior izquierda de este panel, haga clic en el **crear** botón para crear una asociación con este servicio.

    ![instancia de la aplicación de función](images/AzureLabs-Lab313-54.png)

6.  Una vez que ha hecho clic **crear**, rellene lo siguiente:

    1. Para **nombre de la aplicación**, inserte el nombre deseado para esta instancia de servicio.

    2. Seleccione un **suscripción**.

    3. Seleccione el plan de tarifa adecuado para usted, si ésta es la primera hora de creación de un **Function App Service**, un nivel gratuito debe estar disponible para usted.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionamiento y administrar, de facturación para una colección de recursos de Azure. Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Para **OS**, haga clic en Windows, ya que es la plataforma prevista.

    6. Seleccione un **Plan de hospedaje** (este tutorial se usará un **Plan de consumo**.

    7. Seleccione un **ubicación** (elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)

    8. Para el **almacenamiento** sección **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.

    9. No necesitará *Application Insights* en esta aplicación, por lo que no dude en dejarlo **desactivar**.

    10. Haga clic en **Crear**.

        ![Crear nueva instancia](images/AzureLabs-Lab313-55.png)

7.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

8.  Una vez creada la instancia de servicio, aparecerá una notificación en el Portal.

    ![nueva notificación](images/AzureLabs-Lab313-56.png)

9.  Haga clic en la notificación, cuando la implementación sea correcta (finalizada).

10. Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio. 

    ![Ir al recurso](images/AzureLabs-Lab313-57.png)

11. En el lado izquierdo del panel nuevo, haga clic en el **+** (más) situado junto a *funciones*, para crear una nueva función.

    ![Agregar nueva función](images/AzureLabs-Lab313-58.png)

12. En el panel central, el **función** aparecerá la ventana de creación. Desplácese más hacia abajo y haga clic en **función personalizada**.

    ![función personalizada](images/AzureLabs-Lab313-59.png)

13. Desplácese hacia abajo en la página siguiente, hasta que encuentre **IoT Hub (centro de eventos)**, a continuación, haga clic en él.

    ![función personalizada](images/AzureLabs-Lab313-60.png)

14. En el **IoT Hub (centro de eventos)** hoja, establezca el **lenguaje** a **C#** y, a continuación, haga clic en **nueva**.

    ![función personalizada](images/AzureLabs-Lab313-61.png)

15. En la ventana que aparece, asegúrese de que **IoT Hub** está seleccionada y el nombre de la *IoT Hub* campo se corresponde con el nombre de su *servicio IoT Hub* que tiene creado anteriormente ([en el paso 8 del capítulo 3](#chapter-3---the-iot-hub-service)). A continuación, haga clic en el **seleccione** botón.

    ![función personalizada](images/AzureLabs-Lab313-62.png)

16. En el **IoT Hub (centro de eventos)** hoja, haga clic en **crear**.

    ![función personalizada](images/AzureLabs-Lab313-63.png)

17. Se le redirigirá al editor de función.

    ![función personalizada](images/AzureLabs-Lab313-64.png)

18. Elimine todo el código en él y reemplácelo con lo siguiente:

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

19. Cambie las siguientes variables, por lo que se correspondan con los valores adecuados (**tabla** y **almacenamiento** valores, de [paso 11 y 13, respectivamente, del capítulo 11](#chapter-11---create-table-service)), que encontrará en su **cuenta de almacenamiento**:

    - **tableName**, con el nombre de su **tabla** ubicado en su **cuenta de almacenamiento**.
    - **tableURL**, con la dirección URL de su **tabla** ubicado en su **cuenta de almacenamiento**.
    - **storageAccountName**, con el nombre del valor correspondiente con el nombre de su **cuenta de almacenamiento** nombre.
    - **storageAccountKey**, con la clave que obtuvo en el servicio de almacenamiento que ha creado anteriormente.

    ![función personalizada](images/AzureLabs-Lab313-65.png)

20. Con el código en su lugar, haga clic en **guardar**.

21. A continuación, haga clic en el **\<** icono (flecha), en el lado derecho de la página.

    ![función personalizada](images/AzureLabs-Lab313-66.png)

22. Un panel se desliza en desde la derecha. En el panel de control, haga clic en **cargar**y un *del explorador de archivos* aparecerá.

23. Vaya a y haga clic en, el **project.json** archivo que creó en **el Bloc de notas** anteriormente y, a continuación, haga clic en el **abierto** botón. Este archivo define las bibliotecas que se va a usar la función.

    ![función personalizada](images/AzureLabs-Lab313-67.png)

24. Cuando se ha cargado el archivo, aparecerá en el panel de la derecha. Haga clic en él se abrirá dentro la **función** editor. Debe examinar **exactamente** igual que la imagen siguiente.

    ![función personalizada](images/AzureLabs-Lab313-68.png)

25. En este momento estaría muy bien probar la funcionalidad de la función para almacenar el mensaje en su *tabla*. En la parte superior derecha de la ventana, haga clic en **prueba**.

    ![función personalizada](images/AzureLabs-Lab313-69.png)

26. Insertar un mensaje en el **cuerpo de la solicitud**, como se muestra en la ilustración anterior y haga clic en **ejecutar**. 

27. La función se ejecutará, mostrar el estado de resultado (observará el verde **estado 202 aceptado**, más arriba la *salida* ventana, lo que significa que produjo una llamada correcta):

    ![resultado de salida](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capítulo 14: ver los mensajes activos

Si ahora abre Visual Studio (**no** Visual Studio Code), puede visualizar el resultado de mensaje de prueba, tal como se almacenará en el *el elemento MessageContent* área de cadena.

![función personalizada](images/AzureLabs-Lab313-71.png)

Con el servicio de tabla y la aplicación de función en su lugar, los mensajes de dispositivo Ubuntu aparecerá en su *IoTMessages* tabla. Si aún no se está ejecutando, inicie de nuevo el dispositivo y podrá ver los mensajes de resultados desde el dispositivo y el módulo, dentro de la tabla, a través mediante Visual Studio *Cloud Explorer*.

![Visualizar datos](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capítulo 15: el programa de instalación de Power BI

Para visualizar los datos desde el dispositivo IOT que configurará **Power BI** (versión de escritorio), para recopilar los datos desde el *tabla* servicio, que acaba de crear. El *HoloLens* versión de Power BI, a continuación, usará esos datos a visualizar el resultado.

1.  Abrir la Microsoft Store en Windows 10 y buscar **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Descargar la aplicación. Una vez que haya terminado de descargarse, ábralo.

3.  Inicie sesión en *Power BI* con su **cuenta de Microsoft 365**. Que se le redirija a un explorador para registrarse. Una vez que se registre, vuelva a la aplicación de Power BI y vuelva a iniciarla.

4.  Haga clic en **obtener datos** y, a continuación, haga clic en **más...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Haga clic en **Azure**, **Azure Table Storage**, a continuación, haga clic en **Connect**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Se le pedirá que inserte la **URL de la tabla** que recopiló anteriormente ([en el paso 13 del capítulo 11](#chapter-11---create-table-service)), al crear el servicio tabla. Después de insertar la dirección URL, elimine la parte de la ruta de acceso que hace referencia a la tabla "subcarpeta" (que era IoTMessages, en este curso). El resultado final debe ser como se muestra en la imagen siguiente. A continuación, haga clic en **Aceptar**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Se le pedirá que inserte la **clave de almacenamiento** que anotó ([en el paso 11 del capítulo 11](#chapter-11---create-table-service)) anteriores al crear el almacenamiento de tabla. A continuación, haga clic en **Connect**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Un **Panel navegador** se mostrará, marque la casilla situada junto a la tabla y haga clic en **carga**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. La tabla ya se ha cargado en Power BI, pero requiere una consulta para mostrar los valores en él. Para ello, haga doble clic en el nombre de tabla que se encuentra en la **panel campos** en el lado derecho de la pantalla. A continuación, haga clic en **Editar consulta**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Un **Editor de Power Query** abrirá una nueva ventana, se muestra la tabla. Haga clic en la palabra **registro** dentro de la *contenido* columna de la tabla, para visualizar el contenido almacenado.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Haga clic en **en la tabla**, en la parte superior izquierda de la ventana. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Haga clic en **cerrar y aplicar**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Una vez finalizada la carga dentro de la consulta, el **panel campos**, en el lado derecho de la pantalla, marque las casillas correspondientes a los parámetros **nombre** y **valor**a visualizar el **el elemento MessageContent** contenido de la columna.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Haga clic en el **icono de disco azul** en la parte superior izquierda de la ventana para guardar el trabajo en una carpeta de su elección.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Ahora puede hacer clic en el botón Publicar para cargar la tabla en el área de trabajo. Cuando se le solicite, haga clic en **mi área de trabajo** y haga clic en *seleccione*. Espere a que se muestre el resultado del envío correcto.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> El capítulo siguiente es específica de HoloLens. Power BI no está actualmente disponible como una aplicación envolvente, sin embargo, puede ejecutar la versión de escritorio en el Portal de realidad mixta de Windows (también conocido como Cliff House), a través de la aplicación de escritorio.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capítulo 16: datos de visualización de Power BI en HoloLens

1. En su HoloLens, inicie sesión en el **Microsoft Store**, al pulsar el icono correspondiente en la lista de aplicaciones.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Busque y, a continuación, descargue el **Power BI** aplicación.

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Iniciar **Power BI** desde la lista de aplicaciones. 

4. **Power BI** podría pedirle que inicie sesión en su **cuenta de Microsoft 365**.

5. Una vez dentro de la aplicación, el área de trabajo debe mostrar de forma predeterminada como se muestra en la imagen siguiente. Si no ocurre, simplemente haga clic en el icono del área de trabajo en el lado izquierdo de la ventana.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Su terminado la aplicación de IoT Hub

Enhorabuena, ha creado correctamente un servicio IoT Hub, con un dispositivo simulado de borde de la máquina Virtual. El dispositivo puede comunicarse los resultados de un modelo de machine learning a un servicio de tabla de Azure, que facilita una Azure Function App, que se leen en Power BI y se visualizan dentro de un Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Ejercicios de bonificación

### <a name="exercise-1"></a>Ejercicio 1

Expanda la estructura de mensajería que se almacena en la tabla y lo muestra como un gráfico. Es posible que desee recopilar más datos y almacenarla en la misma tabla, que se mostrará más adelante.

### <a name="exercise-2"></a>Ejercicio 2

Crear una más "captura de cámara" módulo va a implementar en el panel de IoT, por lo que pueden capturar imágenes a través de la cámara para analizarlos.
