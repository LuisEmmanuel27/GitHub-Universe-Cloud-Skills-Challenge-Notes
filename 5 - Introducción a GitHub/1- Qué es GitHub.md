# ¿Qué es GitHub?

Aquí se describen las principales características de GitHub que se usan a diario para administrar y contribuir a proyectos de software.

## El flujo de GitHub

Además de ser una plataforma de desarrollo de software colaborativo, GitHub ofrece también un flujo de trabajo diseñado para optimizar el uso de sus diversas características. Aunque esta unidad ofrece una visión general de los componentes importantes de la plataforma, se recomienda que primero revise el <a href="https://docs.github.com/es/get-started/quickstart/github-flow">Flujo de GitHub</a>.

## Git y GitHub

Cuando trabaje con Git y GitHub, es posible que se pregunte en qué se diferencian.

Git es un sistema de control de versiones distribuido (DVCS) que permite que varios desarrolladores u otros colaboradores trabajen en un proyecto. Proporciona una manera de trabajar con una o varias ramas locales e insertarlas en un repositorio remoto. Git es responsable de todo lo que sucede localmente en el equipo relacionado con GitHub. Las características principales de Git incluyen:

-   Está instalado y se usa en el equipo local.
-   Se ocupa del control de versiones.
-   Admite la creación de ramas.

Para obtener más información sobre Git, consulte <a href="https://docs.github.com/es/get-started/using-git">Uso de Git</a>.

**GitHub** es una plataforma en la nube que usa Git como tecnología principal. Simplifica el proceso de colaborar en proyectos y proporciona un sitio web, herramientas de línea de comandos y un flujo global que permite a los desarrolladores y usuarios trabajar juntos. _GitHub_ actúa como el "repositorio remoto" mencionado anteriormente en la sección _Git_.

Las características principales de GitHub incluyen:

-   Issues
-   Debates
-   Solicitudes de incorporación de cambios
-   Notificaciones
-   Etiquetas
-   Acciones
-   Horquillas
-   Proyectos

Para obtener más información sobre GitHub, consulte <a href="https://docs.github.com/es/get-started">Introducción a GitHub</a>.

## Incidencias

Las incidencias son el elemento en el que se produce la mayor parte de la comunicación entre los consumidores y el equipo de desarrollo de un proyecto. Puede crear una incidencia para analizar una amplia variedad de temas, como informes de errores, solicitudes de características, aclaraciones sobre la documentación, etc. Una vez creado un problema, puede asignar propietarios, etiquetas, proyectos e hitos. Las incidencias también se pueden asociar con solicitudes de incorporación de cambios y otros elementos de GitHub para proporcionar rastreabilidad en el futuro.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-issue.png"/>

Para obtener más información sobre las incidencias de GitHub, vea <a href="https://docs.github.com/es/issues/tracking-your-work-with-issues/about-issues">Acerca de las incidencias</a>.

## Notificaciones

Como plataforma colaborativa, GitHub ofrece notificaciones para prácticamente todos los eventos que se producen en un flujo de trabajo determinado. Puede ajustar estas notificaciones en función de las preferencias. Por ejemplo, puede suscribirse a todas las creaciones y ediciones de incidencias de un proyecto, o bien recibir notificaciones únicamente de las incidencias en las que se le mencione. También puede decidir si recibirá notificaciones por correo electrónico, por web y dispositivo móvil, o ambos. Para llevar un seguimiento de todas las notificaciones en distintos proyectos, use el <a herf="https://github.com/notifications">panel de notificaciones de GitHub</a>.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-notifications.png"/>

Para obtener más información sobre las notificaciones de GitHub, vea <a href="https://docs.github.com/es/enterprise-server@3.10/account-and-profile/managing-subscriptions-and-notifications-on-github/setting-up-notifications/configuring-notifications">Configuración de notificaciones</a>.

## Ramas

Las ramas son la manera preferida de crear cambios en el <a href="https://docs.github.com/es/get-started/quickstart/github-flow">flujo de GitHub</a>. Proporcionan aislamiento para que varias personas puedan trabajar simultáneamente en el mismo código de manera controlada. Este modelo garantiza la estabilidad entre las ramas críticas, como main, a la vez que da libertad a los desarrolladores para confirmar los cambios que necesiten para alcanzar sus objetivos. Una vez que el código de una rama está listo para formar parte de la rama main, puede combinarlo mediante una solicitud de incorporación de cambios.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-branching.png"/>

Para obtener más información sobre las ramas de GitHub, vea <a href="https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches">Acerca de las ramas</a>.

## Confirmaciones

Un commit refleja uno o varios cambios en uno o varios archivos de una rama. Cada vez que se crea una confirmación, se le asigna un identificador único y se realiza un seguimiento de ella, junto con la hora y el colaborador. Esto proporciona un registro de auditoría claro para todas las personas que revisen el historial de un archivo o un elemento vinculado, como una incidencia o una solicitud de incorporación de cambios.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-commits.png"/>

Para obtener más información sobre las confirmaciones de GitHub, vea <a href="https://docs.github.com/es/desktop/making-changes-in-a-branch/committing-and-reviewing-changes-to-your-project-in-github-desktop">Confirmación y revisión de cambios en el proyecto</a>.

## Solicitudes de incorporación de cambios

