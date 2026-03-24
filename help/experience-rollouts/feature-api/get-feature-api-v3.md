---
title: API de funciones de GET V3
description: Referencia de la API para la API de funciones de despliegue de experiencias V3, que se utiliza para recuperar indicadores de funcionalidades para aplicaciones web y móviles.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 9%

---


# API de funciones de GET V3 {#get-feature-api-v3}

La API de funciones V3 es el punto final principal para recuperar indicadores de funciones en aplicaciones web y móviles. Devuelve las funciones y versiones para las que un usuario es apto, según su identidad y las reglas de audiencia configuradas en la consola.

**Punto final:** `GET {HOST}/fg/api/v3/feature`

Use `https://p13-stage.adobe.io` para Fase y `https://p13n.adobe.io` para Producción.

## Solicitud {#request}

### Encabezados de solicitud {#request-headers}

| Encabezado | Tipo | Descripción | Requerido |
|---|---|---|---|
| `x-api-key` | Cadena | La clave API de su aplicación de Adobe Developer Console. Debe aprovisionarse por separado para Fase y Producción. | Sí |
| `Authorization` | Cadena | **No se requiere** para escenarios no autenticados. Use `Bearer <AccessToken>` para usuarios autenticados. Utilice `Bearer <ServiceToken>` para escenarios de almacenamiento en caché de SDK del lado del servidor. | No |
| `x-adobe-uuid` | Cadena | Un ID único de visitante o dispositivo. Se utiliza para admitir el despliegue porcentual para usuarios no autenticados y para mantener la permanencia entre sesiones y transiciones no autenticadas a autenticadas. | No |

### Parámetros de consulta {#query-parameters}

| Parámetro | Tipo | Descripción | Requerido |
|---|---|---|---|
| `clientId` | Cadena | El ID de cliente de la aplicación, tal como se incorpora en la consola Despliegues de experiencias. | Sí |
| `ignore_rf` | Booleano | Si se selecciona `true`, se omiten los indicadores de versión y se devuelven todas las versiones para el cliente. Predeterminado: `false`. | No |
| `rf` | Cadena | Indicador de lanzamiento. Solo se usa cuando `ignore_rf` es `false`. | No |
| `meta` | Booleano | Si `true`, los metadatos de cada característica se incluyen en la respuesta, devueltos como un par clave-valor donde el valor tiene codificación Base64. Predeterminado: `false`. | No |
| `userId` | Cadena | Requiere un token de servicio. GUID del usuario para el que desea recuperar indicadores de características. | No |
| *Parámetros de contexto* | N/A | Cualquier parámetro de consulta no enumerado anteriormente se trata como variable de contexto y se utiliza para evaluar reglas de audiencia. Pasar varios valores como `?key1=val1&key2=val2`. Ejemplo: `?clientLanguage=ja_JP&contractCurrency=JPY`. | No |

## Respuesta {#response}

### Códigos de estado de respuesta {#response-status}

| Código de estado | Descripción |
|---|---|
| `200 OK` | Datos de indicador de funcionalidad devueltos en el cuerpo de respuesta. |
| `304 Not Modified` | La etiqueta ETag pasada por el cliente coincide con el estado del servidor más reciente. Trate esto como una operación no operativa: no hay cambios que aplicar. |
| `400 Bad Request` | `clientId` no se ha incorporado o la solicitud no tiene el formato correcto. |
| `403 Forbidden` | Clave de API no válida o la aplicación no está suscrita a la API de despliegues de experiencias en Adobe Developer Console. |

### Encabezados de respuesta {#response-headers}

| Encabezado | Descripción |
|---|---|
| `x-request-id` | Un identificador de solicitud único para la depuración. Incluya esto en cualquier solicitud de asistencia. |
| `ETag` | Un token que representa el estado actual del servidor para las características de este usuario. Pase este valor como `If-None-Match` en solicitudes posteriores. Si el estado no ha cambiado, la API devuelve `304`. |
| `x-adobe-fg-poll-interval` | El TTL (en segundos) para la caché local del cliente. Vuelva a llamar a la API solo después de que haya transcurrido este intervalo. |

### Cuerpo de respuesta {#response-body}

