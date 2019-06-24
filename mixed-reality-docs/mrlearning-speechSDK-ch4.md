## <a name="lesson-4"></a>Lección 4

En el capítulo 4, exploramos la característica de intención de servicios de voz. Se configurará nuestro LUIS Azure Portal, nuestra intención/entidades y declaraciones de instalación, publicar nuestro recurso intención, conectar nuestra aplicación de Unity a nuestro recurso intención y realizar nuestra primera llamada de API de intención.

1. Permitir que la máquina para permitir dictado, para ello, vaya a la configuración de Windows, seleccionar "privacy", a continuación, "voz" y, por último, "tinta & escribiendo" y activar los servicios de voz y escritura de sugerencias.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> Nota: para obtener información sobre cómo hacer esto en un Macbook/Mac, haga clic en [aquí](linkgoeshere).

2. Inicie sesión en el [Portal Azure](https://portal.azure.com/). Una vez que haya iniciado sesión, haga clic en crear un recurso y busque "Comprensión del lenguaje" y haga clic en ENTRAR.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Seleccione el botón Crear, para crear una instancia de este servicio. Nombre del proyecto "Speech_SDK_Learning_Module" y seleccione "Pago por uso."

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Seleccione su región.  Para este tutorial, seleccione "(Estados Unidos) West US". A continuación, elija "F0" para el plan de tarifa. Ahora haga clic en "crear" (que se encuentra en la esquina inferior izquierda) para crear el recurso.

   >  Nota: una vez que ha hecho clic en "crear", tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.

5. Una vez creado el recurso, aparecerá una notificación en el portal. Haga clic en esta notificación y seleccione "Vaya al recurso".

6. En la página "Inicio rápido" del servicio "LUIS API", navegue hasta el primer paso, obtener las "claves" y haga clic en "claves" (también puede lograr esto, haga clic en el hipervínculo azul "claves", que se muestra en la imagen siguiente). Esto revelará su servicio, "Claves". Guardar una copia de una de las claves para que pueda usarlo más adelante en la aplicación.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. En la página "Inicio rápido" en la sección 2b, haga clic en "Portal de Language Understanding" (se muestra en la imagen anterior) para redirigir a la página Web que usará para crear su nuevo servicio dentro de la aplicación de LUIS.

> Nota: Cuando se alcanza "Portal de Language Understanding", es posible que debe iniciar sesión, si no está ya, con las mismas credenciales que el portal de Azure. Si se trata de la primera vez que usa a LUIS, deberá desplácese hacia abajo hasta la parte inferior de la página de bienvenida, para buscar y haga clic en el botón de la aplicación "Crear LUIS".

8. Una vez iniciada la sesión, haga clic en mis aplicaciones (si no estás en esa sección actualmente). A continuación, puede hacer clic en Crear nueva aplicación. Nombre de la nueva aplicación "Módulo de aprendizaje de Speech SDK". Agregue "Módulo de aprendizaje de Speech SDK" en el campo de descripción. A continuación, haga clic en "listo".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Nota: Si la aplicación se debía para entender un idioma distinto del inglés, debe cambiar el "Culture" para el idioma adecuado.

9. Haga clic en "Build" que se encuentra en la esquina superior derecha.

10. En recursos de aplicación de la izquierda, seleccione "Intenciones", a continuación, haga clic en "Crear nuevo intento" y denomínelo "PressButton." 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Nota: es importante para los nombres de intenciones y entidades que se usa en este tutorial, dado que la aplicación Lunarcom hará referencia ellos por su nombre.  Para otros proyectos, las convenciones de nomenclatura pueden ser todo lo que desee. 
>
> Nota: ahora debe tener 2 intenciones - "PressButton" y "None".

11. En los recursos de la aplicación de la izquierda, seleccione "Entidades" y haga clic en "Crear nueva entidad" y asígnele el nombre "Action" y mantenga el tipo de entidad como "Simple".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Haga clic en "Crear nueva entidad" nuevo y asígnele el nombre "Target" y mantener así el tipo de entidad como "Simple".

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. En los recursos de la aplicación de la izquierda, seleccione "Intenciones", a continuación, haga clic en su intención de "PressButton" que creó en el paso 10.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Haga clic en la lista desplegable "Ver opciones" de la derecha y seleccione "Mostrar valores de entidad". 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Haga clic en el "Escriba un ejemplo..." cuadro de texto. A continuación, escriba las siguientes declaraciones: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Haga clic en la lista desplegable "Ver opciones" de la derecha y seleccione "Mostrar los nombres de entidad".

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Asegúrese de que cada uno de los 10 grabaciones de voz tienen las siguientes etiquetas de entidad en los lugares siguientes en 1.) al hacer clic en las palabras que están etiquetadas incorrectamente y, en el menú emergente, seleccione "quitar la etiqueta" y 2.) al hacer clic en las palabras que deben estar indicadas y, en el menú emergente, seleccione la etiqueta adecuada.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Ahora, para publicar el modelo, haga clic en "Train" en la esquina superior derecha. A continuación, una vez que haya terminado el procesamiento, haga clic en "Test" en la esquina superior derecha.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Escriba en "seleccionar el botón de inicio" en el cuadro de texto.

