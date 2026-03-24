---
title: Funciones de usuario
description: Obtenga información sobre las cinco funciones de usuario disponibles en los Despliegues de Adobe Experience y cómo elegir la función adecuada para cada miembro del equipo.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---


# Funciones de usuario {#user-roles}

Los despliegues de experiencias proporcionan cinco funciones. Cada función está diseñada para un conjunto específico de responsabilidades. Las funciones se excluyen mutuamente de forma predeterminada: un miembro con la función de administrador no tiene automáticamente permisos de propietario de versión del producto. Asigne varias funciones a un miembro cuando se necesite un acceso más amplio.

## Funciones disponibles {#roles}

| Función | Responsabilidades |
|---|---|
| **Administrador** | Incorpora aplicaciones a la consola, administra miembros del equipo y aprueba o rechaza solicitudes de acceso. Es necesario para que el equipo pueda empezar a utilizar indicadores de funcionalidad. |
| **Propietario de la versión del producto** | Crea y actualiza indicadores y grupos de características para su aplicación. Puede vincular audiencias a indicadores de funcionalidades para que los usuarios externos tengan acceso a las mismas. |
| **Desarrollador** | Funciona en un contexto limitado para probar características detrás de indicadores de características sin afectar a otros usuarios. Puede exponer un indicador de funcionalidad a una audiencia privada (como un ID de usuario o una dirección de correo electrónico específicos) en Fase o Producción. |
| **Administrador de características** | Crea y administra grupos de funciones entre equipos. Utilice esta función cuando coordine indicadores en aplicaciones propiedad de equipos diferentes. |
| **Administrador de versiones** | Gestiona versiones de varios equipos y varias aplicaciones, y actualiza las reglas de audiencia que definen quién recibe una versión. |

## Elección de la función correcta {#choosing}

Siga estas instrucciones para asignar funciones:

* **Agregando o actualizando indicadores de características para su aplicación** → **Propietario del lanzamiento del producto**
* **Prueba de características de forma privada sin afectar a otros** → **Desarrollador**
* **Administración de grupos de funciones entre equipos** → **Administrador de funciones**
* **Administración de versiones en varios equipos y aplicaciones** → **Administrador de versiones**
* **Incorporar aplicaciones y administrar la membresía del equipo** → **Administrador**

>[!NOTE]
>
>Un miembro puede tener más de una función. Por ejemplo, un ingeniero que pruebe características y administre aplicaciones del equipo debe tener los roles **Desarrollador** y **Administrador**.

## Error de permisos {#permissions-error}

Si un miembro encuentra el error &quot;no hay suficientes permisos&quot; al intentar actualizar una característica o un grupo, necesita la función **Propietario de la versión del producto**. Póngase en contacto con el administrador del equipo para que se agregue esta función.

## Consulte también {#see-also}

* [Añadir miembros a su equipo](add-team-members.md)
* [Administrar equipos](manage-teams.md)
