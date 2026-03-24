---
title: Despliegues de Adobe Experience
description: Aprenda a utilizar los despliegues de Adobe Experience para ofrecer funciones de forma segura y gradual con despliegues controlados, indicadores de funciones y administración de audiencias segmentadas.
exl-id: c400d75d-d928-4cf6-a094-1a2f443389f0
source-git-commit: 65effd7e3b12404359e3693820bbf9e5080bea03
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 1%

---

# Despliegues de Adobe Experience {#experience-rollouts-home}

Los despliegues de experiencia de Adobe permiten a los equipos de productos enviar nuevas funciones de forma gradual y segura, sin reimplementaciones ni tiempo de inactividad. Usted define quién ve qué, cuándo y a qué ritmo. Si algo sale mal, se desactiva la función al instante. Si sale bien, la audiencia se amplía según la programación.

## Lo que puede hacer

**Controlar quién ve las nuevas características.** Versiones de Target para usuarios, organizaciones, regiones o atributos personalizados específicos. Comience con un grupo pequeño, valide la experiencia y expanda, todo desde la consola, sin cambios en el código.

**Ejecutar experimentos A/B.** Sirva diferentes variantes a diferentes segmentos de su audiencia y mida cuál tiene un mejor rendimiento. Utilice los resultados para tomar decisiones informadas sobre el producto antes de una versión completa.

**Reducir el riesgo de versión.** Divida los cambios grandes en despliegues más pequeños y controlados. Si aparece un error o un problema de rendimiento, deshabilite solo la función afectada; el resto de la aplicación permanecerá estable.

**Coordinar entre equipos.** Los grupos de funciones entre equipos permiten que varios equipos participen en una sola versión coordinada, cada uno de los cuales gestiona sus propios indicadores de funciones a la vez que comparten una programación y una audiencia de despliegue comunes.

## Incorpore su primera función

La obtención de valor de los lanzamientos de experiencias comienza con tres pasos:

1. **Configure su equipo y su aplicación** — [Solicite acceso](guides/console/request-access.md) a la consola y, a continuación, [incorpore su aplicación](guides/applications/onboard-your-application.md) para que los lanzamientos de experiencias sepan qué clientes atender.

2. **Crear y publicar una marca de características** — Siga la guía de [Crear su primera marca de características](guides/feature-flags/create-your-first-feature-flag.md) para definir una marca, establecer su audiencia inicial y publicarla en su entorno.

3. **Integrar con su aplicación**: conecte su aplicación a la API de despliegues de experiencia o a SDK para que pueda recuperar y aplicar indicadores de características durante la ejecución. Comience con los [pasos de integración](guides/integrate/integration-steps.md) para su tipo de aplicación.

Una vez que su primer indicador esté activo, puede refinar su audiencia, configurar un despliegue gradual y promocionarlo a través de [estados de lanzamiento](guides/feature-flags/release-states.md) desde guardado a despliegue completo.

## ¿Necesita ayuda?

Si algo no se comporta como se espera, la [guía de solución de problemas](guides/support/troubleshooting.md) trata los problemas más comunes. Para cualquier otra cosa, [comuníquese con la atención al cliente](guides/support/contact-support.md).
