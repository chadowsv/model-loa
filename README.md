# Proyecto Integrador I — Análisis y predicción de homicidios intencionales en Ecuador

## Descripción

Este repositorio reúne el desarrollo de un proyecto de análisis de datos y aprendizaje automático sobre **homicidios intencionales en Ecuador**. Se exploran patrones históricos por **cantón y fecha**, se construye un conjunto de datos agregado y se evalúan modelos preliminares para estimar el número de víctimas y la presencia o ausencia de víctimas en una unidad cantón-día.

**Alcance actualizado:** no se utilizarán datos de emergencias del ECU 911. La fuente principal para el análisis de homicidios son los registros publicados por el **Ministerio del Interior**. Se contempla integrar datos de feriados mediante una API como variable contextual; dicha integración **todavía no está implementada** en los modelos disponibles.

## Objetivos

- Analizar y depurar datos históricos de homicidios intencionales por ubicación y fecha.
- Construir un panel temporal agregado por **cantón-día** para exploración y modelado.
- Evaluar modelos de regresión y clasificación como **líneas base exploratorias**, sin considerarlos los modelos finales del proyecto.
- Comparar distintas estrategias de procesamiento y **al menos tres modelos de Machine Learning** durante las siguientes etapas del proyecto.
- Adaptar el conjunto de datos a nuevos enfoques y desarrollar modelos más completos para el análisis espacio-temporal, con evaluación y selección basadas en evidencia.
- Evaluar el aporte del calendario de feriados y diseñar visualizaciones para comunicar hallazgos.
- Documentar calidad, supuestos, métricas, limitaciones y reproducibilidad.

## Datos y periodo

| Fuente | Uso | Estado |
| --- | --- | --- |
| Ministerio del Interior, homicidios 2014–2025 | Datos históricos | Utilizados en el cuaderno principal |
| Ministerio del Interior, homicidios 2026 | Continuación temporal | El cuaderno actual llega a **agosto de 2026** |
| API de feriados de Ecuador | Variable contextual (`es_feriado`) | Documentada; integración pendiente |

**Importante:** si se dispone del corte **enero–septiembre de 2026**, habrá que adaptar la búsqueda del archivo en el cuaderno, volver a ejecutar el pipeline y **regenerar las tablas y métricas**. Los archivos de resultados incluidos aquí corresponden a **2014-01-01 a 2026-08-31**; no representan una ejecución con datos de septiembre.

El panel del modelo contiene **994.590 filas** (una por cantón-día) para **215 cantones**, bajo el supuesto —aún sujeto a validación— de que una combinación sin registros equivale a cero víctimas. Se debe revisar la cobertura de la fuente antes de interpretar los ceros como hechos confirmados.

## Modelos y estado actual

> **Importante: los modelos incluidos actualmente NO son los modelos finales.** La regresión lineal y la regresión logística son pruebas iniciales que permiten verificar la preparación del conjunto de datos, definir líneas base y detectar limitaciones. El objetivo es avanzar hacia modelos más completos para el análisis de homicidios intencionales. **No se afirma que los modelos planeados estén entrenados, evaluados o seleccionados.**

### Fase 1 — Modelos preliminares (estado real del repositorio)

| Enfoque | Variable objetivo | Algoritmo | Estado |
| --- | --- | --- | --- |
| Regresión | `victimas_homicidio`: conteo en cantón-día | Regresión lineal | Implementado; resultados disponibles |
| Clasificación binaria | `hubo_victimas`: 0 o 1 en cantón-día | Regresión logística | Implementado en el cuaderno; faltan los CSV exportados |
| Clasificación en niveles | Frecuencia baja, media o alta, con umbrales por justificar | Aún no seleccionado | Objetivo del proyecto; pendiente |

### Fase 2 — Adaptación del conjunto de datos y experimentación (próximos pasos)

Antes de entrenar modelos más complejos se buscará **adaptar las variables, la agregación espacial y temporal y los formatos de entrada** para evaluar:

- **SVM (Support Vector Machine):** alternativa de clasificación a contrastar con las líneas base.
- **«landsmark»:** nombre de trabajo indicado por el equipo; **pendiente de confirmar la técnica o algoritmo exacto** antes de implementarlo.
- **«gauss gradiente»:** nombre de trabajo indicado por el equipo; **pendiente de precisar a qué algoritmo se refiere** antes de implementarlo.

Los enfoques de esta fase **aún no figuran como entrenados ni validados**. Se evaluará su pertinencia según las características disponibles y la definición final de la variable objetivo.

### Fase 3 — Modelos previstos para un análisis más completo

Los modelos que el equipo propone explorar como candidatos principales son:

1. **XGBoost:** modelos basados en árboles potenciados para analizar variables geográficas, temporales, históricas y contextuales.
2. **Transformers:** arquitecturas de atención que requerirán definir una representación temporal adecuada y comprobar su viabilidad con los datos disponibles.
3. **LSTM (Long Short-Term Memory):** redes recurrentes para estudiar dependencias temporales, previa construcción y validación de secuencias históricas.

La elección del modelo o conjunto de modelos finales dependerá de la calidad de los datos, la granularidad temporal, el coste computacional y la comparación rigurosa mediante **validación temporal** y métricas apropiadas. Proponer estas tres arquitecturas **no equivale a afirmar que todas serán necesariamente las soluciones finales**.

**Distinción del objetivo:** la clasificación binaria actual (sin víctimas / con víctimas) no es lo mismo que la clasificación baja / media / alta propuesta en `01_Gestion_del_Proyecto/dato_objetivo.md`. El notebook disponible trabaja a nivel de **cantón-día**, no de franja horaria; para esta última hará falta adaptar los datos y verificar la disponibilidad de horas válidas.

