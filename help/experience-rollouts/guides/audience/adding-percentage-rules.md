---
title: Agregar reglas de porcentaje en criterios de audiencia
description: Aprenda a añadir reglas basadas en porcentajes dentro de los criterios de audiencia en los despliegues de Adobe Experience para dirigirse a diferentes porcentajes de despliegue para diferentes segmentos de audiencia.
exl-id: 15a3c26f-31fc-4e73-aa0e-035dcbe7d770
source-git-commit: fcb1d36fc92b3954a902d818a98f579672c577e9
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# Agregar reglas de porcentaje en criterios de audiencia {#adding-percentage-rules}

## Cuándo usar reglas de porcentaje en la pestaña Audiencia {#when-to-use}

El campo **despliegue porcentual** de la ficha Detalles básicos aplica un solo porcentaje a toda la audiencia. Por ejemplo, un 50 % de despliegue significa que el 50 % de todos los usuarios que cumplan los criterios de audiencia recibirán la función.

Sin embargo, algunos escenarios de despliegue requieren porcentajes diferentes para grupos diferentes; por ejemplo:

* 100% de los usuarios del Reino Unido y 50% de los usuarios de Estados Unidos
* Todos los usuarios de una lista de correo electrónico importada, más el 50 % de los usuarios de un país específico

En estos casos, use la regla **Percentage** en la sección de contexto de la pestaña **Audience**, combinada con lógica anidada.

>[!TIP]
>
>Si desea aplicar un solo porcentaje a toda la audiencia (por ejemplo, el 10 % de los usuarios en EE. UU. y Reino Unido), use el **despliegue porcentual** en la pestaña Detalles básicos.

## Cómo añadir una regla de porcentaje {#how-to-add}

La opción **Percentage** está disponible como regla en la sección de contexto de la pestaña Audiencia.

1. Vaya a la ficha **Audiencia** de su indicador o grupo de características.
2. En **Audiencia**, agregue una regla de **Porcentaje de contexto** y establezca el valor deseado.
3. Añada cualquier otra condición de audiencia que necesite (por ejemplo, una regla de país).

## Combinación de reglas de porcentaje con lógica anidada {#nested-logic}

Para aplicar porcentajes diferentes a segmentos diferentes, use **lógica anidada** para combinar las condiciones:

1. Habilite **Lógica anidada** en la sección de reglas de audiencia.
2. A cada condición se le asigna un número automáticamente.
3. Introduzca una expresión lógica que haga referencia a esos números.

Utilice una de las siguientes expresiones para describir la relación entre las condiciones:

* `1 and (2 or 3)` — condición 1 AND (condición 2 O condición 3)
* `(1 and 2) or 3` — (condición 1 Y condición 2) O condición 3
* `(1 and 2) or (3 and 4)` — dos grupos independientes

## Ejemplos {#examples}

**Ejemplo 1: Todos los usuarios de una lista importada y el 10% de los usuarios de un país específico**

Añada dos reglas: una para la lista de usuarios importada y una regla de porcentaje (10 %) combinada con una regla de país. Usar lógica anidada: `1 or (2 and 3)`.

**Ejemplo 2: 10% de usuarios de EE. UU. y 20% de usuarios de Reino Unido**

Añada cuatro reglas: País = EE. UU., Porcentaje = 10 %, País = Reino Unido, Porcentaje = 20 %. Usar lógica anidada: `(1 and 2) or (3 and 4)`.

## Consulte también {#see-also}

* [Audiencia en indicadores y grupos de características](audience-in-feature-flags-and-feature-groups.md)
* [Reglas de audiencia complejas](complex-rules.md)
* [Configurar una función para que se implemente gradualmente](../feature-flags/set-feature-gradual-rollout.md)
