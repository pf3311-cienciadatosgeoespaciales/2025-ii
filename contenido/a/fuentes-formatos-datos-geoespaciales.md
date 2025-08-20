# Fuentes y formatos de datos geoespaciales

## Infraestructuras de Datos Espaciales

Una Infraestructura de Datos Espaciales (IDE) es el conjunto coordinado de datos geográficos, metadatos, servicios web, normas y acuerdos institucionales que facilita descubrir, acceder, integrar y reutilizar información geoespacial desde Internet. Se apoya en estándares abiertos del [Open Geospatial Consortium (OGC)](https://www.ogc.org/) —por ejemplo WMS, WFS, WCS, CSW y la familia OGC API— además de normas ISO (ej. ISO 19115 para metadatos), lo que garantiza la interoperabilidad entre diferentes plataformas y organizaciones.

En Costa Rica, el [SNIT (Sistema Nacional de Información Territorial)](https://www.snitcr.go.cr/) es la plataforma oficial para publicar y compartir la información geográfica fundamental con estándares nacionales, liderada por el Instituto Geográfico Nacional (IGN) del Registro Nacional. El SNIT fue creado por el Decreto Ejecutivo N.° 37773 (7 de mayo de 2013) y hoy articula la IDECORI (Infraestructura de Datos Espaciales de Costa Rica), establecida por el Decreto Ejecutivo N.° 42120-JP (publicado el 13 de febrero de 2020). A través de su geoportal ofrece catálogos y geoservicios interoperables (WMS y WFS) para consulta y reutilización de datos oficiales.

**Ejercicios**  

1. Acceda los [Servicios OGC](https://www.snitcr.go.cr/ico_servicios_ogc) desde QGIS y descargue en su computadora los archivos de datos en formato GeoPackage (GPKG) correspondientes a:

- En el nodo IGN Cartografía 1:5mil CO: Límite Provincial, Límite Cantonal y Límite Distrital.
- En el nodo IGN 1:200mil: Red Vial 1:200mil.
- En el nodo IGN 1:200mil: Aeródromos 1:200mil.

Se recomienda que el nombre de cada capa tenga el mismo nombre que el archivo correspondiente. Guarde los datos en el CRS WGS 84 (EPSG:4326).
