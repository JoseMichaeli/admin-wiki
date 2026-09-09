---
type: synthesis
title: "Conocimiento compilado del pack llm-wiki-historial-clases"
synthesis_kind: state-of-knowledge
status: contested
question: "¿Qué cubre el pack llm-wiki-historial-clases sobre el Avatar USACH Virtual, qué quedó compilado en Atlas-Wiki y qué conflictos siguen abiertos?"
sources:
  - "../sources/llm-wiki-historial-clases.md"
as_of: 2026-09-08
scope:
  - "../projects/avatar-apoyo-educativo-usach-virtual.md"
  - "../requirements/login-pantalla.md"
  - "../requirements/historial-clases-pantalla.md"
  - "../requirements/historial-tutorias-pantalla.md"
authors:
  - "Agente, bajo dirección de la persona usuaria"
created: 2026-09-08
updated: 2026-09-08
---

# Conocimiento compilado del pack llm-wiki-historial-clases

## Pregunta y alcance

Esta síntesis integra el pack submódulo `llm-wiki-historial-clases` (commit `81c6fe5`, consultado el 2026-09-08) para Atlas-Wiki: qué producto describe, qué pantallas cubre, qué páginas se derivaron aquí y qué tensiones no se resolvieron. No sustituye las síntesis operativas del pack ni copia cada slice. Excluye AI Adoption: el índice interno del pack la enumera, pero esas páginas no existen en el árbol.

## Respuesta breve

El pack es una wiki Atlas sobre tres pantallas del [Avatar USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md): [Login](../concepts/login.md) (seis slices), [HistorialClases](../concepts/historial-clases.md) (diez) e [HistorialTutorias](../concepts/historial-tutorias.md) (ocho). Login abre el [flujo profesor](../concepts/flujo-profesor.md) (`CargarMaterialClase`, no especificada) o el [flujo estudiante](../concepts/flujo-estudiante.md). Atlas-Wiki conserva la ficha `wiki-pack`, el proyecto, la organización, los conceptos, las tres decisiones de alcance, los tres requisitos padre, los tres procesos de uso y esta síntesis. El detalle de cada SPEC permanece en el submódulo. El pack está **contestado** sobre autenticación (cuerpo vs anexo vs LOGIN-03) y conserva los conflictos ya abiertos de HC y HT.

## Hallazgos

### H1 — El pack describe un producto de avatar educativo, no un servicio de adopción de IA

El conocimiento real del submódulo es Login, HistorialClases e HistorialTutorias. El índice del pack aún lista AI Adoption, Jonnathan y fuentes de agosto 2026 que no están en este árbol.

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E1, E9
- Tipo: hecho documentado

### H2 — Login es la puerta común; HistorialClases es el hub del estudiante

Tras autenticarse, `PROFESOR` va a `CargarMaterialClase` y `ESTUDIANTE` a `HistorialClases`. El estudiante elige curso y contenidos, entra a `Avatar` con `Estudiemos`, visita tutorías o sale al login.

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E2, E3, E11
- Tipo: hecho documentado

### H3 — Las iteraciones son deliberadamente incompletas

Login queda fuera de registro, MFA e IdP. HC queda fuera de RAG, contexto real, persistencia y LLM. HT queda fuera de conversaciones persistidas, mensajes reales y LLM/RAG/STT/TTS/LiveAvatar. Los mockups `001`, `003` y `004` son obligatorios y no están en el pack. `Avatar` y `CargarMaterialClase` solo se nombran.

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E4, E5, E12, E16
- Tipo: hecho documentado

### H4 — Conflictos de HistorialClases no resueltos

Lista al entrar (HC-01 versus HC-10), GET de documentos con `contenido_extraido` versus exclusión de contexto real, y tres nombres para la lista de ids.

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E6
- Tipo: hecho documentado (contradicción interna del pack)

### H5 — Conflictos de HistorialTutorias no resueltos

Historial mock versus GET de `tutorias` / `clase_tutoria` (HT-02); pantalla «no vacía» versus mensaje de vacío (HT-08); contrato snake_case versus payload camelCase hacia Avatar (HT-04).

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E7
- Tipo: hecho documentado (contradicción interna del pack)

### H6 — Atlas-Wiki no duplica los slices

Los requisitos padre enlazan el directorio de requisitos del pack. Las síntesis operativas y el backlog `BL-*` de HistorialClases permanecen en el pack.

- Evidencia: inventario de [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md)
- Tipo: convención de esta recompilación

### H7 — USACH Virtual es identidad de interfaz

