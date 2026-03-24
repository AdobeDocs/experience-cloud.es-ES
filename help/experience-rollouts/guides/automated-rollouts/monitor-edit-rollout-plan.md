---
title: Monitorización y edición de un plan de despliegue
description: Obtenga información sobre cómo rastrear el progreso de un plan de despliegue automatizado en Despliegues de Adobe Experience y cómo pausar, reanudar o cancelar un plan en curso.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---


# Monitorización y edición de un plan de despliegue {#monitor-edit-rollout-plan}

Una vez que se activa un despliegue automatizado, puede realizar un seguimiento de su progreso e intervenir si es necesario. En esta página se describe cómo leer el indicador de progreso, pausar y reanudar un plan y anularlo si es necesario.

En esta página se da por hecho que ya ha creado y publicado un plan de despliegue. Consulte [Crear un despliegue automatizado](create-automated-rollout.md) si todavía no ha configurado uno.

## Ver progreso de despliegue {#view-progress}

Una vez que el plan de despliegue comience a ejecutarse, abra la pestaña **Audiencia** de la función para ver el estado actual del plan. El plan muestra un indicador de progreso que marca qué bloque de fase está activo actualmente.

Utilice el indicador de progreso para comprender lo siguiente:

* **Bloques completados**: se han ejecutado todos los bloques de fase y espera por encima del indicador. Estos bloques están bloqueados y no se pueden editar.
* **Bloque actual**: el bloque resaltado actualmente es la fase activa o el período de espera.
* **Próximos bloques**: todos los bloques de fase y espera por debajo del indicador aún no se han ejecutado. Pueden seguir editándose.

## Pausar un plan de despliegue {#pause}

Para pausar el despliegue en cualquier momento mientras está en curso, selecciona **Pausar despliegue** en la consola.

Cuando el plan está en pausa:

* La audiencia del último bloque de fase completado permanece activa. Los usuarios de dicha audiencia seguirán recibiendo la función.
* El indicador de funciones, el grupo de funciones o el grupo de funciones entre equipos permanecen en su estado actual activado o publicado. Sigue ofreciendo la función a la audiencia activa actual.
* Los próximos bloques de fase y espera siguen siendo editables.

Para reanudar un plan en pausa, seleccione **Reanudar despliegue**. El plan continúa desde donde lo dejó.

## Anulación de un plan de despliegue {#abort}

Para detener permanentemente el plan de despliegue, selecciona **Anular despliegue** en la consola.

Cuando se anula el plan:

* La audiencia del último bloque de fase completado permanece activa y la función se sigue ofreciendo a esa audiencia.
* La función en sí no está desactivada: si desea dejar de proporcionar la función por completo, debe cancelar por separado la versión o desactivar la marca o el grupo de características.
* Los bloques de fase y espera próximos ya no se pueden editar.
* No se puede reanudar un plan anulado.

>[!IMPORTANT]
>
>Anular un plan de despliegue no desactiva automáticamente la función. Realice una acción independiente en el estado de la función si desea dejar de ofrecerla a los usuarios.

## Editar bloques de fase próximos {#edit-upcoming}

Mientras el plan está en curso (o en pausa), aún puede editar cualquier fase o bloque de espera que aún no se haya ejecutado:

* Ajuste las reglas de audiencia o el porcentaje para un bloque de fase próximo.
* Cambie la duración o la fecha fija de un bloque de espera próximo.

Los bloques completados están bloqueados y no se pueden cambiar.

## Consulte también {#see-also}

* [Creación de un despliegue automatizado](create-automated-rollout.md)
* [Concepto de despliegue automatizado](automated-rollout-concept.md)
* [Estados de versión](../feature-flags/release-states.md)
