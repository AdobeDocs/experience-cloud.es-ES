---
title: Administración de mensajes transaccionales
description: Obtenga información sobre cómo administrar mensajes transaccionales con API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
hidefromtoc: true
hide: true
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 00d39438-a232-49f1-ae5e-1e98c73397e3
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Administración de mensajes transaccionales {#managing-transactional-messages}

Una vez creado y publicado un evento transaccional, debe integrar la activación de este evento en el sitio web.

Por ejemplo, desea que se active un evento &quot;Abandono del carro de compras&quot; cada vez que uno de los clientes abandone el sitio web antes de comprar los productos que tiene en el carro de compras. Para ello, como desarrollador web, debe utilizar la API de mensajes transaccionales de REST.

1. Envíe una solicitud según el método POST, que almacena en déclencheur la variable [envío del evento transaccional](#sending-a-transactional-event).
1. La respuesta a la solicitud del POST contiene una clave principal, que le permite enviar una o varias solicitudes a través de una solicitud de GET. A continuación, puede obtener la [estado del evento](#transactional-event-status).

## Envío de un evento transaccional {#sending-a-transactional-event}

El evento transaccional se envía a través de una solicitud de POST con la siguiente estructura de URL:

```
POST https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>
```

* **&lt;organization>**: su ID de ORGANIZACIÓN personal. Consulte [esta sección](must-read.md).

* **&lt;transactionalapi>**: los puntos finales de la API de mensajes transaccionales.

  El nombre del punto de conexión de la API de mensajes transaccionales depende de la configuración de la instancia. Corresponde al valor &quot;mc&quot; seguido de su ID personal de organización. Veamos el ejemplo de la empresa de Geometrixx, con &quot;geometrixx&quot; como ID de organización. En ese caso, la solicitud del POST sería la siguiente:

  `POST https://mc.adobe.io/geometrixx/campaign/mcgeometrixx/<eventID>`

  Tenga en cuenta que el extremo de la API de mensajes transaccionales también está visible durante la vista previa de la API.

* **&lt;eventid>**: el tipo de evento que desea enviar. Este ID se genera al crear la configuración de evento

### encabezado de solicitud de POST

La solicitud debe contener un encabezado &quot;Content-Type: application/json&quot;.

Debe añadir un conjunto de caracteres, por ejemplo **utf-8**. Tenga en cuenta que este valor depende de la aplicación REST que utilice.

```
-X POST \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79' \
```

### cuerpo de solicitud del POST

Los datos de evento están contenidos dentro del cuerpo del POST JSON. La estructura del evento depende de su definición. El botón Vista previa de API en la pantalla de definición del recurso proporciona un ejemplo de solicitud.

Se pueden añadir los siguientes parámetros opcionales al contenido del evento para administrar el envío de mensajes transaccionales vinculados al evento:

* **vencimiento** (opcional): después de esta fecha, se cancela el envío del evento transaccional.
* **programado** (opcional): a partir de esta fecha, se procesa el evento transaccional y se envía el mensaje transaccional.

>[!NOTE]
>
>Los valores de los parámetros &quot;caducidad&quot; y &quot;programada&quot; siguen el formato ISO 8601. ISO 8601 especifica el uso de la letra mayúscula &quot;T&quot; para separar la fecha y la hora. Sin embargo, se puede eliminar de la entrada o salida para mejorar la legibilidad.

### Respuesta a la solicitud del POST

La respuesta del POST devuelve el estado del evento transaccional en el momento en que se creó. Para recuperar su estado actual (datos de evento, estado de evento...), utilice la clave principal devuelta por la respuesta del POST en una solicitud de GET:

`GET https://mc.adobe.io/<ORGANIZATION>/campaign/<transactionalAPI>/<eventID>/`

<br/>

***Solicitud de ejemplo***

Solicitud del POST para enviar el evento.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/mcAdobe/EVTcartAbandonment \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-H 'Content-Type: application/json;charset=utf-8' \
-H 'Content-Length:79'

{
  "email":"test@example.com",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "ctx":
  {
    "cartAmount": "$ 125",
    "lastProduct": "Leather motorbike jacket",
    "firstName": "Jack"
  }
}
```

Respuesta a la solicitud del POST.

```
{
  "PKey":"<PKEY>",
  "ctx":
  {
    "cartAmount": "",
    "lastProduct": "",
    "firstName": ""
  }
  "email":"",
  "scheduled":"2017-12-01 08:00:00.768Z",
  "expiration":"2017-12-31 08:00:00.768Z",
  "href": "mcAdobe/EVTcartAbandonment/<PKEY>",
  "serverUrl":" https://myserver.com ",
  "status":"pending",
  "type":""
}
```

### Estado del evento transaccional {#transactional-event-status}

En la respuesta, el campo &quot;estado&quot; permite saber si el evento se ha procesado o no:

* **pendiente**: el evento está pendiente: el evento adquiere este estado cuando acaba de activarse.
* **procesamiento**: el evento está pendiente de envío: se está transformando en un mensaje y el mensaje se está enviando.
* **pausado**: el proceso de eventos se está pausando. Ya no se procesa, sino que se mantiene en cola en la base de datos de Adobe Campaign.
* **Procesado**: el evento se procesó y el mensaje se envió correctamente.
* **ignorado**: el envío ignoró el evento, normalmente cuando una dirección está en cuarentena.
* **deliveryFailed**: error de envío mientras se procesaba el evento.
* **routingFailed**: la fase de enrutamiento ha fallado; esto puede ocurrir, por ejemplo, cuando no se encuentra el tipo de evento especificado.
* **toOld**: el evento caducó antes de que se pudiera procesar. Esto puede ocurrir por varios motivos, por ejemplo, cuando un envío falla varias veces (esto hace que el evento ya no esté actualizado) o cuando el servidor ya no puede procesar eventos después de sobrecargarse.
* **targetingFailed**: el Campaign Standard no ha podido enriquecer un vínculo que se está utilizando para la segmentación de mensajes.
