---
title: Visualización de indicadores de funcionalidades en entornos
description: Obtenga información sobre cómo ver el estado de los indicadores de funcionalidades en todos los entornos vinculados para una aplicación en los lanzamientos de Adobe Experience.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Visualización de indicadores de funcionalidades en entornos {#view-flags-across-environments}

Una vez que haya vinculado las instancias de la aplicación en entornos, los Despliegues de experiencias muestran el estado de cada indicador de función en todos los entornos vinculados directamente en la página de lista de indicadores de funciones. Esto le proporciona una sola vista para comparar los estados de los indicadores (por ejemplo, si un indicador está ACTIVADO en Fase y DESACTIVADO en Producción) sin cambiar de entorno.

## Requisitos previos {#prerequisites}

Las instancias de la aplicación deben vincularse entre entornos antes de que el estado entre entornos sea visible. Consulte [Asociar entornos a una aplicación](associate-environments.md) para obtener instrucciones de configuración.

## Funcionamiento {#how-it-works}

Cuando navega a **Características y versiones > Indicadores de características** y selecciona una aplicación que tiene instancias vinculadas, la página del listado muestra columnas adicionales para cada entorno vinculado. Cada columna muestra el estado actual del indicador de funcionalidad en ese entorno.

Los indicadores de características coinciden en todos los entornos por su **clave**, no por su nombre. Esto significa que:

* Un indicador puede tener un nombre para mostrar diferente en cada entorno, siempre y cuando la clave sea la misma.
* El nombre que se muestra en cada columna de entorno es el nombre que se utiliza en ese entorno.

## Ejemplo de uso {#use-case}

Un flujo de trabajo típico consiste en desarrollar y probar un indicador de funciones en un entorno inferior (por ejemplo, Fase) y, a continuación, verificar su estado antes de promocionar la configuración a Producción. La visibilidad entre entornos permite confirmar que el indicador está correctamente configurado en Fase antes de importarlo a Producción, todo desde la consola de producción.

## Consulte también {#see-also}

* [Asociar entornos a una aplicación](associate-environments.md)
* [Importar indicadores de características](import-feature-flags.md)
* [Concepto entre entornos](cross-environment-concept.md)
