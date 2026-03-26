---
title: Programación
description: Obtenga información sobre cómo programar un indicador de funciones, un grupo de funciones o un grupo de funciones entre equipos para que se activen automáticamente en una fecha y hora futuras en los lanzamientos de Adobe Experience.
exl-id: f8309daa-428b-41a0-8817-89c8f603bec8
source-git-commit: 454b5c719a5f8be82d1ed835da58bfca6316def2
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# Programación {#schedule}

La programación es una función opcional que permite establecer una fecha y hora futuras para que un indicador o grupo de características se active automáticamente. El alternado manual de encendido y apagado permanece disponible y no es necesario reemplazarlo por una programación.

Se admite la programación para:

* Indicadores de función
* Grupos de funciones

## Paso 1: Establecer la programación {#set-schedule}

1. Abra la marca de características o el grupo de características en la consola.
2. Seleccione el botón **Programar** que aparece a la derecha de la pantalla.
3. En la ventana emergente, establece la **fecha y hora de inicio** y selecciona la **zona horaria**.

## Paso 2: Guardar {#save}

Seleccione **Establecer horario** y, a continuación, guarde la configuración. La programación no surtirá efecto hasta que la guarde.

## Después de establecer una programación {#after-schedule-set}

Una vez guardadas, la fecha y la hora programadas aparecen en la marca de características o en la vista de grupo de características.

Si intenta cambiar el estado de activación/desactivación manualmente mientras una programación está activa, aparece una advertencia que le pregunta si desea anular la programación o cancelar la acción.

## En la fecha y hora programadas {#on-schedule}

A la hora programada, el indicador o grupo de características se activará automáticamente (pasará al estado ACTIVADO).

Una vez que se activa la programación, se desactiva el botón **Programar**. Las programaciones solo se pueden establecer cuando el indicador o el grupo de características está desactivado.

## Consulte también {#see-also}

* [Creación de la primera marca de funcionalidad](create-your-first-feature-flag.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)
