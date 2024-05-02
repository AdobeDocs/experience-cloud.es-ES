---
title: Promoción de la marca
description: Descubra todas las herramientas disponibles para administrar las identidades de marca
audience: administration
context-tags: branding,overview;branding,main
role: Admin
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 51abadc86b97097d13824651d8c50d4ddd014a51
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 18%

---

# Introducción a la marca {#branding-gs}

>[!IMPORTANT]
>
>Los usuarios finales no pueden crear ni modificar marcas: estas operaciones deben ser realizadas por el administrador técnico de Adobe Campaign. Para cualquier pregunta, póngase en contacto con el servicio de atención al cliente de Adobe.

Cada empresa tiene directrices de marca que definen tanto elementos visuales como detalles técnicos. Adobe Campaign le ayuda a administrar estas directrices de forma centralizada, para que pueda presentar una imagen de marca coherente a sus clientes en todo lo que haga, desde logotipos en correos electrónicos hasta URL y dominios utilizados en sus campañas.

Los administradores técnicos pueden crear y administrar varias marcas en Adobe Campaign. Esto le permite definir todos los elementos que componen su identidad de marca, incluidos los logotipos e incluso la configuración del seguimiento de correo electrónico. Una vez creadas, estas marcas se pueden vincular fácilmente a las entregas.

Puede añadir nuevas entidades de su organización en Campaign o crear un nuevo tipo de correo electrónico que debe enviar en un subdominio diferente. Para ello, siga los pasos a continuación:

1. **Configuración de un nuevo subdominio** : Para que cualquier nuevo subdominio se utilice en el Adobe, el primer paso será configurarlo. Puede realizar esta acción mediante [Panel de control de Campaign de campaña](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/subdomains-branding.html?lang=es) o póngase en contacto con el contacto técnico del Adobe. Más información sobre la configuración de subdominios [en esta página](https://experienceleague.adobe.com/en/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-domain-name-setup).

   >[!NOTE]
   >
   >Todos los usuarios administradores pueden acceder al Panel de control. Los pasos para otorgar acceso de administrador a un usuario se detallan en [esta página](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=es#discover-control-panel).

1. **Creación de una plantilla de envíos** - Una vez que la nueva marca está disponible, la práctica recomendada es crear al menos una nueva plantilla de envíos en blanco que haga referencia a esta nueva marca. [Más información](branding-assign.md).

1. **Comprobación de directrices de entrega** : Antes de empezar a utilizar el nuevo dominio, la estrategia debe discutirse con el equipo de entrega de Adobe. Ayudan a definir las prácticas recomendadas si, por ejemplo, se debe crear una nueva afinidad para dividir las IP entre dominios o si se debe definir un plan de ampliación.

