# Preprocesamiento de los Datos - Conversión de Coordenadas Militares

## Introducción
La base de datos de incendios forestales contiene registros antiguos que emplean métodos en desuso, como el sistema de hoja y cuadrícula del mapa militar 1:250.000.

![Mapa Militar](hojas.png "Hojas del mapa del sistema militar")

![Mapa Militar](cuadriculas.png "Cuadrículas del mapa del sistema militar")

Se explica aquí el proceso realizado para cruzar datos, extraer coordenadas y asignar ubicaciones aproximadas a dichos registros.

## Procesos Realizados

### 1. Cruce de Bases de Datos
Se utilizaron las siguientes fuentes de datos:
- **EGIF**: Base de datos principal sobre incendios forestales.
- **NGMEP**: Nomenclátor Geográfico de Municipios y Entidades de Población del CNIG, que incluye coordenadas, superficie, población y altitud de municipios.
- **INE**: Base de datos del Instituto Nacional de Estadística, empleada para obtener el `COD_INE`, un identificador único para cada municipio.

El cruce inicial permitió enriquecer los registros con información geográfica detallada basada en municipios. Sin embargo, quedaron **67,544 registros** entre los años 1968 y 1982 que no pudieron localizarse mediante este método debido a que utilizaban hojas y cuadrículas del mapa militar en desuso.

### 2. Extracción de Coordenadas del Mapa Militar
Para localizar los registros restantes:
1. Se extrajeron las coordenadas aproximadas de las cuadrículas del mapa militar a partir de archivos `.kmz` mediante la herramienta online [MyGeodata Converter](https://mygeodata.cloud/converter).
2. Los datos se transformaron en un archivo Excel, generando una tabla que relaciona cada hoja y cuadrícula con sus coordenadas decimales.
3. Para resolver duplicados en las áreas irregulares de los bordes del mapa, se calculó la media de las coordenadas de etiquetas repetidas.

Estas coordenadas representan el **centro de cada cuadrícula de 10x10 km**, por lo que son una aproximación geográfica.

### 3. Imputación de Datos de Municipios Cercanos
- Se utilizó la librería **SciPy** para asignar a cada cuadrícula los datos del municipio más cercano, tomando las coordenadas extraídas previamente y las de la base de datos NGMEP.
- De esta forma, los incendios sin ubicación específica se enriquecieron con información del municipio más próximo.

### 4. Resultados Finales
- Se identificaron geográficamente **52,517 registros** adicionales, reduciendo los no localizados a **15,027 registros**.
- Los registros restantes, pertenecientes a los años 1968-1973, se eliminaron debido a la falta de información suficiente.
- El conjunto final contiene **588,556 registros** con localización geográfica precisa o aproximada.

## Recursos
- **MyGeodata Converter**: Herramienta utilizada para transformar archivos KMZ a formatos tabulares.
- **SciPy**: Librería de Python empleada para cálculos de distancia entre coordenadas.
- Bases de datos:
  - EGIF
  - NGMEP (CNIG)
  - INE