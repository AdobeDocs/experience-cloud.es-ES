---
title: Suscripción a la aplicación API en Adobe Developer Console
description: Obtenga información sobre cómo suscribir su aplicación a la API de despliegues de experiencias a través de Adobe Developer Console para que pueda llamar a los extremos de los indicadores de funcionalidades.
source-git-commit: 120a2ea34682c878aaf6f6cb75504a8704d10e3d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 3%

---


# Suscripción a la aplicación API en Adobe Developer Console {#subscribe-to-api}

Para llamar a la API de despliegues de experiencia desde tu aplicación, debes suscribirte a ella a través de [Adobe Developer Console](https://developer.adobe.com/console). Esto proporciona a la aplicación un ID de cliente que los despliegues de experiencia utilizan para identificar al que llama.

## Requisitos previos {#prerequisites}

Antes de suscribirse, confirme lo siguiente:

* Su aplicación está integrada en la consola Despliegues de experiencias. Consulte [Incorporar su aplicación](../applications/onboard-your-application.md)
* Tiene acceso a Adobe Developer Console para su organización

## Suscripción a la API de despliegues de experiencias {#subscribe}

Para suscribir su aplicación a la API de despliegues de experiencias, siga estos pasos:

1. Vaya a [Adobe Developer Console](https://developer.adobe.com/console) e inicie sesión con sus credenciales de organización.
2. Seleccione el proyecto o cree uno nuevo.
3. Seleccione **Agregar API**.
4. Busque y seleccione **API de despliegues de experiencias**.
5. Siga las indicaciones para configurar la API y generar credenciales.
6. Tenga en cuenta la **ID de cliente** generada para su proyecto. Este es el identificador que utiliza al llamar a la API de despliegues de experiencia y al incorporar la aplicación en la consola de despliegues de experiencia.

## Integraciones de SDK del lado del servidor {#server-sdk}

Si está realizando la integración con Java SDK o Node.js SDK, necesita un **token de servicio** ID de cliente además de una clave de API. El token de servicio permite que SDK llame a las API de despliegue de experiencia en segundo plano.

>[!NOTE]
>
>Los ID de cliente de SDK del lado del servidor deben estar incluidos en la lista de permitidos por la compatibilidad con los despliegues de experiencia para poder realizar llamadas de API. Póngase en contacto con el servicio de asistencia después de completar la configuración de Developer Console.

## Consulte también {#see-also}

* [Guía de inicio](startup-guide.md)
* [SDK](sdks.md)
* [Incorporar la aplicación](../applications/onboard-your-application.md)
* [Pasos de integración](integration-steps.md)
