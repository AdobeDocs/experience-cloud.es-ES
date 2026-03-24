---
title: API de parche de administración
description: Utilice la API de PATCH de despliegues de experiencias para actualizar campos individuales de un indicador de funciones, un grupo de funciones o un grupo de funciones de varios equipos sin pasar el objeto completo.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 3%

---


# API de parche de administración {#management-patch-api}

La API de PATCH permite actualizar campos específicos de un indicador de funciones, grupo de funciones o grupo de funciones de varios equipos sin enviar el objeto completo en el cuerpo de la solicitud. Esto resulta útil para actualizaciones de destino, como cambiar una regla de audiencia, cambiar de estado o ajustar un porcentaje de variación.

## Indicador de funcionalidad PATCH {#feature-flag-patch}

Actualiza uno o varios campos de un indicador de funcionalidad.

| | |
|---|---|
| **Extremo** | `PATCH /m/api/v1/mgmt/feature/{featureFlagId}` |
| **Método** | PATCH |

### Encabezados de solicitud {#ff-request-headers}

Todas las solicitudes requieren los encabezados descritos en los [requisitos comunes](feature-management-apis-overview.md#common-requirements).

### Parámetro de ruta {#ff-path-param}

| Parámetro | Tipo | Descripción | Requerido |
|---|---|---|---|
| `featureFlagId` | Número entero | El ID numérico del indicador de funcionalidad que se va a actualizar. | Sí |

### Cuerpo de solicitud {#ff-request-body}

Pase solo los campos que desee actualizar. La respuesta siempre devuelve el objeto de indicador de función actualizado completo.

**Ejemplo — actualizar solo descripción:**

```json
{
  "description": "Updated description"
}
```

**Ejemplo — quitar audiencia existente:**

```json
{
  "audience": null
}
```

**Ejemplo — agregar una audiencia nueva cuando no existe:**

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "DEVELOPMENT", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Ejemplo — actualizar una regla de audiencia existente:**

```json
{
  "audience": [
    {
      "id": 10020035,
      "criteria": {
        "and": [
          { "operator": "EQ", "attr": "sandboxType", "val": "PRODUCTION", "ruleId": 1, "category": "contextual" }
        ]
      }
    }
  ]
}
```

**Ejemplo — cambiar estado y porcentaje de variación:**

```json
{
  "state": "disabled",
  "variations": [
    {
      "id": 10017188,
      "variantName": "Variation 1",
      "variantPercentage": 80.0
    }
  ]
}
```

>[!NOTE]
>
>Al actualizar una regla de audiencia existente, incluya `id` de la regla (disponible en la respuesta de la función de GET) para actualizarla. Al actualizar variaciones, incluya `id` de la variación para evitar la creación de un duplicado.

### Respuesta {#ff-response}

| Estado | Descripción |
|---|---|
| `200` | Correcto. El cuerpo de la respuesta es el objeto de indicador de función actualizado completo. |
| `400` | Carga no válida. |
| `403` | Permisos insuficientes. |
| `417` | Conflicto de actualización simultánea. Recupere la función actual y vuelva a intentarlo. |

## Grupo de funciones PATCH {#feature-group-patch}

Actualiza uno o varios campos de un grupo de funciones. La estructura de solicitud y respuesta es la misma que la del indicador de funcionalidad PATCH; solo difiere el punto de conexión.

| | |
|---|---|
| **Extremo** | `PATCH /m/api/v1/mgmt/group/{featureGroupId}` |
| **Método** | PATCH |

## Grupo de funciones entre equipos de PATCH {#ctfg-patch}

Actualiza uno o varios campos de un grupo de funciones entre equipos. Utiliza el punto final de la versión 2.

| | |
|---|---|
| **Extremo** | `PATCH /m/api/v2/mgmt/release/{CTFGId}` |
| **Método** | PATCH |

## Consulte también {#see-also}

* [API de administración de indicadores de funcionalidad](feature-flags-management-api.md)
* [API de administración de grupos de funciones](feature-group-management-api.md)
* [API de administración de versiones](release-management-apis.md)
* [Información general sobre las API de administración de funciones](feature-management-apis-overview.md)