### Métricas preliminares de regresión

Métricas del archivo `05_Resultados/Regresion/metricas_regresion.csv`, evaluado sobre registros de **2025-01-01 a 2026-08-31**:

| Modelo | MSE | MAE | R² |
| --- | ---: | ---: | ---: |
| Promedio histórico (referencia) | 0.339637 | **0.118178** | 0.249051 |
| Regresión lineal | **0.333986** | 0.164796 | **0.261544** |

La regresión lineal mejora ligeramente MSE y R², pero **empeora el MAE global** respecto de la referencia; por ello, los resultados no demuestran aún capacidad predictiva suficiente para un uso operativo. Véanse las métricas desglosadas por días con y sin víctimas y las limitaciones documentadas en el cuaderno.

## Estructura del repositorio

```text
model-loa/
├── 01_Gestion_del_Proyecto/
│   └── dato_objetivo.md
├── 02_Datos_Big_Data/
│   ├── API_feriados.md
│   ├── Homicidios/               # archivos fuente: mantener en Drive, salvo decisión del equipo
│   └── Calendario/               # integración futura de feriados
├── 03_Procesamiento/             # limpieza, EDA y comparación de motores
├── 04_Modelos_ML/                # líneas base, adaptación y candidatos futuros
├── 05_Resultados/
│   ├── Regresion/                # 4 archivos incorporados del ZIP de Drive
│   └── Clasificacion/            # exportaciones pendientes de subir
├── 06_Dashboard/                 # tablero pendiente
├── 07_Documentacion/             # fuentes, decisiones, validación y entregables
├── Proyecto_Integrador_I_LaraSimbañaPilamunga.ipynb
├── .gitignore
└── README.md
```

Las carpetas vacías tienen un archivo `README.md` de orientación. El cuaderno principal permanece en la raíz para evitar cambiar de forma imprevista su configuración de rutas; podrá modularizarse en `03_Procesamiento/` y `04_Modelos_ML/` en otro avance.

## Archivos importados desde Drive

Los archivos de la carpeta `Regresion` se han añadido a `05_Resultados/Regresion/`:

- `metricas_regresion.csv`: comparación de las métricas MSE, MAE y R².
- `metricas_por_grupo.csv`: errores separados entre días-cantón con y sin víctimas.
- `predicciones_regresion.csv.gz`: **130.720 predicciones** del periodo de prueba.
- `tabla_modelo_regresion.csv.gz`: tabla base agregada con **994.590 filas**.

Los `.csv.gz` son CSV comprimidos; pueden leerse con `pandas.read_csv(ruta, compression="gzip", dtype={"codigo_canton": str})` para **conservar los ceros iniciales** del código cantonal.

## Procesamiento, API y avances pendientes

El notebook implementa limpieza, agregación, codificación y separación temporal. Para completar las exigencias de procesamiento se propone **documentar y contrastar tres alternativas**, por ejemplo **Pandas, Polars y PySpark**, comprobando equivalencia de resultados, tiempos y recursos. Actualmente no se presentan como tres implementaciones terminadas.

La integración de la API de feriados se explica en `02_Datos_Big_Data/API_feriados.md`, pero debe **verificarse el servicio y ejecutar su integración**, conservando la procedencia y el corte de consulta. El calendario serviría como característica exógena conocida de antemano, no como prueba de causalidad.

Falta incorporar las exportaciones de clasificación, confirmar qué algoritmos designan los nombres de trabajo «landsmark» y «gauss gradiente», adaptar y evaluar SVM y otros candidatos, comparar **al menos tres modelos**, definir y validar el objetivo de tres niveles si se adopta, y desarrollar el dashboard. XGBoost, Transformers y LSTM son **modelos previstos**, no implementaciones ya concluidas. Se recomienda comparar con validación temporal, sin reutilizar la prueba final para ajustar hiperparámetros ni generar características con información futura.

## Cómo reproducir el avance actual

1. Abrir `Proyecto_Integrador_I_LaraSimbañaPilamunga.ipynb` en Jupyter o Google Colab.
2. Instalar las dependencias utilizadas por el cuaderno: `pandas`, `numpy`, `matplotlib`, `scikit-learn` y `openpyxl`.
3. Colocar los dos archivos Excel originales requeridos por el cuaderno (histórico 2014–2025 y **2026 enero–agosto**), respetando los nombres y rutas buscados en la celda de carga. Los Excel originales **no están incluidos en este ZIP**.
4. Ejecutar las celdas en orden y revisar los supuestos y métricas.
5. Si se cambia la fuente, el periodo, las variables o el código, volver a exportar los resultados antes de actualizar las cifras del README.

> Los datos disponibles en este repositorio permiten **revisar resultados exportados**; para reproducir el entrenamiento completo se necesitan los Excel originales. Los modelos son exploratorios y no estiman riesgo individual ni permiten afirmar que ocurrirá un homicidio en un lugar o fecha específicos.

## Integrantes

| Nombre | Usuario GitHub | Rol |
| --- | --- | --- |
| Oscar Lara | os-devsec | Desarrollador |
| Liseth Simbaña | chadowsv | Desarrolladora |
| Anthony Pilamunga | anthqny | Desarrollador |

## Referencias de trabajo

- [Datos abiertos de homicidios intencionales — Ecuador](https://www.datosabiertos.gob.ec/dataset/homicidios-intencionales)
- Documentación interna sobre feriados: [`02_Datos_Big_Data/API_feriados.md`](02_Datos_Big_Data/API_feriados.md).

