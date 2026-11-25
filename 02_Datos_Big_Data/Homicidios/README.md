# Homicidios intencionales — fuentes

Fuente indicada en el proyecto: Ministerio del Interior / portal de datos abiertos de Ecuador. [Dataset](https://www.datosabiertos.gob.ec/dataset/homicidios-intencionales).

Archivos requeridos en `MyDrive/ModelLOA/Datos_Iniciales/`:

- `mdi_homicidiosintencionales_pm_2014_2025.xlsx` (39.821 filas según ETL).
- `mdi_homicidiosintencionales_pm_2026_enero_agosto.xlsx` (5.676 filas según ETL).

Hoja en ambos: `1. Homicidios Intencionales`. Mantener los originales separados, de solo lectura y con fecha de descarga registrada por el equipo (no confirmada aquí). Se registraron 45.497 filas combinadas y 5 excluidas por hora inválida en el ETL vigente.

La Fase 2 informa coincidencia de SHA-256 entre originales y copias de Drive; la Fase 3 plantea verificación automática al inicio de notebooks. Ver [seguridad](../../07_Documentacion/Ciberseguridad/README.md). No se ha recalculado el hash aquí porque los Excel no están en el ZIP.
