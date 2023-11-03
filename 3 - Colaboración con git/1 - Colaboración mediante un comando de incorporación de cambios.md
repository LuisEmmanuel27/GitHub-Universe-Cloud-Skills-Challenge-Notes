# Colaboración mediante un comando de incorporación de cambios

En su tiempo de ocio ha estado trabajando en un sitio web que hospeda fotos de gatos. Ha estado usando Git para el control de versiones, y es hora de invitar a colaboradores al proyecto. Durante una cena en su casa, su amiga y también amante de los gatos, Alice, se ofrece a ayudarle a materializar su proyecto, y usted acepta encantado.

Alice primero debe hacer una copia del proyecto de Git. Luego es recomendable que Alice le envíe sus cambios a medida que los realiza. En esta situación es donde destaca la naturaleza _distribuida_ de Git. Con Git, dos o más usuarios pueden trabajar juntos en un proyecto sin miedo a sobrescribir el trabajo de los otros. Además, puede comprobar el trabajo de Alice antes de combinarlo con el suyo. (Alice tiene talento, pero ningún desarrollador es perfecto. Confíe, pero compruebe)

En esta lección va a aprender a clonar un repositorio (también denominado _repo_) para ponerlo a disposición de otros usuarios. También aprenderá a usar una de las características más importantes de Git: las solicitudes de incorporación de cambios.

## Clonación de un repositorio (git clone)

En Git, un repositorio se copia al _clonarlo_ mediante el comando `git clone`. Puede clonar un repositorio independientemente de dónde esté almacenado, siempre que tenga una dirección URL o una ruta de acceso a la que apuntar.

`git clone` acepta rutas de acceso del sistema de archivos, rutas de acceso SSH (por ejemplo, `git@example.com:alice/Cats`; estará familiarizado con este formato si ha usado Rsync o SCP) o direcciones URL, normalmente una que empiece por `file:`, `git:` o `ssh`. Los distintos formatos se describen en la documentación de `git clone`. En Unix y Linux, la operación de clonación usa vínculos físicos, así que es rápida y usa un espacio mínimo, ya que solo hay que copiar las entradas de directorio, no los archivos.

## Repositorios remotos (git pull)

Cuando Git clona un repositorio, crea una referencia al repositorio original, al que se llama _remoto_, mediante el nombre `origin`. Configura el repositorio clonado de modo que _incorpore_ o recupere datos del repositorio remoto. (Git también puede _enviar cambios_. Va a obtener información sobre el envío de cambios en Git más adelante en este módulo). `origin` es la ubicación predeterminada desde la que Git incorpora los cambios y a la que los envía. `git pull` copia los cambios del repositorio remoto en el local. El comando `git pull` es muy eficaz, porque solo copia las confirmaciones y los objetos _nuevos_ y luego los inserta en el árbol de trabajo.

Puede incorporar cambios de `origin` mediante el comando `git pull`. Resulta útil comparar `git pull` con otros métodos de copia de archivos. El comando `scp` copia todo. (`scp` es similar al comando cp de Unix, salvo que los archivos que se copian no tienen que estar en el mismo equipo). Si hay 10 000 archivos en el directorio remoto, `scp` los copia todos. Un programa más eficaz llamado Rsync examina todos los archivos de los directorios local y remoto y solo copia los que son diferentes. Rsync se suele usar para realizar copias de seguridad, pero tiene que aplicar hash a todos los archivos, a menos que tengan diferentes tamaños o fechas de creación.

Git solo examina las confirmaciones. Ya sabe cuál es la última confirmación que ha obtenido del repositorio remoto porque ha guardado la lista de confirmaciones. Luego, Git indica al equipo desde el que está copiando que envíe todo lo que ha cambiado, incluidas las nuevas confirmaciones y los objetos a los que apuntan. Esos objetos y confirmaciones se agrupan en un archivo denominado _paquete_ que se envía en un lote. Por último, Git actualiza el árbol de trabajo al desempaquetar todos los objetos que han cambiado y combinarlos (si fuera necesario) con las confirmaciones y los objetos del árbol de trabajo.

Git solo incorpora o envía cambios si el usuario se lo indica. En eso difiere de, por ejemplo, Dropbox, que tiene que pedir al sistema operativo que le notifique los cambios realizados en su carpeta y, a veces, preguntar al servidor si alguna otra persona ha realizado cambios.

## Creación de solicitudes de incorporación de cambios (git request-pull)

Una vez que otro desarrollador, como Alice, ha clonado el repositorio y realizado algunos cambios en local, es recomendable que incorpore esos cambios al repositorio original. Podría parecer que lo adecuado sería enviar los cambios al repositorio original, pero se produciría un error al hacerlo, ya que otros usuarios no tienen permiso para realizar cambios en él. Y así debe ser. Por ahora, quiere revisar los cambios entrantes antes de combinarlos con la base de código principal.

Por ahora, Alice tendrá que enviar una _solicitud de incorporación de cambios_ para pedirle que incorpore sus cambios a la base de código principal. Alice puede hacerlo mediante `git request-pull`, que podría tener el aspecto de este ejemplo:

    git request-pull -p origin/main .

Alice hace referencia a la rama `main` del remoto `origin` como `origin/main`.

Esta solicitud de incorporación de cambios es básicamente lo mismo que una de GitHub, que es un lugar para almacenar código del que no se habla en este módulo. Una solicitud de incorporación de cambios le ofrece la posibilidad de revisar los cambios de otros colaboradores antes de incorporar su trabajo al que está realizando en el sitio web. Las revisiones de código son una parte importante (algunos dirían que la más importante) de la programación colaborativa.

## Creación de un remoto (git remote) y finalización de la solicitud de incorporación de cambios (git pull)

Como propietario del proyecto, debe saber cómo combinar las solicitudes de incorporación de cambios. En primer lugar, use el comando `git remote` para configurar el repositorio de otro desarrollador como _remoto_. Luego use ese remoto para las incorporaciones y las solicitudes de incorporación de cambios mediante el comando `git pull`.

En segundo plano, `git pull` es una combinación de dos operaciones más sencillas: `git fetch`, que obtiene los cambios, y `git merge`, que combina esos cambios en el repositorio. En este caso, la combinación era de _avance rápido_, lo que significa que Alice tenía la confirmación más reciente en su repositorio, por lo que esta confirmación podría agregarse al principio del historial sin ninguna modificación.
