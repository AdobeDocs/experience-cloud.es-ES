---
title: Creación de la primera marca de funcionalidad
description: Obtenga información sobre cómo crear un indicador de funciones en los despliegues de Adobe Experience, establecer una audiencia y probarlo antes de desplegarlo a los usuarios.
exl-id: ae115120-8da9-465e-a556-c17591ea7054
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Creación de la primera marca de funcionalidad {#create-feature-flag}

## Requisitos previos {#prerequisites}

Antes de crear un indicador de funcionalidad, complete lo siguiente:

* Tiene acceso a la consola Despliegues de experiencias. Consulte [Iniciar sesión en la consola](../console/log-in-to-the-console.md)
* Su aplicación está integrada. Consulte [Incorporar su aplicación](../applications/onboard-your-application.md)
* Tiene la función **Desarrollador** o **Propietario de la versión del producto**

## Paso 1: Crear el indicador de funcionalidad {#create}

Para crear un nuevo indicador de funcionalidad, siga estos pasos en la consola:

1. Inicie sesión en la consola Despliegues de experiencias y vaya a **Características y versiones > Indicadores de características**.
2. Seleccione su aplicación en la lista desplegable **Aplicación**.
3. Seleccione **Nueva característica**.
4. Proporcione un título, clave, descripción y, opcionalmente, una etiqueta.
5. Si lo desea, puede añadir un criterio de audiencia (consulte el paso 2).
6. Guarde la configuración de las marcas de características.

## Paso 2: Añadir un criterio de audiencia {#audience}

Los criterios de audiencia controlan qué usuarios ven la función. Puede agregar criterios basados en lo siguiente:

* Atributos de perfil (como país, dominio de correo electrónico o ID de usuario)
* Variables de contexto
* Segmentos de audiencia predefinidos

Para agregar criterios de audiencia, vaya a la pestaña **Audiencia** al crear o editar una marca de característica.

>[!NOTE]
>
>El rol **Desarrollador** se encuentra en una zona protegida. Los desarrolladores solo pueden exponer una característica a sí mismos agregando su propio ID de usuario en **Audiencia > Perfil > ID de usuario**. Para exponer una característica a usuarios externos, necesita el rol **Propietario de la versión del producto**.

## Paso 3: Calcular el tamaño de la audiencia {#audience-size}

Después de agregar los criterios de audiencia, selecciona **Calcular** en la barra inferior para obtener un recuento estimado de los usuarios que califican para la función. Esto ayuda a validar el direccionamiento antes de lanzarse.

## Paso 4: Programar (opcional) {#schedule}

Puede programar una marca de características para que se active en una fecha y hora futuras mediante la opción **Programar** en la configuración de la marca de características.

## Preguntas frecuentes: No puedo agregar un indicador de funcionalidad como desarrollador {#faq}

El rol **Desarrollador** se encuentra en una zona protegida. Los desarrolladores pueden probar las funciones de forma privada añadiendo su ID de usuario a la audiencia. No pueden exponer las funciones a usuarios externos. Utilice el rol **Propietario de la versión del producto** para publicar características para usuarios externos. Póngase en contacto con el administrador del equipo para actualizar su función.

## Consulte también {#see-also}

* [Configurar una función para que se implemente gradualmente](set-feature-gradual-rollout.md)
* [Creación de un grupo de funciones](create-a-feature-group.md)