Una solicitud de incorporación de cambios es un mecanismo que sirve para indicar que las confirmaciones de una rama están listas para combinarse en otra. El desarrollador que envíe la solicitud de incorporación de cambios normalmente solicitará a uno o varios revisores que comprueben el código y aprueben la combinación. Estos revisores podrán comentar los cambios, agregar otros o usar la solicitud de incorporación de cambios para realizar un análisis más exhaustivo. Una vez que los cambios se han aprobado (en caso de que se requiera aprobación), la rama de origen de la solicitud de incorporación de cambios (la rama de comparación) se podrá combinar con la rama base.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-pull-request.png"/>

Para obtener más información sobre las solicitudes de incorporación de cambios de GitHub, vea <a href="https://docs.github.com/es/enterprise-server@3.10/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests">Acerca de las solicitudes de incorporación de cambios</a>.

## Etiquetas

Las etiquetas proporcionan una manera de categorizar y organizar las incidencias y las solicitudes de incorporación de cambios en un repositorio. Al crear un repositorio de GitHub, se agregan automáticamente varias etiquetas. También puede crear nuevas.

Estos son algunos ejemplos de etiquetas:

-   error
-   en línea
-   duplicar
-   Se solicita ayuda
-   mejora
-   question

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-labels.png"/>

Para obtener más información sobre las etiquetas de GitHub, vea <a href="https://docs.github.com/es/issues/using-labels-and-milestones-to-track-work/managing-labels">Administrar etiquetas</a>.

## Acciones

Las _acciones de GitHub_ proporcionan funcionalidad de flujo de trabajo y automatización de tareas en un repositorio. Puede usar las acciones para simplificar los procesos del ciclo de vida de desarrollo de software e implementar la integración y la implementación continuas (CI/CD).

Las Acciones de GitHub tienen estos componentes:

-   **Flujos de trabajo**: procesos automatizados que se han agregado al repositorio.
-   **Eventos**: actividades que desencadenan un flujo de trabajo.
-   **Trabajos**: conjunto de pasos que se ejecutan en un ejecutor.
-   **Pasos**: tarea que puede ejecutar uno o varios comandos (acciones).
-   **Acciones**: comandos independientes que puede combinar en pasos. Puede combinar varios pasos para crear un trabajo.
-   **Ejecutores**: servidor que tiene instalada la aplicación de ejecutor de Acciones de GitHub.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-actions.png">

Para obtener más información sobre las acciones de GitHub, consulte <a href="https://docs.github.com/es/actions/learn-github-actions/understanding-github-actions">Descripción de Acciones de GitHub</a>.

## Clonación y bifurcación

GitHub proporciona varias maneras de copiar un repositorio para poder trabajar en él.

-   **Clonar un repositorio**: al clonar un repositorio, se realiza una copia del repositorio y de su historial en el equipo local. Si tiene acceso de escritura al repositorio, puede enviar los cambios de la máquina local al repositorio remoto (denominado origen) a medida que se completan. Para clonar un repositorio, puede usar el comando <a href="https://docs.github.com/en/get-started/using-git/getting-changes-from-a-remote-repository#cloning-a-repository">git clone [url]</a> o el comando <a href="https://cli.github.com/manual/gh_repo_clone">gh repo clone [url]</a> de la CLI de GitHub.

-   **Bifurcación de un repositorio**: al bifurcar un repositorio, se realiza una copia del repositorio en la cuenta de GitHub. El repositorio principal se denomina ascendente, mientras que la copia bifurcada se conoce como origen. Una vez que haya bifurcado un repositorio en la cuenta de GitHub, puede clonarlo en el equipo local. La bifurcación permite realizar cambios libremente en un proyecto sin afectar al repositorio ascendente original. Para contribuir con cambios en el repositorio ascendente, cree una solicitud de incorporación de cambios desde el repositorio bifurcado. También puede ejecutar comandos `git` para asegurarse de que la copia local permanezca sincronizada con el repositorio ascendente.

¿Cuándo debería clonar un repositorio en lugar de bifurcarlo? Si está trabajando con un repositorio y tiene acceso de escritura, puede clonarlo en el equipo local. Desde allí, puede realizar modificaciones e introducir los cambios directamente en el repositorio de origen.

Si necesita trabajar con un repositorio creado por otro propietario, como `github/example`, y no tiene acceso de escritura, puede bifurcar el repositorio en su cuenta de GitHub y, luego, clonar la bifurcación en el equipo local. Para representarlo visualmente, supongamos que su cuenta de GitHub se denomina `githubtraining`. A través del sitio web de GitHub, puede bifurcar `github/example` o cualquier otro repositorio en su cuenta. Desde allí, puede clonar la versión bifurcada del repositorio en el equipo local. En la siguiente imagen se muestran estos pasos:

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-fork-clone.png">

Puede realizar cambios en la copia local de `githubtraining/example` y, a continuación, volver a insertarlos en el repositorio de origen remoto (`githubtraining/example`). A continuación, puede enviar estos cambios al repositorio `github/example` **ascendente** mediante una _solicitud de incorporación de cambios_, como se muestra en la siguiente imagen:

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-fork-pullrequest.png">

Para obtener más información, consulte <a href="https://docs.github.com/en/get-started/quickstart/fork-a-repo">bifurcar un repositorio</a>.

GitHub Pages
GitHub Pages es un motor de hospedaje que está integrado directamente en la cuenta de GitHub. Si sigue una serie de convenciones y habilita la característica, puede crear su propio sitio estático generado a partir de código HTML y Markdown extraído directamente del repositorio.

<img src="https://learn.microsoft.com/es-mx/training/github/introduction-to-github/media/2-github-pages.png">

Para obtener más información, vea <a href="https://pages.github.com/">GitHub Pages</a>.
