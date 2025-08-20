# Formatos y fuentes de datos geoespaciales

## Principales formatos de archivos

### Vectoriales

Los formatos de archivos espaciales vectoriales almacenan geometrías discretas (puntos, líneas y polígonos) junto con sus atributos y el sistema de referencia. Cada formato equilibra interoperabilidad, tamaño y capacidades (codificación, índices, capas múltiples, etc.). El soporte real de lectura/escritura depende de la compilación de la biblioteca [GDAL/OGR](https://gdal.org/), la cual mantiene una [lista de formatos vectoriales](https://gdal.org/en/stable/drivers/vector/) soportados.

Los siguientes son algunos de los principales formatos vectoriales:

- GeoPackage (.gpkg) — contenedor SQLite, estándar OGC recomendado para intercambio moderno.
- Shapefile (.shp/.shx/.dbf) — legado muy extendido; límites conocidos (ej. ~2 GB y campos de 10 caracteres).
- GeoJSON (.geojson/.json) — formato ligero para la web, definido por RFC 7946 (WGS84).
- CSV con geometría en WKT/WKB — tabla de texto; geometría en una columna WKT/WKB. Simple e interoperable, sin CRS/metadatos nativos.
- Esri File Geodatabase (.gdb) — carpeta-geodatabase con múltiples clases/tablas, índices y dominios. Óptimo en ArcGIS; soporte parcial en GDAL.
- KML/KMZ — XML de OGC para visualización (estilos, etiquetas). Coordenadas en WGS84; KMZ es la versión comprimida.
- GML — XML de OGC muy flexible; permite esquemas (XSD) y CRS. "Verboso", útil para intercambio formal.
- DXF (CAD) — intercambio CAD por capas/entidades. Suele carecer de CRS/unidades; requiere limpieza al llevarlo a SIG.

### Raster

Los formatos de archivos espaciales raster representan el espacio como una malla de celdas (píxeles) con uno o varios valores por banda; cada formato equilibra compresión, tamaño, tipos de dato, manejo de NoData, pirámides (*overviews*) y organización para acceso local o en la nube. GDAL/OGR también cuenta con una [lista de formatos raster](https://gdal.org/en/stable/drivers/raster/).

Los siguientes son algunos de los principales formatos raster:

- GeoTIFF (.tif/.tiff) — formato general más usado; georreferenciación interna, compresión y *overviews*.
- Cloud Optimized GeoTIFF (COG) — perfil de GeoTIFF diseñado para acceso eficiente vía solicitudes HTTP con rangos (ideal para nube).
- JPEG2000 (.jp2) — compresión con o sin pérdida. Se usa en teledetección.
- Erdas Imagine IMG (.img) — formato de trabajo clásico con amplio rango de tipos de dato y soporte de *overviews*.
- NetCDF (.nc) — contenedor para datos científicos multidimensionales (clima, oceanografía).
- GRIB (grb/grib2) — estándar WMO para distribución de información meteorológica.
- MBTiles (.mbtiles) — mosaicos ráster almacenados en una base SQLite, útil para teselas.
- GeoPackage ráster (.gpkg) — teselas ráster dentro del estándar OGC GeoPackage.
- Esri ASCII Grid (.asc) — grilla en texto plano; fácil de inspeccionar y portar.

## Ejemplos de fuentes de datos

Los datos geoespaciales pueden encontrarse en una gran variedad de fuentes. Examine las siguientes. Descargue algunos archivos de cada una y estúdielos en QGIS.

- [Natural Earth](https://www.naturalearthdata.com/)
- [GADM](https://gadm.org/)
- [geoBoundaries](https://www.geoboundaries.org/)
- [Sistema Mundial de Información sobre Biodiversidad (GBIF)](https://www.gbif.org/)
- [WorldClim](https://www.worldclim.org/)

## Infraestructuras de Datos Espaciales

Una Infraestructura de Datos Espaciales (IDE) es el conjunto coordinado de datos geográficos, metadatos, servicios web, normas y acuerdos institucionales que facilita descubrir, acceder, integrar y reutilizar información geoespacial desde Internet. Se apoya en estándares abiertos del [Open Geospatial Consortium (OGC)](https://www.ogc.org/) —por ejemplo WMS, WFS, WCS, CSW y la familia OGC API— además de normas ISO (ej. ISO 19115 para metadatos), lo que garantiza la interoperabilidad entre diferentes plataformas y organizaciones.

En Costa Rica, el [SNIT (Sistema Nacional de Información Territorial)](https://www.snitcr.go.cr/) es la plataforma oficial para publicar y compartir la información geográfica fundamental con estándares nacionales, liderada por el Instituto Geográfico Nacional (IGN) del Registro Nacional. El SNIT fue creado por el Decreto Ejecutivo N.° 37773 (7 de mayo de 2013) y hoy articula la IDECORI (Infraestructura de Datos Espaciales de Costa Rica), establecida por el Decreto Ejecutivo N.° 42120-JP (publicado el 13 de febrero de 2020). A través de su geoportal ofrece catálogos y geoservicios interoperables (WMS y WFS) para consulta y reutilización de datos oficiales.

**Ejercicios**  

1. Acceda los [Servicios OGC](https://www.snitcr.go.cr/ico_servicios_ogc) desde QGIS y descargue en su computadora los archivos de datos en formato GeoPackage (GPKG) correspondientes a:

- En el nodo IGN Cartografía 1:5mil CO: Límite Provincial, Límite Cantonal y Límite Distrital.
- En el nodo IGN 1:200mil: Red Vial 1:200mil.
- En el nodo IGN 1:200mil: Aeródromos 1:200mil.

Se recomienda que el nombre de cada capa tenga el mismo nombre que el archivo correspondiente. Guarde los datos en el CRS WGS 84 (EPSG:4326).
