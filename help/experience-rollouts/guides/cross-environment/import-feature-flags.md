---
title: Importar indicadores de características
description: Obtenga información sobre cómo importar indicadores de funcionalidades de un entorno inferior a un entorno superior en los Despliegues de Adobe Experience para evitar volver a crear configuraciones de indicadores manualmente.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 1%

---


# Importar indicadores de características {#import-feature-flags}

Los despliegues de experiencias permiten importar indicadores de funciones de un entorno inferior (por ejemplo, Fase) a un entorno superior (por ejemplo, Producción). Esto evita tener que volver a crear las configuraciones de indicador manualmente y reduce el riesgo de deriva de la configuración entre entornos.

## Requisitos previos {#prerequisites}

Para utilizar el flujo de trabajo de importación, las instancias de la aplicación deben estar vinculadas entre entornos. Consulte [Asociar entornos a una aplicación](associate-environments.md).

## Paso 1: Vaya al entorno y la aplicación de destino {#step-1}

Inicie sesión en la consola del entorno **destination**, el entorno al que desea importar los indicadores *en*. Seleccione la aplicación en la que desea importar indicadores desde la lista desplegable de aplicaciones en la página Indicadores de funcionalidad.

>[!IMPORTANT]
>
>El entorno actual y la aplicación seleccionada deben ser el **destino**, no el origen. Por ejemplo, para importar un indicador desde Fase a Producción, inicie sesión en la consola de producción y seleccione la aplicación de producción.

## Paso 2: Abrir el cuadro de diálogo de importación {#step-2}

Seleccione **Importar indicadores de características**. Se abre un cuadro de diálogo que muestra el entorno de origen y la aplicación, previamente rellenados en función de los entornos vinculados configurados para la aplicación. Si es necesario, puede cambiar el entorno de origen y la aplicación desde los menús desplegables del cuadro de diálogo.

## Paso 3: Seleccionar los indicadores de funcionalidad que desea importar {#step-3}

En la lista de indicadores de características del entorno de origen, seleccione los indicadores que desee importar. Puede seleccionar uno, varios o todos los indicadores a la vez.

## Paso 4: Administrar los indicadores existentes (si es necesario) {#step-4}

Si ya existe un indicador de funcionalidad con la misma clave en el entorno de destino, los lanzamientos de experiencias le pedirán que confirme si desea sobrescribirlo. Revise la configuración del indicador existente antes de confirmarlo, ya que la sobrescritura reemplazará la configuración del indicador de destino con la del origen.

## Notas importantes {#important-notes}

Tenga en cuenta lo siguiente al importar indicadores de características:

* Las marcas importadas siempre se establecen con el estado **OFF** en el entorno de destino, independientemente de su estado en el entorno de origen. Debe activarlos manualmente después de la importación.
* Si se programó la activación de un indicador en una fecha y hora futuras en el entorno de origen, esa programación **no** se transfiere. Debe establecer una nueva programación en el entorno de destino si es necesario.

## Consulte también {#see-also}

* [Asociar entornos a una aplicación](associate-environments.md)
* [Visualización de indicadores de funcionalidades en entornos](view-feature-flags-across-environments.md)
* [Concepto entre entornos](cross-environment-concept.md)
