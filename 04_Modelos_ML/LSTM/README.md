# LSTM — Semana 6

[LSTM_V1.ipynb](LSTM_V1.ipynb) usa TensorFlow/Keras, agrega cuatro franjas a distrito–día y construye ventanas de 28 días anteriores. Regresión de conteo y clasificación binaria; validación 2023–2024 y prueba desde 2025 (85.120 ventanas).

Salidas guardadas: MAE 0,213544, RMSE 0,572936 y R² 0,201092. Clasificación: accuracy 0,804124, precisión positiva 0,327926, recall positiva 0,741760, F1 positiva 0,454792 y PR-AUC 0,448487. No comparar MAE directamente con AdaBoost (distinta unidad temporal). Revisar disponibilidad de conteos recientes y evaluar pronóstico de varios días sin información futura antes de una aplicación real.

Entrada `ModelLOA/Datos_Procesados/dataset_homicidios_final.csv`. Salida `ModelLOA/Resultados/LSTM_Semana6/`: modelos `.keras`, escaladores y CSV; no incluidos como archivos independientes. Se recomienda Colab con recursos suficientes; no se ha reentrenado aquí.
