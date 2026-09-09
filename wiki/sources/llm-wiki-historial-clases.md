---
type: source
title: "Pack llm-wiki-historial-clases (Avatar USACH Virtual)"
source_kind: wiki-pack
layout_kind: atlas-wiki
origin: "../../raw/sub_wiki/llm-wiki-historial-clases/"
authors:
  - unknown
published: unknown
accessed: 2026-09-08
language: es
status: integrated
created: 2026-09-08
updated: 2026-09-08
version: "git:81c6fe553aa5bbf2c6d7856bbd0b7616e0af7050"
publisher: "https://github.com/JoseMichaeli/llm-wiki-historial-clases.git"
confidentiality: internal
---

# Pack llm-wiki-historial-clases (Avatar USACH Virtual)

## Resumen

Wiki completa sobre `Login`, `HistorialClases` e `HistorialTutorias` del producto Avatar de Apoyo Educativo USACH Virtual. Incluye evidencia original (maestros y SPECs), fichas de fuente, requisitos por vertical slice, decisiones de alcance, procesos de uso e implementación, y síntesis operativas con conflictos abiertos. El contrato interno del pack es el de Atlas-Wiki (`AGENTS.md`, `schemas/`, `wiki/`).

## Procedencia

El árbol vive como submódulo Git en `raw/sub_wiki/llm-wiki-historial-clases/`, URL `https://github.com/JoseMichaeli/llm-wiki-historial-clases.git`. No ingresó por `@subir_wiki`. La ficha se creó en `@sincronizar` del 2026-09-08 (commit `bb516ee`) y se actualizó en la misma fecha al fast-forward a `81c6fe553aa5bbf2c6d7856bbd0b7616e0af7050` (`docs: ingest Login pack into Atlas-Wiki`). Rama de seguimiento del padre: `origin/main`. No hubo choque de nombre con una copia `@subir_wiki`. El `AGENTS.md` interno del pack no gobierna este repositorio.

## Inventario

Árbol de layout `atlas-wiki`: `AGENTS.md`, `estructura.md`, `schemas/` (9 contratos), `raw/` y `wiki/`. Aproximadamente 121 archivos en el commit citado.

- **Evidencia (`raw/avatar-usach/`):** maestro y SPEC-LOGIN-01 a SPEC-LOGIN-06 en `login/`; maestro y SPEC-HC-01 a SPEC-HC-10 en `historial-clases/`; maestro y SPEC-HT-01 a SPEC-HT-08 en `historial-tutorias/`.
- **Conocimiento compilado en el pack (`wiki/`):** 1 proyecto, 1 organización, 3 decisiones, 27 requisitos, 10 conceptos, 6 procesos, 4 síntesis, 27 fichas de fuente, más `index.md` y `log.md`.
- **Puntos de entrada del pack:** [`wiki/index.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/index.md), [`wiki/syntheses/conocimiento-operativo-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-login.md), [`wiki/syntheses/conocimiento-operativo-historial-clases.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-historial-clases.md), [`wiki/syntheses/conocimiento-operativo-historial-tutorias.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-historial-tutorias.md), [`estructura.md`](../../raw/sub_wiki/llm-wiki-historial-clases/estructura.md).
- **Ausente en el árbol:** páginas de AI Adoption que el índice del pack aún enumera; mockups `001_Login.png`, `003_HistorialClases.png` y `004_HistorialTutorias.png`; specs de `Avatar` y `CargarMaterialClase`.

## Evidencia relevante

- **E1 — Producto:** El pack describe el producto «Avatar de Apoyo Educativo USACH Virtual», con conocimiento cubriendo Login, HistorialClases e HistorialTutorias. El estado `active` del proyecto en el pack refleja specs para el agente Harness, no evidencia de producción.
  - Localizador: [`wiki/projects/avatar-apoyo-educativo-usach-virtual.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/projects/avatar-apoyo-educativo-usach-virtual.md)
  - Uso: [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md)

- **E2 — Packs funcionales:** HistorialClases se implementa con maestro `05_historial_clases` y slices SPEC-HC-01 a SPEC-HC-10. HistorialTutorias se implementa con maestro `06_historial_tutorias` y slices SPEC-HT-01 a SPEC-HT-08. No hay SPEC-HT de validación E2E.
  - Localizador: [`wiki/index.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/index.md) (requisitos); [`estructura.md`](../../raw/sub_wiki/llm-wiki-historial-clases/estructura.md)
  - Uso: [Pantalla HistorialClases del flujo estudiante](../requirements/historial-clases-pantalla.md), [Pantalla HistorialTutorias del flujo estudiante](../requirements/historial-tutorias-pantalla.md)

