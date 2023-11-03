# Ejercicio: Realización de cambios y seguimiento de estos con Git

La mayoría de los proyectos de desarrollo son iterativos. Se escribe algún código y luego se prueba para asegurarse de que funciona. Luego se escribe más código y se invita a otras personas a contribuir. La iteración significa que hay muchos cambios: adiciones de código, correcciones de errores, eliminaciones y sustituciones.

A medida que trabaje en el proyecto, Git le ayudará a realizar un seguimiento de los cambios que realice. También permite deshacer errores. En los ejercicios siguientes va a continuar compilando el sitio web en el que está trabajando y a aprender algunos nuevos comandos importantes, como git `diff`.

## Modificación de index.html

La página principal del sitio web, _index.html_, de momento contiene una sola línea de HTML. Vamos a actualizarla para hacer más cosas y luego a confirmar el cambio en Git.

1.  Vuelva a abrir el archivo _index.html_ en el editor en línea de Cloud Shell (`code index.html`) y reemplace el contenido del archivo por el siguiente código HTML:

        <!DOCTYPE html>
        <html>
            <head>
                <meta charset='UTF-8'>
                <title>Our Feline Friends</title>
            </head>
            <body>
                <h1>Our Feline Friends</h1>
                <p>Eventually we will put cat pictures here.</p>
                <hr>
            </body>
        </html>

2.  Guarde el archivo y cierre el editor en línea.

3.  Use un comando git diff para ver lo que ha cambiado:

        git diff

    El formato de salida es el mismo que el del comando `diff` de Unix, y el comando de Git tiene muchas de las mismas opciones. Aparece un signo "más" delante de las líneas que se han agregado, y un signo "menos" indica las líneas que se han eliminado.

    El valor predeterminado para comparar el árbol de trabajo con el índice es `git diff`. Es decir, muestra todos los cambios que aún no se han almacenado provisionalmente (agregado al índice de Git). Para comparar el árbol de trabajo con la última confirmación, puede usar `git diff HEAD`.

    Si el comando no vuelve al símbolo del sistema después de ejecutarse, escriba `q` para salir de la vista de diferencias.

4.  Ahora confirme el cambio. En lugar de usar la marca `-a`, puede asignar explícitamente un nombre a un archivo para que se almacene provisionalmente y se confirme si Git ya lo tiene en el índice (el comando `commit` solo comprueba la existencia de un archivo).

        git commit -m "Add HTML boilerplate to index.html" index.html

5.  Use git diff de nuevo para comparar el árbol de trabajo con el índice:

        git diff

    Esta vez `git diff` no genera ninguna salida porque el árbol de trabajo, el índice y `HEAD` concuerdan.

6.  Digamos que decide que "peludo" suena más amigable que "felino". Sustituya las dos apariciones de "Felino" en index.html por "Peludo". A continuación, guarde el archivo.

Si ha usado el editor de código integrado con el comando `code`, no verá nada inusual. Pero si ha usado otro editor, como uno llamado sed, es probable que haya creado un archivo index.html.bak que no quiere confirmar. Editores como Vim y Emacs crean archivos de copia de seguridad con nombres como index.html~ y index.html.~1~, en función de cómo estén configurados.

7.  Use el comando siguiente para crear y abrir un archivo denominado .gitgnore en el editor de código integrado:

        code .gitignore

8.  Agregue las líneas siguientes al archivo:

        *.bak
        *~

    Esta línea indica a Git que omita los archivos cuyos nombres de archivo terminan en _.bak_ o ~.

    _.gitignore_ es un archivo muy importante en el mundo de Git porque impide que los archivos extraños se envíen al control de versiones. Hay archivos _.gitignore_ reutilizables disponibles para lenguajes y entornos de programación populares.

9.  Guarde y cierre el editor y luego use estos comandos para confirmar los cambios:

        git add -A
        git commit -m "Make small wording change; ignore editor backups"

Si en este momento usa `git diff`, la salida estará vacía porque los cambios se han confirmado. Sin embargo, siempre puede usar un comando `git diff HEAD^` para comparar las diferencias entre la confirmación más reciente y la anterior. Pruébelo y vea. No olvide incluir el carácter `^` de cursor de inserción al final del comando.

## Adición de un subdirectorio

