# Arrow Maze — Escape Puzzle (Clon)

**Proyecto Semestral | Desarrollo de Software | NRC 25783**

Organización del Grupo 4 para el desarrollo de un clon funcional del juego casual [Arrow Maze — Escape Puzzle](https://play.google.com/store/apps/details?id=com.arrows.escape) de SayGames Ltd.

---

## Descripcion del Proyecto

El proyecto consiste en diseñar e implementar un clon del juego Arrow Maze aplicando principios y buenas practicas de ingenieria de software. El juego se basa en un tablero en cuadricula con celdas que contienen flechas direccionales; el jugador interactua con las flechas para encontrar la ruta de escape a traves de niveles con dificultad progresiva.

### Mecanicas principales del juego de referencia

- Tablero en cuadricula (grid) con celdas que contienen flechas en cuatro direcciones.
- El jugador toca una celda para rotar o activar la direccion de su flecha.
- Dificultad progresiva: niveles facil, medio y dificil.
- Elementos adicionales: paredes, celdas vacias, coleccionables y tiempo limite.
- Sistema de puntuacion basado en numero de movimientos y tiempo empleado.

---

## Estructura de Repositorios

El proyecto se organiza en **tres repositorios** dentro de esta organizacion, mas este repositorio especial de configuracion:

| Repositorio | Tecnologia | Rol |
|---|---|---|
| [**arrowmaze-project-core**](https://github.com/NRC25783-G4-ArrowMaze/arrowmaze-project-core) | Markdown + Gherkin (BDD) | **Fuente unica de verdad**: especificaciones, decisiones arquitectonicas e historial de sesiones SDD |
| [**arrowmaze-game**](https://github.com/NRC25783-G4-ArrowMaze/arrowmaze-game) | React 18 + TypeScript + Vite + Capacitor | **Cliente**: aplicacion movil que implementa las mecanicas del juego |
| [**arrowmaze-backend**](https://github.com/NRC25783-G4-ArrowMaze/arrowmaze-backend) | Express.js + Node.js + TypeScript + PostgreSQL | **API REST**: gestiona usuarios, puntuaciones, niveles y progreso |
| [**`.github`**](https://github.com/NRC25783-G4-ArrowMaze/.github) (este repo) | GitHub Actions | Configuracion organizacional, automatizaciones CI/CD compartidas y perfil de la organizacion |

### Flujo Specification-Driven Development (SDD)

Las especificaciones y decisiones de arquitectura se **centralizan en `arrowmaze-project-core`** antes de escribir codigo. El cliente y el backend **sincronizan sus specs** desde alli para implementarlas:

```
Cambios en specs/decisiones
        ↓
Actualizar features/*.feature + docs/ en project-core
        ↓
arrowmaze-game y arrowmaze-backend sincronizan e implementan
```

### Estado del proyecto

Ambos repositorios de implementacion estan **cerrados y congelados en `v1.0.0`**:

- 🔒 **arrowmaze-backend** — `v1.0.0` (2026-07-09)
- 🔒 **arrowmaze-game** — `v1.0.0` (2026-07-11)
- 📓 **arrowmaze-project-core** — bitácora histórica: registra *cómo* se llegó a la v1.0.0

---

## Requisitos Tecnicos

### Principios SOLID

Todo el codigo debe evidenciar la aplicacion de los cinco principios SOLID, documentados en el README de cada repositorio con ejemplos concretos del codigo:

- **S** — Single Responsibility Principle
- **O** — Open/Closed Principle
- **L** — Liskov Substitution Principle
- **I** — Interface Segregation Principle
- **D** — Dependency Inversion Principle

### Patrones de Diseno (GoF)

Se deben implementar patrones de las tres categorias:

| Categoria | Patrones |
|---|---|
| **Creacionales** | Factory Method / Abstract Factory, Builder, Singleton |
| **Estructurales** | Composite, Decorator, Adapter, Facade |
| **Comportamiento** | Strategy, Observer, Command, State, Template Method |

### Arquitectura CLEAN

El proyecto sigue la Clean Architecture de Robert C. Martin, organizada en cuatro capas concentricas:

1. **Entidades (Domain)** — Objetos de negocio puros, sin dependencias externas.
2. **Casos de Uso (Application)** — Logica de aplicacion, depende solo de interfaces/puertos.
3. **Adaptadores de Interfaz** — Presenters, ViewModels, Controllers, Repositories, Mappers.
4. **Frameworks e Infraestructura** — Motor de juego, base de datos, librerias de red.

> La regla de dependencia se respeta estrictamente: las dependencias siempre apuntan hacia adentro (hacia el dominio).

### Programacion Orientada a Aspectos (AOP)

Se implementan aspectos para separar las responsabilidades transversales (cross-cutting concerns) del codigo de negocio: logging, manejo centralizado de excepciones, metricas de rendimiento, seguridad y/o cache de resultados.

### Pruebas

- **Unitarias**: patron AAA (Arrange-Act-Assert), nomenclatura `should_[resultado]_when_[condicion]`.
- **Integracion**: interaccion entre casos de uso y repositorios, endpoints de la API.
- **Widget/UI**: renderizado y navegacion entre pantallas.
- **Contrato** (recomendadas): verificacion de contratos cliente-servidor con Pact.

---

## Funcionalidades Minimas

### Aplicacion (Juego)

1. Pantalla de inicio con nombre del juego, boton de jugar y acceso a ajustes.
2. Pantalla de seleccion de niveles con indicador de progreso y niveles bloqueados.
3. Motor de juego funcional: tablero en cuadricula, flechas rotables, movimiento por camino.
4. Minimo 15 niveles diseñados manualmente con dificultad progresiva.
5. Sistema de puntuacion configurable.
6. Pantallas de victoria y derrota.
7. Persistencia local del progreso del jugador.
8. Efectos de sonido y musica de fondo con opcion de silenciar.
9. Soporte para al menos dos idiomas (español e ingles).

### Backend (API REST)

1. Autenticacion de usuarios (registro e inicio de sesion) con JWT.
2. Sincronizacion del progreso del jugador con el servidor.
3. Tabla de clasificacion global (leaderboard) por nivel.
4. Gestion de definicion de niveles (añadir niveles sin actualizar la app).
5. Documentacion de la API con Swagger / OpenAPI.
6. Manejo adecuado de errores HTTP y respuestas consistentes.

---

## Automatizaciones CI/CD Configuradas

Este repositorio especial (`.github`) contiene automatizaciones **ya operativas** que aplican a todos los repositorios de la organizacion. Estas automatizaciones van mas alla de lo solicitado en el enunciado del proyecto y representan buenas practicas adicionales adoptadas por el equipo:

### Validacion Automatica de Commits — `commitlint`

Se ha configurado un workflow de GitHub Actions que **valida automaticamente el formato de los mensajes de commit** en cada Pull Request dirigido a las ramas `main` o `develop`.

**Workflow:** [`workflows/commitlint.yml`](../workflows/commitlint.yml)

- **Trigger:** Pull Requests hacia `main` y `develop`.
- **Action:** [`wagoid/commitlint-action@v6`](https://github.com/wagoid/commitlint-github-action) con checkout completo del historial (`fetch-depth: 0`).
- **Configuracion:** [`commitlint.config.js`](../commitlint.config.js) basada en `@commitlint/config-conventional`.

**Reglas aplicadas:**

| Regla | Nivel | Valor |
|---|---|---|
| `scope-enum` | Error | Solo se permiten los scopes: `board`, `player`, `level`, `ui`, `audio`, `auth`, `api`, `db`, `use-case`, `readme`, `ci` |
| `subject-max-length` | Error | Maximo 72 caracteres en el asunto |
| `body-max-line-length` | Warning | Maximo 100 caracteres por linea en el cuerpo |

**Formato obligatorio de commits:**

```
tipo(scope): descripcion breve en ingles
```

**Tipos validos** (segun Conventional Commits):

| Tipo | Uso |
|---|---|
| `feat` | Nueva funcionalidad |
| `fix` | Correccion de errores |
| `test` | Añadir o modificar pruebas |
| `docs` | Cambios en documentacion |
| `refactor` | Refactorizacion de codigo sin cambio de comportamiento |
| `style` | Cambios de formato (espacios, comas, etc.) |
| `chore` | Tareas de mantenimiento (dependencias, configs) |
| `perf` | Mejoras de rendimiento |
| `ci` | Cambios en configuracion de CI/CD |
| `build` | Cambios en el sistema de build |
| `revert` | Revertir un commit anterior |

**Scopes definidos para el dominio del proyecto:**

| Scope | Contexto |
|---|---|
| `board` | Logica del tablero y cuadricula |
| `player` | Movimiento y estado del jugador |
| `level` | Generacion, carga y gestion de niveles |
| `ui` | Componentes de interfaz de usuario |
| `audio` | Sistema de audio (efectos y musica) |
| `auth` | Autenticacion y autorizacion |
| `api` | Endpoints y comunicacion cliente-servidor |
| `db` | Base de datos y persistencia |
| `use-case` | Casos de uso de la capa de aplicacion |
| `readme` | Documentacion README |
| `ci` | Configuracion de integracion continua |

**Ejemplos validos:**

```
feat(board): add arrow rotation logic
fix(player): correct movement when hitting wall
test(use-case): add unit tests for MovePlayerUseCase
docs(readme): update architecture diagram
refactor(level): apply Factory Method pattern to cell creation
chore(ci): update commitlint action to v6
```

> Esta automatizacion garantiza que todo el historial de Git siga el estandar Conventional Commits de forma obligatoria, rechazando automaticamente los PRs cuyos commits no cumplan el formato.

---

## Documentacion Obligatoria

Cada repositorio debe incluir:

| Archivo / Seccion | Descripcion |
|---|---|
| `README.md` | Documentacion completa del proyecto (arquitectura, patrones, SOLID, AOP, setup, pruebas) |
| `AI_USAGE.md` | Registro transparente del uso de herramientas de IA (herramientas, prompts, modificaciones, evaluacion critica) |
| `/docs/` | Diagramas de clases y de capas Clean Architecture (imagen + fuente editable) |

---

## Rubrica de Evaluacion — 20 Puntos

| # | Criterio | Puntos |
|---|---|---|
| 1 | Funcionalidad del Juego | 4 pts |
| 2 | Principios SOLID | 2 pts |
| 3 | Patrones de Diseno | 3 pts |
| 4 | Arquitectura CLEAN | 3 pts |
| 5 | AOP | 2 pts |
| 6 | Pruebas | 2 pts |
| 7 | Backend y API REST | 1 pt |
| 8 | Documentacion (README + Diagramas) | 0.5 pts |
| 9 | Documentacion del Uso de IA | 0.5 pts |
| 10 | Defensa individual | 2 pts |
| | **Total** | **20 pts** |

---

## Uso de IA

El uso de herramientas de IA generativa esta **permitido y es bienvenido**, condicionado a documentacion rigurosa y transparente en el archivo `AI_USAGE.md` de cada repositorio. El equipo es responsable de todo el codigo entregado, independientemente de si fue generado con asistencia de IA.

---

## Fecha de Entrega

**Lunes 13 de julio de 2026, 9:00 AM**

---

## Referencias y Recursos

- [Arrow Maze — Escape Puzzle (Google Play)](https://play.google.com/store/apps/details?id=com.arrows.escape)
- [Conventional Commits](https://www.conventionalcommits.org)
- [Clean Architecture (Uncle Bob)](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [GitHub Actions](https://docs.github.com/en/actions)
- [Pact — Contract Testing](https://docs.pact.io/)
- Martin, R. C. (2017). *Clean Architecture*. Prentice Hall.
- Gamma et al. (1994). *Design Patterns: Elements of Reusable OO Software*. Addison-Wesley.
- Martin, R. C. (2008). *Clean Code*. Prentice Hall.
