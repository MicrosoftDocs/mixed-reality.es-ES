---
title: El Sr. y Azure 307 - Machine learning
description: Realice este curso para obtener información sobre cómo implementar Azure Machine Learning Studio dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, aprendizaje automático, ml studio de machine learning, envolventes, hololens, vr
ms.openlocfilehash: 726a6cce91d46ad878f8502381d085fb979ac72a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600278"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>El Sr. y Azure 307: Aprendizaje automático

![final producto-inicio](images/AzureLabs-Lab7-0.png)

En este curso, obtendrá información sobre cómo agregar funcionalidades de Machine Learning (ML) a una aplicación de realidad mixta mediante Azure Machine Learning Studio.

*Azure Machine Learning Studio* es un servicio de Microsoft, que proporciona a los desarrolladores con un gran número de algoritmos de aprendizaje automático, lo que puede ayudar con la visualización, preparación, salida y entrada de datos. Desde estos componentes, a continuación, es posible desarrollar un experimento de análisis predictivo, realizar iteraciones sobre él y usarlo para entrenar el modelo. Siguiendo el entrenamiento, puede hacer que su modelo de operativa dentro de la nube de Azure, por lo que, a continuación, pueden puntuar nuevos datos. Para obtener más información, visite la [página de Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).

Una vez completado este curso, tendrá una aplicación envolventes auriculares de realidad mixta y habrá aprendido cómo hacer lo siguiente:

1.  Proporcionar una tabla de datos de ventas para el *Azure Machine Learning Studio* portal y diseño de un algoritmo para predecir las ventas futuras de productos populares.
2.  Crear un **proyecto Unity**, que puede recibir e interpretar los datos de predicción desde el servicio de aprendizaje automático.
3.  Mostrar los datos por predicación visualmente dentro la **proyecto Unity**hasta que proporciona los elementos más populares de ventas, en una estantería.

En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño. Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity. Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.

Este curso es un tutorial independiente, que no implican directamente otros laboratorios realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> El Sr. y Azure 307: Aprendizaje automático</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens. Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#. También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018). Es libre de usar el software más reciente, como se muestra en el [instalar el artículo herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .

Se recomiendan el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK más reciente de Windows 10](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Acceso a Internet para el programa de instalación de Azure y la recuperación de datos de aprendizaje automático

## <a name="before-you-start"></a>Antes de empezar

Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capítulo 1: configuración de la cuenta de almacenamiento de Azure

Para usar la API del traductor de Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.
1.  Inicie sesión en el [Portal Azure](https://portal.azure.com).

    > [!NOTE]
    > Si no dispone de una cuenta de Azure, deberá crear uno. Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú izquierdo.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.

3.  En el **cuentas de almacenamiento** pestaña, haga clic en **agregar**.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-2.png)

4.  En el **crear cuenta de almacenamiento** panel:

    1.  Insertar un **nombre** para su cuenta, tenga en cuenta este campo sólo acepta números y letras minúsculas.
    2.  Para **modelo de implementación,** seleccione **Administrador de recursos**.
    3.  Para **tipo de cuenta**, seleccione **almacenamiento (uso general v1)**.
    4.  Para **rendimiento**, seleccione **estándar**.
    5.  Para **replicación** seleccione **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)**.
    6.  Deje **se requiere transferencia segura** como **deshabilitado**.
    7.  Seleccione un **suscripción**.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

5.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-3.png)

6.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

7.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Capítulo 2: Azure Machine Learning Studio

Para usar el *Azure Machine Learning*, deberá configurar una instancia del servicio Machine Learning para que estén disponibles para su aplicación.

1.  En el Portal de Azure, haga clic en **New** en la esquina superior izquierda esquina y busque **el área de trabajo de Machine Learning Studio**, presione **ENTRAR**.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  La nueva página proporcionará una descripción de la **el área de trabajo de Machine Learning Studio** service. En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una asociación con este servicio.

