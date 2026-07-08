# Bike Sharing: Statistical Dispersion Analysis

*[Versión en español abajo](#versión-en-español) · Read in English below*

Measuring **monthly usage and its variability** for a bike-sharing service in 2012, and comparing two dispersion measures to see what each one reveals.

## Problem

Given the `day.csv` dataset of daily bike-sharing usage, for the year 2012:
1. Compute the mean monthly usage (`cnt` column, month by month).
2. Identify the three months with the highest usage dispersion.

## Approach

1. **Filter** to 2012 (`yr == 1`).
2. **Group** by month (`mnth`) and average `cnt` to get mean monthly usage.
3. Compute the **standard deviation** (`.std()`, sample formula, n−1) as an *absolute* dispersion measure.
4. Compute the **coefficient of variation** (CV = σ / mean) as a *relative* dispersion measure, so months with very different usage levels can be compared fairly.
5. Combine mean, standard deviation and CV into a single comparison table.

## Key results

Mean usage rises in the warmer months and peaks in **September (~7,285 rides/day)**, dropping sharply in December and January — consistent with an outdoor service driven by weather.

The two dispersion measures agree on the top two months but diverge on the third:

| Rank | Std. deviation | Coefficient of variation |
|------|----------------|--------------------------|
| 1 | October | December (45%) |
| 2 | December | October (30%) |
| 3 | April | January (28%) |

## Interpretation

The divergence is the interesting part. The **CV normalizes by the mean**, so December and January — low-demand months — show large *relative* variation even though their absolute swings are smaller. This is why January enters the CV ranking but not the standard-deviation one.

**Hypothesis:** the highest-dispersion months cluster around seasonal transitions (autumn and winter), where unstable weather likely produces very uneven daily usage.

**Next step:** this could be validated by cross-referencing `cnt` with the dataset's weather variables (`weathersit`, `temp`, `windspeed`) and day type (`workingday`).

## Why this matters

An average alone hides the risk. Splitting dispersion into an absolute measure (standard deviation) and a relative one (coefficient of variation) shows that "most variable" depends on the question — and normalizing by the mean surfaces low-volume months that raw spread would miss.

## Tools

Python · pandas

## Data

`day.csv` (Bike Sharing dataset, 2012).

## Context

Deliverable for the *Mathematics for Data Processing* module of my Master's in Business Intelligence & Analytics. Notebook and write-up are in Spanish.

________________________________________________________________________________________________________________________________________________________________

## Versión en español

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
