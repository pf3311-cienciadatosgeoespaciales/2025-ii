# Formatos de archivos geoespaciales, fuentes de datos geoespaciales y geoprocesamiento

## Formatos de archivos geoespaciales

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

## Fuentes de datos geoespaciales

### Sitios temáticos

Los datos geoespaciales pueden encontrarse en una gran variedad de fuentes. Examine las siguientes. Descargue algunos archivos de cada una y estúdielos en QGIS.

- [Natural Earth](https://www.naturalearthdata.com/)
- [GADM](https://gadm.org/)
- [geoBoundaries](https://www.geoboundaries.org/)
- [Sistema Mundial de Información sobre Biodiversidad (GBIF)](https://www.gbif.org/)
- [WorldClim](https://www.worldclim.org/)

### Infraestructuras de Datos Espaciales

Una Infraestructura de Datos Espaciales (IDE) es el conjunto coordinado de datos geográficos, metadatos, servicios web, normas y acuerdos institucionales que facilita descubrir, acceder, integrar y reutilizar información geoespacial desde Internet. Se apoya en estándares abiertos del [Open Geospatial Consortium (OGC)](https://www.ogc.org/) —por ejemplo WMS, WFS, WCS, CSW y la familia OGC API— además de normas ISO (ej. ISO 19115 para metadatos), lo que garantiza la interoperabilidad entre diferentes plataformas y organizaciones.

En Costa Rica, el [SNIT (Sistema Nacional de Información Territorial)](https://www.snitcr.go.cr/) es la plataforma oficial para publicar y compartir la información geográfica fundamental con estándares nacionales, liderada por el Instituto Geográfico Nacional (IGN) del Registro Nacional. El SNIT fue creado por el Decreto Ejecutivo N.° 37773 (7 de mayo de 2013) y hoy articula la IDECORI (Infraestructura de Datos Espaciales de Costa Rica), establecida por el Decreto Ejecutivo N.° 42120-JP (publicado el 13 de febrero de 2020). A través de su geoportal ofrece catálogos y geoservicios interoperables (WMS y WFS) para consulta y reutilización de datos oficiales.

**Ejercicios**  

1. Acceda los [Servicios OGC](https://www.snitcr.go.cr/ico_servicios_ogc) del SNIT desde QGIS y descargue en su computadora los archivos de datos en formato GeoPackage (GPKG) correspondientes a:

- En el nodo IGN Cartografía 1:5mil CO: Límite Provincial, Límite Cantonal y Límite Distrital.
- En el nodo IGN 1:200mil: Red Vial 1:200mil.
- En el nodo IGN 1:200mil: Aeródromos 1:200mil.

Se recomienda que el nombre de cada capa tenga el mismo nombre que el archivo correspondiente. Guarde los datos en el CRS WGS 84 (EPSG:4326).

## Geoprocesamiento

### Álgebra de mapas

El [álgebra de mapas](https://en.m.wikipedia.org/wiki/Map_algebra) permite crear nuevas capas espaciales al combinar y transformar capas existentes mediante operaciones matemáticas y lógicas aplicadas celda por celda, como es muestra en la {numref}`figure-algebra-mapas`.

```{figure} img/algebra-mapas.png
:name: figure-algebra-mapas

Álgebra de mapas. Imagen de Bplewe compartida a través de [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:MapAlgebra.png).
```

Cada capa se trata como una matriz en la que cada celda (o píxel) representa una propiedad geográfica específica (ej. elevación, temperatura, uso del suelo), de modo que operaciones simples (suma, resta, multiplicación, división) o funciones más complejas (estadísticas focales, reescalamientos, condicionales y funciones de vecindad) se ejecutan de forma sistemática sobre conjuntos de celdas análogas. El álgebra de mapas raster permite modelar procesos ambientales, evaluar idoneidad territorial, analizar riesgos y realizar simulaciones espaciales de manera reproducible y eficiente.

#### Ejemplo: cálculo del NDVI

El [Índice de vegetación de diferencia normalizada](https://es.wikipedia.org/wiki/%C3%8Dndice_de_vegetaci%C3%B3n_de_diferencia_normalizada) (NDVI, en inglés, *Normalized Difference Vegetation Index*) es un indicador espectral que cuantifica la densidad y el vigor de la vegetación. Puede calcularse a partir de datos recopilados mediante teledetección.

##### Teledetección

La teledetección es la disciplina que trata sobre la adquisición de información sobre la superficie terrestre sin contacto físico directo, registrando la energía electromagnética (EM) reflejada o emitida por los objetos. Las formas más comunes de teledetección se basan en energía electromagnética reflejada. Cuando la energía (luz) del sol u otra fuente golpea un objeto, se refleja una parte de la energía. Diferentes materiales reflejan diferentes cantidades de energía entrante, lo que permite identificar los objetos. Por ejemplo, la energía que refleja una zona boscosa es diferente a la que refleja un cultivo o una ciudad, como se ilustra en la {numref}`figure-teledeteccion`.

```{figure} img/teledeteccion.gif
:name: figure-teledeteccion

Proceso de teledetección. Imagen de Natural Resources Canada.
```

Los sensores instalados en satélites (y aviones o drones) “observan” distintas porciones del [espectro electromagnético](https://es.wikipedia.org/wiki/Espectro_electromagn%C3%A9tico), mediante bandas discretas. Cada banda registra la intensidad de la señal en un rango de longitudes de onda y, por tanto, resalta propiedades físicas particulares. Así, los satélites orbitan la Tierra con cámaras multiespectrales (ej. Landsat 8/9 OLI, Sentinel-2 MSI) o hiperespectrales (ej. EnMAP, PRISMA) que dividen el espectro en decenas o cientos de bandas, además de sensores térmicos (ej. Landsat TIRS, MODIS) y de radar de apertura sintética (SAR) activos en microondas (ej. Sentinel-1, SAOCOM). Cada banda cumple un papel específico: distinguir vegetación sana (rojo + NIR), identificar humedad del suelo (SWIR), estimar temperatura (térmico), penetrar nubes y medir estructura (SAR), etc. La combinación de estas bandas mediante álgebra de mapas raster, índices espectrales o clasificación multibanda permite cartografiar uso del suelo, monitorear cultivos, evaluar desastres y estudiar procesos planetarios con un nivel de detalle y cobertura imposible de lograr *in situ*.

Por ejemplo, los satélites [Sentinel-2](https://es.wikipedia.org/wiki/Sentinel-2) (Sentinel-2A y Sentinel-2B) de la Agencia Espacial Europea constituyen una constelación multiespectral equipada con el instrumento MultiSpectral Instrument (MSI), capaz de registrar 13 bandas distribuidas en el espectro visible, el infrarrojo cercano (NIR) y el infrarrojo de onda corta (SWIR), con resoluciones espaciales de 10 m, 20 m y 60 m según la banda, lo que les permite monitorizar con alta frecuencia y detalle procesos terrestres tan diversos como la salud de la vegetación, la humedad del suelo, la presencia de aerosoles o las nubes cirros.

Las siguientes son las bandas de los satélites Sentinel-2:

<style>
  /* Estilo sencillo para alternar colores de fila */
  table.s2-bandas {
    border-collapse: collapse;
    width: 100%;
  }
  table.s2-bandas th,
  table.s2-bandas td {
    padding: 6px 10px;
    border: 1px solid #ddd;
    text-align: left;
  }
  table.s2-bandas thead {
    background-color: #3f51b5;      /* encabezado en tono azul */
    color: #fff;
  }
  table.s2-bandas tbody tr:nth-child(odd)  { background-color: #ffffff; }
  table.s2-bandas tbody tr:nth-child(even) { background-color: #f2f5ff; } /* fila alterna más clara */
</style>

<table class="s2-bandas">
  <caption style="caption-side: bottom; text-align: left; padding-top: 8px;">
    Fuentes:&nbsp;
    <a href="https://docs.sentinel-hub.com/api/latest/data/sentinel-2-l1c/" target="_blank">
      ESA&nbsp;Sentinel-2&nbsp;MSI&nbsp;documentation
    </a>
    &nbsp;y&nbsp;
    <a href="https://docs.sentinel-hub.com/api/latest/data/sentinel-2-l2a/" target="_blank">
      Sentinel&nbsp;Hub&nbsp;Technical&nbsp;Guide
    </a>.
  </caption>
  <thead>
    <tr>
      <th>Banda</th>
      <th>Longitud de onda central&nbsp;(nm)</th>
      <th>Ancho de banda&nbsp;(nm)</th>
      <th>Resoluci&oacute;n&nbsp;(m)</th>
      <th>Uso principal</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>B01 (aerosoles)</td>
      <td>443</td>
      <td>20</td>
      <td>60</td>
      <td>Detecci&oacute;n de aerosoles, calibraci&oacute;n atmosf&eacute;rica</td>
    </tr>
    <tr>
      <td>B02 (azul)</td>
      <td>490</td>
      <td>65</td>
      <td>10</td>
      <td>Diferenciaci&oacute;n suelo–vegetaci&oacute;n, penetraci&oacute;n agua clara</td>
    </tr>
    <tr>
      <td>B03 (verde)</td>
      <td>560</td>
      <td>35</td>
      <td>10</td>
      <td>Contraste agua limpia/turbia, realce de vegetaci&oacute;n</td>
    </tr>
    <tr>
      <td>B04 (rojo)</td>
      <td>665</td>
      <td>30</td>
      <td>10</td>
      <td>&Iacute;ndices de vegetaci&oacute;n (con NIR), usos/coberturas</td>
    </tr>
    <tr>
      <td>B05 (borde rojo&nbsp;1)</td>
      <td>705</td>
      <td>15</td>
      <td>20</td>
      <td>Fluorescencia clorof&iacute;lica, estr&eacute;s vegetal</td>
    </tr>
    <tr>
      <td>B06 (borde rojo&nbsp;2)</td>
      <td>740</td>
      <td>15</td>
      <td>20</td>
      <td>Clasificaci&oacute;n de vegetaci&oacute;n, contenido de clorofila</td>
    </tr>
    <tr>
      <td>B07 (borde rojo&nbsp;3)</td>
      <td>783</td>
      <td>20</td>
      <td>20</td>
      <td>Biomasa, estructura foliar</td>
    </tr>
    <tr>
      <td>B08 (NIR)</td>
      <td>842</td>
      <td>115</td>
      <td>10</td>
      <td>NDVI/EVI, biomasa, delineaci&oacute;n de costas</td>
    </tr>
    <tr>
      <td>B8A (NIR estrecho)</td>
      <td>865</td>
      <td>20</td>
      <td>20</td>
      <td>Fotofisiolog&iacute;a, discriminaci&oacute;n de tipos de cultivo</td>
    </tr>
    <tr>
      <td>B09 (vapor de agua)</td>
      <td>945</td>
      <td>20</td>
      <td>60</td>
      <td>Contenido atmosf&eacute;rico de H<sub>2</sub>O</td>
    </tr>
    <tr>
      <td>B10 (cirros)</td>
      <td>1375</td>
      <td>30</td>
      <td>60</td>
      <td>Detecci&oacute;n de nubes cirros</td>
    </tr>
    <tr>
      <td>B11 (SWIR&nbsp;1)</td>
      <td>1610</td>
      <td>90</td>
      <td>20</td>
      <td>Humedad de vegetaci&oacute;n y suelo, separaci&oacute;n nieve/nube</td>
    </tr>
    <tr>
      <td>B12 (SWIR&nbsp;2)</td>
      <td>2190</td>
      <td>180</td>
      <td>20</td>
      <td>Incendios, mineralog&iacute;a, humedad del suelo</td>
    </tr>
  </tbody>
</table>

#### NDVI

El NDVI mide el estado de la vegetación mediante la combinación matemática de la reflectancia registrada en las bandas rojo (R) e infrarrojo cercano (NIR) de una imagen satelital o aérea, de acuerdo con la fórmula NDVI = (NIR − R) / (NIR + R). 

$$
\text{NDVI} \;=\; \frac{\text{NIR} - \text{R}}{\text{NIR} + \text{R}}
$$

Los pigmentos clorofílicos absorben gran parte de la luz roja para la fotosíntesis, mientras que la estructura interna de las hojas refleja intensamente el NIR; por ello, valores altos de NDVI (cercanos a +1) se asocian con vegetación densa y saludable, valores cercanos a 0 indican cobertura escasa o suelos expuestos, y valores negativos reflejan superficies como agua, nieve o nubes. Esta métrica, ampliamente utilizada en teledetección y monitoreo ambiental, permite evaluar la productividad de cultivos, detectar estrés hídrico, seguir la fenología de ecosistemas y analizar cambios en la cobertura vegetal a diversas escalas temporales y espaciales, constituyéndose en una herramienta clave para la gestión de recursos naturales y la investigación climática.

**Ejercicio**  

Genere una capa con el cálculo del NDVI para la [imagen de Gandoca-Manzanillo tomada el 2024-06-18](https://github.com/pf3311-cienciadatosgeoespaciales/2025-ii/raw/refs/heads/main/datos/sentinel/gandoca-20240618.tif).
