# Qué es GitHub Copilot

A menudo, al escribir código, debe consultar documentación oficial u otras páginas web para recordar la sintaxis o cómo resolver un problema. También puede dedicar horas a intentar resolver un problema cuando el código no funciona. Además, también dedica tiempo a escribir pruebas y documentación. Todas estas tareas consumen mucho tiempo y, para ser más eficaces, podría usar fragmentos de código o confiar en herramientas en el IDE (entorno de desarrollo integrado) pero, ¿hay una mejor manera?

¿Cómo funciona?
GitHub Copilot es un asistente de inteligencia artificial que se usa desde el IDE y que es capaz de generar código y mucho más. GitHub Copilot usa solicitudes, lenguaje natural y proporciona sugerencias basadas en lo que usted escribe. Una solicitud puede, por ejemplo, tener el siguiente aspecto:

    // Create a web API using express and JavaScript with routes for products and customers

Después, Copilot va a generar una respuesta que puede aceptar o rechazar. Una respuesta a la solicitud podría ser similar a la siguiente:

    const express = require(“express”);

    app = express();
    app.path(“/products”, () => “products”);
    app.listen(3000, () => “app runs”);

Cómo reconoce las solicitudes
Copilot puede decir que algo es una solicitud, una instrucción, si:

Se escribe como un comentario en un archivo de código con un archivo que termina como `.py` o `.js`, por ejemplo.

Se escribe como texto en un archivo Markdown y espera a que Copilot devuelva una respuesta en unos segundos.

Aceptación de sugerencias
Lo que recibe de Copilot es una sugerencia, texto que se muestra como código gris, si usa negro como color de texto. Para aceptar la sugerencia, deberá presionar la tecla "Tabulador".

Copilot puede sugerir más de una opción y es posible desplazarse entre las sugerencias mediante la tecla "ctrl + entrar" y seleccionar la más adecuada.

Cómo configurar GitHub Copilot
Para usar GitHub Copilot, necesita lo siguiente:

Cree una cuenta de GitHub. Ya que Copilot es un servicio de GitHub, necesita una cuenta de GitHub para usar el servicio.

Regístrese. Debe registrarse en Copilot a través de su página web.

En GitHub, seleccione su perfil y, a continuación, vaya a la configuración en la que, en Copilot, puede habilitar el acceso o registrarse para obtener una prueba gratuita.

Para usar GitHub Copilot, debe instalarlo como una extensión en el IDE.

Las extensiones están disponibles para los IDE principales, como Visual Studio, Visual Studio Code.
