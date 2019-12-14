---
title: Creación de una propiedad de inicio para aplicaciones móviles
description: Obtenga información sobre cómo iniciar sesión en la interfaz de Launch y crear una propiedad de lanzamiento móvil. Esta lección forma parte del tutorial Implementación de Experience Cloud en aplicaciones móviles de Swift para iOS.
seo-description: null
seo-title: Creación de una propiedad de inicio para aplicaciones móviles
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Crear una propiedad de inicio

Adobe Experience Platform Launch es la próxima generación de SDK móvil y funciones de administración de etiquetas de sitios web. Launch ofrece a los clientes una forma sencilla de implementar y administrar todas las soluciones de análisis, marketing y publicidad necesarias para potenciar las experiencias relevantes de los clientes. No hay ningún cargo adicional por Launch. Está disponible para cualquier cliente de Adobe Experience Cloud.

En esta lección, creará una propiedad Launch para las aplicaciones móviles.

## Requisitos previos

Para completar las siguientes lecciones, debe tener permiso para desarrollar, aprobar, publicar, administrar extensiones y administrar entornos en Launch. Si no puede completar ninguno de estos pasos porque las opciones de la interfaz de usuario no están disponibles para usted, póngase en contacto con el administrador de Experience Cloud para solicitar acceso. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).

## Objetivos de aprendizaje

Al final de esta lección podrá:

* Inicie sesión en la interfaz de usuario de Launch
* Crear una nueva propiedad móvil Launch
* Configurar una propiedad móvil Launch

## Vaya a Launch

**Para llegar al lanzamiento**

1. Inicie sesión en [Adobe Experience Cloud](https://experiencecloud.adobe.com)

1. Haga clic en el icono del ![conmutador de soluciones](images/mobile-launch-solutionSwitcher.png) para abrir el conmutador de soluciones

1. Select **[!UICONTROL Launch]** from the menu

   ![Abra el conmutador de soluciones mediante el icono y haga clic en Activación](images/mobile-launch-solutionSwitcherActivation.png)

1. En Inicio **[!UICONTROL de]** Adobe Experience Cloud, haga clic en el botón **[!UICONTROL Ir a inicio]**

   ![Haga clic en el botón Iniciar](images/mobile-launch-goToLaunch.png)

You should now see the `Properties` screen (if no properties have ever been created in the account, this screen might be empty):

![Pantalla Propiedades](images/mobile-launch-propertiesScreen.png)

Si utiliza Launch con frecuencia, también puede marcar la siguiente URL e iniciar sesión directamente [https://launch.adobe.com](https://launch.adobe.com)

## Crear una propiedad

Una propiedad es básicamente un contenedor que se rellena con extensiones, reglas, elementos de datos y bibliotecas a medida que se implementan etiquetas en la aplicación. Se puede usar una sola propiedad móvil en varias plataformas de aplicación (por ejemplo, iOS y Android) siempre que las aplicaciones contengan una funcionalidad similar y requieran que se implementen las mismas soluciones.  Para obtener más información sobre la creación de propiedades, consulte ["Configuración de una propiedad móvil"](https://aep-sdks.gitbook.io/docs/getting-started/create-a-mobile-property) en la documentación del producto.

**Creación de una propiedad**

1. Haga clic en el botón **[!UICONTROL Nueva propiedad]** :

   ![Haga clic en Nueva propiedad](images/mobile-launch-addNewProperty.png)

1. Asigne un nombre a la propiedad (p. ej. `Mobile Tutorial`)
1. Como plataforma, haga clic en **[!UICONTROL Móvil]**
1. Haga clic en el botón **[!UICONTROL Guardar]** .

   ![Crear una nueva propiedad](images/mobile-launch-newProperty.png)

La nueva propiedad debe mostrarse en la página Propiedades. Note that if you check the box next to the property name, options to **[!UICONTROL Configure]** or **[!UICONTROL Delete]** the property appear above the property list. Haga clic en el nombre de su propiedad (p. ej. `Mobile Tutorial`) para abrir la `Overview` pantalla.
![Haga clic en el nombre de la propiedad para abrirla](images/mobile-launch-openProperty.png)

[Siguiente "Agregar extensiones" &gt;](launch-add-extensions.md)
