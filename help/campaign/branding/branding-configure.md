---
title: Promoción de la marca
description: Descubra cómo configurar su marca
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados de Campaign Standard"
exl-id: 7afc802d-e90c-48c8-aa04-3ea543dfdfbc
TQID: https://experienceleague.adobe.com/hnN2EgVkkBA0Zp6NYqk2ID2XgHjv1EBDrWRW7k7qJ7Q
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
feature_v2:
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: ad84694f2f6f45e4ee30fc51379106835ac302be
workflow-type: tm+mt
source-wordcount: 380
ht-degree: 42%

---

# Configurar marcas {#branding-configure}

>[!IMPORTANT]
>
>Los usuarios finales no pueden crear ni modificar marcas: estas operaciones deben ser realizadas por el administrador técnico de Adobe Campaign. Para cualquier pregunta, póngase en contacto con el servicio de atención al cliente de Adobe.

En Adobe Campaign V8, las marcas se encuentran en el menú **[!UICONTROL Administración > Plataforma > Marca]**.

Una **[!UICONTROL marca]** se define con las siguientes características:

* Una **[!UICONTROL identidad]**, que define y personaliza su marca. Esta sección contiene los campos siguientes:

   * **[!UICONTROL Etiqueta]** visible en la interfaz.
   * **[!UICONTROL ID]**
   * **[!UICONTROL Nombre de la marca]**.
   * **[!UICONTROL Dirección URL]** y **[!UICONTROL etiqueta del sitio web]** de la marca.
   * **[!UICONTROL Logotipo de marca]**.

  ![](assets/branding_1.png)

* **[!UICONTROL Parámetros de encabezado de correos electrónicos enviados]** que personalizan lo que verán los destinatarios de sus campañas. Esta sección contiene los campos siguientes:

   * **[!UICONTROL Remitente (dirección de correo electrónico)]** con la dirección de correo electrónico de la marca.
   * **[!UICONTROL Remitente (nombre)]** con el nombre de la marca.
   * **[!UICONTROL Responder a (dirección de correo electrónico)]** con la dirección de correo electrónico a la que el cliente puede responder.
   * **[!UICONTROL Responder a (nombre)]** con el nombre de la marca.
   * **[!UICONTROL Error (dirección de correo electrónico)]** con la dirección de correo electrónico que se utiliza en caso de error.

  >[!IMPORTANT]
  >
  >Después de haber actualizado los parámetros de encabezado de los correos electrónicos, si el nombre y la dirección de correo electrónico del remitente no han cambiado en el correo electrónico creado a partir de la plantilla, compruebe la configuración avanzada de esta.

  ![](assets/branding_2.png)

* **[!UICONTROL Configuraciones de marca]** define los servidores que se usan para realizar el seguimiento también para el acceso a la página de aterrizaje. Esta sección contiene los campos siguientes:

   * **[!UICONTROL Subdominio de marca]** hace referencia a la dirección URL de subdominio designada específica de esta marca, solicitada para delegación desde Adobe.

  Tenga en cuenta que la configuración de los servidores de seguimiento, réplica y aplicaciones se almacena en cuentas externas independientes asociadas con el enrutamiento. Esta configuración se aplica durante el aprovisionamiento y no debe modificarse. Para mostrar las direcciones URL, acceda a la pestaña **[!UICONTROL Prefijos de marca]** desde su cuenta externa.

  ![](assets/branding_3.png)

* El menú **[!UICONTROL Configuraciones de URL de seguimiento]** le permite mejorar el seguimiento de URL mediante la definición de parámetros adicionales para la integración con herramientas de Web Analytics como Adobe Analytics y Google Analytics.

  Utilice el menú **[!UICONTROL Parámetros de URL adicionales]** para crear parámetros adicionales como pares clave-valor junto con sus condiciones de aplicabilidad. Cada nombre de parámetro debe ser único y no vacío, y cada valor de parámetro no debe estar vacío. La condición de aplicabilidad puede estar vacía, pero ninguno de estos valores puede incluir etiquetas JST.

  Estos parámetros se aplicarán a las direcciones URL rastreadas que coincidan con cualquier nombre de dominio especificado en la **[!UICONTROL Lista de nombres de dominio]**, que puede incluir expresiones regulares.
