# Prompt para Claude Code — Landing page pública de Tentrego!

> Cómo usarlo: guarda este archivo en la carpeta del proyecto nuevo (ej. `~/Proyectos/tentrego-web/`), abre Claude Code ahí y escribe: **"Lee PROMPT-LANDING-TENTREGO.md y desarrolla el sitio según esa especificación."**
> Antes de pasarlo, revisa las marcas `[CONFIRMAR]` y reemplázalas por el dato real (o deja la instrucción para que Claude Code las deje como placeholder visible).

---

## 1. Rol y objetivo

Actúa como desarrollador front-end senior y diseñador web. Construye una **landing page comercial de una sola página (`index.html`)** para **Tentrego!**, una empresa chilena de envío de paquetería (última milla) enfocada en pymes y emprendedores de Santiago.

El objetivo de la página es **convertir visitas en cotizaciones por WhatsApp**. Todo lo demás (diseño, textos, estructura) está al servicio de ese objetivo. El segundo objetivo es dar acceso al portal de clientes ya existente.

El sitio debe quedar listo para publicarse en Vercel como sitio estático, sin proceso de build.

---

## 2. Restricciones técnicas (obligatorias)

- **Un solo archivo `index.html` autocontenido**: el CSS va en un bloque `<style>` y el JavaScript en un bloque `<script>` dentro del mismo archivo. Nada de frameworks, ni build step, ni `npm install`.
- **Sin dependencias externas de JS/CSS**. Única excepción permitida: Google Fonts (con `preconnect`). Los íconos deben ser **SVG inline**, no librerías de íconos.
- Imágenes en una carpeta `/assets/`. Si no existe una imagen real, genera un **placeholder SVG inline** con las proporciones correctas y un comentario HTML indicando qué foto va ahí y su tamaño recomendado.
- **CSS moderno y ordenado**: variables CSS (`:root`) al inicio con toda la paleta, tipografías, radios y sombras, para que una persona sin conocimientos de código pueda cambiar un color en un solo lugar. Usa Flexbox y Grid. Mobile-first.
- **JavaScript mínimo en vanilla**, solo para: menú hamburguesa en móvil, scroll suave a las anclas, acordeón de preguntas frecuentes, animaciones de entrada con `IntersectionObserver`, header que cambia de estado al hacer scroll y año dinámico en el footer. Nada de `localStorage`.
- Debe **abrirse correctamente haciendo doble clic en el archivo**, sin servidor local.
- Código comentado en español, con comentarios que separen cada sección (`<!-- ===== HERO ===== -->`), pensando en que quien lo edite después no programa.

---

## 3. Identidad de marca

**Nombre:** Tentrego! (siempre con el signo de exclamación final)
**Logo:** caja roja 3D con líneas de velocidad + wordmark "Tentrego!" donde "Tentre" va en rojo, "go" en celeste y el "!" en rojo. Archivo en `/assets/logo.png` `[CONFIRMAR: Gonzalo debe exportar el logo desde el material de Instagram en PNG con fondo transparente o SVG]`.

**Paleta** (tomada de las piezas gráficas de Instagram; ajusta los hex si el logo real difiere):

```css
--rojo:        #E02020;  /* color principal: CTAs, acentos, palabra destacada de los titulares */
--rojo-oscuro: #B81818;  /* hover de botones */
--azul-marino: #143059;  /* titulares, fondos de bloques de confianza */
--celeste:     #3DA9E0;  /* acento secundario, íconos */
--amarillo:    #FFC629;  /* badges y destacados puntuales, uso escaso */
--gris-claro:  #F5F7FA;  /* fondos alternados de sección */
--texto:       #1A1A1A;
--blanco:      #FFFFFF;
```

**Tipografía:** titulares en Montserrat (700/800, varios en MAYÚSCULAS), cuerpo en Inter o Open Sans (400/500). Cargar desde Google Fonts con `preconnect` y `display=swap`.

**Lenguaje visual** (replicar el estilo de sus piezas de Instagram, sin copiarlas literal):
- Titulares en mayúsculas donde una palabra clave va en rojo y el resto en azul marino.
- Subrayado rojo grueso y corto bajo los titulares principales.
- Tarjetas de beneficios sobre banda azul marino, con íconos lineales blancos (escudo, reloj, caja, calendario, corazón).
- Botón de WhatsApp en rojo con ícono de WhatsApp blanco, muy visible.
- Cortes diagonales o curvas suaves entre secciones (sutiles, sin exagerar).
- Mucho blanco, bloques de color sólido, nada de degradados recargados ni sombras pesadas.

**Tono de voz:** cercano, directo, chileno neutro, tratando de "tú". Habla a un emprendedor o pyme que vende online y necesita despachar. Nada de jerga logística corporativa.

---

## 4. Posicionamiento (esto define el copy)

La competencia directa (llego.cl, despachalo.cl, teloenvio.cl) le habla a **retail grande y corporativos**: SLAs, integraciones API, 16 regiones, clientes como Walmart y Mercado Libre. Tentrego! **no compite ahí**.

La diferenciación de Tentrego! es:

