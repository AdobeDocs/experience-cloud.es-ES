---
title: Configuración del acceso a la API
description: Obtenga información sobre cómo configurar el acceso a las API de Campaign Standard.
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: 84b72258789ba61016deb813e93bdca0ea142712
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 31%

---

# Configuración del acceso a API {#setting-up-api-access}

El acceso a la API de Adobe Campaign Standard se configura mediante los pasos siguientes. Cada uno de estos pasos se detalla en [Documentación de Adobe Developer](https://developer.adobe.com/developer-console/docs/guides/#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md).

>[!IMPORTANT]
>
>Para administrar certificados en [Adobe Developer](https://developer.adobe.com/), asegúrese de que tiene **Administrador del sistema** derechos de la organización o [cuenta de desarrollador](https://helpx.adobe.com/es/enterprise/using/manage-developers.html) en el Admin Console.

1. **Compruebe que tiene un certificado digital** o créese uno si es necesario. Las claves pública y privada proporcionadas con el certificado son necesarias en los siguientes pasos.
1. **Cree una nueva integración con el servicio de Adobe Campaign** in [Adobe Developer](https://developer.adobe.com/) y configúrelo. A continuación, se generarán sus credenciales (clave de API, secreto de cliente...).
1. **Cree un token web JSON (JWT)** a partir de las credenciales generadas anteriormente y firme con la clave privada. El JWT codifica toda la información de identidad y seguridad que necesita el Adobe para comprobar su identidad y concederle acceso a la API.

   >[!IMPORTANT]
   >
   >JWT (JSON Web Tokens) está actualmente en desuso y se está reemplazando por OAuth. La transición se está llevando a cabo de forma progresiva en las próximas versiones de Campaign. Las credenciales de la cuenta de servicio (JWT) se han marcado como obsoletas y seguirán funcionando hasta el 27 de enero de 2025. Por lo tanto, debe migrar la aplicación o integración para utilizar la nueva credencial de servidor a servidor OAuth antes del 27 de enero de 2025. Se prefiere la autenticación OAuth. Encontrará todos los elementos para migrar de la autenticación JWT a la autenticación OAuth en estas páginas:
   >* [Migración](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/)
   >* [Implementación](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/)
   >* [Preguntas frecuentes sobre JWT en desuso](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/faqs/)

1. **Intercambio del JWT por un token de acceso** a través de una solicitud de POST. Este token de acceso debe utilizarse en cada encabezado de sus solicitudes de API.

Para establecer una sesión segura de API de Adobe I/O de servicio a servicio, cada solicitud a un servicio de Adobe debe incluir la información siguiente en el encabezado Autorización.

```
-X GET https://mc.adobe.io/<ORGANIZATION>/campaign/profileAndServices/profile \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer <ACCESS_TOKEN>' \
-H 'Cache-Control: no-cache' \
-H 'X-Api-Key: <API_KEY>'
```

* **&lt;organization>**: Este es su ID de ORGANIZACIÓN personal, el Adobe proporciona un ID de ORGANIZACIÓN para cada una de las instancias

   * &lt;organization> : su instancia de producción,
   * &lt;organization-mkt-stage>: su instancia de fase.

  Para obtener el valor del ID de organización, consulte con su administrador o contacto técnico de Adobe. También puede recuperarla en Adobe I/O al crear una nueva integración, en la lista de licencias (consulte la <a href="https://developer.adobe.com/developer-console/docs/guides/authentication/">Documentación de Adobe Developer</a>).

* **&lt;access_token>**: el token de acceso personal, que se recuperó al intercambiar el token web JSON a través de una solicitud de POST.

* **&lt;API_KEY>**: su clave de API personal. Se proporciona en Adobe I/O después de crear una nueva integración con el servicio de Adobe Campaign.

  ![texto alternativo](assets/tenant.png)

## Resolución de problemas

Durante la integración de AdobeIO, si aparece el siguiente error:

```
{ 
"code": 502, 
"message": "Oops. Something went wrong. Check your URI and try again." 
}
```


Póngase en contacto con el administrador o con el contacto técnico del Adobe para comprobar si el parámetro CNAME se crea correctamente.
