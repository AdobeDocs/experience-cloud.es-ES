---
title: Interacción con recursos personalizados
description: Obtenga más información sobre la administración de recursos personalizados con API/
audience: developing
content-type: reference
topic-tags: campaign-standard-apis
role: Data Engineer
level: Experienced
badge: label="DISPONIBILIDAD LIMITADA" type="Informative" url="../campaign-standard-migration-home.md" tooltip="Restringido a usuarios migrados por el Campaign Standard"
exl-id: 19bfeecb-da60-479c-a929-0cfb72ef59e3
source-git-commit: 3f4400f24b75e8e435610afbe49e9d9444dbf563
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Interacción con recursos personalizados {#interacting-with-custom-resources}

El **/customResources** Este punto de conexión le permite exponer los recursos personalizados de Campaign en REST. En función de esta API, hay disponible una integración entre entidades personalizadas y extremos externos.

El extremo /customResources tiene exactamente el mismo comportamiento que el extremo /profileAndServices.

Los recursos personalizados que se exponen dentro de esta API son los siguientes:

* todas las entidades que no se exponen en /profileAndServicesExt
* todas las entidades que no están vinculadas al perfil y, para estas entidades, sus hijos y nietos.
* de forma predeterminada, todas las entidades que no están vinculadas a nada, y sus hijos y nietos.

>[!NOTE]
>Los recursos personalizados disponibles en /profileAndServicesExt no se exponen en la API /customResources.


A continuación, se muestra un ejemplo para recuperar los metadatos de un recurso personalizado:

```
GET /customResources/resourceType/<customResourceName>
```

Para realizar una creación, actualización o eliminación, se utilizan el GET, el POST, el PATCH y el DELETE.

```
POST /customResources/<customResourceName>
```
