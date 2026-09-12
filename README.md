# Sitio web de Tentrego!

Landing page de **Tentrego!** — envío de paquetería el mismo día en Santiago.

Este manual está escrito para que cualquier persona pueda editar el sitio, sin saber
programar. Lee con calma: no hay nada que puedas romper que no se arregle deshaciendo
el cambio.

> **Esta es una versión de revisión, todavía no lista para publicar.** A propósito,
> el sitio muestra una franja amarilla arriba de todo y varias insignias
> **CONFIRMAR** junto a los datos que faltan (precio, hora de corte, email, fotos,
> testimonios, formulario). Así se puede revisar de un vistazo qué falta antes de
> publicar. El punto 6 de este manual tiene la lista completa y cómo quitar cada
> insignia cuando el dato ya esté confirmado.

---

## 1. Qué hay en esta carpeta

| Archivo | Para qué sirve |
|---|---|
| `index.html` | **El sitio completo.** Todo está aquí: los textos, los colores y el diseño |
| `assets/` | Las imágenes. Adentro hay un `README-ASSETS.md` que dice cuáles faltan |
| `README.md` | Este manual |
| `PROMPT-LANDING-TENTREGO.md` | La especificación original con la que se construyó el sitio |

---

## 2. Cómo ver el sitio en tu computador

**Haz doble clic en `index.html`.** Se abre en tu navegador y listo. No necesitas
instalar nada ni tener internet (salvo para que se vean las tipografías correctas).