No hay evidencia de personería jurídica ni de personas vinculadas. LOGIN-01 también exige esa identidad en Login.

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E8, E10
- Tipo: hecho documentado

### H8 — El mecanismo de autenticación de Login no está unificado

El cuerpo del maestro y los criterios de LOGIN-03 niegan o postergan validación real. El anexo exige PostgreSQL, JWT y 401. LOGIN-03 se contradice a sí mismo. HC-07/HT-06 limpian sesión simulada; el anexo la prohíbe. Campos vacíos y nombres de contrato (`idUsuario` / `userId` / `user_id`) también divergen.

- Evidencia: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md) E13, E14, E15, E17
- Tipo: hecho documentado (contradicción interna del pack)

## Análisis

La recompilación incremental trata el pack como una fuente única `wiki-pack`. El commit `81c6fe5` añade Login sin vaciar el conocimiento de HC/HT. Copiar cada SPEC a `wiki/` repetiría el árbol interno.

Inferencia: un implementador conservador puede construir UI, captura y redirección por rol; no puede, sin una decisión humana, cumplir a la vez el anexo JWT y la exclusión de validación real. Para HC/HT, la lectura conservadora sigue siendo mocks sustituibles y GET de documentos/tutorías como contratos no unificados. Esas lecturas las proponen las síntesis del pack; no son decisiones de Atlas-Wiki.

El índice interno del pack no debe usarse como catálogo de AI Adoption.

## Evidencia en conflicto

Los conflictos materiales están dentro del pack, no entre el pack y otras fuentes de Atlas-Wiki:

1. Lista al entrar en HistorialClases (HC-01 vs HC-10 / HU-HC-01).
2. Contexto hacia Avatar (exclusión de contexto real vs GET de documentos en HC-05).
3. Nombre de la lista de ids.
4. Mock vs GET real de tutorías (maestro HT vs HT-02).
5. Pantalla vacía (HT-02 vs HT-08).
6. Contrato hacia Avatar (HT-02 vs HT-04).
7. Validación real de credenciales (cuerpo y criterios LOGIN-03 vs anexo, HU y LOGIN-05).
8. Mocks y usuarios demo (anexo los prohíbe; LOGIN-03 los incluye).
9. Sesión JWT versus simulada (anexo vs HC-07/HT-06).
10. Campos vacíos (HU/LOGIN-05 vs criterios LOGIN-03).
11. Nombres de contrato de usuario (E17).

No hay otra fuente en Atlas-Wiki que confirme, amplíe o contradiga estas afirmaciones.

## Limitaciones y preguntas abiertas

- Dueños, fechas de aprobación y stack Harness no están documentados.
- Faltan mockups y specs de `Avatar` y `CargarMaterialClase`.
- Rutas HTTP, hashing de contraseña, contenido del JWT y retorno desde `Avatar` no están definidos.
- Relación con otros proyectos de Atlas no está documentada; no se infiere.
- El detalle de cada slice y el backlog `BL-*` no están compilados aquí.

## Relaciones

- Fuente: [Pack llm-wiki-historial-clases](../sources/llm-wiki-historial-clases.md)
- Proyecto: [Avatar de Apoyo Educativo USACH Virtual](../projects/avatar-apoyo-educativo-usach-virtual.md)
- Organización: [USACH Virtual](../organizations/usach-virtual.md)
- Decisiones: [Alcance Login](../decisions/alcance-iteracion-login.md), [Alcance HistorialClases](../decisions/alcance-iteracion-historial-clases.md), [Alcance HistorialTutorias](../decisions/alcance-iteracion-historial-tutorias.md)
- Requisitos padre: [Login](../requirements/login-pantalla.md), [HistorialClases](../requirements/historial-clases-pantalla.md), [HistorialTutorias](../requirements/historial-tutorias-pantalla.md)
- Procesos: [Ingresar](../processes/ingresar-al-sistema-desde-login.md), [Iniciar estudio](../processes/iniciar-estudio-desde-historial-clases.md), [Consultar tutorías](../processes/consultar-historial-tutorias.md)
- Síntesis operativas en el pack: [`conocimiento-operativo-login.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-login.md), [`conocimiento-operativo-historial-clases.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-historial-clases.md), [`conocimiento-operativo-historial-tutorias.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/conocimiento-operativo-historial-tutorias.md), [`backlog-historial-clases.md`](../../raw/sub_wiki/llm-wiki-historial-clases/wiki/syntheses/backlog-historial-clases.md)
