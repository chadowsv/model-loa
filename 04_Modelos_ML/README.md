# Modelos de Machine Learning

| Carpeta | Objetivo | Unidad | Corte de prueba |
|---|---|---|---|
| [00_Historicos](00_Historicos/) | Regresión lineal y logística binaria | Cantón–día | Desde 2025 en exportaciones históricas |
| [Avance_II](Avance_II/) | Regresión logística, árbol y SVM lineal: baja/media/alta | Distrito–día–franja | Desde 18/02/2024 |
| [AdaBoost](AdaBoost/) | Conteo y clasificación binaria | Distrito–día–franja | Desde 01/01/2025 |
| [Random_Forest](Random_Forest/) | Clasificación baja/media/alta | Distrito–día–franja | Desde 18/02/2024 |
| [LSTM](LSTM/) | Conteo y clasificación binaria | Distrito–día | Desde 01/01/2025 |

AdaBoost, Random Forest y LSTM son los enfoques principales documentados, con resultados guardados. Los notebooks conservan sus celdas de código y salidas; no se han reentrenado. SVM, árbol y regresión logística constituyen experimentos de Avance II. XGBoost y Transformers fueron propuestas anteriores sin notebook implementado en el ZIP.

No elegir un ganador global: objetivos, unidades y pruebas no coinciden. Comparar contra líneas base y métricas por clase bajo protocolo común, sin usar el conjunto de prueba para calibrar umbrales. Random Forest explora umbrales sobre prueba, por lo que su evaluación es exploratoria. Ver [resultados](../05_Resultados/README.md).
