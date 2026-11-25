# Definición actual del objetivo predictivo

Estudiar la frecuencia histórica de homicidios intencionales registrados en Ecuador, con apoyo de ML y datos de calendario. El dataset de trabajo vigente se organiza por `codigo_provincia`, `codigo_distrito`, `fecha`, `franja_horaria`; el Avance I trabajaba por cantón y día. No intercambiar estas unidades.

## Objetivos modelados

- Regresión: `total_homicidios`, número de registros de víctimas agregados por unidad temporal/geográfica.
- Clasificación multiclase: `categoria_incidencia` (baja = 0; media = 1; alta = 2 o más en la ejecución guardada del ETL). La regla debe fijarse con información de entrenamiento en una evaluación futura.
- Clasificación binaria: `hubo_homicidios` (0 si no hubo registros, 1 si hubo al menos uno). AdaBoost la usa por franja; LSTM agrega por día.

Predictores: códigos territoriales, fecha (año, mes, día de semana), franja horaria, feriado; LSTM incorpora 28 días anteriores. No utilizar conteos del día objetivo ni atributos observados tras el evento como predictores. No se dispone de denominadores poblacionales en el pipeline vigente; conteos no equivalen a tasas de riesgo.

## Experimentos y criterios

Regresión lineal/logística (históricos), regresión logística/árbol/SVM (Avance II), AdaBoost, Random Forest y LSTM (enfoques principales). XGBoost y Transformers figuraban como candidatos anteriores, sin implementación en el ZIP. Comparar por objetivo y unidad común, con validación cronológica, referencia sencilla, métricas de clases minoritarias y errores por grupo. No se ha seleccionado un modelo operativo definitivo.

Fuente: [ETL vigente](../03_Procesamiento/Procesamiento_DatasetModelo.ipynb) y [modelos](../04_Modelos_ML/README.md). Este archivo sustituye las dos ramas incompatibles del texto histórico sin mantener marcadores de conflicto.
