---
type: concept
title: "Flujo estudiante"
status: established
aliases:
  - "Flujo del estudiante"
related_concepts:
  - "../concepts/login.md"
  - "../concepts/historial-clases.md"
  - "../concepts/historial-tutorias.md"
  - "../concepts/flujo-profesor.md"
domains:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# Flujo estudiante

## Definición

El flujo estudiante es la secuencia que recorre un usuario con tipo `ESTUDIANTE` tras [Login](login.md): `Login` → `HistorialClases` → `Avatar`, con rama `HistorialClases` ↔ `HistorialTutorias` → `Avatar`, y salida a `Login` mediante `Salir`. El pack de Login especifica la puerta de entrada; HC y HT especifican el resto.

## Alcance y límites

Describe navegación y consistencia visual del estudiante. El [flujo profesor](flujo-profesor.md) es el otro destino de Login. `Avatar` sigue sin pack. La autenticación (simulada vs JWT/PostgreSQL) está en conflicto en el pack Login. Las tutorías son mock según el maestro HT, con GET real pedido por HT-02.

## Explicación

`HistorialClases` es el hub: desde ahí se inicia estudio, se visita el historial de tutorías o se sale. Desde `HistorialTutorias` se reabre `Avatar` por el ícono de chat, se vuelve a clases o se sale. La identidad `USACH Virtual` y el menú lateral deben sentirse continuos. SPEC-HC-10 añade el retorno al historial después de `Avatar`; HT-04 registra el origen `HistorialTutorias` para el mismo fin. Cómo se implementa ese retorno no está especificado.

## Relaciones

- [Login](login.md): puerta de entrada cuando el tipo es `ESTUDIANTE`.
- [HistorialClases](historial-clases.md): pantalla central del flujo.
- [HistorialTutorias](historial-tutorias.md): rama de historial de sesiones.
- [USACH Virtual](../organizations/usach-virtual.md): identidad de encabezado.

## Aplicaciones en Atlas

- [Ingresar al sistema desde Login](../processes/ingresar-al-sistema-desde-login.md)
- [Iniciar estudio desde HistorialClases](../processes/iniciar-estudio-desde-historial-clases.md)
- [Consultar historial de tutorías](../processes/consultar-historial-tutorias.md)
- [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E3, E11