La respuesta es un objeto JSON con los siguientes campos de nivel superior:

| Campo | Tipo | Descripción |
|---|---|---|
| `api_version` | Cadena | Versión de API. Campo interno: no se requiere procesamiento. |
| `json_version` | Cadena | Versión de esquema JSON. Campo interno: no se requiere procesamiento. |
| `ttl` | Número entero | TTL de caché en segundos. El mismo valor que el encabezado de respuesta `x-adobe-fg-poll-interval`. Predeterminado: 300. |
| `caching_enabled` | Booleano | Si se usa `true`, la evaluación de características se realiza localmente en el cliente. Si se selecciona `false`, la evaluación se realiza en el servidor en cada solicitud. |
| `client_analytics_params` | Objeto | Configuración de Analytics para la aplicación. Consulte [campos client_analytics_params](#client-analytics-params) a continuación. |
| `releases` | Matriz | Lista de versiones e indicadores de funciones para los que el usuario es apto. Consulte [campos de versiones](#releases-fields) a continuación. |

#### campos client_analytics_params {#client-analytics-params}

| Campo | Descripción |
|---|---|
| `app_id` | El ID numérico de la aplicación. |
| `safe_event_required` | `true` si los eventos de retargeting están habilitados para este cliente. |
| `analytics_required` | Siempre `false` en respuestas V3. |

#### campos de versiones {#releases-fields}

| Campo | Descripción |
|---|---|
| `release_name` | El nombre de la versión o del grupo de funciones para el que el usuario es apto. |
| `bit_index` | El índice de bits de lanzamiento. Los valores negativos indican un estado de Despliegue completo. |
| `features` | Matriz de claves de indicador de funcionalidad para las que el usuario es apto. Solo se devuelve una clave de función si el usuario cumple los requisitos y el indicador está en estado habilitado. Este es el campo principal en el que debe basarse la lógica de la aplicación. |
| `meta` | Metadatos codificados en Base64 opcionales asociados con la función. Descodificar antes de utilizar. |
| `release_analytics_params` | Matriz de objetos de metadatos de análisis para cada función elegible. Consulte [campos release_analytics_params](#release-analytics-params) a continuación. En los escenarios del grupo de control, `features` está vacío. |

#### campos release_analytics_params {#release-analytics-params}

| Campo | Tipo | Descripción |
|---|---|---|
| `app_id` | Número entero | ID de aplicación. |
| `release_id` | Número entero | ID de versión. |
| `bit_index` | Número entero | Liberar índice de bits. Obsoleto. |
| `variant_id` | Número entero | `0` si el usuario está en el grupo de control; en caso contrario, distinto de cero. |
| `feature_id` | Número entero | ID de función interna. |
| `f_key` | Cadena | Tecla de indicador de funcionalidad. |

## Solicitud y respuesta de ejemplo {#sample}

### Solicitud de ejemplo {#sample-request}

```http
GET /fg/api/v3/feature?clientId=MyWebApp&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Respuesta de muestra: usuario del grupo de prueba {#sample-response-test}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "analyticsVersion": "2.0",
      "client_analytics_params": {
        "app_id": 1378,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": ["ff1", "ff2", "ff3"],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 10040476,
              "feature_id": 26059,
              "f_key": "ff1",
              "analytics_required": true
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

### Respuesta de muestra: usuario del grupo de control {#sample-response-control}

Cuando un usuario está en el grupo de control, la matriz `features` está vacía y `variant_id` es `0`:

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "MyWebApp": {
      "releases": [
        {
          "bit_index": -160,
          "release_name": "||features||",
          "features": [],
          "release_analytics_params": [
            {
              "app_id": 1378,
              "release_id": -1,
              "bit_index": -160,
              "variant_id": 0,
              "feature_id": 26059,
              "f_key": "ff1"
            }
          ]
        }
      ]
    }
  },
  "ttl": 60
}
```

## Consulte también {#see-also}

* [API de funciones de GET V2](get-feature-api-v2.md)
* [Aplicaciones web](../guides/integrate/web-applications.md)
* [Aplicaciones móviles](../guides/integrate/mobile-applications.md)
* [Pasos de integración](../guides/integrate/integration-steps.md)
