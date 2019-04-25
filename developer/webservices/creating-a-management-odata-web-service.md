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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080693"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="83e09-102">Een Management OData-webservice maken</span><span class="sxs-lookup"><span data-stu-id="83e09-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="83e09-103">Management ODATA IIS-extensie is een infrastructuur voor het maken van een ASP.NET web service-eindpunt dat wordt aangegeven dat uw beheergegevens, toegankelijk is via Windows PowerShell-cmdlets en scripts, als OData-Web-service-entiteiten.</span><span class="sxs-lookup"><span data-stu-id="83e09-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="83e09-104">Dit gebeurt dat door de OData-aanvragen verwerkt en deze omzetten in een Windows PowerShell-aanroep.</span><span class="sxs-lookup"><span data-stu-id="83e09-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="83e09-105">Productteams kunnen bouwen voort op deze infrastructuur om eindpunten die beschikbaar van beheergegevens op specifieke sets maken te maken.</span><span class="sxs-lookup"><span data-stu-id="83e09-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="83e09-106">Download en installeer de [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="83e09-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="83e09-107">Volg de instructies voor het implementeren van de webservice.</span><span class="sxs-lookup"><span data-stu-id="83e09-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="83e09-108">Deze webservice wordt aangegeven dat Services en -processen via maken, lezen, bijwerken en verwijderen (CRUD)-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="83e09-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="83e09-109">CRUD-aanvragen voor de webservice aanroepen Windows PowerShell-opdrachten die de gevraagde bewerkingen uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="83e09-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="83e09-110">Een toewijzing tussen de CRUD-bewerkingen en de onderliggende Windows PowerShell-opdrachten wordt geïmplementeerd door twee schemabestanden, schema.mof en schema.xml.</span><span class="sxs-lookup"><span data-stu-id="83e09-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="83e09-111">Het bestand schema.mof gebruikt de [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) beheerde Object (MOF) standaard.</span><span class="sxs-lookup"><span data-stu-id="83e09-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="83e09-112">Het bestand schema.xml maakt gebruik van een XML-schema dat wordt beschreven in [Resource toewijzen Schema](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="83e09-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83e09-113">Voordat u het inschakelen van Management ODATA IIS-extensie op Windows Server 2008 R2 SP1, moeten de volgende functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="83e09-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="83e09-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="83e09-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="83e09-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="83e09-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="83e09-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="83e09-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="83e09-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="83e09-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="83e09-118">Stappen voor het maken van een Management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="83e09-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="83e09-119">De volgende onderwerpen wordt beschreven hoe u maken en implementeren van een Management OData-webservice.</span><span class="sxs-lookup"><span data-stu-id="83e09-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="83e09-120">Toevoegen van Resources aan een Management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="83e09-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-121">Aangepaste autorisatie voor een Management OData-webservice implementeren</span><span class="sxs-lookup"><span data-stu-id="83e09-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-122">SessionConfiguration voor een Management OData-webservice implementeren</span><span class="sxs-lookup"><span data-stu-id="83e09-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-123">Het schema MOF-bestand voor een Management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="83e09-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-124">Het XML-schemabestand voor een Management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="83e09-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-125">Het bestand Web.config voor een Management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="83e09-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-126">Een Management OData-webservice implementeren</span><span class="sxs-lookup"><span data-stu-id="83e09-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="83e09-127">Management OData entiteiten koppelen</span><span class="sxs-lookup"><span data-stu-id="83e09-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="83e09-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="83e09-128">See Also</span></span>

[<span data-ttu-id="83e09-129">Extensieschema voor Management ODATA IIS-bestanden</span><span class="sxs-lookup"><span data-stu-id="83e09-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
