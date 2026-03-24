---
title: API de administración de versiones
description: Referencia de la API para las API de administración de versiones de los despliegues de experiencia, incluidos los puntos de conexión para obtener, crear y editar versiones y grupos de funciones entre equipos.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 13%

---


# API de administración de versiones {#release-management-apis}

Las API de administración de versiones le permiten recuperar, crear y editar versiones y grupos de funciones entre equipos (CTFG) mediante programación. Estas API utilizan el extremo de administración de la versión 2.

**Ruta básica:** `/m/api/v2/mgmt/release`

Todas las solicitudes requieren los encabezados descritos en los [requisitos comunes](feature-management-apis-overview.md#common-requirements), además del encabezado adicional que se enumera a continuación.

## Encabezado adicional obligatorio {#additional-header}

| Encabezado | Descripción | Requerido |
|---|---|---|
| `x-user-context-org` | El ID de equipo numérico de su organización. Puede encontrar este valor en la consola Despliegues de experiencias en la configuración de su equipo. | Sí |

## Obtener versión por ID {#get-release}

Recupera una sola versión o grupo de funciones entre equipos por su ID numérico.

| | |
|---|---|
| **Extremo** | `GET /m/api/v2/mgmt/release/{id}` |
| **Método** | GET |

### Parámetros de consulta {#get-query-params}

| Parámetro | Tipo | Descripción | Predeterminado |
|---|---|---|---|
| `includePermissions` | Booleano | Incluya permisos para actualizar o eliminar esta versión. | `true` |
| `includeOrg` | Booleano | Incluya información de la organización en esta versión. | `true` |
| `includeAnalyzeInfo` | Booleano | Incluya información de análisis. | `false` |

### Respuesta {#get-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es un objeto de versión; consulte [Referencia de objeto de versión](#release-object). |
| `400` | ID de versión o solicitud mal formada no válidos. |

## Crear versión {#create-release}

Crea una nueva versión o un grupo de funciones entre equipos.

| | |
|---|---|
| **Extremo** | `POST /m/api/v2/mgmt/release` |
| **Método** | PUBLICAR |

### Cuerpo de solicitud {#create-request-body}

El cuerpo de la solicitud usa el [objeto Release](#release-object). Para la creación, `status` debe establecerse en `"SAVED"` para los grupos de características entre equipos (`CROSS_TEAM_FEATURE_GROUP` tipo) o en `"DRAFT"` para las versiones estándar (`RELEASE` tipo).

**Ejemplo — crear grupo de características entre equipos:**

```json
{
  "params": {
    "rolloutType": "manual",
    "cohortingType": "guid",
    "tags": [],
    "canContextOverridePUP": false,
    "label": "my-cross-team-group"
  },
  "status": "SAVED",
  "type": "CROSS_TEAM_FEATURE_GROUP",
  "name": "my-cross-team-group",
  "description": null,
  "meta": "",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{}],
  "clients": [],
  "pollInterval": 300,
  "org": { "id": "95" },
  "comment": ""
}
```

### Respuesta {#create-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es el objeto de versión creado. |
| `400` | Carga no válida. |

## Editar versión {#edit-release}

Actualiza una versión existente o un grupo de funciones entre equipos. Pase el objeto de versión completo, incluido el campo `id`.

| | |
|---|---|
| **Extremo** | `PUT /m/api/v2/mgmt/release/{id}` |
| **Método** | PUT |

### Respuesta {#edit-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es el objeto de versión actualizado. |
| `417` | Conflicto de actualización simultánea. La versión se modificó entre sus llamadas de GET y PUT. Recupere la versión actual e inténtelo de nuevo. |

## Liberar referencia de objeto {#release-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de versión. Solo es necesario para las llamadas de actualización. | Condicional |
| `name` | Cadena | Nombre de la versión. Máximo 50 caracteres. Patrón: `^[a-zA-Z0-9_ ,.:()-]*$`. Debe ser único. | Sí |
| `description` | Cadena | Descripción opcional. Máx. 255 caracteres. | No |
| `type` | Cadena | `"RELEASE"` para versiones estándar; `"CROSS_TEAM_FEATURE_GROUP"` para grupos de funciones entre equipos. | Sí |
| `status` | Cadena | Estado de la versión. Para IMS: `"DRAFT"` al crear; `"DRAFT"`, `"SAVED"`, `"PUBLISHED"` al actualizar. Para CTFG: `"SAVED"` al crear; `"SAVED"`, `"PUBLISHED"` al actualizar. | Sí |
| `clients` | Matriz | Aplicaciones asociadas a esta versión. Cada entrada requiere `id` (numérico) y `imsClientId` (cadena). | No |
| `audience` | Matriz | Lista de reglas de audiencia. Ver [objeto de condición](feature-flags-management-api.md#condition-object). | No |
| `variations` | Matriz | Lista de variaciones. Solo se admite una variación durante el envío. | Requerido para el envío |
| `params` | Objeto | Parámetros de versión. Consulte [Campos de parámetros admitidos](#supported-params). | Requerido para el envío |
| `org` | Objeto | Objeto de organización. Debe incluir `id`. | No |

### Campos de parámetros admitidos {#supported-params}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `label` | Cadena | Nombre para mostrar. Máximo 50 caracteres. | Sí |
| `tags` | Matriz\&lt;Cadena\> | Etiquetas opcionales. Máximo 50 caracteres cada uno. | No |
| `canContextOverridePUP` | Booleano | Si es `true`, las reglas de contexto anulan las reglas de perfil. Predeterminado: `false`. | Sí |
| `isBetaRelease` | Booleano | Si `true`, marca esto como una versión beta. Predeterminado: `false`. | No |

### Objeto de variación {#variation-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de variación. Solo es necesario para las llamadas de actualización. | Condicional |
| `variantName` | Cadena | Nombre de variante. Máximo 50 caracteres. | Sí |
| `variantPercentage` | Duplicada | Porcentaje de audiencia que recibe esta variante. Intervalo: [0, 100]. | Sí |
| `features` | Matriz | Funciones incluidas en esta variación. Cada entrada debe incluir `id`, `name`, `clientId` y `state`. | No |

## Consulte también {#see-also}

* [Información general sobre las API de administración de funciones](feature-management-apis-overview.md)
* [API de administración de indicadores de funcionalidad](feature-flags-management-api.md)
* [API de administración de grupos de funciones](feature-group-management-api.md)
* [Crear un grupo de funciones entre equipos](../guides/feature-flags/create-cross-team-feature-group.md)
