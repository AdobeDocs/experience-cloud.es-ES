---
title: Concepto de despliegue automatizado
description: Comprenda cómo funcionan los despliegues automatizados en los Despliegues de Adobe Experience, incluidos los bloques de fase, los bloques de espera y cómo progresa automáticamente el plan de despliegue.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 2%

---


# Concepto de despliegue automatizado {#automated-rollout-concept}

Un despliegue automatizado le permite definir todo el plan de despliegue por fases de una sola vez. En lugar de volver manualmente a la consola para ampliar la audiencia en cada fase, debe configurar todas las fases y sus programaciones por adelantado y los despliegues de experiencias avanzan a través de ellas automáticamente.

Los despliegues automatizados son compatibles con indicadores de características, grupos de características y grupos de características de varios equipos.

## Funcionamiento {#how-it-works}

Un plan de despliegue se compone de **bloques de fase** y **bloques de espera** que se ejecutan en secuencia:

* **Bloque de fase**: define los criterios de audiencia para una fase del despliegue. Cuando el plan alcanza un bloque de fase, esa audiencia se convierte en la audiencia activa para la función.
* **Bloque de espera** — Define la pausa entre dos bloques de fase. Un bloque de espera puede ser una duración relativa (por ejemplo, &quot;espera 3 días&quot;) o una fecha y hora fijas.

El plan se inicia al publicar la función o programarla para una fecha futura. Los despliegues de experiencias pasan de un bloque al siguiente automáticamente según la programación configurada.

## Comportamiento de bloque de fase {#phase-block-behavior}

Cada bloque de fase posterior se rellena previamente con la audiencia de la fase anterior. Esto facilita la generación de despliegues que se expanden gradualmente, donde cada nueva fase incluye todos los grupos de audiencias anteriores, además de los nuevos.

>[!IMPORTANT]
>
>Las reglas de audiencia en cada bloque de fase son editables, por lo que debe asegurarse de no eliminar los criterios de audiencia de fases anteriores al agregar nuevas. La reducción del alcance de la audiencia durante el despliegue puede provocar que los usuarios pierdan el acceso a una función de forma inesperada.

## Desplegar estados de plan {#rollout-plan-states}

Una vez que un plan de despliegue está activo, puede estar en uno de estos tres estados:

| Estado | Descripción |
|---|---|
| **En curso** | El plan se está ejecutando. Un indicador de progreso en la consola muestra qué bloque de fase está activo actualmente. Todos los bloques completados están bloqueados y no se pueden editar. |
| **En pausa** | El plan está en espera. La audiencia del último bloque de fase completado permanece activa. Los bloques de fase y espera futuros aún se pueden editar mientras se pausan. |
| **Anulado** | El plan se ha detenido de forma permanente. La audiencia del último bloque de fase completado permanece activa. No se permiten más ediciones en el plan. Anular el plan no desactiva la función; debe cambiar por separado el estado de la función si desea dejar de ofrecerla. |

## Consulte también {#see-also}

* [Creación de un despliegue automatizado](create-automated-rollout.md)
* [Monitorización y edición de un plan de despliegue](monitor-edit-rollout-plan.md)
* [Configurar una función para que se implemente gradualmente](../feature-flags/set-feature-gradual-rollout.md)
