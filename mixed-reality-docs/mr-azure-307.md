---
title: MR y Azure 307-machine learning
description: Complete este curso para aprender a implementar Azure Machine Learning Studio en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, machine learning, ml, machine learning Studio, hololens, envolventes, VR
ms.openlocfilehash: c86c592573dd39d926869d8cce6025fa264cc90f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437925"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR y Azure 307: machine learning

![Inicio del producto final](images/AzureLabs-Lab7-0.png)

En este curso, aprenderá a agregar capacidades de Machine Learning (ML) a una aplicación de realidad mixta mediante Azure Machine Learning Studio.

*Azure machine learning Studio* es un servicio de Microsoft, que proporciona a los desarrolladores un gran número de algoritmos de aprendizaje automático, que pueden ayudar con la entrada, la salida, la preparación y la visualización de datos. A partir de estos componentes, es posible desarrollar un experimento de análisis predictivo, realizar una iteración en él y usarlo para entrenar el modelo. Después del entrenamiento, puede hacer que el modelo sea operativo dentro de la nube de Azure, para que pueda puntuar nuevos datos. Para obtener más información, visite la [página Azure machine learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).

Una vez completado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta y habrá aprendido lo siguiente:

1.  Proporcione una tabla de datos de ventas al portal de *Azure machine learning Studio* y diseñe un algoritmo para predecir las ventas futuras de los artículos más populares.
2.  Cree un **proyecto de Unity**, que puede recibir e interpretar los datos de predicción del servicio de ml.
3.  Mostrar visualmente los datos de predication en el **proyecto de Unity**a través de la entrega de los artículos de ventas más populares, en una estantería.

En su aplicación, depende del modo en que va a integrar los resultados con el diseño. Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.

Este curso es un tutorial independiente, que no implica directamente ningún otro laboratorio de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> MR y Azure 307: machine learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens. Al usar HoloLens, puede observar algún Eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo). Puede usar el software más reciente, como se indica en el [artículo instalar las herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado
- Acceso a Internet para la configuración de Azure y la recuperación de datos de ML

## <a name="before-you-start"></a>Antes de empezar

Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capítulo 1: configuración de la cuenta de Azure Storage

Para usar la API de traductor de Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.
1.  Inicie sesión en el [portal de Azure](https://portal.azure.com).

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, tendrá que crear una. Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú de la izquierda.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.

3.  En la pestaña **cuentas de almacenamiento** , haga clic en **Agregar**.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-2.png)

4.  En el panel **crear cuenta de almacenamiento** :

    1.  Inserte un **nombre** para la cuenta. tenga en cuenta que este campo solo acepta números y letras minúsculas.
    2.  En **modelo de implementación,** seleccione **Resource Manager**.
    3.  En **tipo de cuenta**, seleccione **almacenamiento (uso general V1)** .
    4.  En **rendimiento**, seleccione **estándar**.
    5.  En **replicación** , seleccione **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .
    6.  Deje la **transferencia segura requerida** como **deshabilitada**.
    7.  Seleccione una **suscripción**.
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

5.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-3.png)

6.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

7.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Capítulo 2: el Azure Machine Learning Studio

Para usar el *Azure machine learning*, deberá configurar una instancia del servicio machine learning para que esté disponible para la aplicación.

1.  En Azure portal, haga clic en **nuevo** en la esquina superior izquierda y busque **machine learning Studio área de trabajo**, presione **entrar**.

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  La nueva página proporcionará una descripción de la **machine learning Studio** servicio del área de trabajo. En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una asociación con este servicio.

