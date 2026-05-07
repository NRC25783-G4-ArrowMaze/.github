# Convencion de Commits — Arrow Maze

Este proyecto sigue el estandar [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) de forma **obligatoria**. El cumplimiento se valida automaticamente mediante GitHub Actions en cada Pull Request.

---

## Formato

```
tipo(scope): descripcion breve en ingles
                                          ← linea en blanco
cuerpo opcional (max 100 caracteres por linea)
                                          ← linea en blanco
footer opcional
```

### Reglas

| Regla | Nivel | Descripcion |
|---|---|---|
| Formato general | Error | Debe seguir `tipo(scope): descripcion` |
| `scope-enum` | Error | Solo se permiten los scopes definidos abajo |
| `subject-max-length` | Error | Maximo **72 caracteres** en la descripcion |
| `body-max-line-length` | Warning | Maximo **100 caracteres** por linea en el cuerpo |
| Idioma | Obligatorio | Los mensajes de commit deben estar en **ingles** |

---

## Tipos validos

| Tipo | Cuando usarlo |
|---|---|
| `feat` | Nueva funcionalidad para el usuario |
| `fix` | Correccion de un bug |
| `test` | Añadir o modificar pruebas (sin cambiar codigo de produccion) |
| `docs` | Cambios exclusivamente en documentacion |
| `refactor` | Refactorizacion de codigo sin cambiar comportamiento externo |
| `style` | Cambios de formato (espacios, indentacion, punto y coma, etc.) |
| `chore` | Tareas de mantenimiento (actualizar dependencias, configs) |
| `perf` | Mejora de rendimiento sin cambio funcional |
| `ci` | Cambios en configuracion de CI/CD (workflows, pipelines) |
| `build` | Cambios en el sistema de build o dependencias externas |
| `revert` | Revertir un commit anterior |

---

## Scopes permitidos

Los scopes estan limitados al dominio del proyecto Arrow Maze:

| Scope | Contexto de uso |
|---|---|
| `board` | Logica del tablero, cuadricula y celdas |
| `player` | Movimiento, estado y acciones del jugador |
| `level` | Generacion, carga, definicion y gestion de niveles |
| `ui` | Componentes visuales e interfaz de usuario |
| `audio` | Sistema de audio, efectos de sonido y musica |
| `auth` | Autenticacion, registro, JWT y sesiones |
| `api` | Endpoints REST, comunicacion cliente-servidor |
| `db` | Base de datos, migraciones y persistencia |
| `use-case` | Casos de uso de la capa de aplicacion |
| `readme` | Cambios en documentacion README |
| `ci` | Configuracion de integracion continua y despliegue |

---

## Ejemplos

```bash
# Nueva funcionalidad
feat(board): add arrow rotation logic
feat(level): implement level selection screen
feat(auth): add JWT-based user registration

# Correccion de errores
fix(player): correct movement when hitting wall
fix(api): handle 404 response on level fetch

# Pruebas
test(use-case): add unit tests for MovePlayerUseCase
test(board): add integration tests for grid rendering

# Documentacion
docs(readme): update architecture diagram
docs(readme): add SOLID principles section

# Refactorizacion
refactor(level): apply Factory Method pattern to cell creation
refactor(board): extract cell validation to separate service

# Mantenimiento
chore(ci): update commitlint action to v6
chore(build): upgrade Flutter SDK to 3.x
```

---

## Automatizacion

La validacion de commits esta automatizada mediante:

- **Workflow**: [`workflows/commitlint.yml`](workflows/commitlint.yml) — se ejecuta en cada PR hacia `main` o `develop`.
- **Configuracion**: [`commitlint.config.js`](commitlint.config.js) — reglas basadas en `@commitlint/config-conventional`.
- **Action**: [`wagoid/commitlint-action@v6`](https://github.com/wagoid/commitlint-github-action) — valida todos los commits del PR.

> Los PRs con commits que no cumplan el formato seran bloqueados automaticamente por el workflow de CI.

---

## Referencia

- [Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)
- [commitlint](https://commitlint.js.org/)
- [@commitlint/config-conventional](https://www.npmjs.com/package/@commitlint/config-conventional)
