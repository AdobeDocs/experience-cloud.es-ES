---
title: Obtener los criterios de audiencia deseados
description: Obtenga información sobre cómo generar la estructura JSON de criterios de audiencia correcta para utilizarla en las API de administración de despliegues de experiencia mediante la consola y la API de funciones de GET.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 1%

---


# Obtener los criterios de audiencia deseados {#get-audience-criteria}

El campo de criterios de audiencia en las API de administración utiliza un formato JSON estructurado que puede ser complejo de escribir a mano. El método recomendado es crear la audiencia deseada mediante la consola y luego recuperar su representación JSON mediante la API.

## Pasos {#steps}

Para obtener el JSON para un criterio de audiencia deseado, siga estos pasos:

1. En la consola Despliegues de experiencias, cree un indicador de función temporal con los criterios de audiencia que desee utilizar en la llamada de API.
2. Después de guardar, anote el ID de indicador de funcionalidad de la dirección URL del explorador. El ID aparece en la dirección URL después del ID de cliente. Por ejemplo, en `.../feature-flags/1191/22080`, el id. de característica es `22080`.
3. Llame al extremo [Get Feature by ID](feature-flags-management-api.md#get-feature-by-id) con ese ID de característica.
4. En el archivo JSON de respuesta, busque el campo `audience`. Contiene la estructura exacta de criterios de audiencia que necesita.
5. Copie el valor `audience`, quitando el atributo `id` de cada objeto de regla. Utilícelo en su llamada de API de Crear o actualizar función.

## Ejemplo {#example}

Después de llamar a GET `/m/api/v1/mgmt/feature/22080`, la respuesta incluye:

```json
{
  "audience": [
    {
      "id": 10034665,
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

Para usar esto en una llamada de Crear característica, quite el campo `id` del objeto de audiencia:

```json
{
  "audience": [
    {
      "criteria": {
        "and": [
          {
            "operator": "EQ",
            "attr": "LOCALE",
            "val": "EN",
            "ruleId": 1,
            "category": "default"
          }
        ]
      }
    }
  ]
}
```

## Consulte también {#see-also}

* [API de administración de indicadores de funcionalidad](feature-flags-management-api.md)
* [Obtener el ID de cliente de una aplicación](get-client-id.md)
* [API de parche de administración](management-patch-api.md)
