# CV Web Profesional con Astro

Sitio web tipo CV/perfil profesional personal, en espanol, orientado a reclutadores y responsables de contratacion del area TI, cloud, infraestructura y operaciones.

## Requisitos

- Node.js 20 o superior
- npm 10 o superior

## Instalacion

```bash
npm install
```

## Desarrollo local

```bash
npm run dev
```

## Build de produccion

```bash
npm run build
```

La salida estatica se genera en `dist/`.

## Deploy en Netlify

1. Conecta el repositorio en Netlify.
2. Configura:
   - Build command: `npm run build`
   - Publish directory: `dist`
   - Node version: `20`
3. Despliega.

Tambien puedes usar el archivo `netlify.toml` incluido.

## Edicion de contenido

Todo el contenido principal vive en `src/content/`:

- `profile.json`
- `experience.json`
- `education.json`
- `courses.json`
- `certifications.json`
- `skills.json`
- `contact.json`

Puedes actualizar textos, enlaces o bloques de informacion sin tocar los componentes visuales.
