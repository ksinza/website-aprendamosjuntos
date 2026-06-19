# Landing Page — Aprendiendo Juntos

Documentación del estado actual del sitio web (`public/index.html`).

---

## Datos del proyecto

| Campo | Valor |
|---|---|
| Nombre del negocio | Aprendiendo Juntos |
| Tipo de negocio | Taller de refuerzo y nivelación escolar |
| Archivo principal | `public/index.html` |
| Hosting | Firebase Hosting (`public/` como raíz pública) |
| Dominio | https://www.aprendiendojuntostaller.com/ |
| Email de contacto | aprendiendojuntostallertareas@gmail.com |
| WhatsApp | `+57 317 017 1728` (enlace `wa.me/573170171728`) |
| Facebook | https://www.facebook.com/share/1EigzRYmUD/ |
| TikTok | https://www.tiktok.com/@aprendiendojuntostaller |

---

## Stack técnico

### Frontend
| Capa | Detalle |
|---|---|
| Markup | HTML5 semántico · sin framework |
| Estilos | CSS custom embebido en `<style>` · CSS custom properties · sin framework (no Tailwind, no Bootstrap) |
| Scripts | JavaScript vanilla inline · sin bundler (no Webpack, no Vite) |
| Fuentes | Google Fonts CDN: **Fredoka**, **Nunito**, **Yellowtail** |
| Iconos | SVG inline optimizados · sin librerías externas |
| Imágenes | `.webp` para hero · `.png` / `.svg` para favicons y PWA |

### Infraestructura y deploy
| Capa | Detalle |
|---|---|
| Hosting | **Firebase Hosting** · carpeta pública `public/` |
| CI/CD | **GitHub Actions** · deploy automático en merge a `main` + preview en PRs |
| Workflows | `.github/workflows/firebase-hosting-merge.yml` · `.github/workflows/firebase-hosting-pull-request.yml` |
| Config Firebase | `firebase.json` · `public/` como raíz · sin rewrites ni redirects |

### Sin dependencias de build
No hay `package.json`, no hay `node_modules`, no hay paso de compilación. El sitio se sirve directamente desde HTML/CSS/JS estáticos.

---

## Sistema de diseño

### Paleta de colores

| Variable CSS | Valor | Uso |
|---|---|---|
| `--cream` | `#FDF5F1` | Fondo general del cuerpo |
| `--cream-card` | `#FFFDFC` | Fondo de tarjetas |
| `--ink` | `#4a3a6b` | Texto principal |
| `--ink-soft` | `#6f6189` | Texto secundario y descriptivo |
| `--pink` | `#E5388B` | Color de acento / CTA principal |
| `--pink-deep` | `#D11A75` | Hover de botones rosas |
| `--pink-soft` | `#FAD4E5` | Fondos suaves rosas |
| `--purple` | `#6E4FB8` | Color institucional / pill headers |
| `--purple-deep` | `#5a3da3` | Títulos y marca |
| `--purple-soft` | `#E6DCF7` | Fondos suaves púrpura |
| `--teal` | `#239B9B` | Lema hero / plan mensual |
| `--teal-deep` | `#1c8585` | Hover teal |
| `--teal-soft` | `#CFEBEB` | Fondo icono teal |
| `--yellow` | `#F4C740` | Estrellas decorativas |
| *(sin variable)* | `#FCE3D4` / `#C2410C` | Fondo y texto de tarjeta "Maquetas y Carteleras" (clase `.o`) |

### Tipografía

| Fuente | Uso |
|---|---|
| **Fredoka** | Títulos (`h1`–`h4`), botones, nav brand, pill headers |
| **Nunito** | Cuerpo de texto, descripciones |
| **Yellowtail** | Display hero (`.l2`, `.l3` del `h1`) y frase de cierre |

---

## Estructura de secciones

