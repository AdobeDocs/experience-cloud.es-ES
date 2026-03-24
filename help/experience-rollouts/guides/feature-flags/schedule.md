---
title: Programación
description: Obtenga información sobre cómo programar un indicador de funciones, un grupo de funciones o un grupo de funciones entre equipos para que se activen automáticamente en una fecha y hora futuras en los lanzamientos de Adobe Experience.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 2%

---


# Programación {#schedule}

La programación es una función opcional que permite establecer una fecha y hora futuras para que un indicador de funciones, un grupo de funciones o un grupo de funciones entre equipos se activen automáticamente. El alternado manual de encendido y apagado permanece disponible y no es necesario reemplazarlo por una programación.

Se admite la programación para:

* Indicadores de función
* Grupos de funciones
* Grupos de funciones entre equipos (programa la transición al estado **Publish**)

## Paso 1: Establecer la programación {#set-schedule}

1. Abra la marca de características, el grupo de características o el grupo de características entre equipos en la consola.
2. Seleccione el botón **Programar** que aparece a la derecha de la pantalla.
3. En la ventana emergente, establece la **fecha y hora de inicio** y selecciona la **zona horaria**.

## Paso 2: Guardar {#save}

Seleccione **Establecer horario** y, a continuación, guarde la configuración. La programación no surtirá efecto hasta que la guarde.

## Después de establecer una programación {#after-schedule-set}

Una vez guardadas, la fecha y la hora programadas aparecen en la marca de características o en la vista de grupo de características.

Si intenta cambiar el estado de activación/desactivación manualmente mientras una programación está activa, aparece una advertencia que le pregunta si desea anular la programación o cancelar la acción.

## En la fecha y hora programadas {#on-schedule}

A la hora programada, el indicador o grupo de características se activará automáticamente (pasará al estado ACTIVADO). Para los grupos de características entre equipos, el estado cambia a **Publicado**.

Una vez que se activa la programación, se desactiva el botón **Programar**. Las programaciones solo se pueden definir cuando el indicador de funciones o el grupo de funciones está en estado desactivado (o Guardado, para grupos de funciones de varios equipos).

## Consulte también {#see-also}

* [Creación de la primera marca de funcionalidad](create-your-first-feature-flag.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)
* [Crear un grupo de funciones entre equipos](create-cross-team-feature-group.md)
