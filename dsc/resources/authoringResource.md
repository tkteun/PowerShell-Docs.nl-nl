---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Maken van aangepaste Windows PowerShell Desired State Configuration Resources
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076868"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="8c2c9-103">Maken van aangepaste Windows PowerShell Desired State Configuration Resources</span><span class="sxs-lookup"><span data-stu-id="8c2c9-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="8c2c9-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8c2c9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8c2c9-105">Windows PowerShell Desired State Configuration (DSC) heeft ingebouwde resources die u gebruiken kunt om uw omgeving te configureren.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="8c2c9-106">Dit onderwerp bevat een overzicht van het ontwikkelen van resources en koppelingen naar onderwerpen met specifieke informatie over en voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="8c2c9-107">Onderdelen van de DSC-resource</span><span class="sxs-lookup"><span data-stu-id="8c2c9-107">DSC resource components</span></span>

<span data-ttu-id="8c2c9-108">Een DSC-resource is een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="8c2c9-109">De module bevat zowel het schema (de definitie van de configureerbare eigenschappen) en de implementatie (de code die het echte werk dat is opgegeven door een configuratie) voor de resource.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="8c2c9-110">Een DSC-resource-schema kan worden gedefinieerd in een MOF-bestand en de implementatie wordt uitgevoerd door een scriptmodule.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="8c2c9-111">U begint met de ondersteuning van PowerShell-klassen in versie 5, kunnen het schema en de implementatie zowel worden gedefinieerd in een klasse.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="8c2c9-112">De volgende onderwerpen wordt beschreven in meer detail over het maken van DSC-resources.</span><span class="sxs-lookup"><span data-stu-id="8c2c9-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="8c2c9-113">Een aangepaste DSC-resource met MOF schrijven</span><span class="sxs-lookup"><span data-stu-id="8c2c9-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="8c2c9-114">Een DSC-resource in implementerenC#</span><span class="sxs-lookup"><span data-stu-id="8c2c9-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="8c2c9-115">Schrijven van een aangepaste DSC-resource met de PowerShell-klassen</span><span class="sxs-lookup"><span data-stu-id="8c2c9-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="8c2c9-116">Samengestelde resources: Met behulp van een DSC-configuratie als een resource</span><span class="sxs-lookup"><span data-stu-id="8c2c9-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="8c2c9-117">Met behulp van de ontwerpfunctie voor Resource-hulpprogramma</span><span class="sxs-lookup"><span data-stu-id="8c2c9-117">Using the Resource Designer tool</span></span>](../authoringResourceMofDesigner.md)
