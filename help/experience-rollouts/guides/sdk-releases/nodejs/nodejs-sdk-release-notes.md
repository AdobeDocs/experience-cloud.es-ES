---
title: Notas de la versión de SDK de Node.js
description: Notas de la versión de los despliegues de experiencia de Node.js SDK, incluido un registro de cambios de nuevas funciones, mejoras y correcciones de errores en todas las versiones publicadas.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 1%

---


# Notas de la versión de SDK de Node.js {#nodejs-sdk-release-notes}

Esta página enumera el historial de versiones de los despliegues de experiencia de Node.js en SDK. Para configurar la integración, consulte [Guía de integración de SDK de Node.js](nodejs-sdk-integration-guide.md).

## Versión 1.0.10 {#v1-0-10}

**Correcciones de errores y mejoras en el socket**

* Se ha corregido la excepción `ESOCKETTIMEDOUT` que se producía durante las actualizaciones de caché programadas. Se eliminó el parámetro `maxSockets` de `featureRequestHttpParams` y `ingestAnalyticsHttpParams` en `createInstance()`.
* Se corrigió un error en el cual los clientes almacenables en caché se marcaban incorrectamente como no almacenables en caché después de las respuestas HTTP 304 (no modificado).
* Se eliminó `isReleaseBitEnabled()`: ya no se admite este método.
* Se mejoró el resultado de registro para mejores diagnósticos.
* Las carpetas de prueba y cobertura ya no se incluyen en el paquete npm publicado.

## Versión 1.0.5 {#v1-0-5}

**Mejoras de estabilidad**

Correcciones generales para la administración de la actualización de la caché y casos extremos de inicialización de SDK.

## Versión 1.0.3 {#v1-0-3}

**Versión estable inicial**

Primera versión de producción de Node.js SDK que admite la recuperación autenticada, anónima y predeterminada de los indicadores de funciones de despliegue completo.

## Consulte también {#see-also}

* [Guía de integración de SDK de Node.js](nodejs-sdk-integration-guide.md)
* [Notas de la versión de Java SDK](../../sdk-releases/java/java-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
