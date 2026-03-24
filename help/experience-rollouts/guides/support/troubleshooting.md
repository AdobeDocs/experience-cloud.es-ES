---
title: Solución de problemas
description: Utilice el área de trabajo Despliegues de experiencias para diagnosticar problemas de evaluación de indicadores de características para usuarios específicos, incluida la comprobación de qué características están habilitadas, deshabilitadas o no coinciden para una identidad de usuario determinada.
source-git-commit: d824d85c6701edc9be314713bb8e9624b183e2d2
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---


# Solución de problemas {#troubleshooting}

Los despliegues de experiencias incluyen una herramienta de diagnóstico integrada llamada **Área de trabajo de características** que le ayuda a comprender exactamente qué indicadores de características recibe un usuario específico y por qué. Utilícela para investigar informes sobre comportamientos de funciones inesperados sin necesidad de reproducir problemas en el código de.

## Acceso a Workbench de funciones {#access-workbench}

Para abrir el Área de trabajo de funciones, siga estos pasos:

1. Inicie sesión en la consola Despliegues de experiencias.
2. Vaya a **Workbench > Usuarios finales** desde el menú superior.
3. Seleccione la ficha **Características**.

## Introducir una identidad de usuario {#input-identity}

Para buscar evaluaciones de indicadores de funciones para un usuario específico, introduzca la siguiente información en el formulario de Workbench:

* **Tipo de identificador**: seleccione el tipo de identificador que está utilizando. Los tipos compatibles incluyen correo electrónico, GUID e ID de visitante. También puede ingresar un **indicador de versión** directamente para buscar qué versiones se habilitaron para un usuario en función de su valor de indicador.
* **Valor de identificador**: escriba el identificador del usuario. Si selecciona correo electrónico como tipo de ID, tenga en cuenta que se pueden asociar varios GUID con la misma dirección de correo electrónico. Se proporciona un menú desplegable de GUID para que pueda cambiar entre GUID asociados.
* **Tipo de origen de autenticación**: seleccione si corresponde a su integración.
* **Variables de contexto**: proporcione opcionalmente pares de clave-valor de contexto que afecten a la evaluación de reglas de audiencia (por ejemplo, país, tipo de dispositivo).
* **Equipo y aplicación**: seleccione el equipo y la aplicación para los que desea recuperar indicadores de características. Su equipo actual y una de sus aplicaciones están preseleccionadas de forma predeterminada.

Después de rellenar el formulario, seleccione **Buscar características**.

## Interpretación de los resultados {#interpret-results}

Los resultados dependen del tipo de ID que haya introducido.

### Búsqueda de correo electrónico o GUID {#email-guid-lookup}

Cuando busca un usuario por correo electrónico o GUID, aparecen dos secciones en los resultados:

**Indicadores de liberación**

Esta sección muestra tres listas para el equipo y la aplicación seleccionados:

* **Habilitado** — Versiones actualmente activas para este usuario.
* **Deshabilitado**: versiones que existen pero no están habilitadas para este usuario.
* **Sin usar**: bits de versión que no tienen ninguna versión adjunta a ellos.

Las versiones asociadas con el equipo y la aplicación seleccionados aparecen en la parte superior de cada lista.

**Indicadores de características y grupos**

En esta sección se muestran todos los indicadores de funcionalidades del equipo y la aplicación seleccionados que están actualmente habilitados para el usuario. Cada entrada muestra:

* Clave y nombre de indicador de funcionalidad
* Grupo de funciones (si el indicador pertenece a uno)
* Variante (si está configurada la prueba A/B)
* Si el indicador está vinculado a la audiencia

También puede seleccionar **Mostrar solicitud/respuesta** para inspeccionar la solicitud y la respuesta de API exactas que produjeron los resultados.

### Correo electrónico no automático o ID sin GUID {#non-self-lookup}

Cuando el correo electrónico especificado no es suyo, o cuando se usa un tipo de ID que no es GUID, solo se muestra la sección **Indicadores de características y grupos**.

### Búsqueda de marcas de versión {#release-flag-lookup}

Cuando se introduce una **marca de liberación** como tipo de ID, solo se muestra la sección **marcas de liberación**, en la que se enumeran las versiones que se habilitaron y deshabilitaron para el usuario asociado con esa marca.

## Problemas comunes {#common-issues}

En la tabla siguiente se describen problemas comunes y cómo investigarlos mediante Workbench.

| Síntoma | Qué comprobar |
|---|---|
| El usuario no recibe un indicador de funcionalidad que deba | Compruebe la selección del equipo y la aplicación. Compruebe que el ID del usuario coincida con el tipo de regla de audiencia (correo electrónico, GUID, etc.). Confirme que la característica tiene el estado **Publicar** o **Despliegue completo**. |
| La función está habilitada para todos los usuarios de forma inesperada | Confirme que la función no tiene reglas de audiencia aplicadas o que el porcentaje está establecido en 100%. Compruebe si la característica tiene el estado **Despliegue completo**. |
| La regla de audiencia no coincide | Utilice Workbench con variables de contexto para confirmar que los valores pasados en tiempo de ejecución coinciden con lo configurado en la regla de audiencia. |
| El estado del indicador de funcionalidad es correcto, pero el usuario sigue viendo el comportamiento antiguo | Compruebe el TTL configurado para la aplicación. SDK almacena en caché los datos de las funciones y solo se actualiza en el intervalo de sondeo configurado. |

## Consulte también {#see-also}

* [Obtener asistencia técnica](get-support.md)
* [Atención al cliente](contact-support.md)
* [Actualizar reglas de audiencia de lanzamiento](../feature-flags/update-release-audience-rules.md)
* [Estados de versión](../feature-flags/release-states.md)
