# Documentación de la API de Feriados

## 1. Descripción general

La API de feriados permite consultar los días festivos de un país para un año específico. En este proyecto, se utilizará para identificar si la fecha de cada registro histórico corresponde a un feriado nacional.

Esta información servirá como una variable adicional para entrenar un modelo de aprendizaje automático que estime la categoría de la tasa de homicidios en un cantón, considerando variables temporales, geográficas y contextuales.

## 2. Información del servicio

| Propiedad | Descripción |
|---|---|
| Servicio | API de feriados |
| Método HTTP | `GET` |
| Endpoint | `/v1/{country}/holidays/{year}` |
| País objetivo | Ecuador |
| Código de país | `EC` |
| Parámetro temporal | Año de consulta |
| Formato de respuesta | JSON |

## 3. Endpoint de consulta

### 3.1. Descripción

El endpoint retorna la lista de feriados correspondientes al país y año especificados.

Se consultará el calendario anual de feriados de Ecuador para identificar las fechas festivas que coincidan con los registros del conjunto de datos históricos.

### 3.2. Parámetros de ruta

| Parámetro | Tipo | Obligatorio | Descripción |
|---|---|---|---|
| `country` | `string` | Sí | Código ISO 3166-1 alpha-2 del país. Para Ecuador se utiliza `EC`. |
| `year` | `integer` | Sí | Año para el cual se desea consultar los feriados. El rango admitido por la API es de 1900 a 2100. |

### 3.3. Ejemplo de solicitud

```http
GET /v1/EC/holidays/2025
Accept: application/json
```

Esta solicitud obtiene los feriados de Ecuador correspondientes al año 2025.

## 4. Estructura de la respuesta

La API devuelve un objeto JSON con el resultado de la operación, la lista de feriados y metadatos de la consulta.

### 4.1. Ejemplo de respuesta

El siguiente ejemplo ilustra la estructura esperada; los datos son demostrativos y no representan una consulta verificada al servicio.

```json
{
  "success": true,
  "data": [
    {
      "date": "2025-01-01",
      "name": "Año Nuevo",
      "type": "national"
    },
    {
      "date": "2025-05-01",
      "name": "Día del Trabajo",
      "type": "national"
    }
  ],
  "meta": {
    "country": "EC",
    "year": 2025,
    "total": 2
  }
}
```

### 4.2. Descripción de los campos

| Campo | Tipo | Descripción |
|---|---|---|
| `success` | `boolean` | Indica si la consulta fue procesada correctamente. |
| `data` | `array` | Contiene los feriados encontrados. |
| `data[].date` | `string` | Fecha observada del feriado en formato `YYYY-MM-DD`. |
| `data[].name` | `string` | Nombre del feriado. |
| `data[].type` | `string` | Tipo de feriado, por ejemplo, `national`. |
| `data[].original_date` | `string` | Fecha nominal original, cuando el feriado fue trasladado. |
| `data[].mandatory_rest` | `boolean` | Indica si el día constituye descanso obligatorio en los casos en que este campo aparece. |
| `meta.country` | `string` | Código del país consultado. |
| `meta.year` | `integer` | Año consultado. |
| `meta.total` | `integer` | Cantidad de feriados devueltos. |
| `meta.warning` | `object` | Advertencias sobre la precisión histórica, cuando corresponda. |

Los campos opcionales deben tratarse de forma segura, ya que no necesariamente estarán presentes en todos los registros.

## 5. Integración con el conjunto de datos

### 5.1. Propósito de la integración

La API no se utilizará para predecir directamente los homicidios. Su función será proporcionar información contextual que permita identificar los días festivos de cada año.

La integración seguirá este proceso:

1. Obtener las fechas de los registros históricos de homicidios.
2. Identificar los años presentes en el conjunto de datos.
3. Consultar una vez los feriados de cada año necesario.
4. Construir un conjunto de fechas de feriados.
5. Comparar las fechas de los registros históricos con dicho conjunto.
6. Crear una variable binaria denominada `es_feriado`.
7. Incorporar la variable al conjunto de datos utilizado para entrenar el modelo.

### 5.2. Variable generada

| Variable | Tipo | Valores | Descripción |
|---|---|---|---|
| `es_feriado` | `int` | `0`, `1` | Indica si la fecha del registro corresponde a un feriado reconocido por la API. |

Interpretación:

- `1`: la fecha coincide con un feriado.
- `0`: la fecha no coincide con un feriado.

Esta variable podrá utilizarse junto con otras características, como el cantón, la zona geográfica, el día de la semana, la hora y el mes.

## 6. Estrategia de consulta y almacenamiento

Para optimizar el procesamiento del conjunto de datos:

1. Extraer los años únicos presentes en los registros históricos.
2. Consultar el endpoint una vez por cada año requerido.
3. Almacenar las respuestas en archivos JSON o en una tabla auxiliar.
4. Mantener un registro de la fecha de consulta y la versión o procedencia de los datos.
5. Reutilizar la información almacenada durante el entrenamiento.
6. Actualizar los datos cuando se incorporen nuevos años o se detecten modificaciones en el calendario.

Esta estrategia reduce las solicitudes a la API y mejora la reproducibilidad de los experimentos de entrenamiento.

## 7. Referencia

- **Proveedor:** Feriados.io.
- **Endpoint:** `GET /v1/{country}/holidays/{year}`.
- **Documentación:** https://feriados.io/docs