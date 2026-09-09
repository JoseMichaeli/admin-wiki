---
type: decision
title: "Alcance de la iteración HistorialClases"
status: accepted
decided: unknown
decision_makers:
  - unknown
projects:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
scope:
  - "../requirements/historial-clases-pantalla.md"
---

# Alcance de la iteración HistorialClases

## Decisión

En la iteración documentada por el pack `05_historial_clases` y SPEC-HC-01 a SPEC-HC-10, `HistorialClases` se implementa como pantalla funcional del flujo estudiante con datos mock o APIs de listado, selección temporal y navegación. Queda fuera de la iteración la carga real de contexto académico hacia el avatar, RAG, vectorización, persistencia de la selección, creación de tutoría real, integración real con LLM, analítica de uso y reglas avanzadas de permisos académicos.

El mockup `003_HistorialClases.png` es referencia visual obligatoria. Los mocks se usan solo donde el pack lo permite, y la pantalla debe quedar preparada para sustituirlos.

El estado `accepted` representa que el pack lo formula como instrucción de implementación para Harness, no que exista un acta de aprobación nominada. `decided` permanece `unknown`.

## Contexto

`HistorialClases` es el punto de entrada post-login. Harness debe construirla por vertical slices verificables. Varios slices permiten funcionar sin datos reales de profesor, tutorías o sesión institucional.

## Opciones consideradas

Las fuentes no enumeran alternativas formales. Documentan el curso elegido (iteración limitada, mocks permitidos, sin RAG) frente a capacidades explícitamente aplazadas.

### Iteración limitada con mocks y navegación

- Ventajas declaradas: permite construir y validar la pantalla; no bloquea si falta integración del profesor; deja la lista sustituible.
- Costos y riesgos: el estudiante no obtiene aún estudio con contexto real; hay tensión con el GET de documentos de SPEC-HC-05.

### Capacidades aplazadas

- Ventajas declaradas: evitan implementar RAG, vectorización, LLM, analítica y permisos avanzados en esta pantalla.
- Costos y riesgos: no documentados como evaluación comparativa.

## Razones

El maestro exige no implementar RAG ni carga real de contexto en esta pantalla, usar mocks solo donde el documento lo permite, e implementar slices pequeños y verificables.

## Consecuencias

- La implementación puede (y en varios slices debe) operar con datos mock.
- `Estudiemos` navega a `Avatar` con selección temporal; Avatar no recibe todavía contexto académico real, según el maestro y los criterios de HC-05 y HC-10.
- SPEC-HC-05 también pide un GET de clases y documentos, incluido `contenido_extraido`. Esa consecuencia está en conflicto con la exclusión de contexto real; ver la [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Relaciones

- Delimita [Pantalla HistorialClases del flujo estudiante](../requirements/historial-clases-pantalla.md).
- Restringe el proceso [Iniciar estudio desde HistorialClases](../processes/iniciar-estudio-desde-historial-clases.md).
- Complementa, sin reemplazar, el [alcance de HistorialTutorias](alcance-iteracion-historial-tutorias.md).

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E4, E6
