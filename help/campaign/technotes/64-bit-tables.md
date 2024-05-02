---
title: Interfaz de usuario web de Adobe Campaign
description: Tablas de 64 bits
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 47b06a42fad73254025d8e21d14724f6fe93345b
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 6%

---


# Esquemas de 64 bits {#64-bit-tables}

Para facilitar la transición de Campaign Standard a Campaign v8, se han cambiado varias tablas de 32 a 64 bits. De hecho, Campaign Standard admite PK de 64 bits en varios esquemas predeterminados, mientras que Campaign v8 admite PK de 32 bits en la mayoría de los esquemas.

## Limitaciones

* Este cambio técnico solo se aplica a los clientes que migran de Campaign Standard.
* La extensión de esquema y &quot;broadlog&quot; no es compatible con 64 bits. Permanecerá en 32 bits.
* Los registros relacionados con las entregas enviadas a los usuarios técnicos no estarán disponibles en Campaign v8.
* Solo se admite PostgreSQL.

## Esquemas modificados

Esta es la lista de esquemas cambiados a 64 bits y sus atributos modificados.

| Nombre del esquema | Nombre del atributo |
|--- |--- |
| nms:broadLogRcp | id |
| nms:trackingLogRcp | id |
| nms:excludeLogRcp | id |
| nms:broadLogVisitor | id |
| nms:trackingLogVisitor | id |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrackingLog | id |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | id |
| nms:trackingLogAppSubRcp | id |
| nms:excludeLogAppSubRcp | id |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |


