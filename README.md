# Calculadora de Mudanzas — PWA

App web instalable. Se ve y funciona como una app nativa, pero es una página web.

## Archivos

```
calculadora-pwa/
├── index.html         (la calculadora completa)
├── manifest.json      (metadata de la app: nombre, ícono, color)
├── service-worker.js  (cache offline)
├── icon.svg           (ícono vectorial)
├── icon-192.png       (ícono 192×192)
└── icon-512.png       (ícono 512×512)
```

---

## Publicarla online en 2 minutos (Netlify Drop)

Para que sea instalable desde el celular necesitás una URL HTTPS. La forma más rápida y gratis:

### Pasos

1. Andá a **https://app.netlify.com/drop**
2. **Arrastrá la carpeta `calculadora-pwa` completa** a la página (literalmente, arrastrá y soltá)
3. Netlify te da una URL del estilo `https://nombre-random.netlify.app` — esa es tu app
4. (Opcional) Crear cuenta gratis para reclamar el sitio y darle un nombre custom

Listo. La PWA queda online, gratis, con HTTPS, sin tarjeta.

---

## Cómo instalarla en el teléfono

### Android (Chrome)

1. Abrí la URL en Chrome
2. Aparece automáticamente un banner "**Instalar app**" abajo
3. Si no aparece, tocá los **3 puntos** arriba a la derecha → "**Instalar app**" o "**Añadir a pantalla de inicio**"
4. Confirmá. Queda como un ícono más en la pantalla de inicio
5. Al abrirla, va sin barra de navegador, como app nativa

### iPhone (Safari)

1. Abrí la URL en Safari (no Chrome — Apple solo permite instalar PWAs desde Safari)
2. Tocá el botón **Compartir** (cuadrado con flecha arriba)
3. Bajá y tocá **"Añadir a pantalla de inicio"**
4. Confirmá

### Computadora (Chrome/Edge)

1. Abrí la URL
2. En la barra de direcciones, arriba a la derecha, aparece un ícono de instalar (+ o pantalla)
3. Click → "**Instalar**"
4. Queda en el escritorio / menú de inicio como una app

---

## Otras opciones de hosting gratuito

Si no querés Netlify:

- **Vercel** — https://vercel.com → "Add new" → arrastrar la carpeta
- **GitHub Pages** — subir los archivos a un repo público, activar Pages en Settings
- **Cloudflare Pages** — https://pages.cloudflare.com

Todos son gratis y dan HTTPS automático.

---

## Probarla local (sin publicar)

Si solo querés ver la app antes de publicarla:

1. Abrí `index.html` con doble click → se abre en el navegador
2. **Pero**: el service worker (offline) y la opción de instalar solo funcionan desde HTTPS. Localmente la página se ve y calcula bien, pero no podés instalarla.

Para probar instalación local podés correr un servidor con Python:

```bash
cd calculadora-pwa
python3 -m http.server 8000
```

Y abrir http://localhost:8000 — Chrome permite instalar desde localhost.

---

## Cómo se ven los cambios

Si modificás `index.html`, subí los archivos a Netlify de nuevo (drag & drop sobre el sitio existente). Los usuarios ya instalados van a recibir la versión nueva la próxima vez que abran la app — el service worker se actualiza solo.

Si querés forzar la actualización inmediatamente, cambiá la línea `const CACHE_NAME = 'mudanzas-v1';` en `service-worker.js` a `mudanzas-v2`, `v3`, etc. cada vez que hagas cambios.

---

## Personalización rápida

- **Nombre de la app**: editá `name` y `short_name` en `manifest.json`
- **Color de tema**: cambiá `theme_color` en `manifest.json` y el `<meta name="theme-color">` en `index.html`
- **Ícono**: reemplazá `icon.svg`, `icon-192.png` y `icon-512.png` con tus archivos (mismo nombre, mismo tamaño)
- **Tarifas**: están en `index.html`, al inicio del bloque `<script>` — `LABOR_BY_MOVERS`, `TRUCK_CONFIGS`, `LONG_PER_MILE`, etc.
