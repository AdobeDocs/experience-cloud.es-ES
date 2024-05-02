---
title: Resumen de devoluciones
description: Con el informe Predeterminado Resumen de devoluciones, obtenga información sobre el estado de las campañas enviadas y los errores que puedan haber encontrado.
audience: end-user
level: Intermediate
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 1%

---

# Resumen de devoluciones{#bounce-summary}

Este informe detalla los errores generales, tanto los errores graves como los leves que se han encontrado durante las entregas, así como el procesamiento automático de las devoluciones.

![](assets/campaign_reports_bounces.png)

Cada tabla está representada por números de resumen y gráficos. Puede cambiar cómo se muestran los detalles en sus respectivos ajustes de visualización.

**Flop 5 repartition** enumera las cinco entregas con el mayor número de cuarentenas:

El **Motivos del rechazo** contiene los datos disponibles para los tipos de errores que causaron devoluciones para cada entrega:

* **[!UICONTROL Usuario desconocido]**: Tipo de error generado cuando se envía un envío a una dirección de correo electrónico no válida.
* **[!UICONTROL Dominio no válido]**: Tipo de error generado cuando se realiza un envío a una dirección de correo electrónico cuyo dominio es incorrecto o ya no existe.
* **[!UICONTROL Inaccesible]**: tipo de error encontrado en la cadena de entrega de mensajes, como dominio temporalmente inaccesible.
* **[!UICONTROL Cuenta deshabilitada]**: Tipo de error generado cuando se realiza un envío a una dirección de correo electrónico que ya no existe.
* **[!UICONTROL Buzón lleno]**: Tipo de error generado cuando la bandeja de entrada del destinatario está llena. Hay cinco intentos de enviar el mensaje antes de que se genere este error.
* **[!UICONTROL Sin conexión]**: Tipo de error generado cuando el teléfono móvil del destinatario está apagado o no está conectado a una red en el momento en que se envía el mensaje.

  >[!NOTE]
  >
  >Este tipo de error solo afecta a las entregas de canales móviles.

* **[!UICONTROL Rechazado]**: Tipo de error generado cuando el proveedor de servicios de Internet (ISP) rechaza una dirección. Por ejemplo, cuando un software antispam ha aplicado una regla de seguridad.

El **Repartición de dominio** La tabla muestra los problemas generales encontrados durante las entregas según el dominio del destinatario.
