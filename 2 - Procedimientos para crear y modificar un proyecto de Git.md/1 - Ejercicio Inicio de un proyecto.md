# Ejercicio: Inicio de un proyecto

Ahora que ha dedicado tiempo a descubrir los comandos de Git fundamentales, pasemos a crear un proyecto en Git.

En los ejercicios que siguen, va a agregar un sencillo archivo HTML al árbol de trabajo para empezar a usar Git. Luego va a realizar algunos cambios en el directorio y a aprender a confirmar los cambios.

## Creación y adición (almacenamiento provisional) de un archivo

Git no hace mucho con los directorios vacíos, así que vamos a agregar un archivo al árbol de trabajo para que actúe como página principal del sitio web de fotos de gatos.

1.  Asegúrese de que la sesión de Cloud Shell sigue activa y de que se encuentra en la carpeta del repositorio de nombre Cats.

2.  Use un comando `touch` para crear un archivo denominado index.html:

        touch index.html

    `touch` actualiza la hora de la última modificación de un archivo, si este existe. Si el archivo no existe, Git crea un archivo vacío con ese nombre de archivo.

3.  Ahora, use `git status` para obtener el estado del árbol de trabajo:

        git status

    Git responde informándole de que no se ha confirmado nada, pero el directorio contiene un nuevo archivo:

        No commits yet

        Untracked files:
        (use "git add <file>..." to include in what will be committed)

            index.html

        nothing added to commit but untracked files present (use "git add" to track)

    Observe que `git status` ofrece sugerencias sobre lo que puede hacer a continuación. Git puede configurarse para que sea menos detallado, pero en esta fase, cuanto más, mejor.

4.  Use `git add` para agregar el nuevo archivo al índice de Git, seguido de `git status` para comprobar el estado. No olvide el punto al final del comando. Este indica a Git que indexe todos los archivos del directorio actual que se han agregado o modificado.

        git add .

    Ahora se ha almacenado provisionalmente una confirmación. El índice de Git es un área de almacenamiento provisional para las confirmaciones. Se trata de una lista de todas las versiones de archivo que van a formar parte de la `siguiente` confirmación que se haga.

    En lugar de `git add .`, podría haber usado `git add index.html`, porque index.html era el único archivo nuevo del directorio. Pero si se hubieran agregado varios archivos, `git add .` los habría incluido todos.

5.  Por último, vuelva a usar git status para asegurarse de que los cambios se han almacenado provisionalmente de forma correcta:

        git status

6.  Debería ver una salida como la de este ejemplo:

        On branch main

        Initial commit

        Changes to be committed:
        (use "git rm --cached <file>..." to unstage)

            new file:   index.html

## Realización de la primera confirmación

Ahora que index.html se ha agregado al índice, el paso siguiente consiste en confirmarlo.

1.  Utilice el comando siguiente para crear otra confirmación:

        git commit index.html -m "Create an empty index.html file"

    La marca `-m` en este comando indica a Git que está proporcionando un mensaje de confirmación.

    Hay muchas maneras de formular mensajes de confirmación, pero una buena pauta consiste en escribir la primera línea de modo que indique lo que la _confirmación hace en el árbol_. También es habitual poner en mayúsculas la primera letra y dejar fuera el punto final para ahorrar espacio. Imagine que la primera línea del mensaje completa la oración que empieza por "Cuando se inserte, esta confirmación...".

    Un mensaje de confirmación puede tener varias líneas. La primera línea no debe tener más de 50 caracteres y debe ir seguida de una línea en blanco. Las líneas siguientes no deben tener más de 72 caracteres. No se trata de requisitos estrictos, y se remontan a los días de las tarjetas perforadas y los terminales "tontos", pero mejoran el aspecto de la salida de `git log`.

2.  Git responde con una confirmación de lo que ha hecho:

        [main (root-commit) 87e874c] Create an empty index.html file
        1 file changed, 0 insertions(+), 0 deletions(-)
        create mode 100644 index.html

3.  Realice un seguimiento con un comando `git status` y confirme que el árbol de trabajo está limpio, es decir, que no contiene cambios sin confirmar.

4.  Ahora, use un comando `git log` para mostrar información sobre la confirmación:

        git log

5.  La respuesta de Git debería ser similar a este ejemplo:

        commit 87e874c4aeeb3f9692ae5d9875235353708d7dd5
        Author: User Name <user-name@contoso.com>
        Date:   Fri Nov 15 20:47:05 2019 +0000

        Create an empty index.html file

## Modifique index.html y confirme el cambio.

_index.html_ se ha creado para servir como página principal del sitio web, pero actualmente está vacío. El siguiente paso es agregarle algún código HTML. Para hacerlo sencillo, vamos a usar el editor integrado de Cloud Shell para agregar una sola línea de HTML.

1.  Abra index.html en el editor en línea escribiendo `code index.html` en el símbolo del sistema de Terminal:

        code index.html

2.  Escriba o pegue las instrucciones siguientes en el editor:

        <h1>Our Feline Friends</h1>

3.  Guarde el archivo y cierre el editor en línea. Puede seleccionar los puntos suspensivos "..." de la esquina derecha del editor de Cloud Shell o usar la tecla de aceleración (Ctrl+S en Windows y Linux, Cmd+S en macOS).

4.  Use un comando `git status` para comprobar el estado del árbol de trabajo:

        git status

5.  Puede ver que Git es consciente de los cambios realizados:

        On branch main
        Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git checkout -- <file>..." to discard changes in working directory)

            modified:   index.html

        no changes added to commit (use "git add" and/or "git commit -a")

6.  Ahora, confirme los cambios:

        git commit -a -m "Add a heading to index.html"

    Observe que esta vez no se ha ejecutado el comando `git add` para almacenar provisionalmente los cambios. En su lugar, usamos la marca `-a` en el comando `git commit`. La opción `-a` agrega todos los archivos que se han modificado desde la última confirmación. No agregará archivos nuevos. Para agregar nuevos archivos, se sigue necesitando `git add`.

7.  Compruebe los resultados. Deberían parecerse a los de este ejemplo:

        [main 8c9143a] Add a heading to index.html
        1 file changed, 1 insertion(+)

Se ha confirmado el cambio en _index.html_. Ahora hay dos versiones del archivo en el repositorio, aunque solo se ve una de ellas (la actual). Una de las ventajas de usar Git es que se pueden revertir los cambios realizados o retroceder en el tiempo y ver las versiones anteriores. Veremos más cosas sobre este tema tan importante más adelante.
