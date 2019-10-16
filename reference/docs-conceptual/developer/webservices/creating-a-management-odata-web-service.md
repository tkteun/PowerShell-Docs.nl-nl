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
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="9c563-102">Een Management OData-webservice maken</span><span class="sxs-lookup"><span data-stu-id="9c563-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="9c563-103">Beheer ODATA IIS-extensie is een infra structuur voor het maken van een ASP.NET-eind punt voor webservices waarmee uw beheer gegevens, toegankelijk via Windows Power shell-cmdlets en-scripts, worden weer gegeven als OData-webservice-entiteiten.</span><span class="sxs-lookup"><span data-stu-id="9c563-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="9c563-104">Dit doet u door OData-aanvragen te verwerken en deze te converteren naar een Windows Power shell-aanroep.</span><span class="sxs-lookup"><span data-stu-id="9c563-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="9c563-105">Product teams kunnen op deze infra structuur bouwen om eind punten te maken die specifieke sets beheer gegevens beschikbaar stellen.</span><span class="sxs-lookup"><span data-stu-id="9c563-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="9c563-106">Down load en installeer het [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -voor beeld.</span><span class="sxs-lookup"><span data-stu-id="9c563-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="9c563-107">Volg de instructies voor het implementeren van de webservice.</span><span class="sxs-lookup"><span data-stu-id="9c563-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="9c563-108">Met deze webservice worden services en processen beschikbaar gesteld via Create-, Read-, update-en delete-bewerkingen (ruw).</span><span class="sxs-lookup"><span data-stu-id="9c563-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="9c563-109">RUWE aanvragen voor de webservice roepen Windows Power shell-opdrachten aan waarmee de aangevraagde bewerkingen worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c563-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="9c563-110">Een toewijzing tussen de ruwe bewerkingen en de onderliggende Windows Power shell-opdrachten wordt geïmplementeerd door twee schema bestanden: schema. mof en schema. XML.</span><span class="sxs-lookup"><span data-stu-id="9c563-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="9c563-111">Het bestand schema. MOF maakt gebruik van de [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) Managed object (MOF) standaard.</span><span class="sxs-lookup"><span data-stu-id="9c563-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="9c563-112">Het schema. XML-bestand maakt gebruik van een XML-schema dat wordt beschreven in het [resource toewijzings schema](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="9c563-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9c563-113">Voordat u de beheer-ODATA IIS-extensie inschakelt in Windows Server 2008 R2 SP1, moeten de volgende functies zijn ingeschakeld.</span><span class="sxs-lookup"><span data-stu-id="9c563-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="9c563-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="9c563-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="9c563-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="9c563-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="9c563-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="9c563-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="9c563-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="9c563-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="9c563-118">Stappen voor het maken van een management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="9c563-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="9c563-119">In de volgende onderwerpen wordt beschreven hoe u een management OData-webservice maakt en implementeert.</span><span class="sxs-lookup"><span data-stu-id="9c563-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="9c563-120">Resources toevoegen aan een management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="9c563-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-121">Aangepaste autorisatie implementeren voor een management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="9c563-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-122">SessionConfiguration implementeren voor een management OData-webservice</span><span class="sxs-lookup"><span data-stu-id="9c563-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-123">Het MOF-schema bestand voor een management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="9c563-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-124">Het XML-schema bestand voor een management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="9c563-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-125">Het web. config-bestand voor een management OData-webservice ontwerpen</span><span class="sxs-lookup"><span data-stu-id="9c563-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-126">Een management OData-webservice implementeren</span><span class="sxs-lookup"><span data-stu-id="9c563-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="9c563-127">Beheer OData-entiteiten koppelen</span><span class="sxs-lookup"><span data-stu-id="9c563-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="9c563-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9c563-128">See Also</span></span>

[<span data-ttu-id="9c563-129">Schema bestanden ODATA IIS-extensie beheer</span><span class="sxs-lookup"><span data-stu-id="9c563-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
