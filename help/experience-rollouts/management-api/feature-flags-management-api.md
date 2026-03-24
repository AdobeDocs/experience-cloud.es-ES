---
title: API de administración de indicadores de funcionalidad
description: Referencia de la API para la API de administración de indicadores de funcionalidades de los despliegues de experiencias, incluidos los puntos finales para obtener, crear, actualizar y eliminar indicadores de funcionalidades para una aplicación.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 12%

---


# API de administración de indicadores de funcionalidad {#feature-flags-management-api}

La API de administración de indicadores de funcionalidades le permite crear, leer, actualizar y eliminar mediante programación indicadores de funcionalidades para sus aplicaciones en Despliegues de experiencias.

**Ruta básica:** `/m/api/v1/mgmt/feature`

Todas las solicitudes requieren los encabezados descritos en los [requisitos comunes](feature-management-apis-overview.md#common-requirements).

## Obtener todos los indicadores de características {#get-all-features}

Recupera todos los indicadores de características de una aplicación especificada.

| | |
|---|---|
| **Extremo** | `GET /m/api/v1/mgmt/feature` |
| **Método** | GET |

### Parámetros de consulta {#get-all-query-params}

| Parámetro | Tipo | Descripción | Requerido |
|---|---|---|---|
| `clientId` | Número entero | ID numérica de la aplicación. Consulte [Obtener ID de cliente](get-client-id.md). Obligatorio si no se proporciona `imsClientId`. | Condicional |
| `imsClientId` | Cadena | ID de cliente de formato de cadena de la aplicación. Obligatorio si no se proporciona `clientId`. | Condicional |
| `nonReleaseFeature` | Booleano | Se establece en `true` para incluir indicadores de características independientes no asociados a ningún grupo o versión. Necesario para flujos de trabajo basados en API. | Sí |

### Respuesta {#get-all-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de la respuesta contiene una lista de objetos de indicador de funcionalidad. |

El cuerpo de respuesta contiene una matriz `features`. Cada elemento es un objeto de indicador de características con los campos descritos en la [referencia de objeto FeatureDTO](#featuredto-object).

**Respuesta de muestra:**

```json
{
  "features": [
    {
      "id": 22079,
      "name": "new.FF.1",
      "clientId": 1191,
      "state": "enabled",
      "description": "first feature flag",
      "release": { "id": 2631, "name": "FF.group", "status": "SAVED" },
      "audience": null,
      "params": { "label": "new FF 1", "rolloutType": "manual" }
    },
    {
      "id": 22080,
      "name": "new.FF.2",
      "clientId": 1191,
      "state": "enabled",
      "description": "second feature flag",
      "audience": [
        {
          "id": 10034665,
          "criteria": { "and": [{ "operator": "EQ", "attr": "LOCALE", "val": "EN" }] }
        }
      ]
    }
  ]
}
```

## Obtener indicador de funcionalidad por identificador {#get-feature-by-id}

Recupera un único indicador de funcionalidad por su ID numérico.

| | |
|---|---|
| **Extremo** | `GET /m/api/v1/mgmt/feature/{featureId}` |
| **Método** | GET |

### Respuesta {#get-by-id-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de la respuesta es un único [objeto FeatureDTO](#featuredto-object). |
| `400` | ID de función no válido. |

## Crear indicador de funcionalidad {#create-feature}

Crea un nuevo indicador de funcionalidad.

| | |
|---|---|
| **Extremo** | `POST /m/api/v1/mgmt/feature` |
| **Método** | PUBLICAR |

### Cuerpo de solicitud {#create-request-body}

El cuerpo de la solicitud es un [objeto FeatureDTO](#featuredto-object). Se requieren los siguientes campos para la creación:

| Campo | Requerido | Notas |
|---|---|---|
| `name` | Sí | Tecla de indicador de funcionalidad. Máximo de 50 caracteres. Patrón: `^[a-zA-Z0-9_.-]*$` |
| `clientId` | Sí | ID de aplicación numérica. Consulte [Obtener ID de cliente](get-client-id.md). |
| `state` | Sí | `"enabled"` o `"disabled"` |

### Respuesta {#create-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de la respuesta contiene `{ "generatedFeatureId": <id> }`. |
| `400` | Carga no válida. |
| `403` | Permisos insuficientes para este cliente o regla de audiencia. |
| `417` | Los usuarios con el rol de Desarrollador no pueden guardar una función con una regla pública; se requiere al menos una regla de audiencia. |

**Solicitud de ejemplo:**

```json
{
  "name": "my-new-feature",
  "clientId": 1191,
  "state": "disabled",
  "description": "A new feature flag",
  "meta": "VGVzdA==",
  "audience": [
    {
      "criteria": {
        "and": [{ "operator": "EQ", "attr": "COUNTRY", "category": "default", "ruleId": 1, "val": "US" }]
      }
    }
  ],
  "variations": [{ "variantPercentage": 100, "variantName": "Variation 1" }],
  "params": { "label": "My New Feature", "tags": [] }
}
```

## Actualizar indicador de funcionalidad {#update-feature}

Actualiza una marca de característica existente. Pase el objeto [FeatureDTO](#featuredto-object) completo, incluido el campo `id`.

| | |
|---|---|
| **Extremo** | `PUT /m/api/v1/mgmt/feature` |
| **Método** | PUT |

### Respuesta {#update-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de la respuesta es el objeto FeatureDTO actualizado. |
| `400` | Carga no válida. |
| `403` | Permisos insuficientes. |
| `417` | Conflicto de actualización simultánea. Recupere primero la característica actual y vuelva a intentarlo con el último valor `version` de `params`. |

## Eliminar indicador de funcionalidad {#delete-feature}

Elimina una marca de característica por su ID numérico.

| | |
|---|---|
| **Extremo** | `DELETE /m/api/v1/mgmt/feature/{featureId}` |
| **Método** | DELETE |

### Respuesta {#delete-response}

| Estado | Descripción |
|---|---|
| `204` | Correcto. No hay cuerpo de respuesta. |
| `403` | Permisos insuficientes. |

## Referencia de objeto FeatureDTO {#featuredto-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de indicador de funcionalidad. Solo es necesario para las llamadas de actualización. | Condicional |
| `name` | Cadena | Clave de indicador de funcionalidad (devuelta en las respuestas de API). Máximo 50 caracteres. Patrón: `^[a-zA-Z0-9_.-]*$` | Sí (crear) |
| `clientId` | Número entero | ID de aplicación numérica. | Sí |
| `state` | Cadena | `"enabled"` o `"disabled"` | Sí |
| `meta` | Cadena | Los metadatos codificados en Base64 devueltos con la función en las respuestas de API. Máx. 1024 caracteres. | No |
| `description` | Cadena | Descripción para mostrar. Máx. 225 caracteres. | No |
| `audience` | Matriz | Lista de reglas de audiencia. Consulte [Objeto FeatureRule](#featurerule-object). Use [Obtener los criterios de audiencia deseados](get-audience-criteria.md) para generar esto. | No |
| `variations` | Matriz | Lista de variantes. Máx. 3. Consulte [Objeto FeatureVariation](#featurevariation-object). | No |
| `params` | Objeto | Metadatos adicionales. Claves compatibles: `label` (nombre para mostrar en la interfaz de usuario), `tags` (matriz de cadenas). | No |
| `release` | Objeto | Asociación de versión/grupo. `null` si el indicador no está en un grupo. Sólo lectura. | No |

### Objeto FeatureVariation {#featurevariation-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de variación. Solo es necesario para las llamadas de actualización. | Condicional |
| `variantName` | Cadena | Nombre de variante. Valores fijos: `"Variation 1"`, `"Variation 2"`, `"Variation 3"`. | Sí |
| `variantPercentage` | Decimal | Porcentaje de audiencia que recibe esta variante. Debe ser mayor que 0 y no más de 100, con hasta 2 decimales. | Sí |

### Objeto FeatureRule {#featurerule-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de regla. Solo es necesario para las llamadas de actualización. Se establece en `null` al agregar una regla nueva. | Condicional |
| `criteria` | Objeto | Objeto de condición que define la regla de audiencia. Ver [objeto de condición](#condition-object). | Sí |

### Objeto Condition {#condition-object}

| Campo | Tipo | Descripción |
|---|---|---|
| `and` | Matriz\&lt;Condición\> | Todas las condiciones deben ser verdaderas. |
| `or` | Matriz\&lt;Condición\> | Al menos una condición debe ser verdadera. |
| `not` | Condición | Esta condición debe ser falsa. |
| `attr` | Cadena | Atributo de usuario que se va a evaluar (por ejemplo, `COUNTRY`, `LOCALE`). |
| `operator` | Cadena | Operador de comparación (por ejemplo, `EQ`, `IN`, `LT`). |
| `val` | Cadena | Valor con el que comparar. |
| `meta` | Objeto | Metadatos de condición opcionales. `desc` establece la etiqueta de visualización en la interfaz de usuario. |

Se debe proporcionar uno de `and`, `or` o `not`, o una combinación de `attr`, `operator` y `val` en cada condición.

## Consulte también {#see-also}

* [Información general sobre las API de administración de funciones](feature-management-apis-overview.md)
* [API de parche de administración](management-patch-api.md)
* [Obtener el ID de cliente de una aplicación](get-client-id.md)
* [Obtener los criterios de audiencia deseados](get-audience-criteria.md)
