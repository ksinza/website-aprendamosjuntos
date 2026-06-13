# Prompt: Landing Page "Aprendamos juntos"

Actúa como un desarrollador frontend experto en performance web y UI/UX.
Utilizando tu skill `design-taste-frontend`, necesito que desarrolles una landing page ultra ligera, responsiva y optimizada para producción para un taller de tareas y refuerzo escolar llamado "Aprendamos juntos".
El sitio se alojará en Firebase Hosting, por lo que el peso del archivo y la velocidad de carga son prioridades críticas.
Requiero que todo el proyecto se estructure en un único archivo `index.html` autocontenido (o con un archivo `styles.css` mínimo separado), utilizando HTML5 semántico y Tailwind CSS (mediante su CDN optimizada o clases puras) para evitar bundles pesados de JavaScript.

## REQUISITOS DE RENDIMIENTO Y DISEÑO:
1. **Cero imágenes pesadas:** Reemplaza cualquier necesidad de imágenes rasterizadas (PNG/JPG) por componentes visuales basados en CSS, degradados suaves, formas geométricas elegantes y bordes redondeados que emulen el estilo educativo, cálido e infantil del flyer.
2. **Iconos integrados:** No utilices librerías externas de iconos (como FontAwesome). Genera todos los iconos de las tarjetas y redes sociales (WhatsApp, Facebook, TikTok) exclusivamente como código SVG inline y optimizado.
3. **Diseño y Paleta de Colores Estricta:** El diseño debe transmitir confianza, crecimiento y alegría. Aplica exactamente esta paleta utilizando valores arbitrarios en Tailwind CSS (ej. `bg-[#87CEFA]`, `text-[#1E3A8A]`):
   - **Colores Principales (Fondos, tarjetas y elementos visuales clave):** Azul Claro (`#87CEFA`), Verde Menta (`#98FF98`) y Amarillo Suave (`#FFFF99`). Alterna estos colores de manera armónica en las distintas secciones.
   - **Colores Neutros (Lectura y estructura):** Utiliza Azul Marino (`#1E3A8A`) para todos los textos, títulos y subtítulos garantizando un contraste accesible; y Gris Claro (`#F1F1F1`) para fondos de secciones secundarias.
   - **Color de Acento / CTA:** Utiliza Lima (`#66E880`) exclusivamente para resaltar las llamadas a la acción (como el botón principal de WhatsApp) y detalles interactivos.




## ESTRUCTURA DE CONTENIDO:

### 1. Hero Section:
* **Título:** Refuerzo y Nivelación Escolar "Aprendamos juntos".
* **Subtítulo:** "Acompañamos el aprendizaje de tus hijos con amor, paciencia y dedicación".
* **CTA (Botón principal):** Un botón llamativo con efecto hover fluido que dirija a WhatsApp: "¡Contáctame para más información!".

### 2. Sección de Servicios (¿Qué ofrecemos?):
Diseño en cuadrícula de tarjetas (cards) limpias con sus respectivos iconos SVG:
* **Nivelación en Lectura:** Fortalecemos la lectura comprensiva, fluidez y comprensión.
* **Nivelación en Matemáticas:** Desarrollamos el pensamiento lógico, resolución de problemas y habilidades numéricas básicas.
* **Refuerzo Escolar:** Apoyo en las diferentes áreas para mejorar el rendimiento académico.
* **Acompañamiento en Tareas:** Acompañamos y guiamos en las tareas diarias para reforzar el aprendizaje.

### 3. Sección de Tarifas (Todo incluido en nuestros planes):
Bloque de precios limpio y contrastante con dos opciones:
* **Quincena Laboral** (10 días hábiles de clase): $100.000
* **Mes Completo** (4 semanas laborales): $200.000

### 4. Sección de Beneficios / Valor Agregado:
Viñetas estilizadas con SVGs de checkmarks:
* Apoyo integral en el aprendizaje para que tus hijos puedan avanzar con confianza.
* Atención personalizada en un ambiente de respeto, paciencia y motivación.
* Comprometidos con el desarrollo académico y emocional de cada niño/a.
* **Frase destacada:** "Enseñar es inspirar y acompañar para crecer."

### 5. Footer:
* **Frase:** "Aprender hoy, para un mejor mañana ❤️".
* **Enlaces de redes sociales:** Iconos SVG de WhatsApp, Facebook y TikTok con transiciones suaves.

Entrégame el código completamente optimizado, minificable, con semántica HTML correcta y accesibilidad básica (atributos alt, aria-labels en los enlaces de redes sociales).