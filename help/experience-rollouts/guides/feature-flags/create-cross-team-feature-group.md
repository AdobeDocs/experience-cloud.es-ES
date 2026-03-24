---
title: Crear un grupo de funciones entre equipos
description: Obtenga información sobre cómo crear un grupo de funciones entre equipos en los despliegues de Adobe Experience para coordinar los indicadores de funciones en las aplicaciones propiedad de distintos equipos.
source-git-commit: db719ba7b9db91aea818d8ef216a28fcedc6aa65
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 2%

---


# Crear un grupo de funciones entre equipos {#create-cross-team-feature-group}

## Requisitos previos {#prerequisites}

Antes de crear un grupo de funciones entre equipos, confirme lo siguiente:

* Tiene acceso a la consola; consulte [Iniciar sesión en la consola](../console/log-in-to-the-console.md)
* Pertenece a un equipo y la aplicación está integrada
* Tiene el rol **Administrador de características**; consulte [Roles de usuario](../teams/user-roles.md)
* Ha creado los indicadores de características que desea incluir. Consulte [Crear su primer indicador de características](create-your-first-feature-flag.md)

Un grupo de funciones entre equipos permite agrupar indicadores de funciones de aplicaciones de varios equipos con segmentación de audiencia enriquecida. A diferencia de las versiones, es completamente autoservicio y no tiene límite en el número que puede crear. Consulte [Versiones y grupos de características entre equipos](releases-and-cross-team-feature-groups.md) para ver una comparación.

## Paso 1: Crear el grupo de funciones entre equipos {#create}

Inicie el proceso de creación desde la sección Versiones de la consola:

1. Vaya a **Características y versiones > Versiones** en la consola.
2. Seleccione **Nuevo grupo de funciones (entre equipos)**.

## Paso 2: Detalles básicos {#basic-details}

Proporcione un título, clave, descripción y, opcionalmente, una etiqueta. Configure las siguientes opciones:

* **Despliegue porcentual**: establezca la cantidad de audiencia que recibe la función.
* **Tipo de despliegue** — Definir como Manual. El porcentaje se administra paso a paso a medida que progresa el despliegue.

>[!NOTE]
>
>Las pruebas A/B no son compatibles con los grupos de funciones entre equipos. Para ejecutar pruebas A/B, use un [grupo de características](create-a-feature-group.md) estándar (las aplicaciones deben estar en el mismo equipo).

## Paso 3: Audiencia {#audience}

En la ficha **Audiencia**, habilite **Reglas de audiencia** y configure:

* **Segmentos**: seleccione un segmento de audiencia predefinido.
* **Filtros adicionales**: agregue directamente criterios basados en perfiles o en contexto.
* **Aplicaciones**: seleccione una o más aplicaciones de su equipo u otros equipos.

>[!IMPORTANT]
>
>Al añadir una solicitud de otro equipo, se concede a los administradores de funciones de dicho equipo el derecho de añadir indicadores de funciones para su aplicación a este grupo de funciones de varios equipos. No puede agregar sus indicadores de características usted mismo.

## Paso 4: Funciones {#features}

En la ficha **Características**, verá un cuadro para cada aplicación incluida:

* Para las aplicaciones de su propio equipo, puede agregar indicadores de características directamente.
* Para las aplicaciones de otros equipos, esas casillas aparecen atenuadas; los administradores de características del equipo correspondiente deben agregar sus indicadores.

>[!IMPORTANT]
>
>Un indicador de funcionalidad solo se puede proporcionar mediante un método a la vez. Al agregar una marca a un grupo de funciones entre equipos, se elimina directamente cualquier despliegue de audiencia o porcentaje establecido en la marca. Las marcas que ya se encuentren en otra versión o grupo de funciones no aparecerán.

## Paso 5: Programar (opcional) {#schedule}

Puede programar el grupo de funciones entre equipos para que se active en una fecha y hora futuras. Consulte [Programar](schedule.md) para obtener más información.

## Administración de estados {#states}

El equipo que crea el grupo de funciones entre equipos es el propietario y puede administrar su estado. Los miembros del administrador de funciones del equipo propietario pueden realizar la transición entre estados mediante la lista desplegable de estados:

| Estado | Descripción |
|---|---|
| **Guardar** | Guardado y no activo. Se permiten todos los cambios. |
| **Publicar** | Activa para la audiencia configurada. Los administradores de funciones pueden seguir actualizando los criterios de audiencia y el porcentaje de despliegue. |
| **Despliegue completo** | Disponible para todos los usuarios. No se puede restringir más la audiencia después de este punto. |
| **Línea base** | Ahora, las funciones son las predeterminadas. El grupo de funciones entre equipos está cerrado. |
| **Anular** | El despliegue está detenido. Ningún usuario recibe características de este grupo. |

## Preguntas frecuentes {#faqs}

**¿Hay un límite en el número de grupos de características entre equipos?**
No. A diferencia de las versiones, no hay límite. Sin embargo, puede archivar o deshabilitar los grupos cuando ya no los necesite.

**¿Cuál es la diferencia entre una versión y un grupo de características entre equipos?**
Consulte [Versiones y grupos de características entre equipos](releases-and-cross-team-feature-groups.md) para ver una comparación detallada.

## Consulte también {#see-also}

* [Versiones y grupos de funciones entre equipos](releases-and-cross-team-feature-groups.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)
