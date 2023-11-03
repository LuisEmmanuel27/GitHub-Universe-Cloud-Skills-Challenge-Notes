# Ramas en Git

Es un desarrollador web que intenta aprender más cosas sobre Git por motivos laborales. Ha creado un sitio web HTML y CSS sencillo que presenta fotos de gatos para poner en práctica sus aptitudes de Git y ha trabajado en él con sus amigos, Alice y Bob.

A medida que el proyecto avanza, se da cuenta de que quiere que todos puedan trabajar en más de una tarea a la vez sin interponerse en la forma de trabajar de otra persona. Necesita mantener por separado el trabajo de todos para que el nuevo desarrollo no interfiera con las correcciones de errores existentes. En Git, las ramas facilitan este tipo de colaboración.

El trabajo que se hace en una rama no se tiene que compartir, y tampoco interfiere con el trabajo realizado en otras ramas. Las ramas le permiten mantener las confirmaciones relacionadas con cada tema juntas y aisladas de otro trabajo, por lo que los cambios realizados en un tema son fáciles de revisar y supervisar.

El desarrollo de software moderno se realiza casi por completo en ramas. El objetivo es mantener limpia la rama principal hasta que el trabajo esté listo para su inserción en el repositorio. Después, inserte los cambios en la rama principal, o mejor aún, envíe una solicitud de incorporación de cambios para fusionar los cambios.

Una ventaja de Git con respecto a los sistemas de control de versiones (VCS) anteriores es que, con Git, la creación de una rama es muy rápida; equivale a escribir un hash de 40 caracteres en un archivo en `.git/heads`. La conmutación de ramas también es rápida, ya que Git almacena archivos completos y los descomprime en lugar de intentar reconstruirlos a partir de listas de cambios. La combinación en Git no es tan simple, pero es sencilla y a menudo totalmente automática.

Veamos qué son las ramas, cómo se usan y cómo funcionan.

## Estructura y nomenclatura de las ramas

Una rama es simplemente una cadena de confirmaciones que se ramifica a partir de la línea principal de desarrollo, como una rama de un árbol.

Si va a cambiar a Git desde otro VCS, es posible que esté acostumbrado a una terminología algo distinta. La subversión del VCS nombra su rama predeterminada como `trunk`, mientras que Git la denomina `master`. Puede cambiar el nombre de la rama predeterminada de la misma forma que puede hacerlo con cualquier otra rama. En este módulo, la rama predeterminada se denomina `main`.

Normalmente, una rama comienza con una confirmación en la rama predeterminada; en este caso, en `main`. A medida que se agregan confirmaciones, la rama desarrolla una cadena de historial independiente. Finalmente, los cambios de la rama se vuelven a combinar en `main`. En este módulo, aprenderá a realizar confirmaciones en una rama y a combinarlas en la rama `main`.

Supongamos que crea una rama a partir de la rama `main`. Aquí se muestra cómo visualizar lo que sucede:

<center>
    <img src="https://learn.microsoft.com/es-mx/training/modules/branch-merge-git/media/branch-tree.png"/>
</center>

Cada letra mayúscula del diagrama representa una confirmación. Las ramas reciben nombres tales como `add-authentication` y `fix-css-bug`, y pueden tener sus propias ramas. El objetivo final es dejar que los desarrolladores hagan lo que tienen que hacer sin interferir unos con otros y terminar con una rama principal que represente los mejores esfuerzos de todos los implicados.

## Creación y modificación de ramas (rama de Git y desprotección de Git)

Una razón común para crear una rama es realizar cambios en una característica existente. Una rama con este fin se denominaría habitualmente _rama puntual o rama de características_.

Puede crear una rama con el comando `git branch`. Cambie entre las ramas con el comando `git checkout`.

Ha identificado `checkout` como una forma de reemplazar archivos en el árbol de trabajo obteniéndolos del índice. Sin rutas de acceso en la lista de argumentos, `checkout` actualiza todo lo que hay en el árbol de trabajo y el índice para que coincida con la confirmación especificada (en este caso, el encabezado de la rama).

## Combinación de ramas (combinación de Git)

Una vez que haya finalizado algún trabajo en una rama, quizá una característica o una corrección de errores, querrá _combinar_ la rama de nuevo con la rama principal. Puede usar el comando `git merge` para combinar una rama específica con la rama actual.

Por ejemplo, si estuviera trabajando en una rama llamada `my-feature`, el flujo de trabajo sería similar al del siguiente ejemplo:

    # Switch back to the main branch
    git checkout main

    # Merge my-feature branch into main
    git merge my-feature

Después de usar estos comandos y resolver los conflictos de combinación (los describiremos más adelante en este módulo), todos los cambios de la rama `my-feature` se encontrarían en `main`.
