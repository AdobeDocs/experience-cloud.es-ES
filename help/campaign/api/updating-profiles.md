---
title: Actualización de perfiles
description: Obtenga más información sobre cómo actualizar perfiles con API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: fa3796ee-a00c-4d70-bf3d-e8d2099f1116
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '105'
ht-degree: 1%

---

# Actualización de perfiles con API{#updating-profiles-api}

La actualización de perfiles se realiza con una solicitud de **PATCH**.

`https://mc.adobe.io/<ORGANIZATION>/campaign/<apiName>/<resourceName>/<PKEY>`

1. El primer paso es **recuperar el perfil**.

1. En una segunda solicitud, realice una **solicitud de PATCH** en el perfil con la información completada en la carga útil.

1. Para comprobar si la solicitud del PATCH ha actualizado el perfil, podemos realizar una solicitud de GET final.

<br/>

***Solicitud de muestra***

Solicitud de GET de muestra para recuperar un perfil.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY>\
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Respuesta a la solicitud.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "Amy",
            "lastName":"Dakota",
            "birthDate": "1980-10-24",
            ...
        }
    ]
}
```

Solicitud del PATCH para actualizar el atributo &quot;phone&quot;.

```
-X PATCH https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/<PKEY> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-d '{"phone":"3301020304"}'
```

Devuelve la PKEY y la URL para recuperar el perfil actualizado.

```
{
    "PKey": "<PKEY>",
    "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/@2v1dr3ZKJveMDhAdh0MPnh9hNQQ93qb7AW6BNVVKknjwXvTZRBAgUqz1SNcB4ZndgjqOofx3BwBZYBftlmObISoM3rs"
}
```