3.  Una vez que haya hecho clic en **crear**, aparecerá un panel donde debe proporcionar algunos detalles sobre el nuevo servicio de **machine learning Studio**:

    1.  Inserte el **nombre de área de trabajo** que desee para esta instancia de servicio.

    2.  Seleccione una **suscripción**.

    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común). 

        > Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Idealmente, la ubicación estará en la región donde se ejecutará la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones. Debe usar el mismo grupo de recursos que utilizó para crear el Azure Storage en el capítulo anterior.

    5.  En la sección **cuenta de almacenamiento** , haga clic en **usar existente**, haga clic en el menú desplegable y, desde allí, haga clic en la **cuenta de almacenamiento** que creó en el último capítulo.

    6.  Seleccione el **plan de tarifa del área de trabajo** adecuado en el menú desplegable.

    7.  En la sección **plan de servicio Web** , haga clic en **crear** **nuevo y** , a continuación, inserte un nombre en el campo de texto.

    8.  En la sección **nivel de precios del plan de servicio Web** , seleccione el nivel de precios que prefiera. Un nivel de prueba de desarrollo denominado **DEVTEST Standard** debe estar disponible sin cargo alguno.

    9.  También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.

    10. Haz clic en **Crear**.

        ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

5.  Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Haga clic en la notificación para explorar la nueva instancia de servicio.

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.

8.  En la página que se muestra, en la sección **vínculos adicionales** , haga clic en **iniciar machine learning Studio**, que dirigirá el explorador al portal de **machine learning Studio** .

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Use el botón **iniciar sesión** , en la parte superior derecha o en el centro, para iniciar sesión en el machine learning Studio.

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Capítulo 3: configuración Machine Learning Studio del conjunto de

Una de las formas en que Machine Learning funcionan los algoritmos es analizar los datos existentes y, a continuación, intentar predecir resultados futuros basados en el conjunto de datos existente. Por lo general, esto significa que los datos más existentes que tenga, mejor será el algoritmo para predecir resultados futuros.

Se le proporciona una tabla de ejemplo, para este curso, denominada [ProductsTableCSV, que se puede descargar aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> El archivo. zip anterior contiene **ProductsTableCSV** y **. unitypackage Tools**, que necesitará en el [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package). Este paquete también se proporciona en ese capítulo, aunque sea independiente del archivo CSV.

Este conjunto de datos de ejemplo contiene un registro de los objetos que mejor se venden cada hora de cada día del año 2017.
        
![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-11.png)

Por ejemplo, en el día 1 de 2017, a la 13:00 (hora 13), el artículo de mejor venta era Salt y pimiento.

Esta tabla de ejemplo contiene 9998 entradas.

1.  Vuelva al portal de **machine learning Studio** y agregue esta tabla como un **conjunto** de datos para los ml. Para ello, haga clic en el botón **+ nuevo** en la esquina inferior izquierda de la pantalla.

    ![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-12.png)

2.  Una sección aparecerá en la parte inferior y, dentro de ella, en el panel de navegación de la izquierda. Haga clic en **conjunto**de archivos y, a la derecha de, **desde archivo local**.

    ![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-13.png)

3.  Cargue el nuevo **conjunto** de elementos siguiendo estos pasos:

    1. Aparecerá la ventana cargar, donde puede examinar el disco duro para **Ver** el nuevo conjunto de

        ![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-14.png)

    2.  Una vez seleccionado, y de nuevo en la ventana de carga, deje la casilla sin marcar.

    3.  En el campo de texto que aparece a continuación, escriba **ProductsTableCSV. csv** como el nombre del conjunto de nombres (aunque debe agregarse automáticamente).

    4.  En el menú desplegable de **tipo**, seleccione **archivo CSV genérico con un encabezado (. csv)** .

    5.  Presione la marca de verificación en la parte inferior derecha de la ventana de carga y se cargará el **conjunto** de resultados.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Capítulo 4: el Machine Learning Studio: el experimento

Antes de poder compilar el sistema de aprendizaje automático, deberá compilar un experimento para validar su teoría sobre los datos. Con los resultados, sabrá si necesita más datos o si no hay ninguna correlación entre los datos y un resultado posible.

Para empezar a crear un experimento:

1.  Haga **clic de nuevo** en el botón **+ nuevo** situado en la parte inferior izquierda de la página y, a continuación, haga clic en experimento > **experimento en blanco**.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-15.png)

2.  Se mostrará una nueva página con un experimento en blanco:

