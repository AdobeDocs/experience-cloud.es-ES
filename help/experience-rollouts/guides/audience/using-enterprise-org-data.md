---
title: Uso de datos de organización empresarial en reglas de audiencia
description: Aprenda a utilizar los ID de organización empresarial como criterios de audiencia en los lanzamientos de Adobe Experience para segmentar organizaciones de clientes específicas.
exl-id: 74f97ec7-a809-41bf-a41d-bb57f033040f
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 1%

---

# Uso de datos de organización empresarial en reglas de audiencia {#enterprise-org-data}

Los despliegues de experiencias admiten la segmentación de usuarios en función de su ID de organización empresarial (org). Esto le permite implementar funciones para organizaciones de clientes específicas antes de que estén disponibles en todo el mundo.

## Adición de una organización en una regla de audiencia {#adding-org-rule}

El direccionamiento de organización empresarial está disponible en la ficha **Audiencia** en **Reglas de audiencia > Perfil > Empresa**.

Se admiten dos tipos de organización:

### Organizaciones DME {#dme-orgs}

Las organizaciones de DME se identifican por su identificador de organización. Al crear la regla, introduzca solo el ID de organización de (no incluya un origen de autenticación).

### Organizaciones DMA {#dma-orgs}

Las organizaciones de DMA utilizan ID de organización con el formato `XXXXXXXXXXXXXXXXXXXXXXXX@ADOBEORG`. Al introducir un ID de organización de DMA:

* Utilice el identificador de organización completo, incluido el sufijo `@ADOBEORG`.
* Escriba `ADOBEORG` en mayúsculas.

**Ejemplo:** `57F22B5D5A5F83AE0A495E6E@ADOBEORG`

## Notas importantes {#important-notes}

* La segmentación basada en organización se evalúa según la organización asociada con la sesión autenticada del usuario. Asegúrese de que el usuario ha iniciado sesión en la organización correcta al realizar la prueba.
* Si una organización que espera encontrar no aparece en los criterios de audiencia o si las funciones no se devuelven como se espera para una organización específica, póngase en contacto con el servicio de asistencia de los despliegues de experiencias.
* Los entornos de fase y producción pueden diferir en las organizaciones disponibles. Pruebe las reglas de audiencia en Fase antes de pasar a Producción.

## Consulte también {#see-also}

* [Audiencia en indicadores y grupos de características](audience-in-feature-flags-and-feature-groups.md)
* [Reglas de audiencia complejas](complex-rules.md)
