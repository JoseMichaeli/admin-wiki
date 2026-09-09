---
type: concept
title: "Tipo de usuario"
status: contested
aliases:
  - "tipoUsuario"
  - "rol real"
  - "tipo_usuario"
related_concepts:
  - "../concepts/login.md"
  - "../concepts/flujo-estudiante.md"
  - "../concepts/flujo-profesor.md"
domains:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# Tipo de usuario

## Definición

En el pack de Login, el tipo de usuario es el discriminante de rol que el sistema obtiene al autenticar y que decide la pantalla siguiente: `PROFESOR` o `ESTUDIANTE`.

## Alcance y límites

Aplica al ingreso. No define un modelo de permisos ni autorización avanzada. El origen del valor y el contrato JSON no están unificados. Estado `contested` por divergencia de nombres y de fuentes de verdad, no por debate de producto.

## Explicación

Modelo que las fuentes hacen operativo:

| Origen | Campos o valores |
| --- | --- |
| Tabla `tipo_usuario` (anexo y LOGIN-03) | `nombre` = `PROFESOR` o `ESTUDIANTE`; `usuarios.tipo_usuario_id` |
| JSON demo LOGIN-03 | `tipoUsuario` |
| Criterios LOGIN-03 | `userId` (frente a `idUsuario` en el JSON) |
| Anexo API | `tipo_usuario`, `user_id`, `persona_id`, `nombre_completo`; request con `username` |

El anexo prohíbe fijar el rol por variable de entorno o usuario ficticio. LOGIN-03 incluye usuarios demo.

## Interpretaciones

- El maestro (HU) y LOGIN-04 tratan el rol como dato real retornado por el login.
- LOGIN-01 reserva un «estado o configuración para rol real» ya en el render.
- El anexo exige leerlo de PostgreSQL (`tipo_usuario.nombre`).
- LOGIN-03 criterios niegan validación real de credenciales, lo que deja el rol sin una fuente de verdad única.

## Relaciones

- Gobierna [flujo profesor](flujo-profesor.md) y [flujo estudiante](flujo-estudiante.md).
- Lo produce el slice LOGIN-03 del pack.

## Aplicaciones en Atlas

- [Login](login.md)
- [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)
- [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E11, E13, E17
