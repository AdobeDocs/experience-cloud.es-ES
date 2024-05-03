---
title: Lectura obligatoria
description: Debe leerse antes de usar las API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Lectura obligatoria {#must-read}

## Requisitos técnicos

* Las API de Adobe Campaign solo deben utilizarse de servidor a servidor.
* Consulte siempre con su contacto técnico de Adobe si el caso de uso que desea implementar está alineado con la escala permitida por las API de Adobe Campaign.
* La configuración de un acceso de AdobeIO requiere permisos específicos; póngase en contacto con el soporte técnico de Adobe para cualquier problema.

## Derechos y acceso

* De forma predeterminada, las API de Adobe Campaign utilizan el contexto de administrador y, por lo tanto, las unidades y funciones de la organización no se aplican.
* Las API de Adobe Campaign se excluyen del contexto de funciones.
* Si desea configurar las API con una unidad organizativa o funciones, consulte primero con su contacto técnico de Adobe.

## Representación de recursos

Todos los recursos de la API están disponibles en **JSON** con una extensión URL o dentro de un encabezado Aceptar HTTP:

`GET /profileAndServices/<resourceName>.json`

>[!NOTE]
>
>Sin extensión en la dirección URL, la variable **el formato json es el predeterminado** para el tipo de contenido.

<br/>

***solicitar muestra***

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile.json \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

## Clave principal y direcciones URL

* No intente crear una dirección URL usted mismo. La API devuelve todas las direcciones URL. Sin embargo, es posible crear una dirección URL basada en el nombre del recurso de nivel superior.

* Los valores de clave principal automática (PKey) que ilustran los ejemplos no están pensados para funcionar en otra implementación específica. Las produce la API de Adobe Campaign.

* Los valores de clave principal automática generados por Adobe Campaign nunca deben almacenarse en una base de datos o sitio web externo. Debe generar campos clave específicos en la definición de la base de datos y utilizarlos durante los desarrollos.

## Claves personalizadas {#custom-keys}

Si el recurso de perfil se ha ampliado con un campo de clave personalizada, puede utilizar este campo como clave en lugar de la clave principal automática generada por Adobe Campaign:

`GET /.../profileAndServicesExt/profile/<customKey>`

Las claves personalizadas no se pueden modificar mediante una operación de PATCH si el valor de la clave es diferente de la clave de origen o si utiliza su propia clave comercial como URI en lugar de la proporcionada por Adobe.

Utilizar una clave personalizada para **recursos de perfil de nivel superior** solo. La API devuelve las direcciones URL, que nunca debe crear usted mismo.

<br/>

***Solicitud de ejemplo***

GET Para recuperar las suscripciones de un perfil mediante una clave personalizada, realice una operación en la clave personalizada.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/<customKey> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Realizar una solicitud de GET en la URL de suscripciones devuelta.

```
-X GET <SUBSCRIPTION_URL> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve la lista de suscripciones del perfil.

```
"service": {
"PKey": "<PKEY>",
"href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/service/<PKEY>",
"label": "Sport Newsletter",
"name": "SVC1",
"title": "Sport Newsletter (SVC1)"
}
```
