---
title: Preguntas frecuentes sobre gestión de versiones
description: Encuentre respuestas a preguntas comunes acerca de la administración de versiones en los lanzamientos de Adobe Experience.
source-git-commit: d311efb995b20ffc17370d68d57dd84a8605896c
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 1%

---


# Preguntas frecuentes sobre gestión de versiones {#release-management-faqs}

## ¿Cómo puedo solicitar una versión? {#request-release}

Consulte [Solicitar una versión](request-a-release.md) para ver el proceso completo y la información que necesita proporcionar.

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

Puede combinar varias reglas mediante la lógica AND/OR, incluidas las condiciones anidadas. Consulte [Actualizar las reglas de audiencia de la versión](update-release-audience-rules.md) para obtener instrucciones de configuración detalladas.

## ¿Cómo añado una aplicación a una versión? {#onboard-application}

Una vez creada la versión, ábrala en la consola y añada la aplicación a la configuración de la versión. El propietario de la versión del producto de cada aplicación puede añadir los indicadores de funciones relevantes. Consulte [Lanzar flujo de trabajo de extremo a extremo](release-workflow-end-to-end.md) para ver la secuencia completa.

## No se devuelve una función para un usuario que deba cumplir los requisitos. ¿Cómo puedo solucionar problemas? {#troubleshoot}

Siga estos pasos para depurar:

1. **Compruebe el estado de la versión.** La versión debe tener el estado **Publicado** o **Despliegue completo** para poder usar las funciones. Consulte [Estados de la versión](release-states.md).
2. **Compruebe la aplicación y la marca de características.** Compruebe que se ha creado el indicador de funciones para la aplicación correcta y que la aplicación está asociada a la versión correcta.
3. **Compruebe que la marca de características esté habilitada.** No se mostrará un indicador desactivado aunque la versión esté activa.
4. **Revise los criterios de audiencia.** Confirme que el usuario cumple todas las condiciones definidas en las reglas de audiencia. Compruebe los criterios de la versión específica a la que está asociada la función.

## Consulte también {#see-also}

* [Solicitar una versión](request-a-release.md)
* [Actualizar reglas de audiencia de lanzamiento](update-release-audience-rules.md)
* [Estados de versión](release-states.md)
* [Flujo de trabajo de la versión de extremo a extremo](release-workflow-end-to-end.md)
