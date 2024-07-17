---
title: Activación de una actividad de señal
description: Obtenga información sobre cómo almacenar en déclencheur una actividad de señal con API.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 9f94e98f-fe04-4369-8946-1380e02cdece
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 2%

---

# Activación de una actividad de señal {#triggering-a-signal-activity}

En un flujo de trabajo de Adobe Campaign Standard, puede haber una o más actividades **External signal**. Estas actividades son &quot;oyentes&quot; que esperan a activarse.

Las API de Campaign Standard le permiten almacenar en déclencheur una actividad **Señal externa** para llamar a un flujo de trabajo. La llamada de API puede incluir parámetros que se incorporarán a las variables de eventos del flujo de trabajo (un nombre de audiencia para el destinatario, un nombre de archivo para importar, una parte del contenido del mensaje, etc.). De este modo, puede integrar fácilmente las automatizaciones de Campaign con su sistema externo.

>[!NOTE]
>
>Las actividades de señal externa no se pueden activar con más frecuencia que cada 10 minutos y el flujo de trabajo de destino debe estar ya en ejecución.

Para almacenar en déclencheur un flujo de trabajo, siga los pasos a continuación:

1. Realice una solicitud **GET** en el flujo de trabajo para recuperar la URL del déclencheur de actividad de señal externa.

   `GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID>`

1. Realice una solicitud **POST** en la dirección URL devuelta para almacenar en déclencheur la actividad de señal con el parámetro **&quot;origen&quot;** en la carga. Este atributo es obligatorio, permite indicar el origen de la solicitud que lo activa.

Si desea llamar al flujo de trabajo con parámetros, agréguelos a la carga útil con el atributo **&quot;parameters&quot;**. La sintaxis consiste en el nombre del parámetro seguido de su valor (se admiten los siguientes tipos: **string**, **number**, **boolean** y **date/time**).

```
  -X POST <TRIGGER_URL>
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>' \
  -H 'Content-Type: application/json;charset=utf-8' \
  -H 'Content-Length:79' \
  -i
  -d {
  -d    "source":"<SOURCE>",
  -d    "parameters":{
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>",  
  -d      "<PARAMETER_NAME":"<PARAMETER_VALUE>"
  -d    }
  -d }
```

>[!NOTE]
>
>Al agregar un parámetro a la carga útil, asegúrese de que sus valores **name** y **type** sean coherentes con la información declarada en la actividad Señal externa. Además, el tamaño de la carga útil no debe superar los 64 Ko.

<br/>

***Solicitud de muestra***

Realice una solicitud de GET en el flujo de trabajo.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<workflowID> \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

Devuelve la actividad de señal de flujo de trabajo y la URL de déclencheur asociada.

```
{
"PKey": "<PKEY>",
"activities": {
  "activity": {
    "signal1": {
      ...
      "trigger": {
        "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger/"
        },
        ...
      }
    }
  }
}
```

Para almacenar en déclencheur una actividad de señal, realice una solicitud de POST en la dirección URL de déclencheur con la &quot;fuente&quot;. Agregue los atributos &quot;parameters&quot; si desea llamar al flujo de trabajo con parámetros.

```
-X POST https://mc.adobe.io/<ORGANIZATION>/campaign/workflow/execution/<PKEY>/activities/activity/<PKEY>/trigger \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>' \
-i
-d '{
-d "source":"API",
-d "parameters":{
-d    "audience":"audience",
-d    "email":"anna.varney@mail.com",
-d    "template":"05",
-d    "contentURL":"http://www.adobe.com",
-d    "test":"true",
-d    "segmentCode":"my segment",
-d    "attribute":"2019-04-03 08:17:19.100Z"}
-d  }'
```

<!-- + réponse -->

Si uno de los parámetros no se declara en la actividad Señal externa, la solicitud del POST devuelve el error siguiente, que indica qué parámetro falta.

```
RST-360011 An error has occurred - please contact your administrator.
'contentURL' parameter isn't defined in signal activity.
XTK-170006 Unable to parse expression 'HandleTrigger(@name, $(source), $({parameters}))'.
RST-360000 Error while assessing 'HandleTrigger(@name, $(source), $({parameters}))' expression ('xtk:workflow:execution/activities/signal/trigger' resource)
```
