# AdaBoost — Semana 6

[AdaBoost_V1.ipynb](AdaBoost_V1.ipynb): AdaBoostRegressor y AdaBoostClassifier (binario) sobre distrito–día–franja. Valida con 2023–2024, reentrena con datos anteriores a 2025 y prueba desde 2025. Usa submuestras de entrenamiento de hasta 300.000 y 400.000 filas por RAM. La prueba tiene 340.480 filas.

Resultados guardados: MAE 0,079006, MSE 0,099754, R² −0,183924; la referencia de media histórica logra MAE 0,056677. Clasificación: F1 positiva 0,137757, recall positiva 0,159263 y balanced accuracy 0,560168. El regresor no supera la referencia y la clase positiva tiene baja sensibilidad.

Entrada `ModelLOA/Datos_Procesados/dataset_homicidios_final.csv`; salida `ModelLOA/Resultados/AdaBoost_Semana6/`. Exportaciones no incluidas como archivos independientes. No confundir clasificación binaria con tres clases. Ver [resultados](../../05_Resultados/README.md).
