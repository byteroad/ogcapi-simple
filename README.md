# OCG API Simple

*Keep it simple*

## Quick Setup

You will need `docker` and `docker-compose` installed in your system, in order to run this infrastructure. 

## Start pygeoapi

Type:

```
docker compose up
```

Or, if you want to run it in the background

```
docker compose up -d
```


## Environment Variables

This compositions read secrets from an environment file on this folder: ```.env```.

Create this file with the following format, replacing "SOMEPASSWORD" by a reasonable value.

```
POSTGRES_PASSWORD="SOMEPASSWORD"
POSTGRES_DB="geodb"
POSTGRES_USER="postgres"
DATABASE_URL=postgresql://postgres:SOMEPASSWORD@postgis/geodb
```

## Setup DB

Connect to DB:

```
psql -h localhost -U [USERNAME] -W
```

Donwload Shapefile from [here](https://www.dgterritorio.gov.pt/download/agt/).

Insert data:

```
docker run --network=ogcapi-simple_bridge1 -v "${PWD}/data:/mnt" ghcr.io/osgeo/gdal:ubuntu-full-3.8.4 \
ogr2ogr -a_srs "EPSG:3763" -t_srs "EPSG:4326" -f "PostgreSQL" PG:"dbname='geodb' user='postgres'
 host='postgis'" /mnt/CRUS+_31_julho2024.shp -lco GEOMETRY_NAME=geom -lco FID=OBJECTID -lco precision=NO -lco SPATIAL_INDEX=GIST \
-nlt PROMOTE_TO_MULTI -nln crus_31_julho2024 -overwrite
```

docker run --rm --volumes-from="matomo" --link matomo python:3-alpine python /var/www/html/misc/log-analytics/import_logs.py --url=http://localhost --idsite=2 --recorders=4 /apache/access_log.log

python /var/www/html/misc/log-analytics/import_logs.py --url=http://localhost  --login=user --password=matomo --idsite=2 --recorders=4 /apache/access_log.log



## License

This project is released under an [MIT License](./LICENSE)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
