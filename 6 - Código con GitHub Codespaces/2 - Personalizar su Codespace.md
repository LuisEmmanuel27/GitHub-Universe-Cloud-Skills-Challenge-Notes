# Personalizar su Codespace

GitHub Codespaces es un entorno dedicado. Puede configurar los repositorios con un contenedor de desarrollo para definir su entorno predeterminado de GitHub Codespaces y personalizar la experiencia de desarrollo en todos los codespaces con dotfiles y Sincronización de configuración.

## Qué se puede personalizar

Existen muchas formas de personalizar su codespace. Se revisarán a continuación.

-   `Sincronización de configuración`: puede sincronizar la configuración de Visual Studio Code (VS Code) entre la aplicación de escritorio y el cliente web de VS Code.

-   `Dotfiles`: puede usar un repositorio dotfiles para especificar scripts, preferencias del shell y otras configuraciones.

-   `Cambiar un codespace de nombre`: al crear un codespace, se le asigna un nombre para mostrar generado automáticamente. Si tiene varios codespaces, el nombre para mostrar le ayuda a diferenciar entre ellos. Puede cambiar el nombre para mostrar del codespace.

-   `Cambiar el shell`: puede cambiar el shell en un codespace para mantener su configuración habitual. Al trabajar en un codespace, puede abrir una nueva ventana de terminal con un shell de su elección, cambiar el shell predeterminado para las nuevas ventanas de terminal o instalar un nuevo shell. También puedes usar dotfiles para configurar el shell.

-   `Cambiar el tipo de máquina`: puede cambiar el tipo de máquina que ejecuta el codespace para usar los recursos adecuados para el trabajo que lleva a cabo.

-   `Establecer el editor predeterminado`: puede establecer el editor predeterminado para codespaces en su página de configuración personal. Establezca el editor de su preferencia para que, al crear un codespace o abrir un codespace existente, se abra en el editor predeterminado.

    -   Visual Studio Code (aplicación de escritorio)
    -   Visual Studio Code (aplicación cliente web)
    -   JetBrains Gateway: para abrir codespaces en un IDE de JetBrains
    -   JupyterLab (interfaz web para Project Jupyter)

-   `Establecer la región predeterminada`: puede configurar la región predeterminada en la página de configuración de perfil de GitHub Codespaces para personalizar el lugar donde se conservan sus datos.

-   `Establecer el tiempo de espera`: un codespace dejará de ejecutarse después de un período de inactividad. De manera predeterminada, este período es de 30 minutos, pero puede especificar un período de tiempo de espera predeterminado más largo o más corto en su configuración personal en GitHub. La configuración actualizada se aplica a los codespaces que cree o a los ya existentes la próxima vez que los inicie.

-   `Configuración de eliminación automática`: los codespaces inactivos se eliminan de forma automática. Puede elegir cuánto tiempo se conservan los codespaces detenidos, hasta un máximo de 30 días.

En la unidad Resumen, al final de este módulo, existe información adicional e instrucciones detalladas relativas a la personalización.

## Agregar al codespace con extensiones o complementos

Puede agregar complementos y extensiones en un codespace para personalizar su experiencia en JetBrains y VS Code.

## Extensiones de VS Code

Si trabaja en sus codespaces en el cliente web o la aplicación de escritorio de VS Code, puede agregar cualquier extensión que necesite desde Visual Studio Code Marketplace. Consulte el artículo sobre <a href="https://code.visualstudio.com/api/advanced-topics/remote-extensions">compatibilidad con el desarrollo remoto y GitHub Codespaces</a> en la documentación de VS Code para obtener información sobre cómo se ejecutan las extensiones en GitHub Codespaces.

Si ya utiliza VS Code, puede usar Sincronización de configuración para sincronizar automáticamente las extensiones, configuraciones, temas y métodos abreviados de teclado entre la instancia local y cualquier codespace que cree.

Complementos de JetBrains
Si trabaja con los codespaces en un IDE de JetBrains, puede agregar complementos desde el Marketplace de JetBrains.
