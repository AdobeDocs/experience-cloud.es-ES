---
title: Concepto entre entornos
description: Descubra cómo las funciones entre entornos de los lanzamientos de Adobe Experience le permiten vincular aplicaciones entre entornos y administrar indicadores de funciones de forma coherente, desde el desarrollo hasta la producción.
source-git-commit: 5c99061a7f2aaaad98190166ea6fd79b7eb26dec
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Concepto entre entornos {#cross-environment-concept}

Las funciones entre entornos permiten vincular las instancias de la aplicación en distintos entornos de implementación, como control de calidad, fase y producción, y administrar los indicadores de funciones de forma coherente en todos ellos desde los lanzamientos de experiencias.

## El problema se resuelve en todos los entornos {#problem}

Sin vinculación entre entornos, cada instancia de aplicación en los Despliegues de experiencias es completamente independiente de sus equivalentes en otros entornos. Esto crea varios puntos de fricción:

* Una aplicación denominada `my-app` en fase no tiene relación con `my-app` en producción; se tratan como aplicaciones independientes no relacionadas.
* No se puede ver el estado de un indicador de funcionalidad en Fase mientras se trabaja en Producción. Debe cambiar de entorno manualmente para comparar los estados de los indicadores.
* La importación de una configuración de indicador de funcionalidad de un entorno inferior a uno superior requiere la recreación manual.

## Lo que habilita el entorno cruzado {#what-it-enables}

Al vincular instancias de aplicaciones entre entornos, su equipo puede:

* Defina cuál de los entornos de implementación de su aplicación debe asignar a qué entornos de Despliegues de experiencias
* Use etiquetas de entorno personalizadas (por ejemplo, `Dev`, `Staging`, `Prod`) que coincidan con las convenciones de nomenclatura de su equipo
* Ver el estado de un indicador de funcionalidad en todos los entornos vinculados desde una sola vista
* Importe indicadores de características de un entorno inferior a uno superior con unos pocos clics, sin volver a crearlos manualmente

## Estructura de los entornos {#environment-structure}

Los lanzamientos de experiencias tienen dos entornos de plataforma: **Fase** y **Producción**. Sin embargo, la aplicación puede tener más entornos, por ejemplo, control de calidad, ensayo y producción. La vinculación entre entornos le permite decidir dónde vive cada uno de los entornos de la aplicación:

* Los entornos de control de calidad y ensayo se pueden alojar en el entorno de ensayo de despliegues de experiencias o de producción.
* Los entornos de producción deben alojarse en el entorno de producción Despliegues de experiencias.

Esta flexibilidad significa que no se verá obligado a utilizar una asignación única para todos los casos.

## Próximos pasos {#next-steps}

* [Asociar entornos a una aplicación](associate-environments.md): configure los vínculos entre las instancias de la aplicación
* [Ver indicadores de características en entornos](view-feature-flags-across-environments.md): supervise el estado de los indicadores en todos los entornos vinculados
* [Importar indicadores de características](import-feature-flags.md) — promocionar indicadores de características de entornos inferiores a superiores
