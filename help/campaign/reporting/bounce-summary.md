---
title: Resumen de devoluciones
description: Con el informe Predeterminado Resumen de devoluciones, obtenga información sobre el estado de las campañas enviadas y los errores que puedan haber encontrado.
audience: end-user
level: Intermediate
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: b341edad-aa82-43d8-a5a1-b33a19973a1a
TQID: https://experienceleague.adobe.com/gfOXWpdQvONw72sdpnGehwpXcgte16B6dLiWV2LZXOc
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 298
ht-degree: 8%

---

# Resumen de devoluciones{#bounce-summary}

Este informe detalla los errores generales, tanto los errores graves como los leves que se han encontrado durante las entregas, así como el procesamiento automático de las devoluciones.

![](assets/campaign_reports_bounces.png)

Cada tabla está representada por números de resumen y gráficos. Puede cambiar cómo se muestran los detalles en sus respectivos ajustes de visualización.

**Flop 5 repartition** enumera las cinco entregas con el mayor número de cuarentenas:

La tabla **Razones de rechazo** contiene los datos disponibles para los tipos de errores que causaron devoluciones en cada envío:

* **[!UICONTROL Usuario desconocido]**: Tipo de error generado cuando se envía un envío a una dirección de correo electrónico no válida.
* **[!UICONTROL Dominio no válido]**: Tipo de error generado cuando se envía una entrega a una dirección de correo electrónico cuyo dominio es incorrecto o ya no existe.
* **[!UICONTROL Inaccesible]**: tipo de error encontrado en la cadena de entrega de mensajes, como un dominio temporalmente inaccesible.
* **[!UICONTROL Cuenta deshabilitada]**: Tipo de error generado cuando se envía una entrega a una dirección de correo electrónico que ya no existe.
* **[!UICONTROL Buzón lleno]**: Tipo de error generado cuando la bandeja de entrada del destinatario está llena. Hay cinco intentos de enviar el mensaje antes de que se genere este error.
* **[!UICONTROL No conectado]**: Tipo de error generado cuando el teléfono móvil del destinatario está apagado o no está conectado a una red en el momento de enviar el mensaje.

  >[!NOTE]
  >
  >Este tipo de error solo afecta a las entregas de canales móviles.

* **[!UICONTROL Rechazado]**: Tipo de error generado cuando el proveedor de servicios Internet (ISP) rechaza una dirección. Por ejemplo, cuando un software antispam ha aplicado una regla de seguridad.

La tabla **Domain repartition** muestra los problemas generales encontrados durante las entregas según el dominio del destinatario.
