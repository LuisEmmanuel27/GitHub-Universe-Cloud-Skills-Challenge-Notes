# Ciclo de vida de un codespace

GitHub Codespaces se puede configurar, lo que le permite crear un entorno de desarrollo personalizado para el proyecto. Al configurar un entorno de desarrollo personalizado para su proyecto, puede tener una configuración de codespace repetible para todos los usuarios del proyecto.

El ciclo de vida de un codespace comienza cuando se crea y termina cuando se elimina. Puede desconectarse y reconectarse a un codespace activo sin que esto afecte a sus procesos en ejecución. También puede detener y reiniciar un codespace sin perder los cambios que haya realizado en su proyecto.

<img src="https://learn.microsoft.com/es-mx/training/github/code-with-github-codespaces/media/codespace-circular-lifecycle.png"/>

## Crear un codespace

Puede crear un codespace en GitHub.com, en Visual Studio Code o en la CLI de GitHub. Existen cuatro formas de crear un codespace:

-   Desde una plantilla de GitHub o desde cualquier repositorio de plantillas de GitHub.com para iniciar un nuevo proyecto.
-   Desde una rama del repositorio para el trabajo de nuevas características.
-   Desde una solicitud de cambios abierta para explorar el trabajo en curso.
-   Desde una confirmación en el historial de un repositorio para investigar un error en un punto específico del tiempo.

Puede usar un codespace temporalmente para probar código o volver al mismo codespace para realizar trabajo de características de larga duración.

Puede crear más de un codespace por repositorio o incluso por rama. Sin embargo, hay límites respecto al número de codespaces que puede crear y ejecutar al mismo tiempo. Si alcanza el número máximo de codespaces e intenta crear otro, aparece un mensaje que indica que se debe quitar o eliminar un codespace existente para poder crear uno nuevo.

Puede crear un nuevo codespace cada vez que desarrolle en GitHub Codespaces o mantener un codespace de larga duración para una característica. Si va a iniciar un proyecto nuevo, cree un codespace a partir de una plantilla y publíquelo en un repositorio de GitHub más adelante.

Al crear un codespace cada vez que se trabaja en un proyecto, debe enviar los cambios periódicamente para asegurarse de que todas las confirmaciones nuevas estén en GitHub. Al usar un codespace de larga duración para un proyecto nuevo, incorpore los cambios desde la rama predeterminada del repositorio cada vez que empiece a trabajar en el codespace. Esto permite al entorno obtener las últimas confirmaciones. El flujo de trabajo es similar a trabajar con un proyecto en una máquina local.

Los administradores de repositorios pueden habilitar las precompilaciones de GitHub Codespaces para que un repositorio acelere la creación de un codespace.

Para ver un tutorial y una guía detallados, consulte los recursos Guía para principiantes para aprender a codificar con GitHub Codespaces y Desarrollar en un codespace que se encuentran en la unidad Resumen al final de este módulo.

## Proceso de creación de un codespace

<img src="https://learn.microsoft.com/es-mx/training/github/code-with-github-codespaces/media/codespace-connection-editor.png"/>

Al crear un codespace de GitHub tienen lugar cuatro procesos:

1. Se asignan al codespace una máquina virtual y almacenamiento.
2. Se crea un contenedor.
3. Se establece una conexión con el codespace.
4. Se realiza una configuración posterior a la creación.

## Guardar cambios en un codespace

Cuando se conecta a un codespace a través de la web, se habilita de forma automática la opción de autoguardado para guardar los cambios cuando haya transcurrido una cantidad de tiempo específica. Al conectarse a un codespace a través de Visual Studio Code en ejecución en el escritorio, debe habilitar Autoguardado.

El trabajo se guarda en una máquina virtual en la nube. Puede cerrar y detener un codespace y volver al trabajo guardado más adelante. Si tiene cambios sin guardar, recibirá un mensaje para guardarlos antes de salir. Sin embargo, si el codespace se elimina, se pierde el trabajo. Para guardar el trabajo, debe confirmar los cambios y enviarlos al repositorio remoto o publicar el trabajo en uno nuevo si ha creado el codespace a partir de una plantilla.

