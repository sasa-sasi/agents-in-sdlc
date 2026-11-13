---
title: "Ejercicio 5: Iterar sobre el trabajo de GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lección anterior: Administración de agentes][previous-lesson] |
|:--|

## Revisa el trabajo

Durante este taller has trabajado con GitHub Copilot en varias tareas para mejorar la experiencia de usuario y añadir funcionalidades. Le pediste que documentara el código, creara una función de juegos relacionados para que el equipo de diseño pudiera probarla e implementara mejoras de accesibilidad, incluidos controles para los modos de alto contraste y claro. Revisa los cambios de código y, si hace falta, envía comentarios a Copilot para que los mejore.

### Escenario

Como ya hemos señalado, los fundamentos del diseño de software y el desarrollo y las operaciones (DevOps) no cambian por incorporar inteligencia artificial generativa. Siempre debemos revisar el código generado y seguir el proceso habitual de DevOps. Con eso en cuenta, revisa las propuestas de GitHub Copilot para documentar el código, añadir la función de juegos relacionados y mejorar la accesibilidad antes de habilitar la revisión para el resto del equipo.

## Seguridad y agente en la nube de GitHub Copilot

Como el agente en la nube de Copilot realiza tareas de forma asíncrona y sin supervisión, se han establecido restricciones de seguridad para que el trabajo se mantenga protegido. Entre ellas:

- Copilot solo tiene acceso de lectura al repositorio y acceso de escritura **únicamente** a la rama que usará para su código.
- El agente en la nube se ejecuta en GitHub Actions y crea un entorno independiente y efímero para trabajar.
- Una persona debe aprobar cualquier flujo de trabajo de GitHub Actions antes de que pueda ejecutarse.
- [El acceso a recursos externos está limitado de forma predeterminada](https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall), incluidos los servidores del protocolo de contexto de modelo (MCP).

## Revisa la documentación generada

Empieza por la primera solicitud de incorporación de cambios (PR) que generó el agente en la nube de GitHub Copilot: la que añade documentación al código. La revisarás desde la interfaz habitual de PR de GitHub.com.

> [!NOTE]
> Es posible que la PR muestre un aviso de que un firewall bloquea a GitHub Copilot. Es **lo esperado**, porque el acceso del agente en la nube a recursos externos está limitado de forma predeterminada, incluidas las llamadas a servidores MCP externos. Si quieres, puedes [personalizar o deshabilitar el firewall del agente en la nube de Copilot][agent-firewall].

1. Vuelve a tu repositorio en github.com.
2. Selecciona **Pull Requests** para abrir la lista de PR.
3. Abre la solicitud cuyo título se parezca a **Add missing documentation** o que tenga una descripción más detallada.

> [!NOTE]
> Si Copilot aún está trabajando, la solicitud tendrá la etiqueta **[WIP]**. En ese caso, espera a que termine. Puede tardar unos minutos; mientras tanto, puedes descansar o repasar lo aprendido.

4. Cuando la PR esté lista, selecciona la pestaña **Files changed** y revisa los cambios.

    ![Pestaña Files changed](../../../_images/shared-pr-files-changed.png)

5. Explora el código actualizado, que incluye los nuevos comentarios de documentación TSDoc y otros cambios. El contenido exacto variará.

   Al revisar los cambios, busca comentarios TSDoc, convenciones de TypeScript y encabezados de comentarios. Estas indicaciones proceden de los archivos de instrucciones personalizadas que revisaste al principio del Ejercicio 2.

6. Cuando hayas revisado los cambios y estés conforme, vuelve a la pestaña **Conversation** y desplázate hacia abajo.
7. Busca un indicador que señale que hay flujos de trabajo pendientes de aprobación.
8. Si hay flujos pendientes, selecciona **Approve and run workflows**.

   ![Botón Approve and run workflows](../../../_images/shared-approve-workflows.png)

9. Los flujos de trabajo deberían aparecer en la sección de comprobaciones de la PR. Si todo va bien, las comprobaciones del proyecto para la aplicación Astro deberían superarse. Puede tardar unos minutos.

## Pide cambios a GitHub Copilot

La colaboración con Copilot no tiene por qué ser unidireccional. Puedes mencionarlo en comentarios de la PR, igual que harías con otra persona del equipo, o en comentarios en línea sobre el código. Copilot verá esos comentarios e iniciará otra sesión para resolverlos. Como los resultados no son deterministas, no podemos darte un texto exacto que debas usar. Algunas ideas para pedirle cambios:

