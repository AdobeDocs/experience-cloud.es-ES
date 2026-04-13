---
title: Guía de integración de la extensión de Experience Rollout para iOS
description: Obtenga información sobre cómo integrar la extensión de despliegue de experiencias con Adobe Experience Platform Mobile SDK en iOS.
source-git-commit: a9f6746c2b470377d2fd58de18e984d1ec404a77
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 7%

---

# Extensión de despliegue de experiencias para iOS {#ios-extension-integration-guide}

En esta guía se describe cómo integrar la extensión de despliegue de Experience Cloud con Adobe Experience Platform Mobile SDK en iOS.

## Requisitos previos {#prerequisites}

Antes de implementar la extensión de despliegue de experiencia, asegúrese de lo siguiente:

* Una propiedad móvil configurada en [Recopilación de datos de Adobe Experience Platform](https://experience.adobe.com/#/data-collection)
* La extensión de despliegue de Experience instalada y configurada en su propiedad móvil
* Un ID de organización de Adobe Experience Cloud
* Destino mínimo de implementación: iOS 12.0
* Xcode 14.1 o posterior

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
1. Siga el [proceso de publicación](https://experienceleague.adobe.com/es/docs/experience-platform/tags/publish/overview) para actualizar la configuración.

### Obtener el ID del archivo de entorno {#environment-file-id}

1. En su propiedad móvil, vaya a **Entornos**.
1. Seleccione el icono de cuadro debajo de la columna **Instalar** para su entorno.
1. En el cuadro de diálogo **Instrucciones de instalación de Mobile**, copie el **Id. de archivo de entorno**.

## Añadir la extensión de Experience Rollout a la aplicación. {#add-to-app}

### Añadir dependencias {#add-dependencies}

Agregue las dependencias de Mobile SDK al proyecto. La extensión de despliegue de experiencias requiere Mobile Core y las extensiones relacionadas con Edge que se enumeran a continuación.

#### Uso Del Administrador De Paquetes Swift (Recomendado) {#swift-package-manager}

1. En Xcode, vaya a **Archivo** > **Agregar dependencias del paquete**.
1. Introduzca la URL del repositorio de Adobe Experience Platform Mobile SDK:

   ```
   https://github.com/adobe/aepsdk-core-ios
   ```

1. Añada los siguientes paquetes:

   | Paquete | Repositorio |
   |---|---|
   | AEPCore, AEPLilifecycle | `https://github.com/adobe/aepsdk-core-ios` |
   | AEPEdge | `https://github.com/adobe/aepsdk-edge-ios` |
   | AEPdgeIdentity | `https://github.com/adobe/aepsdk-edgeidentity-ios` |
   | AEPRollout | `https://github.com/adobe/aepsdk-rollout-ios` |

#### Uso de CocoaPods {#cocoapods}

Agregue los siguientes pods a su `Podfile`:

```ruby
pod 'AEPCore'
pod 'AEPLifecycle'
pod 'AEPEdge'
pod 'AEPEdgeIdentity'
pod 'AEPRollout'
```

A continuación, ejecute:

```bash
pod install
```

>[!IMPORTANT]
>
>Para aplicaciones de producción, Adobe recomienda anclar a números de versión explícitos en lugar de utilizar `~>` o intervalos abiertos. Consulte la [Guía de versiones de CocoaPods](https://guides.cocoapods.org/using/the-podfile.html) para obtener más información.

### Inicialización de SDK {#initialize-sdk}

Inicialice Mobile SDK en `AppDelegate` (o `SceneDelegate`) antes de llamar a cualquier API de extensión de despliegue de experiencia. Utilice el ID del archivo de entorno de su propiedad móvil para que la aplicación recoja la configuración de despliegue publicada en la recopilación de datos.

**Swift**

```swift
import AEPCore
import AEPLifecycle
import AEPEdge
import AEPEdgeIdentity
import AEPRollout

@main
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(
        _ application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?
    ) -> Bool {

        MobileCore.setLogLevel(.error)

        MobileCore.registerExtensions(
            [Lifecycle.self, Edge.self, Identity.self, Rollout.self]
        ) {
            // Initialize with your Environment File ID from Data Collection
            MobileCore.configureWith(appId: "YOUR_ENVIRONMENT_FILE_ID")
        }

        return true
    }
}
```

**Objective-C**

```objc
@import AEPCore;
@import AEPLifecycle;
@import AEPEdge;
@import AEPEdgeIdentity;
@import AEPRollout;

@implementation AppDelegate

- (BOOL)application:(UIApplication *)application
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {

    [AEPMobileCore setLogLevel:AEPLogLevelError];

    NSArray *extensions = @[
        AEPMobileLifecycle.class,
        AEPMobileEdge.class,
        AEPMobileEdgeIdentity.class,
        AEPMobileRollout.class
    ];

    [AEPMobileCore registerExtensions:extensions completion:^{
        // Initialize with your Environment File ID from Data Collection
        [AEPMobileCore configureWithAppId:@"YOUR_ENVIRONMENT_FILE_ID"];
    }];

    return YES;
}

@end
```

>[!IMPORTANT]
>
>Para aplicaciones de producción, use `LogLevel.error` solamente. No use `.debug` ni `.verbose` en las compilaciones de versión.

## Contexto de evaluación {#evaluation-context}

`FeatureEvaluationContext` incluye atributos de segmentación (utilizados para la coincidencia de reglas de despliegue) e identidad opcional (utilizados para análisis).

| Método | Requerido | Descripción |
|---|---|---|
| `withIdentity(namespace:id:)` | No | Primer argumento: área de nombres de identidad (consulte [Áreas de nombres de identidad de Adobe](https://experienceleague.adobe.com/es/docs/experience-platform/identity/features/namespaces)). Segundo argumento: valor de identidad. Incluya esto cuando desee que el área de nombres y el ID se representen en Analytics para esta evaluación. Si no se proporciona, Analytics utiliza ECID de forma predeterminada. No se usa para tomar decisiones de habilitación de características. |
| `withAttributes(_:)` | No | `[String: [String]]`. Clave es el nombre de atributo de contexto utilizado por las reglas de despliegue (por ejemplo `locale`, `platform`, `appVersion`, `deviceType`). Value es la lista de valores de atributos candidatos para esa clave para el usuario o la sesión actual (por ejemplo `["en_US"]` o `["phone"]`). |

**Swift**

```swift
import AEPRollout

let attrs: [String: [String]] = [
    "locale": ["en_US"],
    "platform": ["IOS"],
    "appVersion": ["3.0.0"]
]

let ctx = FeatureEvaluationContext.builder()
    .withIdentity(namespace: "Email", id: "customer@example.com")
    .withAttributes(attrs)
    .build()
```

**Objective-C**

```objc
@import AEPRollout;

NSDictionary<NSString *, NSArray<NSString *> *> *attrs = @{
    @"locale": @[@"en_US"],
    @"platform": @[@"IOS"],
    @"appVersion": @[@"3.0.0"]
};

AEPFeatureEvaluationContext *ctx = [[[AEPFeatureEvaluationContextBuilder builder]
    withIdentityNamespace:@"Email" id:@"customer@example.com"]
    withAttributes:attrs]
    .build;
```

### Atributos de segmentación de muestra {#sample-attributes}

| Atributo | Descripción | Valores de ejemplo |
|---|---|---|
| `locale` | Configuración regional/idioma del usuario | `["en_US"]`, `["fr_FR"]` |
| `platform` | Identificador de plataforma | `["IOS"]` |
| `appVersion` | Versión de aplicación | `["3.0.0"]` |
| `deviceType` | Tipo de dispositivo | `["phone"]`, `["tablet"]` |

## Referencia de la API {#api-reference}

### isFeatureEnabled {#is-feature-enabled}

`isFeatureEnabled` devuelve si una característica de despliegue de experiencia está activada o desactivada en el contexto determinado. Pase `featureKey`, un `FeatureEvaluationContext` (atributos de segmentación opcionales e identidad opcional para Analytics) y un controlador de finalización. Consulte [Contexto de evaluación](#evaluation-context).

**Firma**

*Swift*

```swift
Rollout.isFeatureEnabled(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    completion: @escaping (Bool) -> Void
)
```

*Objective-C*

```objc
[AEPMobileRollout isFeatureEnabled:(NSString *)featureKey
               evaluationContext:(AEPFeatureEvaluationContext *)evaluationContext
                      completion:(void (^)(BOOL))completion];
```

**Parámetros**

| Parámetro | Tipo | Descripción |
|---|---|---|
| `featureKey` | Cadena | Clave de función a evaluar en el despliegue de experiencias |
| `evaluationContext` | FeatureEvaluationContext | Incluya atributos de segmentación e identidad opcional para Analytics según sea necesario; use `FeatureEvaluationContext.builder().build()` para un contexto vacío. Consulte [Contexto de evaluación](#evaluation-context). |
| `completion` | `(Bool) -> Void` | Se llama con `true` si la característica está habilitada, `false` en caso contrario. |

**Ejemplos**

*Swift*

```swift
import AEPRollout

Rollout.isFeatureEnabled(
    featureKey: "new-checkout-experience",
    evaluationContext: ctx
) { isEnabled in
    if isEnabled {
        showNewCheckout()
    } else {
        showDefaultCheckout()
    }
}
```

*Objective-C*

```objc
@import AEPRollout;

[AEPMobileRollout isFeatureEnabled:@"new-checkout-experience"
               evaluationContext:ctx
                      completion:^(BOOL isEnabled) {
    if (isEnabled) {
        [self showNewCheckout];
    } else {
        [self showDefaultCheckout];
    }
}];
```

### getFeature {#get-feature}

`getFeature` devuelve la carga útil de la característica evaluada para el contexto proporcionado. Utilice esta API cuando necesite más de habilitar/deshabilitar y desee metadatos o valores de características.

**Firma**

*Swift*

```swift
Rollout.getFeature(
    featureKey: String,
    evaluationContext: FeatureEvaluationContext,
    completion: @escaping (FeatureEvaluationResult?) -> Void
)
```

*Objective-C*

```objc
[AEPMobileRollout getFeature:(NSString *)featureKey
         evaluationContext:(AEPFeatureEvaluationContext *)evaluationContext
                completion:(void (^)(AEPFeatureEvaluationResult * _Nullable))completion];
```

**Parámetros**

| Parámetro | Tipo | Descripción |
|---|---|---|
| `featureKey` | Cadena | Clave de función a evaluar en el despliegue de experiencias |
| `evaluationContext` | FeatureEvaluationContext | Incluya atributos de segmentación e identidad opcional para Analytics según sea necesario; use `FeatureEvaluationContext.builder().build()` para un contexto vacío. Consulte [Contexto de evaluación](#evaluation-context). |
| `completion` | `(FeatureEvaluationResult?) -> Void` | Se llama con la carga útil de la característica evaluada; puede ser `nil` cuando no se encuentra la característica. |

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

*Swift*

```swift
import AEPRollout

Rollout.getFeature(
    featureKey: "new-checkout-experience",
    evaluationContext: ctx
) { feature in
    if let meta = feature?.meta, !meta.isEmpty {
        applyMetaDrivenExperience(meta)
    } else {
        showFallbackExperience()
    }
}
```

*Objective-C*

```objc
@import AEPRollout;

[AEPMobileRollout getFeature:@"new-checkout-experience"
         evaluationContext:ctx
                completion:^(AEPFeatureEvaluationResult * _Nullable feature) {
    NSString *meta = feature.meta;
    if (meta != nil && meta.length > 0) {
        [self applyMetaDrivenExperience:meta];
    } else {
        [self showFallbackExperience];
    }
}];
```

### refreshCache {#refresh-cache}

De forma predeterminada, la extensión de despliegue de Experience sincroniza regularmente las reglas y funciones de despliegue más recientes del servidor según una programación que puede configurar. Si necesita una actualización antes de la siguiente sincronización programada, llame a `refreshCache` para forzar una actualización. Los casos habituales incluyen después del inicio de sesión o cuando el estado de la aplicación cambia de una manera que debería afectar a la segmentación.

**Sintaxis**

*Swift*

```swift
Rollout.refreshCache()
```

*Objective-C*

```objc
[AEPMobileRollout refreshCache];
```

### extensionVersion {#extension-version}

Devuelve la cadena de versión de la extensión de despliegue de experiencia.

**Sintaxis**

```swift
Rollout.extensionVersion(): String
```

**Ejemplo**

*Swift*

```swift
let version = Rollout.extensionVersion()
```

*Objective-C*

```objc
NSString *version = [AEPMobileRollout extensionVersion];
```

## Resumen de API {#api-summary}

| API | Devuelve |
|---|---|
| `isFeatureEnabled(featureKey:evaluationContext:completion:)`. `FeatureEvaluationContext` lleva atributos de segmentación para reglas e identidad opcional para analytics. Consulte [isFeatureEnabled](#is-feature-enabled). | Booleano mediante controlador de finalización |
| `getFeature(featureKey:evaluationContext:completion:)`. Devuelve la carga útil de la función evaluada para el contexto determinado. Ver [getFeature](#get-feature). | ¿FeatureEvaluationResult? mediante controlador de finalización |
| `refreshCache()` | Anular |
| `extensionVersion()` | Cadena |

## Consulte también {#see-also}

* [Aplicaciones móviles](../../integrate/mobile-applications.md)
* [Pasos de integración](../../integrate/integration-steps.md)
* [SDK](../../integrate/sdks.md)
* [Guía de integración de Android extension](../android/android-extension-integration-guide.md)
