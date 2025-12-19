# TFM de Análisis Predictivo Global de Salud Pública

## Descripción del Proyecto

Este proyecto realiza un análisis de datos para comprender los factores globales que influyen en la esperanza de vida de los países. Utilizando técnicas de análisis exploratorio de datos, examinamos las relaciones complejas entre la desigualdad económica, la pobreza, el acceso a la salud y los resultados de salud poblacional.

El análisis cubre los países con datos que abarcan desde 2000 hasta 2019, integrando múltiples conjuntos de datos internacionales para identificar predictores clave de la esperanza de vida y proporcionar recomendaciones de políticas basadas en evidencia.

## Hallazgos Principales

- **Insight Clave**: La relación entre factores socioeconómicos y esperanza de vida es fundamentalmente no lineal
- **Mejor Modelo**: Random Forest alcanzó R² = 0.8291 (MAE = 2.33 años)

## Conjuntos de Datos Utilizados

### 1. **life_expectancy.csv**
- **Fuente**: Estadísticas globales de salud
- **Registros**: 20,755 filas
- **Variable Principal**: Esperanza de vida al nacer por período (todos los sexos, edad 0)
- **Cobertura**: Múltiples países y años
- **Propósito**: Variable objetivo para modelos de predicción

### 2. **poverty_explorer.csv**
- **Fuente**: Banco Mundial y sistemas de monitoreo de pobreza
- **Registros**: 2,602 filas
- **Variables Principales**: 
  - Tasas de pobreza en múltiples umbrales ($1, $2.15, $3.65, $6.85, $10, $20, $30, $40/día)
  - Métricas de desigualdad de ingresos (coeficiente de Gini, participaciones por deciles)
  - Ingreso/consumo medio y mediano
- **Propósito**: Indicadores de desigualdad económica y pobreza

### 3. **gdp_per_capita_penn_world_table.csv**
- **Fuente**: Penn World Table
- **Registros**: 10,108 filas
- **Variable Principal**: PIB per cápita (producción, múltiples puntos de referencia de precios)
- **Propósito**: Indicador de desarrollo económico

### 4. **global_vaccination_coverage.csv**
- **Fuente**: Estimaciones de cobertura de inmunización OMS/UNICEF
- **Registros**: 7,897 filas
- **Variables Principales**: Tasas de cobertura para BCG, HepB3, Hib3, IPV1, MCV1, PCV3, Pol3, RCV1, RotaC, YFV, DTP3
- **Propósito**: Indicadores de acceso a salud y cuidado preventivo

### 5. **public_healthcare_spending_share_gdp.csv**
- **Fuente**: Organización Mundial de la Salud
- **Registros**: 4,014 filas
- **Variable Principal**: Gasto gubernamental general en salud doméstica (% del PIB)
- **Propósito**: Inversión gubernamental en atención médica

### 6. **homicide_rate_unodc.csv**
- **Fuente**: Oficina de las Naciones Unidas contra la Droga y el Delito (UNODC)
- **Registros**: 4,204 filas
- **Variable Principal**: Tasa de homicidios por cada 100,000 habitantes
- **Propósito**: Indicador de violencia y estabilidad social

### 7. **death_rate_from_suicides_gho.csv**
- **Fuente**: Observatorio Global de Salud (GHO)
- **Registros**: 3,880 filas
- **Variable Principal**: Tasa de suicidio estandarizada por edad (ambos sexos)
- **Propósito**: Indicador de salud mental y bienestar social

### 8. **annual_number_of_deaths_by_cause.csv**
- **Fuente**: Estudio de Carga Global de Enfermedad
- **Registros**: 6,840 filas
- **Variables Principales**: Muertes por 31 causas diferentes (ej. enfermedades cardiovasculares, neoplasias, enfermedades infecciosas, lesiones)
- **Propósito**: Análisis de carga de enfermedad y patrones de mortalidad


