# Ejercicio: Agregar la extensión GitHub Copilot

El objetivo es desarrollar una aplicación de minijuego de consola Python mediante GitHub Copilot. Como está trabajando en un Codespace, necesita instalar la extensión GitHub Copilot actualizando el archivo de configuración del contenedor de desarrollo.

¿Qué es un contenedor de desarrollo?
Los contenedores de desarrollo son contenedores de Docker que están configurados para proporcionar un entorno de desarrollo completo. Siempre que trabaje en un codespace, estará usando un contenedor de desarrollo en una máquina virtual.

Puede configurar el contenedor de desarrollo para un repositorio y Codespaces puede crear un entorno de desarrollo a medida, con todas las herramientas y runtimes que necesita para trabajar en un proyecto específico.

En este diagrama de la <a href="https://code.visualstudio.com/docs/devcontainers/containers">documentación oficial de Visual Studio Code</a> se muestra esta funcionalidad.

<img src="https://learn.microsoft.com/es-mx/training/modules/challenge-project-create-mini-game-with-copilot/includes/media/dev-container.png">

## Especificación

En este ejercicio de desafío, debe abrir la carpeta devcontainer y actualizar el archivo JSON devcontainer.json para agregar la extensión GitHub Copilot.

-   Codespaces identifica las extensiones necesarias mediante su marketplace de Visual Studio Codeid.
-   La identificación de la extensión GitHub Copilot es GitHub.copilot.

Al agregar la extensión GitHub Copilot a este archivo, se garantiza que está instalado en el contenedor de desarrollo y está disponible para su uso en Codespace.

## Comprobar el trabajo

1.  Acceda a Codespaces y abra el archivo app.py en Visual Studio Code.

2.  Empiece a escribir el comentario:

        # write 'hello world' to the console

3.  GitHub Copilot debe completar el código. El resultado debería asemejarse al código siguiente:

        # write 'hello world' to the console
        print('hello world')

4.  Ejecute la aplicación con el comando `python app.py` en el terminal y compruebe si el resultado es similar al siguiente mensaje de consola:

        hello world

Tras validar los resultados de este ejercicio, continúe con el siguiente ejercicio de este desafío.
