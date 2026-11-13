---
title: "Ejercicio 4: Supervisar y administrar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

En los últimos ejercicios has pedido al agente en la nube de Copilot que se ocupe de tres tareas distintas para mejorar la experiencia de usuario y añadir funcionalidades. Aunque trabaja de forma asíncrona y autónoma, es importante que puedas supervisar las tareas.

Dispones de varias herramientas para administrar las tareas asignadas al agente en la nube, incluida la [página de agentes][agents-page] de GitHub.com. Desde este centro de control puedes ver todas las tareas de los agentes que tienen solicitudes de incorporación de cambios abiertas, consultar las operaciones realizadas e incluso guiar una sesión en curso.

En este ejercicio:

- Explorarás la página de agentes para supervisar las tareas del agente en la nube.
- Guiarás una sesión en curso para pedir una funcionalidad adicional.

## Escenario

Después de asignarle la creación de un modo de alto contraste, el equipo decidió que sería buen momento para añadir también un modo claro. Como ya se estaba actualizando el estilo del sitio y añadiendo controles de cambio de modo, parecía razonable incluir esta funcionalidad. Guiarás el trabajo del agente para que añada el modo claro además del modo de alto contraste.

## Revisa las tareas del agente en la nube de Copilot

Consulta el estado de las tareas que has asignado al agente en la nube de Copilot.

1. Abre la [página de agentes de Copilot](https://github.com/copilot/agents).
2. Observa las tareas de los paneles principal e izquierdo. Deberías ver las tareas que has asignado a Copilot, entre ellas:
   - Actualizar la documentación del código.
   - Generar interfaces de programación de aplicaciones (API) para modificar juegos.
   - Añadir un modo de alto contraste al sitio web.
3. Selecciona una de las tareas en curso y revisa las operaciones que ha realizado Copilot. Pueden incluir:
   - Obtener una copia del código del repositorio.
   - Crear el entorno de trabajo de Copilot.
   - Configurar servidores del protocolo de contexto de modelo (MCP).
   - Realizar distintos pasos para completar la tarea asignada.

> [!NOTE]
> Los pasos concretos variarán según el estado del trabajo de Copilot y el enfoque que haya seguido.

4. Observa también el panel de solicitudes de incorporación de cambios de la derecha. Desde allí puedes consultar la solicitud y los archivos modificados para seguir supervisando el trabajo.

## Guía al agente en la nube

Ahora que has visto las tareas activas, pídele a Copilot que añada un control para el modo claro mientras trabaja en el modo de alto contraste.

1. Selecciona la sesión relacionada con el modo de alto contraste. El título exacto dependerá del nombre que le haya dado Copilot y del estado actual del trabajo.

    ![Sesión de accesibilidad en el centro de control](../../../_images/ex6-accessibility-session.png)

2. Observa la sesión durante unos minutos, hasta que indique que ha terminado de configurar el entorno y ha empezado a trabajar. Lo sabrás cuando aparezcan mensajes parecidos a los siguientes.
3. En el cuadro de diálogo **Steer active session while Copilot is working**, escribe este prompt:

    ```plaintext
    While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
    ```

    ![Tarea del agente en la nube en la página de agentes, con el cuadro de diálogo Steer active session while Copilot is working resaltado](../../../_images/ex6-steer-cloud-agent-task.png)

4. Pulsa <kbd>Enter</kbd> para enviar el prompt.
5. Observa cómo Copilot confirma que lo ha recibido y lo incorpora a su flujo de trabajo.

## Deja que Copilot trabaje

Como antes, Copilot empezará a trabajar en la tarea actualizada. Incorporará la nueva solicitud al flujo cuando termine el paso en curso.

El proceso tardará varios minutos. Es un buen momento para hacer una pausa y repasar lo que has aprendido y explorado hasta ahora.

## Resumen y siguientes pasos

En este ejercicio has explorado la página de agentes de Copilot, el centro de control para supervisar y guiar las tareas del agente en la nube de GitHub Copilot. Desde allí puedes seguir las tareas activas y completadas, revisar el trabajo y redirigir las tareas en curso para ajustar su alcance o añadir indicaciones.

Has explorado estos conceptos:

- Exploraste el centro de control y la página de agentes para supervisar las tareas del agente en la nube.
- Redirigiste una sesión en curso para pedir una funcionalidad adicional.

Mientras Copilot termina de trabajar en las funciones de accesibilidad, puedes [iterar sobre las solicitudes de incorporación de cambios que ha creado][next-lesson].

## Recursos

- [Página de agentes de Copilot][agents-page]
- [Acerca de los agentes personalizados][custom-agents]

---

| [← Lección anterior: Agentes personalizados][previous-lesson] | [Siguiente lección: Iterar sobre el trabajo de Copilot →][next-lesson] |
|:--|--:|

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
