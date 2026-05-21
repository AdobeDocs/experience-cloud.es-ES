---
title: Interfaz de usuario web de Adobe Campaign
description: Tablas de 64 bits
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: ab5f01fd-4ad5-46e9-b132-011fe0f7bbd2
TQID: https://experienceleague.adobe.com/D0f4gYkyUcNVpGxpvj3JrBGRyIAgSq1mF7R4ld5COmk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 175
ht-degree: 17%

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
