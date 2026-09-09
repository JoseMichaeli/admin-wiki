---
type: process
title: "Ingresar al sistema desde Login"
status: draft
owners:
  - unknown
version: "draft-1"
created: 2026-09-08
updated: 2026-09-08
organizations:
  - "../organizations/usach-virtual.md"
---

# Ingresar al sistema desde Login

## Propósito

Describir el recorrido desde que el usuario abre `Login` hasta que entra a `CargarMaterialClase` o `HistorialClases`, o permanece en Login si la validación falla.

## Alcance

Flujo de la iteración documentada en el pack. Empieza al abrir `Login` y termina en una de las dos pantallas destino o de nuevo en Login. Estado `draft` porque el mecanismo de autenticación no está unificado y `CargarMaterialClase` no está especificada.

## Entradas y condiciones previas

- Pantalla `Login` disponible según `001_Login.png`.
- Credenciales que el usuario va a escribir.
- Según el anexo: tablas `personas`, `usuarios`, `tipo_usuario` y endpoint `POST /api/v1/auth/login`. Según LOGIN-03: servicio real o simulado de Harness.

## Roles y responsabilidades

| Rol | Responsabilidad |
| --- | --- |
| Usuario | Escribe correo y contraseña, pulsa `Ingresar`. |
| Sistema (frontend) | Renderiza, captura, valida mínimo, llama al servicio, redirige o muestra error. |
| Servicio de autenticación | Valida (o no) credenciales y retorna usuario con tipo. |

## Procedimiento

1. **Usuario:** Abre `Login`. Resultado: formulario según la referencia visual.
2. **Usuario:** Escribe correo y contraseña (contraseña oculta).
3. **Sistema (rama vacíos):** Si correo o contraseña faltan, HU-LOGIN-01 y LOGIN-05 impiden avanzar. LOGIN-03 criterios niegan error por vacío. No resuelto.
4. **Usuario:** Pulsa `Ingresar`.
5. **Sistema:** Ejecuta autenticación. Éxito: usuario con tipo. Fallo: mensaje de correo o contraseña erróneos y permanece en Login (HU-LOGIN-02).
6. **Sistema:** Si `PROFESOR` → `CargarMaterialClase`. Si `ESTUDIANTE` → `HistorialClases`.
7. **Usuario (regreso):** Desde historiales, `Salir` vuelve a Login (HC-07, HT-06). Esos slices limpian sesión simulada; el anexo exige JWT.

## Salidas y condición de finalización

- Ingreso profesor: pantalla `CargarMaterialClase`.
- Ingreso estudiante: pantalla `HistorialClases`.
- Fallo: permanece en `Login`.

## Controles y excepciones

- Campos vacíos o correo mal formado: LOGIN-05.
- Credenciales inválidas: 401 en el anexo; mensaje en HU-LOGIN-02.
- Tipo de usuario distinto de los dos documentados: no definido.

## Relaciones

- [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)
- Continúa en [Iniciar estudio desde HistorialClases](iniciar-estudio-desde-historial-clases.md) si el rol es estudiante.
- Versión más detallada en el pack: [`wiki/processes/ingresar-al-sistema-desde-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/processes/ingresar-al-sistema-desde-login.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E11, E13, E14, E15