## Apertura de un codespace existente

Puede volver a abrir cualquiera de los codespaces activos o detenidos en GitHub.com, en un IDE de JetBrains, en Visual Studio Code o mediante la CLI de GitHub.

Para reanudar un codespace existente, puede ir al repositorio donde existe el codespace, presionar la tecla "," en el teclado y seleccionar Reanudar este codespace o bien abrir https://github.com/codespaces en el explorador, seleccionar el repositorio y, a continuación, seleccionar el codespace existente.

## Tiempos de espera de un codespace

Si un codespace está inactivo o si sale del codespace sin detenerlo de forma explícita, la aplicación agota el tiempo de espera después de un período de inactividad y deja de ejecutarse. El tiempo de espera predeterminado es después de 30 minutos de inactividad. No se puede personalizar la duración del período de tiempo de espera para los nuevos codespaces. Cuando se agota el tiempo de espera de un codespace, se preservan los datos de la última vez que haya guardado los cambios.

## Conexión a Internet al usar GitHub Codespaces

Un codespace requiere conexión a Internet. Si la conexión a Internet se pierde mientras trabaja en un codespace, no podrá acceder a este. Sin embargo, cualquier cambio pendiente de confirmación se guarda. Al restablecer la conexión a Internet, puede acceder al codespace en el mismo estado que se dejó cuando se perdió la conexión.

Si tiene una conexión de internet inestable, debe confirmar e insertar los cambios frecuentemente.

## Cerrar o detener un codespace

Si sale del codespace sin ejecutar el comando para detenerlo (por ejemplo, cierra la pestaña del explorador) o si deja el codespace en ejecución sin interacción, el codespace y sus procesos en ejecución continuarán durante el período de tiempo de espera de inactividad. El período de tiempo de espera de inactividad predeterminado es de 30 minutos. Puede definir su configuración de tiempo de espera personal para los codespaces que cree, pero una directiva de tiempo de espera de la organización puede invalidarla.

Solo los codespaces en ejecución conllevan cargos de CPU. Un codespace detenido solo conlleva costos de almacenamiento.

Puede detener y reiniciar un codespace para aplicar cambios. Por ejemplo, si cambia el tipo de máquina que se usa para el codespace, debe detenerlo y reiniciarlo para que el cambio surta efecto. Al cerrar o detener su codespace, todos los cambios pendientes de confirmación se preservan hasta que vuelva a conectarse al codespace.

También puede detener el codespace y elegir restablecerlo o eliminarlo si encuentra un error o algo inesperado.

## Recompilación de un codespace

Puede recompilar el codespace para implementar cambios en la configuración de contenedor de desarrollo. Para la mayoría de los usos, puede crear un codespace como alternativa a recompilar uno. Al recompilar su codespace, las imágenes de la memoria caché aceleran el proceso de recompilación. También puede realizar una recompilación completa para borrar la memoria caché y recompilar el contenedor con imágenes nuevas.

Al recompilar el contenedor en un codespace, los cambios realizados fuera del directorio /workspaces se borran. Los cambios realizados dentro del directorio /workspaces, incluido el clon del repositorio o la plantilla desde la que ha creado el codespace, se conservan al recompilar.

## Eliminar un codespace

Puede crear un codespace para una tarea determinada. Después de enviar los cambios a una rama remota, puede eliminar ese codespace de forma segura.

Si intenta eliminar un codespace con confirmaciones de GIT sin enviar, el editor le notifica que tiene cambios que no se han enviado a una rama remota. Puede enviar cualquier cambio deseado y, después, eliminar su codespace. También puede continuar con la eliminación del codespace y los cambios pendientes de confirmación o exportar el código a una rama nueva sin crear un codespace.

Los codespaces detenidos que permanecen inactivos durante un período de tiempo especificado se eliminan automáticamente. Los codespaces inactivos se eliminan después de 30 días, pero puede personalizar los intervalos de retención de codespaces.
