---
title: Puntos de conexión
description: Obtenga más información acerca de los extremos de las API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 9%

---

# Puntos de conexión {#endpoints}

Los extremos disponibles para la API de REST de Adobe Campaign:

* **/profileAndServices**: interactúe con los campos predeterminados. No se puede acceder a los campos extendidos con este extremo.
* **/profileAndServicesExt**: interactúe con los campos personalizados agregados durante la extensión de recurso personalizado de Perfil o Servicios. Para obtener más información sobre recursos personalizados, consulte [esta sección](custom-resources.md).
* **/&lt;transactionalapi>**: interactúe con la API de mensajes transaccionales (el nombre del punto final de la API de mensajes transaccionales depende de la configuración de la instancia). Para obtener más información, consulte [esta sección](managing-transactional-messages.md).
* **/workflow/execution**: interactúe con flujos de trabajo. Para obtener más información, consulte [esta sección](controlling-a-workflow.md).

De forma predeterminada, los recursos principales disponibles para **profileAndServices** y **profileAndServicesExt** Las API son:

* **/perfil**: interactúe con los perfiles de la base de datos de Campaign. Para añadir perfiles a un servicio, utilice el **/service** punto final. Para obtener más información sobre los perfiles en Campaign, consulte [Documentación de Campaign](https://helpx.adobe.com/campaign/standard/audiences/using/about-profiles.html).
* **/service**: administre los servicios de suscripción. Para obtener más información sobre los servicios de Campaign, consulte la [Documentación de Campaign](https://helpx.adobe.com/campaign/standard/audiences/using/creating-a-service.html).

>[!NOTE]
>
>Todos los demás recursos que se han ampliado o creado están disponibles a través de la **ProfileAndServicesExt** Solo API. Deben estar vinculados al **Perfil** para que sea accesible.
