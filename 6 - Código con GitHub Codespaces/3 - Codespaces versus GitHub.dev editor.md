# Codespaces versus GitHub.dev editor

Probablemente se pregunte cuándo debe usar GitHub Codespaces y cuándo GitHub.dev.

Puede usar GitHub.dev para navegar por archivos y repositorios de código fuente desde GitHub, así como hacer cambios de código y confirmarlos. Puede abrir cualquier repositorio, bifurcación o solicitud de incorporación de cambios en el editor GitHub.dev.

Si quiere realizar tareas más complicadas, como probar el código, use GitHub Codespaces. Se asocia con un proceso, por lo que puede compilar el código, ejecutarlo y tener acceso de terminal. GitHub.dev no incluye ningún proceso. Con GitHub Codespaces se obtiene la potencia de una máquina virtual (VM) personal con acceso de terminal, de la misma forma que puede usar el entorno local, solo en la nube.

Comparison of Codespaces and GitHub.dev
En la tabla siguiente se enumeran las diferencias principales entre Codespaces y GitHub.dev:

<table aria-label="Comparison of Codespaces and GitHub.dev" class="table">
    <thead>
        <tr>
            <th></th>
            <th scope="col">GitHub.dev</th>
            <th scope="col">GitHub Codespaces</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">Costee</th>
            <td>Gratuito</td>
            <td>Cuota mensual gratuita de uso para cuentas personales</td>
        </tr>
        <tr>
            <th scope="row">Disponibilidad</th>
            <td>Disponible para todos en GitHub.com</td>
            <td>Disponible para todos en GitHub.com</td>
        </tr>
        <tr>
            <th scope="row">Startup</th>
            <td>GitHub.dev se abre instantáneamente al presionar una tecla y puede comenzar a usarlo de inmediato sin tener que esperar a su configuración o instalación.</td>
            <td>Al crear o reanudar un codespace, a este se le asigna una máquina virtual y el contenedor se configura en función del contenido de un archivo devcontainer.json. Esta configuración tarda unos minutos en crear el entorno de desarrollo.</td>
        </tr>
        <tr>
            <th scope="row">Proceso</th>
            <td>No hay cálculos asociados, así que no podrá compilar y ejecutar su código ni utilizar el terminal integrado.</td>
            <td>Con GitHub&nbsp;Codespaces se obtiene la eficacia de una máquina virtual dedicada para ejecutar y depurar la aplicación.</td>
        </tr>
        <tr>
            <th scope="row">Acceso al terminal</th>
            <td>Ninguno</td>
            <td>GitHub&nbsp;Codespaces proporciona un conjunto común de herramientas de manera predeterminada, lo que significa que puede utilizar el terminal exactamente como lo haría en su entorno local.</td>
        </tr>
        <tr>
            <th scope="row">Extensiones</th>
            <td>En la vista de extensiones solo aparece un subconjunto de las extensiones que pueden ejecutarse en la web y que se pueden instalar.</td>
            <td>Con GitHub Codespaces se pueden usar la mayoría de las extensiones de Visual&nbsp;Studio Code Marketplace.</td>
        </tr>
    </tbody>
</table>

## Continuación del trabajo en Codespaces

Puede iniciar el flujo de trabajo en Github.dev y seguir trabajando en un codespace. Si intenta acceder a la vista de ejecución y depuración o al terminal, se le notifica que no están disponibles en GitHub.dev.

Para continuar el trabajo en un codespace, seleccione Continuar trabajando en.... Seleccione Crear un codespace para crear un codespace en la rama actual. Antes de que elijas esta opción, debes confirmar cualquier cambio.
