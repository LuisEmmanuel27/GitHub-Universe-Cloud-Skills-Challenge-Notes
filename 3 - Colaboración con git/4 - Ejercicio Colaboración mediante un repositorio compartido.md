# Ejercicio: Colaboración mediante un repositorio compartido

La incorporación de cambios directa desde el repositorio de otro usuario funciona, siempre que ambos estén en la misma red. Pero es un proceso burdo, y la mayoría de los colaboradores no están en la misma red. Es mejor configurar un repositorio central en el que todos los colaboradores pueden insertar y enviar.

Cuando le habla a su amigo desarrollador Bob sobre su proyecto y este le pide participar, eso es exactamente lo que decide hacer: configurar un repositorio central, que también se conoce como repositorio vacío.

## Creación de un repositorio vacío

Lo que necesita es un repositorio que no tenga árbol de trabajo. Un repositorio vacío tiene varias ventajas con respecto a un árbol de trabajo:

-   Sin un árbol de trabajo, todo el mundo puede enviar cambios sin tener que preocuparse de qué rama se extrae del repositorio.
-   Para Git es fácil detectar si otro usuario ha enviado cambios que podrían entrar en conflicto con los suyos.
-   Un repositorio compartido se escala a cualquier número de desarrolladores. Con un repositorio vacío solo tiene que saber sobre el repositorio compartido y no sobre los demás colaboradores de los que puede que tenga que incorporar.
-   Al colocar el repositorio compartido en un servidor al que todos pueden acceder, no tiene que preocuparse por los firewalls ni los permisos.
-   No necesita cuentas independientes en el servidor, ya que Git realiza un seguimiento de quién ha realizado cada confirmación. (GitHub tiene millones de usuarios que comparten la cuenta git. Todos usan el protocolo de red criptográfico de Secure Shell (SSH) y los usuarios se distinguen por sus claves públicas).

Crear un repositorio vacío para compartir es sencillo:

1.  Cree un nuevo directorio denominado `Shared.git` en el mismo nivel que los directorios Alice y Cats para que contenga el repositorio vacío:

        cd ..
        mkdir Shared.git
        cd Shared.git

    El nombre del directorio no tiene importancia, pero en estos ejercicios nos referiremos a él como el directorio `Shared.git` o simplemente como el directorio _compartido_.

    Al asignar al directorio el nombre `Shared.git` se sigue la larga tradición de asignar a los repositorios vacíos un nombre que finaliza en `.git` para distinguirlos de los árboles de trabajo. Se trata de una convención, no de un requisito.

2.  Ahora use el siguiente comando para crear un repositorio vacío en el directorio compartido:

        git init --bare

3.  Cuando un repositorio todavía está vacío, no se puede usar el comando git checkout para establecer el nombre de la rama predeterminada. Para realizar esta tarea, puede cambiar la rama HEAD para que apunte a otra rama; en este caso es la rama main:

        git symbolic-ref HEAD refs/heads/main

4.  El siguiente paso consiste en obtener el contenido de su repositorio en el repositorio compartido. Use estos comandos para volver al directorio del proyecto donde está almacenado el repositorio, configure un remoto origin y realice un envío de cambios inicial:

        cd ../Cats
        git remote add origin ../Shared.git
        git push origin main

5.  Compruebe los resultados. La salida debería indicar que la operación se ha realizado correctamente:

        Counting objects: 12, done.
        Delta compression using up to 2 threads.
        Compressing objects: 100% (8/8), done.
        Writing objects: 100% (12/12), 1.07 KiB | 0 bytes/s, done.
        Total 12 (delta 1), reused 0 (delta 0)
        To ../Shared.git
        * [new branch]      main -> main

6.  Quiere que `push` y `pull` usen de manera predeterminada la rama `main` de `origin`, como si se hubiera creado el repositorio clonándolo. Pero primero debe indicar a Git la rama cuyo seguimiento se va a efectuar.

        git branch --set-upstream-to origin/main

7.  Busque esta salida:

        Branch main set up to track remote branch main from origin.

8.  Git se quejaría si se intentara ejecutar este comando antes del envío de cambios inicial, ya que el nuevo repositorio no tendría ramas. Git no puede realizar el seguimiento de una rama que no existe. Lo único que Git hace por debajo es buscar en .`git/refs/remotes/origin` un archivo denominado _trunk_.

