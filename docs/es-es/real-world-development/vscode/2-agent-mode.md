---
title: "Ejercicio 2: Añade funcionalidad con el modo de agente de Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Incluso los cambios más sencillos de una aplicación suelen requerir modificar varios archivos y realizar tareas como ejecutar pruebas. El flujo habitual de un desarrollador consiste en localizar todos los archivos necesarios, hacer los cambios, ejecutar las pruebas, depurar, averiguar qué archivo falta, volver a modificarlo… y así sucesivamente.

El modo de agente de Copilot puede ayudarte con ese trabajo.

El modo de agente de Copilot está diseñado para trabajar de forma más autónoma en el entorno de desarrollo integrado (IDE). Se comporta de manera parecida a un desarrollador: primero explora la estructura del proyecto, realiza los cambios necesarios, ejecuta tareas como las pruebas y corrige automáticamente los errores que encuentra. Explora cómo usar el modo de agente para añadir funcionalidad al sitio.

> [!NOTE]
> Aunque los nombres se parecen, el modo de agente y el agente en la nube ofrecen experiencias distintas. El modo de agente trabaja en tu IDE y permite ciclos de respuesta e interacción rápidos. El agente en la nube trabaja de forma asíncrona como integrante del equipo y se comunica contigo mediante incidencias y solicitudes de incorporación de cambios.

En este ejercicio aprenderás cómo:

- el modo de agente de Copilot explora el proyecto, identifica los archivos pertinentes y coordina los cambios.
- el modo de agente de GitHub Copilot implementa funcionalidades en la interfaz de usuario (UI) y la capa de datos.
- revisar los cambios y las pruebas generados por Copilot antes de combinarlos en el código.

## Escenario

A medida que crece la lista de juegos, quieres permitir que se filtren por categoría y editorial. En el ejercicio anterior ya creaste una función auxiliar de editoriales; ahora completarás con el modo de agente de Copilot el resto del trabajo de la capa de datos, la interfaz de usuario y las pruebas.

## Ejecuta el sitio web Tailspin Toys

Antes de hacer cambios, explora el sitio web Tailspin Toys para conocer su funcionalidad actual.

El sitio es una plataforma de financiación colectiva para juegos de mesa con temática de desarrollo. Permite mostrar los juegos y sus detalles. Toda la aplicación es un proyecto Astro que genera páginas en lenguaje de marcado de hipertexto (HTML) estáticas en el momento de la compilación. Las páginas consultan directamente una base de datos SQLite local mediante Drizzle, un mapeador objeto-relacional (ORM); no hay una interfaz de programación de aplicaciones (API) de backend independiente ni un framework de interfaz de cliente. Las funciones auxiliares de acceso a datos están en `src/lib/`, y la interactividad se implementa con pequeños elementos `<script>` de Astro que usan las API estándar del modelo de objetos del documento (DOM).

### Inicia el sitio web

Para simplificar el inicio del sitio, el proyecto incluye una tarea `npm run dev` que inicia el único servidor de desarrollo de Astro. Ejecútala en tu GitHub Codespace:

1. Vuelve a tu codespace. Después del ejercicio anterior, deberías estar en `main`.
2. Abre un terminal nuevo en el Codespace pulsando <kbd>Control</kbd>+<kbd>`</kbd> (Mac) o <kbd>Ctrl</kbd>+<kbd>`</kbd> (Windows/Linux).
3. Crea una rama para el trabajo de filtrado y cámbiate a ella:

   ```bash
   git checkout main
   git pull
   git checkout -b filtering-vscode
   ```

4. Inicia el sitio web con este comando:

   ```bash
   npm run dev
   ```

   Cuando se inicie el servidor de desarrollo de Astro, verás un mensaje parecido a este:

   ```bash
   🚀 Tailspin Toys is ready!
      Astro server: http://localhost:4321
      Press Ctrl-C to stop.
   ```

> [!NOTE]
> Si aparece un cuadro de diálogo para abrir `http://localhost:4321` en el navegador, ciérralo seleccionando **x**.

5. Para abrir el sitio, mantén pulsada la tecla <kbd>Command</kbd> (Mac) o <kbd>Ctrl</kbd> (Windows/Linux) y selecciona la dirección del servidor Astro `http://localhost:4321` en el terminal.

