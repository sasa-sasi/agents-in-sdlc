---
title: "Ejercicio 5: Supervisar y administrar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lección anterior: Agentes personalizados][previous-lesson] |
|:--|

Cuando usas el modo de agente de GitHub Copilot, trabaja de forma autónoma: explora el código, propone cambios, edita archivos y ejecuta comandos. Como el trabajo se realiza en tu equipo y en tiempo real, Copilot Chat en VS Code te muestra cada llamada a una herramienta y cada edición de archivo. Puedes revisar las diferencias, aceptar o rechazar cambios concretos y guiar la conversación con prompts de seguimiento para ajustar o ampliar el trabajo sin salir del editor.

En este ejercicio:

- Supervisarás en tiempo real el trabajo del agente de accesibilidad.
- Revisarás y aceptarás las ediciones propuestas.
- Guiarás al agente durante la sesión para que añada un control para el modo claro junto al de alto contraste.

## Escenario

El agente personalizado de accesibilidad que usaste en el [Ejercicio 4][previous-lesson] está implementando el modo de alto contraste. Mientras trabaja, el equipo de diseño ha pedido también un control para el modo claro, destinado a las personas a quienes les resulta demasiado oscuro el tema predeterminado. En lugar de empezar una conversación nueva, ampliarás el trabajo desde la sesión actual.

## Supervisa el progreso de Copilot

La vista Copilot Chat muestra cada paso del agente: los archivos que explora, los comandos que ejecuta y las ediciones que propone. Cada edición aparece en el chat con las diferencias y los controles **Keep** y **Undo**.

1. Vuelve a la vista Copilot Chat del Ejercicio 4.
2. Mientras trabaja el agente, desplázate por el chat para observar las llamadas a herramientas, las lecturas y ediciones de archivos y los comandos de terminal que pide ejecutar.
3. Cuando proponga una edición, aparecerá con las diferencias en el chat:
   - Selecciona **Keep** para aceptar el cambio.
   - Selecciona **Undo** para revertirlo y permitir que el agente vuelva a intentarlo.
4. También puedes abrir el indicador **Files changed** de la parte superior del chat para ver todos los archivos modificados durante la sesión.

> [!NOTE]
> Si una llamada a una herramienta pide permiso —por ejemplo, para ejecutar un comando de terminal—, el agente se detendrá y mostrará una solicitud **Allow**. Aprueba solo los comandos que consideres seguros.

5. Espera a que el agente termine de implementar el modo de alto contraste. Al acabar, debería mostrar un mensaje con un resumen de los cambios.

## Guía al agente para que añada el modo claro

Ahora que está implementado el modo de alto contraste, ampliarás la misma conversación para añadir un control para el modo claro. Como continuarás en la misma sesión, el agente conservará el contexto del trabajo anterior, incluidos los componentes modificados, el enfoque de estilo y el patrón de almacenamiento local.

1. En el campo de Copilot Chat, envía este prompt de seguimiento:

    ```plaintext
    Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
    ```

2. El agente continuará desde donde lo dejó, explorará los cambios realizados y propondrá los cambios necesarios para añadir el modo claro.
3. Revisa cada edición nueva a medida que aparezca, como hiciste con el modo de alto contraste. Usa **Keep** o **Undo** en cada conjunto de diferencias.
4. Si el agente sigue un enfoque que no quieres —por ejemplo, intenta reorganizar los controles de modo de una forma que no te convence—, deténlo con el botón **Stop** junto al campo de chat y envía un mensaje de seguimiento para aclarar lo que necesitas.

> [!TIP]
> Guiar una sesión en curso es más rápido que empezar de nuevo. Puedes enviar prompts de seguimiento para pedir ajustes («simplifica las hojas de estilo en cascada (CSS) y usa variables CSS en lugar de duplicar selectores»), corregir el enfoque («no añadas un tercer control; integra el modo claro en el panel de configuración existente») o ampliar el alcance («añade también métodos abreviados de teclado para ambos controles»).

## Revisa los archivos modificados

Antes de confirmar los cambios, revisa rápidamente todo lo que haya modificado el agente.

1. Abre la vista **Source Control** de VS Code.
2. Revisa la lista completa de archivos modificados. Deberías ver cambios en los componentes Astro, los estilos y las pruebas relacionadas.
3. Abre algunos archivos modificados y revisa las diferencias. Confirma que se sigan las pautas de accesibilidad del agente personalizado: atributos de Accessible Rich Internet Applications (ARIA), navegación con el teclado, lenguaje de marcado de hipertexto (HTML) semántico y persistencia mediante almacenamiento local.
4. Cuando estés conforme, prepara y confirma los cambios desde el panel Source Control. Los publicarás en [la siguiente lección][next-lesson].

## Resumen y siguientes pasos

Has usado el modo de agente de Copilot Chat para supervisar y guiar una sesión en curso: has revisado las ediciones a medida que aparecían, las has aceptado o rechazado y has enviado prompts de seguimiento para ampliar el trabajo sin perder el contexto.

En este ejercicio:

- Has supervisado en tiempo real el trabajo de un agente.
- Has aceptado y rechazado ediciones de archivos concretas.
- Has guiado una sesión en curso con prompts de seguimiento.

En la [siguiente lección][next-lesson] publicarás el trabajo de accesibilidad en una solicitud de incorporación de cambios y revisarás los cambios realizados por el agente personalizado local durante el taller.

## Recursos

- [Copilot Chat en VS Code][copilot-chat-vscode]
- [Usar el modo de agente][agent-mode]

---

| [← Lección anterior: Agentes personalizados][previous-lesson] | [Siguiente lección: Iterar sobre el trabajo de Copilot →][next-lesson] |
|:--|--:|

[previous-lesson]: ../4-custom-agents/
[next-lesson]: ../6-iterating/
[copilot-chat-vscode]: https://code.visualstudio.com/docs/copilot/chat/copilot-chat
[agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