## Configuración para colaboradores

El siguiente paso es que Bob clone el repositorio vacío y que Alice defina el origen en su repositorio para establecer como destino de las incorporaciones y los envíos de cambios el repositorio compartido.

1.  Cree un directorio denominado Bob que sea un elemento del mismo nivel que el directorio del proyecto y luego vaya al directorio Bob:

        cd ..
        mkdir Bob
        cd Bob

2.  Ahora, clone el repositorio compartido (asegúrese de incluir el punto al final del comando):

        git clone ../Shared.git .

3.  Actualmente, el repositorio de Alice está configurado para enviar e incorporar cambios desde su propio repositorio. Use los siguientes comandos para ir al directorio Alice y cambie `origin` para que apunte al repositorio compartido:

        cd ../Alice
        git remote set-url origin ../Shared.git

## Inicio de la colaboración

Ahora que Bob lo tiene todo a punto para trabajar en el sitio web, decide agregar un pie de página en la parte inferior. Vamos a asumir el rol de Bob y Alice durante unos minutos para aprender los aspectos básicos de la colaboración.

1.  Comience por ir al directorio Bob y trabaje como Bob:

        cd ../Bob
        git config user.name Bob
        git config user.email bob@contoso.com

2.  Abra _index.html_ y reemplace el elemento `<hr>` por esta línea (se encuentra al final del elemento `<body>`):

        <footer><hr>Copyright (c) 2021 Contoso Cats</footer>

    Luego guarde el archivo y cierre el editor.

3.  Confirme los cambios e insértelos en el origen remoto:

        git commit -a -m "Put a footer at the bottom of the page"
        git push

4.  Compruebe los resultados. Si ve una advertencia similar a la del ejemplo siguiente, no se preocupe. Simplemente comunica a los usuarios un cambio en los comportamientos predeterminados de Git. Si quiere asegurarse de no volver a ver esta advertencia, puede ejecutar `git config --global push.default simple`.

        warning: push.default is unset; its implicit value has changed in
        Git 2.0 from 'matching' to 'simple'. To squelch this message
        and maintain the traditional behavior, use:

        git config --global push.default matching

        To squelch this message and adopt the new behavior now, use:

        git config --global push.default simple

        When push.default is set to 'matching', git will push local branches
        to the remote branches that already exist with the same name.

        Since Git 2.0, Git defaults to the more conservative 'simple'
        behavior, which only pushes the current branch to the corresponding
        remote branch that 'git pull' uses to update the current branch.

        See 'git help config' and search for 'push.default' for further information.
        (the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
        'current' instead of 'simple' if you sometimes use older versions of Git)

5.  Mientras Bob edita el sitio, Alicia también lo hace. Ella decide agregar una barra de navegación a la página. Esta incorporación obliga a Alice a modificar dos archivos: index.html y site.css. Empiece por volver al directorio Alice:

        cd ../Alice

6.  Ahora, abra index.html e inserte la línea siguiente inmediatamente después de la etiqueta `<body>`, en la línea 8:

        <nav><a href="./index.html">home</a></nav>

    Luego guarde el archivo y cierre el editor.

