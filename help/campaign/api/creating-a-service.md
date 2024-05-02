---
title: Creación de un servicio con API
description: Obtenga información sobre cómo crear un servicio con API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 91bbce9e-a618-4be2-840b-c7d021271f4e
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Creación de un servicio con API{#creating-a-service-api}

La creación de servicios se realiza con un **POST** solicitud en el recurso de servicio.

Si desea crear el servicio con atributos específicos, agréguelos a la carga útil. De lo contrario, el nuevo servicio se creará con los predeterminados.

<br/>

***Solicitud de ejemplo***

Solicitud del POST de ejemplo para crear un servicio con atributos específicos.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/ \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
-i
-d {
-d "label": "My newsletter",
-d "messageType": "email",
-d "name": "email_newsletter",
-d "start": "2019-10-06"
-d }
```

Devuelve el servicio recién creado con los atributos actualizados.

```
{
    "PKey": "<PKEY>",
    "builtIn": false,
    "created": "2019-09-26 12:00:37.005Z",
    "href": "https://mc.adobe.io/<ORGANIZATION>/profileAndServices/service/@NLscZuVHxdVu9rPftvrMWFfR1zRIxQGswSOmGLrK09JTF_iWhB0JCUHEndA_vvy__k9mzOYa5NVkcWDcrK8qGh0wygahX9kRcD44kiWWSEceShn3",
    "label": "My newsletter",
    ...
}
```
