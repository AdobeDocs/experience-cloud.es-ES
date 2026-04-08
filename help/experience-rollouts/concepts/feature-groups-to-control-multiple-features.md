---
title: Grupos de funciones para controlar varias funciones
description: Descubra cómo los grupos de funciones en los Despliegues de experiencias le permiten agrupar y administrar indicadores de funciones relacionados en todas las aplicaciones como una sola unidad.
exl-id: dfeb7eff-34f1-4cb5-9c3e-a40d1eda3016
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# Grupos de funciones para controlar varias funciones {#feature-groups}

Una [marca de característica](what-is-a-feature-flag.md) controla una sola característica. Cuando necesite administrar varios indicadores de características relacionados juntos (y asegurarse de que lleguen a la misma audiencia), utilice un **grupo de características**.

## Qué hace un grupo de funciones {#what-it-does}

Un grupo de funciones agrupa varios indicadores de funciones y permite aplicar una sola regla de audiencia a todos a la vez. Esto resulta útil cuando una sola capacidad orientada al usuario abarca varias aplicaciones o servicios.

Por ejemplo, considere una función de colaboración que implique cambios en una aplicación de escritorio, una aplicación móvil y un servicio back-end. Al crear un grupo de funciones con indicadores de las tres aplicaciones, puede abrir la función al 1 % de los usuarios y garantizar que estos vean una experiencia coherente en las tres superficies simultáneamente.

## Agrupación entre aplicaciones {#cross-application}

Los grupos de funciones admiten la administración de funciones entre aplicaciones. Los indicadores relacionados de varias aplicaciones se pueden agrupar.

