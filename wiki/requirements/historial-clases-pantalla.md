---
type: requirement
title: "Pantalla HistorialClases del flujo estudiante"
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

# Pantalla HistorialClases del flujo estudiante

## Enunciado

El estudiante, tras ingresar al sistema, debe poder usar `HistorialClases` como punto de entrada para ver contenidos de clase, seleccionar uno o más, iniciar estudio en `Avatar` cuando haya selección, acceder a `HistorialTutorias` y salir a `Login`.

## Justificación

El documento maestro del pack presenta esta pantalla como el punto de entrada principal después del login y como el lugar donde el estudiante elige el material a estudiar con el avatar. Las historias HU-HC-01 a HU-HC-05 descomponen esa necesidad.

## Alcance

Aplica al flujo estudiante de [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md) en la iteración de [HistorialClases](../concepts/historial-clases.md). Los slices HC-01 a HC-10 existen en el pack y no se duplican aquí. Queda fuera lo definido en el [alcance de la iteración](../decisions/alcance-iteracion-historial-clases.md).

## Criterios de aceptación

- [ ] Dado un ingreso correcto, al abrir `HistorialClases` el estudiante ve la estructura del mockup `003_HistorialClases.png`.
- [ ] Puede ver contenidos disponibles (o mock) con título, fecha y descripción, o el estado vacío definido.
- [ ] Puede marcar y desmarcar uno o más contenidos; `Estudiemos` solo se habilita con selección.
- [ ] El clic en `Estudiemos` navega a `Avatar` con la selección temporal.
- [ ] El menú lleva a `HistorialTutorias` sin consultar tutorías reales.
- [ ] `Salir` regresa a `Login` y no deja al estudiante en una pantalla protegida.

## Verificación

Recorrido de punta a punta descrito en SPEC-HC-10 del pack, más inspección visual contra el mockup. Automatización no definida en las fuentes. El guion E2E del pack omite el dropdown de curso exigido por HC-01.

## Dependencias y relaciones

- Hijos funcionales (en el pack, no compilados como páginas propias): SPEC-HC-01 a SPEC-HC-10 en [`wiki/requirements/`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/).
- Acotado por [Alcance de la iteración HistorialClases](../decisions/alcance-iteracion-historial-clases.md).
- Ejecución estudiante: [Iniciar estudio desde HistorialClases](../processes/iniciar-estudio-desde-historial-clases.md).
- Conflictos de estado inicial y de GET de documentos: [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E2, E3, E4, E6