- **E3 — Flujo estudiante:** Secuencia `Login` → `HistorialClases` → `Avatar`, con rama `HistorialClases` ↔ `HistorialTutorias` → `Avatar`, y `Salir` a `Login`. El pack de Login especifica la puerta; `Avatar` sigue sin pack.
  - Localizador: [`wiki/concepts/flujo-estudiante.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/concepts/flujo-estudiante.md)
  - Uso: [Flujo estudiante](../concepts/flujo-estudiante.md)

- **E4 — Alcance de HistorialClases:** Iteración con mocks o APIs de listado, selección temporal y navegación. Fuera: contexto académico real al avatar, RAG, vectorización, persistencia de selección, tutoría real, LLM, analítica y permisos académicos avanzados. Mockup obligatorio `003_HistorialClases.png`, no ingerido.
  - Localizador: [`wiki/decisions/alcance-iteracion-historial-clases.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/decisions/alcance-iteracion-historial-clases.md)
  - Uso: [Alcance de la iteración HistorialClases](../decisions/alcance-iteracion-historial-clases.md)

- **E5 — Alcance de HistorialTutorias:** Historial visible, navegación real a `Avatar`, retorno a clases y salida a `Login`. Fuera: conversaciones reales, persistencia de tutorías nuevas, mensajes históricos reales, analítica, LLM, RAG, STT, TTS o LiveAvatar desde esta pantalla. Mockup obligatorio `004_HistorialTutorias.png`, no ingerido.
  - Localizador: [`wiki/decisions/alcance-iteracion-historial-tutorias.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/decisions/alcance-iteracion-historial-tutorias.md)
  - Uso: [Alcance de la iteración HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md)

- **E6 — Conflictos abiertos en HistorialClases:** (1) lista visible al entrar según HC-10 versus lista oculta hasta elegir curso según HC-01; (2) exclusión de contexto real versus GET de documentos con `contenido_extraido` en HC-05; (3) tres nombres para la lista de ids (`clasesSeccionadas`, `clasesSeleccionadas`, `selectedContentIds`).
  - Localizador: [`wiki/syntheses/conocimiento-operativo-historial-clases.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-historial-clases.md), sección «Evidencia en conflicto»
  - Uso: [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md)

- **E7 — Conflictos abiertos en HistorialTutorias:** (1) historial mock y prohibición de consulta real versus GET de `tutorias` / `clase_tutoria` en HT-02; (2) criterio de HT-02 de que la pantalla no aparezca vacía versus estado vacío de HT-08; (3) contrato snake_case de HT-02 versus payload camelCase de HT-04 hacia Avatar.
  - Localizador: [`wiki/syntheses/conocimiento-operativo-historial-tutorias.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-historial-tutorias.md), sección «Evidencia en conflicto»
  - Uso: [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md)

- **E8 — USACH Virtual:** Aparece como identidad de encabezado y marco visual en Login, HistorialClases e HistorialTutorias, no como entidad legal descrita de forma independiente. El pack marca como inferencia la asociación con la Universidad de Santiago de Chile.
  - Localizador: [`wiki/organizations/usach-virtual.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/organizations/usach-virtual.md)
  - Uso: [USACH Virtual](../organizations/usach-virtual.md)

- **E9 — Índice del pack desalineado:** [`wiki/index.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/index.md) enumera páginas de AI Adoption (proyecto, persona Jonnathan, fuentes de 2026-08-24/25) que no existen en este árbol. El conocimiento real del submódulo es Login, HistorialClases e HistorialTutorias.
  - Localizador: [`wiki/index.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/index.md) frente a la ausencia de `wiki/projects/ai-adoption.md` y `wiki/people/`
  - Uso: [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md)

- **E10 — Dueños y fechas:** El pack no nombra personas dueñas del producto ni fechas de aprobación. `decision_makers` y `owners` permanecen `unknown`. No se documenta vínculo con otros proyectos de Atlas.
  - Localizador: [`wiki/projects/avatar-apoyo-educativo-usach-virtual.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/projects/avatar-apoyo-educativo-usach-virtual.md), sección «Responsables y participantes»
  - Uso: [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md)

- **E11 — Pack Login:** Maestro `03_login` y slices SPEC-LOGIN-01 a SPEC-LOGIN-06. No hay slice E2E; el cierre es la sección 7 del maestro. Tras ingreso exitoso, `PROFESOR` va a `CargarMaterialClase` y `ESTUDIANTE` a `HistorialClases`.
  - Localizador: [`wiki/requirements/login-pantalla.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/requirements/login-pantalla.md); [`wiki/concepts/login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/concepts/login.md)
  - Uso: [Login](../concepts/login.md), [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)

- **E12 — Alcance de Login:** UI según `001_Login.png`, captura de correo y contraseña, rol y redirección. Fuera: recuperación de contraseña, registro, MFA, autorización avanzada e IdP. Mockup `001_Login.png` no ingerido.
  - Localizador: [`wiki/decisions/alcance-iteracion-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/decisions/alcance-iteracion-login.md)
  - Uso: [Alcance de la iteración Login](../decisions/alcance-iteracion-login.md)