3.  Una vez que ha hecho clic **crear**, se mostrará un panel donde debe proporcionar algunos detalles sobre la nueva **servicio Machine Learning Studio**:

    1.  Insertar el elemento **nombre de área de trabajo** para esta instancia de servicio.

    2.  Seleccione un **suscripción**.

    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes). 

        > Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos). La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones. Debe usar el mismo grupo de recursos que usó para crear el almacenamiento de Azure en el capítulo anterior.

    5.  Para el **cuenta de almacenamiento** sección, haga clic en **usar existente**, a continuación, haga clic en el menú desplegable y desde allí, haga clic en el **cuenta de almacenamiento** que creó en el último capítulo.

    6.  Seleccione la **plan de tarifa del área de trabajo** para usted, en el menú desplegable.

    7.  Dentro de la **plan de servicio Web** sección, haga clic en **crear** **nuevos,** , a continuación, inserte un nombre para ella en el campo de texto.

    8.  Desde el **plan de servicio Web tarifa** , seleccione el nivel de precios de su elección. Un nivel llamado de pruebas de desarrollo **DEVTEST estándar** deben estar disponibles para usted sin cargo alguno.

    9.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    10. Haga clic en **Crear**.

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

5.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.

8.  En la página que aparece, en el **vínculos adicionales** sección, haga clic en **iniciar Machine Learning Studio**, que dirija el explorador a la **Machine Learning Studio** Portal.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Use la **sesión** botón, en la esquina superior derecha o en el centro, para iniciar sesión en el Machine Learning Studio.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Capítulo 3: Machine Learning Studio: Programa de instalación del conjunto de datos

Una de las maneras en que funcionan los algoritmos de Machine Learning es analizar los datos existentes y, a continuación, intentar predecir resultados futuros según el conjunto de datos existente. Esto generalmente significa que los datos más existentes que tiene, mejor que será el algoritmo predecir resultados futuros.

Se proporciona una tabla de ejemplo, en este curso, llamado [ProductsTableCSV y puede descargarse aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> El archivo .zip anterior contiene tanto el **ProductsTableCSV** y el **.unitypackage**, ya que lo necesitará en [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package). Este paquete también se proporciona en este capítulo, aunque independiente para el archivo csv.

Este conjunto de datos de ejemplo contiene un registro de los objetos vendidos en cada hora de cada día del año 2017.
        
![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-11.png)

Por ejemplo, en el día 1 de 2017, a la 1 p.m. (hora 13), el elemento vendido fue sal y pimienta.

Esta tabla de ejemplo contiene 9998 entradas.

1.  Regrese a la **Machine Learning Studio** portal, y agregue esta tabla como un **Dataset** para el aprendizaje automático. Haga clic en el **+ nuevo** botón en la esquina inferior izquierda de la pantalla.

    ![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-12.png)

2.  Una sección aparecerá en la parte inferior y en que es el panel de navegación de la izquierda. Haga clic en **Dataset**, a continuación, a la derecha, **desde archivo Local**.

    ![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-13.png)

3.  Cargar el nuevo **Dataset** siguiendo estos pasos:

    1. Aparecerá la ventana de carga, donde puede **examinar** el disco duro para el nuevo conjunto de datos.

        ![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-14.png)

    2.  Una vez seleccionado y realizar una copia en la ventana de carga, deje la casilla de verificación desactivado.

    3.  En el campo de texto, escriba **ProductsTableCSV.csv** como el nombre del conjunto de datos (aunque debería agregarse automáticamente).

    4.  Mediante el menú desplegable de **tipo**, seleccione **archivo CSV genérico con un encabezado (.csv)**.

    5.  Presione el "Tick" en la parte inferior derecha de la ventana de carga y su **Dataset** se cargará.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Capítulo 4: Machine Learning Studio: El experimento

Antes de generar el sistema de aprendizaje automático, deberá crear un experimento para validar su teoría acerca de los datos. Con los resultados, sabrá si necesita más datos, o si no hay ninguna correlación entre los datos y un resultado posible.

Para empezar a crear un experimento:

1.  Haga clic en nuevo en el **+ nuevo** situado en la parte inferior izquierda de la página y luego haga clic en **experimento** > **experimento en blanco**.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-15.png)

