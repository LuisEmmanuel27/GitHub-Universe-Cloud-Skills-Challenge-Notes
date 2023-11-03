# Ejercicio: Resolución de conflictos de combinación

A veces, independientemente de lo bien que lo planee todo, las cosas salen mal. Imagine que dos desarrolladores están trabajando en el mismo archivo del proyecto al mismo tiempo. El primer desarrollador envía sus cambios a la rama `main` del repositorio del proyecto sin ningún problema. Cuando el segundo desarrollador intenta enviar los cambios, Git indica que hay un conflicto de combinación. El archivo que el segundo desarrollador está intentando modificar ya no está actualizado con los cambios o la versión de archivo más recientes. La versión de archivo debe estar actualizada antes de que se puedan combinar los cambios del segundo desarrollador. Una de las principales preocupaciones de los desarrolladores que usan el control de versiones es un conflicto de combinación.

Pueden producirse conflictos como este, por lo que debe saber cómo tratarlos. La buena noticia es que Git ofrece soluciones para tratar los conflictos de combinación.

## Creación de ramas para Alice y Bob

Comencemos por crear una rama para Alice y otra para Bob. Ambos amigos desarrolladores están actualizando los archivos del repositorio del proyecto al mismo tiempo. No son conscientes de los cambios que realiza el otro porque están realizando las actualizaciones en sus ramas locales.

1.  Asegúrese de que se encuentra en el directorio Alice y, a continuación, cree una rama denominada `add-cat` para que Alice trabaje en:

        git checkout -b add-cat

2.  Cambie al directorio `Bob` y, después, cree una rama denominada `style-cat` para que Bob trabaje en:

        cd ../Bob
        git checkout -b style-cat

Ahora vamos a realizar algunos cambios en las ramas.

## Realización de un cambio como Alice

Para empezar, suponga que tiene el rol de Alice y realice un cambio en la página principal del sitio web. Reemplace la imagen del gato de Bob por una fotografía del de Alice.

1.  Vuelva a cambiar al directorio Alice:

        cd ../Alice

2.  Abra el archivo index.html y, a continuación, reemplace esta instrucción (que usa una de las imágenes del gato de Bob):

        <img src="Assets/bobcat2-317x240.jpg" />

    Con esta instrucción (que usa una de las imágenes del gato de Alice):

        <img class="cat" src="Assets/bombay-cat-180x240.jpg" />

3.  Guarde el archivo y cierre el editor.

4.  Ahora, ejecute los siguientes comandos de Git para enviar los cambios al repositorio del proyecto. En primer lugar, vamos a agregar las confirmaciones realizadas en la carpeta Assets (Recursos). Después, volveremos a la rama `main` y ejecutaremos `git pull` para asegurarnos de que no haya cambiado nada. Por último, vamos a combinar la rama local `add-cat` con la rama `main` y, después, enviaremos los cambios al repositorio.

        git add Assets
        git commit -a -m "Add picture of Alice's cat"
        git checkout main
        git pull
        git merge --ff-only add-cat
        git push

Por último, es necesario confirmar que el envío de cambios se ha realizado correctamente.

## Realización de un cambio como Bob

Sin saber lo que está haciendo Alice, Bob observa que el último envío de cambios de Alice ha agregado un estilo CSS denominado `cats` al archivo site.css para el repositorio. Por tanto, Bob decide aplicar esa clase a la imagen de su gato.

1.  Vuelva al directorio Bob:

        cd ../Bob

2.  Abra el archivo _index.html_ y reemplace la instrucción que usa la imagen del gato de Bob por la siguiente instrucción que agrega un atributo class="cat" al elemento <img>:

        <img class="cat" src="Assets/bobcat2-317x240.jpg" />

3.  Guarde el archivo y cierre el editor.

4.  Ahora, ejecute los siguientes comandos de Git para sincronizar los cambios en el repositorio del proyecto, como hizo para las actualizaciones en el repositorio de Alice. Confirme el cambio, cambie a la rama `main`, ejecute `git pull` y, a continuación, combine el cambio de estilo:

        git commit -a -m "Style Bob's cat"
        git checkout main
        git pull
        git merge style-cat

