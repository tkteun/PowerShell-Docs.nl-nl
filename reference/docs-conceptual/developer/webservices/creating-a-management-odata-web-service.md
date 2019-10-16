---
title: Een beheer-OData-webservice maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352218"
---
# <a name="creating-a-management-odata-web-service"></a>Een Management OData-webservice maken

Beheer ODATA IIS-extensie is een infra structuur voor het maken van een ASP.NET-eind punt voor webservices waarmee uw beheer gegevens, toegankelijk via Windows Power shell-cmdlets en-scripts, worden weer gegeven als OData-webservice-entiteiten. Dit doet u door OData-aanvragen te verwerken en deze te converteren naar een Windows Power shell-aanroep. Product teams kunnen op deze infra structuur bouwen om eind punten te maken die specifieke sets beheer gegevens beschikbaar stellen.

Down load en installeer het [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -voor beeld. Volg de instructies voor het implementeren van de webservice. Met deze webservice worden services en processen beschikbaar gesteld via Create-, Read-, update-en delete-bewerkingen (ruw). RUWE aanvragen voor de webservice roepen Windows Power shell-opdrachten aan waarmee de aangevraagde bewerkingen worden uitgevoerd. Een toewijzing tussen de ruwe bewerkingen en de onderliggende Windows Power shell-opdrachten wordt geïmplementeerd door twee schema bestanden: schema. mof en schema. XML. Het bestand schema. MOF maakt gebruik van de [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) Managed object (MOF) standaard. Het schema. XML-bestand maakt gebruik van een XML-schema dat wordt beschreven in het [resource toewijzings schema](./resource-mapping-schema.md).

> [!IMPORTANT]
> Voordat u de beheer-ODATA IIS-extensie inschakelt in Windows Server 2008 R2 SP1, moeten de volgende functies zijn ingeschakeld.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Stappen voor het maken van een management OData-webservice

In de volgende onderwerpen wordt beschreven hoe u een management OData-webservice maakt en implementeert.

- [Resources toevoegen aan een management OData-webservice](./adding-resources-to-a-management-odata-web-service.md)

- [Aangepaste autorisatie implementeren voor een management OData-webservice](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [SessionConfiguration implementeren voor een management OData-webservice](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Het MOF-schema bestand voor een management OData-webservice ontwerpen](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Het XML-schema bestand voor een management OData-webservice ontwerpen](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Het web. config-bestand voor een management OData-webservice ontwerpen](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Een management OData-webservice implementeren](./deploying-a-management-odata-web-service.md)

- [Beheer OData-entiteiten koppelen](./associating-management-odata-entities.md)

## <a name="see-also"></a>Zie ook

[Schema bestanden ODATA IIS-extensie beheer](./management-odata-iis-extension-schema-files.md)
