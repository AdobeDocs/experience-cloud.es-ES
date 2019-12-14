---
title: Implementación del servicio de identidad de Adobe Experience Platform con Launch
description: Obtenga información sobre cómo agregar la extensión del servicio de identidad de Adobe Experience Platform y utilizar la acción Definir ID de cliente para recopilar ID de cliente. Esta lección forma parte del tutorial Implementación de Experience Cloud en aplicaciones móviles Android.
seo-description: null
seo-title: Implementación del servicio de identidad de Adobe Experience Platform con Launch
solution: Experience Cloud
translation-type: tm+mt
source-git-commit: e9dee6d0aa3b775d0ce617e2b2c57b56de491b8d

---


# Agregar el servicio de identidad de Adobe Experience Platform

El servicio [de identidad de](https://docs.adobe.com/content/help/en/id-service/using/home.html) Adobe Experience Platform establece un ID de visitante común en todas las soluciones de Adobe para potenciar las funciones de Experience Cloud, como el uso compartido de público entre soluciones.  También puede enviar sus propios ID de cliente al Servicio para habilitar la segmentación entre dispositivos y las integraciones con su sistema de administración de la relación con los clientes (CRM).

El servicio de identidad forma parte de la extensión Mobile Core, ***por lo que ya lo ha implementado al instalar el SDK*** de Mobile. En este momento, este tutorial no incluye instrucciones para configurar los ID de cliente. Consulte la documentación para obtener detalles sobre [cómo configurar los ID de cliente](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/identity/identity-api-reference).

## Pasos de validación

Para validar las llamadas al servicio de identidad, ejecute la aplicación de ejemplo en Android Studio, abra la consola de depuración y busque la solicitud y la respuesta:

1. **Solicitud al servicio** de identidad (filtrar Logcat a `IdentityExtension`) En este ejemplo, el ID (`d_mid`)ya se ha establecido y se vuelve a registrar)

   ```java
   03-14 17:01:18.526 7743-7803/com.adobe.busbooking D/ADBMobile: IdentityExtension - Sending request (https://dpm.demdex.net/id?d_mid=59651426340521082405908216148091920022&d_ver=2&d_orgid=7ABB3E6A5A7491460A495D61%40AdobeOrg)
   ```

1. **Respuesta del servicio** de identidad (filtrar Logcat a `IdentityExtension`). Observe cómo el `mid` valor coincide con el `d_mid` de la solicitud anterior:

   ```java
   03-14 17:01:19.033 7743-7803/com.adobe.busbooking D/ADBMobile: IdentityExtension - Received ID response (mid: 59651426340521082405908216148091920022, blob: j8Odv6LonN4r3an7LhD3WZrU1bUpAkFkkiY1ncBR96t2PTI, hint: 9, ttl: 604800
   ```

[Siguiente "Agregar compatibilidad con VEC de Adobe Target" &gt;](target-vec.md)
