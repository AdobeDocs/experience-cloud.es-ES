---
title: Recommendations y limitaciones
description: Recommendations y limitaciones al migrar a las API de REST de Campaign v8.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
mini-toc-levels: 1
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 45acebb1-9325-4e26-8fe9-cc73f745d801
source-git-commit: 6e4e214731b9772014d01dde89b3f80e4c4e93a6
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 1%

---

# Recommendations y limitaciones {#limitations}

## Permisos y seguridad {#permissions}

### Asignación de perfiles de producto

En Campaign Standard, se le otorgó un acceso elevado a la función de administrador a las API independientemente del perfil de producto asignado. La versión 8 de Campaign presenta un conjunto diferente de perfiles de producto, que requieren la asignación de perfiles de producto de Campaign Standard a Campaign v8.

Con la migración, se añaden dos perfiles de producto a las cuentas técnicas existentes o creadas previamente: Administrador y Centro de mensajes (para acceder a las API transaccionales). Revise la asignación de perfiles de producto y asigne el perfil de producto necesario si no desea que el perfil de producto de administrador se asigne con su cuenta técnica.

### ID de inquilino

Después de la migración, para cualquier integración futura, se recomienda usar su **ID de inquilino de Campaign v8** en las URL de REST, reemplazando su ID de inquilino de Campaign Standard anterior.

### Uso de claves

La administración de los valores de PKey difiere entre Campaign Standard y Campaign v8. Si almacenaba claves principales con Campaign Standard, asegúrese de que la implementación forme dinámicamente llamadas de API posteriores mediante claves principales o href obtenidas de llamadas de API anteriores.

## API disponibles {#deprecated}

Por ahora, las API de REST enumeradas a continuación están disponibles para su uso:

* **Perfiles**
* **Servicios y suscripciones**
* **Recursos personalizados**
* **Flujos de trabajo**

>[!AVAILABILITY]
>
>Por ahora, la API de REST **mensajes transaccionales** no está disponible.
>
>Las API de REST enumeradas a continuación están en desuso y no están disponibles para su uso:
>* Historial de marketing
>* Unidades organizativas
>* Administración de la privacidad

## Filtrado

* Para utilizar los filtros en las cargas útiles de API REST, debe editarlos en Campaign v8 y proporcionar un nombre para utilizarlo en las cargas útiles. Para ello, obtenga acceso a los parámetros adicionales del filtro desde la ficha **[!UICONTROL Parámetros]** y proporcione el nombre que desee en el campo **[!UICONTROL Nombre del filtro en la API de REST]**.

  ![](assets/api-filtering.png)


* El prefijo &quot;by&quot; necesario para utilizar filtros personalizados ya no es necesario. El nombre del filtro debe usarse tal cual en sus solicitudes.

  Por ejemplo:

  `GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/<resourceName>/<customFilterName>?<customFilterparam>=<customFilterValue>`

## Campos de base de datos descartados

Algunos campos de la base de datos se pierden durante la migración. Al utilizar un campo colocado, las API de REST devolverán valores en blanco. En el futuro, todos los campos perdidos quedarán obsoletos y se eliminarán.

## POST con recursos vinculados

Cuando se utiliza el siguiente formato de cuerpo de solicitud, con &quot;propietario del vehículo&quot; representando el vínculo a &quot;nms:destinatario&quot;:

```
{
    "vehicleNumber": "20009",
    "vehicleName": "Model E",
    "vehicleOwner":{
        "firstName":"tester 11",
        "lastName":"Smith 11"
    }
}
```

Se ignora la información del vínculo. En consecuencia, se genera un nuevo registro en &quot;cusVehicle&quot; que contiene solo los valores de &quot;número de vehículo&quot; y &quot;nombre de vehículo&quot;. Sin embargo, el vínculo sigue siendo nulo, lo que hace que &quot;excipientePropietario&quot; se establezca en nulo.

En Campaign v8, cuando se utiliza la misma estructura de cuerpo de solicitud y el &quot;vehículo&quot; está vinculado a un perfil, se produce un error. Este error se produce porque la propiedad &quot;firstName&quot; no se reconoce como válida para &quot;cusVehicle&quot;. Sin embargo, un cuerpo de solicitud que incluye solo los atributos sin el vínculo funciona sin ningún problema.

## operaciones del PATCH

* La versión 8 de Campaign no admite PATCH con un cuerpo de solicitud vacío: devuelve el estado 204 Sin contenido.
* Aunque Campaign Standard admite PATCH en elementos/atributos dentro de un esquema, tenga en cuenta que las operaciones de PATCH en la ubicación no son compatibles con Campaign v8. Si se intenta un PATCH en una ubicación, se producirá un error de servidor interno 500 con un mensaje de error que indica que la propiedad &quot;zipCode&quot; no es válida para el recurso &quot;perfil&quot;.

## Respuestas REST

La sección siguiente enumera diferencias menores entre las respuestas de Campaign Standard y REST v8.

* Para registros de GET únicos, la respuesta incluye el href en la respuesta.
* Cuando se consulta con el atributo, Campaign v8 proporciona Recuento y Paginación en la respuesta.
* Después de las operaciones del POST, los valores de los recursos vinculados se devuelven en la respuesta.

## Códigos de error y mensajes

