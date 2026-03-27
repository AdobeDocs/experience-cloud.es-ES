---
title: SDK
description: Obtenga información acerca de la arquitectura de SDK en los Despliegues de Adobe Experience y los SDK disponibles para Java y Node.js.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 2%

---

# SDK {#sdks}

Los despliegues de experiencia proporcionan SDK del lado del servidor para la integración del servicio back-end. Esta página describe la arquitectura de SDK y las opciones disponibles.

## Arquitectura de SDK {#architecture}

Todos los SDK de despliegues de experiencias comparten la misma arquitectura principal:

* **Inicialización**: SDK se configura mediante una llamada de `createInstance()` que devuelve un objeto singleton.
* **Recuperación de características**: el método `getFeatures()` recupera datos de indicadores de características de SDK.
* **Almacenamiento en caché**: SDK almacena en caché las respuestas del servicio Despliegues de experiencias. Un Administrador de caché actualiza la caché en un intervalo de sondeo (TTL) configurable.
* **Control de errores**: si el servicio devuelve un error 503, el Administrador de caché retendrá los datos en caché existentes y seguirá sirviendo las evaluaciones de indicadores de características. Si los datos no han cambiado desde la última llamada (304), la caché no se actualiza.

## Requisitos previos {#prerequisites}

Antes de integrar un SDK, asegúrese de que dispone de lo siguiente:

1. **ID de aplicación**: el ID de cliente para cada aplicación integrada en la consola Despliegues de experiencias.
2. **Token de servicio** — Utilizado por SDK para llamar a las API de despliegues de experiencia en segundo plano.
3. **Clave de API**: se usa junto con el token de servicio para la autenticación de API.

## SDK disponibles {#available-sdks}

### SDK de Java {#java-sdk}

Java SDK se distribuye mediante Maven. Agregue la dependencia a `pom.xml` de su proyecto para integrarla. En el caso de las aplicaciones basadas en Spring, la dependencia de Maven configura automáticamente la caché de SDK antes de que la aplicación se cargue completamente.

Especificaciones clave de Java SDK:

* **JDK compatible:** JDK 8 y posterior
* **Clientes no almacenables en caché:** Compatible a partir de la versión 0.8 de SDK. Para los clientes que no se pueden almacenar en caché, `getFeature()` realiza una llamada de API activa en lugar de leer la caché. SDK continúa encuestando en segundo plano y cambia al servicio basado en caché si el cliente se puede almacenar en caché.

Consulte la [Guía de integración de Java SDK](../sdk-releases/java/java-sdk-integration-guide.md) para obtener instrucciones de configuración.

### SDK de Node.js {#nodejs-sdk}

La SDK de Node.js se distribuye mediante npm.

Consulte la [Guía de integración de SDK de Node.js](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md) para obtener instrucciones de configuración.

## Consulte también {#see-also}

* [Servicios web](web-services.md)
* [Pasos de integración](integration-steps.md)
* [Guía de integración de Java SDK](../sdk-releases/java/java-sdk-integration-guide.md)
* [Guía de integración de SDK de Node.js](../sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
