---
audience: user
user-guide-title: Despliegues de Adobe Experience
user-guide-description: Aprenda a utilizar los despliegues de Adobe Experience para administrar indicadores de funcionalidades, despliegues controlados y versiones de destino en las aplicaciones.
source-git-commit: c654ca1507abcefcff84cef9f99830042939805d
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 6%

---


# Despliegues de Adobe Experience {#experience-rollouts}

+ [Información general](home.md)
+ Primeros pasos {#get-started}
   + [Introducción a los despliegues de experiencias](getting-started/introduction.md)
   + [Razones para utilizar los despliegues de experiencias](getting-started/why-use-experience-rollouts.md)
   + [Modos de despliegues de experiencia](getting-started/experience-rollouts-modes.md)
+ Conceptos {#concepts}
   + [¿Qué es un indicador de funcionalidad?](concepts/what-is-a-feature-flag.md)
   + [Indicadores de características para habilitar y deshabilitar características](concepts/feature-flags-to-enable-disable-features.md)
   + [Grupos de funciones para controlar varias funciones](concepts/feature-groups-to-control-multiple-features.md)
   + [Concepto de administración de versiones](concepts/concept-of-release-management.md)
   + [Administración de versiones en despliegues de experiencias](concepts/release-management.md)
   + [Despliegue gradual](concepts/gradual-rollout.md)
+ Guías {#guides}
   + Introducción a la consola {#console}
      + [Inicie sesión en la consola Despliegues de experiencias](guides/console/log-in-to-the-console.md)
      + [Seleccione la zona protegida](guides/console/environments-overview.md)
      + [Solicitar acceso](guides/console/request-access.md)
   + Aplicaciones {#applications}
      + [Administrar aplicaciones](guides/applications/manage-applications.md)
      + [Incorporar la aplicación](guides/applications/onboard-your-application.md)
   + Integrar despliegues de experiencias {#integrate}
      + [Integración de despliegues de experiencias en la aplicación](guides/integrate/integrating-in-your-app.md)
      + [Guía de inicio](guides/integrate/startup-guide.md)
      + [Aplicaciones de escritorio](guides/integrate/desktop-applications.md)
      + [Aplicaciones móviles](guides/integrate/mobile-applications.md)
      + [Aplicaciones web](guides/integrate/web-applications.md)
      + [Servicios web](guides/integrate/web-services.md)
      + [SDK](guides/integrate/sdks.md)
      + [Pasos de integración](guides/integrate/integration-steps.md)
      + [Suscripción a la aplicación API en Adobe Developer Console](guides/integrate/subscribe-to-api-application.md)
   + Indicadores de función {#feature-flags}
      + [Características y grupos de características](guides/feature-flags/features-feature-groups-releases.md)
      + [Creación de la primera marca de funcionalidad](guides/feature-flags/create-your-first-feature-flag.md)
      + [Configurar una función para que se implemente gradualmente](guides/feature-flags/set-feature-gradual-rollout.md)
      + [Creación de un grupo de funciones](guides/feature-flags/create-a-feature-group.md)
      + [Configuración de un grupo de funciones para su despliegue gradual](guides/feature-flags/set-feature-group-gradual-rollout.md)
      + [Pruebas A/B con indicadores de funcionalidades](guides/feature-flags/a-b-testing.md)
      + [Preguntas frecuentes sobre gestión de versiones](guides/feature-flags/release-management-faqs.md)
      + [Analytics](guides/feature-flags/analytics.md)
      + [Programación](guides/feature-flags/schedule.md)
   + Criterios de audiencia {#audience}
      + [Audiencia en indicadores y grupos de características](guides/audience/audience-in-feature-flags-and-feature-groups.md)
      + [Uso del contexto en las reglas de audiencia](guides/audience/using-context-in-audience-rules.md)
      + [Reglas de audiencia complejas](guides/audience/complex-rules.md)
      + [Uso de datos de organización empresarial en reglas de audiencia](guides/audience/using-enterprise-org-data.md)
      + [Agregar reglas de porcentaje en criterios de audiencia](guides/audience/adding-percentage-rules.md)
      + [Regla de audiencia con variable de contexto IP de cliente](guides/audience/clientip-rule.md)
   + Flujos de trabajo entre entornos {#cross-environment}
      + [Concepto entre entornos](guides/cross-environment/cross-environment-concept.md)
      + [Asociar entornos a una aplicación](guides/cross-environment/associate-environments.md)
      + [Visualización de indicadores de funcionalidades en entornos](guides/cross-environment/view-feature-flags-across-environments.md)
      + [Importar indicadores de características](guides/cross-environment/import-feature-flags.md)
   + Asistencia {#support}
      + [Solución de problemas](guides/support/troubleshooting.md)
      + [Obtener asistencia técnica](guides/support/get-support.md)
      + [Atención al cliente](guides/support/contact-support.md)
   + Versiones de SDK {#sdk-releases}
      + SDK de Java {#java-sdk}
         + [Guía de integración de Java SDK](guides/sdk-releases/java/java-sdk-integration-guide.md)
         + [Notas de la versión de Java SDK](guides/sdk-releases/java/java-sdk-release-notes.md)
      + SDK de Node.js {#nodejs-sdk}
         + [Guía de integración de SDK de Node.js](guides/sdk-releases/nodejs/nodejs-sdk-integration-guide.md)
         + [Notas de la versión de SDK de Node.js](guides/sdk-releases/nodejs/nodejs-sdk-release-notes.md)
      + [pruebas comparativas de SDK](guides/sdk-releases/java-sdk-benchmarking.md)
+ API de funciones {#feature-api}
   + [API de funciones de GET V3](feature-api/get-feature-api-v3.md)
   + [API de funciones de GET V2](feature-api/get-feature-api-v2.md)
+ API de administración {#management-api}
   + [Información general sobre las API de administración de funciones](management-api/feature-management-apis-overview.md)
   + [API de administración de indicadores de funcionalidad](management-api/feature-flags-management-api.md)
   + [API de administración de grupos de funciones](management-api/feature-group-management-api.md)
   + [API de administración de versiones](management-api/release-management-apis.md)
   + [Obtener el ID de cliente de una aplicación](management-api/get-client-id.md)
   + [Obtener los criterios de audiencia deseados](management-api/get-audience-criteria.md)
   + [API de parche de administración](management-api/management-patch-api.md)
