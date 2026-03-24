---
title: Funciones, grupos de funciones y versiones
description: Obtenga información acerca de las diferencias entre los indicadores de características, los grupos de características, los grupos de características entre equipos y las versiones en los Despliegues de Adobe Experience y cuándo utilizarlos.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 2%

---


# Funciones, grupos de funciones y versiones {#features-feature-groups-releases}

Los despliegues de experiencias proporcionan cuatro artefactos para administrar los despliegues de funciones. La elección del adecuado depende del ámbito del despliegue, el número de equipos implicados y las capacidades de segmentación de audiencia que necesite.

## Los cuatro artefactos {#artifacts}

**Indicador de característica**
La unidad más atómica. Controla una única función para una única aplicación, propiedad de un equipo. Se puede habilitar o deshabilitar para una audiencia definida.

**Grupo de funciones**
Colección de indicadores de características que pertenecen al mismo equipo. Permite administrar varios indicadores en varias aplicaciones en un equipo como una sola unidad.

**Grupo de características entre equipos**
Amplía las capacidades de los grupos de funciones en varios equipos y aplicaciones. Autoservicio y admite criterios de audiencia enriquecidos, pero no admite el almacenamiento en caché.

**Versión**
Diseñado para implementaciones grandes y coordinadas en varios equipos y aplicaciones. Utiliza la segmentación de audiencia basada en token de autenticación. Admite el almacenamiento en caché en el servidor de SDK.

## Comparación {#comparison}

| | Indicador de funcionalidad | Grupo de funciones | Grupo de funciones entre equipos | Versión |
|---|---|---|---|---|
| **Se requiere el rol para administrar la audiencia** | Propietario de versión del producto | Propietario de versión del producto | Administrador de funciones | Administrador de versiones |
| **Aplicaciones** | Único | Múltiple (mismo equipo) | Múltiple (entre equipos) | Múltiple (entre equipos) |
| **Equipos** | Único | Único | Equipo cruzado | Equipo cruzado |
| **Criterios de audiencia enriquecidos** | ✓ | ✓ | ✓ | Limitado |
| **Despliegue de porcentaje** | Combinado con cualquier criterio de audiencia | Combinado con cualquier criterio de audiencia | Combinado con cualquier criterio de audiencia | Combinado con criterios de audiencia fijos |
| **Pruebas A/B** | ✓ | ✓ | ✗ | ✗ |
| **Almacenamiento en caché en el servidor SDK** | Solo indicadores de activación/desactivación predeterminados | Sin almacenamiento en caché | Sin almacenamiento en caché | Todas las versiones almacenadas en caché localmente |
| **Autoservicio** | ✓ | ✓ | ✓ | Requiere solicitud de soporte |
| **Pista de auditoría** | ✓ | ✓ | ✓ | ✓ |

## Cuándo usar cada {#when-to-use}

| Situación | Utilice |
|---|---|
| Prueba o despliegue de una única función para una aplicación | **Indicador de característica** |
| Coordinación de varias funciones en el mismo equipo, que se activan al mismo tiempo | **Grupo de funciones** |
| Coordinación de funciones entre aplicaciones en equipos diferentes, con direccionamiento enriquecido | **Grupo de características entre equipos** |
| Versión coordinada a gran escala en varios equipos, con almacenamiento en caché a nivel de SDK | **Versión** |

## Consulte también {#see-also}

* [Creación de la primera marca de funcionalidad](create-your-first-feature-flag.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)
* [Crear un grupo de funciones entre equipos](create-cross-team-feature-group.md)
* [Versiones y grupos de funciones entre equipos](releases-and-cross-team-feature-groups.md)
