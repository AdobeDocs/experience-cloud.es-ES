---
title: Paginación
description: Obtenga información sobre cómo realizar operaciones de paginación.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 1%

---

# Paginación

De forma predeterminada, se cargan 25 recursos en una lista.

El **_lineCount** permite limitar el número de recursos enumerados en la respuesta.  A continuación, puede utilizar la variable **siguiente** para mostrar los siguientes resultados.

>[!NOTE]
>
>Utilice siempre el valor de URL devuelto en **siguiente** para realizar una solicitud de paginación.
>
>El **_lineStart** La solicitud de se calcula y siempre se debe utilizar dentro de la dirección URL devuelta en **siguiente** nodo.

<br/>

***Solicitud de ejemplo***

Solicitud de GET de ejemplo para mostrar 1 registro del recurso de perfil.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_lineCount=1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Respuesta a la solicitud, con el **siguiente** para realizar la paginación.

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

De forma predeterminada, la variable **siguiente** El nodo no está disponible al interactuar con tablas con una gran cantidad de datos. Para poder realizar la paginación, debe agregar la variable **_forcePagination=true** a su URL de llamada.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile?_forcePagination=true \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

>[!NOTE]
>
>El número de registros por encima de los cuales una tabla se considera grande se define en Campaign Standard **XtkBigTableThreshold** opción. El valor predeterminado es 100 000 registros.
