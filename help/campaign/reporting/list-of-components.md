---
title: Lista de componentes
description: Aquí encontrará la lista de todos los componentes disponibles en los informes dinámicos, así como sus definiciones.
level: Beginner
audience: end-user
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
source-git-commit: b11d696767209145511b38735f22275a38676ade
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 2%

---

# Lista de componentes {#list-of-components}

Tenga en cuenta que si dos componentes no son compatibles, la celda mostrará el valor **Ninguno**.

## Dimensiones {#dimensions}

La siguiente tabla le proporciona la lista de dimensiones utilizadas en los informes y sus definiciones.

<table> 
 <thead> 
  <tr> 
   <th> Dimension<br/> </th> 
   <th> Definición<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Navegador<br/> </td> 
   <td> Explorador desde el que se abrió o se hizo clic en el mensaje.<br/> </td> 
  </tr> 
  <tr> 
   <td> Campaign<br/> </td> 
   <td> Etiqueta e ID de la campaña.<br/> </td> 
  </tr> 
  <tr> 
   <td> Entrega<br/> </td> 
   <td> Etiqueta e ID de envío.<br/> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo<br/> </td> 
   <td> Dispositivo desde el que se abrió, vio o hizo clic la notificación push/SMS/de correo electrónico.<br/> </td> 
  </tr> 
  <tr> 
   <td> Motivo del error<br/> </td> 
   <td> Tipos de errores que ocasionaban devoluciones para cada entrega; por ejemplo, usuario desconocido, dominio no válido o buzón lleno.<br/> </td> 
  </tr> 
  <tr> 
   <td> Nombre de aplicación móvil<br/> </td> 
   <td> Nombre de la aplicación móvil<br/> </td> 
  </tr>
  <tr> 
   <td> Plataforma<br/> </td> 
   <td> Plataforma del dispositivo desde el que se abrió, visualizó o hizo clic en el mensaje.<br/> </td> 
  </tr> 
  <tr> 
   <td> Perfil<br/> </td> 
   <td> Reagrupa los campos de perfil predeterminados y personalizados creados durante la extensión de recursos de perfil.<br/> </td> 
  </tr> 
  <tr> 
   <td> Dominio del destinatario<br/> </td> 
   <td> Dominio utilizado para abrir el correo electrónico.<br/> </td> 
  </tr> 
  <tr> 
   <td> Entrega recurrente<br/> </td> 
   <td> Etiqueta e ID del envío recurrente.<br/> </td> 
  </tr> 
  <tr> 
   <td> Dominio del remitente<br/> </td> 
   <td> Dominio utilizado para enviar el correo electrónico.<br/> </td> 
  </tr> 
  <tr> 
   <td> IP del remitente<br/> </td> 
   <td> IP utilizada para enviar el correo electrónico.<br/> </td> 
  </tr> 
  <tr> 
   <td> URL de seguimiento<br/> </td> 
   <td> URL en la que el usuario hizo clic desde el mensaje.<br/> </td> 
  </tr> 
  <tr> 
   <td> Categoría de URL de seguimiento<br/> </td> 
   <td> Categoría asignada a la URL de seguimiento.<br/> </td> 
  </tr> 
  <tr> 
   <td> Etiqueta de URL de seguimiento<br/> </td> 
   <td> Etiqueta proporcionada a la dirección URL, como una página espejo, póngase en contacto con nosotros o abra.<br/> </td> 
  </tr> 
  <tr> 
   <td> Envío transaccional<br/> </td> 
   <td> Etiqueta e ID del envío transaccional.<br/> </td> 
  </tr> 
  <tr> 
   <td> Variante<br/> </td> 
   <td> Variante del correo electrónico en el caso de las pruebas A/B.<br/> </td> 
  </tr> 
 </tbody> 
</table>

## Métricas {#metrics}

Las siguientes tablas proporcionan la lista de métricas utilizadas en los informes y sus definiciones según el tipo de envío.

