# Instalación, configuración y solución de problemas de GitHub Copilot

En esta unidad, se describe cómo registrarse en GitHub Copilot, cómo configurar GitHub Copilot mediante Visual Studio Code y algunos pasos para solucionar problemas de GitHub Copilot mediante Visual Studio Code.

## Registro en GitHub Copilot

Para poder empezar a usar GitHub Copilot, es preciso configurar una evaluación gratuita o una suscripción para tu cuenta personal.

Para ello, seleccione su foto de perfil y, después, seleccione Configuración. Copilot está en el menú de la izquierda en Código, planeamiento y automatización.

Después de registrarse, deberá instalar una extensión para su entorno preferido. GitHub Copilot admite GitHub.com, Visual Studio Code, Visual Studio, los entornos de desarrollo integrado de JetBrains y Neovim como una extensión discreta.

Para este módulo concreto, solo se van a examinar las extensiones y las configuraciones de Visual Studio Code, ya que el ejercicio que completaremos en este módulo usa Visual Studio Code.

Si usa otro entorno, puede encontrar vínculos específicos para configurarlo en la sección Referencias del final de este módulo.

## Configuración de GitHub Copilot en Visual Studio Code

### Incorporación de la extensión de Visual Studio Code

Siga estos pasos para agregar la extensión de Visual Studio Code para GitHub Copilot.

1. En Visual Studio Code Marketplace, vaya a la página de la extensión de <a href="https://marketplace.visualstudio.com/items?itemName=GitHub.copilot">GitHub Copilot</a> y seleccione Instalar.
2. Aparecerá un elemento emergente que le solicita abrir Visual Studio Code. Seleccione Open (Abrir).
3. En la pestaña Extensión: GitHub Copilot de Visual Studio Code, seleccione Instalar.
4. Si no ha autorizado previamente Visual Studio Code en su cuenta de GitHub, se le pedirá que inicie sesión en GitHub en Visual Studio Code. Seleccione Iniciar sesión en GitHub.

GitHub Copilot puede autocompletar el código a medida que lo escribe cuando usa Visual Studio Code. Después de la instalación, puede habilitar o deshabilitar GitHub Copilot, y puede configurar opciones avanzadas en Visual Studio Code.

## Habilitación o deshabilitación de GitHub Copilot en Visual Studio Code

1. Para habilitar o deshabilitar GitHub Copilot, seleccione el icono de estado del panel inferior de la ventana de Visual Studio Code

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github-copilot/media/status-icon-visual-studio-code.png"/>

2. Al deshabilitar GitHub Copilot, se le pregunta si desea deshabilitar las sugerencias globalmente, o bien para el idioma del archivo que está editando en ese momento.

-   Para deshabilitar las sugerencias de GitHub Copilot globalmente, seleccione Deshabilitar globalmente.
-   Para deshabilitar las sugerencias de GitHub Copilot para un idioma especificado, seleccione Deshabilitar para IDIOMA.

## Habilitación o deshabilitación de sugerencias insertadas en Visual Studio Code

1. En el menú Archivo, vaya a Preferencias y seleccione Configuración.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github-copilot/media/vsc-settings.png"/>

2. En el panel izquierdo de la pestaña de configuración, seleccione Extensiones y, después, seleccione Copilot.

3. En Sugerencia insertada: habilitar, seleccione o anule la selección de la casilla para habilitar o deshabilitar las sugerencias insertadas

Además, puede optar por habilitar o deshabilitar las sugerencias insertadas y especificar los idiomas para los que desea habilitar o deshabilitar GitHub Copilot.

## Solución de problemas de GitHub Copilot en Visual Studio Code

En Visual Studio Code, los archivos de registro son útiles para diagnosticar problemas de conexión. La extensión GitHub Copilot almacena los archivos de registro en la ubicación de registro estándar para las extensiones de Visual Studio Code. Puede encontrar los archivos de registro por medio de la opción de desarrollador y abrir la carpeta de registros de extensión dentro de Visual Studio Code.

En algunos casos, es posible que los errores no se registren en las ubicaciones normales. Si encuentra errores y no hay nada en los registros, puede intentar verlos en el proceso que ejecuta Visual Studio Code y la extensión. Este proceso le permite ver los registros de Electron. Puede encontrar estos registros en "Desarrollador" y en Ayuda>Activar herramientas de desarrollo en Visual Studio Code.

Al conectarse a GitHub Copilot, pueden producirse restricciones de red, firewalls o un proxy. Si esto ocurriera, siga estos pasos para abrir un nuevo editor con información pertinente que puede inspeccionar o compartir con el equipo de soporte técnico.

1. Abra la paleta de comandos Visual Studio Code:

    - En Mac, use Mayús+Comando+P
    - En Windows o Linux, use Ctrl+Mayús+P

2. Escriba `Diagnósticos` y, después, seleccione GitHub Copilot: Recopilar diagnósticos en la lista.
