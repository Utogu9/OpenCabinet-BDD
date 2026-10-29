# OpenCabinet-BDD

[English](README.md) · [Español](README.es.md)

Imágenes de videojuegos organizadas por plataforma y serial comercial o identificador oficial de la plataforma.

Cada consola contiene un `catalog.json` que relaciona los identificadores con los nombres completos, regiones, revisiones, imágenes disponibles, hashes y procedencia. Las rutas de las imágenes son relativas a la carpeta de la consola.

```text
Sony - PlayStation/
  SLUS-12345/
    cover_front.webp
    disc.webp
  catalog.json
```

Las imágenes raster se convierten a WebP comparando la codificación sin pérdida y con pérdida a calidad 90 y conservando el archivo más pequeño. Los logos de consolas pueden conservar su formato SVG original. Nombres como `cover_front2.webp` identifican variantes distintas. Los juegos con identificadores ausentes o ambiguos quedan fuera de esta biblioteca publicada. La cobertura es parcial.

Las imágenes de consola están en la raíz de su carpeta (`logo.svg` o `logo.webp`, `render.webp`, `screenshot.webp`) y se registran en `console_artwork.json`. Los [créditos de los logos](LOGO-CREDITS.md) indican fuentes, autores y licencias.

## Estructura del catálogo

El `catalog.json` de cada consola contiene:

- `system` y `schema_version`: nombre de la consola y versión del formato del catálogo.
- `games`: juegos organizados por serial o ID oficial. Cada juego contiene `entries` con los nombres completos de sus ediciones e `images` con los medios disponibles, rutas, hashes y detalles de los archivos. El campo opcional `metadata_id` enlaza el juego con una ficha de `metadata`.
- `metadata`: fichas compartidas identificadas por fuente e ID, como `wikidata:Q15087581`. Contienen nombres (`labels`), descripciones breves (`short_descriptions`) y un diccionario `fields` con desarrolladores, editores, géneros, cantidades de jugadores, modos de juego, fechas de lanzamiento y plataformas, cuando están disponibles.
- `metadata_sources`: proveedores de metadatos, créditos y licencias.
- `console_metadata`: nombres, descripciones breves, fechas de lanzamiento, desarrolladores y fabricantes de la consola, cuando están disponibles. `sources` registra su procedencia y licencias.
- `dat`, `source_policy`, `encoding` y `status`: DAT de origen, política de procesamiento, parámetros de codificación de imágenes y estado de generación del catálogo.

Los seriales de distintas regiones, revisiones o discos pueden apuntar a la misma ficha de metadatos dentro de una consola. Los metadatos son opcionales y su cobertura es parcial; las listas de campos vacías indican valores no disponibles. Las fichas conservan los enlaces de procedencia y los calificadores de los datos específicos de una región, plataforma o modo de juego.

## Cómo contribuir

