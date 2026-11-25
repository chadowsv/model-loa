# Resumen de experimentos — salidas guardadas

No se reentrenó ningún modelo. Las cifras se transcriben de los notebooks y CSV del ZIP, redondeadas a seis decimales donde corresponde. No representan un ranking común.

## Avance I (cantón–día; prueba desde 2025)

Fuente: [metricas_regresion.csv](Regresion/metricas_regresion.csv). Media histórica MAE 0,118178, MSE 0,339637, R² 0,249051; regresión lineal MAE 0,164796, MSE 0,333986, R² 0,261544.

## Avance II (distrito–día–franja; 3 clases; prueba desde 18/02/2024)

| Modelo | Accuracy | F1 macro | F1 ponderado |
|---|---:|---:|---:|
| Siempre baja | 0,9693 | 0,3281 | 0,9541 |
| Regresión logística | 0,4186 | 0,2172 | 0,5764 |
| Árbol | 0,6355 | 0,2918 | 0,7579 |
| LinearSVC | 0,8787 | 0,3364 | 0,9127 |

Fuente: [comparativo Avance II](../04_Modelos_ML/Avance_II/Avance_II_Clasificacion_Tres_Modelos%20%281%29%20%282%29.ipynb). El SVM individual registra cifras ligeramente diferentes; no se mezclan.

## Enfoques principales

| Modelo | Unidad / objetivo | Evidencia |
|---|---|---|
| [AdaBoost](../04_Modelos_ML/AdaBoost/) | Franja; regresión | MAE 0,079006; R² −0,183924; media histórica MAE 0,056677 |
| AdaBoost | Franja; binario | Accuracy 0,934886; F1 positiva 0,137757; recall positiva 0,159263 |
| [Random Forest](../04_Modelos_ML/Random_Forest/) | Franja; 3 clases | Umbral 0,35: recall alta 0,913783; precisión alta 0,009755; F1 ponderado 0,440293 |
| [LSTM](../04_Modelos_ML/LSTM/) | Día; regresión | MAE 0,213544; RMSE 0,572936; R² 0,201092 |
| LSTM | Día; binario | Accuracy 0,804124; F1 positiva 0,454792; recall positiva 0,741760; PR-AUC 0,448487 |

AdaBoost/LSTM prueban desde 2025 y Random Forest desde 18/02/2024. RF ajusta/explora umbrales sobre la prueba; requiere nueva evaluación independiente. Los objetivos y granularidades no son homogéneos; no se afirma superioridad definitiva ni utilidad operativa demostrada.