### 1. Nav (sticky)
- Logo + nombre de marca "Aprendiendo Juntos" con badge de corazón
- Links internos: Servicios · Tarifas · Beneficios · Contacto
- Iconos de Facebook y TikTok (escritorio, ocultos en < 560px)
- Botón "Escríbeme" → `#contacto`
- Menú hamburguesa responsive (visible en < 960px), animación 3 líneas → X

### 2. Hero (`#inicio`)
- Eyebrow: "Acompañamiento escolar"
- Título en tres líneas: "Refuerzo y" / "Nivelación" / "Escolar"
- Lema en fondo teal: "Acompañamos el aprendizaje de tus hijos con amor, paciencia y dedicación ♥"
- CTAs: "Quiero más información" (pink, → `#contacto`) + "Ver tarifas" (ghost, → `#tarifas`)
- Stickynote decorativa (amarilla, rotada -6°): "Enseñar es inspirar y acompañar para crecer"
- Imagen: `assets/hero.webp` (600×480, `loading="eager"`)
- Blob decorativo de fondo (degradado púrpura-rosa, oculto en móvil)

### 3. Servicios (`#ofrecemos`)
**5 tarjetas** en grid `repeat(5,1fr)` con íconos SVG inline de 104px:

| Tarjeta | Clase | Color texto | Color fondo ico | Descripción |
|---|---|---|---|---|
| Nivelación en Lectura | `.p` | `--purple-deep` | `--purple-soft` | Fluidez y comprensión lectora |
| Nivelación en Matemáticas | `.y` | `#92400E` | `#FEF3C7` | Pensamiento lógico y operaciones |
| Refuerzo Escolar | `.k` | `--pink` | `--pink-soft` | Apoyo en todas las áreas |
| Acompañamiento en Tareas | `.t` | `--teal-deep` | `--teal-soft` | Guía en las tareas diarias |
| Maquetas y Carteleras | `.o` | `#C2410C` | `#FCE3D4` | Maquetas y carteleras para ferias y proyectos escolares |

Banner inferior: "Todo incluido en nuestros planes ♥ ♥" (pill rosa)

### 4. Tarifario (`#tarifas`)
Dos planes en grid de dos columnas:

| Plan | Clase | Precio | Duración |
|---|---|---|---|
| Quincena Laboral | `.q` (pink) | $100.000 / estudiante | 10 días hábiles |
| Mes Completo | `.m` (teal) | $200.000 / estudiante | 4 semanas laborales |

Incluye: nivelación en lectura, refuerzo en todas las áreas, acompañamiento en tareas diarias (quincena); + seguimiento del progreso y atención personalizada (mes).

### 5. Beneficios (`#beneficios`)
Tres tarjetas en grid `repeat(3,1fr)`:
- **Apoyo integral** (ícono corazón rosa) — avance con confianza
- **Atención personalizada** (ícono estrella amarilla) — respeto, paciencia y motivación
- **Compromiso real** (ícono check teal) — desarrollo académico y emocional

Frase de cierre (Yellowtail / rosa): "Aprender hoy, para un mejor mañana ♥"

### 6. CTA Band (`#contacto`)
- Fondo degradado `var(--purple)` → `var(--pink)`
- Título: "¡Contáctame para más información!"
- Botón WhatsApp (link con número ⚠️ placeholder)
- Email clicable: `aprendiendojuntostallertareas@gmail.com`

### 7. Footer
- Logo + "Aprendiendo Juntos" + enlaces de navegación + iconos FB y TikTok
- Email con ícono de sobre
- Copyright: "Refuerzo y Nivelación Escolar · Hecho con ♥ para acompañar a cada estudiante"

---

## Assets (`public/assets/`)

| Archivo | Estado | Descripción |
|---|---|---|
| `hero.webp` | ✅ Presente | Foto de la docente (600×480) |
| `favicon.svg` | ✅ Presente | Ícono SVG para navegadores modernos |
| `favicon-32.png` | ✅ Presente | Favicon 32×32 px |
| `apple-touch-icon.png` | ✅ Presente | Ícono Apple 180×180 px |
| `icon-512.png` | ✅ Presente | Ícono PWA/manifest |
| `og-image.jpg` | ❌ Faltante | Imagen Open Graph (1200×630 px) |

