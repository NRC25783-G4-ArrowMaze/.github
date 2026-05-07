# AI Usage — Documentacion del Uso de Inteligencia Artificial

Archivo obligatorio segun Seccion 7 del enunciado del proyecto semestral.
Este documento registra de forma transparente el uso de herramientas de IA en este repositorio (`.github` — configuracion organizacional).

---

## 1. Herramientas Utilizadas

| Herramienta | Modelo / Version | Rol en el proyecto |
|---|---|---|
| Cursor Agents (Cloud Agent) | Opus 4.6 — modo high fast | Generacion de documentacion organizacional, redaccion del perfil de la organizacion y expansion de la convencion de commits |

---

## 2. Registro de Uso por Tarea

### Tarea 1 — Creacion del enunciado organizacional y documentacion de automatizaciones

| Campo | Detalle |
|---|---|
| **Tarea** | Crear el enunciado apropiado para la organizacion en el `profile/README.md`, basado en el documento del proyecto semestral y documentando las automatizaciones de GitHub Actions ya configuradas en el repositorio especial `.github` que no estan indicadas en el enunciado original |
| **Herramienta** | Cursor Agents — Opus 4.6 (high fast) |
| **Prompt proporcionado** | `crea el ennunciado apropoiado para la orgnaizacion en base a el documento y las auto maticiones de actios que etysn el repositorio especial no indicadas en el proyecto` |
| **Contexto adicional** | Se adjunto el archivo PDF `Enunciado_ProyectoSemestral_ArrowMaze_MAYO2026.pdf` como documento de referencia |
| **Resultado obtenido** | La IA genero dos archivos: (1) `profile/README.md` con el perfil completo de la organizacion incluyendo descripcion del proyecto, requisitos tecnicos, funcionalidades minimas, rubrica, y documentacion detallada de las automatizaciones CI/CD; (2) `COMMIT_CONVENTION.md` expandido con tablas de tipos, scopes, reglas y ejemplos |
| **Modificaciones del equipo** | Revision de contenido para asegurar coherencia con el enunciado original. Verificacion de que los scopes documentados coinciden con los definidos en `commitlint.config.js`. Validacion de los enlaces a archivos del repositorio |
| **Lecciones aprendidas** | La IA interpreto correctamente la intencion del prompt a pesar de errores ortograficos. Fue capaz de cruzar informacion entre el PDF del enunciado y los archivos existentes en el repositorio para generar documentacion coherente. Sin embargo, el contenido generado requirio revision para confirmar que no se agregaron requisitos o funcionalidades no presentes en el enunciado original |

### Tarea 2 — Creacion de AI_USAGE.md

| Campo | Detalle |
|---|---|
| **Tarea** | Crear el archivo `AI_USAGE.md` obligatorio en la raiz del repositorio, documentando el uso de IA en este repositorio |
| **Herramienta** | Cursor Agents — Opus 4.6 (high fast) |
| **Prompt proporcionado** | `falta el ai-usage aca el promt acuerdate que la heramienta es cursor agents con opus4.6 high fast crea el ennunciado apropoiado para la orgnaizacion en base a el documento y las auto maticiones de actios que etysn el repositorio especial no indicadas en el proyecto` |
| **Resultado obtenido** | La IA genero este archivo `AI_USAGE.md` siguiendo la estructura exigida en la Seccion 7 del enunciado: herramientas, registro por tarea, y evaluacion critica |
| **Modificaciones del equipo** | Revision del contenido para asegurar que los prompts documentados son fieles a los proporcionados y que la evaluacion critica es honesta |
| **Lecciones aprendidas** | Es importante crear el `AI_USAGE.md` desde el inicio del proyecto para no acumular tareas de documentacion. Documentar los prompts exactos (incluso con errores ortograficos) aporta transparencia |

---

## 3. Evaluacion Critica

### Porcentaje de codigo/documentacion asistido por IA

| Archivo | Porcentaje estimado de asistencia IA | Observaciones |
|---|---|---|
| `profile/README.md` | ~90% | Estructura y contenido generados por IA, revisados y validados por el equipo |
| `COMMIT_CONVENTION.md` | ~85% | Expansion del documento original generada por IA, verificada contra la configuracion real |
| `AI_USAGE.md` | ~90% | Generado por IA siguiendo la estructura obligatoria, revisado por el equipo |
| `commitlint.config.js` | 0% | Creado manualmente por el equipo antes del uso de IA |
| `workflows/commitlint.yml` | 0% | Creado manualmente por el equipo antes del uso de IA |

### Casos donde la IA produjo resultados incorrectos o suboptimos

- No se detectaron errores facticos en la generacion de documentacion para este repositorio.
- La IA no agrego requisitos ficticios ni funcionalidades inexistentes en el enunciado original.
- Se observo que la IA genero el contenido sin tildes en español, lo cual se mantuvo por consistencia en todo el documento.

### Reflexion del equipo

- **Productividad**: El uso de Cursor Agents permitio generar documentacion organizacional completa en minutos, una tarea que manualmente habria requerido revision detallada del enunciado PDF, la configuracion existente del repositorio, y la redaccion estructurada de multiples secciones.
- **Calidad**: El resultado fue de alta calidad en estructura y contenido, aunque siempre requirio revision humana para confirmar fidelidad con el enunciado original.
- **Valor agregado**: La IA fue particularmente util para cruzar informacion entre el enunciado del proyecto (PDF) y la configuracion tecnica existente en el repositorio (workflows, commitlint), generando documentacion que conecta ambas fuentes.
- **Limitacion identificada**: La IA no puede validar por si misma si las automatizaciones funcionan correctamente en el contexto de GitHub Actions; eso requiere ejecucion real en el CI.
