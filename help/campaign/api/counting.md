---
title: Recuento
description: Obtenga información sobre cómo realizar operaciones de recuento.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: d6354249-3b0d-4532-951f-b0fae953f7e1
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 2%

---

# Recuento

La API de REST de Adobe Campaign puede contar el número de registros de una solicitud. Para ello, utilice la dirección URL que se devuelve en el nodo **count**.

<br/>

***Solicitud de muestra***

Para contar todos los servicios que tienen un valor **messageType** igual a &quot;sms&quot;, realice una solicitud de GET con el filtro **byChannel**.

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

Realice una solicitud de GET en la dirección URL del nodo **count** para recuperar el número de resultados.

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
