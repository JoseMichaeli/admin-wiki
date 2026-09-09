---
type: concept
title: "Flujo profesor"
status: draft
aliases:
  - "Flujo del profesor"
related_concepts:
  - "../concepts/login.md"
  - "../concepts/flujo-estudiante.md"
  - "../concepts/tipo-usuario.md"
domains:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# Flujo profesor

## Definición

En el pack de Login, el flujo profesor es la secuencia que recorre un usuario con `tipo_usuario.nombre = PROFESOR` tras autenticarse: `Login` → `CargarMaterialClase`.

## Alcance y límites

Solo está documentada la puerta de entrada. `CargarMaterialClase` no tiene pack ingerido. No se describe menú, salida ni relación con el avatar. Estado `draft` porque el resto del flujo docente no está en las fuentes.

## Explicación

El maestro contrapone este flujo al del estudiante (`Login` → `HistorialClases`). LOGIN-04 aplica la regla de redirección. No hay evidencia de otras pantallas profesor en este pack.

## Relaciones

- Parte desde [Login](login.md).
- Contrasta con [flujo estudiante](flujo-estudiante.md).
- El discriminante es [tipo de usuario](tipo-usuario.md).

## Aplicaciones en Atlas

- [Ingresar al sistema desde Login](../processes/ingresar-al-sistema-desde-login.md)
- [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E11, E16