## Notebooks de Análisis

### 1. **1_Esperanza_vida_quintiles.ipynb**
- **Datasets**: life_expectancy.csv, public_healthcare_spending_share_gdp.csv, global_vaccination_coverage.csv, annual_number_of_deaths_by_cause.csv
- **Propósito**: Análisis de esperanza de vida por quintiles de gasto en salud, evaluando cobertura vacunal y muertes por enfermedades prevenibles

### 2. **2_Vacunacion_suicidio_PIB.ipynb**
- **Datasets**: global_vaccination_coverage.csv, death_rate_from_suicides_gho.csv
- **Propósito**: Exploración de relaciones entre cobertura de vacunación y tasas de suicidio

### 3. **3_Vacunacion_suicidio__PIB.ipynb**
- **Datasets**: global_vaccination_coverage.csv, death_rate_from_suicides_gho.csv
- **Propósito**: Análisis exploratorio ampliado de vacunación y suicidio con función de exploración

### 4. **4_Pobreza.ipynb**
- **Datasets**: poverty_explorer.csv
- **Propósito**: Exploración inicial del dataset de pobreza y sus variables

### 5. **5_Pobreza_correlacion.ipynb**
- **Datasets**: life_expectancy.csv, poverty_explorer.csv
- **Propósito**: Análisis de correlación entre indicadores de pobreza y esperanza de vida (2000-2019)

### 6. **6_PIB_esperanza_vida.ipynb**
- **Datasets**: gdp_per_capita_penn_world_table.csv, life_expectancy.csv, annual_number_of_deaths_by_cause.csv
- **Propósito**: Análisis de la relación entre PIB per cápita y esperanza de vida

### 7. **7_Causas_de_muerte.ipynb**
- **Datasets**: annual_number_of_deaths_by_cause.csv
- **Propósito**: Exploración de causas de muerte y agrupación por regiones geográficas

### 8. **8_ETL_Homicidios.ipynb**
- **Datasets**: homicide_rate_unodc.csv, gdp_per_capita_penn_world_table.csv, life_expectancy.csv
- **Propósito**: ETL y análisis exploratorio inicial de tasas de homicidio

### 9. **9_Homicidios_PIB.ipynb**
- **Datasets**: homicide_rate_unodc.csv, gdp_per_capita_penn_world_table.csv, life_expectancy.csv
- **Propósito**: Análisis de relación entre homicidios, PIB per cápita y esperanza de vida

### 10. **10_Homiciods__PIB.ipynb**
- **Datasets**: homicide_rate_unodc.csv, gdp_per_capita_penn_world_table.csv, life_expectancy.csv
- **Propósito**: Análisis exploratorio de homicidios y PIB per cápita

## Metodología Modelo

1. **Integración de Datos**: Fusión de 8 conjuntos de datos por país-año
2. **Ingeniería de Características**: Creación de indicadores compuestos y manejo de valores faltantes
3. **Análisis Exploratorio**: Análisis de correlación y tendencias temporales
4. **Modelos de Aprendizaje Automático**: 
   - Regresión Lineal
   - Regresión Ridge
   - Regresión Lasso
   - Árbol de Decisión
   - Random Forest (mejor desempeño)
5. **Validación**: División temporal (entrenamiento en años anteriores, prueba en años posteriores)

## Estructura del Proyecto

```
├── README.md
├── 1_Datasets/ 
├── 2_Notebooks/
├── 3_Dashboard/
├── 4_Modelo/
└── 5_Reporte/
```

## Requisitos

- Python 3.x
- pandas
- numpy
- scikit-learn
- seaborn
- matplotlib

## Contacto

Para preguntas u oportunidades de colaboración sobre este análisis, comuníquese a través del grupo en Slack 05-daesp-0425-grupo-3


---

*Período de Análisis: 2000-2019 | Países Analizados: 132 | Trabajo de Fin de Máster de Análisis de Datos*
