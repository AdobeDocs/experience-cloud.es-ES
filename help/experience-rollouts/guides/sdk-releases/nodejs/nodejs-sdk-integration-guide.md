---
title: Guía de integración de SDK de Node.js
description: Obtenga información sobre cómo integrar los despliegues de experiencia de SDK de Node.js en su servicio back-end para recuperar y evaluar indicadores de funcionalidades.
exl-id: 063829fe-6933-45ff-add4-285ca7391778
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 1%

---

# Guía de integración de SDK de Node.js {#nodejs-sdk-integration-guide}

La biblioteca de despliegues de experiencia Node.js de SDK es una biblioteca del lado del servidor destinada a los servicios de Node.js. Almacena en caché los datos de indicadores de funcionalidades localmente y evalúa los indicadores sin una llamada API sincrónica en cada solicitud.

>[!NOTE]
>
>El SDK de Node.js está diseñado para utilizarse únicamente en el lado del servidor. Para las aplicaciones web del lado del cliente, utilice el SDK web. La documentación de Web SDK se está preparando actualmente y estará disponible próximamente.

## Requisitos previos {#prerequisites}

Antes de integrar el SDK de Node.js, asegúrese de lo siguiente:

* Una aplicación del lado del servidor de Node.js
* Una **clave de API** y un **token de servicio** obtenidos a través de Adobe Developer Console. Póngase en contacto con el servicio de asistencia técnica de los lanzamientos de experiencias para que se incluida en la lista de permitidos su ID de cliente.
* Sus **ID de cliente de aplicaciones** se registraron en la consola de despliegues de experiencias; consulte [Incorporar su aplicación](../../applications/onboard-your-application.md)

## Instalación de SDK {#install}

Agregue el SDK al `package.json` de su proyecto:

```json
"@floodgate/fg-client-sdk": "~1.0.10"
```

A continuación, pídalo en el código:

```javascript
const { floodgateClient } = require('@floodgate/fg-client-sdk');
```

## Inicialización de SDK {#initialize}

Llamar a `createInstance()` una vez al inicio de la aplicación:

```javascript
floodgateClient.createInstance(
  {
    adobeIoApiKey: "<YOUR_API_KEY>",
    clientIds: ["<CLIENT_ID_1>", "<CLIENT_ID_2>"],
    env: "PRD",    // Use "STG" for Stage
    featureRequestHttpParams: {
      timeout: 60 * 1000  // Optional: request timeout in ms
    },
    ingestAnalyticsHttpParams: {
      timeout: 5 * 1000   // Optional: analytics timeout in ms
    }
  },
  function(cb) {
    // Fetch a fresh service token from IMS and pass it in the callback
    cb(null, SERVICE_TOKEN);
  },
  function() {
    return true;  // Return false to disable analytics
  },
  function(response) {
    // Called when the SDK initializes successfully
    console.log("SDK initialized");
  },
  function(err) {
    // Called if initialization fails
    console.error("SDK init error:", err);
  }
);
```

## Recuperar indicadores de funcionalidad {#retrieve-features}

Los indicadores de características se devuelven de forma asíncrona en una llamada de retorno. Elija el método adecuado en función del contexto de usuario.

### Usuario autenticado {#authenticated-user}

```javascript
floodgateClient.getFeatures(
  {
    userAccessToken: "<USER_ACCESS_TOKEN>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: true
  },
  function(err, features) {
    if (err) {
      // Handle error and serve default experience
      return;
    }
    const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");
    // Serve experience based on isEnabled
  }
);
```

### Usuario anónimo {#anonymous-user}

Cuando no haya ningún token de acceso de usuario disponible, utilice un indicador de versión u omita el token para recibir versiones de despliegue completo:

```javascript
floodgateClient.getFeatures(
  {
    releaseFlag: "<RELEASE_FLAG>",
    visitorId: "<VISITOR_ID>",
    clientId1: "<CLIENT_ID>",
    meta: false
  },
  callback
);
```

### Versiones de despliegue completo predeterminadas {#default-releases}

Cuando no se proporciona ni un token de acceso ni una marca de lanzamiento, SDK devuelve características con el estado **Despliegue completo** o **Línea de base**:

```javascript
floodgateClient.getFeatures(
  {
    clientId1: "<CLIENT_ID>",
    visitorId: "<VISITOR_ID>",
    meta: false
  },
  callback
);
```

## Comprobar si una función está habilitada {#check-feature}

```javascript
const isEnabled = floodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

## Habilitar el registro de depuración {#debug-logging}

Para habilitar los registros detallados de SDK, pase una instancia de registrador de nivel de depuración al llamar a `createInstance()`:

```javascript
const bunyan = require('bunyan');
const logger = bunyan.createLogger({ name: "fg", sourceType: "SDK", level: "debug" });

floodgateClient.createInstance(
  { ..., log: logger },
  ...
);
```

## Consulte también {#see-also}

* [Notas de la versión de SDK de Node.js](nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [Pasos de integración](../../integrate/integration-steps.md)
