---
title: Recuento
description: Obtenga información sobre cómo realizar operaciones de recuento.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: d6354249-3b0d-4532-951f-b0fae953f7e1
TQID: https://experienceleague.adobe.com/HgtrtWqn6tdgTQR9lORGusyQswJX2zOWUvPOWXksS8c
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 95
ht-degree: 2%

---

# Recuento

La API de REST de Adobe Campaign puede contar el número de registros de una solicitud. Para ello, utilice la dirección URL que se devuelve en el nodo **count**.

<br/>

***Solicitud de muestra***

Para contar todos los servicios que tienen un valor **messageType** igual a &quot;sms&quot;, realice una petición GET con el filtro **byChannel**.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel?channel=sms \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve los servicios correspondientes al filtro.

```
{
    "content": [
        {
            ...
            "messageType": "sms",
            "mode": "newsletter",
            "name": "SVC6",
            ...
        },
        ...
    ],
    "count": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy"
    },
    "serverSidePagination": true
}
```

Realice una petición GET en la dirección URL del nodo **count** para recuperar el número de resultados.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/byChannel/_count?channel=sms&_lineStart=@iKTZ2q3IiSEDqZ5Nw1vdoGnQCqF-8DAUJRaVwR9obqqTxhMy \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve el número de registros.

```
{
    "count": 26
}
```
