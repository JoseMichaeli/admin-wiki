---
type: concept
title: "HistorialTutorias"
status: established
aliases:
  - "Historial de tutorías"
  - "Pantalla HistorialTutorias"
broader_concepts:
  - "../concepts/flujo-estudiante.md"
related_concepts:
  - "../concepts/historial-clases.md"
domains:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# HistorialTutorias

## Definición

`HistorialTutorias` es la pantalla del [flujo estudiante](flujo-estudiante.md) donde el alumno ve un historial de tutorías —mock o consultadas según el slice— y puede abrir `Avatar` desde el ícono o botón de chat de una fila, volver a `HistorialClases` o salir a `Login`.

## Alcance y límites

Incluye el shell (menú lateral, identidad `Avatar`, encabezado `USACH Virtual`, `Salir`, título `Historial de tutorías`, texto descriptivo, tabla o listado, acción `Ver` o chat). No es `HistorialClases`, ni `Avatar`, ni `Login`. En esta iteración no persiste conversaciones ni crea tutorías nuevas. La referencia visual obligatoria es `004_HistorialTutorias.png`, no ingerida.

## Explicación

El estudiante llega desde `HistorialClases`. El área principal lista tutorías con fecha, resumen y acción de chat; HT-02 y HT-03 añaden un título generado a partir de las clases asociadas. El clic en chat navega a `Avatar` con estado temporal y origen `HistorialTutorias`. El menú permite volver a clases; `Salir` vuelve al login. Si no hay filas, se muestra «No hay tutorías registradas». HT-02 también exige que la pantalla no aparezca vacía; esa tensión permanece abierta.

## Relaciones

- [Flujo estudiante](flujo-estudiante.md): rama alternativa del hub `HistorialClases`.
- [HistorialClases](historial-clases.md): origen y destino de retorno.
- [Login](login.md): destino de `Salir`.
- Destino nombrado y no especificado: `Avatar`.

## Aplicaciones en Atlas

- Requisito padre: [Pantalla HistorialTutorias del flujo estudiante](../requirements/historial-tutorias-pantalla.md)
- Proceso: [Consultar historial de tutorías](../processes/consultar-historial-tutorias.md)
- Decisión: [Alcance de la iteración HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md)
- Slices HT-01 a HT-08: en el pack, [`wiki/requirements/`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E2, E3, E5, E7
