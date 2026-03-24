---
title: API de funciones de GET V2
description: Referencia de API para la API de funciones de despliegue de experiencias V2, que se utiliza para recuperar indicadores de características para aplicaciones de escritorio.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 11%

---


# API de funciones de GET V2 {#get-feature-api-v2}

La API de funciones V2 está diseñada para la integración de aplicaciones de escritorio. Recupera indicadores de funcionalidades y datos de versiones para el usuario autenticado, lo que admite código de producto y versión de producto como identificador de aplicación, además de un ID de cliente estándar.

**Punto final:** `GET {HOST}/fg/api/v2/feature`

Use `https://p13-stage.adobe.io` para Fase y `https://p13n.adobe.io` para Producción.

## Solicitud {#request}

### Encabezados de solicitud {#request-headers}

| Encabezado | Tipo | Descripción | Requerido |
|---|---|---|---|
| `x-api-key` | Cadena | La clave API de su aplicación de Adobe Developer Console. Debe aprovisionarse por separado para Fase y Producción. | Sí |
| `Authorization` | Cadena | `Bearer <AccessToken>` o `Bearer <ServiceToken>`. | Sí |
| `x-adobe-uuid` | Cadena | Un ID único de visitante o dispositivo. Se utiliza para el despliegue porcentual en escenarios no autenticados y para mantener la permanencia de la sesión. | No |

### Parámetros de consulta {#query-parameters}

| Parámetro | Tipo | Descripción | Requerido |
|---|---|---|---|
| `clientId` | Cadena | El ID de cliente de la aplicación, tal como se incorpora en la consola Despliegues de experiencias. Se pueden pasar varios valores: `clientId=C1&clientId=C2`. | No |
| `p` | Cadena | Product, version, platform, locale string (formato PVPL). Ejemplo: `PHSP:17.0:WIN:en_US`. Se pueden pasar varios valores: `p=PHSP:17.0:WIN:en_US&p=PPRO:8:WIN:en_US`. En la evaluación solo se utilizan el código y la versión del producto. | No |
| `meta` | Booleano | Si es `true`, se devuelven metadatos codificados en Base64 para cada característica. Predeterminado: `false`. | No |
| *Parámetros de contexto* | N/A | Cualquier par clave-valor adicional se trata como una variable de contexto para la evaluación de reglas de audiencia. Ejemplo: `clientLanguage=ja_JP&contractCurrency=JPY`. | No |

>[!NOTE]
>
>Se requiere al menos uno de `clientId` o `p` para identificar la aplicación.

## Respuesta {#response}

### Códigos de estado de respuesta {#response-status}

| Código de estado | Descripción |
|---|---|
| `200 OK` | Datos de indicador de funcionalidad devueltos en el cuerpo de respuesta. |
| `304 Not Modified` | ETag coincide con el estado actual del servidor. Tratar como una operación no operativa: no hay cambios que aplicar. |
| `401 Unauthorized` | El token de autorización no es válido. |

### Encabezados de respuesta {#response-headers}

| Encabezado | Descripción |
|---|---|
| `x-request-id` | Un identificador de solicitud único para la depuración. Incluya esto en cualquier solicitud de asistencia. |
| `ETag` | Token que representa el estado actual de la función para el usuario. Pasar como `If-None-Match` en solicitudes posteriores. Devuelve `304` si no se ha modificado. |
| `x-adobe-fg-poll-interval` | TTL en segundos para la caché local del cliente. Vuelva a llamar a la API solo después de que transcurra este intervalo. |

### Cuerpo de respuesta {#response-body}

La respuesta es un objeto JSON con los siguientes campos de nivel superior:

| Campo | Tipo | Descripción |
|---|---|---|
| `api_version` | Cadena | Versión de API. Campo interno: no se requiere procesamiento. |
| `json_version` | Cadena | Versión de esquema JSON. Campo interno: no se requiere procesamiento. |
| `ttl` | Número entero | TTL de caché en segundos. Predeterminado: 300. |
| `clients` | Objeto | Asignación de ID de cliente (o cadenas de VPL) a sus datos de versión. Cada clave contiene los campos que se describen a continuación. |

#### Campos de respuesta por cliente {#per-client-fields}

| Campo | Descripción |
|---|---|
| `releases` | Matriz de versiones para las que el usuario es apto. Consulte [campos de versiones](#releases-fields) a continuación. |
| `client_analytics_params` | Objeto de configuración de Analytics. Consulte [campos client_analytics_params](#analytics-fields) a continuación. |

#### campos de versiones {#releases-fields}

| Campo | Descripción |
|---|---|
| `release_name` | Nombre de la versión o del grupo de funciones. |
| `bit_index` | Liberar índice de bits. Obsoleto. Puede ser `null` o negativo según el estado de la versión. |
| `features` | Matriz de claves de indicador de funcionalidad para las que el usuario es apto. Las claves de función solo aparecen si el usuario cumple los requisitos y el indicador está activado. |
| `meta` | Metadatos codificados en Base64 opcionales. Descodificar antes de utilizar. |
| `release_analytics_params` | Metadatos de Analytics para funciones aptas. En los escenarios del grupo de control, `features` está vacío. |

#### campos release_analytics_params {#release-analytics-params}

| Campo | Tipo | Descripción |
|---|---|---|
| `app_id` | Número entero | ID de aplicación. |
| `release_id` | Número entero | ID de versión. |
| `bit_index` | Número entero | Obsoleto. |
| `variant_id` | Número entero | `0` si es el grupo de control; distinto de cero en caso contrario. |
| `feature_id` | Número entero | ID de función interna. |
| `f_key` | Cadena | Tecla de indicador de funcionalidad. |

#### campos client_analytics_params {#analytics-fields}

| Campo | Tipo | Descripción |
|---|---|---|
| `app_id` | Número entero | ID de aplicación. |
| `safe_event_required` | Booleano | `true` si los eventos de retargeting están habilitados. |
| `analytics_required` | Booleano | `false` si el análisis está deshabilitado o en un flujo predeterminado; `true` si el flujo Kinesis está habilitado. |

## Solicitud y respuesta de ejemplo {#sample}

### Solicitud de ejemplo {#sample-request}

```http
GET /fg/api/v2/feature?clientId=MyDesktopApp&p=PHSP:17.0:WIN:en_US&meta=true HTTP/1.1
Host: p13n.adobe.io
Authorization: Bearer <ACCESS_TOKEN>
x-api-key: <YOUR_API_KEY>
If-None-Match: <ETAG>
```

### Respuesta de muestra {#sample-response}

```json
{
  "api_version": "0.1",
  "json_version": "0.1",
  "clients": {
    "PHSP:17.0:WIN:en_US": {
      "analyticsVersion": "1.0",
      "releases": []
    },
    "MyDesktopApp": {
      "analyticsVersion": "1.0",
      "client_analytics_params": {
        "app_id": 388,
        "safe_event_required": false,
        "analytics_required": false
      },
      "releases": [
        {
          "bit_index": 160,
          "release_name": "||features||",
          "features": ["feature_a", "feature_b"],
          "release_analytics_params": [
            {
              "app_id": 388,
              "release_id": -1,
              "bit_index": 160,
              "variant_id": 10031741,
              "feature_id": 2918,
              "f_key": "feature_a"
            }
          ],
          "meta": []
        }
      ]
    }
  },
  "ttl": 300
}
```

## Consulte también {#see-also}

* [API de funciones de GET V3](get-feature-api-v3.md)
* [Aplicaciones de escritorio](../guides/integrate/desktop-applications.md)
* [Pasos de integración](../guides/integrate/integration-steps.md)
