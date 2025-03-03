# Proyecto de Machine Learning con Docker y TensorFlow Extended (TFX)

## Descripción

Este proyecto utiliza **Docker** y **TensorFlow Extended (TFX)** para la ingestión, validación, transformación y análisis de datos. Está diseñado para ejecutar un entorno de **Jupyter Notebook** dentro de un contenedor Docker, facilitando la exploración y el procesamiento de datos con **TFX** y **ML Metadata**.

## Estructura del Proyecto

```
.
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── main.py
├── data/
│   ├── covertype_training.csv
└── README.md
```

## Requisitos

- **Docker**
- **Docker Compose**
- Archivo de datos `covertype_training.csv` dentro de la carpeta `data/`

## Configuración y Ejecución

### 1. Construcción del Contenedor

Ejecutar el siguiente comando para construir la imagen del contenedor:

```sh
docker-compose build
```

### 2. Ejecución del Contenedor

Para iniciar el contenedor con Jupyter Notebook, ejecutar:

```sh
docker-compose up
```

Esto iniciará un servidor Jupyter Notebook accesible en `http://localhost:8888`.

## Contenido de los Archivos

### Dockerfile

Define un entorno basado en **Python 3.8 slim**, instalando las dependencias necesarias y configurando **Jupyter Notebook** para su uso dentro del contenedor.

### docker-compose.yml

Orquesta la ejecución del contenedor, montando el directorio local como volumen dentro de `/app` para facilitar el acceso a los archivos.

### main.py

Contiene la implementación del flujo de trabajo de **TFX**, incluyendo:

- Carga y preprocesamiento de datos.
- Selección de características con `SelectKBest` de `sklearn`.
- Creación de un pipeline con `CsvExampleGen`, `StatisticsGen`, `SchemaGen`, `ExampleValidator` y `Transform`.
- Uso de **ML Metadata** para rastrear los artefactos generados.
- Visualización de anomalías y actualización del esquema de datos.



## Notas

- Revise de que el archivo `covertype_training.csv` esté disponible en la ruta especificada.
- Puede modificar el `Dockerfile` y `docker-compose.yml` para adaptarlo a sus necesidades.

## Autor

Proyecto desarrollado por Juan Felipe Gonzalez Sanmiguel