3.  En el panel de la izquierda, expanda **conjuntos de valores guardados** > **mis conjuntos de valores** y arrastre el **ProductsTableCSV** al **lienzo del experimento**.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-16.png)

4.  En el panel de la izquierda, expanda **transformación de datos** > **ejemplo y dividir**. A continuación, arrastre el elemento **Split Data** al **lienzo del experimento**. El elemento dividir datos dividirá el conjunto de datos en dos partes. Una parte que se utilizará para entrenar el algoritmo de aprendizaje automático. La segunda parte se usará para evaluar la precisión del algoritmo generado.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-17.png)

5.  En el panel derecho (mientras está seleccionado el elemento dividir datos en el lienzo), edite la **fracción de filas del primer conjunto de** datos de salida a **0,7**. Esto dividirá los datos en dos partes, la primera parte será del 70% de los datos y la segunda parte será el 30% restante. Para asegurarse de que los datos se dividen de forma aleatoria, asegúrese de que la casilla **División aleatoria** permanece activada.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-18.png)

6.  Arrastre una conexión desde la base del elemento **ProductsTableCSV** del lienzo hasta la parte superior del elemento de datos dividido. Esto conectará los elementos y enviará la salida del conjunto de datos **ProductsTableCSV** (los datos) a la entrada de datos divididos.  

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-19.png)

7.  En el panel **experimentos** en el lado izquierdo, expanda **machine learning** > **entrenar**. Arrastre el elemento **entrenar modelo** hacia el lienzo del experimento. El lienzo debería tener el mismo aspecto que el siguiente.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-20.png)

8.  En la ***parte inferior izquierda*** del elemento **dividir datos** , arrastre una conexión a la **parte superior derecha** del elemento **entrenar modelo** . El modelo de entrenamiento usará la primera división del 70% del conjunto de filas para entrenar el algoritmo.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-21.png)

9.  Seleccione el elemento **entrenar modelo** en el lienzo y, en el panel **propiedades** (en el lado derecho de la ventana del explorador), haga clic en el botón **iniciar selector de columnas** .

10. En el cuadro de texto escriba **Product** y, a continuación, presione **entrar**; *Product* se establecerá como una columna para entrenar las predicciones. Después, haga clic en la **marca** de verificación en la esquina inferior derecha para cerrar el cuadro de diálogo de selección.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-22.png)

11. Va a entrenar un algoritmo de **regresión logística multiclase** para predecir el **producto** más vendido en función de la hora del día y la fecha. Sin embargo, queda fuera del ámbito de este documento la explicación de los detalles de los distintos algoritmos proporcionados por Azure Machine Learning Studio. puede encontrar más información en la hoja de referencia rápida de [algoritmos de machine learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. En el panel elementos del experimento de la izquierda, expanda **Machine Learning** > **inicializar modelo** > **clasificación**y arrastre el elemento **regresión logística multiclase** al lienzo del experimento.

13. Conecte la salida, desde la parte inferior de la **regresión logística multiclase**, a la entrada superior izquierda del elemento **entrenar modelo** .

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-23.png)

14. En la lista de elementos del experimento en el panel de la izquierda, expanda **Machine Learning** > **puntuación**y arrastre el elemento **puntuar modelo** al lienzo.

15. Conecte la salida, desde la parte inferior del **modelo de tren**, a la entrada superior izquierda del **modelo de puntuación**.

16. Conecte la salida inferior derecha de **Split Data (dividir datos**) a la entrada superior derecha del elemento **score Model (puntuar modelo** ).

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-24.png)

17. En la lista de elementos del **experimento** en el panel de la izquierda, expanda **machine learning** > **evaluar**y arrastre el elemento **Evaluar modelo** al lienzo.

18. Conecte el resultado del **modelo de puntuación** a la entrada superior izquierda del modelo de **evaluación**.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-25.png)

19. Ha creado su primer experimento Machine Learning. Ahora puede guardar y ejecutar el experimento. En el menú de la parte inferior de la página, haga clic en el botón **Guardar** para guardar el experimento y, a continuación, haga clic en **Ejecutar** para iniciar el experimento.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-26.png)

