# Imágenes que necesita el sitio

Esta carpeta guarda todas las imágenes de la landing page de Tentrego!.

**Cómo funciona hoy:** mientras una imagen no exista, el sitio muestra un dibujo gris
de relleno (un "placeholder") con el nombre del archivo que falta. El sitio se ve
completo igual, solo que sin las fotos reales.

**Cómo reemplazar un placeholder:** abre `index.html`, busca el nombre del archivo
(por ejemplo `hero.jpg`). Justo encima vas a encontrar un comentario con la línea
`<img ...>` ya escrita. Borra el bloque `<svg ...> ... </svg>` que está debajo y
saca la línea `<img>` del comentario.

---

## Lista de archivos

| Archivo | Tamaño recomendado | Formato | Qué debe mostrar | Estado |
|---|---|---|---|---|
| `logo.png` | 400 × 120 px | PNG con fondo transparente (o SVG) | El logo oficial: caja roja 3D con líneas de velocidad + la palabra "Tentrego!" | **Falta** — hoy el logo está dibujado con código |
| `hero.jpg` | 1200 × 900 px | JPG | Repartidor de Tentrego! entregando un paquete. Idealmente con la caja o polera de la marca, luz natural | **Ya está listo** |
| `equipo.jpg` | 1000 × 1100 px | JPG | El equipo cargando la camioneta, o el despacho/bodega. Debe transmitir cercanía y trabajo real | **Ya está listo** |
| `portal.png` | 1600 × 1000 px | PNG | Captura de pantalla del portal de clientes (`package-delivery-inventory.vercel.app`) | **Falta** |
| `mapa-cobertura.jpg` | 900 × 900 px | JPG o PNG | Mapa ilustrado de la Región Metropolitana con puntos de entrega distribuidos por Santiago | **Ya está listo** |
| `og-image.jpg` | 1200 × 630 px | JPG | Imagen que aparece cuando alguien comparte el link por WhatsApp, Instagram o Facebook. Logo + frase corta sobre fondo de marca | **Falta** |
| `favicon.png` | 512 × 512 px | PNG | Ícono de la pestaña del navegador | Opcional — ya hay uno provisional (`favicon.svg`) |
| `apple-touch-icon.png` | 180 × 180 px | PNG | Ícono al guardar el sitio en la pantalla de inicio de un iPhone | Opcional |
| `favicon.svg` | — | SVG | Ícono provisional hecho con la caja de la marca | **Ya está listo** |

---

## Recomendaciones antes de subir las fotos

- **Peso:** deja cada foto bajo los 300 KB. Puedes comprimirlas gratis en
  [squoosh.app](https://squoosh.app) sin perder calidad visible. Fotos pesadas hacen
  lento el sitio y eso baja la posición en Google.
- **Derechos:** usa solo fotos propias, tomadas por ustedes. No descargues imágenes de
  Google ni de bancos de imágenes sin licencia.
- **Personas:** si aparecen clientes o trabajadores identificables, pide su
  autorización antes de publicarlas.
- **Captura del portal:** antes de tomarla, asegúrate de que no se vean datos reales
  de clientes (nombres, direcciones, teléfonos). Usa datos de ejemplo.
- **Mapa de cobertura:** si usas una captura de Google Maps, revisa sus condiciones de
  uso antes de publicarla (lo habitual es que una captura simple para mostrar una zona
  esté bien, pero evita reproducir el mapa a gran escala o venderlo). Como alternativa,
  puedes generar un mapa simple con una herramienta como [Mapbox](https://www.mapbox.com)
  o [OpenStreetMap](https://www.openstreetmap.org).
- **Nombres de archivo:** respeta exactamente los nombres de la tabla, en minúsculas y
  sin tildes ni espacios. Si cambias un nombre, también hay que cambiarlo en
  `index.html`.

---

## Notas sobre el logo

Hoy el logo del header y del pie de página está dibujado directamente con código
(la caja roja es un SVG y el texto "Tentrego!" usa la tipografía Montserrat).
Se ve nítido en cualquier pantalla y no pesa nada.

Cuando tengas el archivo oficial exportado desde el material de Instagram, en
`index.html` busca el comentario que dice `Logo` dentro del bloque de estilos: ahí
está explicado cómo reemplazarlo por una imagen.
