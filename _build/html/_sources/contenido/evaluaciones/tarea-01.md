# Tarea 01 - Elaboración de un mapa en QGIS

## Fecha de entrega

La fecha y hora límite para la entrega de esta tarea es **miércoles 17 de setiembre de 2025 a las 17:00**.

## Desarrollo

Debe elaborar un [mapa de coropletas](https://es.wikipedia.org/wiki/Mapa_coropl%C3%A9tico) en [QGIS](https://qgis.org/) que muestre la densidad de la red vial en los cantones de Costa Rica. 

La densidad de la red vial para un polígono se define como:  
**km de longitud de red vial / km2 de área**  
Por ejemplo, si un cantón tiene 500 km de longitud de red vial y un área de 1000 km2, la densidad de su red vial es 0.5.

Utilice las siguientes capas Web Feature Service (WFS) publicadas por el Instituto Geográfico Nacional (IGN) en el [Sistema Nacional de Información Territorial (SNIT)](https://www.snitcr.go.cr/):

- [Límite cantonal 1:5000](https://www.snitcr.go.cr/ico_servicios_ogc_info?k=bm9kbzo6OTM=&nombre=IGN%20Cartograf%C3%ADa%201:5mil%20CO)
- [Red vial 1:200000](https://www.snitcr.go.cr/ico_servicios_ogc_info?k=bm9kbzo6NDI=&nombre=IGN%201:200mil)

## Entregables

Un archivo comprimido (ej. ZIP) que incluya tres archivos:

- Un archivo GeoPackage (GPKG) con la capa de cantones y el campo correspondiente a la densidad de la red vial para cada cantón.
- Un archivo gráfico (ej. PNG, JPG) con el mapa de coropletas correspondiente a la densidad de la red vial en los cantones de Costa Rica.
- Un archivo llamado `leame.txt` con una descripción, no mayor a 250 palabras, del procedimiento seguido para elaborar el mapa.

La entrega debe realizarse a través de la plataforma Mediación Virtual.

## Calificación

- 30% - Archivo GeoPackage (GPKG) con la capa de cantones y el campo correspondiente a la densidad de la red vial para cada cantón.
- 60% - Archivo gráfico con el mapa
  - 25% - Capa de coropletas.
  - 15% - Simbología.
  - 10% - Grilla de coordenadas en WGS84 (EPSG:4326).
  -  5% - Escala.
  -  5% - Información general: título, especificación del sistema de coordenadas y fuentes de datos utilizadas.
- 10% - Archivo `leame.txt` con descripción del proceso realizado para elaborar el mapa.

Tenga en cuenta las siguientes consideraciones:

- Obtenga las longitudes y áreas que necesite a través de cálculos (ej. SQL, funcionalidades de QGIS). **No utilice los campos precalculados de las capas (si los hay)**.
- Elija cuidadosamente las categorías y los colores del mapa de coropletas.

**Esta tarea debe realizarse de manera estrictamente individual**.
