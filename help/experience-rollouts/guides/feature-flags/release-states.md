---
title: Estados de versión
description: Obtenga información acerca de los estados del ciclo vital de una versión en los Despliegues de Adobe Experience, incluido qué significa cada estado y qué transiciones están permitidas.
source-git-commit: ae420329b94b24fcd173734b414aecf1c5fc16ca
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 3%

---


# Estados de versión {#release-states}

Un Release Manager puede actualizar el estado de una versión directamente desde la barra de navegación de la consola. El estado controla si la versión está activa, limitada a pruebas, implementada por completo o cerrada.

## Estados disponibles {#states}

| # | Estado | Descripción | Cambios permitidos |
|---|---|---|---|
| 1 | **Borrador** | La versión se guarda en el sistema, pero aún no está activa. No se aplican reglas de audiencia. | Todos los cambios permitidos (versión, funciones, audiencia). |
| 2 | **Guardado** | La versión se registra y se le asigna una ranura. La versión aún no es visible para los usuarios. | Se permiten todos los cambios. |
| 3 | **Publicadas** | La versión está activa para la audiencia especificada. Los usuarios que cumplan los criterios de audiencia reciben las funciones. | Se permiten todos los cambios. |
| 4 | **Despliegue completo** | La versión está disponible para todos los usuarios, independientemente de las reglas de audiencia. Se eliminan todas las reglas de audiencia. | Se permiten cambios de características. La audiencia no se puede cambiar. |
| 5 | **Aprobado** | Ahora todos los usuarios tienen las funciones de esta versión como comportamiento predeterminado. El código condicional se puede eliminar. La ranura de liberación está liberada. | No se permiten cambios. |
| 6 | **Anulado** | La versión se ha detenido. Ningún usuario recibe funciones de esta versión. La ranura de liberación está liberada. | No se permiten cambios. |

## Transiciones permitidas {#transitions}

No se permiten todas las transiciones de estado. Comprender las rutas permitidas le ayuda a planificar el despliegue y a evitar errores al administrar los cambios de estado:

* Una versión puede avanzar entre los siguientes estados: Borrador → Guardado → Publicado → Despliegue completo → Aprobado
* Una versión puede anularse del borrador, guardarse, publicarse o implementarse por completo
* Una vez aprobada o anulada, no se permiten más cambios

## Capacidad de versión {#capacity}

El número de versiones activas (guardadas o publicadas) en cualquier momento es limitado. Para liberar capacidad:

* Mover las versiones completadas a **Aprobadas** una vez que todas las aplicaciones participantes hayan eliminado su código condicional.
* **Anular** versiones que no se realizaron correctamente y que no continuarán.

Planifique la línea de base o anule las versiones en un plazo de tres meses.

## Consulte también {#see-also}

* [Solicitar una versión](request-a-release.md)
* [Flujo de trabajo de la versión de extremo a extremo](release-workflow-end-to-end.md)
* [Actualizar reglas de audiencia de lanzamiento](update-release-audience-rules.md)