La sección siguiente enumera las diferencias entre los códigos de error y los mensajes de Campaign Standard y Campaign v8.

| Escenario | Campaign Standard | Versión 8 de Campaign |
|  ---  |  ---  |  ---  |
| Usar una clave principal no válida en el cuerpo de la solicitud | 500 - Atributo &#39;O5iRp40EGA&#39; desconocido (consulte la definición del esquema &#39;Profiles (nms:recipient)&#39;). XTK-170036 No se ha podido analizar la expresión &#39;@id = @O5iRp40EGA&#39;. | 404: No se puede descifrar la clave principal. (PKey=@jksad) |
| Usar una clave principal no válida en el URI | 500 - Atributo &#39;O5iRp40EGA&#39; desconocido (consulte la definición del esquema &#39;Profiles (nms:recipient)&#39;). XTK-170036 No se ha podido analizar la expresión &#39;@id = @O5iRp40EGA&#39;. | 404: No se puede descifrar la clave principal. (PKey=@jksad) Extremo no compatible. (extremo=rest/profileAndServices/profile/@jksad) |
| Uso de dos claves sin procesar diferentes en el URI y en el cuerpo de la solicitud | 500 - RST-360011 Se ha producido un error. Póngase en contacto con el administrador. RST-360012 Operación incoherente en el recurso &quot;servicio&quot;: no se puede actualizar la clave &quot;SVC3&quot; a &quot;SVC4&quot;. | 500 - Se ha producido un error - póngase en contacto con su administrador. |
| Uso de PKey en el URI y de una PKey sin procesar diferente en el cuerpo de la solicitud | 500: ya existe un &quot;servicio&quot; con la misma clave &quot;SVC4&quot;. PGS-220000 Error de PostgreSQL: ERROR: el valor de clave duplicado viola la restricción única &quot;nmsservice_name&quot; DETALLE: La clave (sname)=(SVC4) ya existe. | 500 - Se ha producido un error - póngase en contacto con su administrador. |
| Uso de raw-id no existente en el URI | 404 - RST-360011 Se ha producido un error. Póngase en contacto con el administrador. No se puede encontrar el documento con la ruta &#39;Servicio&#39; de la clave &#39;adobe_nl:0&#39; (documento con el esquema &#39;service&#39; y el nombre &#39;adobe_nl&#39;) | 404: No se puede encontrar el documento con la ruta &quot;Servicio&quot; de la clave &quot;adobe_nl&quot; (documento con el esquema &quot;service&quot; y el nombre &quot;adobe_nl&quot;) |
| Uso de raw-id no existente en el cuerpo de la solicitud | 404 - RST-360011 Se ha producido un error. Póngase en contacto con el administrador. No se pudo encontrar documento con ruta &#39;Servicio&#39; de la clave &#39;adobe_nl&#39; (documento con esquema &#39;service&#39; y nombre &#39;adobe_nl&#39;) | 404: No se puede encontrar el documento con la ruta &quot;Servicio&quot; de la clave &quot;adobe_nl&quot; (documento con el esquema &quot;service&quot; y el nombre &quot;adobe_nl&quot;) |
| - | 500 - RST-360011 Se ha producido un error. Póngase en contacto con el administrador. | 500 - Se ha producido un error - póngase en contacto con su administrador. |
| Inserte un perfil o servicio con un valor de enumeración de sexo no válido (o cualquier cosa) | 500 - RST-360011 Se ha producido un error. Póngase en contacto con el administrador. El valor &quot;invalid&quot; no es válido para la enumeración &quot;nms:recipient:gender&quot; del campo &quot;@gender&quot; | 500: Se ha producido un error. Póngase en contacto con el administrador. |

## Perfil: zona horaria

Con el Campaign Standard, la zona horaria se muestra como parte de la respuesta JSON de **profileAndServices/profile** llamadas a la API de REST.

Con Campaign v8, la zona horaria solo se muestra al usuario como parte de las llamadas a la API REST **profileAndServicesExt/profile**. No forma parte de las llamadas a la API REST **profileAndServices/profile** porque se está agregando en un esquema extendido.

## Flujos de trabajo: activación de señal externa

La API de flujo de trabajo de Campaign Standard GET devuelve nombres de parámetros como las variables de instancia de flujo de trabajo y sus tipos de datos (booleano, cadena, etc.). Se utiliza para crear un cuerpo de solicitud JSON con el formato adecuado al activar la señal a través de una llamada de API de POST.

Campaign v8 no admite variables de instancia de flujo de trabajo de publicidad, pero espera que los desarrolladores sepan cuáles son. Como tal, después de la migración, la información de parámetros en el cuerpo de solicitud del POST deberá construirse sin la disponibilidad de la información de parámetros en la respuesta de la API de GET.

<!--## Transactional messages

* With Campaign Standard, a POST request returns empty fields for elements and attributes in the request body. With Campaign v8, the response returns values that match the ones in the request body instead.

* When publishing an event configuration, the API preview panel displays the REST URL alongside the request body syntax.

    Since Campaign v8 does not support event configuration fields definition (event creation is just adding a value to eventType enumeration), there is no API preview panel when adding an event type. The REST URL is displayed  in the transactional message user interface once an event transactional message is published.-->