7.  Abra site.css en la carpeta CSS y agregue la línea siguiente en la parte inferior:

        nav { background-color: #C0D8DF; }

    Guarde el archivo y cierre el editor.

8.  Ahora imagine que Alice recibe un correo electrónico de Bob en el que le dice que ha hecho cambios en el sitio. Alice decide extraer los cambios de Bob antes de confirmarlos. (Si Alice ya hubiera confirmado los cambios, tendrían otro problema que trataremos en otro módulo). Alice ejecuta este comando:

        git pull

9.  Compruebe los resultados. Por la salida, parece que Git ha evitado un problema:

        remote: Counting objects: 3, done.
        remote: Compressing objects: 100% (3/3), done.
        remote: Total 3 (delta 2), reused 0 (delta 0)
        Unpacking objects: 100% (3/3), done.
        From ../Shared
        843d142..2cf6cbf main -> origin/main
        Updating 843d142..2cf6cbf
        error: Your local changes to the following files would be overwritten by merge:
        index.html
        Please commit your changes or stash them before you can merge.
        Aborting

    Git advierte que la incorporación de cambios sobrescribiría la versión de Alice de _index.html_ y se perderían sus cambios. Esto se debe a que Bob también ha modificado _index.html_. Si Alice no hubiera cambiado _index.html_, Git habría confirmado la combinación.

10. Use un comando git diff para ver qué cambios ha realizado Bob en index.html:

        git diff origin -- index.html

11. Compruebe los resultados. Por la salida, es evidente que los cambios de Alice y los de Bob no se superponen. Ahora Alice puede guardar _provisionalmente_ sus cambios.

    `git stash` guarda el estado del árbol de trabajo y el índice mediante un par de confirmaciones temporales. Piense en el almacenamiento provisional como una manera de guardar el trabajo actual mientras hace otra cosa, sin tener que realizar una confirmación "real" ni afectar al historial del repositorio.

    En realidad, Alice debería haber confirmado o guardado provisionalmente sus cambios antes de intentar incorporar cambios. La incorporación de cambios a un árbol de trabajo "sucio" es algo arriesgado, ya que puede provocar incidencias más complejas de subsanar.

    Use el siguiente comando para guardar provisionalmente los cambios de Alice:

        git stash

12. Compruebe los resultados. Deberían parecerse a los de este ejemplo:

        Saved working directory and index state WIP on main: 95bbc3b Change background color to light blue
        HEAD is now at 95bbc3b Change background color to light blue

13. Ahora Alice puede incorporar los cambios con seguridad, después de lo cual puede "sacar" los cambios guardados provisionalmente, que están organizados como una pila. (De hecho, `git stash` es una forma abreviada de `git stash push`. Es muy similar a la pila donde se colocan las facturas que aún no se han podido pagar). Ejecute estos comandos:

        git pull
        git stash pop

    Los cambios guardados provisionalmente se combinan al extraerlos. Si los cambios se superponen, podría haber un conflicto. Puede obtener información sobre cómo resolver esas situaciones en un módulo de Git más avanzado de Microsoft Learn.

14. Compruebe los resultados. Alice debería ver esta salida, que le permite saber que la combinación se ha realizado correctamente y que los cambios están de vuelta, aunque aún no se hayan almacenado provisionalmente para su confirmación:

        Auto-merging index.html
        On branch main
        Your branch is up-to-date with 'origin/main'.
        Changes not staged for commit:
        (use "git add <file>..." to update what will be committed)
        (use "git checkout -- <file>..." to discard changes in working directory)

                modified:   CSS/site.css
                modified:   index.html

        no changes added to commit (use "git add" and/or "git commit -a")
        Dropped refs/stash@{0} (0cfb7b75d56611d9fc6a6ab660a51f5582b8d9c5)

    En este punto Alice puede seguir trabajando o simplemente confirmar y enviar los cambios. Vamos a hacer otro cambio como Alice: asignar a los pies de página el mismo estilo que a las barras de navegación.

15. Abra site.css en la carpeta CSS y reemplace la tercera línea (la que aplica estilo a los elementos `<nav>`) por esta regla CSS compartida. Luego, como de costumbre, guarde los cambios y cierre el editor.

        nav, footer { background-color: #C0D8DF; }

16. Ahora confirme los cambios y envíelos al repositorio compartido:

        git commit -a -m "Stylize the nav bar"
        git push

    El sitio actualizado está ahora en el repositorio compartido.

17. Para finalizar, vuelva al directorio del proyecto y realice una incorporación de cambios:

        cd ../Cats
        git pull

18. Abra index.html (el que se encuentra en el directorio del proyecto) para confirmar que los cambios realizados por Bob y Alice están presentes en el repositorio local. Compruebe que index.html tiene el código más actualizado:

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
                <p>Eventually we will put cat pictures here.</p>
                <footer><hr>Copyright (c) 2021 Contoso Cats</footer>
            </body>
        </html>

19. En este momento, su repositorio y el de Alice están sincronizados, pero el de Bob no lo está. Para finalizar, actualice también el de Bob:

        cd ../Bob
        git pull

Los tres repositorios ya están alineados. El repositorio compartido es el único origen de confianza para todos los usuarios, y todos los envíos de cambios e incorporaciones se dirigen a él.