1. **Somos pyme y apoyamos a la pyme.** Trato humano, hablas con personas, no con un formulario.
2. **Sin volúmenes mínimos altos ni contratos largos.**
3. **Retiro sin costo en tu bodega o casa** (desde 5 paquetes).
4. **Entrega el mismo día** en todo Santiago ("Tentregamos en el mismo día").
5. **Portal de seguimiento propio**, algo que un courier chico normalmente no ofrece.

Todo el copy debe reforzar esto: cercanía + cumplimiento + tecnología simple.

---

## 5. Estructura de la página (en este orden)

### 5.1 Header (sticky)
Logo a la izquierda. Navegación: Servicios · Cómo funciona · Cobertura · Tarifas · Preguntas · Contacto. A la derecha dos botones: **"Ingresar al portal"** (secundario, borde azul) y **"Cotizar por WhatsApp"** (primario, rojo). En móvil, menú hamburguesa a pantalla completa.

### 5.2 Hero
- **H1:** `CUMPLIMOS CADA ENTREGA, CUMPLIMOS CONTIGO` — con "CADA ENTREGA" en rojo.
- **Subtítulo:** "Envío de paquetería para pymes y emprendedores en todo Santiago. Retiramos en tu bodega sin costo y entregamos el mismo día."
- **CTA principal:** "Cotiza por WhatsApp" → `https://wa.me/56987872109?text=Hola%20Tentrego!%2C%20quiero%20cotizar%20un%20env%C3%ADo`
- **CTA secundario:** "Ver cómo funciona" (ancla a la sección correspondiente).
- Imagen a la derecha: foto de repartidor con paquete (placeholder `/assets/hero.jpg`, 1200×900, con `alt` descriptivo).
- Bajo el hero, **franja de confianza** en azul marino con 4 ítems e íconos: **Entregas el mismo día · Retiros sin costo · Todo Santiago · Lunes a sábado**.

### 5.3 Servicios (4 tarjetas)
1. **Despacho same day** — "Retiramos y entregamos en el mismo día dentro de Santiago."
2. **Retiro sin costo** — "Pasamos por tus paquetes a tu bodega, oficina o casa, sin costo adicional desde 5 paquetes."
3. **Paquetería hasta 25 kg** — "Llevamos todo tipo de paquetes, hasta 25 kg por bulto."
4. **Seguimiento y evidencia** — "Sigue el estado de cada envío en tu portal y recibe respaldo de la entrega."

### 5.4 Cómo funciona (4 pasos numerados, horizontal en desktop)
1. **Cotizas por WhatsApp** — "Nos cuentas cuántos paquetes y a qué comunas."
2. **Agendamos el retiro** — "Coordinamos día y hora que te acomode, de lunes a sábado."
3. **Retiramos en tu bodega** — "Pasamos por tus paquetes sin costo."
4. **Entregamos y registramos** — "Entregamos el mismo día y queda el registro en tu portal."

### 5.5 Por qué Tentrego! (diferenciación, formato 2 columnas o lista con íconos)
- "Somos pyme y nos importa apoyar tu emprendimiento."
- "Trato personalizado: hablas con personas, no con un bot."
- "Sin contratos ni volúmenes mínimos imposibles."
- "Tarifas competitivas desde $2.500 por envío." `[CONFIRMAR vigencia del precio]`
- "Seguridad y cuidado en cada paquete: entregamos más que paquetes, entregamos confianza."

### 5.6 Portal de clientes (bloque destacado, fondo azul marino)
- **Título:** "Sigue tus envíos en línea"
- **Texto:** "Cada cliente de Tentrego! tiene acceso a su portal para revisar el estado de sus envíos, historial y respaldo de entregas."
- **CTA:** "Ingresar al portal" → `https://package-delivery-inventory.vercel.app` (abrir en pestaña nueva, con `rel="noopener"`).
- A la derecha, mockup del portal en un marco de laptop/celular (placeholder `/assets/portal.png`) `[CONFIRMAR: Gonzalo debe tomar una captura de la app]`.

### 5.7 Cobertura
Texto: "Operamos en todas las comunas de Santiago, de lunes a sábado." Base de operaciones en Ñuñoa. Acompañar con un mapa estilizado de la Región Metropolitana en SVG simple o una imagen placeholder. **No inventes un listado de comunas con tarifas por zona.**

### 5.8 Tarifas
Bloque simple, sin tabla de precios cerrada:
- Titular: "Tarifas competitivas, sin letra chica"
- "Desde **$2.500** por envío dentro de Santiago."
- "Retiros sin costo desde 5 paquetes."
- "El valor final depende de la comuna, el volumen mensual y el tipo de paquete."
- CTA: "Pide tu cotización" → WhatsApp.

### 5.9 Preguntas frecuentes (acordeón, 7 preguntas)
1. ¿Cuánto cuesta un envío? → desde $2.500, depende de comuna y volumen.
2. ¿Retiran en mi bodega o casa? → sí, sin costo desde 5 paquetes.
3. ¿Cuál es el peso máximo por paquete? → 25 kg.
4. ¿Entregan el mismo día? → sí, agendando el retiro antes de `[CONFIRMAR hora de corte]`.
5. ¿Qué comunas cubren? → todas las comunas de Santiago.
6. ¿Qué días operan? → lunes a sábado.
7. ¿Cómo sigo mis envíos? → a través del portal de clientes.

