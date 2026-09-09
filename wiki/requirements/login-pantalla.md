---
type: requirement
title: "Pantalla Login del MVP Avatar USACH Virtual"
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

# Pantalla Login del MVP Avatar USACH Virtual

## Enunciado

El usuario del MVP debe poder entrar desde `Login` con correo y contraseña, obtener un tipo de usuario y ser redirigido a `CargarMaterialClase` si es `PROFESOR` o a `HistorialClases` si es `ESTUDIANTE`.

## Justificación

HU-LOGIN-01 a HU-LOGIN-03: ingreso, identificación de rol y experiencia institucional. El maestro presenta esta pantalla como punto de entrada común de los dos flujos.

## Alcance

Aplica al MVP de [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md). Los slices LOGIN-01 a LOGIN-06 existen en el pack y no se duplican aquí. Queda fuera lo listado en el [alcance de la iteración](../decisions/alcance-iteracion-login.md), salvo las tensiones del anexo. No hay slice E2E; el cierre es la sección 7 del maestro.

## Criterios de aceptación

- [ ] La pantalla se renderiza según `001_Login.png` con título `Avatar de Apoyo Educativo`, correo, contraseña e `Ingresar`.
- [ ] El usuario puede escribir correo y contraseña; la contraseña no se muestra en claro.
- [ ] `Ingresar` ejecuta autenticación y, si corresponde, redirige por rol.
- [ ] Si la validación falla, el usuario permanece en Login con indicación de error (HU-LOGIN-02).
- [ ] La lógica de autenticación queda encapsulada para sustituirse.

## Verificación

Recorrido del flujo de la sección 6 del maestro más inspección visual contra el mockup. Automatización no definida. El criterio de fallo vs. avance sin validación real está en conflicto (LOGIN-03 vs HU y anexo).

## Dependencias y relaciones

- Hijos funcionales (en el pack, no compilados como páginas propias): LOGIN-01 a LOGIN-06 en [`wiki/requirements/`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/).
- Destino estudiante: [Pantalla HistorialClases del flujo estudiante](historial-clases-pantalla.md).
- Retorno: slices HC-07 y HT-06 en el pack.
- Conflictos de autenticación, vacíos y sesión: [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E11, E12, E13, E14
