# OpenCabinet-BDD

[English](README.md) · [Español](README.es.md)

Game artwork organized by platform and commercial serial or official platform title ID.

Each platform contains a `catalog.json` mapping identifiers to full game names, regions, revisions, available artwork, hashes and provenance. Image paths are relative to their platform directory.

```text
Sony - PlayStation/
  SLUS-12345/
    cover_front.webp
    disc.webp
  catalog.json
```

Raster artwork is converted to WebP by comparing lossless and quality 90 encodings and keeping the smaller result. Console logos may retain their original SVG format. Filenames such as `cover_front2.webp` identify distinct variants. Games with missing or ambiguous identifiers remain outside this published library. Coverage is incomplete.

Console artwork is stored at the console directory root (`logo.svg` or `logo.webp`, `render.webp`, `screenshot.webp`) and listed in `console_artwork.json`. See [console logo credits](LOGO-CREDITS.md) for sources, authors and licenses.

## Catalog structure

Each console's `catalog.json` contains:

- `system` and `schema_version`: the console name and catalog format version.
- `games`: games indexed by serial or official title ID. Each game contains `entries` with its full release names and `images` with available media, paths, hashes and file details. An optional `metadata_id` links the game to a record in `metadata`.
- `metadata`: shared game records keyed by source and identifier, such as `wikidata:Q15087581`. Records contain names (`labels`), brief descriptions (`short_descriptions`), and a `fields` dictionary with developers, publishers, genres, player counts, game modes, release dates and platforms, where available.
- `metadata_sources`: metadata providers, credits and licenses.
- `console_metadata`: console names, brief descriptions, release dates, developers and manufacturers, where available. `sources` records their provenance and licenses.
- `dat`, `source_policy`, `encoding` and `status`: the source DAT, processing policy, image encoding settings and catalog generation status.

Different regional serials, revisions or discs can reference the same metadata record within a console. Metadata is optional and incomplete; empty field arrays indicate unavailable values. Records retain source links and qualifiers for facts specific to a region, platform or game mode.

## Contributing

We recommend [OpenCabinet-BDD_Editor](https://github.com/Utogu9/OpenCabinet-BDD_Editor) to replace artwork, add image types and variants, or import CBZ manuals and create them from images. Download the Windows executable from its [Releases](https://github.com/Utogu9/OpenCabinet-BDD_Editor/releases/latest); Python is not required.

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

### Media requirements

- Submit only media you are permitted to redistribute. State its source and the applicable permission or license. Making a scan or screenshot yourself does not automatically grant redistribution rights to the underlying artwork.
- Do not submit images obtained through bulk scraping of commercial databases. Do not bypass access restrictions or remove watermarks.
- For each raster artwork image outside a manual, generate two WebP candidates from the same original: **lossless** and **lossy with quality set to 90**. Keep the file with the smaller byte size; on a tie, keep the lossless version. Quality 90 is an encoder setting, not a target file size or a guaranteed percentage of retained quality. The recommended editor applies this rule automatically. Console logos supplied as SVG may retain the original file.
- Complete manuals use CBZ archives named `manual.cbz`, `manual2.cbz`, etc., with the same source and permission requirements. Encode each page directly as **WebP at quality 90**, without a lossless candidate, and fit it within **3840 pixels wide by 2160 pixels high**, preserving proportions without enlarging smaller images. Store pages in reading order as `0001.webp`, `0002.webp`, etc. The editor's **IMG to CBZ** tool applies these rules; imported CBZ archives are validated and preserved without recompression.
- Use the correct console and official serial or platform title ID folder for game media, such as `Sony - PlayStation/SLUS-12345/`. Store console artwork at the console directory root. Do not invent identifiers or use placeholders such as `!NONE`.
- Name images by type: `cover_front.webp`, `cover_back.webp`, `disc.webp`, etc. Distinct variants use `cover_front2.webp`, `cover_front3.webp`, etc.; byte-identical duplicates should not become variants.
- Include the updated `catalog.json`. Leave editor backups, history, settings and temporary files out of the pull request.

If the identifier, source or redistribution permission is uncertain, open an issue with the available information before uploading the media. Contributions may be declined when their provenance or permission cannot be established.

## Sources and credits

- Original images: [libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails) and its contributors. Its [credits](https://github.com/libretro-thumbnails/libretro-thumbnails#credits) acknowledge MobyGames, Fandom, volunteer contributors, photographers and scanners.
- Game names and identifiers: [No-Intro / DAT-o-MATIC](https://datomatic.no-intro.org/) and [Redump](https://redump.info/).
- Shared game metadata: [Wikidata](https://www.wikidata.org/) and its contributors. Its structured data is released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/); see [Wikidata's licensing policy](https://www.wikidata.org/wiki/Wikidata:Licensing). Source links are retained in the catalog records.
- Game artwork and promotional materials originate from their respective developers and publishers. This project does not claim ownership of those materials or assign them a new license.

This repository contains the published artwork and catalogues. Conversion scripts, source DAT archives, original libretro files, reports and private editor backups are not included.
