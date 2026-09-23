# <img src="assets/img/favicon.svg" width="28" height="28" alt=""> Web de boda — Juan & Lucía

Web de una sola página (sin navegación entre páginas) para la boda de Juan y
Lucía, el **15 de agosto de 2027** en Robledo de Chavela (Madrid).

Es HTML/CSS/JS puro (sin frameworks ni build), así que se puede publicar tal
cual en GitHub Pages, Netlify, Vercel o cualquier hosting estático.

## Estructura

```
index.html        página única con todas las secciones
css/style.css      estilos
js/main.js         cuenta atrás, menú, galería, lightbox
assets/img/        fotos e ilustraciones (ya optimizadas para web)
```

Secciones de la página (con ancla, por si quieres enlazar directamente a una):
`#inicio`, `#la-boda`, `#alojamiento`, `#dress-code`, `#regalo`, `#rsvp`,
`#galeria`.

## Publicar en GitHub Pages

1. Ve a **Settings → Pages** en este repositorio.
2. En "Build and deployment", elige **Deploy from a branch**.
3. Selecciona la rama (`main` o la que uses) y la carpeta `/ (root)`.
4. Guarda. En un par de minutos la web estará en
   `https://<tu-usuario>.github.io/Web-Boda-J-L/`.

Si más adelante compráis un dominio propio (p. ej. `juanylucia.com`), podéis
añadirlo también en esa misma pantalla de Settings → Pages.

## Formulario de confirmación (RSVP)

La sección `#rsvp` incrusta un **Google Form** dentro de la propia página
mediante un `<iframe>` (en `index.html`, dentro de `.rsvp-embed`). Se eligió
Google Forms en vez de un servicio tipo Formspree porque, con ~180
invitados, el plan gratuito de la mayoría de esos servicios tiene un límite
mensual de envíos que se podría superar si las respuestas llegan agrupadas
(justo después de enviar las invitaciones, o cerca de la fecha límite).
Google Forms no tiene ese límite, y las respuestas se pueden vincular a una
hoja de Google Sheets para consultarlas fácilmente.

Para cambiar las preguntas del formulario, o consultar las respuestas, se
edita directamente desde el propio Google Forms (no hace falta tocar el
código). Si en algún momento se crea un formulario nuevo, hay que sustituir
dos cosas en `index.html`:

```html
<iframe src="https://docs.google.com/forms/d/e/TU-ID-DE-FORMULARIO/viewform?embedded=true" ...>
```

y el enlace de "Ábrelo en una pestaña aparte" (el `forms.gle` corto que
genera el propio Google Forms al pulsar "Enviar").

## Cosas que os pueden interesar personalizar

- **Hoteles recomendados** — la sección "Alojamiento" tiene de momento un
  aviso de "Próximamente". Cuando tengáis la lista, editad el bloque
  `#alojamiento` en `index.html` (segunda `.info-card`) y sustituid el
  `<span class="badge">Próximamente</span>` por los hoteles/enlaces que
  queráis.
- **Datos para transferencia** (sección "Regalo") — sustituid el IBAN de
  ejemplo (`ESXX XXXX...`) por el real, y el nombre/teléfono de contacto
  para sorpresas si cambia.
- **Fotos** — todas están en `assets/img/`. Puedes añadir o cambiar
  cualquiera; solo actualiza la ruta correspondiente en `index.html` (hero,
  "La boda", galería, etc.). Se recomienda que no pesen más de ~500 KB cada
  una para que la web cargue rápido en el móvil.
- **Fecha límite de confirmación** — aparece en la sección RSVP
  ("antes del 15 de junio de 2027"); cambiadla en `index.html` si hace falta.

## Desarrollo local

No hace falta ningún paso de build. Basta con abrir `index.html` en el
navegador, o levantar un servidor local sencillo:

```bash
python3 -m http.server 8000
```

y visitar `http://localhost:8000`.
