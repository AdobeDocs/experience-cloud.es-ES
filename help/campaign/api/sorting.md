---
title: Clasificación
description: Obtenga más información sobre cómo realizar operaciones de ordenación
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 7db25b8d-a6f1-4151-bf37-c47e9991ae48
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 10%

---

# Clasificación

La ordenación está disponible de forma predeterminada en orden ascendente. Para ordenar en orden descendente, agregue **%20desc** a la **_order** valor del parámetro.

Para saber si un campo se puede ordenar, compruebe el parámetro &quot;ordenable&quot; en los metadatos del recurso. Para obtener más información, consulte [esta sección](metadata-mechanism.md).

<br/>

***Solicitudes de ejemplo***

* Solicitud de GET de ejemplo para recuperar correos electrónicos en la base de datos ordenados alfabéticamente.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Respuesta a la solicitud.

  ```
  {
  "content": [
      "adam@email.com",
      "allison.durance@example.com",
      "amy.dakota@mail.com",
      "andrea.johnson@mail.com",
      ...
  ]
  ...
  }
  ```

* Solicitud de GET de ejemplo para recuperar el correo electrónico en la base de datos en orden alfa descendente.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_order=email%20desc \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Respuesta a la solicitud.

  ```
  {
  "content": [
      "tombinder@example.com",
      "tombinder@example.com",
      "timross@example.com",
      "john.smith@example.com",
      ...
  ]
  }
  ```
