---
type: decision
title: "Alcance de la iteración Login"
status: accepted
decided: unknown
decision_makers:
  - unknown
projects:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
created: 2026-09-08
updated: 2026-09-08
scope:
  - "../requirements/login-pantalla.md"
---

# Alcance de la iteración Login

## Decisión

En la iteración documentada por `03_login` y SPEC-LOGIN-01 a SPEC-LOGIN-06, `Login` se implementa como punto de entrada común: UI según `001_Login.png`, captura de correo y contraseña, determinación de rol y redirección a `CargarMaterialClase` o `HistorialClases`. Quedan fuera recuperación de contraseña, registro, MFA, autorización avanzada y autenticación institucional con proveedor de identidad.

El pack no unifica si esta iteración valida credenciales de verdad. El cuerpo del maestro (secciones 4 y 5) y los criterios de LOGIN-03 excluyen o niegan validación real. El anexo y partes de LOGIN-03/05 exigen PostgreSQL, JWT, 401 y prohibición de mocks. El estado `accepted` registra que el pack instruye a Harness; no hay acta nominada. `decided` permanece `unknown`.

## Contexto

`Login` abre los dos flujos del MVP. Los packs HC y HT trataban el login como simulado. Este pack nombra autenticación real y, en el anexo, la vuelve obligatoria contra base de datos.

## Opciones consideradas

Las fuentes no enumeran alternativas formales. Documentan a la vez un curso limitado (sin IdP, con preparación futura) y un curso de implementación obligatoria con BD real.

### Iteración limitada, validación no real

- Ventajas declaradas: permite construir UI y redirección; excluye IdP, MFA y gestión avanzada de sesión.
- Costos y riesgos: choca con el anexo y con HU-LOGIN-01/02.

### Autenticación obligatoria contra PostgreSQL y JWT

- Ventajas declaradas: rol desde `tipo_usuario`; sin mocks ni seeds; error 401.
- Costos y riesgos: no evaluados frente a la exclusión de «validación real de credenciales».

## Razones

El maestro pide slices verificables, fidelidad a `001_Login.png` y preparación para sustituir el mecanismo. El anexo añade reglas «obligatorias» de datos y API. Ambas están en el mismo documento.

## Consecuencias

- La UI y la redirección por rol son exigibles con independencia del mecanismo de auth.
- Implementar solo sesión simulada incumple el anexo; implementar JWT/PostgreSQL incumple la sección 5 y los criterios de LOGIN-03 que niegan validación real.
- HC-07 y HT-06 siguen describiendo logout simulado; el anexo prohíbe sesiones simuladas.
- Ver la [síntesis del pack](../syntheses/pack-llm-wiki-historial-clases.md).

## Relaciones

- Delimita [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md) y LOGIN-01 a LOGIN-06 (en el pack).
- Complementa, y en sesión contradice, los alcances de [HistorialClases](alcance-iteracion-historial-clases.md) e [HistorialTutorias](alcance-iteracion-historial-tutorias.md).

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E12, E13, E15
