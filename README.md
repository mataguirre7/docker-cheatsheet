# 🐳 Docker Cheatsheets

Cheatsheets de Docker en español, pensadas para quien empieza: cada página explica sus términos y hay una guía para pasar de cero a una app propia en un contenedor. Incluyen diagramas, comandos con buscador, botón copiar y tema claro/oscuro.
Sitio 100 % estático (HTML + CSS + JS, sin build ni dependencias).

| Hoja | Contenido |
|---|---|
| `index.html` | Portada, orden recomendado, buscador “Quiero…” y descargas en PNG |
| `00-empezar.html` | Instalar Docker Desktop, verificar, primer contenedor y tu propia imagen, paso a paso |
| `01-conceptos.html` | Imagen vs contenedor, ciclo de vida, puertos, redes y volúmenes |
| `02-comandos.html` | CLI completa: imágenes, contenedores, `run`, logs, `exec`, redes, volúmenes, limpieza |
| `03-dockerfile.html` | Instrucciones, capas y caché, Node prod/dev, multi-stage .NET, `.dockerignore` |
| `04-compose.html` | Comandos, claves del YAML, compose de producción y desarrollo, `.env`, varios servicios |
| `05-problemas.html` | Errores comunes con causa y solución |

## Estructura

```
docker-cheatsheets/
├── index.html, 01-…05-*.html   # páginas
├── 404.html                    # página de error (Netlify la usa sola)
├── assets/
│   ├── style.css               # estilos y temas
│   └── app.js                  # navegación, buscador, copiar, resaltado
├── img/                        # cada hoja exportada a PNG (oscuro y claro)
└── netlify.toml                # config de deploy
```

## Verlo en local

Doble clic en `index.html` funciona. Para probarlo igual que en Netlify (rutas absolutas del 404, portapapeles):

```bash
python -m http.server 8080
```

y abrí <http://localhost:8080>.

## Subir a GitHub

1. Creá un repositorio **vacío** en <https://github.com/new> (sin README ni .gitignore), por ejemplo `docker-cheatsheets`.
2. Desde esta carpeta:

```bash
git remote add origin https://github.com/<tu-usuario>/docker-cheatsheets.git
git push -u origin main
```

## Publicar en Netlify

1. <https://app.netlify.com> → **Add new site → Import an existing project → GitHub**.
2. Elegí el repo `docker-cheatsheets`.
3. Dejá **Build command** vacío y **Publish directory** en `.` (ya lo define `netlify.toml`).
4. **Deploy**. Cada `git push` a `main` vuelve a publicar solo.
5. Opcional: **Site configuration → Change site name** para tener `docker-cheatsheets.netlify.app` (si está libre).

## Enlazar con las cheatsheets de Kubernetes

En `assets/app.js`, completá la URL del sitio hermano y aparece el botón en la barra:

```js
other: { label: "Kubernetes", href: "https://<tu-sitio-kubernetes>.netlify.app/", icon: "helm" },
```

## Editar contenido

- Cada página es HTML plano: agregá tarjetas copiando una existente (`<div class="card t-cont">…</div>`).
- Los bloques `<pre><code>` se resaltan y reciben el botón copiar solos. `data-lang="yaml"`, `"dockerfile"` o `"plain"` cambia el resaltado (por defecto, shell).
- Los valores a reemplazar se escriben como `&lt;nombre&gt;` y se ven en rosa.
- Las imágenes de `img/` **no se regeneran solas**: si cambiás una hoja, volvé a exportarla (por ejemplo, con la captura de página completa de las DevTools del navegador, abriendo la hoja con `?theme=dark` o `?theme=light`).