- Añadir encabezados de comentarios al principio de cada archivo de código con una breve descripción de su función.
- Añadir comentarios de documentación TSDoc a los archivos TypeScript y Astro.
- Crear un archivo README con una descripción de la estructura de la aplicación Astro.

1. Añade un comentario para solicitar un cambio en la documentación generada y menciona a **@copilot**, como harías con cualquier otra persona. Usa una de las ideas anteriores u otra sugerencia sobre la documentación del código.
2. Selecciona **View Session** para observar cómo Copilot trabaja. Verás que inicia una sesión nueva para realizar los cambios.
3. Puedes seleccionar **Back to pull request** para volver a la solicitud.

    ![Botón Back to pull request](../../../_images/ex7-back-to-pr.png)

4. Cuando Copilot termine, debería aparecer una confirmación nueva en la PR.
5. Selecciona la pestaña **Files changed** para revisar los cambios.

Sigue iterando hasta que estés conforme. Después, puedes marcar la PR como lista para revisión y combinarla en la rama principal.

![Opción para marcar una PR como lista para revisión](../../../_images/ex7-ready-for-review.png)

## Revisa la función de juegos relacionados

Vuelve a la PR que Copilot generó para resolver la incidencia sobre los juegos relacionados en la página de detalles.

1. Vuelve a tu repositorio en GitHub.com.
2. Selecciona la pestaña **Pull Requests**.
3. Selecciona la PR cuyo título se parezca a **Show related games on the game details page** o que tenga una descripción más detallada.
4. Selecciona la pestaña **Files changed** para revisar el código generado.
5. Cuando hayas revisado los cambios y estés conforme, vuelve a la pestaña **Conversation** y desplázate hacia abajo.
6. Busca un indicador que señale que hay flujos de trabajo pendientes de aprobación.
7. Si hay flujos pendientes, selecciona **Approve and run workflows**.

   ![Botón Approve and run workflows](../../../_images/shared-approve-workflows.png)

8. Los flujos de trabajo deberían aparecer en la sección de comprobaciones de la PR. Si todo va bien, las comprobaciones del proyecto para la aplicación Astro deberían superarse. Puede tardar unos minutos.
9. **Opcional:** Puedes cambiar a esta rama en tu codespace para probar manualmente la función de juegos relacionados. Abre el terminal y ejecuta estos comandos; sustituye `<branch-name>` por el nombre de la rama que creó Copilot, por ejemplo, `copilot/fix-8`:

    ```bash
    git fetch origin
    git checkout <branch-name>
    ```

Copilot ha creado la función de juegos relacionados. Como antes, puedes pedir cambios al agente en la nube de forma iterativa. Por ejemplo, puedes solicitar que ajuste el número de juegos relacionados o que añada encabezados de comentarios y comentarios TSDoc (recuerda que esta tarea se asignó **antes** de actualizar las instrucciones personalizadas). Para ello, añade un comentario nuevo en la pestaña **Conversation**. Copilot lo verá e iniciará otra sesión.

## Revisa las funciones de accesibilidad

Por último, revisa las funciones de accesibilidad implementadas con el agente personalizado de accesibilidad. Esta PR debería incluir el modo de alto contraste que asignaste en el Ejercicio 3 y el modo claro que solicitaste desde el centro de control en el Ejercicio 4.

1. Vuelve a tu repositorio en GitHub.com.
2. Selecciona la pestaña **Pull Requests**.
3. Selecciona la PR cuyo título se parezca a **Add high contrast mode to website** o que tenga una descripción más detallada.

> [!NOTE]
> Si Copilot aún está trabajando, la PR tendrá la etiqueta **[WIP]**. En ese caso, espera a que termine. Puede tardar unos minutos.

4. Selecciona la pestaña **Files changed** para revisar el código generado.
5. Revisa la implementación y presta especial atención a:
   - Los componentes de la interfaz para cambiar entre los modos.
   - El uso del almacenamiento local para conservar las preferencias.
   - Los cambios de hojas de estilo en cascada (CSS) o de estilo para los modos de alto contraste y claro.
   - Los atributos de Accessible Rich Internet Applications (ARIA), la navegación con el teclado y otros aspectos de accesibilidad.
   - El código JavaScript o TypeScript que controla el cambio de modo.
