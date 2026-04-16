---
title: SDK
description: Obtenga información acerca de la arquitectura de SDK en Banderas y las extensiones disponibles de AEP Web SDK y AEP Mobile SDK.
hide: true
exl-id: 110a440d-b52a-4e1e-a94f-86f9741a223a
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 4%

---

# SDK {#sdks}

Marcas proporciona SDK para integrar marcas de características en sus aplicaciones. Flags se implementa mediante AEP Web SDK y AEP Mobile SDK.

## Arquitectura de SDK {#architecture}

Todos los SDK de marcas comparten la misma arquitectura principal:

* **Inicialización**: SDK se configura durante el inicio y se registra con el servicio Marcas.
* **Recuperación de características**: SDK recupera los datos de indicadores de características y evalúa los indicadores localmente.
* **Almacenamiento en caché**: SDK almacena en caché los datos de indicadores de características y los actualiza en un intervalo de sondeo (TTL) configurable.
* **Control de errores**: si el servicio no está disponible, SDK continúa ofreciendo evaluaciones de indicadores de características desde la caché local.

## SDK disponibles {#available-sdks}

### SDK web de AEP {#web-sdk}

La extensión Flags para la web se integra con Adobe Experience Platform Web SDK, lo que permite la evaluación de indicadores en aplicaciones web.

### Extensión de Android {#android-extension}

La extensión Flags para Android se integra con Adobe Experience Platform Mobile SDK.

Consulte la [guía de integración de extensiones de Android](../sdk-releases/android/android-extension-integration-guide.md) para obtener instrucciones de configuración.

### Extensión de iOS {#ios-extension}

La extensión Flags para iOS se integra con Adobe Experience Platform Mobile SDK.

Consulte la [guía de integración de extensiones de iOS](../sdk-releases/ios/ios-extension-integration-guide.md) para obtener instrucciones de configuración.

## Consulte también {#see-also}

* [Guía de integración de Android extension](../sdk-releases/android/android-extension-integration-guide.md)
* [Servicios web](web-services.md)
* [Pasos de integración](integration-steps.md)

<!-- -->
