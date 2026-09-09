---
type: project
title: "Avatar de Apoyo Educativo USACH Virtual"
status: active
owners:
  - unknown
organizations:
  - "../organizations/usach-virtual.md"
started: unknown
created: 2026-09-08
updated: 2026-09-08
aliases:
  - "Avatar USACH Virtual"
  - "Avatar de Apoyo Educativo"
confidentiality: internal
---

# Avatar de Apoyo Educativo USACH Virtual

## Resumen

Producto de apoyo educativo con avatar. El conocimiento compilado en Atlas-Wiki a 2026-09-08 proviene del pack [llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) (commit `81c6fe5`) y cubre [Login](../concepts/login.md) como puerta común, [HistorialClases](../concepts/historial-clases.md) e [HistorialTutorias](../concepts/historial-tutorias.md) del [flujo estudiante](../concepts/flujo-estudiante.md). El [flujo profesor](../concepts/flujo-profesor.md) solo está documentado en su puerta (`CargarMaterialClase`).

El estado `active` refleja que el pack contiene specs de implementación dirigidas al agente Harness, no que el producto esté en producción. No hay evidencia de fecha de inicio, responsables nominados ni aprobación formal.

## Objetivo

Habilitar que un usuario ingrese por `Login` según su [tipo de usuario](../concepts/tipo-usuario.md), que el estudiante elija material y estudie con el avatar, y que consulte tutorías, sin RAG ni conversaciones persistidas. El mecanismo de autenticación (simulado vs PostgreSQL/JWT) no está unificado.

## Alcance

### Incluye

- Pantalla [Login](../concepts/login.md) y slices SPEC-LOGIN-01 a SPEC-LOGIN-06 (detalle en el pack).
- Pantalla [HistorialClases](../concepts/historial-clases.md) y slices SPEC-HC-01 a SPEC-HC-10 (detalle en el pack).
- Pantalla [HistorialTutorias](../concepts/historial-tutorias.md) y slices SPEC-HT-01 a SPEC-HT-08 (detalle en el pack).
- Selector de cursos, listado de clases, selección temporal y botón `Estudiemos`.
- Listado de tutorías (mock o tablas `tutorias` / `clase_tutoria`, según el conflicto de HT-02).
- Navegación a `Avatar` desde `Estudiemos` o desde el chat de una tutoría; ida y vuelta entre las dos pantallas de historial; salida a `Login`.
- Identidad visual [USACH Virtual](../organizations/usach-virtual.md).

### No incluye

- Carga real de contexto académico hacia el avatar, RAG, vectorización, LLM, analítica de uso y permisos académicos avanzados, según el [alcance de HistorialClases](../decisions/alcance-iteracion-historial-clases.md).
- Persistencia de la selección, creación de tutoría real y conversaciones persistidas, según el [alcance de HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md).
- Recuperación de contraseña, registro, MFA e IdP, según el [alcance de Login](../decisions/alcance-iteracion-login.md).
- Especificación de `Avatar` y de `CargarMaterialClase` (solo se nombran).
- Los archivos gráficos `001_Login.png`, `003_HistorialClases.png` y `004_HistorialTutorias.png`, citados y no ingeridos.

## Estado actual

A 2026-09-08 el submódulo está en el commit `81c6fe5`. En Login permanece abierto si manda el anexo (PostgreSQL/JWT) o el cuerpo que excluye validación real. Siguen abiertos los conflictos ya registrados de HC y HT. El detalle de cada slice se consulta en el árbol del pack.

## Relaciones

### Responsables y participantes

- unknown. El pack se dirige al agente Harness y no nombra personas dueñas del producto.

### Requisitos y decisiones

- [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)
- [Pantalla HistorialClases del flujo estudiante](../requirements/historial-clases-pantalla.md)
- [Pantalla HistorialTutorias del flujo estudiante](../requirements/historial-tutorias-pantalla.md)
- [Alcance de la iteración Login](../decisions/alcance-iteracion-login.md)
- [Alcance de la iteración HistorialClases](../decisions/alcance-iteracion-historial-clases.md)
- [Alcance de la iteración HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md)

### Procesos y proyectos relacionados

- [Ingresar al sistema desde Login](../processes/ingresar-al-sistema-desde-login.md)
- [Iniciar estudio desde HistorialClases](../processes/iniciar-estudio-desde-historial-clases.md)
- [Consultar historial de tutorías](../processes/consultar-historial-tutorias.md)
- [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md)
- Ningún otro proyecto de Atlas está vinculado en las fuentes; no se infiere relación con iniciativas no presentes en el pack.

### Conceptos relevantes

- [Login](../concepts/login.md)
- [Tipo de usuario](../concepts/tipo-usuario.md)
- [Flujo profesor](../concepts/flujo-profesor.md)
- [HistorialClases](../concepts/historial-clases.md)
- [HistorialTutorias](../concepts/historial-tutorias.md)
- [Flujo estudiante](../concepts/flujo-estudiante.md)

## Preguntas abiertas

- ¿Qué bloque de Login manda: anexo (PostgreSQL/JWT), cuerpo (sin validación real) o criterios de LOGIN-03?
- ¿Cuál es el mecanismo vigente en Harness para pasar la selección a `Avatar`?
- ¿El GET de documentos de HC-05 y el GET de tutorías de HT-02 forman parte de esta iteración?
- ¿Dónde están los mockups y los specs de `Avatar` y `CargarMaterialClase`?
- ¿Quiénes son los dueños del producto?

## Fuentes

- [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md), evidencia E1, E2, E10, E11, E12, E13, E16
