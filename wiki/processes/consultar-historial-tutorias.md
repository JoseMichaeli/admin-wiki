---
type: process
title: "Consultar historial de tutorías"
status: draft
owners:
  - unknown
version: "draft-1"
created: 2026-09-08
updated: 2026-09-08
organizations:
  - "../organizations/usach-virtual.md"
---

# Consultar historial de tutorías

## Propósito

Describir el recorrido del estudiante desde `HistorialClases` hacia `HistorialTutorias`, la apertura de `Avatar` desde una fila, el retorno a clases y la salida a `Login`.

## Alcance

Flujo de la iteración documentada en el pack. Empieza en `HistorialClases` (opción de menú) y termina en `Avatar`, de vuelta en `HistorialClases` o en `Login`. No incluye conversación real ni persistencia. Estado `draft` porque `Avatar` no está especificado y HT-02 no resuelve mock frente a GET real.

## Entradas y condiciones previas

- Estudiante autenticado de forma simulada, ya en el flujo estudiante.
- Shell de `HistorialTutorias` disponible según el mockup `004_HistorialTutorias.png`.
- Lista de tutorías mock o respuesta del GET de HT-02, según la resolución de alcance.

## Roles y responsabilidades

| Rol | Responsabilidad |
| --- | --- |
| Estudiante | Abre el historial, elige una tutoría o navega a clases o login. |
| Sistema (frontend) | Renderiza, carga la lista, muestra vacío si aplica, navega con estado temporal. |
| API de tutorías | Según HT-02, devuelve tutorías del `usuario_id` con clases relacionadas y título generado; su uso en esta iteración está en conflicto de alcance. |

## Procedimiento

1. **Estudiante:** Desde `HistorialClases`, elige `Historial de tutorías` en el menú. Resultado: el sistema navega a `HistorialTutorias`.
2. **Sistema:** Renderiza el shell según `004_HistorialTutorias.png` (menú, `USACH Virtual`, `Salir`, título).
3. **Sistema:** Carga tutorías. Si hay filas, las muestra con fecha, resumen y acción de chat (y título generado, si aplica). Si la lista está vacía, muestra «No hay tutorías registradas» y conserva menú y encabezado.
4. **Estudiante:** Pulsa el ícono o botón de chat de una fila. Resultado: navega a `Avatar` con estado temporal y origen `HistorialTutorias`.
5. **Estudiante (rama):** Desde el menú, vuelve a `HistorialClases`. No es obligatorio preservar la selección de contenidos previa.
6. **Estudiante (rama):** `Salir` → `Login`, con limpieza de sesión simulada si aplica.
7. **Estudiante (regreso):** HT-04 deja el origen disponible para volver a `HistorialTutorias` desde `Avatar` si aplica. Cómo se implementa ese retorno no está especificado.

## Salidas y condición de finalización

- Tutoría abierta: pantalla `Avatar` con conocimiento temporal de la sesión.
- Retorno a estudio: pantalla `HistorialClases`.
- Salida: pantalla `Login` sin permanecer en `HistorialTutorias`.

## Controles y excepciones

- Lista vacía: mensaje de HT-08; navegaciones a clases y login siguen disponibles.
- Sin conversación persistida: la navegación a `Avatar` no debe fallar.
- Backend ausente: la UI no se bloquea; se usan mocks, salvo que se resuelva implementar el GET.

## Relaciones

- [Pantalla HistorialTutorias del flujo estudiante](../requirements/historial-tutorias-pantalla.md)
- [Flujo estudiante](../concepts/flujo-estudiante.md)
- Complementa [Iniciar estudio desde HistorialClases](iniciar-estudio-desde-historial-clases.md)
- Versión más detallada en el pack: [`wiki/processes/consultar-historial-tutorias.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/processes/consultar-historial-tutorias.md)

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E3, E5, E7
