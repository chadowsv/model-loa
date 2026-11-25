# Avance II — clasificación supervisada multiclase

- [Notebook comparativo de tres modelos](Avance_II_Clasificacion_Tres_Modelos%20%281%29%20%282%29.ipynb): regresión logística, árbol de decisión y LinearSVC; muestra de entrenamiento común de 300.000 filas y prueba de 518.560 filas desde 18/02/2024.
- [DecisionTreeModel](DecisionTreeModel.ipynb) y [SVMModel](SVMModel%20%281%29.ipynb): experimentos individuales conservados.

Las clases baja, media y alta están muy desbalanceadas. En la comparación guardada, F1 macro = 0,2172 / 0,2918 / 0,3364 respectivamente, frente a 0,3281 de siempre baja. Accuracy de la referencia = 0,9693. SVM casi no detecta la clase media; no basta accuracy o F1 ponderado. Exportación del comparativo está desactivada (`EXPORTAR = False`). Ver [clasificación](../../05_Resultados/Clasificacion/README.md).