Y ahí está: el temido _conflicto de combinación_. Dos personas han cambiado la misma línea en el mismo archivo. Git detecta el conflicto y notifica un error de combinación automática. Git no tiene forma de saber si el atributo `src` del elemento `<img>` debe hacer referencia a los archivos bobcat2-317x240.jpg o bombay-cat-180x240.jpg.

        Auto-merging index.html
        CONFLICT (content): Merge conflict in index.html
        Automatic merge failed; fix conflicts and then commit the result.

La salida de Git identifica el archivo index.html como origen del conflicto.

La pregunta ahora es: ¿Qué puede hacer Bob?

## Resolución del conflicto de combinación

Bob tiene pocas opciones en este momento. Bob puede realizar una de estas acciones:

-   Ejecute el comando `git merge --abort` para restaurar la rama `main` a su estado anterior a la combinación intentada. Ejecute el comando `git pull` para obtener los cambios de Alice. A continuación, cree una rama, realice los cambios y combine su rama con la rama `main`. Por último, envían los cambios.

-   Ejecute el comando `git reset --hard` para volver a la ubicación en la que estaban antes de que iniciaran la combinación.

-   Resuelva el conflicto manualmente mediante la información que Git inserta en los archivos afectados.

Los desarrolladores parecen preferir la última opción. Cuando Git detecta un conflicto en las versiones del contenido, inserta ambas versiones del contenido en el archivo. Git usa un formato especial para ayudarle a identificar y resolver el conflicto: corchetes angulares de apertura `<<<<<<<`, guiones dobles (signos igual) `=======` y corchetes angulares de cierre `>>>>>>>`. El contenido situado encima de la línea de guiones `=======` muestra los cambios en la rama. El contenido que se encuentra debajo de la línea de separación muestra la versión del contenido de la rama en la que intenta realizar la combinación.

Este es el aspecto ahora del archivo _index.html_ del repositorio de Bob. Tenga en cuenta el formato especial que rodea el contenido con conflictos:

        <!DOCTYPE html>
        <html>
            <head>
                <meta charset='UTF-8'>
                <title>Our Feline Friends</title>
                <link rel="stylesheet" href="CSS/site.css">
            </head>
            <body>
                <nav><a href="./index.html">home</a></nav>
                <h1>Our Feline Friends</h1>
                <<<<<<< HEAD
                <img class="cat" src="Assets/bombay-cat-180x240.jpg">
                =======
                <img class="cat" src="assets/bobcat2-317x240.jpg">
                >>>>>>> style-cat
                <footer><hr>Copyright (c) 2021 Contoso Cats</footer>
            </body>
        </html>

Vamos a resolver el conflicto de combinación mediante la edición del archivo _index.html_. Dado que este conflicto de combinación se corrige rápidamente, realizará el cambio directamente en la rama `main`, aunque todavía esté en el directorio Bob.

1.  Abra el archivo _index.html_ y, a continuación, elimine las líneas de formato especiales. No quite ninguna otra instrucción.

        <<<<<<< HEAD
        =======
        >>>>>>> style-cat

2.  Guarde el archivo y cierre el editor.

    El archivo _index.html_ ahora tiene dos elementos `<img>`: uno para la imagen del gato de Bob y otro para la del gato de Alice.

    Algunos editores de texto incluyen la integración de Git y ofrecen ayuda cuando ven texto que indica un conflicto de combinación. Si abre el archivo _index.html_ en Visual Studio Code, verá el código siguiente:

    <center>
    <img src="https://learn.microsoft.com/es-mx/training/modules/branch-merge-git/media/resolve-conflict.png"/>
    </center>

    Si selecciona `Aceptar ambos cambios`, el editor quita las líneas alrededor de los elementos `<img>` y los dos elementos permanecen intactos.

3.  Ejecute los comandos siguientes para confirmar el cambio:

        git add index.html
        git commit -a -m "Style Bob's cat"

    El comando `git add` indica a Git que se ha resuelto el conflicto en el archivo _index.html_.

4.  Envíe los cambios a la rama main en el repositorio remoto:

        git push

5.  Ahora, sincronice los cambios con el repositorio de Alice:

        cd ../Alice
        git pull

6.  Por último, abra el archivo _index.html_ de Alice y confirme que su versión también tiene dos etiquetas `<img>` con imágenes de gatos.
