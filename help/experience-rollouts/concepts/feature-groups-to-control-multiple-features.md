---
title: Grupos de funciones para controlar varias funciones
description: Descubra cómo los grupos de funciones en los Despliegues de experiencias le permiten agrupar y administrar indicadores de funciones relacionados en todas las aplicaciones como una sola unidad.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---


# Grupos de funciones para controlar varias funciones {#feature-groups}

Una [marca de característica](what-is-a-feature-flag.md) controla una sola característica. Cuando necesite administrar varios indicadores de características relacionados juntos (y asegurarse de que lleguen a la misma audiencia), utilice un **grupo de características**.

## Qué hace un grupo de funciones {#what-it-does}

Un grupo de funciones agrupa varios indicadores de funciones y permite aplicar una sola regla de audiencia a todos a la vez. Esto resulta útil cuando una sola capacidad orientada al usuario abarca varias aplicaciones o servicios.

Por ejemplo, considere una función de colaboración que implique cambios en una aplicación de escritorio, una aplicación móvil y un servicio back-end. Al crear un grupo de funciones con indicadores de las tres aplicaciones, puede abrir la función al 1 % de los usuarios y garantizar que estos vean una experiencia coherente en las tres superficies simultáneamente.

## Agrupación entre aplicaciones {#cross-application}

Los grupos de características admiten la administración de características entre aplicaciones siempre que los indicadores pertenezcan al **mismo equipo** en los despliegues de experiencias. Un equipo puede ser propietario de varias aplicaciones, por lo que los indicadores relacionados de esas aplicaciones se pueden agrupar.

## Grupos de funciones frente a versiones {#vs-releases}

| | Grupo de funciones | Versión |
|---|---|---|
| Ámbito | Dentro de un solo equipo | En varios equipos |
| Ejemplo de uso | Coordinación de indicadores dentro del equipo | Coordinación del lanzamiento de equipos grandes y múltiples |
| Privilegios necesarios | Nivel de equipo | Superior (administrador de versiones) |

Si los indicadores de características que desea agrupar pertenecen a aplicaciones propiedad de equipos diferentes, use una [versión](release-management.md) en lugar de un grupo de características.
