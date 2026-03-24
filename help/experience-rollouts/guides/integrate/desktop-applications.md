---
title: Aplicaciones de escritorio
description: Obtenga información sobre cómo integrar Despliegues de experiencias de Adobe en una aplicación de escritorio mediante la API de funciones V2.
source-git-commit: b82520eebe0070b5f76e0f7daeb2bb79a4bccca0
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 1%

---


# Aplicaciones de escritorio {#desktop-applications}

Las aplicaciones de escritorio se integran con los despliegues de experiencias realizando llamadas directas a la API de REST. Use la **API de características V2** para clientes de escritorio.

Consulte **GET Feature API V2** en la sección Feature API de esta guía para obtener la referencia completa de la API.

## Requisitos de integración {#requirements}

Los clientes de escritorio deben:

* **Respete el valor TTL** devuelto en la respuesta de la API. El TTL define cuánto tiempo el cliente debe almacenar en caché los datos de indicadores de funciones antes de volver a llamar a la API. Implemente un caso de prueba que valide este comportamiento para asegurarse de que las versiones de aplicaciones anteriores entren en hibernación correctamente cuando no se proporcionen indicadores de características.
* **Controlar correctamente los escenarios de error HTTP**. Compile un conjunto de características de reserva para que la aplicación siga funcionando si la API no está disponible temporalmente.
* **Mantenga un plan de prueba de integración detallado** que cubre los requisitos de TTL y de gestión de errores anteriores.

## ID de aplicación {#app-id}

Los clientes de escritorio pueden usar un **código de producto y una versión de producto** como identificador de aplicación al llamar a la API, en lugar de un identificador de cliente estándar.

## Consulte también {#see-also}

* [Pasos de integración](integration-steps.md)
* [Guía de inicio](startup-guide.md)
