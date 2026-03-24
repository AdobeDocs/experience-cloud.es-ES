---
audience: user
user-guide-title: Despliegues de Adobe Experience
user-guide-description: Aprenda a utilizar los despliegues de Adobe Experience para administrar indicadores de funcionalidades, despliegues controlados y versiones de destino en las aplicaciones.
source-git-commit: cd1d882942705f51440ae99f4ce6daf467d3283c
workflow-type: tm+mt
source-wordcount: '315'
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
      + [Resumen de los entornos](guides/console/environments-overview.md)
      + [Solicitar acceso](guides/console/request-access.md)
      + [Equipos y sus administradores](guides/console/teams-and-admins.md)
      + [Crear un nuevo equipo](guides/console/create-a-new-team.md)
   + Equipos {#teams}
      + [Administrar equipos](guides/teams/manage-teams.md)
      + [Funciones de usuario](guides/teams/user-roles.md)
      + [Añadir miembros a su equipo](guides/teams/add-team-members.md)
      + [Preguntas frecuentes sobre administración de equipos](guides/teams/team-management-faq.md)
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
   + Indicadores de funciones y versiones {#feature-flags-releases}
      + [Funciones, grupos de funciones y versiones](guides/feature-flags/features-feature-groups-releases.md)
      + [Creación de la primera marca de funcionalidad](guides/feature-flags/create-your-first-feature-flag.md)
      + [Configurar una función para que se implemente gradualmente](guides/feature-flags/set-feature-gradual-rollout.md)
      + [Creación de un grupo de funciones](guides/feature-flags/create-a-feature-group.md)
      + [Configuración de un grupo de funciones para su despliegue gradual](guides/feature-flags/set-feature-group-gradual-rollout.md)
      + [Pruebas A/B con indicadores de funcionalidades](guides/feature-flags/a-b-testing.md)
      + [Versiones y grupos de funciones entre equipos](guides/feature-flags/releases-and-cross-team-feature-groups.md)
      + [Flujo de trabajo de la versión de extremo a extremo](guides/feature-flags/release-workflow-end-to-end.md)
      + [Solicitar una versión](guides/feature-flags/request-a-release.md)
      + [Actualizar reglas de audiencia de lanzamiento](guides/feature-flags/update-release-audience-rules.md)
      + [Estados de versión](guides/feature-flags/release-states.md)
      + [Crear un grupo de funciones entre equipos](guides/feature-flags/create-cross-team-feature-group.md)
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
   + Despliegues automatizados {#automated-rollouts}
      + [Creación de un despliegue automatizado](guides/automated-rollouts/create-automated-rollout.md)
      + [Concepto de despliegue automatizado](guides/automated-rollouts/automated-rollout-concept.md)
      + [Monitorización y edición de un plan de despliegue](guides/automated-rollouts/monitor-edit-rollout-plan.md)
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
<!--+ Feature API {#feature-api}
  + [GET Feature API V3](feature-api/get-feature-api-v3.md)
  + [GET Feature API V2](feature-api/get-feature-api-v2.md)
+ Management API {#management-api}
  + [Feature management APIs overview](management-api/feature-management-apis-overview.md)
  + [Feature flags management API](management-api/feature-flags-management-api.md)
  + [Feature group management API](management-api/feature-group-management-api.md)
  + [Release management APIs](management-api/release-management-apis.md)
  + [Get client ID for an application](management-api/get-client-id.md)
  + [Get desired audience criteria](management-api/get-audience-criteria.md)
  + [Management patch API](management-api/management-patch-api.md)-->
