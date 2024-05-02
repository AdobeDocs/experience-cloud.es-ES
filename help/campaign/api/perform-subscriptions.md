---
title: Realización de suscripciones
description: Obtenga información sobre cómo realizar suscripciones con API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 64f321a3-436a-4b7c-99d8-0c006203012e
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Realización de suscripciones con API{#performing-subscriptions}

## Método 1: Suscripción de un perfil a un servicio

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

Realice una solicitud de POST en la URL de suscripciones con la clave principal de servicio deseada dentro de la carga útil.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>/subscriptions \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"service":{"PKey":"<PKEY>"}}'
```

Devuelve el perfil actualizado con el nodo de servicio completado.

```
{
  ...
  "service": {
    "PKey": "<PKEY>",
    "title": "Sport Newsletter (SVC1)"
  },
  "serviceName": "",
  "subscriber": ...,
  ...
}
```

## Método 2: Añadir un perfil a los suscriptores de un servicio

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

Realice una solicitud de POST en la URL de suscripciones con la clave principal del perfil deseada dentro de la carga útil.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign//profileAndServices/service/<PKEY>/subscriptions/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"subscriber":{"PKey":"<PKEY>"}}'
```

Devuelve el servicio actualizado con el nodo de suscriptores completado.

```
{
  ...
  "service": ...,
  "serviceName": "",
  "subscriber": {
    "PKey": "<PKEY>",
    ...
  },
}
```
