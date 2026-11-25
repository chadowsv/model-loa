# Diccionario del dataset vigente

Fuente: notebook de procesamiento y columnas requeridas por los modelos. Clave: provincia + distrito + fecha + franja. Conservar los códigos geográficos como texto.

| Campo | Descripción |
|---|---|
| `codigo_provincia` | Código de provincia extraído de subcircuito |
| `codigo_distrito` | Identificador de distrito con prefijo de provincia |
| `fecha` | Día de observación; exportado dd/mm/aaaa |
| `franja_horaria` | madrugada (00–05), manana (06–11), tarde (12–17), noche (18–23) |
| `total_homicidios` | Conteo de registros de víctimas por unidad |
| `es_feriado` | Indicador de calendario, normalizar 0/1 según modelo |
| `nombre_feriado` | Nombre asociado a la fecha, según calendario |
| `categoria_incidencia` | baja (0), media (1), alta (≥2) en el corte guardado |
| `anio` | Año |
| `mes` | Mes |
| `dia_semana_num` | 0 = lunes, 6 = domingo |
| `dia_semana` | Nombre del día de semana |

No incorporar `total_homicidios` ni `categoria_incidencia` del día objetivo como predictores. `hubo_homicidios` es una variable derivada por los notebooks binarios, no una de las 12 columnas del CSV base.
