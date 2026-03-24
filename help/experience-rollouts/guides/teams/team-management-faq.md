---
title: Preguntas frecuentes sobre administración de equipos
description: Encuentre respuestas a preguntas comunes sobre la administración de equipos, miembros y funciones en los Despliegues de experiencias de Adobe.
source-git-commit: 53edbee220e7ef17c4a3ea066743192c1e9681f4
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 1%

---


# Preguntas frecuentes sobre administración de equipos {#team-management-faq}

## Estoy intentando añadir un usuario, pero la búsqueda no devuelve ningún resultado {#user-not-found}

Esto puede ocurrir en el entorno de ensayo si el usuario nunca ha iniciado sesión en Fase antes. Para resolver esto, pida al usuario que inicie sesión en la consola de fase al menos una vez para crear su cuenta en el sistema de identidad de fase. Cuando hayan iniciado sesión, intente buscarlos de nuevo.

## Soy administrador, pero no puedo crear ni editar indicadores de funcionalidades {#admin-cannot-edit-flags}

Las funciones en los Despliegues de experiencias se excluyen mutuamente. El rol **Administrador** concede permisos de administración de equipos, pero no incluye los permisos de un **Propietario de la versión del producto**. Para crear y editar indicadores de características, un miembro necesita la función **Propietario de la versión del producto** además de la función **Administrador**.

Póngase en contacto con el administrador del equipo para que se le asignen funciones adicionales. Consulte [Funciones de usuario](user-roles.md) para obtener un desglose completo de lo que cada función puede hacer.

## ¿Los administradores tienen una jerarquía? ¿Puede un administrador anular a otro? {#admin-hierarchy}

No. Los equipos de los despliegues de experiencias tienen una estructura plana. Todos los miembros con el rol **Admin** tienen los mismos permisos y pueden administrar las configuraciones de los demás. No hay ningún flujo de trabajo de aprobación jerárquico entre administradores.

## ¿Cómo elimino a un miembro de mi equipo? {#remove-member}

Los miembros se eliminan a través del sistema de administración de acceso. Como administrador, busque el registro de acceso del miembro para su equipo y revoque su función. Si no está seguro de cómo hacerlo, póngase en contacto con el equipo de administración de acceso de su organización.

## ¿Puede un miembro tener más de una función? {#multiple-roles}

Sí. Asigne varios roles a un miembro cuando sus responsabilidades abarquen más de una función. Por ejemplo, un miembro del equipo que administre el equipo y cree indicadores de características debe tener los roles **Administrador** y **Propietario de la versión del producto**.

## Consulte también {#see-also}

* [Funciones de usuario](user-roles.md)
* [Añadir miembros a su equipo](add-team-members.md)
* [Administrar equipos](manage-teams.md)
