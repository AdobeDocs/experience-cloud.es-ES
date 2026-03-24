---
title: Información general sobre las API de administración de funciones
description: Información general sobre las API de administración de despliegues de experiencias, que le permiten crear, leer, actualizar y eliminar indicadores de características, grupos de características y versiones mediante programación.
source-git-commit: 6ecedbfc6c7de392f214f3f8f2e71aa18e1bacb9
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---


# Información general sobre las API de administración de funciones {#feature-management-apis-overview}

Las API de administración de despliegues de experiencia permiten administrar indicadores de características, grupos de características y versiones de forma programada. Los equipos que necesiten automatizar flujos de trabajo o integrar Despliegues de experiencias en canalizaciones de implementación existentes pueden utilizar estas API en lugar de la consola.

>[!NOTE]
>
>El acceso a las API de administración mediante un token de servicio se concede previa solicitud. Póngase en contacto con el servicio de asistencia de Despliegues de experiencias y proporcione una justificación empresarial para solicitar acceso.

## API de administración disponibles {#available-apis}

Las siguientes API de administración están disponibles:

* [API de administración de indicadores de características](feature-flags-management-api.md): cree, lea, actualice y elimine indicadores de características para una aplicación.
* [API de administración de grupos de funciones](feature-group-management-api.md): cree, lea, actualice, elimine y controle planes de despliegue automatizados para grupos de funciones.
* [API de administración de versiones](release-management-apis.md): cree y edite grupos de funciones y versiones entre equipos.

## Requisitos comunes {#common-requirements}

Todas las llamadas a la API de administración requieren lo siguiente:

* Una **clave API** de Adobe Developer Console; consulte [Suscribirse a la aplicación API](../guides/integrate/subscribe-to-api-application.md).
* Un **token de acceso de usuario de IMS** o **token de servicio**, pasado como `Bearer <token>` en el encabezado `Authorization`.
* Un encabezado `Content-Type: application/json`.

Las claves y los tokens de API deben aprovisionarse por separado para los entornos de ensayo y producción.

## Guías de ayuda {#helper-guides}

Las siguientes guías le ayudarán a crear cargas útiles de API correctas:

* [Obtener ID de cliente para una aplicación](get-client-id.md): busque el ID de cliente numérico requerido por los indicadores de características y las API de administración de grupos de características.
* [Obtener los criterios de audiencia deseados](get-audience-criteria.md): utilice la consola y la API de GET para generar la estructura JSON de criterios de audiencia correcta.
* [API de parche de administración](management-patch-api.md): actualice los campos individuales de un indicador de características, un grupo de características o un grupo de características de varios equipos sin pasar el objeto completo.

## Consulte también {#see-also}

* [API de funciones de GET V3](../feature-api/get-feature-api-v3.md)
* [API de funciones de GET V2](../feature-api/get-feature-api-v2.md)
* [Suscripción a la aplicación API](../guides/integrate/subscribe-to-api-application.md)