> [!NOTE]
> En un codespace, al seleccionar el enlace localhost en el terminal se te redirigirá automáticamente a `https://<your-codespace-name>-4321.app.github.dev/`. Se trata de un túnel privado al codespace, que ahora aloja el servidor web.

### Explora el sitio web

Cuando el sitio esté en ejecución, explora sus funciones principales:

- **Página de inicio**: muestra juegos de mesa con sus títulos, imágenes y descripciones.
- **Página de detalles del juego**: al seleccionar un juego, se abre una página con más información, como el título, la descripción, la editorial y la categoría.

## Explora el backlog con Copilot

> [!TIP]
> **Abre Copilot Chat**
>
> Antes de empezar, vuelve al codespace, abre el panel de Copilot Chat y selecciona **New Chat** para iniciar una conversación nueva. El modo y el modelo varían según el ejercicio; cada paso indicará qué seleccionar cuando sea necesario.

La implementación inicial del sitio funciona, pero queremos añadir más funciones. Empieza por revisar el backlog. Al crear el proyecto a partir de la plantilla, se generó automáticamente un backlog de incidencias. Pide a GitHub Copilot que te muestre esas tareas.

1. En el menú desplegable de agentes de la vista Chat, selecciona **Agent**. El agente planifica e implementa cambios en varios archivos, ejecuta comandos de terminal y usa herramientas.

   ![Selector de agentes en la vista Chat.](../../../_images/shared-chat-mode-selector.png)

2. Selecciona **Claude Sonnet 4.5** en la lista de modelos disponibles.

> [!CAUTION]
> Los autores de este taller no recomiendan un modelo sobre otro. Durante su elaboración usamos Claude Sonnet 4.5 y lo incluimos en estas instrucciones para que las sugerencias fueran relativamente coherentes y la experiencia, satisfactoria. Sin embargo, como los modelos de lenguaje grandes (LLM) son probabilísticos, es normal que las sugerencias varíen.

> [!NOTE]
> Debido al carácter probabilístico de los modelos de lenguaje grandes, Copilot puede usar un comando del protocolo de contexto de modelo (MCP) distinto y aun así completar la tarea.

3. Envía este prompt para pedir a Copilot que muestre el backlog de incidencias:

   ```plaintext
   Please show me the backlog of items from my GitHub repository. Help me prioritize them based on those which will be most useful to the user.
   ```

4. Selecciona **Continue** para permitir que se enumeren todas las incidencias.
5. Revisa la lista generada.

Observa que Copilot también ha priorizado las tareas según lo que considera más útil para los usuarios.

## Revisa los archivos de instrucciones

Antes de pedir al agente que genere código, revisa el archivo de instrucciones que proporcionará contexto a Copilot. Usarás el archivo de [instrucciones de interfaz de usuario](https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/ui.instructions.md), que explica cómo añadir funciones al sitio web.

1. En el codespace, abre `.github/instructions/ui.instructions.md`.
2. Revisa las indicaciones generales para añadir funcionalidad, entre ellas:
   - Una descripción de la arquitectura.
   - Principios de diseño de componentes, facilidad de prueba y accesibilidad.
   - Enlaces a instrucciones específicas para distintos tipos de archivo, como:
     - Astro
     - Tailwind CSS
     - Drizzle

> [!TIP]
> Los archivos de instrucciones pueden incluir enlaces a otros archivos de instrucciones y a archivos del proyecto. Las rutas son relativas al archivo de instrucciones. Así puedes reutilizar indicaciones, dividir instrucciones complejas en archivos más manejables y proporcionar ejemplos y plantillas.

## Implementa el filtrado

Para completar el filtrado hay que hacer al menos tres cambios independientes en la aplicación:

- Añadir o mejorar la lógica de filtrado en la capa de datos (`src/lib/`).
- Añadir o actualizar pruebas del comportamiento del filtrado.
- Actualizar la página de lista de juegos para incluir la interfaz de filtrado.

Además, las pruebas deben ejecutarse y superarse antes de combinar los cambios. El modo de agente de Copilot puede realizar estas tareas. Añade la funcionalidad:

