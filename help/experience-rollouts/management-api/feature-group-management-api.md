---
title: API de administración de grupos de funciones
description: Referencia de la API para la API de administración de grupos de funciones de los despliegues de experiencias, incluidos los puntos finales para obtener, crear, actualizar, eliminar y controlar planes de despliegue para grupos de funciones.
source-git-commit: 8a92b7a3e8c52da8bb2474f52c831e159420b878
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 14%

---


# API de administración de grupos de funciones {#feature-group-management-api}

La API de administración de grupos de funciones le permite crear, leer, actualizar y eliminar grupos de funciones en los lanzamientos de experiencias mediante programación, incluidos planes de despliegue automatizados y de pruebas A/B.

**Ruta básica:** `/m/api/v1/mgmt/group`

Todas las solicitudes requieren los encabezados descritos en los [requisitos comunes](feature-management-apis-overview.md#common-requirements).

## Obtener todos los grupos de funciones {#get-all-groups}

Recupera todos los grupos de funciones de su organización.

| | |
|---|---|
| **Extremo** | `GET /m/api/v1/mgmt/group` |
| **Método** | GET |

### Parámetros de consulta {#get-all-query-params}

| Parámetro | Tipo | Descripción | Requerido |
|---|---|---|---|
| `myOrg` | Booleano | Se establece en `true` para incluir la información de la organización. | Sí |
| `includeClientInfo` | Booleano | Establezca el valor en `true` para incluir información de la aplicación para cada grupo. | Sí |

### Respuesta {#get-all-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es una matriz de objetos de grupos de funciones. |

## Obtener grupo de funciones por ID {#get-group-by-id}

Recupera un solo grupo de funciones por su ID numérico.

| | |
|---|---|
| **Extremo** | `GET /m/api/v1/mgmt/group/{groupId}` |
| **Método** | GET |
| **Parámetro de consulta** | `includeAnalyzeInfo=true` (opcional: agrega datos de análisis a la respuesta) |

### Respuesta {#get-by-id-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es un objeto de grupo de funciones. |
| `400` | ID de grupo de funciones no válido. |

## Crear grupo de funciones {#create-group}

Crea un nuevo grupo de funciones con un tipo de despliegue manual, automatizado o de prueba A/B.

| | |
|---|---|
| **Extremo** | `POST /m/api/v1/mgmt/group` |
| **Método** | PUBLICAR |

### Cuerpo de solicitud {#create-request-body}

El cuerpo de la solicitud usa el [objeto de grupo de características](#feature-group-object). `rolloutType` dentro de `params` es obligatorio y determina la estructura de la carga útil.

**Muestra — despliegue manual:**

```json
{
  "params": {
    "rolloutType": "manual",
    "label": "my-feature-group",
    "tags": [],
    "canContextOverridePUP": false
  },
  "status": "SAVED",
  "type": "group",
  "name": "my.feature.group",
  "description": "A manual feature group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "audience": [{ "criteria": { "and": [{ "operator": "EQ", "attr": "COUNTRY", "val": "US", "ruleId": 1, "category": "default" }] } }],
  "clients": [],
  "org": { "id": 95 }
}
```

**Muestra — despliegue automatizado:**

```json
{
  "params": { "rolloutType": "automated", "label": "my-automated-group", "tags": [] },
  "status": "SAVED",
  "type": "group",
  "name": "my.automated.group",
  "variations": [{ "variantPercentage": 100, "variantName": "Variant 1", "features": [] }],
  "phaseRollOutPlan": {
    "phaseRollOutBlocks": [
      { "isPhaseBlock": true, "phaseRule": { "audience": [] }, "waitRule": null, "blockId": 1, "blockName": "", "isBlockActivated": false },
      { "isPhaseBlock": false, "phaseRule": null, "waitRule": { "waitDuration": { "val": "2", "unit": "HOURS" } }, "blockId": 2, "blockName": "", "isBlockActivated": false },
      { "isPhaseBlock": true, "phaseRule": { "audience": [] }, "waitRule": null, "blockId": 3, "blockName": "", "isBlockActivated": false }
    ],
    "rollOutPlanState": "DRAFT"
  },
  "clients": [],
  "org": { "id": 95 }
}
```

### Respuesta {#create-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es el objeto del grupo de funciones creado. |
| `400` | Carga no válida: vea [mensajes de error](#error-messages) para obtener detalles. |
| `403` | Permisos insuficientes. |

## Actualizar grupo de funciones {#update-group}

Actualiza un grupo de funciones existente. Pase la misma estructura que el cuerpo de la solicitud de creación, incluido el campo `id`.

| | |
|---|---|
| **Extremo** | `PUT /m/api/v1/mgmt/group` |
| **Método** | PUT |

### Respuesta {#update-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de respuesta es el objeto del grupo de funciones actualizado. |
| `400` | Carga no válida. |
| `403` | Permisos insuficientes. |

## Pausar, reanudar o cancelar un plan de despliegue {#pause-resume-abort}

Controla la ejecución de un plan de despliegue de pruebas A/B o automatizadas en curso.

| Acción | Punto de conexión |
|---|---|
| **Reanudar** | `POST /m/api/v1/mgmt/phaserollout/resume` |
| **Pause** | `POST /m/api/v1/mgmt/phaserollout/pause` |
| **Anular** | `POST /m/api/v1/mgmt/phaserollout/abort` |

### Cuerpo de solicitud {#control-request-body}

```json
{
  "entityId": 10282,
  "fgEntityType": "GROUP"
}
```

### Respuesta {#control-response}

Devuelve `true` si se realizó correctamente.

## Eliminar grupo de funciones {#delete-group}

Elimina un grupo de funciones por su ID numérica.

| | |
|---|---|
| **Extremo** | `DELETE /m/api/v1/mgmt/group/{groupId}` |
| **Método** | DELETE |

### Respuesta {#delete-response}

| Estado | Descripción |
|---|---|
| `204` | Correcto. No hay cuerpo de respuesta. |
| `403` | Permisos insuficientes. |

## Referencia de objeto del grupo de funciones {#feature-group-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de grupo de funciones. Solo es necesario para las llamadas de actualización. | Condicional |
| `name` | Cadena | Clave de grupo de funciones. Máximo 50 caracteres. Patrón: `^[a-zA-Z0-9_.-]*$` | Sí (crear) |
| `clients` | Matriz | Aplicaciones asociadas al grupo. Cada entrada debe incluir `id` y `imsClientId`. | Sí |
| `status` | Cadena | `"SAVED"` o `"PUBLISHED"` | Sí |
| `type` | Cadena | Siempre `"group"` para grupos de características. | Sí |
| `org` | Objeto | Detalles de la organización. Debe incluir `id`. | Sí |
| `params` | Objeto | Parámetros de grupo. `rolloutType` es obligatorio (`"manual"`, `"automated"` o `"ab-testing"`). También admite `label` y `tags`. | Sí |
| `audience` | Matriz | Reglas de audiencia para tipos de despliegue manual. | No |
| `variations` | Matriz | Lista de variantes. Consulte [Objeto FeatureGroupVariation](#featuregroupvariation-object). | No |
| `phaseRollOutPlan` | Objeto | Plan de despliegue gradual. Necesario para tipos de prueba automatizada y A/B. Ver [objeto PhaseRollOutPlan](#phaserolloutplan-object). | Condicional |
| `description` | Cadena | Descripción para mostrar opcional. Máx. 225 caracteres. | No |

### Objeto FeatureGroupVariation {#featuregroupvariation-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `id` | Número entero | ID de variación. Solo es necesario para las llamadas de actualización. | Condicional |
| `variantName` | Cadena | Nombre de variante. Codificado para `"Variant 1"`. | Sí |
| `variantPercentage` | Decimal | Porcentaje de audiencia que recibe esta variante. Debe ser mayor que 0 y no mayor que 100. | Sí |

### Objeto PhaseRollOutPlan {#phaserolloutplan-object}

| Campo | Tipo | Descripción | Requerido |
|---|---|---|---|
| `phaseRollOutBlocks` | Matriz | Lista ordenada de bloques de fase y bloques de espera. El último bloque debe ser un bloque de fase. | Sí |
| `rollOutPlanState` | Cadena | `"DRAFT"`, `"RUNNING"`, `"PAUSED"` o `"ABORTED"` | Sí |

Cada bloque de `phaseRollOutBlocks` es un **bloque de fase** (`isPhaseBlock: true`) que contiene `phaseRule` con criterios de audiencia o un **bloque de espera** (`isPhaseBlock: false`) que contiene `waitRule` con `waitDuration` (relativo) o `executionDate` (marca de tiempo fija).

## Mensajes de error {#error-messages}

| Condición | Estado | Mensaje de error |
|---|---|---|
| Nombre no válido o vacío | 400 | `Error: Invalid value for release name.` |
| Criterios de audiencia vacíos | 400 | `Error: Release is not valid` |
| Varias variaciones para el tipo automatizado | 400 | `Error: Feature variation is not valid. Variation name should be unique across variations` |
| Grupo publicado sin clientes | 400 | `Error: At least one client must be associated with enabled feature group.` |
| El último bloque del plan no es un bloque de fase | 400 | `Error: The last block in the Phase Rollout plan should be phase block` |
| Tiempo de espera de bloque desordenado | 400 | `Error: Wait block timings are not in order in the phase rollout plan` |
| Tipos de bloques de espera incoherentes | 400 | `Error: Wait block should be of same type.` |
| Edición de un bloque de fase activado | 400 | `Error: Activated phase block should not be changed` |
| Tipo de despliegue vacío | 400 | `Error: Rollout type cannot be empty while feature group creation` |
| Plan de fase aprobado con tipo manual | 400 | `Error: PhaseRollOutPlan can't be added with manual rollout type while feature group creation` |
| Programación superada con estado PUBLICADO | 400 | `Error: Schedule can't be added in published state while release/group creation` |

## Consulte también {#see-also}

* [Información general sobre las API de administración de funciones](feature-management-apis-overview.md)
* [API de administración de indicadores de funcionalidad](feature-flags-management-api.md)
* [API de parche de administración](management-patch-api.md)
* [Creación de un despliegue automatizado](../guides/automated-rollouts/create-automated-rollout.md)
