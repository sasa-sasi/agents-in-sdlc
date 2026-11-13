---
title: "Lección 8: Crea y combina la solicitud de incorporación de cambios (PR) de la funcionalidad"
description: "Revisa conjuntamente el filtrado, las instrucciones, la actualización de la habilidad quality-checks, el perfil de control de calidad (QA) y las pruebas; después, crea una PR y usa Agent Merge."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

La implementación del filtrado, las instrucciones actualizadas, la habilidad `quality-checks` modificada, el perfil de control de calidad (QA) y las pruebas están en una sola rama. Ahora revisarás los cambios en conjunto y abrirás una solicitud de incorporación de cambios (PR). Tú combinaste la PR de valoraciones por estrellas; esta vez dejarás que **Agent Merge** gestione el proceso.

> [!NOTE]
> En condiciones normales, dividiríamos la funcionalidad, las actualizaciones de instrucciones, los cambios en la habilidad y el agente de QA en varias PR. Para agilizar el taller, has mantenido todo el trabajo de filtrado y calidad en una conversación y una rama, y lo incluirás en esta PR.

En esta lección:

- Aprenderás qué es Agent Merge y cómo automatiza el ciclo de una PR.
- Inspeccionarás el cambio completo de la funcionalidad y las pruebas de verificación.
- Crearás la PR del filtrado.
- Activarás Agent Merge solo después de revisar los cambios y confirmarás que la PR se ha combinado.

## Escenario

Durante el trabajo de filtrado has usado Copilot para planificar, implementar y verificar una funcionalidad. Tailspin Toys quiere automatizar el trabajo pendiente de la PR, pero mantener bajo el control del desarrollador la autorización para combinarla.

## Introducción a Agent Merge

**Agent Merge** automatiza el trabajo restante para integrar una solicitud de incorporación de cambios. Cuando lo activas, Copilot resuelve los impedimentos que bloquean la PR: corrige las comprobaciones de integración continua (CI) que fallan, responde a los comentarios de revisión y, cuando hace falta, vuelve a aplicar los cambios sobre la rama base. Después, habilita la combinación automática de GitHub si la configuración del repositorio lo permite.

Hasta ahora has seleccionado **Merge pull request** manualmente. Agent Merge puede encargarse de ese proceso. Revisa el trabajo y confirma que está listo antes de activarlo.

## Usa Agent Merge para administrar la PR

Ya has creado todo el código. Revísalo, crea la PR y deja que Agent Merge se ocupe del resto.

1. Vuelve a tu Codespace.
2. Abre el diálogo del agente con `/agent`.
3. Selecciona **Default** en la lista de opciones y pulsa <kbd>Enter</kbd>.
4. Crea una PR nueva con el comando `/pr create`.
5. Activa Agent Merge con `/pr agentmerge`.
6. Copilot supervisará el proceso de integración continua de la PR. Cuando todas las comprobaciones se superen, la combinará.
7. Confirma que Copilot muestre un mensaje parecido a `PR #14 was squash-merged successfully.`

> [!IMPORTANT]
> Agent Merge no omite las aprobaciones obligatorias, la protección de ramas, las colas de combinación, la configuración del repositorio ni los permisos que falten. Si el proceso se bloquea, revisa el motivo indicado y, si la configuración del repositorio lo permite, completa manualmente la combinación revisada.

## Resumen y siguientes pasos

Has automatizado varias partes del proceso de desarrollo: la generación de código, las pruebas y la validación, y ahora el flujo de la PR. En esta lección:

- Has aprendido qué es Agent Merge y cómo automatiza el ciclo de una PR.
- Has inspeccionado el cambio completo de la funcionalidad y las pruebas de verificación.
- Has creado la PR del filtrado.
- Has activado Agent Merge solo después de revisar los cambios y has confirmado que la PR se ha combinado.

A continuación, [explorarás otros comandos de barra útiles de Copilot CLI][next-lesson] para el contexto, los modelos, el uso compartido y la delegación opcional al agente en la nube.

## Recursos

- [Administrar solicitudes de incorporación de cambios con Copilot CLI][manage-prs]
- [Referencia de comandos de Copilot CLI][cli-reference]

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