### Métricas de correo electrónico {#email-and-sms-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Métrica<br/> </th> 
   <th> Definición<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> En la lista de bloqueados<br/> </td> 
   <td> Número de destinatarios que han declarado un correo electrónico como no deseado o no deseado.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de Lista de bloqueados de la<br/> </td> 
   <td> Porcentaje de envíos marcados en el momento de la lista de bloqueados de la.<br/> </td> 
  </tr> 
  <tr> 
   <td> Devoluciones + Errores<br/> </td> 
   <td> Total de errores acumulados durante el envío y el procesamiento automático de devoluciones en relación con el número total de mensajes enviados.<br/> </td> 
  </tr> 
  <tr> 
   <td> Devolución + Tasa de error<br/> </td> 
   <td> Porcentaje de correos electrónicos devueltos en comparación con los enviados por correo electrónico.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clic<br/> </td> 
   <td> Número de veces que se hizo clic en un contenido en una entrega.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de pulsaciones<br/> </td> 
   <td> Porcentaje de clics en una entrega.<br/> </td> 
  </tr> 
  <tr> 
   <td> Entrega<br/> </td> 
   <td> Número de mensajes enviados correctamente en relación con el número total de mensajes enviados.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de entrega<br/> </td> 
   <td> Porcentaje de mensajes enviados correctamente.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rechazo duro<br/> </td> 
   <td> Número total de errores permanentes, como una dirección de correo electrónico incorrecta.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de salida hacia otro sitio dura<br/> </td> 
   <td> Porcentaje de envíos que fallaron debido a errores permanentes.<br/> </td> 
  </tr> 
  <tr> 
   <td> Página espejo<br/> </td> 
   <td> Número de destinatarios que hicieron clic en el vínculo de la página espejo.<br/> </td> 
  </tr> 
  <tr> 
   <td> Velocidad de página espejo<br/> </td> 
   <td> Porcentaje de clics en el vínculo de la página espejo comparados con el total de mensajes de envío.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clics de oferta<br/> </td> 
   <td> Número de veces que se hizo clic en una oferta en una entrega.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de pulsaciones de oferta<br/> </td> 
   <td> Porcentaje de clics en una oferta.<br/> </td> 
  </tr> 
  <tr> 
   <td> Apertura<br/> </td> 
   <td> Número de veces que se ha abierto un mensaje en una entrega.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de apertura<br/> </td> 
   <td> Porcentaje de mensajes abiertos.<br/> </td> 
  </tr> 
  <tr> 
   <td> Procesado/enviado<br/> </td> 
   <td> Número total de envíos para el envío.<br/> </td> 
  </tr> 
  <tr> 
   <td> Cuarentena<br/> </td> 
   <td> Número de mensajes que rebotaron y que dieron lugar a la cuarentena de la dirección.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de cuarentena<br/> </td> 
   <td> Porcentaje de cuarentenas comparadas con mensajes enviados.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rechazado<br/> </td> 
   <td> Número de mensajes clasificados como correo no deseado por los servidores SMTP.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de rechazados<br/> </td> 
   <td> Porcentaje de mensajes marcados como rechazados.<br/> </td> 
  </tr> 
  <tr> 
   <td> Rechazo suave<br/> </td> 
   <td> Número total de errores temporales, como una bandeja de entrada llena.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de devoluciones suaves<br/> </td> 
   <td> Porcentaje de envíos que fallaron debido a un motivo temporal.<br/> </td> 
  </tr> 
  <tr> 
   <td> Clics únicos<br/> </td> 
   <td> Número de destinatarios que hicieron clic en un contenido de una entrega.<br/> </td> 
  </tr> 
  <tr> 
   <td> Aperturas únicas<br/> </td> 
   <td> Número de destinatarios que abrieron la entrega.<br/> </td> 
  </tr> 
  <tr> 
   <td> Suscripción única cancelada<br/> </td> 
   <td> Número de destinatarios que hicieron clic en el vínculo de baja de suscripción.<br/> </td> 
  </tr> 
  <tr> 
   <td> Tasa de cancelación de suscripción<br/> </td> 
   <td> Número de bajas únicas comparadas con los mensajes enviados.<br/> </td> 
  </tr> 
  <tr> 
   <td> Cancelado<br/> </td> 
   <td> Número de clics en el vínculo de baja de suscripción.<br/> </td> 
  </tr> 
 </tbody> 
</table>

