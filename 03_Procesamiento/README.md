# Procesamiento, limpieza y análisis exploratorio

Notebook vigente: [Procesamiento_DatasetModelo.ipynb](Procesamiento_DatasetModelo.ipynb). Lee dos XLSX separados y el calendario CSV; valida código territorial, fecha y hora; agrega por provincia/distrito/día/franja; completa combinaciones, une feriados, genera variables de calendario y categorías; realiza EDA y exporta el CSV.

| Evidencia de salida | Valor |
|---|---:|
| Registros combinados | 45.497 |
| Válidos para agregación | 45.492 |
| Excluidos (hora inválida) | 5 |
| Unidades observadas antes de completar | 36.000 |
| Unidades finales | 2.590.560 |
| Ceros completados/observados | 2.554.560 (98,61 %) |
| Baja / media / alta | 2.554.560 / 29.994 / 6.006 |
| Columnas exportadas | 12 |

**Entrada:** `MyDrive/ModelLOA/Datos_Iniciales/`. **Salida:** `MyDrive/ModelLOA/Datos_Procesados/dataset_homicidios_final.csv`, fecha `dd/mm/aaaa`. Crear la carpeta de salida si falta. Ver [diccionario](diccionario_dataset.md).

La expansión temporal introduce el supuesto de cero para combinaciones sin registro, no demuestra cobertura completa. Cinco registros se separan para revisión; no confundir con el Avance I (cantón–día). El umbral alta = 2 procede de la ejecución guardada; para evaluar generalización definirlo con el periodo de entrenamiento.

**Alternativas de procesamiento:** pandas implementado; Polars y PySpark propuestos. Falta comparar tiempos, memoria, consistencia de resultados y complejidad sobre los mismos insumos; no se inventan benchmarks. [Histórico](Historico/README.md) conserva el entregable inicial sin modificarlo.
