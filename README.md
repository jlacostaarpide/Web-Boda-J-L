# Web de boda — Juan & Lucía 💍

Web de una sola página (sin navegación entre páginas) para la boda de Juan y
Lucía, el **15 de agosto de 2027** en Robledo de Chavela (Madrid).

Es HTML/CSS/JS puro (sin frameworks ni build), así que se puede publicar tal
cual en GitHub Pages, Netlify, Vercel o cualquier hosting estático.

## Estructura

```
index.html        página única con todas las secciones
css/style.css      estilos
js/main.js         cuenta atrás, menú, galería, formulario RSVP
assets/img/        fotos (ya optimizadas para web)
```

Secciones de la página (con ancla, por si quieres enlazar directamente a una):
`#inicio`, `#nosotros`, `#la-boda`, `#cuando-donde`, `#alojamiento`,
`#dress-code`, `#regalo`, `#galeria`, `#rsvp`.

## Publicar en GitHub Pages

1. Ve a **Settings → Pages** en este repositorio.
2. En "Build and deployment", elige **Deploy from a branch**.
3. Selecciona la rama (`main` o la que uses) y la carpeta `/ (root)`.
4. Guarda. En un par de minutos la web estará en
   `https://<tu-usuario>.github.io/Web-Boda-J-L/`.

Si más adelante compráis un dominio propio (p. ej. `juanylucia.com`), podéis
añadirlo también en esa misma pantalla de Settings → Pages.

## Activar el formulario de confirmación (RSVP)

El formulario de la web usa **[Formspree](https://formspree.io)**, un
servicio gratuito que envía por email lo que la gente rellena, sin necesidad
de programar ningún backend.

1. Entra en https://formspree.io y crea una cuenta gratuita.
2. Crea un formulario nuevo (New Form) y dale un nombre, p. ej. "RSVP boda".
3. Formspree te da una URL tipo `https://formspree.io/f/abcdwxyz`. Copia esa
   URL.
4. Abre `js/main.js` y busca esta línea, cerca del final del archivo:

   ```js
   var FORMSPREE_ENDPOINT = "https://formspree.io/f/REPLACE_ME";
   ```

   Sustituye `https://formspree.io/f/REPLACE_ME` por la URL que te ha dado
   Formspree.
5. Guarda, sube el cambio (`git add`, `git commit`, `git push`) y listo: cada
   confirmación que se rellene en la web os llegará por email.

Mientras no se rellene ese paso, el formulario muestra un aviso pidiendo
paciencia en vez de fallar en silencio.

> El plan gratuito de Formspree permite un número limitado de envíos al mes,
> más que suficiente para una boda. Si tenéis muchísimos invitados, revisad
> los límites del plan gratuito en su web.

## Cosas que os pueden interesar personalizar

- **Hoteles recomendados** — la sección "Alojamiento" tiene de momento un
  aviso de "Próximamente". Cuando tengáis la lista, editad el bloque
  `#alojamiento` en `index.html` (segunda `.info-card`) y sustituid el
  `<span class="badge">Próximamente</span>` por los hoteles/enlaces que
  queráis.
- **Datos para transferencia** (sección "Regalo") — si al final queréis
  añadir un IBAN o un enlace de Bizum, se puede añadir fácilmente en esa
  sección de `index.html`.
- **Fotos** — todas están en `assets/img/`. Puedes añadir o cambiar
  cualquiera; solo actualiza la ruta correspondiente en `index.html` (hero,
  historia, galería, etc.). Se recomienda que no pesen más de ~500 KB cada
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
