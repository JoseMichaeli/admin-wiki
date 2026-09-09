---
type: process
title: "Iniciar estudio desde HistorialClases"
status: draft
owners:
  - unknown
version: "draft-1"
created: 2026-09-08
updated: 2026-09-08
organizations:
  - "../organizations/usach-virtual.md"
---

# Iniciar estudio desde HistorialClases

## Propósito

Describir el recorrido del estudiante desde el login simulado hasta iniciar `Avatar` con contenidos seleccionados, incluyendo las ramas a tutorías y salida.

## Alcance

Flujo de la iteración documentada en el pack. Empieza en [Login](../concepts/login.md) y termina en `Avatar`, `HistorialTutorias` o de vuelta en `Login`. No incluye RAG ni contexto académico real. Estado `draft` porque `Avatar` no está especificada, el mecanismo de autenticación de Login no está unificado y hay tensiones entre HC-01 y HC-10. El interior de `HistorialTutorias` se describe en [Consultar historial de tutorías](consultar-historial-tutorias.md).

## Entradas y condiciones previas

- Estudiante autenticado de forma simulada.
- Cursos asociados vía `curso_alumno`, o mock equivalente.
- Mockup y shell de `HistorialClases` disponibles.

## Roles y responsabilidades

| Rol | Responsabilidad |
| --- | --- |
| Estudiante | Selecciona curso y contenidos, inicia estudio, navega a tutorías o sale. |
| Sistema (frontend) | Renderiza, carga listas, mantiene selección temporal, habilita `Estudiemos`, navega. |
| API de cursos | Devuelve cursos del usuario conectado. |
| API de clases | Devuelve clases del `curso_id` seleccionado. |
| API de clases y documentos | Según HC-05, devuelve clases seleccionadas con documentos; su uso en esta iteración está en conflicto de alcance. |

## Procedimiento

1. **Estudiante:** Ingresa desde `Login`. Resultado: el sistema navega a `HistorialClases`.
2. **Sistema:** Renderiza el shell según `003_HistorialClases.png`. El área principal no lista clases. `Estudiemos` desactivado. Dropdown en «Seleccione un curso».
3. **Sistema:** Carga cursos del alumno en el dropdown (`nombre_curso` / `id`).
4. **Estudiante:** Elige un curso. Resultado: se solicitan clases por `curso_id`.
5. **Sistema:** Si hay clases, las muestra con fecha, título, `resumen_clase` y checkbox. Si la lista está vacía, muestra «No hay contenidos disponibles para estudiar en este momento.» y deja `Estudiemos` desactivado.
6. **Estudiante:** Marca uno o más checkboxes. Resultado: los ids entran en la lista temporal; `Estudiemos` se activa.
7. **Estudiante (opcional):** Cambia de curso. Resultado: se recarga la lista y se vacía la selección.
8. **Estudiante:** Pulsa `Estudiemos`. Resultado: si hay selección, navega a `Avatar` con el estado temporal; si no, no navega.
9. **Estudiante (rama):** Desde el menú, `Historial de tutorías` → `HistorialTutorias`.
10. **Estudiante (rama):** `Salir` → `Login`, con limpieza de sesión simulada y de selección si aplica.
11. **Estudiante (regreso):** Según HC-10, puede volver posteriormente al historial desde `Avatar`. Cómo se implementa ese retorno no está especificado.

## Salidas y condición de finalización

- Estudio iniciado: pantalla `Avatar` con conocimiento de la selección temporal.
- Rama de tutorías: pantalla `HistorialTutorias`.
- Salida: pantalla `Login` sin permanecer en `HistorialClases`.

## Controles y excepciones

- Sin selección o lista vacía: `Estudiemos` desactivado; no hay navegación a `Avatar`.
- Sin integración de clases del profesor: la UI no se bloquea; se usan mocks.
- Backend o mock vacío: mensaje de HC-09, sin error técnico.
- Logout simulado: opcional si el endpoint existe.

## Relaciones

- [Pantalla HistorialClases del flujo estudiante](../requirements/historial-clases-pantalla.md)
- [Flujo estudiante](../concepts/flujo-estudiante.md)
- Precedido por [Ingresar al sistema desde Login](ingresar-al-sistema-desde-login.md)
- Rama detallada: [Consultar historial de tutorías](consultar-historial-tutorias.md)
- Versión más detallada en el pack: [`wiki/processes/iniciar-estudio-desde-historial-clases.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/processes/iniciar-estudio-desde-historial-clases.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E3, E4, E6
