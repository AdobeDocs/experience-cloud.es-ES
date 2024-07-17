---
title: Recuperación de suscripciones
description: Obtenga información sobre cómo recuperar suscripciones con API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 6d935074-3196-45c5-97cd-ccb7c80bbba8
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Recuperación de suscripciones con API {#retrieving-subscriptions-api}

## Recuperación de los perfiles suscritos a un servicio

Este es un procedimiento de dos pasos.

1. Recupere la URL de suscripciones del servicio deseado.
1. Realizar una solicitud de GET en la URL de suscripciones. Devuelve la lista de suscripciones del servicio, con cada perfil asociado.

>[!CAUTION]
>
>La API de REST devuelve la propiedad &quot;href&quot;, que contiene la dirección URL que se va a utilizar. <b>Use siempre la dirección URL contenida en la respuesta para realizar la solicitud de API posterior</b>.

<br/>

***Solicitud de muestra***

Realice una solicitud de GET para recuperar el servicio.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve la URL de suscripciones del servicio.

```
  {
    ...
    "messageType": "email",
    "name": "SVC1",
    "subscriptions": {
                "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions/"
    },
    ...
  },
```

Realizar una solicitud de GET en la URL de suscripciones.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Se muestra la lista de suscripciones para el servicio, con cada perfil asociado.

```
  {
    ...
    "service": ...,
    "serviceName": "SVC3",
    "subscriber": {
        "PKey": "<PKEY>",
        "email": "",
        "firstName": "John",
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>",
        "lastName": "Doe",
    },
  }
```

## Recuperación de los servicios a los que se ha suscrito un perfil

Este es un procedimiento de dos pasos.

1. Recupere la URL de suscripciones de un perfil determinado.
1. Realice una solicitud de GET en la dirección URL. Devuelve la lista de suscripciones del perfil, con cada servicio asociado.

<br/>

***Solicitud de muestra***

Realice una solicitud de GET para recuperar el perfil.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve la URL de suscripciones del perfil.

```
  {
    ...
    "postalAddress":...,
    "preferredLanguage": "none",
    "subscriptions": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions/"
    },
    ...
  }
```

Realizar una solicitud de GET en la URL de suscripciones.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve la lista de servicios a los que se suscribió el perfil.

```
  {
    ...
    "PKey": "<PKEY>",
    "created": "2017-03-03 10:54:00.363Z",
    "service": {
      "PKey": "<PKEY>",
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
      "label": "Sport Newsletter",
      "name": "SVC1",
      "title": "Sport Newsletter (SVC1)"
    },
    ...
  }
```
