# Publicar la calculadora en GitHub Pages

Guía paso a paso. Sin terminal, sin git instalado, todo desde el navegador.

---

## 1. Crear cuenta de GitHub (si no tenés)

1. Andá a https://github.com/signup
2. Registrate con tu email y contraseña
3. Verificá el email (te llega un código)

---

## 2. Crear un repositorio nuevo

1. Una vez logueado, hacé click en el **`+`** arriba a la derecha → **"New repository"**
2. Configurá así:
   - **Repository name**: `calculadora-mudanzas` (o el nombre que quieras — solo letras, números y guiones)
   - **Description**: opcional, podés poner "Calculadora de precios de mudanzas"
   - **Public** ✅ (debe ser público para que GitHub Pages funcione gratis)
   - **No marques** "Add a README", "Add .gitignore" ni "Choose a license"
3. Click en **"Create repository"**

---

## 3. Subir los archivos (drag & drop)

Ahora estás en el repo vacío. GitHub te muestra una página con instrucciones.

1. Buscá el link que dice **"uploading an existing file"** (en el medio de la página, en la sección "Quick setup")
2. O andá directo a `https://github.com/TU-USUARIO/calculadora-mudanzas/upload/main`
3. **Arrastrá los 6 archivos** de la carpeta `calculadora-pwa` a la zona punteada:
   - `index.html`
   - `manifest.json`
   - `service-worker.js`
   - `icon.svg`
   - `icon-192.png`
   - `icon-512.png`
   - `README.md` (opcional, no afecta a la PWA)
4. Bajá al final de la página
5. En "Commit changes" dejá el mensaje por defecto y click en **"Commit changes"**

Esperá unos segundos. Cuando termina, ves los archivos listados en el repo.

---

## 4. Activar GitHub Pages

1. En tu repo, click en la pestaña **"Settings"** (arriba a la derecha)
2. En el menú lateral izquierdo, click en **"Pages"**
3. En la sección **"Build and deployment"**:
   - **Source**: dejá "**Deploy from a branch**"
   - **Branch**: seleccioná **`main`** (o `master` si te aparece así) y carpeta **`/ (root)`**
   - Click **"Save"**
4. Aparece un mensaje "Your site is live at..." con la URL — **puede tardar 1-2 minutos en aparecer la primera vez**

---

## 5. Acceder a tu app

Tu URL va a ser:

```
https://TU-USUARIO.github.io/calculadora-mudanzas/
```

(Reemplazá `TU-USUARIO` por tu nombre de usuario de GitHub y `calculadora-mudanzas` por el nombre que le pusiste al repo).

Refrescá la página después de 1-2 minutos. Si no aparece, esperá un poco más — la primera vez tarda.

---

## 6. Instalar la PWA desde la URL

Ya con tu URL HTTPS pública, podés instalarla:

**Android (Chrome)**: abrí la URL → tocá los 3 puntos → "Instalar app" / "Añadir a pantalla de inicio"

**iPhone (Safari)**: abrí la URL en Safari → tocá Compartir → "Añadir a pantalla de inicio"

**Computadora (Chrome/Edge)**: abrí la URL → click en el ícono de instalar en la barra de direcciones (arriba a la derecha)

---

## Actualizar la app después

Cuando quieras cambiar algo (tarifas, diseño, etc.):

1. Edití el archivo localmente
2. Andá al repo en GitHub
3. Click en el archivo (ej: `index.html`)
4. Click en el ícono del lápiz (✏️) arriba a la derecha para editar online, **O** click en el botón **"Add file"** → **"Upload files"** para reemplazar
5. Hacé los cambios y commit
6. GitHub Pages se actualiza automáticamente en 1-2 minutos
7. **Importante**: si los usuarios ya tienen la PWA instalada, para que vean los cambios:
   - Abrí `service-worker.js`, cambiá `'mudanzas-v1'` por `'mudanzas-v2'` (o el siguiente número)
   - Subí el archivo. La próxima vez que abran la app, recibe los cambios.

---

## Problemas comunes

**"404 Page not found" al entrar a la URL**
- Esperá 2-3 minutos, la primera vez tarda
- Verificá que activaste Pages en Settings → Pages
- La rama tiene que ser `main` (o `master`) y carpeta `/ (root)`

**"Your site is live" no aparece**
- Refrescá la página de Settings → Pages
- Asegurate de que el repo es **Public**, no Private

**La PWA no ofrece instalación**
- Tiene que abrirse desde la URL HTTPS de GitHub Pages, no desde un archivo local
- En iPhone solo funciona desde Safari
- Cerrá y volvé a abrir la página

**Cambié algo pero no se ve**
- Esperá 1-2 minutos al deploy de GitHub
- Refrescá con Ctrl+Shift+R (Windows) o Cmd+Shift+R (Mac) para forzar
- Si tenés la PWA instalada, actualizá el `CACHE_NAME` del service worker como expliqué arriba

---

## Dominio propio (opcional)

Si tenés un dominio comprado (ej: `tuempresa.com`), podés conectarlo:

1. En Settings → Pages → **Custom domain** → escribí tu dominio
2. En el panel de tu proveedor de dominio (GoDaddy, Namecheap, etc.), agregá un registro **CNAME** apuntando a `TU-USUARIO.github.io`
3. Esperá unos minutos para que propague

URL final: `https://tuempresa.com/calculadora-mudanzas/`
