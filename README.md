# OpenCabinet-BDD

[English](#english) · [Español](#español)

## English

Game artwork organized by platform and commercial serial or official platform title ID.

Each platform contains a `catalog.json` mapping identifiers to full game names, regions, revisions, available artwork, hashes and provenance. Image paths are relative to their platform directory.

```text
Sony - PlayStation/
  SLUS-12345/
    cover_front.webp
    disc.webp
  catalog.json
```

Artwork is converted to WebP by comparing lossless and quality 90 encodings and keeping the smaller result. Filenames such as `cover_front2.webp` identify distinct variants. Games with missing or ambiguous identifiers remain outside this published library. Coverage is incomplete.

### Contributing

We recommend [OpenCabinet-BDD_Editor](https://github.com/Utogu9/OpenCabinet-BDD_Editor) to replace artwork, add image types and variants, or import PDF manuals. Download the Windows executable from its [Releases](https://github.com/Utogu9/OpenCabinet-BDD_Editor/releases/latest); Python is not required.

1. Fork this repository on GitHub, then clone your fork. You can download the entire library or use a partial clone with sparse checkout to download only the consoles you want to edit; see the commands below.
2. Open the editor and select your local repository folder, which contains the console folders and their `catalog.json` files.
3. Find the game by title or official identifier and import your changes. The editor optimizes images as WebP and updates the catalogue.
4. Review the changed media and catalogue entries. Commit those files and open a pull request explaining what changed and where the media came from.
5. Complete the media checklist in the pull request template before submitting it.

Replace `YOUR_USERNAME` with your GitHub username. Choose one of these options.

**Clone the entire library:**

```bash
git clone https://github.com/YOUR_USERNAME/OpenCabinet-BDD.git
cd OpenCabinet-BDD
```

**Clone only the consoles you want to edit:**

```bash
git clone --filter=blob:none --sparse https://github.com/YOUR_USERNAME/OpenCabinet-BDD.git
cd OpenCabinet-BDD
git sparse-checkout set "Nintendo - Game Boy Advance"
```

Replace the example console with its exact folder name. You can select several consoles by listing their quoted folder names in the same `git sparse-checkout set` command. The editor should open the `OpenCabinet-BDD` folder, which contains the selected console folders.

#### Media requirements

- Submit only media you are permitted to redistribute. State its source and the applicable permission or license. Making a scan or screenshot yourself does not automatically grant redistribution rights to the underlying artwork.
- Do not submit images obtained through bulk scraping of commercial databases. Do not bypass access restrictions or remove watermarks.
- For each image, generate two WebP candidates from the same original: **lossless** and **lossy with quality set to 90**. Keep the file with the smaller byte size; on a tie, keep the lossless version. Quality 90 is an encoder setting, not a target file size or a guaranteed percentage of retained quality. The recommended editor applies this rule automatically.
- Complete manuals may be submitted as PDF files, with the same source and permission requirements. The two-candidate WebP rule applies to images, not to PDF files.
- Use the correct console and official serial or platform title ID folder, such as `Sony - PlayStation/SLUS-12345/`. Do not invent identifiers or use placeholders such as `!NONE`.
- Name images by type: `cover_front.webp`, `cover_back.webp`, `disc.webp`, etc. Distinct variants use `cover_front2.webp`, `cover_front3.webp`, etc.; byte-identical duplicates should not become variants.
- Include the updated `catalog.json`. Leave editor backups, history, settings and temporary files out of the pull request.

If the identifier, source or redistribution permission is uncertain, open an issue with the available information before uploading the media. Contributions may be declined when their provenance or permission cannot be established.

### Sources and credits

- Original images: [libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails) and its contributors. Its [credits](https://github.com/libretro-thumbnails/libretro-thumbnails#credits) acknowledge MobyGames, Fandom, volunteer contributors, photographers and scanners.
- Game names and identifiers: [No-Intro / DAT-o-MATIC](https://datomatic.no-intro.org/) and [Redump](https://redump.info/).
- Game artwork and promotional materials originate from their respective developers and publishers. This project does not claim ownership of those materials or assign them a new license.

This repository contains the published artwork and catalogues. Conversion scripts, source DAT archives, original libretro files, reports and private editor backups are not included.

## Español

Imágenes de videojuegos organizadas por plataforma y serial comercial o identificador oficial de la plataforma.

Cada consola contiene un `catalog.json` que relaciona los identificadores con los nombres completos, regiones, revisiones, imágenes disponibles, hashes y procedencia. Las rutas de las imágenes son relativas a la carpeta de la consola.

```text
Sony - PlayStation/
  SLUS-12345/
    cover_front.webp
    disc.webp
  catalog.json
```

Las imágenes se convierten a WebP comparando la codificación sin pérdida y con pérdida a calidad 90 y conservando el archivo más pequeño. Nombres como `cover_front2.webp` identifican variantes distintas. Los juegos con identificadores ausentes o ambiguos quedan fuera de esta biblioteca publicada. La cobertura es parcial.

### Cómo contribuir

Recomendamos [OpenCabinet-BDD_Editor](https://github.com/Utogu9/OpenCabinet-BDD_Editor) para reemplazar imágenes, agregar tipos y variantes o importar manuales PDF. Descargá el ejecutable de Windows desde sus [Releases](https://github.com/Utogu9/OpenCabinet-BDD_Editor/releases/latest); no requiere Python.

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

#### Requisitos de los medios

- Aportá únicamente medios que tengas permiso para redistribuir. Indicá su fuente y el permiso o licencia aplicable. Hacer un escaneo o una captura propia no otorga automáticamente derechos de redistribución sobre las imágenes originales.
- No se admiten imágenes obtenidas mediante scraping masivo de bases de datos comerciales. No eludas restricciones de acceso ni elimines marcas de agua.
- Para cada imagen, generá dos candidatos WebP desde el mismo original: **sin pérdida (lossless)** y **con pérdida, con el parámetro de calidad en 90**. Conservá el archivo que pese menos en bytes; si empatan, conservá el de sin pérdida. Calidad 90 es un parámetro del codificador, no un tamaño de archivo objetivo ni un porcentaje garantizado de calidad conservada. El editor recomendado aplica esta regla automáticamente.
- Se admiten manuales completos en PDF, con los mismos requisitos de procedencia y permiso. La comparación de los dos WebP corresponde a las imágenes, no a los archivos PDF.
- Usá la consola y la carpeta del serial o identificador oficial de plataforma correctos, por ejemplo `Sony - PlayStation/SLUS-12345/`. No inventes identificadores ni uses marcadores como `!NONE`.
- Nombrá las imágenes por tipo: `cover_front.webp`, `cover_back.webp`, `disc.webp`, etc. Las variantes distintas usan `cover_front2.webp`, `cover_front3.webp`, etc.; los archivos idénticos byte por byte no deben generar variantes.
- Incluí el `catalog.json` actualizado. Dejá fuera del pull request los respaldos, historial, configuración y archivos temporales del editor.

Si hay dudas sobre el identificador, la fuente o el permiso de redistribución, abrí un issue con la información disponible antes de subir los medios. Las contribuciones pueden rechazarse cuando no se pueda establecer su procedencia o permiso.

### Fuentes y créditos

- Imágenes originales: [libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails) y sus colaboradores. Sus [créditos](https://github.com/libretro-thumbnails/libretro-thumbnails#credits) reconocen a MobyGames, Fandom, colaboradores voluntarios, fotógrafos y personas que realizaron escaneos.
- Nombres e identificadores de juegos: [No-Intro / DAT-o-MATIC](https://datomatic.no-intro.org/) y [Redump](https://redump.info/).
- Las imágenes de los juegos y el material promocional provienen de sus respectivos desarrolladores y distribuidores. Este proyecto no reclama su propiedad ni les asigna una licencia nueva.

Este repositorio contiene las imágenes y los catálogos publicados. No incluye los scripts de conversión, los DAT originales, los archivos originales de libretro, los informes ni los respaldos privados del editor.
