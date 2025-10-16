---
title: Interfaz de usuario web de Adobe Campaign
description: Tablas de 64 bits
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
source-git-commit: 11c49b273164b632bcffb7de01890c6f9d7ae9c2
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 7%

---

# Esquemas de 64 bits {#sixty-four-bit-tables}

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
| nms:broadLogRcp | Identificación |
| nms:trackingLogRcp | Identificación |
| nms:excludeLogRcp | Identificación |
| nms:broadLogVisitor | Identificación |
| nms:trackingLogVisitor | Identificación |
| nms:propositionRcp | interactionId |
| nms:propositionVisitor | interactionId |
| nms:webTrackingLog | Identificación |
| nms:tmpBroadcast | message-id |
| nms:tmpMarketingPressure | message-id |
| nms:tmpBroadcastExclusion | message-id |
| nms:tmpBroadcastPaper | message-id |
| nms:broadLogAppSubRcp | Identificación |
| nms:trackingLogAppSubRcp | Identificación |
| nms:excludeLogAppSubRcp | Identificación |
| nms:webEvent | broadLogSrc-id, broadLogRemkt-id |
| nms:broadLogMid | mktBroadLogId |
| nms:mirrorPageSearch | remoteMessageId |
