# scaffold-base

Template base para arrancar proyectos rápido: **backend en Python (FastAPI + uv)** y **frontend en React (TanStack + Vite)**, ya configurados con linting, formateo y las dependencias más comunes preinstaladas.

> Licencia: [MIT](./LICENSE).

Repositorio: https://github.com/ElPitagoras14/scaffold-base

## Estructura

```
scaffold-base/
├── backend/     # API con FastAPI, gestionado con uv
└── frontend/    # SPA con React, TanStack Router/Query y Vite
```

## Backend (`backend/`)

| Categoría        | Tecnología                                    |
| ----------------- | ---------------------------------------------- |
| Lenguaje / runtime | Python >= 3.13                                 |
| Gestor de paquetes | [uv](https://docs.astral.sh/uv/)               |
| Framework web      | [FastAPI](https://fastapi.tiangolo.com/) (extra `standard`, incluye Uvicorn) |
| ORM / DB driver    | [SQLAlchemy](https://www.sqlalchemy.org/) + [psycopg](https://www.psycopg.org/) (PostgreSQL) |
| Validación / config| [Pydantic](https://docs.pydantic.dev/) + [pydantic-settings](https://docs.pydantic.dev/latest/concepts/pydantic_settings/) |
| Logging            | [loguru](https://github.com/Delgan/loguru)     |
| Seguridad          | [bcrypt](https://pypi.org/project/bcrypt/) (hashing de contraseñas) |
| Config por entorno | [python-dotenv](https://pypi.org/project/python-dotenv/) |

### Setup

```bash
cd backend
uv sync              # crea el venv e instala dependencias según uv.lock
uv run fastapi dev src/main.py   # servidor de desarrollo
```

### Actualizar dependencias a la última versión

```bash
cd backend
uv lock --upgrade    # recalcula uv.lock con las últimas versiones permitidas
uv sync              # instala lo que quedó en el lock actualizado

# actualizar uv mismo
uv self update
```

## Frontend (`frontend/`)

| Categoría          | Tecnología                                                     |
| ------------------- | ---------------------------------------------------------------- |
| Lenguaje / runtime   | TypeScript, Node.js                                             |
| Gestor de paquetes   | [pnpm](https://pnpm.io/)                                        |
| Build tool           | [Vite](https://vite.dev/)                                       |
| UI library           | [React 19](https://react.dev/)                                  |
| Routing              | [TanStack Router](https://tanstack.com/router) (+ devtools, generación de rutas con `tsr`) |
| Data fetching / cache| [TanStack Query](https://tanstack.com/query) (+ devtools)       |
| Estilos              | [Tailwind CSS v4](https://tailwindcss.com/) + [tw-animate-css](https://www.npmjs.com/package/tw-animate-css) |
| Componentes UI       | [shadcn](https://ui.shadcn.com/) sobre [Radix UI](https://www.radix-ui.com/) |
| Iconos               | [lucide-react](https://lucide.dev/)                              |
| Utilidades UI        | class-variance-authority, clsx, tailwind-merge                  |
| Validación de datos  | [Zod](https://zod.dev/)                                          |
| HTTP client          | [axios](https://axios-http.com/)                                 |
| Tipografía           | [@fontsource-variable/inter](https://fontsource.org/fonts/inter) |
| Lint / format        | [Biome](https://biomejs.dev/)                                    |

### Setup

```bash
cd frontend
pnpm install
pnpm dev              # http://localhost:3000
```

### Scripts disponibles

| Script              | Descripción                          |
| -------------------- | ------------------------------------- |
| `pnpm dev`            | levanta el servidor de desarrollo (Vite) |
| `pnpm build`          | build de producción                    |
| `pnpm preview`        | sirve el build de producción localmente|
| `pnpm generate-routes`| regenera las rutas de TanStack Router (`tsr generate`) |
| `pnpm format`         | formatea el código con Biome           |
| `pnpm lint`           | ejecuta el linter (Biome)              |
| `pnpm check`          | lint + format check con Biome          |

### Actualizar dependencias a la última versión

```bash
cd frontend
pnpm update --latest   # actualiza package.json y pnpm-lock.yaml a las últimas versiones
pnpm install            # asegura que node_modules quede sincronizado

# actualizar pnpm mismo
corepack use pnpm@latest
# o, si no usas corepack:
npm install -g pnpm@latest
```

> Nota: `latest` en `@tanstack/react-devtools`, `@tanstack/react-router`, `@tanstack/react-router-devtools`, `@tanstack/devtools-vite` y `@tanstack/router-plugin` ya apunta siempre a la versión más reciente publicada; `pnpm update --latest` de todos modos las revalida junto con el resto.