2.  Se mostrará una página nueva con un experimento en blanco:

3.  Desde el panel de la izquierda expanda **conjuntos de datos guardados* > * Mis conjuntos de datos ** y arrastre el **ProductsTableCSV** en el **lienzo de experimento**.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-16.png)

4.  En el panel de la izquierda, expanda **transformación de datos** > **muestrear y dividir**. A continuación, arrastre el **dividir datos** en de elemento para el **lienzo de experimento**. El elemento de datos de la división dividirá el conjunto de datos en dos partes. Una parte usará para entrenar el algoritmo de aprendizaje automático. La segunda parte se utilizará para evaluar la precisión del algoritmo que genera.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-17.png)

5.  En el panel derecho (mientras que los datos de la división se selecciona el elemento en el lienzo), edite el **fracción de filas del primer conjunto de datos de salida** a **0,7**. Esto dividirá los datos en dos partes, la primera parte será un 70% de los datos y la segunda parte será el 30% restante. Para asegurarse de que los datos se dividen al azar, asegúrese de que el **división aleatoria** permanezca activada la casilla de verificación.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-18.png)

6.  Arrastre una conexión de la base de la **ProductsTableCSV** elemento en el lienzo en la parte superior del elemento de datos de la división. Esto se conectará los elementos y enviar el **ProductsTableCSV** salida del conjunto de datos (los datos) a la entrada de datos de división.  

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-19.png)

7.  En el **experimentos** del panel en el lado izquierdo, expanda **Machine Learning* > * Train **. Arrastre el **entrenar modelo ** elemento horizontalmente al lienzo del experimento. El lienzo debe ser igual a la siguiente.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-20.png)

8.  Desde el ***inferior izquierdo*** de la **dividir datos** elemento arrastrar una conexión a la **la parte superior derecha** de la **Train Model** elemento. La primera división de un 70% del conjunto de datos se usará el modelo de entrenamiento para entrenar el algoritmo.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-21.png)

9.  Seleccione el **Train Model** elemento en el lienzo y, en el **propiedades** panel (en el lado derecho de la ventana del explorador), haga clic la **iniciar el selector de columna**  botón.

10. En el cuadro de texto escriba **producto** y, a continuación, presione **ENTRAR**, *producto* se establecerá como una columna para entrenar predicciones. A continuación, haga clic en el **graduación** en la esquina inferior derecha para cerrar el cuadro de diálogo de selección.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-22.png)

11. Va a entrenar un **regresión logística Multiclase** para predecir la dirección de venta más **producto** según la hora del día y la fecha. Queda fuera del ámbito de este documento para explicar los detalles de los diferentes algoritmos proporcionados por Azure Machine Learning studio, sin embargo, puede encontrar más información en el [hoja de referencia rápida de algoritmos de Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. En el panel de elementos de experimento de la izquierda, expanda ***Machine Learning* > *Initialize Model* > * clasificación ***y arrastre el **Multiclase Logística regresión ** en elemento de una sesión en el lienzo del experimento.

13. Conecte la salida, de la parte inferior de la **regresión logística Multiclase**, a la entrada de la parte superior izquierda de la **Train Model** elemento.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-23.png)

14. En la lista de elementos de experimento en el panel de la izquierda, expanda **Machine Learning* > * puntuación**y arrastre el **elemento de modelo de puntuación ** sesión en el lienzo.

15. Conecte la salida, de la parte inferior de la **Train Model**, a la entrada de la parte superior izquierda de la **Score Model**.

16. Conecte la salida de la esquina inferior derecha de **dividir datos**, a la entrada de la parte superior derecha de la **Score Model* elemento *.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-24.png)

17. En la lista de **experimento** elementos en el panel de la izquierda, expanda ***Machine Learning* > * Evaluate ***y arrastre el **evaluar modelo ** elemento hasta el lienzo.

18. Conecte la salida desde el **Score Model** a la entrada de la parte superior izquierda de la **Evaluate Model**.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-25.png)

