---
title: Audiencia en indicadores y grupos de características
description: Obtenga información sobre cómo definir criterios de audiencia para indicadores de funcionalidades y grupos de funcionalidades en Despliegues de Adobe Experience mediante atributos de perfil, segmentos y la calculadora de audiencias.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Audiencia en indicadores y grupos de características {#audience-overview}

Los despliegues de experiencias proporcionan una segmentación de audiencia enriquecida para indicadores de funcionalidades y grupos de funcionalidades. Puede combinar atributos de perfil, variables de contexto y segmentos de audiencia para controlar con precisión qué usuarios reciben una función.

## Reglas de perfil {#profile-rules}

Las reglas de perfil le permiten segmentar usuarios según atributos como país, dominio de correo electrónico, tipo de cuenta, ID de usuario, etc. Puede combinar varios atributos mediante los operadores AND/OR y crear una lógica anidada para escenarios de segmentación complejos.

Para agregar reglas de perfil, ve a la pestaña **Audiencia** de un marcador de característica o grupo de características y agrega condiciones en **Perfil**.

Puede guardar un conjunto de reglas de audiencia como una **Audiencia** reutilizable para usarla en varios indicadores y grupos.

Para el direccionamiento basado en el contexto (por ejemplo, segmentar según el idioma activo o el tipo de cliente del usuario), vea [Usar el contexto en las reglas de audiencia](using-context-in-audience-rules.md).

## Segmentos {#segments}

Los indicadores de características y los grupos de características admiten segmentos de audiencia. Los segmentos le permiten:

* Utilizar una sola definición de audiencia predefinida en varios indicadores y grupos de funciones
* Incluya **criterios basados en eventos** en la segmentación de audiencia; algo que no es posible solo con las reglas de perfil

Para usar un segmento, ve a la ficha **Audiencia** y selecciona uno o más segmentos de la lista. Puede combinar varios segmentos utilizando los operadores AND/OR y añadir filtros de perfil o contexto adicionales a lo largo de ellos.

>[!NOTE]
>
>Necesita el rol **Administrador de pruebas** o superior para crear segmentos de audiencia.

## Calculadora de audiencias {#audience-calculator}

Después de definir los criterios de audiencia, seleccione **Calcular** en la barra inferior para obtener un recuento estimado de los usuarios aptos. Esto le ayuda a validar el alcance de la segmentación antes de activar la función.

>[!NOTE]
>
>La calculadora de audiencias no devuelve un valor cuando las variables de contexto se incluyen en los criterios, ya que los valores de contexto se determinan en el tiempo de ejecución y no se pueden predecir por adelantado.

## Consulte también {#see-also}

* [Uso del contexto en las reglas de audiencia](using-context-in-audience-rules.md)
* [Agregar reglas de porcentaje en criterios de audiencia](adding-percentage-rules.md)
* [Reglas de audiencia complejas](complex-rules.md)
* [Creación de la primera marca de funcionalidad](../feature-flags/create-your-first-feature-flag.md)
