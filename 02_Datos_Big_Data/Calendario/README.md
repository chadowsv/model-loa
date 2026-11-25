# Calendario de feriados — integración ejecutada

Notebook: [Feriados.ipynb](Feriados.ipynb). Consulta `GET https://api.feriados.io/v1/EC/holidays/{year}` de 2014 a 2026, con `Authorization: Bearer` y credencial `API_Feriados` en Secrets de Colab. La salida guardada informa 173 registros.

El archivo `feriados_ecuador_2014_2026.csv` contiene `fecha` (AAAA/MM/DD) y `nombre_feriado`. La ruta de salida del notebook es `/content/drive/MyDrive/00_Proyecto_Sexto/Datos_Iniciales/`. Copiar al directorio `ModelLOA/Datos_Iniciales/` antes de ejecutar el ETL. No modificar credenciales ni publicar claves. Comprobar años fallidos, duplicados y cobertura antes de usar el CSV. El archivo de salida no está incluido en el ZIP.

Ver [documentación API](../API_feriados.md) y [ETL](../../03_Procesamiento/README.md). Feriados son variables contextuales, no evidencia causal.
