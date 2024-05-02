---
title: Promoción de la marca
description: Descubra cómo configurar su marca
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 56f2d2ff4b2ba4184629615a14724e6640df6961
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 57%

---

# Configurar marcas {#branding-configure}

>[!IMPORTANT]
>
>Los usuarios finales no pueden crear ni modificar marcas: estas operaciones deben ser realizadas por el administrador técnico de Adobe Campaign. Para cualquier pregunta, póngase en contacto con el servicio de atención al cliente de Adobe.

En Adobe Campaign V8, las marcas se encuentran en **[!UICONTROL Administración > Plataforma > Marca]** menú.

Una **[!UICONTROL marca]** se define con las siguientes características:

* Una **[!UICONTROL identidad]**, que define y personaliza su marca. Esta sección contiene los campos siguientes:

   * **[!UICONTROL Etiqueta]** visible en la interfaz.
   * **[!UICONTROL ID]**
   * **[!UICONTROL Nombre de la marca]**.
   * **[!UICONTROL Dirección URL]** y **[!UICONTROL etiqueta del sitio web]** de la marca.
   * **[!UICONTROL Logotipo de marca]**.

  ![](assets/branding_1.png)

* **[!UICONTROL Parámetros de encabezado de correos electrónicos enviados]** , que personaliza lo que ven los destinatarios de sus campañas. Esta sección contiene los campos siguientes:

   * **[!UICONTROL Remitente (dirección de correo electrónico)]** con la dirección de correo electrónico de la marca.
   * **[!UICONTROL Remitente (nombre)]** con el nombre de la marca.
   * **[!UICONTROL Responder a (dirección de correo electrónico)]** con la dirección de correo electrónico a la que el cliente puede responder.
   * **[!UICONTROL Responder a (nombre)]** con el nombre de la marca.
   * **[!UICONTROL Error (dirección de correo electrónico)]** con la dirección de correo electrónico que se utiliza en caso de error.

  >[!IMPORTANT]
  >
  >Después de haber actualizado los parámetros de encabezado de los correos electrónicos, si el nombre y la dirección de correo electrónico del remitente no han cambiado en el correo electrónico creado a partir de la plantilla, compruebe la configuración avanzada de esta.

  ![](assets/branding_2.png)

* **[!UICONTROL Configuraciones de marca]** define los servidores utilizados para el seguimiento también para el acceso a la página de aterrizaje. Esta sección contiene los campos siguientes:

   * **[!UICONTROL Subdominio de marca]** hace referencia a la dirección URL del subdominio designado específica de esta marca, solicitada para la delegación desde el Adobe.

  Tenga en cuenta que la configuración de los servidores de seguimiento, réplica y aplicaciones se almacena en cuentas externas independientes asociadas con el enrutamiento. Esta configuración se aplica durante el aprovisionamiento y no debe modificarse. Para mostrar las direcciones URL, acceda al **[!UICONTROL Prefijos de marca]** de la cuenta externa.

  ![](assets/branding_3.png)

<!--![](assets/branding_05.png)-->

<!--
* **[!UICONTROL Tracking URL configs]**, which defines the configuration of the URLs tracking for your brand.

  The additional parameters that allow the links to be tracked on external systems such as Web Analytics tools like Adobe Analytics or Google Analytics are defined here.
-->
