---
title: Pasos de integración
description: Siga los pasos de integración del tipo de aplicación para conectar los despliegues de Adobe Experience a su servicio web, aplicación web o móvil o aplicación de escritorio.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 3%

---


# Pasos de integración {#integration-steps}

Elija la ruta de integración que coincida con el tipo de aplicación.

## Servicios web {#web-services}

Los servicios back-end se integran con una SDK del lado del servidor. Elija el SDK para su pila de tecnología.

**Java**

Siga la [guía de integración de Java SDK](../sdk-releases/java/java-sdk-integration-guide.md) para la instalación, configuración de dependencia e inicialización.

**Nodo.js**

Siga la [guía de integración de SDK de Node.js](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md) para la instalación e inicialización.

**Otros idiomas**

Si la pila no aparece en la lista anterior, integre directamente con la **API de características V3** (consulte la sección API de características de esta guía). Póngase en contacto con el servicio de asistencia de Despliegues de experiencias si necesita ayuda.

## Aplicaciones web y móviles {#web-mobile}

Las aplicaciones web y móviles llaman a la **API de características V3** para recuperar los indicadores de características del usuario actual y aplicar lógica condicional en la aplicación.

Consulte **API de características de GET V3** en la sección API de características de esta guía para obtener la referencia completa de la API.

## Aplicaciones de escritorio {#desktop}

Las aplicaciones de escritorio llaman a la **API de características V2** para recuperar los indicadores de características.

Consulte **GET Feature API V2** en la sección Feature API de esta guía para obtener la referencia completa de la API.

>[!IMPORTANT]
>
>Los clientes de escritorio deben respetar el valor TTL en la respuesta de API e implementar la gestión de errores correcta para la no disponibilidad de la API. Consulte [Aplicaciones de escritorio](desktop-applications.md) para conocer los requisitos.

## Consulte también {#see-also}

* [Guía de inicio](startup-guide.md)
* [SDK](sdks.md)
* [Servicios web](web-services.md)
* [Aplicaciones de escritorio](desktop-applications.md)
