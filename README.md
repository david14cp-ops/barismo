# Carnet de Syrups Medellín — Cold Brew Sin Alcohol

App de una sola página (HTML/CSS/JS), instalable como PWA (Progressive Web App),
lista para publicar en GitHub Pages.

## Contenido del proyecto

```
├── index.html        ← la app completa (recetas, calculadora, diseñador de mocktails)
├── manifest.json      ← metadatos de instalación (nombre, colores, íconos)
├── sw.js               ← service worker (funcionamiento sin conexión)
└── icons/              ← íconos en todos los tamaños necesarios
```

## 1. Súbelo a GitHub

1. Crea una cuenta en https://github.com si no tienes una.
2. Crea un repositorio nuevo:
   - Ve a https://github.com/new
   - Nombre sugerido: `syrups-medellin` (o el que prefieras)
   - Déjalo en **Public** (los repos privados también sirven con GitHub Pages,
     pero requieren plan de pago para eso; Public es gratis)
   - No marques "Add a README" (ya tienes uno)
   - Clic en **Create repository**

3. Sube los archivos. Tienes dos formas:

   **Opción A — Sin usar la terminal (más fácil):**
   - En la página del repo recién creado, clic en **"uploading an existing file"**
   - Arrastra toda la carpeta (o los archivos `index.html`, `manifest.json`, `sw.js`,
     `README.md` y la carpeta `icons/` completa) a la zona de carga
   - Escribe un mensaje de commit, ej: "Primera versión de la app"
   - Clic en **Commit changes**

   **Opción B — Con Git en la terminal:**
   ```bash
   cd carpeta-donde-descomprimiste-el-zip
   git init
   git add .
   git commit -m "Primera versión de la app"
   git branch -M main
   git remote add origin https://github.com/TU-USUARIO/syrups-medellin.git
   git push -u origin main
   ```

## 2. Activa GitHub Pages

1. En tu repositorio, ve a **Settings** (⚙️, arriba a la derecha).
2. En el menú lateral izquierdo, clic en **Pages**.
3. En **Source**, selecciona **Deploy from a branch**.
4. En **Branch**, elige `main` y la carpeta `/ (root)`.
5. Clic en **Save**.
6. Espera 1-2 minutos. GitHub te mostrará la URL pública, algo como:
   ```
   https://TU-USUARIO.github.io/syrups-medellin/
   ```
   Refresca la página de Settings > Pages si no aparece de inmediato.

¡Listo! Tu app ya está publicada y accesible desde cualquier navegador.

## 3. Instalarla como aplicación (PWA)

La app ya incluye todo lo necesario (`manifest.json`, `sw.js` e íconos) para
que el navegador ofrezca instalarla como si fuera una app nativa.

**Importante:** la instalación como PWA solo funciona sobre **HTTPS**
(GitHub Pages ya sirve todo por HTTPS automáticamente, así que no tienes que
hacer nada extra) — no funciona abriendo el `index.html` directamente desde
tu computador con doble clic (`file://`).

### En Android (Chrome)
1. Abre la URL de GitHub Pages en Chrome.
2. Aparecerá un banner "Agregar Carnet de Syrups Medellín a la pantalla de inicio",
   o toca el menú (⋮) → **Instalar aplicación**.
3. Confirma. Quedará un ícono en tu pantalla de inicio, igual que cualquier app.

### En iPhone/iPad (Safari)
1. Abre la URL en Safari (debe ser Safari, no Chrome, para esta función en iOS).
2. Toca el botón de compartir (el cuadrado con la flecha hacia arriba).
3. Baja hasta **"Agregar a pantalla de inicio"**.
4. Confirma el nombre y toca **Agregar**.

### En computador (Windows/Mac/Linux, Chrome o Edge)
1. Abre la URL.
2. A la derecha de la barra de direcciones aparecerá un ícono de instalación
   (una pantalla con una flecha ⬇, o "Instalar Syrups Medellín").
3. Clic en **Instalar**. Se abrirá como ventana propia, con su ícono en el
   menú de aplicaciones / escritorio.

## 4. Actualizar la app después de publicada

Cada vez que quieras cambiar una receta o el diseño:
1. Edita `index.html` (o los archivos que necesites).
2. Vuelve a subir los cambios a GitHub (arrastrando el archivo actualizado en
   la web de GitHub, o con `git add . && git commit -m "actualización" && git push`).
3. GitHub Pages se actualiza solo en 1-2 minutos.
4. El Service Worker (`sw.js`) usa una caché con nombre `syrups-medellin-v1`.
   Si haces cambios grandes y quieres forzar que todos los usuarios reciban
   la versión nueva de inmediato, sube el número de versión en `sw.js`
   (por ejemplo `syrups-medellin-v2`) — así el navegador descarta la caché vieja.

## 5. Cambiar el ícono más adelante (opcional)

Los íconos están en `icons/`. Si quieres reemplazarlos por tu propio logo:
- Genera tu imagen en al menos 512×512 px, fondo cuadrado (sin transparencia
  para los íconos "maskable").
- Reemplaza los archivos manteniendo los mismos nombres y tamaños que ya
  están en `manifest.json` (`icon-192.png`, `icon-512.png`, etc.), o actualiza
  las rutas en `manifest.json` si usas nombres distintos.
