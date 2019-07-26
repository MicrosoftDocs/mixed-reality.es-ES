# <a name="2-getting-unity-ready-for-development"></a>2. Preparar Unity para el desarrollo 


En este tutorial, aprendemos a preparar y configurar Unity para el desarrollo de aplicaciones, incluida la importación del kit de herramientas de realidad mixta, la configuración de las opciones de compilación y la preparación de la escena.

Objetivos

- Configuración de Unity para el desarrollo de aplicaciones

- Importación de Mixed Reality Toolkit

- Preparación de la escena del proyecto

## <a name="instructions"></a>Instrucciones

1. Descargue y guarde el paquete de Unity del kit de herramientas de realidad mixta; para ello, haga clic [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)

2. En Unity, haga clic en el menú activos y seleccione Importar paquete y, a continuación, haga clic en paquete personalizado.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Seleccione el paquete de Unity que acaba de descargar del vínculo proporcionado en el paso 1. Una vez que aparezca la ventana emergente importar en Unity, haga clic en el botón importar para iniciar la importación. La importación de MRTK puede tardar varios minutos.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Nota: El paquete descargado se encuentra en la carpeta local donde ha guardado el archivo. La imagen anterior no indica dónde encontrará el paquete.

4. Cree una nueva escena. Para ello, haga clic en archivo y seleccione nueva escena "). Guarde la escena como HLSharedProjectMain.

> Nota: es posible que reciba un elemento emergente que tenga un aspecto similar a la imagen siguiente. Por ahora, haga clic en no.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. En el kit de herramientas de realidad mixta, haga clic en Agregar a escena y configurar.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una vez que haya finalizado, aparecerá un nuevo archivo de configuración que le dará la opción de personalizar el perfil. Haga clic en copiar y personalizar.

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Desplácese hacia abajo y desactive habilitar el sistema de diagnósticos si desea ocultar la ventana de diagnóstico. Se recomienda mantener la ventana de diagnósticos habilitada durante el desarrollo de aplicaciones para supervisar el rendimiento y deshabilitarlo durante las demostraciones de producción o de aplicación. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Para abrir la configuración de compilación, presione Control + Mayús + B o vaya a archivo-> configuración de compilación. Tenga en cuenta que el programa está establecido actualmente en la plataforma independiente PC, Mac y Linux. Para el desarrollo de HoloLens 2, establezca la plataforma que se va a Plataforma universal de Windows. Selecciónelo y haga clic en switch Platform (cambiar plataforma).

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Una vez que haya finalizado, haga clic en el cuadro que indica agregar escenas abiertas. Ahora, vaya al panel Inspector y asegúrese de que esté activada la casilla situada a la derecha de realidad virtual (como se muestra en la imagen siguiente). Asegúrese también de que la casilla situada junto a Scenes/HLSharedProjectMain también se comprueba como se muestra en la imagen siguiente.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. En la sección configuración de publicación del panel Inspector, desplácese hacia abajo hasta capacidades y asegúrese de que las siguientes casillas están marcadas como:

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importe el paquete personalizado llamado SharingAssetCollection que puede descargarse [aquí.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. En el panel Proyecto, vaya a la carpeta Prefabs. En los siguientes pasos, se implementan algunos Prefabs en la escena. En la carpeta Prefabs, haga clic y arrastre la ventana de depuración recurso prefabricado a la jerarquía. Una vez finalizado, guarde el proyecto haciendo clic en archivo, luego en guardar o presione Control + S.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Nota: Es posible que observe que aparece una ventana emergente al hacer clic en el recurso prefabricado, donde se le pregunta sobre TMP Essentials. Haga clic en importar TMP Essentials según sea necesario. Si aparece esta ventana emergente, es posible que tenga que eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Enhorabuena

El proyecto de Unity ya está listo para Photon. En los tutoriales venideros, se basará en esta escena y nuestro proyecto de Unity en una experiencia completa compartida.

[Siguiente tutorial: 3. Conexión de varios usuarios](mrlearning-sharing(photon)-ch3.md)

