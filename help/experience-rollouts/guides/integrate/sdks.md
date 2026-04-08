---
title: SDK
description: Obtenga información acerca de la arquitectura de SDK en los Despliegues de Adobe Experience y la extensión móvil de SDK disponible para Android.
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 3%

---

# SDK {#sdks}

Los despliegues de experiencias proporcionan SDK para integrar indicadores de funcionalidades en sus aplicaciones. Esta página describe la arquitectura de SDK y las opciones disponibles.

## Arquitectura de SDK {#architecture}

Todos los SDK de despliegues de experiencias comparten la misma arquitectura principal:

* **Inicialización**: SDK se configura al inicio y se registra con el servicio Despliegues de experiencias.
* **Recuperación de características**: SDK recupera los datos de indicadores de características y evalúa los indicadores localmente.
* **Almacenamiento en caché**: SDK almacena en caché los datos de indicadores de características y los actualiza en un intervalo de sondeo (TTL) configurable.
* **Control de errores**: si el servicio no está disponible, SDK continúa ofreciendo evaluaciones de indicadores de características desde la caché local.

## SDK disponibles {#available-sdks}

### Extensión de Android {#android-extension}

La extensión de despliegue de experiencias para Android se integra con Adobe Experience Platform Mobile SDK.

Consulte la [guía de integración de extensiones de Android](../sdk-releases/android/android-extension-integration-guide.md) para obtener instrucciones de configuración.

>[!NOTE]
>
>Se están preparando opciones adicionales de SDK para plataformas web y otras plataformas móviles, que estarán disponibles próximamente. Póngase en contacto con su representante de Adobe para obtener ayuda sobre el acceso anticipado.

## Consulte también {#see-also}

* [Guía de integración de Android extension](../sdk-releases/android/android-extension-integration-guide.md)
* [Servicios web](web-services.md)
* [Pasos de integración](integration-steps.md)
