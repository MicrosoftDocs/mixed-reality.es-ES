## <a name="lesson-2"></a>Lección 2

En la lección 2, agregaremos un modo sin conexión que nos permitirá realizar la traducción de voz a texto local cuando no se puede conectar al servicio de Azure y se lo *simular* estado desconectado.

1. Seleccione el objeto "Lunarcom_Base" en la jerarquía y haga clic en "Agregar componente" en el panel del inspector. Busque y seleccione el "reconocimiento sin conexión Lunarcom".

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. Haga clic en la lista desplegable en la sección "LunarcomOfflineRecognizer" y seleccione "Habilitado". Esto programará el proyecto para que actúe como el usuario no tiene conexión. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. Ahora, presione reproducir en el Editor de Unity y probarlo. Presione el micrófono en la esquina inferior izquierda de la escena y empiece a hablar. 

> Nota: ya se están sin conexión, se ha deshabilitado la funcionalidad Wake Word. Por lo tanto, tendrá que físicamente cada vez que desea que su voz reconoce, haga clic en el micrófono mientras sin conexión. 

A continuación es un ejemplo del aspecto que podría tener la escena:

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Enhorabuena

Se ha habilitado el modo sin conexión. Ahora cuando esté fuera de cualquier forma de internet, puede trabajar en el proyecto con el SDK de voz. 

[Siguiente lección: SpeechSDK lección 3](link placeholder)