20. Puede ver el **Estado** del experimento en la parte superior derecha del lienzo. Espere unos instantes hasta que finalice el experimento.

    > Si tiene un conjunto de datos grande (mundo real), es probable que el experimento tarde horas en ejecutarse.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-27.png)

21. Haga clic con el botón derecho en el elemento **Evaluar modelo** del lienzo y, en el menú contextual, mantenga el mouse sobre **los resultados**de la evaluación y seleccione **visualizar**.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-28.png)

22. Los resultados de la evaluación se mostrarán mostrando los resultados previstos frente a los resultados reales. Esto utiliza el 30% del conjunto de filas original, que se dividió anteriormente, para evaluar el modelo. Puede ver que los resultados no son excelentes; lo ideal es que el número más alto de cada fila sea el elemento resaltado en las columnas.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-29.png)

23. Cierre los **resultados**.

24. Para usar el modelo de Machine Learning recién entrenado, debe exponerlo como un **servicio Web**. Para ello, haga clic en el elemento de menú **configurar servicio Web** en el menú de la parte inferior de la página y haga clic en **servicio Web predictivo**.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-30.png)

25. Se creará una nueva pestaña y se combinará el modelo de entrenamiento para crear el nuevo servicio Web. 

26. En el menú de la parte inferior de la página, haga clic en **Guardar**y, a continuación, haga clic en **Ejecutar**. Verá el estado actualizado en la esquina superior derecha del lienzo del experimento.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-31.png)

27. Una vez que haya finalizado la ejecución, aparecerá un botón **implementar servicio Web** en la parte inferior de la página. Está listo para implementar el servicio Web. Haga clic en **implementar servicio Web** (clásico) en el menú de la parte inferior de la página.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-32.png)

    > Es posible que el explorador le solicite que permita un elemento emergente, que debe **permitir**, aunque es posible que tenga que volver a presionar **implementar servicio Web** si no se muestra la página implementar. 

28. Una vez creado el experimento, se le redirigirá a una página de **Panel** en la que se mostrará la **clave de API** . Cópielo en un bloc de notas por el momento, lo necesitará en el código muy pronto. Una vez que haya anotado la clave de API, haga clic en el botón **solicitud/respuesta** en la sección **punto de conexión predeterminado** debajo de la clave.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Si hace clic en probar en esta página, podrá especificar los datos de entrada y ver la salida. Especifique el **día** y la **hora**. Deje la entrada del **producto** en blanco. A continuación, haga clic en el botón **confirmar** . La salida en la parte inferior de la página mostrará el JSON que representa la probabilidad de que cada producto sea la elección.

29. Se abrirá una nueva página web, en la que se mostrarán las instrucciones y algunos ejemplos sobre la estructura de la solicitud requerida por el Machine Learning Studio. Copie el **URI de solicitud** que se muestra en esta página en el Bloc de notas.

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-34.png)

Ahora ha creado un sistema de aprendizaje automático que proporciona el producto más probable que se venda en función de los datos de compra históricos, correlacionados con la hora del día y el día del año.

Para llamar al servicio Web, necesitará la dirección URL del punto de conexión de servicio y una clave de API para el servicio. Haga clic en la pestaña **consumo** , en el menú superior.

En la página información de **consumo** se mostrará la información necesaria para llamar al servicio web desde el código. Realice una copia de la **clave principal** y la dirección URL **de solicitud-respuesta** . Los necesitará en el siguiente capítulo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capítulo 5: configuración del proyecto de Unity

Configure y pruebe sus auriculares de la realidad mixta.