1. Continúa en la conversación actual con Copilot o selecciona **New Chat** para empezar otra.
2. Selecciona **Add Context**, **Instructions** y **ui** como archivo de instrucciones.

   ![Ejemplo de selección del archivo de instrucciones de interfaz de usuario](../../../_images/ex3-select-instructions-file.png)

3. Confirma que **Agent** siga seleccionado en el menú desplegable de agentes de la vista Chat.

   ![Selector de agentes en la vista Chat.](../../../_images/shared-chat-mode-selector.png)

4. Confirma que **Claude Sonnet 4.5** siga seleccionado como modelo.
5. Usa este prompt para pedir a Copilot que implemente la funcionalidad según la incidencia relacionada del backlog:

   ```plaintext
   Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
   ```

6. Observa cómo Copilot explora el proyecto y localiza los archivos relacionados con la funcionalidad: las funciones auxiliares de la capa de datos, la interfaz y las pruebas. Después, modifica los archivos y ejecuta las pruebas.

   ![Copilot explora los archivos del proyecto](../../../_images/ex3-agent-mode-explores.png)

> [!NOTE]
> Copilot explorará el proyecto, modificará archivos y ejecutará pruebas. El proceso puede tardar varios minutos, según la complejidad de la tarea y del código. Mientras trabaja, puede que aparezcan los botones **Keep** y **Undo** en el editor. Cuando termine, verás uno de estos botones para cada cambio. No hace falta que los selecciones mientras el agente sigue trabajando.

7. Cuando Copilot te lo pida, selecciona **Continue** para ejecutar las pruebas.

   ![Cuadro de diálogo de Copilot Chat que pide permiso para ejecutar pruebas](../../../_images/ex3-agent-mode-run-tests.png)

8. Puede que Copilot se detenga varias veces y que algunas pruebas fallen durante el proceso. Es normal: alterna entre generar código y ejecutar pruebas hasta completar la tarea y dejar de detectar errores.

   ![Sesión completa de Copilot Agent Mode en el chat](../../../_images/ex3-agent-mode-proposed-changes.png)

9. Explora el código generado para detectar posibles problemas.

> [!CAUTION]
> Revisa siempre el código que genere Copilot o cualquier otra herramienta de inteligencia artificial.

10. Vuelve al navegador donde se está ejecutando el sitio y explora la nueva funcionalidad.
11. Cuando hayas confirmado que todo funciona y revisado el código, selecciona **Keep** en la ventana de Copilot Chat.

## Resumen y siguientes pasos

Has explorado cómo usar el modo de agente de GitHub Copilot para añadir funciones al sitio web Tailspin Toys. En concreto, has aprendido cómo:

- El modo de agente de GitHub Copilot implementa funciones en la interfaz y la capa de datos.
- El modo de agente de Copilot explora el proyecto, identifica los archivos pertinentes y coordina los cambios.
- Revisar los cambios y las pruebas generados por el modo de agente antes de combinarlos en el código.

A continuación, [probarás la funcionalidad con el servidor Playwright MCP][next-lesson] y abrirás una solicitud de incorporación de cambios.

### Ejercicio de exploración adicional: implementa la paginación

A medida que crezca la lista de juegos, será necesario habilitar la paginación. Usa lo aprendido en este ejercicio y pide a Copilot que implemente la paginación del sitio. Al redactar el prompt, considera:

- Seguir las prácticas recomendadas existentes, incluidos los archivos de instrucciones.
- Decidir cómo implementar la paginación: por ejemplo, si quieres que el usuario pueda seleccionar el tamaño de página o prefieres definirlo en el código.
- Dar a Copilot las indicaciones necesarias para que implemente lo que necesitas.
- Iterar con Copilot, solicitar cambios y proporcionar contexto. Es el proceso habitual al trabajar con Copilot.

## Recursos

- [Modos ask, edit y agent de Copilot: qué hacen y cuándo usarlos][choose-mode]
- [Modo de agente en VS Code][vs-code-agent-mode]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-mcp/
[choose-mode]: https://github.blog/ai-and-ml/github-copilot/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/
[vs-code-agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
