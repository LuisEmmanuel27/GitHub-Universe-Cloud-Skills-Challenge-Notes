# Ejercicio: Combinación de la rama de Bob

Aunque Alice está trabajando en CSS para el sitio web, Bob está trabajando en casa, completamente ajeno al trabajo que está realizando Alice. No hay problema con esta disposición porque ambos usan ramas. Bob decide realizar algunos cambios por su cuenta.

## Creación de una rama para Bob

1.  Vuelva al directorio Bob y ejecute el comando siguiente para crear una rama denominada `add-cat`. Use la popular opción `checkout -b` para crear la rama y cambiar a ella con un solo comando.

        cd ../Bob
        git checkout -b add-cat

2.  Descargue el archivo ZIP que contiene algunos recursos del sitio web. A continuación, descomprima los archivos de recursos:

        wget https://github.com/MicrosoftDocs/mslearn-branch-merge-git/raw/main/git-resources.zip
        unzip git-resources.zip

3.  Ahora, mueva el archivo bobcat2-317x240.jpg al directorio Assets (Recursos) de Bob. Elimine los demás archivos. Descargará los archivos y los volverá a usar más adelante.

        mv bobcat2-317x240.jpg Assets/bobcat2-317x240.jpg
        rm git-resources.zip
        rm bombay-cat-180x240.jpg

4.  A continuación, abra el archivo _index.html_ y reemplace la línea que dice "Eventually we will put cat pictures here" (al final se incluirán aquí las imágenes de gatos) por la siguiente línea:

        <img src="Assets/bobcat2-317x240.jpg" />

5.  Guarde el archivo y cierre el editor.

6.  Ha realizado dos cambios en la rama `add-cat` de Bob: se ha agregado un archivo y se ha modificado otro. Ejecute `git status` para volver a comprobar los cambios:

        git status

7.  Después, ejecute los comandos siguientes para agregar el nuevo archivo del directorio _Assets_ (Recursos) al índice y confirmar todos los cambios:

        git add .
        git commit -a -m "Add picture of Bob's cat"

8.  Bob ahora realiza la misma acción que antes hizo Alice. Bob vuelve a cambiar a la rama `main` y ejecuta una incorporación de cambios para ver si ha cambiado algo:

        git checkout main
        git pull

9.  Compruebe los resultados. Esta vez, el resultado indica que los cambios se han realizado en la rama `main` en el repositorio compartido (el resultado de las inserciones de Alice). También indica que el cambio extraído de `main` en el repositorio compartido se ha combinado con `main` en el repositorio de Bob:

        remote: Counting objects: 4, done.
        remote: Compressing objects: 100% (3/3), done.
        remote: Total 4 (delta 1), reused 0 (delta 0)
        Unpacking objects: 100% (4/4), done.
        From D:/Labs/Git/Bob/../Shared
        e81ae09..1d2bfea  main     -> origin/main
        Updating e81ae09..1d2bfea
        Fast-forward
        Assets/site.css | 3 ++-
        1 file changed, 2 insertions(+), 1 deletion(-)

10. A continuación, Bob combina su rama en la rama para que de su repositorio tenga sus cambios `main` y `main` los de Alice. A continuación, Bob envía los cambios de `main` del equipo de la rama `main` del repositorio compartido:

        git merge add-cat --no-edit
        git push

    Bob no usó la marca --ff-only porque sabían que main había cambiado. Una combinación de solo avance rápido habría producido un **_`error`_**.

## Sincronización de los repositorios

En este momento, Bob tiene un repositorio actualizado, pero Alice no. Alice tiene que ejecutar `git pull` en el repositorio compartido para asegurarse de que tiene la versión óptima y más reciente del sitio.

Ejecute los comandos siguientes para sincronizar el repositorio de Alice con el repositorio compartido:

    cd ../Alice
    git pull

Tómese unos minutos para comprobar que el repositorio de Alice y el repositorio de Bob están sincronizados. Cada repositorio debe tener un archivo JPG en el directorio Assets (Recursos) y un elemento `<img>` declarado en el archivo _index.html_. El archivo site.css de la carpeta Assets (Recursos) de cada repositorio debe contener una línea que defina una hoja de estilo CSS llamada cat. Alice agregó este estilo cuando realizó los cambios.

Si abre _index.html_ en un explorador, verá la imagen siguiente:

<center>
    <img src="https://learn.microsoft.com/es-mx/training/modules/branch-merge-git/media/first-cat.png"/>
</center>

En la lección siguiente, aprenderá a resolver conflictos de combinación, los cuales se producen cuando se superponen los cambios realizados por dos o más desarrolladores.
