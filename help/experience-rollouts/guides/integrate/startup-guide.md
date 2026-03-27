---
title: Guía de inicio
description: Siga estos pasos para integrar su aplicación con los despliegues de Adobe Experience, desde solicitar acceso a crear su primer indicador de funcionalidad.
exl-id: 7aa09535-45fa-4ddf-9e3f-a23f8a8ee666
source-git-commit: 2a946868f58e25f8aafbf3ccfcf6571e7d0d8d20
workflow-type: tm+mt
source-wordcount: '286'
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

## Paso 3: Consiga sus credenciales {#step-3-credentials}

Si está realizando la integración mediante un SDK del lado del servidor, necesita un ID de cliente de token de servicio. Póngase en contacto con la asistencia de despliegues de experiencia para que su ID de cliente esté incluido en la lista de permitidos antes de poder realizar llamadas de API desde SDK.

## Paso 4: Integración con un SDK {#step-4-integrate}

Siga los [pasos de integración](integration-steps.md) para su tipo de aplicación. Elija la ruta que se ajuste a la pila:

* **Servicios web** → Java SDK o Node.js SDK
* **Aplicaciones web y móviles** → Web SDK o SDK móvil (próximamente)
* **Aplicaciones de escritorio** → SDK (próximamente)

## Paso 5: Crear y probar el primer indicador de funcionalidad {#step-5-feature-flag}

Una vez completada la integración, cree el primer indicador de funcionalidad en la consola y pruébelo:

* [Creación de la primera marca de funcionalidad](../feature-flags/create-your-first-feature-flag.md)

## Consulte también {#see-also}

* [Integración de despliegues de experiencias en la aplicación](integrating-in-your-app.md)
* [Pasos de integración](integration-steps.md)
* [SDK](sdks.md)