19. Ha creado su primer experimento de Machine Learning. Ahora puede guardar y ejecutar el experimento. En el menú en la parte inferior de la página, haga clic en el **guardar** botón para guardar el experimento y, a continuación, haga clic en **ejecutar** al principio del experimento.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-26.png)

20. Puede ver el **estado** del experimento en la parte superior derecha del lienzo. Espere unos instantes para el experimento finalice.

    > Si tiene un conjunto de datos grande (reales) es probable que el experimento podría tardar horas en ejecutarse.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-27.png)

21. Haga clic con el botón derecho en el **Evaluate Model** de elemento en el lienzo y de mantener el mouse del menú de contexto el mouse sobre **resultados de la evaluación**, a continuación, seleccione **visualizar**.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-28.png)

22. Se mostrará los resultados de evaluación que muestra los resultados predichos frente a los resultados reales. Esto usa el 30% del conjunto de datos original, que se ha dividido en versiones anteriores, para evaluar el modelo. Puede ver que los resultados no son excelentes, lo ideal es que podría tener el número más alto en cada fila estará el elemento resaltado en las columnas.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-29.png)

23. Cerrar la **resultados**.

24. Para usar el modelo recién entrenado de Machine Learning debe exponer como un **servicio Web**. Para ello, haga clic en el **Configurar servicio Web** menú de elemento en el menú en la parte inferior de la página y haga clic en **servicio Web predictivo**.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-30.png)

25. Se creará una nueva pestaña y el modelo de entrenamiento se combina para crear el nuevo servicio web. 

26. En el menú en la parte inferior de la página, haga clic en **guardar**, a continuación, haga clic en **ejecutar**. Verá el estado actualizado en la esquina superior derecha del lienzo del experimento.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-31.png)

27. Una vez que haya terminado de ejecutarse, una **implementar servicio Web** botón aparecerá en la parte inferior de la página. Está listo para implementar el servicio web. Haga clic en **implementar servicio Web** (clásica) en el menú en la parte inferior de la página.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-32.png)

    > El explorador puede preguntar para permitir que una ventana emergente, que debería **permitir**, aunque es posible que deba presionar **implementar servicio Web** nuevamente, si no aparece la página implementar. 

28. Una vez creado el experimento se le redirigirá a una **panel** página donde tendrá su **clave de API** muestra. Cópiela en el Bloc de notas por el momento, ya que lo necesitará en el código muy pronto. Una vez que haya anotado la clave de API, haga clic en el **solicitud/respuesta** situado en la **punto de conexión predeterminado** sección debajo de la clave.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Si hace clic en prueba en esta página, podrá escribir datos de entrada y ver la salida. Escriba el **día** y **hora**. Deje el **producto** entrada en blanco. A continuación, haga clic en el **confirmar** botón. La salida en la parte inferior de la página mostrará el JSON que representa la probabilidad de cada producto que se va a la opción.

29. Se abrirá una página web nueva, mostrar las instrucciones y algunos ejemplos sobre la estructura de solicitud requeridos por Machine Learning Studio. Copia el **URI de solicitud** muestra en esta página, en el Bloc de notas.

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-34.png)

Ahora ha creado un sistema de aprendizaje automático que proporciona el producto para venderse probablemente basándose en datos históricos de compras, que se correlacionan con la hora del día y el día del año.

Para llamar al servicio web, necesitará la dirección URL para el extremo de servicio y una clave de API para el servicio. Haga clic en el **Consume** ficha, en el menú superior.

El **consumo** página de información mostrará la información que necesitará llamar al servicio web desde el código. Realice una copia de la **Primary Key** y **Request-Response** dirección URL. Necesitará estos en el capítulo siguiente.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capítulo 5: configurar el proyecto de Unity

Configurar y probar los auriculares envolventes de realidad mixta.

