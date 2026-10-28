# Modelos de aprendizaje automático

## Estado actual: modelos preliminares

El cuaderno principal de la raíz contiene **regresión lineal** para conteos y **regresión logística** para clasificación binaria. Son pruebas exploratorias y **no son los modelos finales del proyecto**. Los resultados de regresión están en `../05_Resultados/Regresion/`; las exportaciones de clasificación siguen pendientes de incorporar.

## Próxima etapa: adaptación y experimentación

Se prepararán los datos para ensayar **SVM** y para estudiar otras dos propuestas que el equipo identifica provisionalmente como **«landsmark»** y **«gauss gradiente»**. Es necesario confirmar los nombres técnicos exactos de estas últimas antes de definir su implementación.

## Modelos de análisis avanzado previstos

- **XGBoost**, para explorar relaciones no lineales entre variables tabulares.
- **Transformers**, sujetos a diseñar representaciones temporales y comprobar la disponibilidad de datos y cómputo.
- **LSTM**, sujetos a generar secuencias cronológicas y asegurar una evaluación sin fuga de datos.

Estos modelos todavía **no han sido entrenados ni comparados en el repositorio**. Se justificarán con métricas y validación temporal, sin dar por hecho que su complejidad garantiza mejores resultados. El objetivo de clasificación en niveles **bajo / medio / alto** sigue pendiente de implementación.
