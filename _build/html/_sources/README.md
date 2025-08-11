# Creación y configuración del Jupyter Book de PF-3311 Ciencia de datos geoespaciales 2025-II

1. Creación de un ambiente Conda.
2. Creación del Jupyter Book principal: pf3311-cienciadatosgeoespaciales.github.io
3. Creación de un Jupyter Book para cada curso, por ejemplo: 2025-ii, accesible en https://pf3311-cienciadatosgeoespaciales.github.io/2025-ii/
4. Publicación de modificaciones.

### 1. Creación de un ambiente Conda

```shell
# Actualización de Conda
conda update -n base -c defaults conda

# Borrado del ambiente (si es que existe)
# conda remove -n pf3311-2025-ii --all

# Creación del ambiente
conda create -n pf3311-2025-ii

# Activación del ambiente
conda activate pf3311-2025-ii

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de módulos requeridos
mamba install git python jupyter jupyter-book ghp-import numpy pandas matplotlib seaborn plotly gdal fiona shapely geopandas pyarrow duckdb rasterio xarray rioxarray earthpy xarray-spatial pystac-client python-graphviz folium leafmap lonboard streamlit

# Desactivación del ambiente
conda deactivate
```

### 2. Creación del Jupyter Book principal y publicación inicial del sitio web en GitHub Pages

```shell
conda activate pf3311-2025-ii

# Creación del Jupyter Book con una plantilla inicial
jupyter-book create pf3311-cienciadatosgeoespaciales.github.io

# Generación de archivos HTML (en el subdirectorio _build/html)
jupyter-book build pf3311-cienciadatosgeoespaciales.github.io

# En este punto, se crea en GitHub el repositorio pf3311-cienciadatosgeoespaciales.github.io

# Configuración del repositorio local y su branch main (para manejar los archivos fuente)
cd pf3311-cienciadatosgeoespaciales.github.io
git init
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin git@github.com:pf3311-cienciadatosgeoespaciales/pf3311-cienciadatosgeoespaciales.github.io.git
git push -u origin main

# Creación del branch gh-pages (para manejar los archivos HTML publicados)
ghp-import -n -p -f _build/html

# En este punto, se configura el repositorio para buscar los archivos de GH Pages en la rama gh-pages
# El sitio debe estar disponible en https://pf3311-cienciadatosgeoespaciales.github.io/

conda deactivate
```

### 3. Creación de un Jupyter Book para cada curso y publicación inicial del sitio web en GitHub Pages

```shell
conda activate pf3311-2025-ii

# Creación del Jupyter Book con una plantilla inicial
jupyter-book create 2025-ii

# Generación de archivos HTML (en el subdirectorio _build/html)
jupyter-book build 2025-ii

# En este punto, se crea en GitHub el repositorio 2025-ii

# Configuración del repositorio local y su branch main (para manejar los archivos fuente)
cd 2025-ii
git init
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin git@github.com:pf3311-cienciadatosgeoespaciales/2025-ii/
git push -u origin main

# Creación del branch gh-pages (para manejar los archivos HTML publicados)
ghp-import -n -p -f _build/html

# En este punto, se configura el repositorio para buscar los archivos de GH Pages en la rama gh-pages
# El sitio debe estar disponible en https://pf3311-cienciadatosgeoespaciales.github.io/2025-ii/
```

### 4. Publicación de modificaciones

```shell
# Generación de archivos HTML (debe hacerse desde el directorio padre del Jupyter Book)
jupyter-book build 2025-ii

cd 2025-ii

# Aplicación de cambios en el branch main
git status
git add .
git commit -m "###Comentario###"
git push

# Aplicación de cambios en el branch gh-pages
ghp-import -n -p -f _build/html
```

