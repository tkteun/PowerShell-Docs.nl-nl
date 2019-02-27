---
title: Het maken van een OData-Web-beheerservice | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847248"
---
# <a name="creating-a-management-odata-web-service"></a>Een Management OData-webservice maken

Management ODATA IIS-extensie is een infrastructuur voor het maken van een ASP.NET web service-eindpunt dat wordt aangegeven dat uw beheergegevens, toegankelijk is via Windows PowerShell-cmdlets en scripts, als OData-Web-service-entiteiten. Dit gebeurt dat door de OData-aanvragen verwerkt en deze omzetten in een Windows PowerShell-aanroep. Productteams kunnen bouwen voort op deze infrastructuur om eindpunten die beschikbaar van beheergegevens op specifieke sets maken te maken.

Download en installeer de [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) voorbeeld. Volg de instructies voor het implementeren van de webservice. Deze webservice wordt aangegeven dat Services en -processen via maken, lezen, bijwerken en verwijderen (CRUD)-bewerkingen. CRUD-aanvragen voor de webservice aanroepen Windows PowerShell-opdrachten die de gevraagde bewerkingen uitvoeren. Een toewijzing tussen de CRUD-bewerkingen en de onderliggende Windows PowerShell-opdrachten wordt geïmplementeerd door twee schemabestanden, schema.mof en schema.xml. Het bestand schema.mof gebruikt de [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) beheerde Object (MOF) standaard. Het bestand schema.xml maakt gebruik van een XML-schema dat wordt beschreven in [Resource toewijzen Schema](./resource-mapping-schema.md).

> [!IMPORTANT]
> Voordat u het inschakelen van Management ODATA IIS-extensie op Windows Server 2008 R2 SP1, moeten de volgende functies zijn ingeschakeld.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Stappen voor het maken van een Management OData-webservice

De volgende onderwerpen wordt beschreven hoe u maken en implementeren van een Management OData-webservice.

- [Toevoegen van Resources aan een Management OData-webservice](./adding-resources-to-a-management-odata-web-service.md)

- [Aangepaste autorisatie voor een Management OData-webservice implementeren](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [SessionConfiguration voor een Management OData-webservice implementeren](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Het schema MOF-bestand voor een Management OData-webservice ontwerpen](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Het XML-schemabestand voor een Management OData-webservice ontwerpen](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Het bestand Web.config voor een Management OData-webservice ontwerpen](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Een Management OData-webservice implementeren](./deploying-a-management-odata-web-service.md)

- [Management OData entiteiten koppelen](./associating-management-odata-entities.md)

## <a name="see-also"></a>Zie ook

[Extensieschema voor Management ODATA IIS-bestanden](./management-odata-iis-extension-schema-files.md)
