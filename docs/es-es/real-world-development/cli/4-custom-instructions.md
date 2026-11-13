---
title: "Lección 4: Guía a Copilot con instrucciones personalizadas"
description: "Explora las instrucciones del repositorio, añade un estándar de documentación y aplícalo al código de filtrado."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

El contexto es fundamental cuando trabajas con inteligencia artificial generativa. Si una tarea debe realizarse de una manera concreta, asegúrate de que Copilot pueda acceder a las indicaciones pertinentes. Los [archivos de instrucciones][instruction-files] describen no solo *qué* código quieres, sino también *cómo* debe estructurarse. Ahora que ya has creado el filtrado, explorarás las instrucciones que ha usado Copilot, añadirás un estándar de documentación y lo aplicarás al código.

En esta lección:

- Explorarás cómo llegan al agente las instrucciones del repositorio y los archivos de instrucciones asociados a rutas.
- Actualizarás el archivo de instrucciones para que se sigan los estándares de programación.
- Observarás el efecto de los archivos de instrucciones en el código.

## Escenario

Como cualquier empresa de desarrollo, Tailspin Toys tiene pautas y requisitos para sus prácticas de desarrollo. Entre ellos:

- Los comentarios deben explicar la intención y las decisiones que no sean evidentes, no limitarse a repetir el código.
- Las funciones exportadas de `db/` y `src/lib/` deben documentar su propósito, parámetros y valores devueltos mediante TSDoc/JSDoc, incluido el argumento `db` inyectable cuando exista.
- Los componentes reutilizables de Astro deben documentar sus contratos `Props`, y los comentarios deben mantenerse actualizados cuando cambie el código relacionado.
- Se deben conservar las pautas de formato y lint existentes.

Con los archivos de instrucciones, proporcionarás a Copilot la información necesaria para que realice las tareas de acuerdo con estas prácticas.

## Archivos de instrucciones

Las instrucciones personalizadas proporcionan a Copilot contexto y preferencias para que pueda entender mejor tu estilo de programación y tus requisitos. Esta función te permite orientar a Copilot para que genere sugerencias y fragmentos de código más pertinentes. Puedes especificar tus convenciones de programación, bibliotecas e incluso los tipos de comentarios que prefieres. Puedes crear instrucciones para todo el repositorio o para tipos concretos de archivos y tareas.

Hay dos tipos de archivos de instrucciones:

- `.github/copilot-instructions.md` es un único archivo que se envía a Copilot en **todas** las solicitudes del repositorio. Debe contener información general del proyecto que sea pertinente para la mayoría de las solicitudes, como la pila tecnológica, una descripción de lo que se está desarrollando, las prácticas recomendadas y otras indicaciones globales.
- Los archivos `.github/instructions/*.instructions.md` proporcionan pautas para lenguajes, tipos de archivo o tareas concretos.

> [!NOTE]
> La disponibilidad de otros formatos de instrucciones varía según el entorno. Consulta la [referencia sobre los formatos de instrucciones admitidos][custom-instructions-support] antes de depender de uno en concreto.

## Explora los archivos de instrucciones personalizadas del proyecto

El proyecto inicial ya incluye varios archivos de instrucciones. Explóralos antes de hacer cambios para ver el efecto que tienen.

1. Vuelve a tu Codespace.
2. En Copilot CLI, escribe `/exit` para salir de la aplicación.
3. Abre `.github/copilot-instructions.md` en el editor de Codespaces, no en el terminal.
4. Explora el archivo y fíjate en la descripción breve del proyecto y las pautas de programación. Estas instrucciones se aplican a todas las interacciones con Copilot en este repositorio.
5. Abre la carpeta `.github/instructions` y explora los archivos. Hay instrucciones para Astro, la capa de datos de Drizzle, pruebas y otros elementos.
6. Abre `.github/instructions/unit-tests.instructions.md`. Fíjate en el campo `applyTo` de la parte superior, que define un patrón global para los archivos a los que se aplican las instrucciones.
7. Abre `.github/instructions/drizzle.instructions.md` y fíjate en los enlaces a otros archivos de instrucciones y a archivos existentes del proyecto. Así puedes dividir conjuntos grandes de instrucciones en archivos pequeños y reutilizables, y señalar a Copilot ejemplos que debe seguir.

## Actualiza los archivos de instrucciones según las pautas del equipo

Los archivos existentes son un buen punto de partida, pero falta una indicación. Modificarás el archivo principal `copilot-instructions.md` para pedir comentarios TSDoc en el nuevo código TypeScript.

1. En `.github/copilot-instructions.md`, busca la sección **Code formatting guidance**, que debería estar cerca de la línea 35.
2. Añade esta viñeta al final de la sección:

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

El archivo se guardará automáticamente.

## Aplica las instrucciones actualizadas

Copilot CLI carga las instrucciones del repositorio al iniciar una conversación. Después de guardar las instrucciones, sal de la conversación de filtrado y retómala para que Copilot cargue las nuevas indicaciones sin perder el contexto de la funcionalidad.

1. Si la conversación de filtrado sigue abierta, escribe `/exit` para cerrarla. Copilot CLI guarda las conversaciones automáticamente.
2. Desde la raíz del repositorio en la rama `game-filters-cli`, retoma la conversación guardada:

   ```bash
   copilot --resume
   ```

   Si se te solicita, selecciona la conversación de filtrado y confirma que está activa la rama `game-filters-cli`.
3. Envía a Copilot este prompt para que aplique las instrucciones actualizadas:

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. Escribe `/diff` y revisa los archivos TypeScript modificados. Observa los nuevos comentarios TSDoc y comprueba que describan el código correctamente.

## Resumen y siguientes pasos

Has explorado cómo usa Copilot CLI el contexto de los archivos de instrucciones y has aplicado un estándar nuevo a la funcionalidad. En concreto:

- Has explorado cómo llegan al agente las instrucciones del repositorio y los archivos de instrucciones asociados a rutas.
- Has actualizado el archivo de instrucciones para que se sigan los estándares de programación.
- Has observado el efecto de los archivos de instrucciones en el código.

A continuación, [personalizarás y ejecutarás la habilidad reutilizable `quality-checks`][next-lesson] para que el lint y las pruebas se ejecuten de forma coherente.

## Recursos

- [Añadir instrucciones personalizadas para Copilot CLI][instruction-files]
- [Compatibilidad con instrucciones personalizadas][custom-instructions-support]
- [Prácticas recomendadas para crear instrucciones personalizadas][instructions-best-practices]
- [Awesome Copilot: colección de archivos de instrucciones y otros recursos][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
