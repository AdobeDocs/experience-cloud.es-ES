---
title: Puntos de conexión
description: Obtenga más información acerca de los extremos de las API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Developer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: 9f6d3da6-374d-47f5-bc8f-b31b19cbb5ca
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 9%

---

# Puntos de conexión {#endpoints}

Los extremos disponibles para la API de REST de Adobe Campaign:

* **/profileAndServices**: interactúe con los campos predeterminados. No se puede acceder a los campos extendidos con este extremo.
* **/profileAndServicesExt**: interactúe con los campos personalizados agregados durante la extensión de recursos personalizados de perfil o servicios. Para obtener más información sobre los recursos personalizados, consulte [esta sección](custom-resources.md).
* **/&lt;transactionalAPI>**: interactúe con la API de mensajes transaccionales (el nombre del extremo de la API de mensajes transaccionales depende de la configuración de su instancia). Para obtener más información, consulte [esta sección](managing-transactional-messages.md).
* **/workflow/execution**: interactuar con flujos de trabajo. Para obtener más información, consulte [esta sección](controlling-a-workflow.md).

De manera predeterminada, los recursos principales disponibles para las API **profileAndServices** y **profileAndServicesExt** son:

* **/profile**: interactúe con los perfiles de la base de datos de Campaign. Para agregar perfiles a un servicio, use el extremo **/service**. Para obtener más información sobre los perfiles de Campaign, consulte la [Documentación de Campaign](https://helpx.adobe.com/campaign/standard/audiences/using/about-profiles.html).
* **/servicio**: administrar servicios de suscripción. Para obtener más información sobre los servicios de Campaign, consulte la [Documentación de Campaign](https://helpx.adobe.com/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Todos los demás recursos que se han ampliado o creado están disponibles únicamente a través de la API **ProfileAndServicesExt**. Deben estar vinculados al recurso **Profile** para que sea accesible.
