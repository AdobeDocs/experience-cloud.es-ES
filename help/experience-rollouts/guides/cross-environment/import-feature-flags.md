---
title: Importar indicadores de características
description: Obtenga información sobre cómo importar indicadores de funcionalidades de una zona protegida a otra en los despliegues de Adobe Experience para evitar volver a crear configuraciones de indicadores manualmente.
exl-id: 37c84d75-a565-4202-8c99-f630e05b6bb6
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 1%

---

# Importar indicadores de características {#import-feature-flags}

Los despliegues de experiencias permiten importar indicadores de características de una zona protegida (por ejemplo, la zona protegida 1) a otra zona protegida (por ejemplo, la zona protegida 2). Esto evita tener que volver a crear las configuraciones de indicador manualmente y reduce el riesgo de deriva de la configuración entre zonas protegidas.

## Paso 1: Vaya a la zona protegida y a la aplicación de destino {#step-1}

Inicie sesión en la consola de la zona protegida **destination**: la zona protegida en la que desea importar los indicadores *en*. Seleccione la aplicación en la que desea importar indicadores desde la lista desplegable de aplicaciones en la página Indicadores de funcionalidad.

>[!IMPORTANT]
>
>La zona protegida actual y la aplicación seleccionada deben ser el **destino**, no el origen. Por ejemplo, para importar un indicador de la zona protegida 1 en la zona protegida 2, inicie sesión en la consola de la zona protegida 2 y seleccione la aplicación de zona protegida 2.

## Paso 2: Abrir el cuadro de diálogo de importación {#step-2}

Seleccione **Importar indicadores de características**. Se abre un cuadro de diálogo que muestra la zona protegida y la aplicación de origen, previamente rellenadas en función de las aplicaciones disponibles. Si es necesario, puede cambiar la zona protegida y la aplicación de origen desde los desplegables del cuadro de diálogo.

## Paso 3: Seleccionar los indicadores de funcionalidad que desea importar {#step-3}

En la lista de indicadores de características de la zona protegida de origen, seleccione los indicadores que desee importar. Puede seleccionar uno, varios o todos los indicadores a la vez.

## Paso 4: Seleccionar el estado de los indicadores de funcionalidad que desea importar {#step-4}

Utilice el menú desplegable para elegir cómo se deben importar los indicadores de características: **Habilitado**, **Deshabilitado** o en su **Estado actual**. De manera predeterminada, los indicadores de características se importan en el estado **Deshabilitado**.

## Notas importantes {#important-notes}

Tenga en cuenta lo siguiente al importar indicadores de características:

* Si ya existe un indicador de funciones con la misma clave en la zona protegida de destino, no se importará.

## Consulte también {#see-also}

* [Características y grupos de características](../feature-flags/features-feature-groups-releases.md)
* [Creación de la primera marca de funcionalidad](../feature-flags/create-your-first-feature-flag.md)