Marca claramente con un comentario HTML las respuestas que tienen `[CONFIRMAR]` para que se completen antes de publicar.

### 5.10 Contacto / CTA final
- Titular: "¿Listo para despachar con nosotros?"
- Botón grande de WhatsApp, número visible **+56 9 8787 2109**, Instagram **@tentrego.chile** (`https://instagram.com/tentrego.chile`), email `[CONFIRMAR]`, ubicación "Ñuñoa, Santiago".
- Formulario de contacto opcional (nombre, email, teléfono, mensaje) que envíe por `mailto:` o que quede preparado para conectar a Formspree; si lo incluyes, deja un comentario explicando cómo activarlo. Si no hay email confirmado, **prioriza WhatsApp y deja el formulario comentado.**

### 5.11 Footer
Logo, frase corta ("Envío de paquetería con compromiso y puntualidad"), navegación, redes, año dinámico, y línea legal "© [año] Tentrego! Todos los derechos reservados."

### 5.12 Botón flotante de WhatsApp
Fijo abajo a la derecha en todas las resoluciones, con animación de entrada suave y `aria-label`.

---

## 6. SEO y metadatos

- `<title>`: "Tentrego! | Envío de paquetería el mismo día en Santiago"
- `<meta name="description">`: "Retiro sin costo y entrega el mismo día en todas las comunas de Santiago. Paquetería para pymes y emprendedores, desde $2.500. Cotiza por WhatsApp."
- `lang="es-CL"`, viewport, `theme-color`, canonical `[CONFIRMAR dominio final]`.
- Open Graph y Twitter Card completos, con `/assets/og-image.jpg` (1200×630).
- Favicon en `/assets/favicon.png`.
- JSON-LD de tipo `LocalBusiness` (o `DeliveryService`): nombre, teléfono `+56987872109`, `areaServed` "Santiago, Chile", `openingHours` "Mo-Sa", `sameAs` con el Instagram.
- Jerarquía correcta de encabezados: un solo `<h1>`, `<h2>` por sección.

---

## 7. Accesibilidad y performance

- HTML semántico (`header`, `nav`, `main`, `section`, `footer`), contraste AA como mínimo (ojo con el rojo sobre azul: no usar texto rojo sobre fondo azul marino).
- `alt` descriptivo en todas las imágenes, `:focus-visible` visible en todos los elementos interactivos, acordeón navegable por teclado con `aria-expanded`.
- Respetar `prefers-reduced-motion`.
- `loading="lazy"` en imágenes bajo el pliegue, `width` y `height` explícitos para evitar saltos de layout.
- Objetivo: Lighthouse ≥ 90 en las cuatro categorías.

---

## 8. Prohibiciones explícitas

- **No inventes testimonios, nombres de clientes, logos de empresas, premios ni cifras** (cantidad de entregas, años de experiencia, porcentajes de cumplimiento). Si quieres dejar la sección de testimonios lista, déjala **comentada en el HTML** con un ejemplo de estructura y una nota de que debe llenarse con reseñas reales.
- No copies textos, imágenes ni layouts de llego.cl, despachalo.cl ni teloenvio.cl. Sirven solo como referencia de qué secciones incluye el rubro.
- No uses imágenes con derechos de terceros ni de stock sin licencia; usa placeholders.
- No agregues integraciones, APIs, ni sistemas de tracking que Tentrego! no tenga hoy.
- No prometas cobertura fuera de Santiago ni servicios que no están listados aquí.

---

## 9. Entregables

1. `index.html` — el sitio completo, autocontenido.
2. `/assets/` — carpeta creada, con un `README-ASSETS.md` que liste cada imagen necesaria, su nombre exacto de archivo y el tamaño recomendado en píxeles.
3. `README.md` breve, escrito para alguien sin conocimientos de programación, con: cómo ver el sitio localmente, dónde editar el teléfono, los textos y los colores (indicando los números de sección de los comentarios), y cómo publicarlo en Vercel.

---

## 10. Criterios de aceptación

Antes de darte por terminado, verifica:

- [ ] El archivo abre correctamente con doble clic, sin servidor.
- [ ] Se ve bien a 360 px, 768 px, 1024 px y 1440 px de ancho, sin scroll horizontal.
- [ ] Todos los CTA de WhatsApp apuntan a `wa.me/56987872109` con mensaje prellenado.
- [ ] El botón del portal abre `https://package-delivery-inventory.vercel.app` en pestaña nueva.
- [ ] El menú móvil abre, cierra y navega correctamente.
- [ ] El acordeón de FAQ funciona con mouse y con teclado.
- [ ] La consola del navegador no muestra ningún error.
- [ ] Todos los `[CONFIRMAR]` quedaron visibles como comentarios HTML, no como texto público en la página.
- [ ] Entrega al final un resumen de qué falta para publicar (imágenes reales, datos por confirmar).
