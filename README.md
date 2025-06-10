# Análisis de Evasión de Clientes (Churn) en Telecom X

## 📑 Introducción

Este notebook de Google Colab presenta un análisis detallado de la evasión de clientes (Churn) en **Telecom X**. El objetivo principal es identificar los factores y características que influyen en la decisión de un cliente de darse de baja del servicio. Comprender estos impulsores es fundamental para desarrollar estrategias de retención efectivas, mejorar la satisfacción del cliente y optimizar la rentabilidad del negocio.

El análisis cubre las etapas clave de un proyecto de ciencia de datos: **Extracción**, **Transformación** y **Carga/Análisis (ETL+A)**. Se utilizan librerías populares de Python como `pandas` para la manipulación de datos, `numpy` para operaciones numéricas y `matplotlib` y `seaborn` para la visualización de datos.

## 📌 Extracción de Datos

Los datos se extraen directamente de un archivo JSON (`TelecomX_Data.json`) alojado en un repositorio de GitHub. Este archivo contiene información detallada sobre los clientes, incluyendo datos demográficos, servicios contratados, información de facturación y el estado de Churn.

El proceso de extracción implica:
1.  Importar las librerías necesarias (`pandas`).
2.  Leer el archivo JSON directamente desde la URL.
3.  Cargar los datos en un DataFrame de pandas para su posterior procesamiento.

## 🔧 Transformación de Datos

Esta sección se enfoca en la limpieza y el preprocesamiento de los datos extraídos para prepararlos para el análisis. Los pasos clave incluyen:

1.  **Conocimiento del Conjunto de Datos:** Inspección inicial de la estructura del DataFrame, tipos de datos y nombres de columnas (`df.info()`, `df.columns`).
2.  **Normalización:** El JSON contiene estructuras anidadas. Se normalizan las secciones `customer`, `phone`, `internet` y `account` para crear un DataFrame plano y fácil de trabajar.
3.  **Comprobación de Incoherencias y Normalización de Valores:**
    *   Se contabilizan las ocurrencias de valores en cada columna para identificar posibles errores o representaciones inconsistentes (e.g., espacios vacíos).
    *   Se elimina la columna `customerID` al no ser relevante para la predicción de Churn.
    *   Se tratan los valores faltantes o inconsistentes en la columna `Churn` (espacios vacíos), optando por eliminar las filas correspondientes (clientes nuevos sin historial).
    *   Se codifica la variable objetivo `Churn` a formato numérico (0 para 'No', 1 para 'Yes').
    *   Se limpian y convierten a tipo numérico las columnas `tenure` y `Charges.Total`, manejando espacios vacíos y valores faltantes.
4.  **Creación de Nuevas Características:** Se deriva una nueva métrica, `Cuentas_Diarias`, calculando el promedio de cargos diarios a partir de los cargos mensuales.
5.  **One-Hot Encoding:** Se aplican técnicas de One-Hot Encoding a las columnas categóricas restantes (como género, tipo de servicio, método de pago, etc.) para convertirlas en un formato numérico binario adecuado para el análisis y modelado.

Al finalizar esta etapa, el DataFrame está limpio, transformado y listo para el análisis exploratorio.

## 📊 Carga y Análisis (Exploratorio)

En esta sección, se realiza un análisis exploratorio de datos (EDA) para descubrir patrones, tendencias y relaciones entre las variables y la variable objetivo (`Churn`).

Los puntos principales del análisis exploratorio incluyen:

1.  **Análisis Descriptivo:**
    *   Obtención de estadísticas descriptivas básicas para variables numéricas (`df.describe()`).
    *   Análisis de la distribución y frecuencia de la variable objetivo `Churn` (conteo y porcentaje de clientes que se dieron de baja).
    *   Comparación de medidas de tendencia central (media, mediana, moda) y dispersión (desviación estándar, varianza, rango, cuartiles) para variables numéricas, segmentado por el estado de Churn.
2.  **Distribución de Evasión:**
    *   Visualización de la proporción de clientes que se dan de baja versus los que permanecen mediante gráficos de pastel y barras.
3.  **Recuento de Evasión por Variables Categóricas:**
    *   Análisis de la tasa de Churn para cada categoría dentro de las variables categóricas (resultantes del One-Hot Encoding).
    *   Identificación de las categorías que presentan las tasas de Churn más altas y más bajas.
    *   Visualización de las tasas de Churn por categoría utilizando gráficos de barras.
4.  **Recuento de Evasión por Variables Numéricas:**
    *   Análisis comparativo de la distribución de variables numéricas (`tenure`, `Charges.Monthly`, `Charges.Total`, `Cuentas_Diarias`, `SeniorCitizen`) para los grupos de Churn y No Churn.
    *   Visualización de estas distribuciones utilizando histogramas y boxplots para identificar diferencias clave.
5.  **Matriz de Correlación:**
    *   Generación y visualización de la matriz de correlación para entender las relaciones lineales entre todas las variables, prestando especial atención a las correlaciones con `Churn`.

Este análisis exploratorio proporciona una base sólida para comprender qué características de los clientes están más fuertemente asociadas con la probabilidad de Churn.

## 📄 Informe Final

El informe final consolida los hallazgos del análisis exploratorio y presenta conclusiones y recomendaciones estratégicas para Telecom X.

### 🔹 Introducción

Breve contexto del problema de Churn en la industria de telecomunicaciones y el objetivo del análisis.

### 🔹 Limpieza y Tratamiento de Datos

Descripción detallada del proceso de preprocesamiento, incluyendo la normalización, el manejo de valores faltantes/inconsistentes, la codificación de la variable objetivo y la aplicación de One-Hot Encoding.

### 🔹 Análisis Exploratorio de Datos

Resumen de los principales hallazgos derivados del EDA, destacando los factores más influyentes identificados a partir del análisis de variables numéricas y categóricas, así como las visualizaciones clave.

### 🔹 Conclusiones e Insights

Síntesis de los aprendizajes clave del análisis, presentando insights accionables sobre los perfiles de clientes con mayor riesgo de Churn (ej., clientes nuevos, contratos mensuales, servicios específicos, métodos de pago).

### 🔹 Recomendaciones

Propuestas de estrategias concretas y específicas para que Telecom X aborde la evasión de clientes, basadas en los insights obtenidos. Las recomendaciones pueden incluir programas de retención, ajustes en la oferta de servicios, mejoras en la experiencia del cliente, etc.

Este notebook sirve como un análisis inicial completo y detallado para comprender el problema de Churn en Telecom X y sentar las bases para posibles trabajos futuros, como la construcción de un modelo predictivo de Churn.