> Nota: no agregamos "select" como una acción en cualquiera de nuestras declaraciones - pero si hace clic en "Inspeccionar", el modelo reconoce "select" como una entidad de la acción.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Ahora, haga clic en "publicar" en la esquina superior derecha. Asegúrese de que la lista desplegable dice "Producción" y haga clic en "publicar" en la ventana emergente también. 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Una vez publicado, debe aparecer una barra verde en la parte superior de la página.  Haga clic en la barra de color verde para ir a la página "Administrar". 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Haga clic en "Claves y los puntos de conexión" en "Configuración de aplicación" a la izquierda. A continuación, establezca la lista desplegable "Publish To" como "Producción". Establezca la zona horaria para que coincida con el suyo y Active la casilla para incluir todas las puntuaciones previstas de intención. Por último, haga clic en "Asignar recursos".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Seleccione el inquilino de la primera lista desplegable y seleccione "Pago por uso" en la lista desplegable Nombre de la suscripción. En nombre de recurso de LUIS, elija el recurso que se crearon anteriormente en los pasos 1-5. A continuación, haga clic en "Asignar recursos". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Nota: asegúrese de copiar y guardar la dirección URL del extremo asociado al recurso asignamos simplemente para que sea fácilmente accesible para la sección siguiente.
>
> Nota: para el nombre del inquilino, incluya su corporación o el perfil que ha creado para esta aplicación.

23. Ahora, abra la nueva aplicación en Unity y seleccione el objeto Lunarcom_Base en la jerarquía. Haga clic en "Agregar componente" en el panel de inspector y busque y seleccione "LunarcomIntentRecognizer."

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. En el campo de Luis Endpoint de "LunarcomIntentRecognizer" en el panel del inspector, escriba la dirección URL del extremo que guardó en el paso 22. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Nota: En el componente "LunarcomOfflineRecognizer" en el panel del inspector, asegúrese de que "Deshabilitar" esté seleccionada para "SimulateOfflineMode" en caso contrario, probando el programa no funcionará. 

25. Presione el botón Reproducir en el Editor de Unity y haga clic en el botón de cohete para iniciar el reconocimiento de intenciones mediante. Auténtica la frase "Seleccione el botón de cohete de inicio".

>  Nota: La aplicación reconoce la función deseada y activa el botón rocket.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Enhorabuena

¡Oficialmente, ha aprendido cómo agregar comandos de voz desde el programa de speech SDK! Ahora su programa pueda reconocer los comandos de voz de todos los tipos de variantes. Comenzar a probarlo y divertirse un poco con ella.

[Siguiente lección: Speech SDK lección 5](placeholderlink)

