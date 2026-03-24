---
title: Guía de inicio
description: Siga estos pasos para integrar su aplicación con los despliegues de Adobe Experience, desde solicitar acceso a crear su primer indicador de funcionalidad.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 1%

---


# Guía de inicio {#startup-guide}

Siga estos pasos para integrar Despliegues de experiencias en su aplicación.

## Paso 1: Solicitar acceso {#step-1-access}

Solicite acceso a la consola Despliegues de experiencias y únase a su equipo. Consulte [Solicitar acceso](../console/request-access.md) para obtener instrucciones paso a paso.

## Paso 2: Incorporar la aplicación {#step-2-onboard}

Después de obtener acceso, inicie sesión en la consola Despliegues de experiencias y compruebe que la aplicación aparece en la lista de su equipo. Si no es así, pídale al administrador del equipo que lo añada. Consulte [Incorporar su aplicación](../applications/onboard-your-application.md).

Antes de la incorporación, prepare lo siguiente:

| Requisito | Detalles |
|---|---|
| **ID de aplicación** | Identificador de cliente único que se utiliza al llamar a las API de despliegues de experiencia. Utilice el ID de cliente existente de la aplicación donde esté disponible. |
| **Clientes del lado del servidor** | Si se integra con un SDK del lado del servidor, necesita un ID de cliente de administración con los permisos adecuados. |
| **Clientes de escritorio** | Se puede utilizar un código de producto y una versión de producto en lugar de un ID de cliente. |

## Paso 3: Suscripción a la API de despliegues de experiencia {#step-3-subscribe}

Suscríbase a la API de despliegues de experiencia a través de Adobe Developer Console para que su aplicación pueda llamar a los extremos de los indicadores de funcionalidades. Ver [Suscribirse a la aplicación API en Adobe Developer Console](subscribe-to-api-application.md).

>[!NOTE]
>
>Si está realizando la integración mediante un SDK del lado del servidor, necesita un ID de cliente de token de servicio. Póngase en contacto con el servicio de asistencia de Despliegues de experiencias para que su ID de cliente esté incluido en la lista de permitidos.

## Paso 4: Integración con una SDK o la API {#step-4-integrate}

Siga los [pasos de integración](integration-steps.md) para su tipo de aplicación. Elija la ruta que se ajuste a la pila:

* **Servicios web** → Java SDK o Node.js SDK
* **Aplicaciones web y móviles** → API de funciones V3
* **Aplicaciones de escritorio** → API de característica V2

## Paso 5: Crear y probar el primer indicador de funcionalidad {#step-5-feature-flag}

Una vez completada la integración, cree el primer indicador de funcionalidad en la consola y pruébelo:

* [Creación de la primera marca de funcionalidad](../feature-flags/create-your-first-feature-flag.md)

## Consulte también {#see-also}

* [Integración de despliegues de experiencias en la aplicación](integrating-in-your-app.md)
* [Pasos de integración](integration-steps.md)
* [SDK](sdks.md)
