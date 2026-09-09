---
type: concept
title: "Login"
status: established
aliases:
  - "Pantalla Login"
  - "Ingreso"
related_concepts:
  - "../concepts/flujo-estudiante.md"
  - "../concepts/flujo-profesor.md"
  - "../concepts/tipo-usuario.md"
domains:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
---

# Login

## Definición

`Login` es la pantalla de entrada común del MVP Avatar USACH Virtual: el usuario ve un formulario institucional, escribe correo y contraseña, pulsa `Ingresar` y, si la autenticación y el rol lo permiten, entra al [flujo profesor](flujo-profesor.md) o al [flujo estudiante](flujo-estudiante.md).

## Alcance y límites

Cubre el shell visual (`001_Login.png`), la captura de `email`/`password` y la navegación post-ingreso. No cubre registro, recuperación de contraseña, MFA ni proveedor institucional de identidad. El mecanismo de autenticación (simulado, tablas `usuarios` o JWT/PostgreSQL) no está unificado en las fuentes. La referencia visual no está ingerida.

## Explicación

El título visible es `Avatar de Apoyo Educativo`, con identidad [USACH Virtual](../organizations/usach-virtual.md). Tras un ingreso exitoso, `PROFESOR` va a `CargarMaterialClase` y `ESTUDIANTE` a `HistorialClases`. HC-07 y HT-06 vuelven a esta pantalla con `Salir`.

## Relaciones

- Destinos: [HistorialClases](historial-clases.md); `CargarMaterialClase` (nombrada, no especificada).
- El rol lo define [tipo de usuario](tipo-usuario.md).
- Slices LOGIN-01 a LOGIN-06: en el pack, [`wiki/requirements/`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/).

## Aplicaciones en Atlas

- Requisito padre: [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)
- [Ingresar al sistema desde Login](../processes/ingresar-al-sistema-desde-login.md)
- [Alcance de la iteración Login](../decisions/alcance-iteracion-login.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E11, E12, E13
