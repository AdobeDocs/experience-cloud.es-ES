---
title: Incorporar la aplicación
description: Obtenga información sobre cómo incorporar una nueva aplicación a los despliegues de Adobe Experience para que su equipo pueda empezar a crear y administrar indicadores de funcionalidades.
source-git-commit: 9bfe0e55e89c1d7fbd77cde63831a6a186820e24
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 1%

---


# Incorporar la aplicación {#onboard-your-application}

Debe tener el rol **Administrador** para agregar una aplicación nueva. Consulte [Funciones de usuario](../teams/user-roles.md) si necesita verificar la función o solicitarla al administrador del equipo.

## Agregar nueva aplicación {#add-application}

1. Inicie sesión en la consola Despliegues de experiencias y vaya a **Administración > Aplicaciones**.

   >[!NOTE]
   >
   >Si el botón **Nueva aplicación** no está visible, compruebe que está en el equipo correcto y que tiene el rol **Administrador**.

2. Seleccione **Nueva aplicación**.

3. Seleccione el **canal** que coincida con el tipo de aplicación (web, móvil, escritorio o servicio).

4. Proporcione la siguiente información:

   | Campo | Descripción |
   |---|---|
   | **ID de aplicación** | Un identificador único que se utiliza al llamar a los despliegues de experiencia desde el código. Utilice el ID de cliente de su aplicación. |
   | **TTL** | Intervalo de sondeo (en segundos) para actualizar la caché por aplicación. Solo se aplica a los SDK del lado del servidor. |
   | **Equipo** | Equipo que será el propietario y administrará esta aplicación. Solo los miembros de este equipo pueden crear y editar indicadores de características para él. |

5. Seleccione **Agregar**. La aplicación ya está registrada y lista para la configuración de indicadores de características.

## Qué viene después {#next-steps}

Una vez integrada la aplicación, el equipo puede empezar a crear indicadores de funcionalidades:

* [Creación de la primera marca de funcionalidad](../feature-flags/create-your-first-feature-flag.md)
* [Integración de despliegues de experiencias en la aplicación](../integrate/integrating-in-your-app.md)

## Consulte también {#see-also}

* [Administrar aplicaciones](manage-applications.md)
* [Funciones de usuario](../teams/user-roles.md)
* [Inicie sesión en la consola de](../console/log-in-to-the-console.md)
