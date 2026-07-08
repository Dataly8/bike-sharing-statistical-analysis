# bike_sharing_estadistica

# Análisis de uso de un servicio de bicicletas compartidas (2012)

Análisis estadístico descriptivo del uso diario de un servicio de *bike sharing*, centrado en identificar los patrones de uso mensual y los meses de mayor variabilidad durante el año 2012.

## Objetivo

Calcular, para cada mes de 2012:
- La **media de uso diario** (número de alquileres).
- La **dispersión** del uso, para identificar los meses más variables.

## Datos

Dataset **Bike Sharing** (UCI Machine Learning Repository), archivo `day.csv` con registros diarios de alquileres. La columna analizada es `cnt` (total de bicicletas alquiladas por día).

El dataset se carga directamente desde una URL pública, de modo que el notebook es **reproducible sin necesidad de descargar el archivo en local**.

## Herramientas

- **Python** (pandas)
- Google Colab

Se optó por Python en lugar de una hoja de cálculo para lograr un análisis reproducible y auditable, y para reflejar un flujo de trabajo profesional.

## Metodología

Para medir la dispersión se calcularon **dos indicadores complementarios**:

- **Desviación estándar (σ):** variabilidad en unidades absolutas (bicis/día).
- **Coeficiente de variación (CV = σ / media):** variabilidad relativa al nivel medio de uso de cada mes.

Comparar ambas medidas permite distinguir entre meses con mucha oscilación en términos brutos y meses proporcionalmente más inestables respecto a su volumen de uso.

## Resultados

El uso medio crece en los meses cálidos (máximo en septiembre, ~7.286 bicis/día) y desciende en invierno (mínimo en enero, ~3.121 bicis/día).

**Meses con mayor dispersión:**

| Medida | Top 3 |
|--------|-------|
| Desviación estándar (absoluta) | Octubre, Diciembre, Abril |
| Coeficiente de variación (relativa) | Diciembre, Octubre, Enero |

Octubre y diciembre aparecen en ambos rankings, lo que los señala de forma robusta como los meses más dispersos. La diferencia en el tercer puesto (abril vs. enero) se explica por el efecto de la escala: enero es un mes de baja demanda cuya variación, aunque modesta en términos absolutos, es grande en proporción a su media.

## Posibles ampliaciones
El análisis podría enriquecerse cruzando el uso (`cnt`) con las variables meteorológicas del dataset (`weathersit`, `temp`, `windspeed`) y con el tipo de día (`workingday`), para contrastar la hipótesis de que la variabilidad se concentra en periodos de transición estacional.
El análisis podría enriquecerse cruzando el uso (`cnt`) con las variables meteorológicas del dataset (`weathersit`, `temp`, `windspeed`) y con el tipo de día (`workingday`), para contrastar la hipótesis de que la variabilidad se concentra en periodos de transición estacional.
