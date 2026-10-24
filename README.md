# OpenCabinet-BDD

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

## Sources and credits

- Original images: [libretro-thumbnails](https://github.com/libretro-thumbnails/libretro-thumbnails) and its contributors. Its [credits](https://github.com/libretro-thumbnails/libretro-thumbnails#credits) acknowledge MobyGames, Fandom, volunteer contributors, photographers and scanners.
- Game names and identifiers: [No-Intro / DAT-o-MATIC](https://datomatic.no-intro.org/) and [Redump](https://redump.info/).
- Game artwork and promotional materials originate from their respective developers and publishers. This project does not claim ownership of those materials or assign them a new license.

This repository contains the published artwork and catalogues. Conversion scripts, source DAT archives, original libretro files, reports and private editor backups are not included.