> [!NOTE]
>  Podrá **no** requieren controladores de movimiento de este curso. Si necesita admite la configuración de los auriculares envolventes, por favor, haga clic en [aquí](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity** y cree un nuevo proyecto de Unity denominado **MR\_MachineLearning.** Asegúrese de que el tipo de proyecto se establece en **3D**.

2.  Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**. Vaya a ***editar* > *preferencias*** y, a continuación, en la ventana nueva, vaya a **herramientas externas**. Cambio **External Script Editor** a **de Visual Studio 2017**. Cerrar la **preferencias** ventana.

3.  A continuación, vaya a ***archivo* > *configuración de compilación*** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el ***Cambiar plataforma*** botón.

4.  También asegúrese de que:

    1.  **Dispositivo de destino** está establecido en **cualquier dispositivo**.

        > Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.

    2.  **Tipo de compilación** está establecido en **D3D**.

    3.  **SDK** está establecido en **más reciente instalado**.

    4.  **Versión de Visual Studio** está establecido en **más reciente instalado**.

    5.  **Compilar y ejecutar** está establecido en **máquina Local**.

    6.  No se preocupe sobre cómo configurar **escenas** ahora mismo, tal como se proporcionan más adelante.

    7.  Por ahora, se debe dejar el resto de la configuración como valor predeterminado.

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-35.png)

5.  En el **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra. 

6. En este panel, es necesario comprobar algunas opciones de configuración:

    1.  En el **otra configuración** pestaña:

        1.  **Scripting** **en tiempo de ejecución versión** debe ser **Experimental** (.NET 4.6 equivalente)

        2. **Scripting de back-end** debe ser ***.NET***

        3. **Nivel de compatibilidad de API** debe ser **.NET 4.6**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-36.png)

    2.  Dentro de la **configuración de publicación** ficha **capacidades**, consulte:

        - **InternetClient**

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-37.png)

    3.  Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-38.png)

    

6.  En **configuración de compilación** *Unity C#*  proyectos ya no está atenuada; Marque la casilla situada junto a esto. 

7.  Cierre la ventana de configuración de compilación.

