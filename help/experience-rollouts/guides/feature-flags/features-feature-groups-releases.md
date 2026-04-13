---
title: Características y grupos de características
description: Obtenga información sobre las diferencias entre los indicadores de características y los grupos de características en los Despliegues de Adobe Experience y cuándo utilizarlos.
hide: true
exl-id: 852aa777-6f8a-47c9-bf54-e645a5ee2f3e
source-git-commit: 12032cbed45e694a3f25f16afe80308b3eb82924
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 4%

---

# Características y grupos de características {#features-feature-groups}

Los despliegues de experiencias proporcionan dos artefactos para administrar los despliegues de funciones. La elección de la correcta depende del ámbito del despliegue y de la cantidad de funciones involucradas.

## Los dos artefactos {#artifacts}

**Indicador de funcionalidad**
La unidad más atómica. Controla una única función para una única aplicación. Se puede habilitar o deshabilitar para una audiencia definida.

**Grupo de funciones**
Colección de indicadores de características que pertenecen al mismo equipo. Permite administrar varios indicadores en varias aplicaciones como una sola unidad.

## Comparación {#comparison}

| | Indicador de funcionalidad | Grupo de funciones |
|---|---|---|
| **Se requiere el rol para administrar la audiencia** | Propietario de versión del producto | Propietario de versión del producto |
| **Aplicaciones** | Único | Múltiple (mismo equipo) |
| **Criterios de audiencia enriquecidos** | ✓ | ✓ |
| **Despliegue de porcentaje** | Combinado con cualquier criterio de audiencia | Combinado con cualquier criterio de audiencia |
| **Pruebas A/B** | ✓ | ✓ |
| **Autoservicio** | ✓ | ✓ |
| **Pista de auditoría** | ✓ | ✓ |

## Cuándo usar cada {#when-to-use}

| Situación | Utilice |
|---|---|
| Prueba o despliegue de una única función para una aplicación | **Indicador de característica** |
| Coordinación de varias funciones en el mismo equipo, que se activan al mismo tiempo | **Grupo de funciones** |

## Consulte también {#see-also}

* [Creación de la primera marca de funcionalidad](create-your-first-feature-flag.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)

<!-- -->
