# Ejercicio: Prueba de Git

1.  Para configurar Git, debe definir algunas variables globales: user.name y user.email. Ambas son necesarias para realizar confirmaciones.

2.  Establezca su nombre en Cloud Shell con el siguiente comando. Reemplace <USER_NAME> por el nombre de usuario que quiere usar.

        git config --global user.name "<USER_NAME>"

3.  Ahora, use este comando para crear una variable de configuración user.email; para ello, reemplace <USER_EMAIL> por su dirección de correo electrónico:

        git config --global user.email "<USER_EMAIL>"

4.  Ejecute el siguiente comando para comprobar que los cambios han funcionado:

        git config --list

5.  Confirme que la salida incluye dos líneas similares al siguiente ejemplo. El nombre y la dirección de correo electrónico serán distintos a los que se muestran en el ejemplo.

        user.name=User Name
        user.email=user-name@contoso.com

# Configuración del repositorio de Git

Git funciona buscando cambios en los archivos dentro de una determinada carpeta. Vamos a crear una carpeta que actúe como árbol de trabajo (directorio del proyecto) y a permitir que Git sepa sobre ella para que pueda comenzar a seguir los cambios. Se indica a Git que empiece a realizar el seguimiento de los cambios mediante la inicialización de un repositorio de Git en esa carpeta.

Empiece por crear una carpeta vacía para el proyecto y luego inicialice un repositorio de Git dentro de ella.

1.  Cree una carpeta con el nombre Cats. Esta carpeta va a ser el directorio del proyecto, también denominado árbol de trabajo. El directorio del proyecto es donde se almacenan todos los archivos relacionados con el proyecto. En este ejercicio, es donde se almacenan el sitio web y los archivos que crean el sitio web y su contenido.

        mkdir Cats

2.  Vaya al directorio del proyecto mediante el comando cd:

        cd Cats

3.  Ahora, inicialice el nuevo repositorio y establezca el nombre de la rama predeterminada en main:

    Si está ejecutando la versión 2.28.0 o una posterior de Git, use el comando siguiente:

        git init --initial-branch=main

    O bien, use el siguiente comando:

        git init -b main

    En versiones anteriores de Git, use estos comandos:

        git init
        git checkout -b main

    Después de ejecutar el comando de inicialización, debería ver una salida similar a la de este ejemplo:

        Initialized empty Git repository in /home/<user>/Cats/.git/

        Switched to a new branch 'main'

4.  Ahora, use un comando git status para mostrar el estado del árbol de trabajo:

        git status

    Git responde con esta salida, que indica que master es la rama actual. (De hecho, también es la única rama). Por ahora todo está claro.

        On branch master

        No commits yet

        nothing to commit (create/copy files and use "git add" to track)

5.  Use un comando ls para mostrar el estado del árbol de trabajo:

        ls -a

    Confirme que el directorio contiene un subdirectorio denominado .git. (El uso de la opción -a con ls es importante, ya que Linux normalmente oculta los nombres de archivos y directorios que comienzan con un punto). Esta carpeta es el repositorio de Git: el directorio en el que Git almacena los metadatos y el historial del árbol de trabajo.

    Normalmente no se hace nada directamente con el directorio .git. Git actualiza los metadatos a medida que el estado del árbol de trabajo cambia para mantener un seguimiento de lo que ha cambiado en sus archivos. Este directorio es práctico para usted, pero es increíblemente importante para Git.

# Ayuda desde Git

Git, al igual que la mayoría de las herramientas de línea de comandos, tiene una función de ayuda integrada que se puede usar para buscar comandos y palabras clave.

1.  Git, al igual que la mayoría de las herramientas de línea de comandos, tiene una función de ayuda integrada que se puede usar para buscar comandos y palabras clave.

        git --help

2.  El comando muestra la salida siguiente:

        usage: git [--version] [--help] [-C <path>] [-c name=value]
            [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
            [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
            [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
            <command> [<args>]

        These are common Git commands used in various situations:

        start a working area (see also: git help tutorial)
        clone      Clone a repository into a new directory
        init       Create an empty Git repository or reinitialize an existing one

        work on the current change (see also: git help everyday)
        add        Add file contents to the index
        mv         Move or rename a file, a directory, or a symlink
        reset      Reset current HEAD to the specified state
        rm         Remove files from the working tree and from the index

        examine the history and state (see also: git help revisions)
        bisect     Use binary search to find the commit that introduced a bug
        grep       Print lines matching a pattern
        log        Show commit logs
        show       Show various types of objects
        status     Show the working tree status

        grow, mark and tweak your common history
        branch     List, create, or delete branches
        checkout   Switch branches or restore working tree files
        commit     Record changes to the repository
        diff       Show changes between commits, commit and working tree, etc
        merge      Join two or more development histories together
        rebase     Forward-port local commits to the updated upstream head
        tag        Create, list, delete or verify a tag object signed with GPG

        collaborate (see also: git help workflows)
        fetch      Download objects and refs from another repository
        pull       Fetch from and integrate with another repository or a local branch
        push       Update remote refs along with associated objects

        'git help -a' and 'git help -g' list available subcommands and some
        concept guides. See 'git help <command>' or 'git help <concept>'
        to read about a specific subcommand or concept.

Lea las distintas opciones disponibles con Git y observe que cada comando incluye su propia página de ayuda, para cuando empiece a profundizar más. No todos estos comandos tendrán sentido todavía, pero es posible que algunos le resulten familiares si tiene experiencia con un VCS.

En la lección siguiente va a obtener más información sobre los comandos que acaba de probar y los aspectos básicos de Git.
