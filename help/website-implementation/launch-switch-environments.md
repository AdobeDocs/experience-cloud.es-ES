---
title: Cambiar entornos de inicio con Adobe Experience Cloud Debugger
description: Obtenga información sobre cómo utilizar Experience Cloud Debugger para cargar distintos códigos incrustados de Launch. Esta lección forma parte del tutorial Implementación de Experience Cloud en sitios web con Launch.
seo-description: null
seo-title: Cambiar entornos de inicio con Adobe Experience Cloud Debugger
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 79d5274d09d66b80a49aba5db3e0a997d0f0ff61

---


# Cambiar entornos de inicio con Experience Cloud Debugger

In this lesson you will use the [Adobe Experience Cloud Debugger extension](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) to replace the Launch property hardcoded on the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) with your own property.

Esta técnica se denomina cambio de entorno y será útil posteriormente, cuando trabaje con Launch en su propio sitio web. Podrá cargar su sitio web de producción en su navegador, pero con su entorno de *desarrollo* Launch. Esto le permite realizar y validar con confianza los cambios de Launch independientemente de las versiones de código habituales.  Después de todo, esta separación de las versiones de etiquetas de marketing de las versiones de código normal es una de las principales razones por las que los clientes utilizan Launch en primer lugar.

## Objetivos de aprendizaje

Al final de esta lección podrá:

* Utilice el depurador para cargar un entorno de lanzamiento alternativo
* Use el depurador para validar que ha cargado un entorno de lanzamiento alternativo

## Obtenga la dirección URL de su entorno de desarrollo

1. In your Launch property, open the `Environments` page

1. In the **[!UICONTROL Development]** row, click the Install icon ![Install icon](images/launch-installIcon.png) to open the modal

1. Haga clic en el icono Copiar ![Copiar icono](images/launch-copyIcon.png) Copiar para copiar el código incrustado en el portapapeles

1. Click **[!UICONTROL Close]** to close the modal

   ![Icono de instalación](images/launch-copyInstallCode.png)

## Reemplazar la URL de inicio en el sitio de demostración de luminancia

1. Open the [Luma demo site](https://luma.enablementadobe.com/content/luma/us/en.html) in your Chrome browser

1. Abra la extensión [de](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) Experience Cloud Debugger haciendo clic en el icono ![Debugger](images/icon-debugger.png)

   ![Haga clic en el icono del depurador](images/switchEnvironments-openDebugger.png)

1. Tenga en cuenta que la propiedad Launch implementada actualmente se muestra en la ficha Resumen

   ![Entorno de lanzamiento mostrado en Debugger](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Vaya a la ficha Herramientas

1. Desplácese a la sección **[!UICONTROL Reemplazar código incrustado de lanzamiento]**

1. Asegúrese de que la ficha Chrome con el sitio Luma está en el centro de atención detrás del depurador (no la ficha con este tutorial o la ficha con la interfaz Launch).  Pegue el código incrustado que se encuentra en el portapapeles en el campo de entrada

1. Alternar en la función "Aplicar en luma.enablementadobe.com" para que todas las páginas del sitio de luminancia se asignen a la propiedad Launch

1. Haga clic en el botón **[!UICONTROL Guardar]** .

   ![Entorno de lanzamiento mostrado en Debugger](images/switchEnvironments-debugger-save.png)

1. Vuelva a cargar el sitio Luma y marque la ficha Resumen del depurador. En la sección Inicio, debería ver que se está utilizando la propiedad Desarrollo. Confirme que el nombre de la propiedad coincide con el suyo y que el entorno indica "desarrollo".

   ![Entorno de lanzamiento mostrado en Debugger](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE] El depurador guardará esta configuración y reemplazará los códigos de incrustación de Launch cada vez que vuelva al sitio de Luma. No afectará a otros sitios que visite en otras fichas abiertas. To stop the Debugger from replacing the embed code, click the **[!UICONTROL Remove]** button next to the embed code in the Tools tab of the Debugger.

A medida que continúe con el tutorial, utilizará esta técnica de asignación del sitio de Luma a su propia propiedad Launch para validar la implementación de Launch. Cuando comience a utilizar Launch en el sitio web de producción, puede utilizar esta misma técnica para validar los cambios.

[Siguiente "Add the Adobe Experience Platform Identity Service" &gt;](id-service.md)