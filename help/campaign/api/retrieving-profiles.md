---
title: Recuperación de perfiles
description: Obtenga más información sobre cómo recuperar perfiles con API
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 19679804-f728-49fa-b26e-8f31b67c29bf
source-git-commit: 14d8cf78192bcad7b89cc70827f5672bd6e07f4a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 4%

---

# Recuperación de perfiles con API {#retrieving-profiles}

La recuperación de perfiles se realiza con una solicitud **GET**.

A continuación, puede restringir la búsqueda mediante filtros, pedidos y paginación. Para obtener más información, consulte la sección [Operaciones adicionales](sorting.md).

Además, las API de Campaign Standard le permiten buscar perfiles en función de uno de estos campos: correo electrónico, nombre, apellidos o cualquier campo personalizado. Para obtener más información, consulte [esta sección](#searching-field).

<br/>

***Solicitudes de muestra***

* Solicitud de GET de muestra para recuperar todos los perfiles.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Respuesta a la solicitud.

  ```
  {
      "content": [
          {
              "PKey": "<PKEY>",
              "firstName": "John",
              "lastName":"Doe",
              "birthDate": "1980-10-24",
              ...
          },
          ...
  }
  ```

* Solicitud de GET de muestra para recuperar los 10 primeros valores de correo electrónico.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10 \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

  Respuesta a la solicitud. El nodo &quot;siguiente&quot; devuelve la dirección URL que le permite acceder a los 10 valores de correo electrónico siguientes.

  ```
  {
  "content": [
      "amy.dakota@mail.com",
      "kristen.smith@mail.com",
      "omalley@mail.com",
      "xander.harrys@mail.com",
      "jane.summer@mail.com",
      "gloria.boston@mail.com",
      "edward.snow@mail.com",
      "dorian.simons@mail.com",
      "peter.paolini@mail.com",
      "mingam+test08@adobe.com"
  ],
  "next": {
      "href": "https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/email?_lineCount=10&_
      lineStart=@Qy2MRJCS67PFf8soTf4BzF7BXsq1Gbkp_e5lLj1TbE7HJKqc"
  }
  }
  ```

## Búsqueda de perfiles basados en un campo {#searching-field}

El parámetro **[!UICONTROL filterType]** le permite recuperar perfiles basados en uno de estos campos: correo electrónico, nombre, apellidos o cualquier campo personalizado que se haya agregado en el filtrado avanzado al ampliar el recurso de perfil.

>[!NOTE]
>
>Las búsquedas distinguen entre mayúsculas y minúsculas y solo se realizan en prefijos. Por ejemplo, no podrá buscar un perfil con las últimas letras de su apellido.

***Solicitudes de muestra***

* Solicitud de muestra para filtrar perfiles sobre la base del nombre.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John&filterType=firstName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Solicitud de muestra para filtrar perfiles según el apellido.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=Miller&filterType=lastName \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Solicitud de muestra para filtrar perfiles según el correo electrónico.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile/byText?text=John%40gmail.com&filterType=email \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```

* Solicitud de muestra para filtrar perfiles en función del campo personalizado &quot;Afición&quot;.

  ```
  -X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServicesExt/profile/byText?cusHobby=Dancing&filterType=Hobby \
  -H 'Content-Type: application/json' \
  -H 'Authorization: Bearer <ACCESS_TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'X-Api-Key: <API_KEY>'
  ```
