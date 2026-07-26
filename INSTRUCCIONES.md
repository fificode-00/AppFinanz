# Mis Finanzas — Guía de instalación

Esta versión de tu app ya **no depende de Claude**: es una PWA (Progressive Web App) que corre 100% en tu iPhone, con tus datos guardados solo en tu teléfono (localStorage). El registro rápido por voz/texto usa la **API gratuita de Google Gemini**.

Archivos incluidos: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`.

---

## 1. Conseguí tu API key gratis de Gemini

1. Andá a **aistudio.google.com/apikey**.
2. Iniciá sesión con una cuenta de Google.
3. Tocá **"Create API key"**.
4. Copiá la clave (empieza con `AIza...`). Guardala en un lugar seguro.

No pide tarjeta de crédito. El límite gratuito diario (~1.000-1.500 solicitudes/día) es muchísimo más de lo que vas a usar en un registro personal de gastos.

---

## 2. Subí la app a internet gratis (GitHub Pages)

Para instalarla como app real en el iPhone, necesita una dirección web (https://...).

1. Creá una cuenta gratis en **github.com**.
2. Tocá **"+"** (arriba a la derecha) → **"New repository"**.
3. Ponele un nombre (ej: `mis-finanzas`), dejalo en **Public**, y creá el repositorio.
4. Dentro del repo: **"Add file" → "Upload files"**.
5. Arrastrá los 5 archivos: `index.html`, `manifest.json`, `service-worker.js`, `icon-192.png`, `icon-512.png`.
6. **"Commit changes"**.
7. **Settings** (del repo) → **Pages** (menú izquierdo).
8. En "Source" elegí **"Deploy from a branch"**, branch `main`, carpeta `/ (root)`. Guardar.
9. Esperá 1-2 minutos. Tu app queda en:
   `https://TU-USUARIO.github.io/mis-finanzas/`

> ⚠️ El repositorio y el sitio quedan **públicos** (es la única forma gratuita en GitHub). Por eso esta versión no trae tus cifras reales — las cargás vos la primera vez que abrís la app, y quedan guardadas **solo en tu iPhone**, nunca en GitHub. No compartas el link públicamente.

---

## 3. Instalala en tu iPhone como app

1. Abrí la URL de tu app en **Safari** (tiene que ser Safari, no Chrome).
2. Tocá el botón de compartir (cuadrado con flecha hacia arriba).
3. **"Agregar a pantalla de inicio"**.
4. Ya tenés un ícono como cualquier app, se abre a pantalla completa y funciona sin conexión.

---

## 4. Configurá tu API key dentro de la app

1. Abrí la app → ícono **⚙️** (arriba a la derecha).
2. Pegá tu API key de Gemini.
3. **Guardar**.

---

## 5. Cargá tus datos reales

Usá "+ Actualizar saldo", "+ Agregar deuda", "+ Nueva meta", etc. en cada sección. Todo queda guardado en tu teléfono.

---

## 6. Usá el registro rápido con IA

1. Tocá el botón **⚡** flotante (abajo a la derecha, en cualquier pantalla).
2. Escribí o **dictá** (tocá el micrófono 🎤 del teclado de iOS) algo como:
   - *"gasté 15 mil en almuerzo"*
   - *"pagué 20000 de transporte"*
   - *"me pagaron 50 mil de un trabajo"*
3. Tocá **"Registrar con IA"**. Identifica monto, categoría, y si es gasto o ingreso, y lo agrega solo.

---

## 7. Recordatorio diario con Atajos (gratis, nativo de iOS)

iOS no permite que ninguna app lea notificaciones de otras apps — ni siquiera Atajos. Lo que sí es 100% nativo y gratuito es un recordatorio propio:

1. Abrí **Atajos** → pestaña **Automatización** → **"+"** → **"Crear automatización personal"**.
2. Elegí **Hora del día**, poné la hora que prefieras, "Diario". Siguiente.
3. **"Agregar acción"** → buscá **"Mostrar notificación"** → escribí algo como *"¿Registraste tus gastos hoy? 💸"*.
4. (Opcional) Agregá **"Abrir URLs"** con el link de tu app, para que al tocar la notificación se abra directo.
5. Desactivá **"Preguntar antes de ejecutar"**.

Todos los días a esa hora vas a recibir una notificación nativa, sin costo.

---

## Cosas importantes que hay que saber

- **Los datos son solo de este dispositivo.** No hay backend ni sincronización entre teléfonos.
- **La API key queda guardada en tu iPhone** (localStorage). El riesgo de exposición es bajo para uso personal, pero no compartas el link de tu app.
- **iOS nunca va a permitir** leer notificaciones de tu banco automáticamente — es una restricción de Apple para todas las apps y automatizaciones, no algo que se pueda evitar.
- Si en el futuro Google descontinúa el modelo `gemini-2.5-flash`, solo hay que cambiar ese nombre por otro modelo vigente en una línea del código (`index.html`, dentro de `parseConIA`). La lista de modelos disponibles siempre está en aistudio.google.com.