6. Cuando hayas revisado los cambios y estés conforme, vuelve a la pestaña **Conversation** y desplázate hacia abajo.
7. Busca un indicador que señale que hay flujos de trabajo pendientes de aprobación.
8. Si hay flujos pendientes, selecciona **Approve and run workflows**.

   ![Botón Approve and run workflows](../../../_images/shared-approve-workflows.png)

9. Los flujos de trabajo deberían aparecer en la sección de comprobaciones de la PR. Si todo va bien, las comprobaciones del proyecto para la aplicación Astro deberían superarse. Puede tardar unos minutos.
10. **Opcional:** Puedes cambiar a esta rama en tu codespace para probar manualmente las funciones de accesibilidad. Abre el terminal y ejecuta estos comandos; sustituye `<branch-name>` por el nombre de la rama que creó Copilot:

    ```bash
    git fetch origin
    git checkout <branch-name>
    ```

    A continuación, inicia la aplicación y prueba los controles de los modos de alto contraste y claro en el navegador. Comprueba que funcionen como se espera y que las preferencias se conserven al volver a cargar la página.

Observa cómo el agente personalizado de accesibilidad ayudó a Copilot a implementar estas funciones siguiendo prácticas recomendadas de accesibilidad. Si detectas algún problema o mejora posible, puedes mencionarlo con **@copilot** en un comentario para pedir cambios, igual que hiciste con las otras PR.

## Ejercicio opcional: sigue delegando

El agente en la nube resulta útil para asignarle tareas reales del backlog mientras tú te ocupas de otras cosas. Para adquirir el hábito, crea más incidencias en tu repositorio y asígnaselas a Copilot. Por ejemplo:

- Crear un formulario para expresar interés en un juego desde su página de detalles.
- Implementar la paginación en la página de la lista de juegos.
- Añadir validación de entradas y gestión de errores a las funciones auxiliares de acceso a datos.

## Resumen

Has completado el entorno del agente en la nube. En estas lecciones:

- **Revisaste los archivos de instrucciones personalizadas del repositorio** para observar su efecto en el trabajo del agente en la nube.
- **Asignaste incidencias al agente en la nube de Copilot** y observaste cómo configuraba el entorno, planificaba y trabajaba de forma asíncrona.
- **Creaste y usaste un agente personalizado** para mejorar la accesibilidad con controles para los modos de alto contraste y claro.
- **Usaste la página de agentes de Copilot como centro de control** para supervisar y guiar la sesión de accesibilidad mientras estaba en curso.
- **Revisaste e iteraste sobre las solicitudes de incorporación de cambios del agente en la nube**, mencionaste a `@copilot` para pedir cambios y aprobaste flujos de trabajo.

## Revisión y siguientes pasos

Has completado el entorno del agente en la nube. Si quieres seguir explorando, los otros entornos complementan lo que has practicado:

- 🖥️ **[Entorno de VS Code](../../vscode/)**: explora el modo de agente de Copilot Chat y la integración con MCP directamente desde el entorno de desarrollo integrado (IDE).
- 💻 **[Entorno de CLI](../../cli/)**: entrega dos cambios revisados desde el terminal con los modos Plan y Autopilot, habilidades de agente, un agente personalizado de control de calidad (QA), Playwright MCP, Agent Merge y un puente opcional (`/delegate`) al agente en la nube.

En tu propio repositorio, prueba estas ideas:

- Asigna al agente en la nube una incidencia de refactorización o de cobertura de pruebas.
- Crea un agente personalizado para otro ámbito.
- Configura `copilot-setup-steps.yml` para otra pila tecnológica.

## Recursos

- [GitHub Copilot][github-copilot]
- [Acerca de los agentes de Copilot][copilot-agents]
- [Asignar incidencias de GitHub a Copilot][assign-issue]
- [Prácticas recomendadas para el flujo de trabajo de configuración del agente en la nube][cloud-agent-best-practices]
- [Configurar el firewall del agente en la nube de Copilot][agent-firewall]

---

| [← Lección anterior: Administración de agentes][previous-lesson] |
|:--|

[github-copilot]: https://github.com/features/copilot
[cloud-agent-overview]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[setup-workflow]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall

[previous-lesson]: ../4-managing-agents/
