---
title: "Lección 1: Instala GitHub Copilot CLI"
description: "Instala y autentica Copilot CLI en tu codespace, conoce sus comandos y encuentra la incidencia de filtrado preparada."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

[GitHub Copilot CLI][about-copilot-cli] es un potente asistente de programación con agentes que se ejecuta en el terminal. Te permite explorar bases de código, generar código, ejecutar comandos e interactuar con herramientas externas desde la línea de comandos. Puedes delegar tareas, solicitar cambios y mantener la concentración. El primer paso, como imaginarás, es instalar la herramienta. Por suerte, puedes hacerlo con herramientas que ya conoces.

En esta lección:

- Instalarás GitHub Copilot CLI con npm.
- Te autenticarás con tu cuenta de GitHub.
- Confiarás en el repositorio del taller y probarás una conversación.
- Encontrarás la incidencia de filtrado mediante el servidor integrado del protocolo de contexto de modelo (MCP) de GitHub.

## Escenario

Tu equipo está empezando a usar agentes de inteligencia artificial para avanzar en un backlog cada vez mayor. Copilot CLI lleva esa capacidad al terminal, donde ya trabajan muchos desarrolladores. En esta lección instalarás y autenticarás la herramienta para poder usarla durante el resto del taller.

## Instala Copilot CLI

Puedes instalar Copilot CLI mediante [npm][install-cli], WinGet o Homebrew. Como GitHub Codespaces ya incluye Node.js, usarás npm.

1. Vuelve a tu codespace y abre un terminal.
2. Comprueba que Node.js esté instalado y cumpla el requisito de versión:

   ```bash
   node --version
   ```

   Deberías ver la versión 24 o posterior.

3. Instala Copilot CLI globalmente:

   ```bash
   npm install -g @github/copilot
   ```

4. Comprueba la instalación:

   ```bash
   copilot --version
   ```

   Deberías ver el número de versión.

## Autentícate con GitHub

La primera vez que se inicia, Copilot CLI te pide que te autentiques con tu cuenta de GitHub.

1. Inicia Copilot CLI:

   ```bash
   copilot
   ```

2. Si se te solicita, sigue las instrucciones del código de dispositivo para autenticarte y autorizar Copilot CLI.
3. Copilot CLI muestra este aviso:

   ```plaintext
   Copilot can read files in this folder and, with your permission, edit them or run code and shell commands. It will remember your permissions for the rest of this session.

   Do you trust the files in this folder?
   ```

4. Comprueba que la ruta corresponda al repositorio de Tailspin Toys y responde que sí seleccionando **Yes, and remember this folder for future sessions**.

> [!NOTE]
> Es posible que ya estés autenticado mediante tu sesión de GitHub en el codespace. Si Copilot CLI se inicia sin pedirte que te autentiques, ya está listo.

## Familiarízate con la herramienta

Los comandos que escribes en el terminal normal se ejecutan directamente en tu codespace. Una vez iniciado Copilot CLI, el lenguaje natural se envía al agente y los comandos de barra controlan la conversación.

1. Escribe `/model`, usa las teclas de dirección para seleccionar **Auto**, pulsa <kbd>Enter</kbd> y vuelve a pulsar <kbd>Enter</kbd> para confirmar.
2. Escribe `/help` para ver los comandos disponibles en la versión instalada y pulsa <kbd>Esc</kbd> para cerrar la ayuda.
3. Haz una pregunta sencilla a Copilot para comprobar que todo funciona:

   ```plaintext
   What are the key files in this project?
   ```

4. Lee la respuesta y observa cómo Copilot explora el repositorio antes de responder.
5. Escribe `/mcp list` y confirma que está disponible el servidor integrado de GitHub para MCP.
6. Pide a Copilot que encuentre la incidencia de filtrado:

   ```plaintext
   Using GitHub MCP, find the issue in this repository titled "Allow users to filter games by category and publisher." Give me its URL and a short summary. Don't change anything.
   ```

7. Abre el enlace y lee la incidencia. La usarás después de completar un primer cambio breve.

> [!TIP]
> Una sesión normal de Copilot CLI trabaja en la rama seleccionada en el terminal; no crea automáticamente un árbol de trabajo. Crearás una rama de funcionalidad antes de cada cambio.

## Usa el acceso directo del taller

Normalmente, Copilot CLI pide permiso antes de usar herramientas fuera de los permisos ya establecidos. En este taller volverás a iniciarlo con `--yolo`, un acceso directo aprobado por ti que elimina esas solicitudes de aprobación en el codespace para que puedas centrarte en los ejercicios.

> [!CAUTION]
> `--yolo` activa permisos automáticos completos (`--allow-all-tools`, `--allow-all-paths` y `--allow-all-urls`). Úsalo solo en un entorno aislado, como un codespace o una máquina virtual (VM), y nunca lo configures como alias predeterminado para el desarrollo diario. Consulta [Permitir y denegar el uso de herramientas][allow-all-warning] para obtener más información.

En este taller, `--enable-all-github-mcp-tools` activa las herramientas de lectura y escritura de GitHub MCP que usarán las lecciones posteriores para trabajar con incidencias y solicitudes de incorporación de cambios. El codespace limita el acceso a tu equipo local, pero los recursos de GitHub autenticados siguen siendo reales. Revisa los cambios antes de publicarlos o combinarlos.

1. Sal de Copilot CLI con `/exit`.
2. Vuelve a iniciarlo desde la raíz del repositorio:

   ```bash
   copilot --yolo --enable-all-github-mcp-tools
   ```

3. Haz otra pregunta breve sobre el proyecto para confirmar que la conversación funciona y, después, sal con `/exit`.

Copilot guarda las conversaciones automáticamente. Más adelante, cuando cambies instrucciones o añadas un agente, usarás `copilot --resume` para volver a la misma conversación de funcionalidad y a la misma rama.

## Resumen y siguientes pasos

En esta lección:

- Instalaste GitHub Copilot CLI con npm.
- Te autenticaste con tu cuenta de GitHub.
- Confiaste en el repositorio del taller y probaste una conversación.
- Encontraste la incidencia de filtrado mediante el servidor integrado de GitHub MCP.

A continuación, [harás tu primer cambio acotado][next-lesson] y usarás Copilot CLI para mostrar una valoración por estrellas en las tarjetas de juegos.

## Recursos

- [Instalar GitHub Copilot CLI][install-cli]
- [Acerca de GitHub Copilot CLI][about-copilot-cli]
- [Referencia de comandos de Copilot CLI][cli-reference]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-add-star-rating/
[install-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[allow-all-warning]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli#allowing-and-denying-tool-use