Para editarlo, ábrelo con un editor de texto. Recomendado:
[Visual Studio Code](https://code.visualstudio.com) (gratis). Después de guardar un
cambio, vuelve al navegador y aprieta `F5` para ver cómo quedó.

> **Consejo:** antes de cambiar algo, haz una copia de `index.html` y guárdala como
> `index-respaldo.html`. Si algo sale mal, vuelves a la copia.

---

## 3. Cómo cambiar el teléfono de WhatsApp

El número aparece en **varios lugares** del archivo. Para cambiarlos todos de una vez:

1. Abre `index.html` en tu editor.
2. Aprieta `Ctrl + H` (en Mac: `Cmd + Option + F`). Se abre "buscar y reemplazar".
3. En "buscar" escribe: `56987872109`
4. En "reemplazar" escribe el número nuevo, **sin el signo +, sin espacios y sin guiones**
   (ejemplo: `56911112222`).
5. Aprieta "reemplazar todo".

**Falta un paso más.** El número que se *muestra escrito* en la página está con
espacios, así que hay que cambiarlo aparte. Busca `+56 9 8787 2109` y reemplázalo por
el número nuevo con el mismo formato (ejemplo: `+56 9 1111 2222`).

### Cambiar el mensaje que sale escrito en WhatsApp

Cuando alguien aprieta un botón de WhatsApp, el mensaje ya viene escrito. Ese texto
está en la parte de la dirección que dice `?text=`. Para cambiarlo, busca:

```
?text=Hola%20Tentrego!%2C%20quiero%20cotizar%20un%20env%C3%ADo
```

Los códigos raros son la forma en que internet escribe caracteres especiales:
`%20` es un espacio, `%2C` es una coma y `%C3%ADo` es "ío". Si quieres otro mensaje,
escríbelo en [urlencoder.org](https://www.urlencoder.org/) y pega el resultado.

---

## 4. Cómo cambiar los textos

Todo el contenido está en la parte de abajo de `index.html`, y cada sección empieza
con un comentario grande en mayúsculas que la identifica. Busca el nombre de la
sección que quieres editar:

| Busca este comentario | Corresponde a |
|---|---|
| `HEADER` | La barra de arriba con el menú |
| `HERO` | La primera pantalla: el titular grande y los dos botones |
| `FRANJA DE CONFIANZA` | La banda azul con los 4 compromisos |
| `SERVICIOS` | Las 4 tarjetas de servicios |
| `CÓMO FUNCIONA` | Los 4 pasos numerados |
| `POR QUÉ TENTREGO!` | La lista de diferencias con la competencia |
| `TESTIMONIOS` | Sección desactivada, lista para cuando haya reseñas reales |
| `PORTAL DE CLIENTES` | El bloque azul con el acceso al portal |
| `COBERTURA` | El mapa y los datos de zona |
| `TARIFAS` | El bloque del precio |
| `PREGUNTAS FRECUENTES` | El acordeón de 7 preguntas |
| `CONTACTO` | El llamado final y los datos de contacto |
| `FOOTER` | El pie de página |

**Regla de oro:** cambia solo el texto que ves entre `>` y `<`.

```html
<h3>Retiro sin costo</h3>
        ↑ esto sí lo puedes cambiar
```

No borres las etiquetas `<h3>` ni `</h3>` ni nada que esté entre `<` y `>`.

### Palabras en rojo dentro de los titulares

Los titulares llevan una palabra destacada en rojo. Se marca así:

```html
<h2 class="titulo">Lo que <span class="c-rojo">hacemos</span> por ti</h2>
```

Para mover el rojo a otra palabra, mueve las etiquetas `<span class="c-rojo">` y
`</span>` alrededor de la palabra que quieras.

---

## 5. Cómo cambiar los colores

Todos los colores están juntos al principio del archivo, en el bloque que dice
`1. COLORES Y TIPOGRAFIAS`. Cambia el código de color en un solo lugar y se actualiza
en todo el sitio.

```css
:root{
  --rojo:        #E02020;  /* Botones, acentos, palabra destacada */
  --rojo-oscuro: #B81818;  /* Rojo cuando pasas el mouse por un botón */
  --azul-marino: #143059;  /* Titulares y fondos azules */
  --celeste:     #3DA9E0;  /* Acento secundario */
  --amarillo:    #FFC629;  /* Destacados puntuales */
  --gris-claro:  #F5F7FA;  /* Fondo de las secciones alternadas */
  --texto:       #1A1A1A;  /* Color del texto normal */
}
```

Los códigos tipo `#E02020` son colores en formato hexadecimal. Puedes sacar el código
de cualquier color en [htmlcolorcodes.com](https://htmlcolorcodes.com).

> **Ojo con el contraste.** Si aclaras mucho un color, el texto puede quedar difícil de
> leer. Verifica la combinación en [webaim.org/resources/contrastchecker](https://webaim.org/resources/contrastchecker/):
> la relación debe ser **4.5 o más**.

Las tipografías están justo debajo, en `--fuente-titulo` y `--fuente-texto`. Si cambias
alguna, acuérdate de cambiar también el enlace de Google Fonts que está más arriba en
el archivo (la línea que empieza con `<link href="https://fonts.googleapis.com...`).

---

## 6. Lo que falta antes de publicar

Mientras el sitio no esté listo, esto se ve **directamente en la página**: una franja
amarilla arriba de todo, y una insignia amarilla `⚠ CONFIRMAR` junto a cada dato
pendiente (precio, hora de corte, email, fotos, testimonios, formulario). Es a
propósito, para poder revisar de un vistazo qué falta sin tener que abrir el código.
También puedes buscar la palabra **`CONFIRMAR`** dentro de `index.html` (con
`Ctrl + F`) para ver el detalle de cada pendiente en los comentarios.

- [ ] **Dominio final.** Reemplazar `https://www.tentrego.cl/` por el dominio real.
      Está en 5 líneas al principio del archivo. (No tiene insignia en la página:
      va en metadatos que no se ven directamente).
- [ ] **Logo oficial.** Exportar el logo desde el material de Instagram y guardarlo
      como `assets/logo.png`. Hoy está dibujado con código (no tiene insignia: ya
      se ve terminado, aunque sea provisional).
- [ ] **Fotos reales.** Faltan `hero.jpg`, `equipo.jpg`, `portal.png` (captura del
      portal) y `og-image.jpg`. Las tres primeras se ven en la página con un marco
      punteado amarillo y la insignia CONFIRMAR. Ver `assets/README-ASSETS.md`.
- [ ] **Hora de corte.** Definir hasta qué hora se puede agendar un retiro para que el
      envío salga el mismo día, y escribirla en la pregunta 4 del acordeón.
- [ ] **Vigencia del precio.** Confirmar que "desde $2.500" sigue vigente. Si cambia,
      hay que actualizarlo en 4 lugares (el archivo lo indica en los comentarios).
- [ ] **Email de contacto.** Si existe un correo oficial, reemplazar el bloque
      marcado "Email — Confirmar" en la sección `CONTACTO` por el correo real.
- [ ] **Testimonios.** Solo publicar reseñas reales y con autorización del cliente.
      Hoy se ven 3 tarjetas de ejemplo con el texto entre corchetes — hay que
      reemplazarlas o volver a comentar toda la sección si no hay reseñas listas.
- [ ] **Formulario de contacto.** Está visible pero sin conectar (el botón no envía
      nada todavía). Conéctalo a un correo o a Formspree, o vuelve a comentarlo si
      prefieres usar solo WhatsApp. Su propio comentario en el código explica cómo.

**Antes de publicar de verdad**, quita también el modo de revisión: la franja
amarilla de arriba y las insignias `CONFIRMAR`. Todo está agrupado en un solo bloque
de `index.html` — búscalo por el título **"21. MARCAS 'PENDIENTE DE CONFIRMAR'"**
dentro de la etiqueta `<style>`; ese comentario explica exactamente qué borrar y qué
dejar.

---

## 7. Cómo publicarlo en Vercel

Vercel es un servicio gratuito para publicar sitios web. El sitio no necesita ninguna
configuración especial: es HTML puro.

### Opción A — Arrastrando la carpeta (la más simple)

1. Entra a [vercel.com](https://vercel.com) y crea una cuenta gratis.
2. En el panel, aprieta **Add New → Project**.
3. Busca la opción de subir archivos y **arrastra la carpeta completa** del sitio.
4. Vercel detecta que es un sitio estático y publica solo. En menos de un minuto te
   entrega una dirección tipo `tentrego.vercel.app`.

### Opción B — Conectando GitHub (recomendada)

Con esta opción, cada vez que guardes un cambio en GitHub el sitio se actualiza solo.

1. Sube esta carpeta a un repositorio de GitHub.
2. En Vercel, aprieta **Add New → Project** e **Import Git Repository**.
3. Elige el repositorio.
4. Deja **todo** en blanco o por defecto:
   - Framework Preset: **Other**
   - Build Command: *vacío*
   - Output Directory: *vacío*
   - Install Command: *vacío*
5. Aprieta **Deploy**.

### Conectar el dominio propio

1. En el proyecto de Vercel, ve a **Settings → Domains**.
2. Escribe tu dominio (por ejemplo `tentrego.cl`) y aprieta **Add**.
3. Vercel te muestra unos datos (registros DNS) que hay que copiar en el panel de la
   empresa donde compraste el dominio (NIC Chile, GoDaddy, etc.).
4. Puede tardar unas horas en activarse.
5. **Cuando el dominio esté funcionando**, vuelve al punto 6 de este manual y reemplaza
   `https://www.tentrego.cl/` por la dirección definitiva.

---

## 8. Detalles técnicos (por si alguien más lo mantiene)

- Un solo archivo `index.html` autocontenido: el CSS y el JavaScript van adentro.
- Sin frameworks, sin dependencias y sin proceso de compilación (`build`).
- Única carga externa: Google Fonts (Montserrat + Inter). Todos los íconos son SVG
  escritos dentro del archivo.
- JavaScript en vanilla, solo para: menú móvil, scroll suave, acordeón de preguntas,
  animaciones de entrada con `IntersectionObserver`, estado del header al hacer scroll
  y el año del pie de página.
- Accesibilidad: HTML semántico, un solo `<h1>`, `aria-expanded` en el menú y el
  acordeón, foco visible con teclado y soporte de `prefers-reduced-motion`.
- SEO: metadatos, Open Graph, Twitter Card y datos estructurados JSON-LD del tipo
  `DeliveryService`.
- Probado en Chromium a 360, 768, 1024 y 1440 px de ancho, sin scroll horizontal ni
  errores en la consola.
