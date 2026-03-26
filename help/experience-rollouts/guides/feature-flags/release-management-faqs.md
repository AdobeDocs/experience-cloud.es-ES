---
title: Preguntas frecuentes sobre gestión de versiones
description: Encuentre respuestas a preguntas comunes acerca de la administración de versiones en los lanzamientos de Adobe Experience.
exl-id: 802b99bd-85ee-4f4d-afca-88d1297f8782
source-git-commit: 4a3133f014a9bb9d6ed26eb9d9f763db79ce63b3
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 1%

---

# Preguntas frecuentes sobre gestión de versiones {#release-management-faqs}

## ¿Cómo puedo solicitar una versión? {#request-release}

Póngase en contacto con el servicio de asistencia técnica de Despliegues de experiencias para solicitar una versión. Proporcione el nombre de su equipo, los detalles de la aplicación, la audiencia de destino y la cronología de despliegue deseada.

## ¿Qué criterios de audiencia se admiten en las versiones? {#audience-criteria}

Las versiones admiten las siguientes reglas de audiencia:

* Tipo de ID (tipo de cuenta)
* País
* ID de usuario (GUID)
* Dirección de correo electrónico (lista individual o en bloque)
* Dominio de correo electrónico
* IP del cliente
* Porcentaje (todos los usuarios)
* Porcentaje (solo usuarios autenticados)

Puede combinar varias reglas mediante la lógica AND/OR, incluidas las condiciones anidadas.

## ¿Cómo añado una aplicación a una versión? {#onboard-application}

Una vez creada la versión, ábrala en la consola y añada la aplicación a la configuración de la versión. El propietario de la versión del producto de cada aplicación puede añadir los indicadores de funciones relevantes.

## No se devuelve una función para un usuario que deba cumplir los requisitos. ¿Cómo puedo solucionar problemas? {#troubleshoot}

Siga estos pasos para depurar:

1. **Compruebe el estado de la versión.** La versión debe tener el estado **Publicado** o **Despliegue completo** para poder usar las funciones.
2. **Compruebe la aplicación y la marca de características.** Compruebe que se ha creado el indicador de funciones para la aplicación correcta y que la aplicación está asociada a la versión correcta.
3. **Compruebe que la marca de características esté habilitada.** No se mostrará un indicador desactivado aunque la versión esté activa.
4. **Revise los criterios de audiencia.** Confirme que el usuario cumple todas las condiciones definidas en las reglas de audiencia. Compruebe los criterios de la versión específica a la que está asociada la función.

## Consulte también {#see-also}

* [Atención al cliente](../support/contact-support.md)
