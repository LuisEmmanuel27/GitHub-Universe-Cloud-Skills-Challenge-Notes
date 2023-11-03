# Ejercicio: Creación de una solicitud de incorporación de cambios

En el espacio aislado, asegúrese de que sigue en el directorio Alice, que es la carpeta superior del clon de Alice del repositorio Cats. Puede usar el comando `pwd` para comprobar la ubicación de la carpeta.

    pwd

En este momento no hay nada que Alice pueda incorporar, porque no se ha realizado ningún cambio desde que ella clonó el repositorio. Puede probarlo con el siguiente comando, que muestra la salida `Already up-to-date`:

    git pull

## Realización de un cambio y envío de una solicitud de incorporación de cambios

Alice comienza a trabajar en el sitio web. Su primera decisión es cambiar el color de fondo del sitio. Alice experimenta en local y, finalmente, elige su tono favorito de azul claro.

1.  Configure una identidad para Alice mediante la ejecución de los siguientes comandos:

        git config user.name "Alice"
        git config user.email "alice@contoso.com"

    Estos valores de configuración `config` se almacenan en el repositorio en el archivo _.git/config_, así que no tendrá que volver a escribirlos. Cada vez que vaya al directorio Alice, asumirá la identidad de Alice.

2.  Abra el archivo _site.css_ del directorio _Alice/CSS_:

        code CSS/site.css

3.  Para cambiar el color de fondo de la página a azul claro, reemplace la segunda línea del archivo por la siguiente instrucción:

        body { font-family: serif; background-color: #F0FFF8; }

    Luego guarde el archivo y cierre el editor.

4.  Luego guarde el archivo y cierre el editor.

        git commit -a -m "Change background color to light blue"

5.  Luego realice una solicitud de incorporación de cambios al repositorio original:

        git request-pull -p origin/main .

6.  Compruebe los resultados. Debería ver una salida similar al ejemplo siguiente:

        The following changes since commit 2bf69ab0226d8d35efd1e92c83cd92c5cc09a7ae:

        Add simple HTML and stylesheet (2019-11-21 01:57:24 +0000)

        are available in the git repository at:

        .

        for you to fetch changes up to 95bbc3b6929953e9b04353920e97230b463022f0:

        Change background color to light blue (2019-11-21 02:33:48 +0000)

        ----------------------------------------------------------------
        Alice (1):
            Change background color to light blue

        CSS/site.css | 2 +-
        1 file changed, 1 insertion(+), 1 deletion(-)

        diff --git a/CSS/site.css b/CSS/site.css
        index caefc86..86d41e8 100644
        --- a/CSS/site.css
        +++ b/CSS/site.css
        @@ -1,2 +1,2 @@
        h1, h2, h3, h4, h5, h6 { font-family: sans-serif; }
        -body { font-family: serif; }
        \ No newline at end of file
        +body { font-family: serif; background-color: #F0FFF8; }
        \ No newline at end of file

## Creación de un remoto y finalización de la solicitud de incorporación de cambios

Dado que el directorio del proyecto y el directorio _Alice_ están en el mismo equipo, puede incorporar los cambios directamente desde el directorio _Alice_. En la vida real, el directorio _Alice_ estaría en el equipo de ella. Esta circunstancia se soluciona mediante la configuración de un remoto con el comando `git remote`. Luego se usa ese remoto para las solicitudes de incorporación y envío de cambios. En este ejercicio no resulta práctico configurar dos máquinas para realizar estos pasos, así que se va a configurar un remoto que use un nombre de ruta de acceso local. En realidad, se usaría una ruta de acceso de red o una URL.

1.  Vuelva al directorio del proyecto y use el comando `git remote` para crear un remoto de nombre `remote-alice` que tenga como destino el directorio del proyecto de Alice:

        cd ../Cats
        git remote add remote-alice ../Alice

2.  Ahora ejecute una incorporación de cambios:

        git pull remote-alice main

    Observe que tiene que especificar una rama, `main`, en el comando de incorporación de cambios. En la siguiente lección va a aprender a configurar una dirección URL ascendente para la rama.

3.  Compruebe los resultados. Debería ver una salida como la de este ejemplo, que muestra que la solicitud de incorporación de cambios se ha realizado correctamente:

        remote: Counting objects: 4, done.
        remote: Compressing objects: 100% (3/3), done.
        remote: Total 4 (delta 1), reused 0 (delta 0)
        Unpacking objects: 100% (4/4), done.
        From ../Alice
        * branch            main     -> FETCH_HEAD
        * [new branch]      main     -> remote-alice/main
        Updating 2bf69ab..95bbc3b
        Fast-forward
        CSS/site.css | 2 +-
        1 file changed, 1 insertion(+), 1 deletion(-)

La diversión acaba de empezar. En la siguiente lección, aprenderá a configurar y utilizar un repositorio compartido, lo que hace que la colaboración resulte más sencilla y cómoda.
