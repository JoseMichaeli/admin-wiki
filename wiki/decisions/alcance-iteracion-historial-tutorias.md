---
type: decision
title: "Alcance de la iteración HistorialTutorias"
status: accepted
decided: unknown
decision_makers:
  - unknown
projects:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
scope:
  - "../requirements/historial-tutorias-pantalla.md"
---

# Alcance de la iteración HistorialTutorias

## Decisión

En la iteración documentada por el pack `06_historial_tutorias` y SPEC-HT-01 a SPEC-HT-08, `HistorialTutorias` se implementa como pantalla funcional del flujo estudiante: historial visible, navegación real a `Avatar`, retorno a `HistorialClases` y salida a `Login`. Quedan fuera la consulta de conversaciones reales, la persistencia de tutorías nuevas, la carga de mensajes históricos reales, la analítica de tutorías y la integración de LLM, RAG, STT, TTS o LiveAvatar desde esta pantalla.

El mockup `004_HistorialTutorias.png` es referencia visual obligatoria. Los mocks se usan donde el maestro lo permite, y la pantalla debe quedar preparada para sustituir el listado mock por tutorías reales.

El estado `accepted` representa que el pack lo formula como instrucción de implementación para Harness, no que exista un acta de aprobación nominada. `decided` permanece `unknown`.

## Contexto

`HistorialTutorias` es la rama del [flujo estudiante](../concepts/flujo-estudiante.md) que se abre desde `HistorialClases`. El maestro declara historial mock y prohíbe consulta real a base de datos. SPEC-HT-02, en el mismo pack, pide un GET sobre `tutorias` y `clase_tutoria`. Esa tensión no está resuelta.

## Opciones consideradas

Las fuentes no enumeran alternativas formales. Documentan el curso elegido (iteración limitada, mocks permitidos, navegación real a Avatar) frente a capacidades explícitamente aplazadas.

### Iteración limitada con mocks y navegación

- Ventajas declaradas: permite construir y validar la pantalla; no bloquea si falta backend; deja el listado sustituible.
- Costos y riesgos: el estudiante no retoma una conversación real; hay tensión con el GET de HT-02 y con el envío de clases relacionadas de HT-04.

### Capacidades aplazadas

- Ventajas declaradas: evitan persistencia, mensajes reales, analítica e integración de LLM/RAG/STT/TTS/LiveAvatar en esta pantalla.
- Costos y riesgos: no documentados como evaluación comparativa.

## Razones

El maestro exige no consultar tutorías reales, no persistir conversaciones, no cargar mensajes históricos reales y no integrar LLM ni RAG desde esta pantalla.

## Consecuencias

- La implementación puede (y según el maestro debe) operar con datos mock.
- El ícono de chat navega a `Avatar` con estado temporal; no se carga conversación persistida.
- SPEC-HT-02 también pide un GET filtrado por `usuario_id` y un título generado desde `clase_tutoria`. Esa consecuencia está en conflicto con la exclusión de consulta real; ver la [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Relaciones

- Delimita [Pantalla HistorialTutorias del flujo estudiante](../requirements/historial-tutorias-pantalla.md).
- Restringe el proceso [Consultar historial de tutorías](../processes/consultar-historial-tutorias.md).
- Complementa, sin reemplazar, el [alcance de HistorialClases](alcance-iteracion-historial-clases.md).

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E5, E7
