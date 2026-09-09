---
type: requirement
title: "Pantalla HistorialTutorias del flujo estudiante"
requirement_kind: user
status: proposed
priority: unassigned
owners:
  - unknown
projects:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# Pantalla HistorialTutorias del flujo estudiante

## Enunciado

El estudiante, desde el menú de `HistorialClases`, debe poder usar `HistorialTutorias` para ver un historial de tutorías con fecha, resumen y acción de chat, abrir `Avatar` con información temporal de una tutoría, volver a `HistorialClases` y salir a `Login`.

## Justificación

El documento maestro del pack presenta esta pantalla como la rama del flujo estudiante para identificar conversaciones anteriores y retomarlas. Las historias HU-HT-01 a HU-HT-04 descomponen esa necesidad.

## Alcance

Aplica al flujo estudiante de [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md) en la iteración de [HistorialTutorias](../concepts/historial-tutorias.md). Los slices HT-01 a HT-08 existen en el pack y no se duplican aquí. Queda fuera lo definido en el [alcance de la iteración](../decisions/alcance-iteracion-historial-tutorias.md). No hay slice de validación integral equivalente a HC-10; el cierre se toma de la sección 11 del maestro.

## Criterios de aceptación

- [ ] La pantalla se renderiza según `004_HistorialTutorias.png`: menú, encabezado y título `Historial de tutorías` visibles.
- [ ] Se muestran tutorías (mock o API, según la resolución de HT-02) con fecha, resumen y acción de chat, o el estado vacío definido.
- [ ] El ícono o botón de chat navega a `Avatar` con estado temporal; no se carga conversación real persistida.
- [ ] El menú permite volver a `HistorialClases`.
- [ ] `Salir` regresa a `Login` y no deja al estudiante en una pantalla protegida.
- [ ] Los datos de listado están organizados para ser reemplazados por API real después.

## Verificación

Recorrido de las rutas del maestro (llegada desde HistorialClases; ida a Avatar, HistorialClases y Login) más inspección visual contra el mockup. Automatización no definida. No existe SPEC de validación E2E en este pack.

## Dependencias y relaciones

- Hijos funcionales (en el pack, no compilados como páginas propias): SPEC-HT-01 a SPEC-HT-08 en [`wiki/requirements/`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/).
- Acotado por [Alcance de la iteración HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md).
- Llegada desde [HistorialClases](../concepts/historial-clases.md) (slice HC-06 en el pack).
- Ejecución estudiante: [Consultar historial de tutorías](../processes/consultar-historial-tutorias.md).
- Conflictos mock/GET y contrato hacia Avatar: [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E2, E3, E5, E7
