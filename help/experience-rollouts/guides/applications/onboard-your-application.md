---
title: Incorporar la aplicación
description: Obtenga información sobre cómo incorporar una nueva aplicación a los despliegues de Adobe Experience para poder empezar a crear y administrar indicadores de funcionalidades.
exl-id: d88c27a5-f490-4504-9764-5e4ce98fdf20
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 2%

---

# Incorporar la aplicación {#onboard-your-application}

Debe tener el rol **Administrador** para agregar una aplicación nueva. Póngase en contacto con el administrador si necesita comprobar o actualizar su función.

## Agregar nueva aplicación {#add-application}

1. Inicie sesión en la consola Despliegues de experiencias y vaya a **Despliegue de experiencias > Aplicaciones**.

   >[!NOTE]
   >
   >Si el botón **Nueva aplicación** no está visible, verifique que tiene el rol **Administrador de Floodgate**.

2. Seleccione **Nueva aplicación**.

3. Seleccione la **plataforma** que coincida con su tipo de aplicación (web o móvil).

4. Proporcione la siguiente información:

   | Campo | Descripción |
   |---|---|
   | **ID de aplicación** | Un identificador único que se utiliza al llamar a los despliegues de experiencia desde el código. Utilice el ID de cliente de su aplicación. |
   | **TTL** | Intervalo de sondeo (en segundos) para actualizar la caché por aplicación. Solo se aplica a los SDK del lado del servidor. |

5. Seleccione **Agregar**. La aplicación ya está registrada y lista para la configuración de indicadores de características.

## Qué viene después {#next-steps}

Una vez integrada la aplicación, puede empezar a crear indicadores de funcionalidades:

* [Creación de la primera marca de funcionalidad](../feature-flags/create-your-first-feature-flag.md)
* [Integración de despliegues de experiencias en la aplicación](../integrate/integrating-in-your-app.md)

## Consulte también {#see-also}

* [Administrar aplicaciones](manage-applications.md)
* [Inicie sesión en la consola de](../console/log-in-to-the-console.md)
