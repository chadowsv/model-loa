# Random Forest

[RandomForestModel.ipynb](RandomForestModel.ipynb): RandomForestClassifier con 100 árboles, profundidad máxima 12, `class_weight="balanced"`, semilla 42. Clasifica baja/media/alta por provincia–distrito–fecha–franja. Corte 18/02/2024 (prueba 518.560 filas).

Umbral explorado en prueba: 0,35; recall alta 0,913783, precisión alta 0,009755, recall media 0,093935 y F1 ponderado 0,440293. Es un análisis exploratorio, no una validación independiente; seleccionar el umbral en validación y medir una prueba reservada. La precisión baja implica muchos falsos positivos.

Entrada `ModelLOA/Datos_Procesados/dataset_homicidios_final.csv`. No se adjuntan exportaciones CSV de este modelo. Ver [clasificación](../../05_Resultados/Clasificacion/README.md).
