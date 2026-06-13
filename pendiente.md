# Tareas Pendientes — Aprendamos Juntos

> Última revisión: 13 de junio de 2026.

---

## 🔴 Prioridad alta — Bloquean la publicación

### 1. Número de WhatsApp real
Facebook y TikTok ya fueron actualizados. Falta solo el número de WhatsApp, que aparece en **dos lugares**:

| Elemento | Línea aprox. | Qué cambiar |
|---|---|---|
| Botón CTA principal (sección contacto) | 678 | `wa.me/0000000000` → número real con código de país |
| Botón flotante verde | 721 | mismo cambio |

Ejemplo: `https://wa.me/573001234567?text=Hola,%20quiero%20información%20sobre%20el%20refuerzo%20escolar`

---

### 2. ⚠️ Emails rotos fuera de Cloudflare
El archivo actual tiene los emails obfuscados por Cloudflare (`/cdn-cgi/l/email-protection#...`). Esto funciona **solo si el sitio está servido a través del proxy de Cloudflare**. En Firebase Hosting sin Cloudflare delante, los enlaces de email aparecerán como `[email protected]` o no funcionarán.

**Solución:** reemplazar los dos `href="/cdn-cgi/l/email-protection#..."` y los `<span class="__cf_email__">` por el email en texto plano:

```html
<a href="mailto:aprendiendojuntostallertareas@gmail.com">
  aprendiendojuntostallertareas@gmail.com
</a>
```

Afecta la sección CTA (línea ~681) y el footer (línea ~711).

---

### 3. Configuración de Firebase Hosting
No existe ningún archivo de configuración. Sin esto no se puede desplegar.

- [ ] Crear `firebase.json`
- [ ] Crear `.firebaserc` con el ID del proyecto
- [ ] (Opcional) Crear `404.html`

**`firebase.json` mínimo listo para usar:**
```json
{
  "hosting": {
    "public": ".",
    "ignore": ["firebase.json", "**/.*", "handoff_extracted/**", "*.md", "skills-lock.json"],
    "headers": [
      {
        "source": "assets/**",
        "headers": [{ "key": "Cache-Control", "value": "public, max-age=31536000, immutable" }]
      },
      {
        "source": "index.html",
        "headers": [{ "key": "Cache-Control", "value": "no-cache" }]
      }
    ]
  }
}
```

---

## 🟠 Prioridad media — SEO y visibilidad

### 4. Metaetiquetas SEO y Open Graph
Sin estas etiquetas el sitio no aparece bien en Google ni en las vistas previas al compartir el enlace por WhatsApp o Facebook.

Agregar dentro del `<head>`, reemplazando `TU-DOMINIO` con la URL real de Firebase:

```html
<meta name="description" content="Refuerzo y nivelación escolar con amor y dedicación. Lectura, Matemáticas, tareas y más. Planes desde $100.000.">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://TU-DOMINIO.web.app/">

<meta property="og:type" content="website">
<meta property="og:locale" content="es_CO">
<meta property="og:title" content="Aprendamos Juntos — Refuerzo y Nivelación Escolar">
<meta property="og:description" content="Acompañamos el aprendizaje de tus hijos con amor, paciencia y dedicación.">
<meta property="og:url" content="https://TU-DOMINIO.web.app/">
<meta property="og:image" content="https://TU-DOMINIO.web.app/assets/og-image.jpg">
```

La imagen OG (`og-image.jpg`) debe ser de al menos **1200 × 630 px** — se puede usar una captura de pantalla del hero del sitio.

### 5. Favicon
No hay ícono en la pestaña del navegador.

```html
<!-- pegar en el <head> -->
<link rel="icon" type="image/png" href="assets/favicon.png">
<link rel="apple-touch-icon" href="assets/apple-touch-icon.png">
```

Tamaños necesarios: `favicon.png` (32 × 32 px) y `apple-touch-icon.png` (180 × 180 px). Se puede generar desde el ícono del corazón del logo.

---

## 🟢 Prioridad baja — Mejoras opcionales

### 6. Preload de la imagen hero
Agrega esta línea en el `<head>` para que el navegador cargue la foto antes de procesar el CSS:

```html
<link rel="preload" as="image" href="assets/hero.webp" type="image/webp">
```

### 7. Medición y analítica
Sin analítica no hay forma de saber cuántas personas visitan el sitio.

- [ ] Activar Google Analytics 4 o Firebase Analytics en la consola de Firebase.
- [ ] Agregar el snippet de seguimiento al `<head>`.
- [ ] Configurar conversiones para los clics en los botones de WhatsApp.

### 8. Política de privacidad
Si se activa Analytics se recopilan datos. Recomendado agregar al menos una sección o página simple.

---

## Resumen de estado

| # | Tarea | Prioridad | Estado |
|---|---|---|---|
| 1 | Número de WhatsApp real | 🔴 Alta | Pendiente |
| 2 | Emails rotos fuera de Cloudflare | 🔴 Alta | ✅ Completado |
| 3 | Configuración Firebase Hosting | 🔴 Alta | Pendiente |
| 4 | Metaetiquetas SEO y Open Graph | 🟠 Media | Pendiente |
| 5 | Favicon | 🟠 Media | Pendiente |
| 6 | Preload imagen hero | 🟢 Baja | Pendiente |
| 7 | Google Analytics / Firebase Analytics | 🟢 Baja | Pendiente |
| 8 | Política de privacidad | 🟢 Baja | Pendiente |
| — | Facebook y TikTok | — | ✅ Completado |
| — | Email de contacto en CTA y footer | — | ✅ Completado |
| — | Tarjeta Nivelación en Matemáticas | — | ✅ Completado |
| — | Menú hamburguesa para móvil | — | ✅ Completado |
| — | Botones sociales flotantes en móvil | — | ✅ Completado |
