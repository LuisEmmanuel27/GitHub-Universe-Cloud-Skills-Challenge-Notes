# Corrección de errores simples

En ocasiones, algo no sale según lo previsto. Es posible que se olvide de agregar un archivo nuevo o que agregue uno por error. Quizás haya cometido un error ortográfico en la confirmación más reciente o haya confirmado algo que no quería confirmar. Quizás _haya eliminado_ accidentalmente un archivo.

Git le permite realizar cambios sin miedo, porque siempre ofrece una manera de volver atrás. Puede incluso cambiar el historial de confirmaciones de Git siempre y cuando cambie solo las confirmaciones que no se hayan compartido.

## Rectificación de una confirmación: marca --amend

En el ejercicio anterior ha actualizado el archivo index.html para modificar la ruta de acceso a la hoja de estilos. Debería haber agregado la siguiente instrucción:

    <link rel="stylesheet" href="CSS/site.css">

Imagine que descubre que ha cometido un error al escribir la instrucción. En lugar de especificar la ruta de acceso de la carpeta como `CSS`, ha escrito `CS`:

    <link rel="stylesheet" href="CS/site.css">

Al actualizar la página en el explorador, observará que no se aplica la hoja de estilos CSS. Después de investigar, se da cuenta de que ha especificado los valores de la ruta de acceso de forma incorrecta.

Por lo tanto, actualice index.html con la ruta de acceso correcta a la hoja de estilos. En este punto bastaría con confirmar la versión corregida de index.html, pero, en lugar de ello, prefiere colocarla en la misma confirmación que la original. La opción `--amend` para `git commit` permite cambiar el historial (¿y con qué frecuencia se tiene la oportunidad de cambiar el historial?).

    git commit --amend --no-edit

La opción `--no-edit` indica a Git que realice el cambio sin cambiar el mensaje de confirmación. También puede usar `--amend` para editar un mensaje de confirmación, para agregar archivos dejados accidentalmente fuera de la confirmación o para quitar archivos agregados por equivocación.

### Nota:

**La capacidad de cambiar el historial es una de las características más útiles de Git. Al igual que la mayoría de las herramientas avanzadas, debe usarse con cuidado. En concreto, es mala idea cambiar las confirmaciones que se han compartido con otro desarrollador, o que se han publicado en un repositorio compartido, como GitHub.**

## Recuperación de un archivo eliminado: git checkout

Imagine que ha realizado un cambio en un archivo de código fuente que ha interrumpido todo el proyecto, por lo que quiere revertir a la versión anterior de ese archivo. Quizás haya eliminado un archivo por completo accidentalmente. Git facilita la recuperación de una versión anterior, incluso aunque la versión actual ya no exista. El mejor aliado en esta situación es el comando <a href="https://git-scm.com/docs/git-checkout">git checkout</a>.

`git checkout` tiene varias utilidades, pero en el siguiente ejercicio se va a usar para recuperar un archivo eliminado. `git checkout` actualiza los archivos del árbol de trabajo para que coincidan con la versión del índice o la del árbol especificado.

Si ha eliminado un archivo por accidente, puede recuperarlo si devuelve la versión del índice al árbol de trabajo con este comando:

    git checkout -- <file_name>

También puede extraer del repositorio un archivo de una confirmación anterior (normalmente, el nivel superior de otra rama), pero el valor predeterminado es obtener el archivo del índice. El objeto `--` de la lista de argumentos sirve para diferenciar la confirmación de la lista de rutas de archivo. No es estrictamente necesario en este caso, pero si tuviera una rama llamada `<nombre_archivo>` (quizás porque ese es el nombre del archivo en el que se está trabajando en esa rama), `--` evitaría que Git se confundiera.

Más adelante va a aprenderá que `checkout` también se usa para cambiar de rama.

## Recuperación de archivos: git reset

También puede eliminar un archivo con git rm. Este comando elimina el archivo en el disco, pero también hace que Git registre su eliminación en el índice.

Por lo tanto, si ha ejecutado este comando:

    git rm index.html
    git checkout -- index.html

Git no restauraría _index.html_ fácilmente. Por el contrario, se obtendría un error como este ejemplo:

    error: pathspec 'index.html' did not match any file(s) known to git.

Para recuperar _index.html_, habría que usar otra técnica: `git reset`. Puede usar `git reset` para anular el almacenamiento provisional de los cambios.

_index.html_ se puede recuperar con estos dos comandos:

    git reset HEAD index.html
    git checkout -- index.html

Aquí, `git reset` revierte la eliminación del archivo del almacenamiento provisional de Git. Este comando devuelve el archivo al índice, aunque sigue eliminado del disco. Luego se puede restaurar en el disco desde el índice con `git checkout`.

He aquí otro momento "¡Ahá!" para los nuevos usuarios de Git. Muchos VCS hacen que los archivos sean de solo lectura para asegurarse de que solo una persona pueda efectuar cambios cada vez; los usuarios usan un comando `checkout` no relacionado para obtener una versión grabable del archivo. También usan `checkin` para una operación similar a la que realiza Git con una combinación de `add`, `commit` y `push`. A veces este hecho origina confusión cuando los usuarios empiezan a usar Git.

## Reversión de una confirmación: git revert

El último comando importante que se debe conocer para corregir errores con Git es `git revert`. `git checkout` solo funciona en situaciones en las que los cambios que se van a deshacer están en el índice. Después de confirmar los cambios, debe emplear otra estrategia para deshacerlos. En este caso se puede usar `git revert` para revertir la confirmación anterior. Crea otra confirmación que cancela la primera.

Se puede usar `git revert HEAD` para realizar una confirmación exactamente opuesta a la última, con lo que esta se deshace y deja todo el historial intacto. La parte `HEAD` del comando simplemente indica a Git que se quiere "deshacer" solo la última confirmación.

Por otro lado, también se puede quitar la confirmación más reciente con el comando `git reset`:

    git reset --hard HEAD^

Git ofrece varios tipos de restablecimientos. El valor predeterminado es `--mixed`, que restablece el índice, pero no el árbol de trabajo; también mueve `HEAD` si se especifica otra confirmación. La opción -`-soft` solo mueve `HEAD` y deja el índice y el árbol de trabajo sin cambios. Esta opción deja todos los cambios como "pendientes de confirmar", como indicaría g`it status`. Un restablecimiento `--hard` cambia el índice y el árbol de trabajo para que coincidan con la confirmación especificada; los cambios realizados en los archivos seguidos se descartan.
