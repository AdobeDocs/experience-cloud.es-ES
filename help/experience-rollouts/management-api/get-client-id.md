---
title: Obtener el ID de cliente de una aplicación
description: Obtenga información sobre cómo encontrar el ID de cliente numérico para una aplicación en la consola Despliegues de experiencia, que es necesario al llamar a las API de administración.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---


# Obtener el ID de cliente de una aplicación {#get-client-id}

Los indicadores de características y las API de administración de grupos de características requieren un valor numérico `clientId` para identificar a qué aplicación pertenece la característica. Es diferente al ID de cliente IMS basado en cadenas que se utiliza para la autenticación API.

Siga estos pasos para buscar el ID de cliente numérico para una aplicación.

## Pasos {#steps}

Para buscar el ID de cliente numérico de una aplicación, siga estos pasos:

1. Inicie sesión en la consola Despliegues de experiencias.
2. Vaya a **Características y versiones**.
3. Seleccione la ficha **Indicadores de característica**.
4. Abra el menú desplegable **Aplicación** y seleccione la aplicación cuyo ID de cliente necesite.
5. Observe la dirección URL en la barra de direcciones del explorador. Después de `feature-flags/`, el número que se muestra es el ID de cliente numérico para esa aplicación.

Por ejemplo, si la dirección URL termina con `.../feature-flags/1191/...`, el identificador de cliente es `1191`.

## Uso del ID de cliente en llamadas API {#use-in-api}

Pase este valor como parámetro `clientId` en las solicitudes de API de administración. Por ejemplo, al crear un indicador de funcionalidad:

```json
{
  "name": "my-feature-flag",
  "clientId": 1191,
  "state": "disabled"
}
```

## Consulte también {#see-also}

* [API de administración de indicadores de funcionalidad](feature-flags-management-api.md)
* [API de administración de grupos de funciones](feature-group-management-api.md)
* [Obtener los criterios de audiencia deseados](get-audience-criteria.md)
