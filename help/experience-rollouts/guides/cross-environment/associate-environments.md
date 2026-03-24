---
title: Asociar entornos a una aplicación
description: Obtenga información sobre cómo vincular las instancias de aplicaciones entre entornos en los despliegues de Adobe Experience para poder administrar los indicadores de funcionalidades de forma coherente desde el desarrollo hasta la producción.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 1%

---


# Asociar entornos a una aplicación {#associate-environments}

La vinculación de las instancias de aplicación entre entornos permite la visibilidad entre entornos y los flujos de trabajo de importación. Debe tener el rol **Administrador** para configurarlo. Consulte [Funciones de usuario](../teams/user-roles.md) si necesita verificar su función.

Para obtener información general sobre por qué esto resulta útil, consulte [Concepto entre entornos](cross-environment-concept.md).

## Paso 1: Abrir la configuración de la aplicación {#step-1}

1. Inicie sesión en la consola Despliegues de experiencias.
2. Vaya a **Administración > Aplicaciones**.
3. Seleccione **Nueva aplicación** para incorporar una aplicación nueva o seleccione una aplicación existente para editarla.

## Paso 2: Configurar la sección Entornos asociados {#step-2}

En el formulario de solicitud, desplácese hasta la sección **Entornos asociados**. Cada fila de esta sección define uno de los entornos de implementación de la aplicación. Para cada entorno, configure los siguientes campos:

| Campo | Descripción |
|---|---|
| **Entorno** | Seleccione un identificador de entorno estándar de la lista: QA1, QA2, STG1, STG2, PROD1 o PROD2. Esto indica a los despliegues de experiencias si el entorno es de producción o no de producción y determina la codificación de color utilizada en la consola. |
| **Etiqueta de entorno** | Un nombre personalizado para este entorno como lo hace referencia su equipo, por ejemplo, `Dev`, `Staging` o `Production`. Es de forma libre y no necesita coincidir con el identificador estándar. |
| **Entorno de despliegues de experiencias** | El entorno de plataforma (fase o producción) en el que se aloja esta instancia de aplicación. Rellenado previamente en función de la consola en la que se encuentre actualmente. |
| **ID de aplicación** | El ID de cliente de la instancia de aplicación en este entorno. Se rellena automáticamente al seleccionar una aplicación de la lista desplegable. |

## Paso 3: Vincular instancias de aplicaciones entre entornos {#step-3}

Para vincular instancias entre entornos, siga estos pasos para cada entorno adicional:

1. Cree la instancia de la aplicación en su entorno de destino (por ejemplo, cree la aplicación de control de calidad en la consola de fase).
2. Vuelva a la aplicación que está configurando y agregue una fila nueva en **Entornos asociados**.
3. En la lista desplegable **ID de aplicación**, seleccione la instancia de aplicación que acaba de crear. La etiqueta de entorno y la etiqueta se rellenan automáticamente.
4. Seleccione **Actualización** para guardar.

Repita este proceso para cada entorno que desee vincular; por ejemplo, para vincular instancias de control de calidad, fase y producción de la misma aplicación.

## Notas importantes {#important-notes}

* Los entornos de control de calidad y ensayo se pueden alojar en el entorno de la plataforma Experience Rollouts o Production.
* Los entornos de producción (PROD1, PROD2) solo se pueden alojar en el entorno de producción Despliegues de experiencias.
* Solo puede vincular a un entorno inferior desde uno superior. Por ejemplo, desde Producción puede vincular a una instancia de fase o control de calidad, pero al revés es de solo lectura.

## Consulte también {#see-also}

* [Concepto entre entornos](cross-environment-concept.md)
* [Visualización de indicadores de funcionalidades en entornos](view-feature-flags-across-environments.md)
* [Importar indicadores de características](import-feature-flags.md)