8.  Guarde el proyecto (**archivo > Guardar proyecto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capítulo 6: importar el paquete de Unity MLProducts

En este curso, deberá descargar un paquete de activos de Unity llamado [ **MR-Azure-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Este paquete viene acompañada de una escena, con todos los objetos de ese creados previamente, para que pueda centrarse en hacer que todo funciona correctamente. El **ShelfKeeper** se proporciona la secuencia de comandos, aunque solo contiene las variables públicas, con el fin de la estructura del programa de instalación de escena. Deberá realizar todas las demás secciones. 

Para importar este paquete:

1.  Con el panel de Unity delante de usted, haga clic en **activos** en el menú en la parte superior de la pantalla, a continuación, haga clic en **Importar paquete, paquete personalizado**.

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  Utilice el selector de archivos para seleccionar la **MR-Azure-307.unitypackage** del paquete y haga clic en **abierto**.

3.  Se mostrará una lista de componentes para este recurso para usted. Haga clic en confirmar la importación **importar**.

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  Una vez que haya terminado de importarse, observará que algunas carpetas nuevas han aparecido en el Unity **Panel proyecto**. Estos son los modelos 3D y los materiales respectivos que forman parte de la escena prefabricada que funcionará en. En este curso, escribirá la mayoría del código.

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  Dentro de la **Panel proyecto** carpeta, haga clic en el **escenas** carpeta y haga doble clic en la escena dentro de (denominada **MR_MachineLearningScene**). Se abrirá la escena (consulte la imagen siguiente). Si faltan los rombos rojo, simplemente haga clic en el **Gizmos** situado en la parte superior derecha de la **Panel juego**.

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capítulo 7: comprobación de los archivos DLL en Unity

Para aprovechar el uso de bibliotecas JSON (usado para serializar y deserializar), se ha implementado con el paquete en que puede poner una DLL de Newtonsoft. La biblioteca debe tener la configuración correcta, aunque es conveniente comprobar (especialmente si tiene problemas con el código no funciona). 

Para ello:

-  Haga clic en el archivo Newtonsoft dentro de la carpeta de complementos y examine el **panel Inspector**. Asegúrese de que **cualquier plataforma** está activada. Vaya a la **ficha UWP** y asegúrese también de **no procesar** está activada.

    ![Importar los archivos DLL en Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capítulo 8: crear la clase ShelfKeeper

El **ShelfKeeper** clase hospeda a los métodos que controlan la interfaz de usuario y los productos generados en la escena.

Como parte del paquete importado, se habrá ha dado esta clase, aunque es incompleta. Ahora es el momento de completar dicha clase:

1.  Haga doble clic en el **ShelfKeeper** secuencia de comandos, en el **Scripts** carpeta para abrirla con **Visual Studio 2017**.

2.  Reemplace todo el código existente en el script con el código siguiente, que establece la fecha y hora y tiene un método para mostrar un producto.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.

4.  Atrás en el Editor de Unity, compruebe que la **ShelfKeeper** clase similar a la siguiente:

    ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Si la secuencia de comandos no tiene los destinos de referencia (es decir, *fecha (texto de la malla)*), basta con arrastrar los objetos correspondientes de la **jerarquía Panel**, en los campos de destino. Consulte más abajo para ver una explicación, si es necesario:
    > 
    > 1.  Abra el **punto Spawn** matriz dentro de la **ShelfKeeper** script componente pulsando en él. Una subsección aparecerá llamada **tamaño**, lo que indica el tamaño de la matriz. Tipo **3** en el cuadro de texto junto a **tamaño** y presione **ENTRAR**, y se crearán tres ranuras debajo.
    > 2. Dentro de la **jerarquía** expandir la **tiempo mostrar** objeto (pulsando la flecha situada junto a él). A continuación, haga clic en el ***cámara principal*** desde el **jerarquía**, de modo que el **Inspector** muestra su información.
    > 3. Seleccione el **cámara principal** en el **jerarquía Panel**. Arrastre el **fecha** y **tiempo** objetos desde el **jerarquía Panel** a la **texto de fecha** y **texto en tiempo de** ranuras dentro de la **Inspector** de la **cámara principal** en el **ShelfKeeper** componente.
    > 4. Arrastre el **Spawn puntos** desde el **jerarquía Panel** (debajo de la *estante* objeto) a la **3** **elemento**hacen referencia a los destinos por debajo de la **punto Spawn** de matriz, como se muestra en la imagen.
    > 
    >     ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capítulo 9: crear la clase ProductPrediction

La siguiente clase que se va a crear es la **ProductPrediction** clase.

Esta clase es responsable de:

-   Consultar el **servicio Machine Learning** instancia, que proporciona la fecha y hora actuales.

-   Deserializar la respuesta JSON en datos utilizables.

-   Interpretación de los datos, recuperar los 3 productos recomendados.

-   Una llamada a la **ShelfKeeper** métodos para mostrar los datos de la escena de la clase.

Para crear esta clase:

1.  Vaya a la **Scripts** carpeta, en el **Panel proyecto**.

2.  Haga clic en la carpeta, **crear** > **C\# Script**. Llame al script **ProductPrediction**.

3.  Haga doble clic en el nuevo **ProductPrediction** script para abrirlo con **Visual Studio 2017**.

4.  Si el **modificación de archivo detectada** cuadro de diálogo emergente, haga clic en ***recargar solución**.

5.  Agregue los siguientes espacios de nombres en la parte superior de la clase ProductPrediction:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  Dentro de la **ProductPrediction** clase insertar los siguientes dos objetos que están compuestos de una serie de clases anidadas. Estas clases se utilizan para serializar y deserializar el JSON para el servicio Machine Learning.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  A continuación, agregue las siguientes variables encima del código anterior (de modo que el JSON relacionados con el código está en la parte inferior de la secuencia de comandos, todos los demás código siguiente y fuera de la forma):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Asegúrese de que se va a insertar el **clave principal** y **punto de conexión solicitud-respuesta**, desde el Portal de Machine Learning, a continuación las variables. Las siguientes imágenes muestran que habría necesitado la clave y el punto de conexión desde. 
    >  
    > ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserte este código dentro de la **Start()** método. El **Start()** método se llama cuando se inicializa la clase:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  El siguiente es el método que recopila la fecha y hora de Windows y lo convierte en un formato que puede usar nuestro experimento de Machine Learning que se compara con los datos almacenados en la tabla.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. También puede **eliminar** el **Update()** método puesto que esta clase no lo usará.

11. Agregue el siguiente método que se comunican la fecha y hora actuales para el punto de conexión de Machine Learning y recibir una respuesta en formato JSON.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Agregue el método siguiente, que es responsable de deserializar la respuesta JSON y comunica el resultado de la deserialización para el **ShelfKeeper** clase. Este resultado será que los nombres de los tres elementos que se prevé que para vender el máximo partido a la fecha y hora actuales. Inserte el código siguiente en el **ProductPrediction** (clase), a continuación el método anterior.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Guardar **Visual Studio** y regrese a **Unity**.

14. Arrastre el **ProductPrediction** clase script desde el **Script** carpeta, en el **cámara principal** objeto.

15. Guarde la escena y el proyecto **archivo** > ***Guardar escena* / *archivo***   >  **Guardar proyecto**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capítulo 10: Compile la solución UWP

Ahora es momento de compilar el proyecto como una solución UWP, para que pueda ejecutarse como una aplicación independiente.

Para compilar:

1.  Guarde la escena actual haciendo clic en **archivo** **guardar escenas**.

2.  Vaya a **archivo** **configuración de compilación**

3.  Active la casilla denominada **Unity C\# proyectos** (Esto es importante porque permite editar las clases, una vez completada la compilación).

4.  Haga clic en **agregar escenas abiertos**,

5.  Haz clic en **Compilación**.

    ![Compile la solución UWP](images/AzureLabs-Lab7-54.png)

6.  Se le pedirá que seleccione la carpeta donde desea compilar la solución.

7.  Crear un **compilaciones** carpeta y dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.

8.  Haga clic en la nueva carpeta y, a continuación, haga clic en **seleccionar la carpeta**, para comenzar a la compilación en esa ubicación.

    ![Compile la solución UWP](images/AzureLabs-Lab7-55.png)

    ![Compile la solución UWP](images/AzureLabs-Lab7-56.png)

9.  Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).

## <a name="chapter-11---deploy-your-application"></a>Capítulo 11: implementar la aplicación

Para implementar la aplicación:

1.  Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.

2.  Con Visual Studio abierto, es preciso restaurar los paquetes de NuGet, lo que puede realizarse a través de haciendo clic en la solución MachineLearningLab_Build, desde el Explorador de soluciones (que se encuentra a la derecha de Visual Studio) y, a continuación, haga clic en restaurar paquetes NuGet:

    ![Agregar paquetes de NuGet](images/AzureLabs-Lab7-57.png)

3.  En, seleccione la configuración de la solución **depurar**.

4.  En la plataforma de soluciones, seleccione **x86**, **máquina Local**. 

    > Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo. Sin embargo, necesitará también hacer lo siguiente:
    > - Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar. 
    > - Asegúrese de **modo de programador** es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.

    ![Agregar paquetes de NuGet](images/AzureLabs-Lab7-58.png)

5.  Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.

6.  La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.

Al ejecutar la aplicación de realidad mixta, verá el banco que configuró en la escena de Unity y, desde la inicialización, se recuperarán los datos configurado dentro de Azure. Se va a deserializar los datos dentro de la aplicación y se proporcionará visualmente, como en el banco de tres modelos de los tres primeros resultados de la fecha y hora actuales.


## <a name="your-finished-machine-learning-application"></a>La aplicación finalizada de Machine Learning
 
Enhorabuena, creó una aplicación de realidad mixta que aprovecha Azure Machine Learning para realizar predicciones de datos y mostrarlos en la escena.

![Agregar paquetes de NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Ejercicio

**Ejercicio 1**

Experimentar con el criterio de ordenación de la aplicación y tener las predicciones de tres inferior aparecen en las estanterías como estos datos potencialmente sería útiles también.

**Ejercicio 2**

Uso de **Azure Tables** rellenar una tabla nueva con información meteorológica y cree un nuevo experimento usando los datos.
