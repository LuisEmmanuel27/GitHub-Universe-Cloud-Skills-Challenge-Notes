# Ejercicio: Uso de Git para corregir errores

Ahora vamos a practicar la corrección de errores.

## Ahora vamos a practicar la corrección de errores.

1.  En primer lugar, intente eliminar _index.html_:

        rm index.html

    Puede parecer una mala idea, pero recuerde: Git le cubre las espaldas.

2.  Use un comando `ls` para comprobar que _index.html_ se haya eliminado:

        ls

3.  Debería ver la siguiente salida. Observe que ahora no hay ningún archivo _index.html_.

        CSS

4.  Vamos a recuperar _index.html_. Use git checkout para recuperar _index.html_:

        git checkout -- index.html

5.  Vuelva a utilizar ls para comprobar el contenido del directorio actual. ¿Se ha restaurado index.html?

    Sí. Ahora la salida debe tener un archivo index.html y un directorio CSS:

        CSS  index.html

## Práctica de la recuperación de un archivo eliminado: git rm

Si quiere recuperar archivos eliminados, las cosas son un poco más complicadas si los elimina mediante `git rm` en lugar de `rm`.

1.  Para ver lo que sucede, pruebe este comando:

        git rm index.html

2.  De nuevo, busque _index.html_ al ejecutar `ls`. No debería ver _index.html_.

3.  Intente recuperar _index.html_ lo mismo que la última vez:

        git checkout -- index.html

4.  Esta vez, Git indica que no sabe nada de _index.html_. Esto se debe a que Git no solo ha eliminado el archivo, sino que ha registrado la eliminación en el índice:

        error: pathspec 'index.html' did not match any file(s) known to git.

5.  Revierta la eliminación de index.html del almacenamiento provisional con el comando `git reset`:

        git reset HEAD index.html

6.  Busque esta salida, que lo confirma:

        Unstaged changes after reset:
        D       index.html

7.  Ahora puede recuperar el archivo del índice con el comando que ha usado antes:

        git checkout -- index.html

8.  `git reset` deshizo el cambio, pero el archivo seguía borrado, así que tuvo que usar `checkout` para recuperarlo.

## Reversión de una confirmación

Ahora vamos a complicar las cosas un poco más. Imagine que por accidente sobrescribe un archivo con otro, o que hace un cambio en un archivo que resulta ser un gran error. Quiere revertir el archivo a la versión anterior, pero ya ha confirmado los cambios. En este caso, un sencillo `git checkout` no va a funcionar.

Una solución a este problema consiste en revertir la confirmación anterior.

1.  Abra _index.html_ con code:

        code index.html

2.  Reemplace el contenido de index.html por este código:

        <h1>That was a mistake!</h1>

3.  Guarde y cierre el archivo.

4.  Use estos comandos para confirmar los cambios y mostrar la confirmación más reciente:

        git commit -m "Purposely overwrite the contents of index.html" index.html
        git log -n1

    La marca `-n1` aquí indica a Git que solo se quiere la entrada de confirmación más reciente.

5.  Use los comandos siguientes para intentar restaurar _index.html_:

        git checkout -- index.html

6.  Abra _index.html_ en el editor:

        code index.html

    ¿Qué versión de index.html verá? ¿La versión anterior o la nueva?

    En esta situación, la mejor opción es revertir el cambio realizando otra confirmación que cancele la primera. Este es un trabajo para `git revert`.

7.  Cierre el archivo y use `git revert` para deshacer los cambios confirmados:

        git revert --no-edit HEAD

8.  Compruebe los resultados. Deben tener un aspecto similar a este ejemplo:

        [main 6a27310] Revert "Purposely overwrite the contents of index.html"
        1 file changed, 13 insertions(+), 1 deletion(-)

9.  Realice un seguimiento con un comando `git log` para mostrar la confirmación más reciente:

        git log -n1

10. Vuelva a comprobar la salida. Deberían parecerse a los de este ejemplo:

        Author: User Name <user-name@contoso.com>
        Date:   Tue Nov 19 23:42:26 2019 +0000

        Revert "Purposely overwrite the contents of index.html"

        This reverts commit 15d3bded388470c98881a632025bc15190fe9d17.

11. Por último, abra el archivo index.html para asegurarse de que el contenido es la versión correcta.

La reversión no es la única manera de solucionar esta situación; bastaría con editar index.html y confirmar el archivo corregido. Esa opción es más difícil si los cambios confirmados fueran muchos. En cualquier caso, `git revert` es una clara señal de intenciones.
