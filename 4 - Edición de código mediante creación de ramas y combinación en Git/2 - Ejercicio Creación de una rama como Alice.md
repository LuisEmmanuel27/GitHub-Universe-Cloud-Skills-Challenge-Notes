# Ejercicio: Creación de una rama como Alice

Su amiga desarrolladora Alice desea agregar algunos estilos CSS para dar estilo a las fotos de gatos del sitio web. Alice desea realizar este trabajo en su propia rama.

## Configurar

Para que podamos asumir el rol de Alice, debe hacer algo de trabajo para configurar un repositorio vacío que todos compartan y, después, agregar algunos archivos.

Git ya se ha instalado automáticamente en Azure Cloud Shell, por lo que podemos usar Git en Cloud Shell, a la derecha.

## Creación de un repositorio vacío compartido

1.  Cree un directorio denominado _Shared.git_ para que contenga el repositorio vacío:

        mkdir Shared.git
        cd Shared.git

2.  Ahora, ejecute el comando siguiente para crear un repositorio vacío en el directorio compartido:

        git init --bare

3.  Establezca el nombre de la rama predeterminada del nuevo repositorio. Para realizar este paso, puede cambiar la rama `HEAD` para que apunte a otra rama; en este caso, la rama `main`:

        git symbolic-ref HEAD refs/heads/main

## Clonación del repositorio compartido para Bob

1.  Suba un nivel a partir de este directorio y cree un directorio para que Bob almacene su repositorio:

        cd ..
        mkdir Bob

2.  Clone y configure el repositorio de Bob:

        cd Bob
        git clone ../Shared.git .
        git config user.name Bob
        git config user.email bob@contoso.com
        git symbolic-ref HEAD refs/heads/main

### **Nota**

**Como quiere empezar con la rama predeterminada de _main_, debe cambiar _HEAD_ para que apunte a _refs/heads/main_ en lugar de _refs/heads/master_, que es el nombre de la rama predeterminada.**

## Incorporación de archivos base

Como paso final de configuración, se agregarán los archivos de sitio web base y se insertarán en el repositorio compartido. En el caso de estos comandos, todavía estamos trabajando en el directorio _Bob_.

1.  Cree algunos archivos mediante el comando `touch` de Linux, agréguelos al "stage" y confírmelos mediante Git:

        touch index.html
        mkdir Assets
        touch Assets/site.css
        git add .
        git commit -m "Create empty index.html and site.css files"

2.  Ahora agregue HTML al archivo con el editor de código de Cloud Shell. Puede abrir el editor mediante la ejecución del comando `code`. Abra index.html en el editor en línea; para ello, introduzca `code index.html` en el símbolo del sistema del terminal:

        code index.html

3.  Pegue este código HTML:

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

4.  Guarde el archivo y cierre el editor. Puede seleccionar los puntos suspensivos "…" de la esquina derecha del editor o usar el método abreviado de teclado (CTRL+S en Windows y Linux, o bien Cmd+S en macOS).

5.  Cambie al directorio Assets (Recursos) y abra site.css en el editor:

        cd Assets
        code site.css

6.  Agregue el siguiente CSS al archivo:

        h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
        body { font-family: serif; background-color: #F0FFF8; }
        nav, footer { background-color: #C0D8DF; }

    Guarde el archivo y cierre el editor.

7.  Vuelva al directorio _Bob_ y confirme de nuevo:

        cd ..
        git add .
        git commit -m "Add simple HTML and stylesheet"
        git push --set-upstream origin main

### **Nota**

**Como se va a usar otro nombre de rama predeterminado, debe indicarle a Git que asocie la rama principal a la rama principal del repositorio de origen.**

8.  Compruebe los resultados. Si ve una advertencia similar a la de este ejemplo, no se preocupe. Esta advertencia simplemente informa a los usuarios de un cambio en los comportamientos predeterminados de Git.

        warning: push.default is unset; its implicit value has changed in
        Git 2.0 from 'matching' to 'simple'. To squelch this message
        and maintain the traditional behavior, use:

        git config --global push.default matching

        To squelch this message and adopt the new behavior now, run:

        git config --global push.default simple

        When push.default is set to 'matching', git will push local branches
        to the remote branches that already exist with the same name.

        Since Git 2.0, Git defaults to the more conservative 'simple'
        behavior, which only pushes the current branch to the corresponding
        remote branch that 'git pull' uses to update the current branch.

        See 'git help config' and search for 'push.default' for further information.
        (the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
        'current' instead of 'simple' if you sometimes use older versions of Git)

    Si quiere asegurarse de que no vuelve a ver esta advertencia, puede ejecutar este comando:

        git config --global push.default simple

9.  Compruebe la salida de este indicador de éxito:

        Counting objects: 9, done.
        Delta compression using up to 2 threads.
        Compressing objects: 100% (6/6), done.
        Writing objects: 100% (9/9), 953 bytes | 953.00 KiB/s, done.
        Total 9 (delta 0), reused 0 (delta 0)
        To ../Shared.git
        * [new branch]      main -> main

## Creación de una rama para Alice

Alice quiere crear una rama puntual denominada `add-style` para realizar su trabajo. Vamos a asumir el rol de Alice y, después, crearemos la rama y agregaremos código a esta rama.

1.  Suba un nivel a partir de este directorio y cree un directorio para la copia del repositorio de Alice:

        cd ..
        mkdir Alice

2.  Clone el repositorio de Alice y, a continuación, configúrelo:

        cd Alice
        git clone ../Shared.git .
        git config user.name Alice
        git config user.email alice@contoso.com

3.  Ahora tiene una copia actual del repositorio. Puede enumerar el contenido del archivo y ejecutar `git status` para confirmar el estado del repositorio.

        ls
        git status

4.  Ejecute el comando `git branch` para crear una rama denominada add-style. Luego, ejecute el comando `git checkout` para cambiar a esa rama (de este modo, la convierte en la _rama actual_).

        git branch add-style
        git checkout add-style

5.  En el directorio _Alice/Assets_ (Alice/Recursos), abra _site.css_. Agregue la siguiente definición de clase CSS al final del archivo:

        .cat { max-width: 40%; padding: 5 }

    Guarde los cambios en el archivo y cierre el editor.

6.  Confirme el cambio:

        git commit -a -m "Add style for cat pictures"

7.  En este momento, Alice quiere poner su estilo a disposición de todos los demás, para que cambien a `main` de nuevo y realicen una incorporación de cambios por si alguna otra persona ha realizado cambios:

        git checkout main
        git pull

8.  La salida indica que la rama `main` está actualizada (es decir, `main` del equipo de Alice coincide con `main` en el repositorio compartido). Por tanto, Alice combina la rama `add-style` con la rama `main` mediante la ejecución del comando git merge `--ff-only` para realizar una combinación de avance rápido. Luego, Alice inserta la `main` de su repositorio en el compartido.

        git merge --ff-only add-style
        git push

En este caso, la combinación de avance rápido no era estrictamente necesaria porque la rama `main` no tenía ningún cambio y Git habría combinado los cambios de todos modos. Sin embargo, usar la marca `--ff only` es una buena práctica porque se produce un error en una combinación de `--ff-only` si `main` ha cambiado.
