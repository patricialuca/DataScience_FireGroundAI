# FireGroundAI

**FireGroundAI** es un proyecto de inteligencia artificial que forma parte del **Trabajo de Fin de Máster en Ciencia de Datos de la UOC**.

## Objetivo

El objetivo principal de **FireGroundAI** es utilizar datos históricos de incendios forestales para predecir la severidad de un incendio forestal en función de varios factores que se observan al inicio del evento. El modelo desarrollado permitirá ayudar en la predicción de la gravedad de un incendio y facilitar la planificación de recursos para la lucha contra el fuego.

### Objetivos Secundarios:
- Enriquecer y consolidar la base de datos con información adicional proveniente de diferentes fuentes.
- Analizar los factores principales que influyen en el comportamiento de los incendios forestales.
- Comparar distintos modelos predictivos para elegir el más adecuado para resolver este tipo de problemas.

## Metodología

El enfoque para resolver este problema se divide en varias etapas:

1. **Consolidación de la Base de Datos**:
   - Unificación de localizaciones geográficas (coordenadas) a formato de latitud y longitud.
   - Incorporación de la altitud, superficie y población
   - Índice FWI
   - Densidad de incendios
   - Densidad de población
   - Obtención de distintas variables meteorológicas de AEMET.

2. **Análisis Exploratorio de los Datos**:
   - Revisión de los datos para detectar valores atípicos, faltantes o nulos.
   - Imputación de valores faltantes
   - Análisis univariante de las variables numéricas y categóricas
   - Análisis multivariante de las variables numéricas y categóricas
   - Análisis por clase de incendio: conato, incendio y gif.

3. **Selección de Características**:
   - Regresión Logística Multiclase.
   - Random Forest

4. **Modelos Predictivos**:
   - Se aplican diferentes enfoques de modelos de predicción:
     - Regresión Logística Multiclase
     - Árboles de decisión
     - Gradient Boosting
     - Redes neuronales

5. **Evaluación de Modelos**:
   - Se evalúa el rendimiento de los modelos utilizando métricas como **precision**, **recall**, **F1-score** y **curva roc**, **área bajo la curva (AUC)** y **matriz de confusión**.

6. **Validación del modelo**:
   - Será validado utilizando datos de incendios forestales correspondientes al año 2017 que serán excluidos del proceso de entrenamiento.

## Estructura del Repositorio

El repositorio contiene los siguientes directorios y archivos principales:

- **data/**: Carpeta que contiene la base de datos con información histórica de incendios forestales, incluidas las coordenadas, altitudes, pendientes y variables meteorológicas, etc.
- **modelos/**: Contiene modelos entrenados para la predicción de la severidad de los incendios.
- **mapa_militar/**: Contiene los archivos necesarios para interpretar los mapas militares en formato hoja cuadrícula ya en desuso.
- **LICENSE.md**: Las licencias que intervienen en el proyecto.
- **README.md**: Este archivo, que proporciona detalles sobre el proyecto y su implementación.

