# Tareas Pendientes — Aprendamos Juntos

> Última revisión: 13 de junio de 2026.

---

## 🔴 Prioridad alta — Bloquean la publicación

### 1. Número de WhatsApp real
El número aparece en **dos lugares** con el placeholder `0000000000`:

| Elemento | Línea aprox. | Qué cambiar |
|---|---|---|
| Botón CTA principal (sección contacto) | 701 | `wa.me/0000000000` → número real con código de país |
| Botón flotante verde (floating WA) | 744 | mismo cambio |

Ejemplo: `https://wa.me/573001234567?text=Hola,%20quiero%20información%20sobre%20el%20refuerzo%20escolar`

---

## 🟠 Prioridad media — SEO y visibilidad

### 2. Metaetiquetas SEO y Open Graph
Sin estas etiquetas el sitio no aparece bien en Google ni en las vistas previas al compartir el enlace por WhatsApp o Facebook.

Agregar dentro del `<head>`, reemplazando `TU-DOMINIO` con la URL real de Firebase:

```html
<meta name="description" content="Refuerzo y nivelación escolar con amor y dedicación. Lectura, Matemáticas, Maquetas y más. Planes desde $100.000.">
<meta name="robots" content="index, follow">
<link rel="canonical" href="https://TU-DOMINIO.web.app/">

<meta property="og:type" content="website">
<meta property="og:locale" content="es_CO">
<meta property="og:title" content="Aprendamos Juntos — Refuerzo y Nivelación Escolar">
<meta property="og:description" content="Acompañamos el aprendizaje de tus hijos con amor, paciencia y dedicación.">
<meta property="og:url" content="https://TU-DOMINIO.web.app/">
<meta property="og:image" content="https://TU-DOMINIO.web.app/assets/og-image.jpg">
```

### 3. Imagen Open Graph (`assets/og-image.jpg`)
El archivo `assets/og-image.jpg` no existe. Es requerido para las vistas previas en WhatsApp, Facebook y Google.

Tamaño mínimo: **1200 × 630 px**. Se puede generar con una captura del hero redimensionada.

---

## 🟢 Prioridad baja — Mejoras opcionales

### 4. Headers de caché en Firebase Hosting
El `firebase.json` actual es básico y no tiene headers de caché. Para mejorar el rendimiento en cargas repetidas:

```json
{
  "hosting": {
    "public": "public",
    "ignore": ["firebase.json", "**/.*", "*.md", "skills-lock.json"],
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

### 5. Preload de la imagen hero
Agrega esta línea en el `<head>` (antes de cualquier `<link>` de CSS) para que el navegador descargue la foto antes de procesar el HTML:

```html
<link rel="preload" as="image" href="assets/hero.webp" type="image/webp">
```

*Nota: el `<img>` ya tiene `loading="eager"`, pero el preload adelanta aún más la descarga.*

### 6. Medición y analítica
Sin analítica no hay forma de saber cuántas personas visitan el sitio.

- [ ] Activar Google Analytics 4 o Firebase Analytics en la consola de Firebase.
- [ ] Agregar el snippet de seguimiento al `<head>`.
- [ ] Configurar conversiones para los clics en los botones de WhatsApp.

### 7. Política de privacidad
Si se activa Analytics se recopilan datos. Recomendado agregar al menos una sección o página simple.

---

## Resumen de estado

| # | Tarea | Prioridad | Estado |
|---|---|---|---|
| 1 | Número de WhatsApp real | 🔴 Alta | Pendiente |
| 2 | Metaetiquetas SEO y Open Graph | 🟠 Media | Pendiente |
| 3 | Imagen OG (`assets/og-image.jpg`) | 🟠 Media | ✅ Completado |
| 4 | Headers de caché en `firebase.json` | 🟢 Baja | Pendiente |
| 5 | Preload imagen hero | 🟢 Baja | ✅ Completado |
| 6 | Google Analytics / Firebase Analytics | 🟢 Baja | Pendiente |
| 7 | Política de privacidad | 🟢 Baja | Pendiente |
| — | Facebook y TikTok | — | ✅ Completado |
| — | Emails rotos por Cloudflare (CTA + footer + script) | — | ✅ Completado |
| — | Tarjeta Nivelación en Matemáticas | — | ✅ Completado |
| — | Tarjeta Maquetas y Carteleras | — | ✅ Completado |
| — | Menú hamburguesa para móvil | — | ✅ Completado |
| — | Botones sociales flotantes en móvil | — | ✅ Completado |
| — | Configuración Firebase Hosting (`firebase.json`) | — | ✅ Completado |
| — | Favicon (SVG, PNG 32px, Apple Touch Icon 180px) | — | ✅ Completado |