Recomendamos [OpenCabinet-BDD_Editor](https://github.com/Utogu9/OpenCabinet-BDD_Editor) para reemplazar imágenes, agregar tipos y variantes o importar manuales CBZ y crearlos desde imágenes. Descargá el ejecutable de Windows desde sus [Releases](https://github.com/Utogu9/OpenCabinet-BDD_Editor/releases/latest); no requiere Python.

1. Hacé un fork de este repositorio en GitHub y cloná tu fork. Podés descargar toda la biblioteca o usar una clonación parcial con sparse checkout para descargar únicamente las consolas que quieras modificar; los comandos están debajo.
2. Abrí el editor y seleccioná la carpeta de tu repositorio local, que contiene las carpetas de las consolas y sus `catalog.json`.
3. Buscá el juego por título o identificador oficial e importá los cambios. El editor optimiza las imágenes a WebP y actualiza el catálogo.
4. Revisá los medios y las entradas del catálogo modificados. Creá un commit con esos archivos y abrí un pull request explicando qué cambiaste y de dónde provienen los medios.
5. Completá la lista de verificación de medios de la plantilla antes de enviar el pull request.

Reemplazá `TU_USUARIO` por tu nombre de usuario de GitHub. Elegí una de estas opciones.

**Clonar toda la biblioteca:**

```bash
git clone https://github.com/TU_USUARIO/OpenCabinet-BDD.git
cd OpenCabinet-BDD
```

**Clonar solo las consolas que quieras modificar:**

```bash
git clone --filter=blob:none --sparse https://github.com/TU_USUARIO/OpenCabinet-BDD.git
cd OpenCabinet-BDD
git sparse-checkout set "Nintendo - Game Boy Advance"
```

Reemplazá la consola del ejemplo por el nombre exacto de su carpeta. Para seleccionar varias consolas, indicá sus nombres de carpeta entre comillas en el mismo comando `git sparse-checkout set`. En el editor elegí la carpeta `OpenCabinet-BDD`, que contiene las carpetas de las consolas seleccionadas.

### Requisitos de los medios

- Aportá únicamente medios que tengas permiso para redistribuir. Indicá su fuente y el permiso o licencia aplicable. Hacer un escaneo o una captura propia no otorga automáticamente derechos de redistribución sobre las imágenes originales.
- No se admiten imágenes obtenidas mediante scraping masivo de bases de datos comerciales. No eludas restricciones de acceso ni elimines marcas de agua.
- Para cada imagen raster fuera de un manual, generá dos candidatos WebP desde el mismo original: **sin pérdida (lossless)** y **con pérdida, con el parámetro de calidad en 90**. Conservá el archivo que pese menos en bytes; si empatan, conservá el de sin pérdida. Calidad 90 es un parámetro del codificador, no un tamaño de archivo objetivo ni un porcentaje garantizado de calidad conservada. El editor recomendado aplica esta regla automáticamente. Los logos de consola aportados como SVG pueden conservar el archivo original.
- Los manuales completos usan archivos CBZ llamados `manual.cbz`, `manual2.cbz`, etc., con los mismos requisitos de procedencia y permiso. Convertí cada página directamente a **WebP al 90 %**, sin generar una alternativa sin pérdida, y ajustala a un máximo de **3840 píxeles de ancho por 2160 de alto**, conservando proporciones y sin ampliar las imágenes más pequeñas. Guardá las páginas en orden de lectura como `0001.webp`, `0002.webp`, etc. La herramienta **IMG a CBZ** del editor aplica estas reglas; los CBZ importados se validan y conservan sin recompresión.
- Usá la consola y la carpeta del serial o identificador oficial de plataforma correctos para los medios de juegos, por ejemplo `Sony - PlayStation/SLUS-12345/`. Guardá las imágenes de consola en la raíz de la carpeta de esa consola. No inventes identificadores ni uses marcadores como `!NONE`.
- Nombrá las imágenes por tipo: `cover_front.webp`, `cover_back.webp`, `disc.webp`, etc. Las variantes distintas usan `cover_front2.webp`, `cover_front3.webp`, etc.; los archivos idénticos byte por byte no deben generar variantes.
- Incluí el `catalog.json` actualizado. Dejá fuera del pull request los respaldos, historial, configuración y archivos temporales del editor.

Si hay dudas sobre el identificador, la fuente o el permiso de redistribución, abrí un issue con la información disponible antes de subir los medios. Las contribuciones pueden rechazarse cuando no se pueda establecer su procedencia o permiso.

## Fuentes y créditos

- Imágenes originales: [libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails) y sus colaboradores. Sus [créditos](https://github.com/libretro-thumbnails/libretro-thumbnails#credits) reconocen a MobyGames, Fandom, colaboradores voluntarios, fotógrafos y personas que realizaron escaneos.
- Nombres e identificadores de juegos: [No-Intro / DAT-o-MATIC](https://datomatic.no-intro.org/) y [Redump](https://redump.info/).
- Metadatos compartidos de los juegos: [Wikidata](https://www.wikidata.org/) y sus colaboradores. Sus datos estructurados se publican bajo [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/); consultá la [política de licencias de Wikidata](https://www.wikidata.org/wiki/Wikidata:Licensing). Los enlaces de procedencia se conservan en las fichas de los catálogos.
- Las imágenes de los juegos y el material promocional provienen de sus respectivos desarrolladores y distribuidores. Este proyecto no reclama su propiedad ni les asigna una licencia nueva.

Este repositorio contiene las imágenes y los catálogos publicados. No incluye los scripts de conversión, los DAT originales, los archivos originales de libretro, los informes ni los respaldos privados del editor.
