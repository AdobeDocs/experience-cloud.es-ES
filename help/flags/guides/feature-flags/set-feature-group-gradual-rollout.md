---
title: Configuración de un grupo de funciones para su despliegue gradual
description: Obtenga información sobre cómo configurar un despliegue gradual basado en porcentajes para un grupo de funciones en Banderas.
hide: true
exl-id: fcf187f1-2f33-4e3a-b740-985d5bc0bcdc
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 3%

---

# Configuración de un grupo de funciones para su despliegue gradual {#gradual-rollout-feature-group}

El porcentaje de despliegue de un grupo de características se ha configurado en la ficha **Detalles básicos**. Puede ajustar este valor hacia arriba o hacia abajo en cualquier momento a medida que avanza el despliegue.

## Funcionamiento {#how-it-works}

Cuando establece un porcentaje de despliegue (por ejemplo, el 60 %), ese porcentaje de la audiencia definida se expone al grupo de funciones. El 40% restante se coloca en el **grupo de control**, que recibe el comportamiento predeterminado.

Si ha configurado varias variantes (para pruebas A/B), el porcentaje de exposición se distribuye equitativamente entre las variantes. Por ejemplo, el 60 % de exposición con tres variantes resulta en un 20 % por variante, con un 40 % en el grupo de control.

Puede aumentar o disminuir el porcentaje en cualquier momento para expandir, reducir o pausar el despliegue.

## Consulte también {#see-also}

* [Creación de un grupo de funciones](create-a-feature-group.md)
* [Pruebas A/B con indicadores de funcionalidades](a-b-testing.md)
* [Despliegue gradual](../../concepts/gradual-rollout.md)

<!-- -->