---

## Comportamientos interactivos

- **Scroll reveal:** clase `.reveal` animada al hacer scroll (pure JS, sin librerías); fallback de 2.5 s que fuerza la visibilidad de todos los elementos
- **Menú hamburguesa:** toggle de clase `.nav-open` en el `<header>`; cierra al hacer clic fuera o presionar Escape
- **Floating WA button:** fijo en esquina inferior derecha; en hover desktop expande el label con animación; en móvil (< 560px) se reduce a círculo sin texto
- **Floating social (mobile):** FB + TikTok como botones circulares apilados sobre el WA, visibles solo en < 560px
- **Nav social (desktop):** iconos FB y TikTok en la barra nav, ocultos en < 560px

---

## Responsive breakpoints

| Breakpoint | Cambios principales |
|---|---|
| `≤ 960px` | Hero en columna única · cards en `repeat(3,1fr)` · planes apilados · menú hamburguesa visible |
| `≤ 560px` | Cards en `1fr` · padding reducido · WA float solo icono · nav social oculto · social flotante visible |

---

## Páginas adicionales

### `public/404.html` — Página de error personalizada

Página 404 de marca completa, consistente con el diseño del sitio principal.

**Características:**
- `<meta name="robots" content="noindex">` — no indexada por buscadores
- Número "404" animado: el cero central es un círculo degradado rosa-púrpura con un corazón blanco y animación `halo` de pulso
- Titular: *"¡Ups! Esta página se fue de recreo"* (combinación Fredoka + Yellowtail)
- Decoración: estrellas y corazón flotantes posicionados absolutamente
- CTAs: "Volver al inicio" (btn-pink) + "Contáctanos" (btn-ghost → `index.html#contacto`)
- Chips de navegación rápida: Servicios · Tarifas · Beneficios · Contacto
- Nav simplificada (solo logo + botón "Ir al inicio")
- Footer con links incluyendo enlace a `privacidad.html`
- Misma paleta y fuentes que `index.html`

---

### `public/privacidad/index.html` — Política de Privacidad

Ruta: `/privacidad/` · Título: *"Política de Privacidad | Aprendiendo Juntos"*

**Estructura de la página:**

| Sección | Descripción |
|---|---|
| Nav | Sticky completa con hamburguesa, links internos (apuntan a `index.html#*`), iconos FB/TikTok, botón WhatsApp |
| Privacy Hero | Eyebrow pill "Tu confianza nos importa" · título Fredoka + Yellowtail · badge de última actualización con dot teal |
| Cuerpo legal | Tarjeta (`priv-card`) con intro + 4 secciones numeradas + bloque de cierre |
| Footer | Igual al de `index.html` + email clicable + iconos sociales |
| Flotante | Botón WhatsApp flotante con pulso + social flotante en mobile |

**Las 4 secciones de la política** (badges de color):

| # | Título | Color badge |
|---|---|---|
| 1 | Recopilación de información | Rosa (`--pink`) |
| 2 | Uso de la información | Púrpura (`--purple`) |
| 3 | Seguridad de los datos | Teal (`--teal`) |
| 4 | Derechos del usuario | Amarillo (`--yellow`) |

**Puntos clave del contenido legal:**
- Solo se recopila número de teléfono y nombre de perfil público de WhatsApp
- No se comparte, vende ni alquila información a terceros
- Cifrado extremo a extremo de WhatsApp (Meta + Google Cloud Platform)
- Para darse de baja: escribir `Detener` en el chat o email de contacto
- Última actualización: 19 de junio de 2026

**WhatsApp número real:** `+57 317 017 1728` (`wa.me/573170171728`)  
— mismo número en todas las páginas y CTA flotante
