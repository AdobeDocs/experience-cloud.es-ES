---
title: Solución de problemas API
description: Obtenga más información acerca de problemas comunes relacionados con las API de Campaign Standard
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Solución de problemas API {#troubleshooting}

* **Al ir a la consola de Adobe.io recibe el siguiente error: &quot;La consola de Adobe I/O solo está disponible para miembros seleccionados de cuentas de empresa. Si cree que debería tener acceso, póngase en contacto con el administrador del sistema&quot;.**

Solo puede crear claves API para las organizaciones de las que es administrador. Si se muestra este mensaje, desea crear claves de API y desea preguntar a uno de los administradores de la organización.

* **Al realizar una solicitud a Adobe.io, se obtiene {&quot;error_code&quot;:&quot;403023&quot;,&quot;message&quot;:&quot;El perfil no es válido&quot;}**

Esto significa que hay un problema con el aprovisionamiento de IMS de su producto de Campaign específico: el equipo de IMS debe solucionarlo.

Para obtener más información, puede llamar a la API de IMS con su token para ver el aspecto de su perfil IMS: Debe tener un prodCtx donde el organization_id sea el mismo que el que puso en su URL para Adobe.io para poder enrutar su solicitud.
Si falta, es necesario corregir el aprovisionamiento de IMS.

```
-X GET https://mc.adobe.io/{ORGANIZATION}/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve el siguiente error.

```
{"error_code":"403023","message":"Profile is not valid"}
```

Compruebe su perfil IMS con esta solicitud.

```
-X GET https://ims-na1.adobelogin.com/ims/profile/v1 \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

En la respuesta, el valor ORGANIZATION_ID debe ser el mismo en la primera solicitud de GET.

```
{
  "countryCode": "FR",
  "mrktPermEmail": null,
  "projectedProductContext": [
    {
    "prodCtx": {
      "statusCode": "ACTIVE",
      "ident": "ZQ9FRQK7BF09YXAESFY9DDQP1G",
      "modDts": 1448307260000,
      "organization_id": "actest",
      "owningEntity": "6096892F54B5819E0A4C98A2@AdobeOrg",
      "serviceCode": "dma_tartan",
      "label": "Adobe Marketing Cloud",
      "serviceLevel": "standard",
      "createDts": 1421181343000,
      "deal_id": " "
      }
    }
  ]
}
```

* **Al hacer una solicitud a Adobe.io, obtienes {&quot;code&quot;:500, &quot;message&quot;:&quot;Uy. Se ha producido un error. Compruebe su URI e inténtelo de nuevo.&quot;}**

Adobe.io declara su URI no válido: lo más probable es que el URI que está solicitando no sea válido. En Adobe.io, al seleccionar el servicio de Campaign, se obtiene un selector con una lista de posibles organization_ids. Debe comprobar que el que elige es el que introduce en la dirección URL.

* **Al realizar una solicitud a Adobe.io, se obtiene {&quot;error_code&quot;:&quot;401013&quot;,&quot;message&quot;:&quot;El token de OAuth no es válido&quot;}**

Su token no es válido (se ha utilizado una llamada IMS incorrecta para generar un token) o su token ha caducado.

* **No veo mi perfil después de la creación**

Según la configuración de la instancia, el perfil creado debe asociarse a un **orgUnit**. Para comprender cómo añadir este campo en la creación, consulte [esta sección](creating-profiles-api.md).

<!-- * (error duplicate key : quand tu crées un profile qui existe déjà , il faut faire un patch pour updater le profile plutôt qu'un POST)

With Curl
List all profiles

Create a profile

Update the mobilePhone attribute of a profile

API Calls on Service

GET the list of services

-->

<!--

How to find and use a filter?
Error codes:

* PAtch sur Age = message d'erreur :
500
Cannot update the 'age' property that is read-only
'age' property is not valid for the 'profile' resource.
-->

<!--
How to filter a list of subscribed profiles with available profile filters ? by date (by les filtres dispo sur la ressource) ?

Pattern classique :

recupérer la liste des subscriptions filtrées d'un profile
1) get sur profile
2) recup PKey
3) get sur PKey
4) get sur href des subscriptions

Comment savoir quel filtre appliquer ?

1) get sur metadata de profile
2) retourne description de la collection subscription
3) get sur la valeur du champ resTarget
4) get sur le href dans filters
5) retourne les filtres applicables sur l'url des data.

-->