- **E13 — Conflicto de autenticación:** El cuerpo del maestro (secciones 4–5) y los criterios de LOGIN-03 niegan o postergan validación real. El anexo y partes de LOGIN-03/05 exigen PostgreSQL, JWT, `POST /api/v1/auth/login`, 401 y prohibición de mocks. LOGIN-03 se contradice a sí mismo (objetivo simulado vs tablas reales vs JSON demo).
  - Localizador: [`wiki/syntheses/conocimiento-operativo-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-login.md), hallazgos H4–H6 y sección «Evidencia en conflicto»
  - Uso: [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md), [Alcance de la iteración Login](../decisions/alcance-iteracion-login.md)

- **E14 — Campos vacíos:** HU-LOGIN-01 y LOGIN-05 impiden avanzar sin correo o contraseña. Los criterios de LOGIN-03 niegan error por vacío.
  - Localizador: [`wiki/syntheses/conocimiento-operativo-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-login.md), hallazgo H7
  - Uso: [Ingresar al sistema desde Login](../processes/ingresar-al-sistema-desde-login.md)

- **E15 — Sesión simulada versus JWT:** HC-07 y HT-06 limpian sesión simulada. El anexo de Login prohíbe sesiones simuladas y exige JWT.
  - Localizador: [`wiki/syntheses/conocimiento-operativo-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-login.md), hallazgo H10
  - Uso: [Alcance de la iteración Login](../decisions/alcance-iteracion-login.md), [Alcance de la iteración HistorialClases](../decisions/alcance-iteracion-historial-clases.md)

- **E16 — Destinos aún no especificados:** `CargarMaterialClase` y `Avatar` están nombrados y no tienen pack en este árbol.
  - Localizador: [`wiki/concepts/flujo-profesor.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/concepts/flujo-profesor.md); [`wiki/projects/avatar-apoyo-educativo-usach-virtual.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/projects/avatar-apoyo-educativo-usach-virtual.md)
  - Uso: [Flujo profesor](../concepts/flujo-profesor.md)

- **E17 — Tipo de usuario contestado:** El discriminante es `PROFESOR` o `ESTUDIANTE`. Los nombres de contrato no están unificados (`tipoUsuario` / `tipo_usuario`, `idUsuario` / `userId` / `user_id`, `username` / `email`).
  - Localizador: [`wiki/concepts/tipo-usuario.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/concepts/tipo-usuario.md)
  - Uso: [Tipo de usuario](../concepts/tipo-usuario.md)

## Alcance y limitaciones

El pack permite sostener el mapa de Login y de las dos pantallas de historial, sus exclusiones de iteración y los conflictos internos de los SPECs. No permite concluir el estado de producción, la gobernanza, el stack Harness, ni unificar el mecanismo de autenticación. No cubre `Avatar` ni `CargarMaterialClase`. Los mockups gráficos citados no están en `raw/`. El índice del pack no es un inventario fiable de AI Adoption. Las síntesis internas del pack contienen recomendaciones de agente que no son decisiones. Esta ficha no sustituye las páginas del pack para el detalle de cada slice.

## Relaciones

### Páginas derivadas

- [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md)
- [USACH Virtual](../organizations/usach-virtual.md)
- [Login](../concepts/login.md)
- [Tipo de usuario](../concepts/tipo-usuario.md)
- [Flujo profesor](../concepts/flujo-profesor.md)
- [HistorialClases](../concepts/historial-clases.md)
- [HistorialTutorias](../concepts/historial-tutorias.md)
- [Flujo estudiante](../concepts/flujo-estudiante.md)
- [Alcance de la iteración Login](../decisions/alcance-iteracion-login.md)
- [Alcance de la iteración HistorialClases](../decisions/alcance-iteracion-historial-clases.md)
- [Alcance de la iteración HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md)
- [Pantalla Login del MVP Avatar USACH Virtual](../requirements/login-pantalla.md)
- [Pantalla HistorialClases del flujo estudiante](../requirements/historial-clases-pantalla.md)
- [Pantalla HistorialTutorias del flujo estudiante](../requirements/historial-tutorias-pantalla.md)
- [Ingresar al sistema desde Login](../processes/ingresar-al-sistema-desde-login.md)
- [Iniciar estudio desde HistorialClases](../processes/iniciar-estudio-desde-historial-clases.md)
- [Consultar historial de tutorías](../processes/consultar-historial-tutorias.md)
- [Conocimiento compilado del pack llm-wiki-historial-clases](../syntheses/pack-llm-wiki-historial-clases.md)

### Fuentes relacionadas

- Ninguna todavía.
