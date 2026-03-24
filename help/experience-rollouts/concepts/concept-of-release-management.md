---
title: Concepto de administración de versiones
description: Descubra cómo la administración de versiones en los Despliegues de experiencias ayuda a coordinar despliegues de funciones grandes entre equipos mediante el indicador de funciones.
source-git-commit: 1c8fd9b42d08f657b4e6b16efae86faa04d15565
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Concepto de administración de versiones {#concept-of-release-management}

Las versiones grandes comparten algunos desafíos comunes: hay varios equipos implicados, las programaciones entran en conflicto y las dependencias son difíciles de coordinar. La administración de versiones aborda estos desafíos al proporcionar una manera estructurada de implementar los cambios sin problemas.

## Qué significa la administración de versiones {#what-it-means}

La administración de versiones cubre la coordinación de una versión de principio a fin: desde el momento en que los equipos comienzan a desarrollar indicadores de funcionalidades hasta el momento en que la funcionalidad está totalmente disponible para todos los usuarios.

Permite a los equipos lo siguiente:

* Implementar de forma independiente en producción, a su propio ritmo, sin revelar funciones a los usuarios finales
* Publique solo cuando todos los equipos participantes estén listos
* Despliegue la versión gradualmente para un subconjunto de usuarios antes de su disponibilidad completa

## Cómo funciona en los despliegues de experiencias {#how-it-works}

La administración de versiones en los lanzamientos de experiencias se basa en el concepto de [marcar características](what-is-a-feature-flag.md). Cada equipo implementa su código en producción tras un indicador de funcionalidad. Una versión es una **colección de indicadores de características definidos en varias aplicaciones y equipos**.

Cuando todos los equipos están listos, la versión se puede activar en una sola operación (o implementarse gradualmente) sin que ningún equipo individual necesite volver a implementar o coordinar el tiempo de implementación.

Este enfoque proporciona lo siguiente:

* **Implementación independiente**: los equipos implementan según su propia programación sin afectar a otros equipos o usuarios finales.
* **Activación coordinada**: todas las marcas de una versión se activan juntas cuando la versión se activa.
* **Despliegue gradual**: la versión se puede abrir progresivamente para aumentar el porcentaje de usuarios.

Para obtener más información sobre la configuración de versiones en los lanzamientos de experiencias, consulte [Administración de versiones](release-management.md).
