# Definición del objetivo predictivo

## 1. Objetivo general

Desarrollar un modelo de inteligencia artificial capaz de estimar si un cantón, en un día y una franja horaria determinados, presentará una frecuencia históricamente alta, media o baja de homicidios, a partir del análisis de registros históricos y variables geográficas, temporales y contextuales.

El propósito es identificar combinaciones de ubicación y tiempo que presenten una mayor frecuencia esperada de casos, proporcionando información de apoyo para el análisis territorial y la planificación de estrategias preventivas.

## 2. Variable objetivo

La variable objetivo será el **nivel de frecuencia de homicidios esperado para una combinación específica de cantón, fecha y franja horaria**.

Para construirla, los registros históricos deberán organizarse por unidades espacio-temporales. Cada unidad representará un cantón en una fecha y franja horaria determinadas, incluyendo también aquellas combinaciones en las que no se hayan registrado homicidios.

A partir del número de casos contabilizados en cada unidad, se establecerán categorías de frecuencia:

- **Baja:** cantidad reducida de homicidios registrados.
- **Media:** cantidad intermedia de homicidios registrados.
- **Alta:** cantidad elevada de homicidios registrados.

Los umbrales que separen estas categorías deberán definirse mediante un análisis de la distribución histórica de los casos, considerando la granularidad temporal, las diferencias entre cantones y la cantidad de registros disponibles.

La variable objetivo será categórica y permitirá abordar el problema como una tarea de clasificación supervisada.

## 3. Variables de entrada

El modelo utilizará variables explicativas que describan las características de cada unidad espacio-temporal.

| Categoría | Variables propuestas |
|---|---|
| Geográficas | Cantón, parroquia, zona o sector. |
| Temporales | Fecha, hora o franja horaria, día de la semana y mes. |
| Contextuales | Indicador de feriado, fin de semana y otras características del calendario. |
| Históricas | Cantidad de homicidios registrados anteriormente en el cantón o zona durante periodos comparables. |
| Demográficas | Características agregadas disponibles, como población de la zona. |

La selección final dependerá de la disponibilidad, calidad y cobertura de los datos. Las variables históricas deberán construirse exclusivamente con información disponible antes del momento que se desea predecir, evitando incorporar información futura.

## 4. Enfoque de modelado

Se compararán **al menos tres modelos de aprendizaje automático**. Las implementaciones de regresión lineal y regresión logística del cuaderno principal constituyen **líneas base preliminares, no modelos finales**. Actualmente trabajan con registros agregados por cantón y día; la inclusión de franjas horarias requiere preparar datos adicionales.

Como fase intermedia se prevé adaptar la información para evaluar **SVM** y dos enfoques que el equipo denomina provisionalmente **«landsmark»** y **«gauss gradiente»**, cuyos nombres técnicos y métodos deberán confirmarse antes de su implementación.

Para el análisis más completo se proponen como candidatos **XGBoost, Transformers y LSTM**. Su adopción dependerá de la calidad de los datos, el volumen de información, la posibilidad de construir secuencias temporales y una comparación objetiva mediante validación temporal. Estos modelos **aún no están implementados**. Se contrastará tanto la predicción directa de categorías bajo / medio / alto como la estimación del conteo y su posterior categorización, cuando los umbrales estén justificados.

## 5. Alcance y limitaciones

El modelo identificará patrones estadísticos asociados con la frecuencia histórica de homicidios. Una categoría alta no implica que necesariamente ocurrirá un homicidio en el momento analizado, ni permite determinar con certeza cuándo o dónde sucederá un incidente individual.

Además, la cantidad absoluta de homicidios no equivale necesariamente al riesgo de ocurrencia. Las diferencias poblacionales entre cantones pueden influir en el número de casos, por lo que deberán considerarse variables de exposición y tasas poblacionales si el propósito evoluciona hacia la estimación de riesgo relativo.

## 6. Definición final

**Dato a predecir:** nivel de frecuencia de homicidios (bajo, medio o alto) para un cantón, en una fecha y franja horaria determinadas, utilizando registros históricos y variables geográficas, temporales y contextuales.

Este planteamiento permite transformar los registros históricos en un problema de clasificación espacio-temporal, con una variable objetivo definida y un conjunto de variables explicativas orientadas a identificar patrones de frecuencia.
