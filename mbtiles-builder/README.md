# MBTiles Builder

| &nbsp;                                 | &nbsp;                                                                                                  |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| The following modules depend on it     | [tileserver](https://github.com/trufi-association/trufi-server-modules/tree/main/extensions/tileserver) |
| This depends on the following builders | [map-pbf-builder](../map-pbf-builder)                                                                   |

## Description

Generates the background map tiles in the `*.mbtile` format used by many tile serving services like [OpenMapTiles](https://github.com/openmaptiles/openmaptiles) what we use for our extension [tileserver](https://github.com/trufi-association/trufi-server-modules/tree/main/tileserver). Maps generated using this builder need to credit `© OpenMapTiles © OpenStreetMap contributors`. Attribution won't be applied automatically. This builder uses [OpenMapTiles](https://github.com/openmaptiles/openmaptiles) underneath.

## How to use

This tool will generate a `.mbtile` file which contains the necessary data for displaying a vector map:

### Download coastline

This only needs to be done on the first use of the builder when the folder `./coastline` is empty or does not exist.

```bash
wget -O water-polygons.zip https://osmdata.openstreetmap.de/download/water-polygons-split-4326.zip
unzip water-polygons.zip
```

Remove the zip file and rename the extracted folder manually to `coastline` or use the following automation:

```bash
# determine folder name via pattern
nameOfFolder=`ls | grep "water-polygons-split"`
## give the found folder the name 'coastline'
mv "$nameOfFolder" "coastline" --verbose
## delete the zip
rm water-polygons.zip --verbose
```

### Running

If the coastline has been downloaded and extracted properly, then we can start building a mbtile using

```bash
docker-compose --env-file ../$envfile -f docker-compose.yml up

```

- The `.mbtile` file out is located at `../data/<Country-City>/tileserver/${city}.mbtiles`