> [!NOTE]
>  **No** necesitará controladores de movimiento para este curso. Si necesita ayuda para configurar el casco envolvente, haga clic [aquí](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity** y cree un nuevo proyecto de Unity denominado **Mr\_MachineLearning.** Asegúrese de que el tipo de proyecto está establecido en **3D**.

2.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**. Cambie el **Editor de script externo** a **Visual Studio 2017**. Cierre la ventana **preferencias** .

3.  A continuación, vaya a **archivo** > **configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón ***cambiar plataforma*** .

4.  Asegúrese también de que:

    1.  El **dispositivo de destino** se establece en **cualquier dispositivo**.

        > Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.

    2.  El **tipo de compilación** se establece en **D3D**.

    3.  **SDK** está establecido en **instalado más**recientemente.

    4.  La **versión de Visual Studio** está establecida en **instalación más reciente**.

    5.  **Compilar y ejecutar** está establecido en **equipo local**.

    6.  No se preocupe por la configuración de **escenas** ahora, ya que se proporcionan más adelante.

    7.  El resto de la configuración debe dejarse como predeterminada por ahora.

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-35.png)

5.  En la ventana **configuración de compilación** , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** . 

6. En este panel, deben comprobarse algunas opciones de configuración:

    1.  En la pestaña **otros valores** :

        1.  La versión de **scripting** **en tiempo de ejecución** debe ser **experimental** (.net 4,6 equivalente)

        2. El **back-end de scripting** debe ser ***.net***

        3. El **nivel de compatibilidad de API** debe ser **.net 4,6**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-36.png)

    2.  En la pestaña **configuración de publicación** , en **capacidades**, seleccione:

        - **InternetClient**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-37.png)

    3.  Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se ha agregado el **SDK de Windows Mixed Reality** .

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-38.png)

    

6.  De nuevo en la **configuración de compilación** , los proyectos de *Unity C#*  ya no están atenuados; Marque la casilla situada junto a este. 

7.  Cierre la ventana Configuración de compilación.

8.  Guarde el proyecto (**archivo > guardar proyecto**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capítulo 6: importar el paquete de Unity de MLProducts

En este curso, tendrá que descargar un paquete de recursos de Unity llamado [**Azure-Mr-307. unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Este paquete viene completo con una escena, con todos los objetos de que se han creado previamente, por lo que puede centrarse en conseguir que todo funcione. Se proporciona el script **ShelfKeeper** , aunque solo contiene las variables públicas para la estructura de configuración de la escena. Tendrá que realizar todas las demás secciones. 

Para importar este paquete:

1.  Con el panel de Unity delante de usted, haga clic en **recursos** en el menú de la parte superior de la pantalla y, luego, haga clic en **importar paquete, paquete personalizado**.

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-39.png)

2.  Use el selector de archivos para seleccionar el paquete **Azure-Mr-307. unitypackage Tools** y haga clic en **abrir**.

3.  Se le mostrará una lista de los componentes de este recurso. Confirme la importación haciendo clic en **importar**.

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-40.png)

4.  Una vez que haya finalizado la importación, observará que algunas nuevas carpetas aparecen en el **panel del proyecto**de Unity. Estos son los modelos 3D y los materiales respectivos que forman parte de la escena previamente realizada en la que trabajará. En este curso, escribirá la mayor parte del código.

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-41.png)

5.  En la carpeta **panel del proyecto** , haga clic en la carpeta **Scenes** y haga doble clic en la escena dentro de (llamada **MR_MachineLearningScene**). La escena se abrirá (consulte la imagen siguiente). Si faltan los rombos rojos, simplemente haga clic en el botón **Gizmos** , en la parte superior derecha del **Panel de juego**.

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capítulo 7: comprobación de los archivos dll en Unity

Para aprovechar el uso de las bibliotecas JSON (que se usan para serializar y deserializar), se ha implementado un archivo DLL de Newtonsoft con el paquete que se ha incorporado. La biblioteca debe tener la configuración correcta, aunque merece la pena realizar una comprobación (especialmente si tiene problemas con el código que no funciona). 

Para ello:

