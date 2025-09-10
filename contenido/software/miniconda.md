# Miniconda

## Descripción

Miniconda es un instalador mínimo para el sistema de gestión de paquetes y entornos virtuales [conda](https://docs.conda.io). Es una versión reducida de [Anaconda](https://www.anaconda.com/) que incluye solamente conda, Python, los paquetes de los que ambos dependen y unos pocos paquetes adicionales.

## Sitio web

[Miniconda](https://docs.anaconda.com/miniconda/)

## Instalación

Descargue del sitio web el instalador correspondiente a su sistema operativo y ejecútelo. Durante el proceso de instalación, se recomienda elegir la opción **Just Me** (para que se instale en el directorio del usuario) y aceptar las otras opciones que presenta por defecto el instalador.

## Creación de un entorno virtual

Los siguientes comandos deben ejecutarse en una interfaz de comandos del sistema operativo que tenga habilitada Miniconda o Anaconda (ej. Anaconda Prompt, en Windows).

```shell
# Actualización de Conda
conda update -n base -c defaults conda

# Borrado del ambiente (si es que existe)
# conda remove -n geopython --all

# Instalación de mamba
conda install -n base mamba -c conda-forge

# Creación del ambiente
conda create -n geopython

# Activación del ambiente
conda activate geopython

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de bibliotecas
mamba install git python jupyter jupyter-book ghp-import numpy pandas matplotlib seaborn plotly gdal fiona shapely geopandas pyarrow duckdb rasterio xarray rioxarray earthpy xarray-spatial pystac-client python-graphviz folium leafmap lonboard streamlit

# Desactivación del ambiente
conda deactivate
```

## Instalación de paquetes en un entorno virtual

Los siguientes comandos deben ejecutarse en una interfaz de comandos del sistema operativo que tenga habilitada Miniconda o Anaconda (ej. Anaconda Prompt, en Windows).

```shell
# Activación del ambiente
conda activate geopython

# Instalación de los paquetes numpy y pandas, como ejemplo
mamba install -c conda-forge numpy pandas

# Desactivación del ambiente (al finalizar la sesión de trabajo)
conda deactivate
```

## Otros comandos de conda

```shell
# Información general sobre conda
conda info

# Ayuda general sobre los comandos de conda
conda --help

# Ayuda sobre un comando
# Sintaxis: conda <NOMBRE_PAQUETE> --help
# Ejemplo:
conda install --help

# Lista de ambientes instalados
conda env list

# Lista de paquetes instalados en un ambiente
conda list

# Almacenamiento de un ambiente en un archivo de texto
# Sintaxis: conda list --explicit > <NOMBRE_ARCHIVO>
# Ejemplo:
conda list --explicit > miambiente.txt

# Creación de un ambiente a partir de un archivo de texto
# Sintaxis: conda create --name <NOMBRE_AMBIENTE> --file <NOMBRE_ARCHIVO>
# Ejemplo:
conda create --name miambiente --file miambiente.txt

# Borrado de un ambiente y de todos sus archivos
# Sintaxis: conda env remove --name <NOMBRE_AMBIENTE> --all
# Ejemplo:
conda env remove --name miambiente --all
```

Hay una lista completa de comandos de conda en:  
[Conda Cheat Sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)
