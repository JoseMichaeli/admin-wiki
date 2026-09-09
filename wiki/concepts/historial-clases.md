---
type: concept
title: "HistorialClases"
status: established
aliases:
  - "Historial de clases"
  - "Pantalla HistorialClases"
broader_concepts:
  - "../concepts/flujo-estudiante.md"
related_concepts:
  - "../concepts/historial-tutorias.md"
  - "../concepts/login.md"
domains:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# HistorialClases

## Definición

`HistorialClases` es la pantalla del [flujo estudiante](flujo-estudiante.md), posterior al `Login`, donde el alumno elige un curso asociado, ve las clases o contenidos de ese curso, selecciona uno o más de forma temporal e inicia el estudio con el avatar mediante el botón `Estudiemos`.

## Alcance y límites

Incluye el shell (menú, identidad `Avatar`, encabezado `USACH Virtual`, `Salir`, título, descripción, tabla, `Estudiemos`, bloque de usuario si el mockup lo contempla) y el dropdown `Curso:`. No es el avatar de tutoría, ni `HistorialTutorias`, ni el `Login`. No persiste la selección ni crea tutorías. La referencia visual obligatoria es `003_HistorialClases.png`, no ingerida.

## Explicación

Al entrar, según SPEC-HC-01, el área principal no lista clases hasta que hay un curso elegido. Elegido el curso, se cargan filas con fecha, título, `resumen_clase` y checkbox. La selección vive solo en memoria de la pantalla. `Estudiemos` permanece inerte sin selección. Desde el menú se va a tutorías; desde `Salir`, al login.

SPEC-HC-10 describe un guion E2E que muestra la lista sin elegir curso. Esa tensión permanece abierta; ver [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Relaciones

- [Flujo estudiante](flujo-estudiante.md): pantalla de entrada del flujo.
- Destinos: [HistorialTutorias](historial-tutorias.md); [Login](login.md) (especificado); `Avatar` (nombrado, no especificado).
- Identidad: [USACH Virtual](../organizations/usach-virtual.md).

## Aplicaciones en Atlas

- Requisito padre: [Pantalla HistorialClases del flujo estudiante](../requirements/historial-clases-pantalla.md)
- Proceso: [Iniciar estudio desde HistorialClases](../processes/iniciar-estudio-desde-historial-clases.md)
- Decisión: [Alcance de la iteración HistorialClases](../decisions/alcance-iteracion-historial-clases.md)
- Slices HC-01 a HC-10: en el pack, [`wiki/requirements/`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E1, E3, E4, E6
