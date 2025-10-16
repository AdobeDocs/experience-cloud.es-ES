---
title: Creación de perfiles con API
description: Obtenga más información sobre cómo crear perfiles con API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: 69e8d034-6bdd-4b82-bcd7-1ef4be0a59b3
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Creación de perfiles con API {#creating-profiles-api}

La creación de perfiles se realiza con una solicitud **POST** en el recurso de perfil.

>[!CAUTION]
>
>Si desea asociar una <b>orgUnit</b> al perfil creado, debe ampliar el recurso de perfil con este campo y, después de la publicación de la extensión, realizar una petición POST en el extremo <b>ProfileAndServicesExt</b>.
>
>Para obtener más información sobre la extensión de recursos del perfil, consulte la <a href="https://helpx.adobe.com/es/campaign/standard/administration/using/organizational-units.html#partitioning-profiles">documentación de Campaign</a>.

<br/>

***Solicitud de muestra***

Ejemplo de solicitud POST para crear un perfil con el correo electrónico &quot;john.doe@mail.com&quot;.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{"email":"john.doe@mail.com"}'
```

Devuelve el perfil recién creado, con la dirección de correo electrónico &quot;john.doe@mail.com&quot;.

```
{
    "PKey": "<PKEY>",
    "firstName": "John",
    "lastName":"Doe",
    "birthDate": "1980-10-24",
    "email": "john.doe@mail.com",
    ...
}
```
