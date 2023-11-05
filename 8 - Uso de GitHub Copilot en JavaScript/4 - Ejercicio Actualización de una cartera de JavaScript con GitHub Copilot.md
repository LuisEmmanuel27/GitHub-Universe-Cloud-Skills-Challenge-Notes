# Ejercicio: Actualización de una cartera de JavaScript con GitHub Copilot

Vamos a explorar cómo puede usar las sugerencias de código de GitHub Copilot. En este ejercicio, agregará animaciones con sugerencias en directo y usará un mensaje para personalizar el comportamiento de desplazamiento de un repositorio de plantillas de JavaScript ya existente. Con GitHub Copilot, puede trabajar rápidamente con una situación de JavaScript en la vida real.

## Cartera de JavaScript

Tanto si es alumno, se acaba de graduar o es un profesional experimentado, su cartera es su espacio personal para mostrar sus aptitudes y experiencia.

Tener una cartera proporciona credibilidad y notoriedad a la experiencia que menciona en su currículum al solicitar empleos. No importa si es científico de datos, diseñador de la experiencia de usuario o desarrollador front-end. Una presencia fuerte en línea puede ayudarle a conseguir un trabajo y a que le descubran.

## **Nota**

**Para este ejercicio, use <a href="https://github.com/codespaces/new/MicrosoftDocs/mslearn-copilot-codespaces-javascript?quickstart=1">Codespace</a> con el entorno preconfigurado en el explorador.**

## Personalización de la cartera de JavaScript

En esta cartera de plantillas, tenemos una aplicación web basada en React que puede usar para personalizar e implementar contenido fácilmente con solo el explorador web.

Antes de empezar, puede personalizar la cartera con sus propios vínculos. Vaya a `src/App`.jsx y actualice `siteProps` con su información. La variable `siteProps` es un objeto de JavaScript que contiene pares clave-valor que se usan para personalizar el sitio. Debería tener este aspecto:

    const siteProps = {
        name: "Alexandrie Grenier",
        title: "Web Designer & Content Creator",
        email: "alex@example.com",
        gitHub: "microsoft",
        instagram: "microsoft",
        linkedIn: "satyanadella",
        medium: "",
        twitter: "microsoft",
        youTube: "Code",
    };

## Animación de los iconos de las redes sociales con un mensaje

Una animación puede hacer que la sección de redes sociales sea más atractiva. Pida ayuda de Copilot para animar los iconos. Escriba el siguiente mensaje en el archivo `src/styles.css`:

    /* add an amazing animation to the social icons */

La sugerencia de Copilot debería ser similar a la siguiente:

    img.socialIcon:hover {
        animation: bounce 0.5s;
        animation-iteration-count: infinite;
    }

    @keyframes bounce {
        0% {
            transform: scale(1);
        }
        50% {
            transform: scale(1.2);
        }
        100% {
            transform: scale(1);
        }
    }

Para aceptar la sugerencia, presione el tabulador. Si no recibe la misma sugerencia exacta, puede experimentar con la sugerencia proporcionada o seguir escribiendo el código CSS hasta que coincida.

El sitio ya debe estar ejecutándose en el codespace, y el cambio se volverá a cargar en la página automáticamente. Para verlo, mantenga el puntero sobre uno de los iconos de las redes sociales en el pie de página.

Enhorabuena, a través del ejercicio, no solo ha usado Copilot para generar código, sino que también lo ha hecho de forma interactiva y divertida. Puede utilizar GitHub Copilot no solo para generar código, sino también para escribir documentación, probar sus aplicaciones y mucho más.

Cuando haya terminado el ejercicio en GitHub, vuelva aquí para lo siguiente:

✔️ Prueba de conocimientos breve
✔️ Resumen de lo que ha aprendido
✔️ Distintivo por completar este módulo
