---
title: Over het maken van de Cmdlet Help-bestand | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083243"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="90efc-102">Het Help-bestand voor cmdlets maken</span><span class="sxs-lookup"><span data-stu-id="90efc-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="90efc-103">Deze sectie beschrijft het maken van een geldig XML-bestand die inhoud van Help-onderwerpen voor Windows PowerShell-cmdlets bevat.</span><span class="sxs-lookup"><span data-stu-id="90efc-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="90efc-104">In deze sectie wordt beschreven hoe het Help-bestand een naam, de juiste XML-headers toevoegen, en het toevoegen van knooppunten die de verschillende secties van de cmdlet Help-inhoud bevat.</span><span class="sxs-lookup"><span data-stu-id="90efc-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="90efc-105">Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90efc-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="90efc-106">Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="90efc-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="90efc-107">Over het maken van een Cmdlet Help-bestand</span><span class="sxs-lookup"><span data-stu-id="90efc-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="90efc-108">Maak een tekstbestand en sla deze met UTF8-codering.</span><span class="sxs-lookup"><span data-stu-id="90efc-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="90efc-109">Naam van het bestand moet de volgende indeling hebben, zodat Windows PowerShell kunnen worden gedetecteerd als een cmdlet Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="90efc-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="90efc-110">De volgende XML-headers toevoegen aan het tekstbestand.</span><span class="sxs-lookup"><span data-stu-id="90efc-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="90efc-111">Let erop dat het bestand worden gevalideerd op basis van het schema voor meerdere Agent Modeling Language (MAML).</span><span class="sxs-lookup"><span data-stu-id="90efc-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="90efc-112">Windows PowerShell biedt op dit moment geen alle hulpprogramma's voor het valideren van het bestand.</span><span class="sxs-lookup"><span data-stu-id="90efc-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="90efc-113">Een knooppunt van de opdracht toevoegen aan de cmdlet Help-bestand voor elke cmdlet in de assembly.</span><span class="sxs-lookup"><span data-stu-id="90efc-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="90efc-114">Elk knooppunt in het knooppunt van de opdracht is gekoppeld aan de verschillende secties van de cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="90efc-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="90efc-115">De volgende tabel bevat de XML-element voor elk knooppunt, gevolgd door een beschrijvingen van elk knooppunt.</span><span class="sxs-lookup"><span data-stu-id="90efc-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="90efc-116">Knooppunt</span><span class="sxs-lookup"><span data-stu-id="90efc-116">Node</span></span>|<span data-ttu-id="90efc-117">Description</span><span class="sxs-lookup"><span data-stu-id="90efc-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="90efc-118">Inhoud voor de naam en de samenvatting secties van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-119">Zie voor meer informatie, [toevoegen van de Cmdlet-naam en de samenvatting](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="90efc-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span><span class="sxs-lookup"><span data-stu-id="90efc-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-121">Zie voor meer informatie, [de gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="90efc-122">Inhoud voor de sectie syntaxis van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-123">Zie voor meer informatie, [over het toevoegen van de syntaxis voor een Cmdlet Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="90efc-124">Inhoud voor de PARAMETERS-sectie van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-125">Zie voor meer informatie, [hoe u Parameters toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="90efc-126">Inhoud voor de invoer-sectie van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-127">Zie voor meer informatie, [over het toevoegen van de invoertypen voor een Cmdlet Help-onderwerp](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="90efc-128">Inhoud voor de sectie uitvoer van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-129">Zie voor meer informatie, [toevoegen retourneren waarden aan een Cmdlet Help-onderwerp hoe u](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="90efc-130">Inhoud toevoegen aan de sectie met opmerkingen van de cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-131">Zie voor meer informatie, [toevoegen aan een Cmdlet Help-onderwerp notities](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="90efc-132">Inhoud voor de sectie met voorbeelden van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-133">Zie voor meer informatie, [over het toevoegen van de voorbeelden aan een Cmdlet Help-onderwerp](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="90efc-134">Inhoud voor de verwante koppelingen-sectie van de cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="90efc-135">Zie voor meer informatie, [hoe u verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="90efc-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="90efc-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="90efc-136">Example</span></span>

 <span data-ttu-id="90efc-137">Hier volgt een voorbeeld van een opdracht-knooppunt met de knooppunten voor de verschillende secties van de cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="90efc-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="90efc-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="90efc-138">See Also</span></span>

 [<span data-ttu-id="90efc-139">Het toevoegen van de Cmdlet-naam en de samenvatting</span><span class="sxs-lookup"><span data-stu-id="90efc-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-140">De gedetailleerde beschrijving toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="90efc-141">Syntaxis toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-142">Parameters toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="90efc-143">Invoertypen toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-144">Geretourneerde waarden toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-145">Het toevoegen van notities aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-146">Voorbeelden van een Cmdlet Help-onderwerp toevoegen</span><span class="sxs-lookup"><span data-stu-id="90efc-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-147">Verwante koppelingen toevoegen aan een Cmdlet Help-onderwerp</span><span class="sxs-lookup"><span data-stu-id="90efc-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="90efc-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="90efc-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)