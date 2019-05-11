# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>La realización de explorador Galaxy para HoloLens 2

Este es el recorrido de cómo estamos actualizando el Explorador de Galaxy para HoloLens 2. [Explorador Galaxy](https://docs.microsoft.com/en-us/windows/mixed-reality/galaxy-explorer "Explorer Galaxy") fue desarrollado originalmente como una aplicación de código abierto para HoloLens (gen 1) a través del programa de la Idea de su recurso compartido, y es una de las primeras experiencias de realidad mixta tenían muchas personas. Ahora vamos a actualizar como parte de la [capacidades nuevas y emocionantes de HoloLens 2](https://www.microsoft.com/en-gb/hololens/hardware).

Como uno de los Studios(1) de realidad mixta de Microsoft, se suele desarrollar soluciones de calidad comercial y estamos desarrollando & pruebas en plataformas de destino durante el proceso de desarrollo y la creatividad. Tenemos ahora la única situación aún donde no tiene acceso a los dispositivos HoloLens 2, pero estamos encantados de iniciar las actualizaciones al explorador Galaxy. Nos estamos embarcarse en este proyecto utilizando las herramientas y marcos (como [MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) como estén disponibles para nosotros y la Comunidad - y queremos ofrecerle a lo largo de la carrera.

Al igual que el Explorador de Galaxy original, estaremos [abrir el proyecto en GitHub](https://github.com/Microsoft/GalaxyExplorer) para asegurarse de que la Comunidad tiene acceso completo. También se a documentar nuestro recorrido por aquí en transparencia completa acerca de las maneras en que llevamos a cabo portabilidad de MRTK v1 a v2 MRTK, cómo se ha mejorado la experiencia en función de las nuevas características disponibles en el 2 de HoloLens y cómo se garantiza que el Explorador de Galaxy seguía siendo un experiencia en múltiples plataformas. Por lo que si está viendo el Explorador de Galaxy en HoloLens (gen 1), 2 de HoloLens, auriculares de realidad mixta de Windows o en el escritorio de Windows 10, queremos asegurarse de que tiene una experiencia realmente cautivadora y disfrutar de viaje como estamos!

Esta página se expandirá a medida que progresamos en el proyecto, e incluiremos los vínculos a artículos más detallados, código, artefactos de diseño, documentación adicional de v2 MRTK, etc. para proporcionarle un análisis en el proyecto.



(1) los equipos de Microsoft Mixed Reality Studio - ubicados América, Europa y Asia Pacífico - son expertos en diseño de la experiencia de usuario, la informática holográfica, VR o AR tecnologías y desarrollo 3D; incluidas la creación de activos 3D, DirectX, Unity y Unreal. Ayudamos a envision futures deseados, diseñar, compilar y entregar soluciones de, al tiempo que permite a los clientes crear impacto cuantificable en toda su organización. Los estudios trabajan estrechamente con más 22.000 profesionales de Microsoft Services para la integración de aplicaciones empresariales, adopción, operaciones y soporte técnico.