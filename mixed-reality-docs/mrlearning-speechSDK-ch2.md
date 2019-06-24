## <a name="lesson-2"></a><span data-ttu-id="45aa8-101">Lección 2</span><span class="sxs-lookup"><span data-stu-id="45aa8-101">Lesson 2</span></span>

<span data-ttu-id="45aa8-102">En la lección 2, agregaremos un modo sin conexión que nos permitirá realizar la traducción de voz a texto local cuando no se puede conectar al servicio de Azure y se lo *simular* estado desconectado.</span><span class="sxs-lookup"><span data-stu-id="45aa8-102">In Lesson 2, we will add an Offline mode that will allow us to perform local speech-to-text translation when we are unable to connect to the Azure service and we will *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="45aa8-103">Seleccione el objeto "Lunarcom_Base" en la jerarquía y haga clic en "Agregar componente" en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="45aa8-103">Select the "Lunarcom_Base" object in the hierarchy and click “Add Component” in the inspector panel.</span></span> <span data-ttu-id="45aa8-104">Busque y seleccione el "reconocimiento sin conexión Lunarcom".</span><span class="sxs-lookup"><span data-stu-id="45aa8-104">Search for and select the "Lunarcom Offline Recognition."</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)



2. <span data-ttu-id="45aa8-106">Haga clic en la lista desplegable en la sección "LunarcomOfflineRecognizer" y seleccione "Habilitado".</span><span class="sxs-lookup"><span data-stu-id="45aa8-106">Click the dropdown in the “LunarcomOfflineRecognizer” and select “Enabled.”</span></span> <span data-ttu-id="45aa8-107">Esto programará el proyecto para que actúe como el usuario no tiene conexión.</span><span class="sxs-lookup"><span data-stu-id="45aa8-107">This will program the project to act like the user doesn't have connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="45aa8-109">Ahora, presione reproducir en el Editor de Unity y probarlo.</span><span class="sxs-lookup"><span data-stu-id="45aa8-109">Now, press play on the Unity Editor and test it.</span></span> <span data-ttu-id="45aa8-110">Presione el micrófono en la esquina inferior izquierda de la escena y empiece a hablar.</span><span class="sxs-lookup"><span data-stu-id="45aa8-110">Press the microphone in the bottom left hand corner in the scene and begin speaking.</span></span> 

> <span data-ttu-id="45aa8-111">Nota: ya se están sin conexión, se ha deshabilitado la funcionalidad Wake Word.</span><span class="sxs-lookup"><span data-stu-id="45aa8-111">note: because we’re offline, the Wake Word functionality has been disabled.</span></span> <span data-ttu-id="45aa8-112">Por lo tanto, tendrá que físicamente cada vez que desea que su voz reconoce, haga clic en el micrófono mientras sin conexión.</span><span class="sxs-lookup"><span data-stu-id="45aa8-112">So, you will have to physically click the microphone every time you wish to have your speech recognized while offline.</span></span> 

<span data-ttu-id="45aa8-113">A continuación es un ejemplo del aspecto que podría tener la escena:</span><span class="sxs-lookup"><span data-stu-id="45aa8-113">Below is an example of what your scene could look like:</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="45aa8-115">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="45aa8-115">Congratulations</span></span>

<span data-ttu-id="45aa8-116">Se ha habilitado el modo sin conexión.</span><span class="sxs-lookup"><span data-stu-id="45aa8-116">The offline mode has been enabled!</span></span> <span data-ttu-id="45aa8-117">Ahora cuando esté fuera de cualquier forma de internet, puede trabajar en el proyecto con el SDK de voz.</span><span class="sxs-lookup"><span data-stu-id="45aa8-117">Now when you're away from any form of internet, you can still work on your project with Speech-SDK!</span></span> 

[<span data-ttu-id="45aa8-118">Siguiente lección: SpeechSDK lección 3</span><span class="sxs-lookup"><span data-stu-id="45aa8-118">Next Lesson: SpeechSDK Lesson 3</span></span>](link placeholder)

