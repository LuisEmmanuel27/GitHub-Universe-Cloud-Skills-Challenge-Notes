# Ejercicio: Clonación de un repositorio

Para que Alice practique cómo clonar un repositorio y realizar una solicitud de incorporación de cambios, primero se debe configurar un repositorio para que Alice lo clone.

## Configuración

1.  Use el comando mkdir para crear una carpeta denominada Cats:

        mkdir Cats

2.  Use el comando `cd` para ir a la carpeta del proyecto:

        cd Cats

3.  Ahora, inicialice el nuevo repositorio y establezca el nombre de la rama predeterminada en `main`.

    Si está ejecutando la versión 2.28.0 o una posterior de Git, use los comandos siguientes:

        git init --initial-branch=main
        git init -b main

4.  Configure Git mediante la incorporación de sus credenciales. Reemplace `<USER_NAME>` y `<USER_EMAIL>` por su propia información (por ejemplo, "Nombre de usuario" y "user-name@contoso.com").

        git config user.name "<USER_NAME>"
        git config user.email "<USER_EMAIL>"

5.  Cree algunos archivos con el comando `touch` y almacénelos provisionalmente y confírmelos mediante Git:

        touch index.html
        mkdir CSS
        touch CSS/site.css
        git add .
        git commit -m "Create empty index.html, site.css files"

6.  Agregue algún código HTML al archivo index.html mediante el editor de código de Cloud Shell, que puede abrir con el comando code en el símbolo del sistema del terminal:

        code index.html

7.  Pegue este código HTML:

        <!DOCTYPE html>
        <html>
        <head>
            <meta charset='UTF-8'>
            <title>Our Feline Friends</title>
            <link rel="stylesheet" href="CSS/site.css">
        </head>
        <body>
            <h1>Our Feline Friends</h1>
            <p>Eventually we will put cat pictures here.</p>
            <hr>
        </body>
        </html>

8.  Guarde el archivo y cierre el editor. Puede seleccionar los puntos suspensivos "..." de la esquina derecha del editor o usar el método abreviado de teclado (Ctrl+S en Windows y Linux, Cmd+S en macOS).

9.  Vaya al directorio CSS y abra site.css en el editor:

        cd CSS
        code site.css

10. Agregue el siguiente CSS a site.css:

        h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
        body { font-family: serif; }

    Luego guarde el archivo y cierre el editor.

11. Vuelva al directorio Cats.

        cd ..

12. Por último, confirme los cambios de nuevo:

        git add .
        git commit -m "Add simple HTML and stylesheet"

13. Compruebe rápidamente el registro de Git para asegurarse de que todo parezca correcto:

        git log --oneline

14. Compruebe los resultados. Debería ver una salida como la de este ejemplo:

        2bf69ab Add simple HTML and stylesheet
        bb371c8 Create empty index.html, site.css files

## Clonación de un repositorio

Ahora vamos a asumir el papel de Alice y a practicar la clonación de un repositorio para colaborar en él.

Para simular la clonación del repositorio por parte de Alice en el equipo de ella, cree un directorio denominado Alice en su equipo y clone en él el directorio del proyecto. En la vida real, esta colaboración se lograría mediante la configuración de un recurso compartido de red o un remoto accesible por medio de una dirección URL.

1.  Cree un directorio denominado Alice en el que clonar el repositorio. No debe ser un subdirectorio del directorio del proyecto (Cats), así que use cd de nuevo para ir al directorio principal desde el directorio del proyecto a fin de convertir Alice en un elemento del mismo nivel que el directorio del proyecto. Luego, use cd para ir al directorio Alice.

        cd ..
        mkdir Alice
        cd Alice

2.  Ahora use `git clone` para clonar el repositorio que se encuentra en el directorio del proyecto en el directorio Alice. Asegúrese de incluir el punto al final del comando:

        git clone ../Cats .

    `../Cats` indica a Git desde dónde debe realizar la clonación, mientras que . le indica la ubicación de destino de esta. En Unix, . hace referencia al directorio actual.

3.  Compruebe los resultados. Git debe mostrar este texto para indicarle que ha funcionado:

    Cloning into '.'...
    done.

    Ahora hay un clon del repositorio del directorio del proyecto en el directorio _Alice_.
