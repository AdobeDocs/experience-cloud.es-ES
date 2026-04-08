---
title: Guía de integración de la extensión de Experience Rollout para Android
description: Obtenga información sobre cómo integrar la extensión de despliegue de experiencias con Adobe Experience Platform Mobile SDK en Android.
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '934'
ht-degree: 7%

---


# Extensión de despliegue de experiencias para Android {#android-extension-integration-guide}

En esta guía se describe cómo integrar la extensión de despliegue de Experience Cloud con Adobe Experience Platform Mobile SDK en Android.

## Requisitos previos {#prerequisites}

Antes de implementar la extensión de despliegue de experiencia, asegúrese de lo siguiente:

* Una propiedad móvil configurada en [Recopilación de datos de Adobe Experience Platform](https://experience.adobe.com/#/data-collection)
* La extensión de despliegue de Experience instalada y configurada en su propiedad móvil
* Un ID de organización de Adobe Experience Cloud
* SDK mínimo: API 21 (Android 5.0 Lollipop)

## Dependencias de extensión {#extension-dependencies}

La extensión de despliegue de experiencia requiere las siguientes extensiones de Adobe Experience Platform:

| Extensión | Descripción | Requerido |
|---|---|---|
| Mobile Core | Proporciona funcionalidad principal, incluida la configuración y el procesamiento de eventos | Sí |
| Ciclo de vida | Recopila datos sobre el ciclo vital y la sesión de la aplicación para Mobile SDK | Sí |
| Edge Network | Habilita la comunicación con Adobe Experience Platform Edge Network | Sí |
| Edge Identity | Administra la identidad del usuario para Edge Network | Sí |

Asegúrese de que estas extensiones estén instaladas en la propiedad móvil de recopilación de datos y se incluyan en las dependencias de la aplicación.

## Configuración de la extensión de despliegue de experiencia en la recopilación de datos {#configure}

### Instalación de la extensión {#install-extension}

1. Inicie sesión en [Adobe Experience Platform Data Collection](https://experience.adobe.com/#/data-collection).
1. Seleccione la ficha **Etiquetas** y elija su propiedad móvil.
1. Vaya a **Extensiones** > **Catálogo**.
1. Busque **Extensión de despliegue de experiencia** y seleccione **Instalar**.
1. Configure las opciones de extensión:

   | Configuración | Descripción |
   |---|---|
   | Zona protegida | La zona protegida de Adobe Experience Platform que contiene la configuración de Despliegue de experiencia |
   | ID de aplicación | Un identificador único para su aplicación en el Despliegue de experiencias |
   | ID de conjunto de datos | ID del conjunto de datos de Adobe Experience Platform para los datos de evento de Analytics |

1. Seleccione **Guardar**.
1. Siga el [proceso de publicación](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/overview) para actualizar la configuración.

### Obtener el ID del archivo de entorno {#environment-file-id}

1. En su propiedad móvil, vaya a **Entornos**.
1. Seleccione el icono de cuadro debajo de la columna **Instalar** para su entorno.
1. En el cuadro de diálogo **Instrucciones de instalación de Mobile**, copie el **Id. de archivo de entorno**.

## Añadir la extensión de Experience Rollout a la aplicación. {#add-to-app}

### Añadir dependencias {#add-dependencies}

Agregue las dependencias de Mobile SDK al proyecto. La extensión de despliegue de experiencias requiere Mobile Core y las extensiones relacionadas con Edge que se enumeran a continuación.

#### Uso de Gradle con BOM (recomendado) {#gradle-bom}

Agregue las siguientes dependencias al archivo `build.gradle.kts` de su aplicación:

```kotlin
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation(platform("com.adobe.marketing.mobile:sdk-bom:3.+"))

    // Required extensions
    implementation("com.adobe.marketing.mobile:core")
    implementation("com.adobe.marketing.mobile:lifecycle")
    implementation("com.adobe.marketing.mobile:edge")
    implementation("com.adobe.marketing.mobile:edgeidentity")

    // Experience Rollout extension
    implementation("com.adobe.marketing.mobile:rollout")
}
```

#### Uso de Gradle (Groovy) {#gradle-groovy}

```groovy
dependencies {
    // Adobe Experience Platform Mobile SDK BOM
    implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')

    // Required extensions
    implementation 'com.adobe.marketing.mobile:core'
    implementation 'com.adobe.marketing.mobile:lifecycle'
    implementation 'com.adobe.marketing.mobile:edge'
    implementation 'com.adobe.marketing.mobile:edgeidentity'

    // Experience Rollout extension
    implementation 'com.adobe.marketing.mobile:rollout'
}
```

>[!IMPORTANT]
>
>Para aplicaciones de producción, Adobe recomienda utilizar números de versión explícitos en lugar de versiones dinámicas. Consulte [Administración de dependencias de Gradle](https://docs.gradle.org/current/userguide/dependency_management.html) para obtener más información.

### Adición de permisos {#add-permissions}

Agregue los siguientes permisos al archivo `AndroidManifest.xml`:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

### Inicialización de SDK {#initialize-sdk}

Inicialice Mobile SDK en la clase `Application` antes de llamar a cualquier API de extensión de despliegue de experiencia. Use el identificador de archivo de entorno de su propiedad móvil con `MobileCore.initialize` para que la aplicación recoja la configuración de despliegue que publicó en la recopilación de datos.

#### Uso de MobileCore.initialize {#mobile-core-initialize}

Esta API, disponible a partir de la versión 3.8.0 de Android BOM, registra automáticamente las extensiones y habilita el seguimiento del ciclo vital.

>[!IMPORTANT]
>
>Para aplicaciones de producción, use `LoggingMode.ERROR` solamente. No use `DEBUG` ni `VERBOSE` en las compilaciones de versión.

**Kotlin**

```kotlin
import android.app.Application
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.MobileCore

class MainApplication : Application() {

    override fun onCreate() {
        super.onCreate()

        MobileCore.setLogLevel(LoggingMode.ERROR)

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID")
    }
}
```

**Java**

```java
import android.app.Application;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;

public class MainApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();

        MobileCore.setLogLevel(LoggingMode.ERROR);

        // Initialize with your Environment File ID from Data Collection
        MobileCore.initialize(this, "YOUR_ENVIRONMENT_FILE_ID", null);
    }
}
```

### Registrar la clase Application {#register-application}

Registre su clase `Application` en `AndroidManifest.xml`:

```xml
<application
    android:name=".MainApplication"
    ... >
</application>
```

## Contexto de evaluación {#evaluation-context}

`FeatureEvaluationContext` incluye atributos de segmentación (utilizados para la coincidencia de reglas de despliegue) e identidad opcional (utilizados para análisis).

| Método | Requerido | Descripción |
|---|---|---|
| `withIdentity(namespace, id)` | No | Primer argumento: área de nombres de identidad (consulte [Áreas de nombres de identidad de Adobe](https://experienceleague.adobe.com/es/docs/experience-platform/identity/features/namespaces)). Segundo argumento: valor de identidad. Incluya esto cuando desee que el área de nombres y el ID se representen en Analytics para esta evaluación. Si no se proporciona, Analytics utiliza ECID de forma predeterminada. No se usa para tomar decisiones de habilitación de características. |
| `withAttributes(map)` | No | `Map<String, List<String>>`. Clave es el nombre de atributo de contexto utilizado por las reglas de despliegue (por ejemplo `locale`, `platform`, `appVersion`, `deviceType`). Value es la lista de valores de atributos candidatos para esa clave para el usuario o la sesión actual (por ejemplo `["en_US"]` o `["phone"]`). |

**Kotlin**

```kotlin
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext

val attrs = mapOf(
    "locale" to listOf("en_US"),
    "platform" to listOf("ANDROID"),
    "appVersion" to listOf("3.0.0")
)

val ctx = FeatureEvaluationContext.builder()
    .withIdentity("Email", "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Java**

```java
import com.adobe.marketing.mobile.rollout.FeatureEvaluationContext;
import java.util.Arrays;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

Map<String, List<String>> attrs = new HashMap<>();
attrs.put("locale", Arrays.asList("en_US"));
attrs.put("platform", Arrays.asList("ANDROID"));
attrs.put("appVersion", Arrays.asList("3.0.0"));

FeatureEvaluationContext ctx = FeatureEvaluationContext.builder()
        .withIdentity("Email", "customer@example.com")
        .withAttributes(attrs)
        .build();
```

### Atributos de segmentación de muestra {#sample-attributes}

| Atributo | Descripción | Valores de ejemplo |
|---|---|---|
| `locale` | Configuración regional/idioma del usuario | `["en_US"]`, `["fr_FR"]` |
| `platform` | Identificador de plataforma | `["ANDROID"]` |
| `appVersion` | Versión de aplicación | `["3.0.0"]` |
| `deviceType` | Tipo de dispositivo | `["phone"]`, `["tablet"]` |

## Referencia de la API {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` devuelve si una característica de despliegue de experiencia está activada o desactivada en el contexto determinado. Pase `featureKey`, un `FeatureEvaluationContext` (atributos de segmentación opcionales e identidad opcional para Analytics) y una llamada de retorno. Consulte [Contexto de evaluación](#evaluation-context).

**Firma**

*Kotlin*

```kotlin
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<Boolean>
)
```

*Java*

```java
Rollout.isFeatureEnabled(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<Boolean> callback);
```

**Parámetros**

| Parámetro | Tipo | Descripción |
|---|---|---|
| `featureKey` | Cadena | Clave de función a evaluar en el despliegue de experiencias |
| `evaluationContext` | FeatureEvaluationContext | Incluya atributos de segmentación e identidad opcional para Analytics según sea necesario; use `FeatureEvaluationContext.builder().build()` para un contexto vacío. Consulte [Contexto de evaluación](#evaluation-context). |
| `callback` | AdobeCallback&lt;Boolean> | Se invocó con `true` si la característica está habilitada; de lo contrario, `false`. También puede pasar `AdobeCallbackWithError<Boolean>` al identificador `fail(...)`. |

**Ejemplos**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<Boolean> {
        override fun call(isEnabled: Boolean?) {
            if (isEnabled == true) {
                showNewCheckout()
            } else {
                showDefaultCheckout()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.isFeatureEnabled(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<Boolean>() {
        @Override
        public void call(Boolean isEnabled) {
            if (Boolean.TRUE.equals(isEnabled)) {
                showNewCheckout();
            } else {
                showDefaultCheckout();
            }
        }
    }
);
```

### getFeature {#get-feature}

`getFeature` devuelve la carga útil de la característica evaluada para el contexto proporcionado. Utilice esta API cuando necesite más de habilitar/deshabilitar y desee metadatos o valores de características.

**Firma**

*Kotlin*

```kotlin
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    callback: AdobeCallback<FeatureEvaluationResult>
)
```

*Java*

```java
Rollout.getFeature(
    String featureKey,
    FeatureEvaluationContext evaluationContext,
    AdobeCallback<FeatureEvaluationResult> callback);
```

**Parámetros**

| Parámetro | Tipo | Descripción |
|---|---|---|
| `featureKey` | Cadena | Clave de función a evaluar en el despliegue de experiencias |
| `evaluationContext` | FeatureEvaluationContext | Incluya atributos de segmentación e identidad opcional para Analytics según sea necesario; use `FeatureEvaluationContext.builder().build()` para un contexto vacío. Consulte [Contexto de evaluación](#evaluation-context). |
| `callback` | AdobeCallback&lt;FeatureEvaluationResult> | Se invocó con la carga útil de la característica evaluada; puede ser `null` cuando no se encuentra la característica. También puede pasar `AdobeCallbackWithError<FeatureEvaluationResult>` al identificador `fail(...)`. |

**Respuesta**

*FeatureEvaluationResult*

| Campo | Tipo | Descripción |
|---|---|---|
| `id` | Int | Identificador de función numérica |
| `key` | Cadena | Tecla de función |
| `releaseKey` | ¿String? | Liberar la clave para esta función cuando esté disponible |
| `meta` | ¿String? | Los metadatos de la función como una cadena JSON cuando están disponibles |
| `analyticsParam` | ¿AnalyticsParam? | Detalles de Analytics para la función evaluada |

*Parámetro de análisis*

| Campo | Tipo | Descripción |
|---|---|---|
| `releaseId` | Int | Identificador numérico de la versión |
| `featureId` | Int | Identificador de función numérica |
| `variantId` | ¿String? | Identificador de variante |

**Ejemplos**

*Kotlin*

```kotlin
import com.adobe.marketing.mobile.AdobeCallback
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult
import com.adobe.marketing.mobile.rollout.Rollout

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    object : AdobeCallback<FeatureEvaluationResult> {
        override fun call(feature: FeatureEvaluationResult?) {
            val meta = feature?.meta
            if (!meta.isNullOrEmpty()) {
                applyMetaDrivenExperience(meta)
            } else {
                showFallbackExperience()
            }
        }
    }
)
```

*Java*

```java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.rollout.FeatureEvaluationResult;
import com.adobe.marketing.mobile.rollout.Rollout;

Rollout.getFeature(
    "new-checkout-experience",
    ctx,
    new AdobeCallback<FeatureEvaluationResult>() {
        @Override
        public void call(FeatureEvaluationResult feature) {
            String meta = feature != null ? feature.getMeta() : null;
            if (meta != null && !meta.isEmpty()) {
                applyMetaDrivenExperience(meta);
            } else {
                showFallbackExperience();
            }
        }
    }
);
```

### refreshCache {#refresh-cache}

De forma predeterminada, la extensión de despliegue de Experience sincroniza regularmente las reglas y funciones de despliegue más recientes del servidor según una programación que puede configurar. Si necesita una actualización antes de la siguiente sincronización programada, llame a `refreshCache` para forzar una actualización. Los casos habituales incluyen después del inicio de sesión o cuando el estado de la aplicación cambia de una manera que debería afectar a la segmentación.

**Sintaxis**

*Kotlin*

```kotlin
Rollout.refreshCache()
```

*Java*

```java
Rollout.refreshCache();
```

### extensionVersion {#extension-version}

Devuelve la cadena de versión de la extensión de despliegue de experiencia.

**Sintaxis**

```kotlin
Rollout.extensionVersion(): String
```

**Ejemplo**

*Kotlin*

```kotlin
val version = Rollout.extensionVersion()
```

*Java*

```java
String version = Rollout.extensionVersion();
```

## Resumen de API {#api-summary}

| API | Devuelve |
|---|---|
| `isFeatureEnabled(featureKey, evaluationContext, callback)`. `FeatureEvaluationContext` lleva atributos de segmentación para reglas e identidad opcional para analytics. Consulte [Evaluación de características](#is-feature-enabled). | Booleano mediante llamada de retorno |
| `getFeature(featureKey, evaluationContext, callback)`. Devuelve la carga útil de la función evaluada para el contexto determinado. Ver [getFeature](#get-feature). | FeatureEvaluationResult mediante llamada de retorno |
| `refreshCache()` | anular |
| `extensionVersion()` | Cadena |

## Consulte también {#see-also}

* [Aplicaciones móviles](../../integrate/mobile-applications.md)
* [Pasos de integración](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
