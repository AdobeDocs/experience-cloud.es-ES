---
title: Regla de audiencia con variable de contexto IP de cliente
description: Aprenda a utilizar la variable de contexto IP del cliente en reglas de audiencia en los lanzamientos de Adobe Experience, incluida la compatibilidad con direcciones IP, bloques CIDR e intervalos de red.
source-git-commit: 3f3f7145b3c58dc721cbeb850e9e8571e3255bb1
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 1%

---


# Regla de audiencia con variable de contexto IP de cliente {#clientip-rule}

La variable de contexto `clientip` le permite dirigirse a los usuarios según su dirección IP de cliente. Esto resulta útil para restringir o habilitar características basadas en la red desde la que los usuarios acceden a la aplicación; por ejemplo, limitar el acceso anticipado a los usuarios de una red corporativa.

## Tipos de entrada admitidos {#input-types}

La variable de contexto `clientip` admite tres tipos de valores de entrada:

| Tipo de entrada | Descripción | Operadores admitidos |
|---|---|---|
| **Dirección IP** | Una sola dirección IPv4 o IPv6 | Es, No es igual a, En |
| **Bloque CIDR** | Un intervalo de direcciones IP en notación CIDR (por ejemplo, `192.168.1.0/24`) | Is, In, Is not equal to |
| **Intervalo de red** | Un intervalo de red con nombre predefinido que mantiene la plataforma | Es parte de |

## Adición de una regla IP de cliente {#adding-rule}

1. Abra la marca de características, el grupo de características o el grupo de características entre equipos en la consola.
2. Vaya a la ficha **Audiencia**.
3. En **Contexto**, agregue una condición con la variable **clientip**.
4. Seleccione el operador e introduzca el valor (dirección IP, bloque CIDR o seleccione un intervalo de red predefinido).

## Consulte también {#see-also}

* [Uso del contexto en las reglas de audiencia](using-context-in-audience-rules.md)
* [Audiencia en indicadores y grupos de características](audience-in-feature-flags-and-feature-groups.md)
* [Reglas de audiencia complejas](complex-rules.md)
