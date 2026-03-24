---
title: Notas de la versión de Java SDK
description: Notas de la versión de los lanzamientos de Experience Cloud en Java SDK, incluido un registro de cambios de nuevas funciones, mejoras y correcciones de errores en todas las versiones publicadas.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 2%

---


# Notas de la versión de Java SDK {#java-sdk-release-notes}

Esta página enumera el historial de versiones de Experience Rollouts Java SDK. Para configurar la integración, consulte [Guía de integración de Java SDK](java-sdk-integration-guide.md).

## Versión 4.0.6 {#v4-0-6}

**Datos del grupo de control en las respuestas**

Ahora puede recuperar datos de variante y grupo de control en la respuesta de SDK, lo que coincide con el comportamiento de las API de funciones REST. Para habilitar esto, agregue `.includeControlGroup()` a su generador de `FloodgateConfiguration`.

## Versión 4.0.5 {#v4-0-5}

**Mejoras de estabilidad y rendimiento**

Pequeñas mejoras internas en la fiabilidad de la actualización de la caché y en la gestión de conexiones.

## Versión 4.0.4 {#v4-0-4}

**Reintentar mejoras de directivas**

Se ha mejorado el comportamiento de reintentos predeterminado en errores de servicio transitorios.

## Versión 4.0.3 {#v4-0-3}

**Corrección de errores**

Correcciones generales de estabilidad para casos extremos en la inicialización asíncrona.

## Versión 4.0.1 (Beta) {#v4-0-1-beta}

**Versión de Beta de SDK 4.x**

Se ha introducido la compatibilidad con clientes DX, la configuración de región DX y la compatibilidad con AEP (zona protegida).

## Versión 3.1.0 {#v3-1-0}

**Soporte de streaming para clientes DX**

Se ha añadido la capacidad de streaming basado en SSE para notificar a los clientes de SDK las actualizaciones de indicadores en tiempo casi real.

## Versión 3.0.x {#v3-0-x}

**Se introdujo el requisito de Java 11**

A partir de la versión 3.0.0, SDK requiere JDK 11 o posterior. Las versiones principales anteriores admiten JDK 8+.

Se ha introducido la compatibilidad audiencia por referencia para clientes DX, lo que permite que el ID haga referencia a las definiciones de audiencia reutilizables en las entidades de funciones.

## Versión 2.x {#v2-x}

**Compatibilidad con clientes que no se pueden almacenar en caché (de 0.8)**

Los clientes que no se pueden almacenar en caché pueden llamar a `getFeature()` en vivo en lugar de leer de la caché de SDK. SDK continúa encuestando en segundo plano y cambia al servicio basado en caché cuando el cliente se vuelve almacenable en la caché.

Entre las mejoras adicionales de la versión 2.x se incluyen las nuevas opciones del generador (`alwaysCache()`, `neverCache()`, compatibilidad con el cliente HTTP personalizado y el ejecutor), el filtrado de claves de funcionalidad y versión y la recuperación de usuarios suplantados.

## Versión 1.x {#v1-x}

Serie de versiones iniciales. Compatible con JDK 8 y versiones posteriores, integración de dependencias Maven y recuperación básica de indicadores de funciones autenticadas y anónimas.

## Consulte también {#see-also}

* [Guía de integración de Java SDK](java-sdk-integration-guide.md)
* [Notas de la versión de SDK de Node.js](../../sdk-releases/nodejs/nodejs-sdk-release-notes.md)
* [SDK](../../integrate/sdks.md)
