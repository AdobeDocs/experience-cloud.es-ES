---
title: Guía de integración de Java SDK
description: Obtenga información sobre cómo integrar los lanzamientos de experiencias de Java SDK en su servicio back-end para recuperar y evaluar indicadores de funcionalidades.
exl-id: 7c12bd6c-1883-4f1c-985f-a2b0432e61ce
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# Guía de integración de Java SDK {#java-sdk-integration-guide}

Experience Rollouts Java SDK es una biblioteca del lado del servidor que almacena en caché localmente los datos de indicadores de funcionalidades y evalúa los indicadores sin una llamada sincrónica de API en cada solicitud. Esta guía describe el SDK actual (4.x).

## Requisitos previos {#prerequisites}

Antes de integrar Java SDK, asegúrese de lo siguiente:

* JDK 11 o posterior (requerido a partir de la versión 3.0.0 de SDK; las versiones anteriores admiten JDK 8+)
* Un sistema de compilación basado en Maven
* Una **clave de API** y un **token de servicio** ID de cliente de su proyecto de Adobe Developer Console. Póngase en contacto con el servicio de asistencia técnica de los lanzamientos de experiencias para que se incluida en la lista de permitidos su ID de cliente.
* Sus **ID de cliente de aplicaciones** se registraron en la consola de despliegues de experiencias; consulte [Incorporar su aplicación](../../applications/onboard-your-application.md)

## Agregar la dependencia de Maven {#maven-dependency}

Agregue el SDK Java de despliegues de experiencias a `pom.xml` de su proyecto:

```xml
<dependency>
  <groupId>com.adobe.cloudtech</groupId>
  <artifactId>fg-client-sdk</artifactId>
  <version>4.0.6</version>
</dependency>
```

## Inicialización de SDK {#initialize}

SDK se inicializa una vez al inicio de la aplicación con `FloodgateClient.createInstance()`. El método toma un objeto `FloodgateConfiguration` que se creó con el generador de configuración.

### Implementación de la llamada de retorno del token de servicio {#service-token-callback}

SDK utiliza una interfaz de llamada de retorno para recuperar un token de servicio nuevo durante la ejecución:

```java
private class FgConfigCallBack implements FGConfigBaseCallBack {

  @Override
  public String getIMSServiceToken() {
    // Fetch and return a valid service token
  }

  @Override
  public boolean isAnalyticsEnabled() {
    return false; // Set to true to enable analytics
  }
}
```

### Creación del objeto de configuración {#configuration}

Utilice el generador de configuración para configurar SDK:

```java
FloodgateConfiguration configuration = FloodgateConfiguration.FloodgateConfigurationBuilder
    .aFloodgateConfiguration(
        FgEnv.PRD,                   // Use FgEnv.STG for Stage
        "<YOUR_API_KEY>",
        Set.of("<CLIENT_ID_1>", "<CLIENT_ID_2>"),
        new FgConfigCallBack(),
        CallType.ASYNC
    )
    .withRetryPolicy(retryPolicy)    // Optional: defaults to 5 retries, 10s interval
    .build();
```

Use `FgEnv.STG` para el entorno de ensayo y `FgEnv.PRD` para la producción.

### Creación de la instancia de cliente {#client-instance}

```java
FloodgateClient fgClient = FloodgateClient.createInstance(configuration);
```

## Recuperar indicadores de funcionalidad {#retrieve-features}

### Usuario autenticado {#authenticated-user}

Utilice un token de acceso de IMS para recuperar los indicadores de funcionalidad del usuario actual:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<USER_ACCESS_TOKEN>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Usuario anónimo {#anonymous-user}

Para los usuarios no autenticados, pase un ID de visitante y su token de servicio:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withServiceToken("<SERVICE_TOKEN>")
    .withVisitorId("<VISITOR_ID>")
    .withContext(context)
    .build();

FeaturesResponse[] features = fgClient.getFeatures(request);
```

### Recuperar una marca o versión de función específica {#specific-feature}

Para recuperar un solo indicador de funcionalidad mediante clave:

```java
GetFeatureRequest request = GetFeatureRequestBuilder
    .aGetFeatureRequest("<CLIENT_ID>")
    .withAccessToken("<ACCESS_TOKEN>")
    .withFeatureKey("<FEATURE_KEY>")
    .build();
```

Para recuperar mediante clave de versión, reemplace `.withFeatureKey()` por `.withReleaseKey()`.

## Comprobar si una función está habilitada {#check-feature}

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_FEATURE_FLAG");

if (isEnabled) {
  // Serve the new experience
} else {
  // Serve the default experience
}
```

Para comprobaciones basadas en versiones:

```java
boolean isEnabled = FloodgateClient.isFeatureEnabled(features, "MY_RELEASE", "MY_FEATURE_FLAG");
```

## Administración de caché {#cache-management}

SDK almacena en caché los datos de indicadores de funcionalidades y los actualiza en un intervalo de sondeo establecido por cada aplicación en la consola. Para almacenar en déclencheur una actualización de caché bajo demanda:

```java
fgClient.refreshClientCache("<CLIENT_ID>");
```

### Clientes no almacenables en caché {#non-cacheable}

Para los clientes que no se pueden almacenar en caché, `getFeature()` realiza una llamada de API activa cada vez. SDK continúa con las encuestas en segundo plano y cambia al servicio basado en caché cuando el cliente se puede almacenar en caché. Compatible a partir de la versión 0.8 de SDK.

## Opciones de configuración {#configuration-options}

Los siguientes métodos de configuración opcionales están disponibles en el generador:

| Opción | Método | Descripción |
|---|---|---|
| Usar siempre la caché | `.alwaysCache()` | Omite la respuesta de almacenamiento en caché de la API; se utiliza para indicadores sin reglas de audiencia |
| Deshabilitar almacenamiento en caché | `.neverCache()` | Deshabilita el almacenamiento en caché predeterminado; útil para la lógica de actualización de caché personalizada |
| Cliente HTTP personalizado | `.withHttpClient(client)` | Usar su propio cliente HTTP |
| Ejecutor personalizado | `.withScheduledExecutorService(executor)` | Utilizar su propio ejecutor programado para el sondeo en segundo plano |
| Incluir grupo de control | `.includeControlGroup()` | Devuelve datos de grupos de control en la respuesta de la función |

## Gestión de errores {#error-handling}

Agrupar `getFeatures()` llamadas para detectar excepciones de SDK:

```java
try {
  features = fgClient.getFeatures(request);
} catch (FgClientException e) {
  int statusCode = e.getStatusCode();
  // Handle error and serve default experience
} catch (FgInitException e) {
  e.printStackTrace();
}
```

## Consulte también {#see-also}

* [Notas de la versión de Java SDK](java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
* [Pasos de integración](../../integrate/integration-steps.md)
