---
title: Creación de un despliegue automatizado
description: Obtenga información sobre cómo configurar un plan de despliegue automatizado en Despliegues de Adobe Experience con bloques de fase y bloques de espera para que la audiencia se expanda automáticamente con el tiempo.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---


# Creación de un despliegue automatizado {#create-automated-rollout}

Un despliegue automatizado le permite definir todas las fases de despliegue y sus programaciones en una sesión. Los despliegues de experiencias avanzan de una fase a la siguiente automáticamente, sin que sea necesario volver a la consola para cada paso. Consulte [Concepto de despliegue automatizado](automated-rollout-concept.md) para obtener una descripción general.

Los despliegues automatizados son compatibles con indicadores de características, grupos de características y grupos de características de varios equipos.

## Paso 1: Habilitar el despliegue automatizado {#enable-automated-rollout}

Al crear una nueva marca de características, un grupo de características o un grupo de características de varios equipos, abre la pestaña **Detalles básicos** y busca la opción **Seleccionar tipo de despliegue**. El valor predeterminado es **Manual**. Para habilitar un plan de despliegue automatizado, seleccione **Despliegue automatizado**.

>[!NOTE]
>
>Al seleccionar Despliegue automatizado, el campo de porcentaje de despliegue en Detalles básicos se establece automáticamente en 100% y no se puede editar. Controlará el porcentaje de cada fase individualmente en la pestaña Audiencia.

## Paso 2: Creación del plan de despliegue {#build-rollout-plan}

Abra la ficha **Audiencia** y habilite la opción **Fases**. Esto activa los controles **Agregar bloque de fase** y **Agregar bloque de espera**.

Para crear el plan de despliegue, agregue bloques de fase y espera en el orden en que desee que se ejecuten:

### Añadir un bloque de fase {#add-phase-block}

Un bloque de fase define los criterios de audiencia para una fase del despliegue. El primer bloque de fase se configura con los criterios de audiencia que ya están en la página. Para cada bloque de fase posterior, la audiencia de la fase anterior se rellena previamente como punto de partida.

Configure la audiencia para cada bloque de fase:

* **Porcentaje** — Defina qué porcentaje de la audiencia definida recibe la función en esta fase.
* **Reglas de audiencia**: agregue reglas de perfil, contexto o basadas en segmentos para segmentar a usuarios específicos.

>[!IMPORTANT]
>
>Cada fase posterior debe ampliarse en la audiencia de la fase anterior, no reemplazarla. No elimine las reglas de audiencia de fases anteriores al configurar las posteriores, ya que esto puede excluir de forma involuntaria a los usuarios que ya estaban recibiendo la función.

### Añadir un bloque de espera {#add-wait-block}

Un bloque de espera define la pausa entre dos bloques de fase. Después de agregar un bloque de espera, seleccione una de las siguientes opciones:

| Opción | Descripción |
|---|---|
| **Espera** | Una duración relativa; por ejemplo, espere 2 días y 4 horas. Los despliegues de experiencias avanzan al siguiente bloque de fase después de que transcurra esta duración. |
| **Esperar** | Una fecha y hora fijas. Los despliegues de experiencias avanzan al siguiente bloque de fase en el momento especificado. |

### Añadir bloques de fase subsiguientes {#add-subsequent-phases}

Repita el proceso para agregar bloques de fase adicionales y espere bloques hasta que se configure todo el plan de despliegue.

## Paso 3: Programar o publicar el despliegue {#schedule-or-publish}

Una vez completado el plan de despliegue, elija cómo activarlo:

* **Programación**: establezca una fecha y hora futuras para que el despliegue se inicie automáticamente. Consulte [Programar](../feature-flags/schedule.md) para obtener más información.
* **Publicar manualmente** — Activa la marca de característica o mueve el grupo de características al estado **Publicar** para que se inicie inmediatamente.

El plan comienza a ejecutarse desde el primer bloque de fase. Puede supervisar y editar el plan activo en cualquier momento. Ver [Supervisar y editar un plan de despliegue](monitor-edit-rollout-plan.md).

## Consulte también {#see-also}

* [Concepto de despliegue automatizado](automated-rollout-concept.md)
* [Monitorización y edición de un plan de despliegue](monitor-edit-rollout-plan.md)
* [Configurar una función para que se implemente gradualmente](../feature-flags/set-feature-gradual-rollout.md)
* [Criterios de audiencia](../audience/audience-in-feature-flags-and-feature-groups.md)