<!--
### Push notification metrics {#push-notification-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Bounces + Errors<br/> </td> 
   <td> Total of errors cumulated during delivery in relation to the total number of sent messages, e.g. errors from MCPNS or provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Bounce + Error rate<br/> </td> 
   <td> Percentage of push notifications that bounced compared to push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and clicked on by the user. The user either wanted to view the notification, which will then be moved to Push Open tracking, or dismiss it.<br/> </td> 
  </tr> 
  <tr> 
   <td> Click through rate<br/> </td> 
   <td> Percentage of users who interacted with the push notification.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Number of push notifications successfully sent, in relation to the total number of sent push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Delivered rate<br/> </td> 
   <td> Percentage of push notifications successfully sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Number of times a push notification has been delivered to the device and left untouched in the notification center. In most cases, impressions number should be similar to the delivered number. This ensures that the device got the message and relayed that information back to the server.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of push notifications sent.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open<br/> </td> 
   <td> Total number of push notifications delivered to the device and clicked on by users thus opening the app. This is similar to the Push Click except a Push Open will not be triggered if the notification was dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Open rate<br/> </td> 
   <td> Percentage of opened push notifications.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique clicks<br/> </td> 
   <td> Number of times a unique user interacts with the push notification, e.g. clicks on the notification or button.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique Opens<br/> </td> 
   <td> Number of recipients who opened the delivery.<br/> </td> 
  </tr> 
 </tbody> 
</table>

### In-App metrics {#in-app-metrics}

<table> 
 <thead> 
  <tr> 
   <th> Metric<br/> </th> 
   <th> Definition<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivered<br/> </td> 
   <td> Total number of In-App messages delivered to the device by the service provider.<br/> </td> 
  </tr> 
  <tr> 
   <td> Impressions<br/> </td> 
   <td> Total of In-App messages seen by recipients depending on whether trigger criterion was met.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App clicks <br/> </td> 
   <td> Total number of recipients who clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App click through rate<br/> </td> 
   <td> Percentage of users who clicked on Button 1 or Button 2 compared to users who saw the message.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal<br/> </td> 
   <td> Total number of messages that recipients dismissed either by clicking the close button or auto-dismiss.<br/> </td> 
  </tr> 
  <tr> 
   <td> In-App dismissal rate<br/> </td> 
   <td> Percentage of In-App messages that recipients dismissed.<br/> </td> 
  </tr> 
  <tr> 
   <td> Processed/sent<br/> </td> 
   <td> Total number of In-App messages sent from Adobe Campaign as part of the delivery sent process.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique impressions<br/> </td> 
   <td> Number of impressions by a unique recipient.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App clicks<br/> </td> 
   <td> Number of times recipients clicked on Button 1 or Button 2.<br/> </td> 
  </tr> 
  <tr> 
   <td> Unique In-App dismissals<br/> </td> 
   <td> Number of time recipients dismissed an In-App message.<br/> </td> 
  </tr> 
 </tbody> 
</table>
-->

## Segmentos {#segments}

La siguiente tabla le proporciona la lista de segmentos utilizados en los informes y sus definiciones.

<table> 
 <thead> 
  <tr> 
   <th> Segmento<br/> </th> 
   <th> Definición<br/> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Edad: 1<br/> </td> 
   <td> Destinatarios nacidos entre 1946 y 1954.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Boomers 2<br/> </td> 
   <td> Destinatarios nacidos entre 1955 y 1965.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: De 18 a 25 años<br/> </td> 
   <td> Destinatarios de 18 a 25 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: De 26 a 30 años<br/> </td> 
   <td> Destinatarios de 26 a 30 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: De 31 a 40 años<br/> </td> 
   <td> Destinatarios de 31 a 40 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: De 41 a 50 años<br/> </td> 
   <td> Destinatarios de 41 a 50 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Generación X<br/> </td> 
   <td> Destinatarios nacidos entre 1966 y 1976.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Generación Y (Millennials)<br/> </td> 
   <td> Destinatarios nacidos entre 1977 y 1994.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Generación Z<br/> </td> 
   <td> Destinatarios nacidos desde 1995 hasta la actualidad.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Mayor de 50 años<br/> </td> 
   <td> Destinatarios cuya edad es mayor de 50 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Menos de 25 años<br/> </td> 
   <td> Destinatarios cuya edad es menor de 25 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Menos de 30 años<br/> </td> 
   <td> Destinatarios cuya edad es menor de 30 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Menos de 40 años<br/> </td> 
   <td> Destinatarios cuya edad es menor de 40 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Menos de 50 años<br/> </td> 
   <td> Destinatarios cuya edad es inferior a 50 años.<br/> </td> 
  </tr> 
  <tr> 
   <td> Edad: Generación silenciosa<br/> </td> 
   <td> Destinatarios nacidos en 1945 o antes.<br/> </td> 
  </tr> 
  <tr> 
   <td> Todas las visitas<br/> </td> 
   <td> Cada destinatario<br/> </td> 
  </tr>
 </tbody> 
</table>
