# <a name="getting-unity-ready-for-development"></a>Cómo prepararse para el desarrollo de Unity 

En este tutorial, se obtenga información sobre cómo preparar y configurar Unity para el desarrollo de aplicaciones, como importar el Kit de herramientas de realidad mixta, configuración de generación y preparación de la escena.

Objetivos:

- Configuración de Unity para el desarrollo de aplicaciones

- Importación de Mixed Reality Toolkit

- Preparación de la escena de proyecto

### <a name="instructions"></a>Instrucciones

1. Descargue y guarde el paquete de unity del Kit de herramientas de realidad mixta haciendo [aquí.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. En Unity, haga clic en el menú de recursos y seleccione Importar paquete, a continuación, haga clic en el paquete personalizado.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Seleccione el paquete de Unity que acaba de descargar desde el vínculo indicado en el paso 1. Una vez que aparece la ventana emergente de importación en Unity, haga clic en el botón Importar para comenzar a importar. Importar el MRTK puede tardar varios minutos.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Nota: El paquete descargado está en la carpeta local donde ha guardado el archivo. La imagen anterior no describe donde encontrará el paquete.

4. Cree una nueva escena. En este ejemplo se puede realizar haciendo clic en archivo, y seleccione nueva escena"). Guarde la escena como HLSharedProjectMain.

> Nota: puede recibir un mensaje emergente que tiene un aspecto similar a la siguiente imagen. Por ahora, haga clic en no.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. En el Kit de herramientas de realidad mixta, haga clic en Agregar a la escena y configurar.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Una vez completado, un nuevo archivo de configuración aparece, lo que le ofrece la opción de personalizar el perfil. Haga clic en copiar y personalizar.

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Desplácese hacia abajo y desactive la opción Habilitar Siagnostics sistema si desea ocultar la ventana de diagnóstico. Se recomienda mantener la ventana diagnóstico habilitado durante el desarrollo de aplicaciones para supervisar el rendimiento y si lo deshabilitan en las demostraciones de producción o la aplicación. 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Abra la configuración de compilación, presione control + MAYÚS + B o vaya a archivo -> configuración de compilación. Tenga en cuenta que el programa está establecido actualmente en la plataforma de PC, Mac y Linux independiente. Para el desarrollo de HoloLens 2, establezca la plataforma que la plataforma Universal de Windows. Selecciónelo y haga clic en la plataforma del conmutador.![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Una vez que haya terminado, haga clic en el cuadro que dice agregar escenas abierto. Ahora vaya al panel de Inspector y asegúrese de que esté marcada la casilla situada a la derecha de admite la realidad Virtual (como se muestra en la imagen siguiente). Asegúrese de que también se comprueba la casilla de verificación situada junto a segundo plano/HLSharedProjectMain tal como se muestra en la imagen siguiente.![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. En la sección de configuración de publicación en el panel del Inspector, desplácese hacia abajo hasta las capacidades y asegúrese de que se marcan las siguientes casillas:![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importar el paquete personalizado llamado SharingAssetCollection que puede descargarse [aquí.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. En el panel de proyecto, vaya a la carpeta prefabricados. En los pasos siguientes implementan unos prefabricados en la escena. En la carpeta prefabricados, haga clic y arrastre el prefabricado verá, DebugWindow en la jerarquía. Una vez terminado, guarde el proyecto por archivo, clckin, a continuación, guardar o presione Control + S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Nota: Puede que observe un elemento emergente aparece al hacer clic en el prefabricado verá, que le pide sobre Essentials TMP. Haga clic en Importar TMP Essentials según sean necesarios. Si este elemento emergente aparece, es posible que deba eliminar el recurso prefabricado de la jerarquía y volver a arrastrarlo a la jerarquía para evitar posibles errores relacionados con el texto.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Enhorabuena

El proyecto de Unity ahora está listo para Photon. En los próximos tutoriales, creamos esta escena y nuestro proyecto de Unity hacia una experiencia completa compartida.

[Tutorial siguiente: Conectar varios usuarios](mrlearning-sharing(photon)-ch3.md)

