---
title: Paginación
description: Obtenga información sobre cómo realizar operaciones de paginación.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: d6ebce3c-1e84-4b3b-a68d-90df4680af64
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# Paginación

De forma predeterminada, se cargan 25 recursos en una lista.

El parámetro **_lineCount** le permite limitar el número de recursos enumerados en la respuesta.  A continuación, puede usar el nodo **next** para mostrar los siguientes resultados.

>[!NOTE]
>
>Utilice siempre el valor de URL devuelto en el nodo **next** para realizar una solicitud de paginación.
>
>La solicitud **_lineStart** se ha calculado y siempre debe usarse en la dirección URL devuelta en el nodo **next**.

<br/>

***Solicitud de muestra***

Solicitud de GET de ejemplo para mostrar 1 registro del recurso de perfil.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Respuesta a la solicitud, con el nodo **next** para realizar la paginación.

```
{
    "content": [
        {
            "PKey": "<PKEY>",
            "firstName": "John",
            "lastName":"Doe",
            "birthDate": "1980-10-24",
            ...
        }
    ],
    "next": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
        lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
    }
    ...
}
```

De manera predeterminada, el nodo **next** no está disponible cuando se interactúa con tablas con una gran cantidad de datos. Para poder realizar la paginación, debe agregar el parámetro **_forcePagination=true** a la dirección URL de la llamada.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>El número de registros por encima de los cuales una tabla se considera grande se define en la opción del Campaign Standard **XtkBigTableThreshold**. El valor predeterminado es 100 000 registros.