La mayoría de los sitios web usan hojas de estilo CSS y HTML, y el sitio que está compilando no es una excepción. Normalmente, las hojas de estilo se almacenan en un subdirectorio, así que vamos a crear uno llamado CSS y a agregarlo al repositorio.

1.  Empiece por crear un subdirectorio llamado CSS en el directorio del proyecto:

        mkdir CSS

2.  Luego ejecute git status:

        git status

    ¿Por qué indica Git que no hay nada que confirmar?

    Los usuarios a menudo se sorprenden al saber que Git no considera que agregar un directorio vacío sea un cambio. Esto se debe a que Git solo realiza el seguimiento de los cambios en los archivos, no en los directorios.

    En ocasiones, especialmente en las fases iniciales de desarrollo, quiere tener directorios vacíos como marcadores de posición. Una convención común es crear un archivo vacío, a menudo llamado .git-keep, en un directorio de marcador de posición.

3.  Use los comandos siguientes para crear un archivo vacío con ese nombre en el subdirectorio CSS y agregue el contenido del subdirectorio al índice:

        touch CSS/.git-keep
        git add CSS

4.  Vuelva a realizar un seguimiento mediante `git status` para comprobar el estado del repositorio. Confirme que informa de un nuevo archivo.

# Reemplazo de un archivo

Ahora vamos a reemplazar _.git-keep_ por un archivo CSS y a actualizar index.html para hacer referencia a él.

1.  Elimine .git-keep del subdirectorio CSS:

        rm CSS/.git-keep

2.  Use el editor integrado para crear un archivo denominado site.css en el subdirectorio CSS:

        cd CSS
        code site.css

3.  Agregue el siguiente CSS al archivo. Después, guarda y cierra el archivo.

        h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
        body { font-family: serif; }

4.  Ahora agregue la siguiente línea a _index.html_ (no olvide volver al directorio Cats) después de la línea `<title>` y guarde el archivo modificado:

        <link rel="stylesheet" href="CSS/site.css">

5.  Use `git status` para ver un resumen de los archivos que han cambiado. Luego, use los siguientes comandos para almacenar provisionalmente los archivos sin seguimiento en el control de versiones y confirmar los cambios en site.css e _index.html_:

        git add .
        git commit -m "Add a simple stylesheet"

A diferencia de la mayoría de los VCS, Git registra el contenido de los archivos en lugar de las diferencias (cambios) entre ellos. Esto es en gran medida lo que hace que la confirmación, la bifurcación y el cambio entre ramas sean tan rápidos en Git. Otros VCS tienen que aplicar una lista de cambios que se quieren obtener entre una versión de un archivo y otra. Git solo descomprime la otra versión.

# Enumeración de las confirmaciones

Ahora que tiene un número razonable de cambios registrados, puede usar `git log` para verlos. Al igual que con la mayoría de los comandos de Git, hay muchas opciones entre las que elegir. Uno de los ejemplos más útiles es `--oneline`.

1.  Use el comando siguiente para revisar todas las confirmaciones:

        git log

2.  Compruebe los resultados. Deben tener un aspecto similar a este ejemplo:

        commit ae3f99c45db2547e59d8fcd8a6723e81bbc03b70
        Author: User Name <user-name@contoso.com>
        Date:   Fri Nov 15 22:04:05 2019 +0000

            Add a simple stylesheet

        commit 4d07803d7c706bb48c52fcf006ad50946a2a9503
        Author: User Name <user-name@contoso.com>
        Date:   Fri Nov 15 21:59:10 2019 +0000

            Make small wording change; ignore editor backups

        ...

3.  Ahora, use este comando para obtener una lista más concisa:

        git log --oneline

4.  Vuelva a comprobar la salida. Esta vez debe parecerse a este ejemplo:

        ae3f99c Add a simple stylesheet
        4d07803 Make small wording change; ignore editor backups
        f827c71 Add HTML boilerplate to index.html
        45535f0 Add a heading to index.html
        a69fe78 Create an empty index.html file

Puede ver por qué cuando hay cientos (o miles) de confirmaciones en un proyecto la opción `--oneline` puede ser su mejor aliada. Otra opción útil es `-nX`, donde `X` es un número de confirmación: 1 para la última confirmación, 2 para la anterior, y así sucesivamente. Para verlo, pruebe un comando `git log -n2`.

Hemos avanzado mucho en cuanto al uso de la funcionalidad básica de Git. A continuación, suba de nivel y aprenda a usar Git para recuperarse de errores comunes.
