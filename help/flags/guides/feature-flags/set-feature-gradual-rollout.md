---
title: Configurar una función para que se implemente gradualmente
description: Obtenga información sobre cómo configurar un despliegue gradual basado en porcentajes para una marca de características en Banderas.
hide: true
exl-id: 1e03c533-398d-4a83-9f4a-c0419828b460
source-git-commit: b3e13a42c19eb7b8b7d5d402bf9a56f89f573044
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 3%

---

# Configurar una función para que se implemente gradualmente {#gradual-rollout-feature}

El despliegue porcentual de un indicador de funcionalidad se configura en la ficha **Detalles básicos**. Puede ajustar este valor hacia arriba o hacia abajo en cualquier momento a medida que avanza el despliegue.

## Funcionamiento {#how-it-works}

Cuando establece un porcentaje de despliegue (por ejemplo, el 25 %), ese porcentaje de la audiencia definida se expone a la función. El porcentaje restante se coloca en el **grupo de control**, que recibe la experiencia predeterminada.

Puede aumentar o disminuir el porcentaje con el tiempo para expandir o contraer el despliegue. Si se reduce el porcentaje al 0 %, la función se desactiva para todos los miembros de la audiencia sin eliminar el indicador.

## Consulte también {#see-also}

* [Despliegue gradual](../../concepts/gradual-rollout.md)
* [Configuración de un grupo de funciones para su despliegue gradual](set-feature-group-gradual-rollout.md)
* [Creación de la primera marca de funcionalidad](create-your-first-feature-flag.md)

<!-- -->
