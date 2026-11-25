# Datos y Big Data

Fuentes vigentes: [homicidios oficiales](Homicidios/README.md) y [feriados](Calendario/README.md), con [documentación de API](API_feriados.md). ECU 911 se excluyó según Fase 2, p. 3. Los datos fuente y el dataset procesado permanecen en Drive restringido; esta carpeta no contiene los Excel ni CSV completos.

## Rutas actuales de Colab (no modificadas)

```text
MyDrive/ModelLOA/
├── Datos_Iniciales/    # dos Excel y calendario CSV
├── Datos_Procesados/   # dataset_homicidios_final.csv
└── Resultados/         # exportaciones de modelos
```

Fase 3 propone `01_originales`, `02_procesados`, `03_notebooks`, `04_resultados` y permisos por rol. Esa estructura es una medida de seguridad en proceso: coordinar la migración antes de cambiar las rutas ejecutables. El notebook de feriados todavía utiliza `00_Proyecto_Sexto/Datos_Iniciales/`; copiar su CSV a la ruta del ETL.