-  Haga clic con el botón izquierdo en el archivo Newtonsoft dentro de la carpeta plugins y mire en el **panel Inspector**. Asegúrese de que se realiza una marca en **cualquier plataforma** . Vaya a la **pestaña UWP** y asegúrese también de que no se ha activado el **proceso** .

    ![Importación de los archivos dll en Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capítulo 8: creación de la clase ShelfKeeper

La clase **ShelfKeeper** hospeda métodos que controlan la interfaz de usuario y los productos generados en la escena.

Como parte del paquete importado, se le proporcionará esta clase, aunque está incompleta. Ahora es el momento de completar esa clase:

1.  Haga doble clic en el script **ShelfKeeper** , dentro de la carpeta **scripts** , para abrirlo con **Visual Studio 2017**.

2.  Reemplace todo el código existente en el script con el código siguiente, que establece la fecha y la hora, y tiene un método para mostrar un producto.

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

4.  De nuevo en el editor de Unity, compruebe que la clase **ShelfKeeper** es similar a la siguiente:

    ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Si el script no tiene destinos de referencia (es decir, *Date (malla de texto)* ), simplemente arrastre los objetos correspondientes del **Panel jerarquía**a los campos de destino. Consulte a continuación la explicación, si es necesario:
    > 
    > 1.  Abra la matriz de **puntos de generación** dentro del script del componente **ShelfKeeper** . para ello, haga clic en ella. Una subsección aparecerá denominada **size**, que indica el tamaño de la matriz. Escriba **3** en el cuadro de texto junto a **tamaño** y presione **entrar**; se crearán tres ranuras debajo.
    > 2. Dentro de la **jerarquía** , expanda el objeto **Time display** (haciendo clic con el botón izquierdo en la flecha situada junto a él). A continuación, haga clic en la ***cámara principal*** desde dentro de la **jerarquía**para que el **Inspector** muestre su información.
    > 3. Seleccione la **cámara principal** en el **Panel jerarquía**. Arrastre los objetos de **fecha** y **hora** desde **el panel jerarquía** hasta las ranuras de **texto** de **fecha** y hora del **Inspector** de la **cámara principal** en el componente **ShelfKeeper** .
    > 4. Arrastre los **puntos de generación** desde el **Panel de jerarquía** (debajo del objeto de *estantería* ) hasta los **tres** destinos de referencia de **elemento** debajo de la matriz de **puntos de generación** , como se muestra en la imagen.
    > 
    >     ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capítulo 9: creación de la clase ProductPrediction

La clase siguiente que va a crear es la clase **ProductPrediction** .

Esta clase es responsable de:

-   Consultar la instancia de **servicio de machine learning** , que proporciona la fecha y hora actuales.

-   Deserializar la respuesta JSON en datos utilizables.

-   Interpretar los datos, recuperar los 3 productos recomendados.

-   Llamar a los métodos de la clase **ShelfKeeper** para mostrar los datos de la escena.

Para crear esta clase:

1.  Vaya a la carpeta **scripts** , en el **panel Proyecto**.

2.  Haga clic con el botón derecho dentro de la carpeta, **cree** >  **C# script**. Llame al script **ProductPrediction**.

3.  Haga doble clic en el nuevo script **ProductPrediction** para abrirlo con **Visual Studio 2017**.

4.  Si aparece el cuadro de diálogo se **ha detectado la modificación del archivo** , haga clic en ***volver a cargar la solución**.

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

6.  Dentro de la clase **ProductPrediction** , inserte los dos objetos siguientes, que se componen de un número de clases anidadas. Estas clases se usan para serializar y deserializar el archivo JSON para el servicio Machine Learning.

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

7.  A continuación, agregue las siguientes variables sobre el código anterior (de modo que el código relacionado con JSON esté en la parte inferior del script, debajo del resto del código y fuera del camino):

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
    > Asegúrese de insertar la **clave principal** y el **punto de conexión de solicitud-respuesta**, desde el portal de machine learning, en las variables aquí. Las siguientes imágenes muestran dónde habría tomado la clave y el punto de conexión de. 
    >  
    > ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserte este código dentro del método **Start ()** . Se llama al método **Start ()** cuando se inicializa la clase:

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

9.  El siguiente es el método que recopila la fecha y la hora de Windows y las convierte en un formato que el experimento de Machine Learning puede utilizar para comparar con los datos almacenados en la tabla.

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

10. Puede **eliminar** el método **Update ()** , ya que esta clase no lo usará.

11. Agregue el método siguiente, que comunicará la fecha y hora actuales con el punto de conexión de Machine Learning y recibirá una respuesta en formato JSON.

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

12. Agregue el método siguiente, que es responsable de deserializar la respuesta JSON y de comunicar el resultado de la deserialización a la clase **ShelfKeeper** . Este resultado será el nombre de los tres elementos previstos para vender más en la fecha y hora actuales. Inserte el código siguiente en la clase **ProductPrediction** , debajo del método anterior.

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

13. Guarde **Visual Studio** y vuelva a la sección **Unity**.

14. Arrastre el script de la clase **ProductPrediction** desde la carpeta **script** hasta el objeto **Camera principal** .

15. Guarde la escena y el **archivo** de proyecto > **guardar la escena o el archivo** > **guardar el proyecto**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capítulo 10: compilar la solución UWP

Ahora es el momento de compilar el proyecto como una solución de UWP, de modo que pueda ejecutarse como una aplicación independiente.

Para compilar:

1.  Guarde la escena actual haciendo clic en **archivo** > **Guardar escenas**.

2.  Ir a **archivo** > **configuración de compilación**

3.  Active la casilla denominada **proyectos C# de Unity** (esto es importante porque le permitirá editar las clases una vez completada la compilación).

4.  Haga clic en **Agregar escenas abiertas**,

5.  Haz clic en **Compilación**.

    ![Compilar la solución de UWP](images/AzureLabs-Lab7-54.png)

6.  Se le pedirá que seleccione la carpeta en la que desea compilar la solución.

7.  Cree una carpeta **compilaciones** y, dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.

8.  Haga clic en la nueva carpeta y, a continuación, haga clic en **Seleccionar carpeta**para iniciar la compilación en esa ubicación.

    ![Compilar la solución de UWP](images/AzureLabs-Lab7-55.png)

    ![Compilar la solución de UWP](images/AzureLabs-Lab7-56.png)

9.  Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-11---deploy-your-application"></a>Capítulo 11: implementación de la aplicación

Para implementar la aplicación:

1.  Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.

2.  Con Visual Studio abierto, debe restaurar los paquetes NuGet, que se pueden realizar a través del clic con el botón derecho en la solución MachineLearningLab_Build, desde el Explorador de soluciones (que se encuentra a la derecha de Visual Studio) y, a continuación, haciendo clic en restaurar paquetes NuGet:

    ![Agregar paquetes NuGet](images/AzureLabs-Lab7-57.png)

3.  En la configuración de soluciones, seleccione **depurar**.

4.  En la plataforma de la solución, seleccione **x86**, **equipo local**. 

    > En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP** de HoloLens, que puede encontrarse en la *configuración > red & Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar. 
    > - Asegurarse de que el **modo de desarrollador** está **activado**; se encuentra en *configuración > actualizar & > de seguridad para desarrolladores*.

    ![Agregar paquetes NuGet](images/AzureLabs-Lab7-58.png)

5.  Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.

6.  La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

Al ejecutar la aplicación de realidad mixta, verá la banco que se configuró en la escena de Unity y, desde la inicialización, se capturarán los datos que configuró en Azure. Los datos se deserializarán dentro de la aplicación y los tres resultados principales de la fecha y hora actuales se proporcionarán visualmente, como tres modelos en la banco.


## <a name="your-finished-machine-learning-application"></a>La aplicación Machine Learning finalizada
 
Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha las Azure Machine Learning para hacer predicciones de datos y mostrarlas en la escena.

![Agregar paquetes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Dicha

**Ejercicio 1**

Experimente con el criterio de ordenación de la aplicación y tenga en cuenta que las tres predicciones inferiores aparecen en la estantería, ya que estos datos también podrían resultar útiles.

**Ejercicio 2**

El uso de **tablas de Azure** rellenará una nueva tabla con información meteorológica y creará un nuevo experimento con los datos.
