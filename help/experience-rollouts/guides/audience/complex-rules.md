---
title: Reglas de audiencia complejas
description: Aprenda a trabajar con conjuntos de reglas de audiencia grandes o complejos en los lanzamientos de Adobe Experience, incluidos los límites de valor masivo y cómo dividir reglas en varias condiciones.
exl-id: 37e037b6-45eb-4261-b580-30d94d8e55da
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Reglas de audiencia complejas {#complex-rules}

## Límites de valores masivos {#bulk-value-limits}

Al agregar un gran número de valores a una sola regla de audiencia (por ejemplo, una larga lista de direcciones de correo electrónico), puede encontrar un error que indique que la regla ha superado el tamaño máximo permitido.

Cada regla de audiencia tiene un límite de tamaño por atributo. En el caso de las direcciones de correo electrónico, el límite depende de la longitud total de caracteres de las entradas, en lugar de un recuento fijo. Como guía general, use aproximadamente **100-115 direcciones de correo electrónico por regla**.

Si necesita dirigirse a más entradas de las que este límite permite, divida la lista en fragmentos más pequeños y aplíquelas como condiciones independientes conectadas mediante una lógica anidada.

## Uso de lógica anidada para reglas complejas {#nested-logic}

La lógica anidada permite combinar varias condiciones de audiencia con un control AND/OR preciso. Para habilitarlo:

1. Añada las condiciones de audiencia que necesite.
2. Habilite **Lógica anidada** en la sección de reglas de audiencia.
3. Cada condición tiene asignado un número. Introduzca una expresión lógica que haga referencia a estos números, por ejemplo:
   * `1 and (2 or 3)`
   * `(1 and 2) or 3`
   * `(1 and 2) or (3 and 4)`

Es el mismo mecanismo que se utiliza para las reglas de porcentaje en combinación con otros criterios. Consulte [Agregar reglas de porcentaje en los criterios de audiencia](adding-percentage-rules.md) para ver ejemplos prácticos.

## Consulte también {#see-also}

* [Audiencia en indicadores y grupos de características](audience-in-feature-flags-and-feature-groups.md)
* [Agregar reglas de porcentaje en criterios de audiencia](adding-percentage-rules.md)
