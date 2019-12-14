---
title: Implementación de Adobe Experience Cloud en sitios web con Adobe Experience Platform Launch
description: La implementación de Experience Cloud en sitios web con Launch es el punto de partida perfecto para desarrolladores de front-end o especialistas en marketing técnico que deseen aprender a implementar las soluciones de Adobe Experience Cloud en su sitio web.
seo-description: null
seo-title: Implementación de Adobe Experience Cloud en sitios web con Adobe Experience Platform Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: 7166d2933cc99bcbbd4713fba8f87fb0826b711e

---


# Información general

_La implementación de Experience Cloud en sitios web con Launch_ es el punto de partida perfecto para desarrolladores de front-end o especialistas en marketing técnico que deseen aprender a implementar las soluciones de Adobe Experience Cloud en su sitio web.

Cada lección contiene ejercicios prácticos e información básica que le ayudará a implementar Experience Cloud y a comprender su valor.  Las llamadas se proporcionan para resaltar información que puede resultar útil para los clientes que migran desde nuestro administrador de etiquetas más antiguo: la administración dinámica de etiquetas. Se proporcionan sitios de muestra para completar el tutorial, lo que le permite aprender las técnicas subyacentes en un entorno seguro. Después de completar este tutorial, estará listo para empezar a implementar todas las soluciones de mercadotecnia a través de Launch en su propio sitio web.

Después de completar esto, podrá:

* Crear una propiedad de inicio

* Instalación de una propiedad de lanzamiento en un sitio web

* Agregue las siguientes soluciones de Adobe Experience Cloud:
   * **[Servicio de ID de Adobe Experience Platform](id-service.md)**
   * **[Adobe Target](target.md)**
   * **[Adobe Analytics](analytics.md)**
   * **[Adobe Audience Manager](audience-manager.md)**

* Cree reglas y elementos de datos para enviar datos a las soluciones de Adobe

* Validar la implementación con Adobe Experience Cloud Debugger

* Publique cambios en Launch mediante entornos de desarrollo, ensayo y producción

>[!NOTE] También hay tutoriales de varias soluciones similares disponibles para las siguientes plataformas:
>
> * [Implementación de Experience Cloud en aplicaciones móviles iOS Swift™](/help/mobile-ios-swift-implementation/index.md)
* [Implementación de Experience Cloud en aplicaciones de iOS con objetivos C para dispositivos móviles](/help/mobile-ios-objective-c-implementation/index.md)
* [Implementación de Experience Cloud en aplicaciones móviles para Android](/help/mobile-android-implementation/index.md)


## Requisitos previos

En estas lecciones, se supone que dispone de un Adobe Id y de los permisos necesarios para completar los ejercicios. Si no es así, es posible que deba ponerse en contacto con el administrador de Experience Cloud para solicitar acceso.

* Para Launch, debe tener permiso para desarrollar, aprobar, publicar, administrar extensiones y administrar entornos. For more information on Launch permissions, see [the documentation](https://docs.adobe.com/content/help/en/launch/using/reference/admin/user-permissions.html).
* Para Adobe Analytics, debe conocer el servidor de seguimiento y los grupos de informes que utilizará para completar este tutorial
* Para Audience Manager, debe conocer el subdominio de Audience Manager (también conocido como "Nombre del socio", "ID del socio" o "Subdominio del socio")

Además, se da por hecho que está familiarizado con los lenguajes de desarrollo front-end como HTML y JavaScript. No necesita dominar a la perfección estos lenguajes para completar las lecciones, pero obtendrá más información si puede leer y comprender el código con comodidad.

## Acerca de Launch

Adobe Experience Platform Launch es la próxima generación de funciones de administración de etiquetas de sitios web y SDK móviles de Adobe. Launch ofrece a los clientes una forma sencilla de implementar y administrar todas las soluciones de análisis, marketing y publicidad necesarias para potenciar las experiencias relevantes de los clientes. No hay ningún cargo adicional por Launch. Está disponible para cualquier cliente de Adobe Experience Cloud.

Launch para sitios web le permite administrar de forma centralizada todo el código JavaScript relacionado con las soluciones de análisis, marketing y publicidad utilizadas en los sitios de escritorio y móviles. Por ejemplo, si implementa Adobe Analytics, Launch administrará la biblioteca JavaScript de AppMeasurement, rellenará las variables y activará las solicitudes.

La etiqueta de contenedor de lanzamiento es un 60% más ligera que la DTM y un 40% más ligera que el Administrador de etiquetas de Google. El contenido de su contenedor, que incluye su código personalizado, se reduce al máximo. Todo es modular. Si no ve un elemento, dicho elemento no está incluido en su biblioteca. El resultado es una implementación rápida y compacta.

Launch es también una plataforma que permite a los proveedores externos crear extensiones para facilitar la implementación de sus soluciones mediante Launch. Una extensión es un paquete de códigos (JavaScript, HTML y CSS) que amplía la funcionalidad del cliente y la interfaz de usuario de Launch. Podríamos equiparar a Launch con un sistema operativo y a las extensiones con las aplicaciones que usa para realizar sus tareas.

## Acerca de las lecciones

En estas lecciones, implementará Adobe Experience Cloud en un sitio web de venta minorista falso denominado Luma. El sitio [](https://luma.enablementadobe.com/content/luma/us/en.html) Luma tiene una capa de datos y una funcionalidad enriquecidas que le permitirán crear una implementación realista. Creará su propia propiedad Launch, en su propia organización de Experience Cloud, y la asignará a nuestro sitio de Luma alojado mediante Experience Cloud Debugger.

[![Sitio web Luma](images/overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)

## Obtención de las herramientas

1. Ya que se utilizan varias extensiones específicas del explorador, le recomendamos que complete el tutorial utilizando el explorador web [Chrome](https://www.google.com/chrome/)
1. Add the [Adobe Experience Cloud Debugger](https://chrome.google.com/webstore/detail/adobe-experience-cloud-de/ocdmogmohccmeicdhlhhgepeaijenapj) extension to your Chrome browser
1. Download the [sample html page](https://www.enablementadobe.com/multi/web/basic-sample.html) (right-click on this link and click "Save Link As")
1. Obtenga un editor de texto en el que puede realizar cambios en la página HTML de muestra. (Si no tiene uno, le recomendamos que pruebe [los corchetes](http://brackets.io/))
1. Marcar el sitio [Luma](https://luma.enablementadobe.com/content/luma/us/en.html)

>[!NOTE] Puede que le resulte más fácil completar este tutorial con el sitio Luma abierto en Chrome, mientras lee este tutorial y completa los pasos de la interfaz de Launch en un navegador diferente.

Empecemos!

[Siguiente "Crear una propiedad de lanzamiento" &gt;](launch.md)