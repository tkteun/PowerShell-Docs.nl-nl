---
title: Het Help-bestand voor de cmdlet maken | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353261"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="8336e-102">Het Help-bestand voor cmdlets maken</span><span class="sxs-lookup"><span data-stu-id="8336e-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="8336e-103">In deze sectie wordt beschreven hoe u een geldig XML-bestand maakt dat inhoud bevat voor Help-onderwerpen over de Windows Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="8336e-104">In deze sectie wordt beschreven hoe u het Help-bestand kunt benoemen, hoe u de juiste XML-headers kunt toevoegen en hoe u knoop punten kunt toevoegen die de verschillende secties van de cmdlet Help-inhoud bevatten.</span><span class="sxs-lookup"><span data-stu-id="8336e-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="8336e-105">Voor een volledig overzicht van een Help-bestand opent u een van de dll-Help. XML-bestanden die zich in de installatiemap van Windows Power shell bevinden.</span><span class="sxs-lookup"><span data-stu-id="8336e-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="8336e-106">Het bestand micro soft. Power shell. commands. Management. dll-Help. XML bevat bijvoorbeeld inhoud voor verschillende Windows Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="8336e-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="8336e-107">Een Help-bestand voor cmdlets maken</span><span class="sxs-lookup"><span data-stu-id="8336e-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="8336e-108">Maak een tekst bestand en sla dit op met UTF8-code ring.</span><span class="sxs-lookup"><span data-stu-id="8336e-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="8336e-109">De bestands naam moet de volgende indeling hebben, zodat deze door Windows Power shell kan worden gedetecteerd als een cmdlet-Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="8336e-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="8336e-110">Voeg de volgende XML-headers toe aan het tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="8336e-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="8336e-111">Houd er rekening mee dat het bestand wordt gevalideerd op basis van het MAML-schema (multi-agent Modeling Language).</span><span class="sxs-lookup"><span data-stu-id="8336e-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="8336e-112">Windows Power shell biedt momenteel geen hulpprogram ma's om het bestand te valideren.</span><span class="sxs-lookup"><span data-stu-id="8336e-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="8336e-113">Voeg een opdracht knooppunt toe aan het Help-bestand van de cmdlet voor elke cmdlet in de assembly.</span><span class="sxs-lookup"><span data-stu-id="8336e-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="8336e-114">Elk knoop punt in het opdracht knooppunt heeft betrekking op de verschillende secties van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="8336e-115">De volgende tabel bevat het XML-element voor elk knoop punt, gevolgd door een beschrijving van elk knoop punt.</span><span class="sxs-lookup"><span data-stu-id="8336e-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="8336e-116">Knooppunt</span><span class="sxs-lookup"><span data-stu-id="8336e-116">Node</span></span>|<span data-ttu-id="8336e-117">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8336e-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="8336e-118">Hiermee voegt u inhoud toe voor de secties naam en samen VATTING van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-119">Zie [de naam en samen vatting van de cmdlet toevoegen](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="8336e-120">Hiermee voegt u inhoud toe voor de sectie Beschrijving van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-121">Zie [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="8336e-122">Hiermee voegt u inhoud toe voor de sectie syntaxis van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-123">Zie [syntaxis toevoegen aan een Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="8336e-124">Voegt inhoud toe aan de sectie para METERs van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-125">Zie [para meters toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-parameter-information.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="8336e-126">Hiermee voegt u inhoud toe voor de sectie invoer van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-127">Zie [invoer typen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="8336e-128">Hiermee voegt u inhoud toe voor de sectie OUTPUTs van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-129">Zie [retour waarden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="8336e-130">Hiermee voegt u inhoud toe aan de sectie Notities van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-131">Zie [opmerkingen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="8336e-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="8336e-132">Hiermee voegt u inhoud toe voor de sectie voor beelden van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-133">Zie voor meer informatie voor [beelden toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8336e-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="8336e-134">Hiermee voegt u inhoud toe aan de sectie verwante koppelingen van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8336e-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="8336e-135">Zie voor meer informatie [Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="8336e-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="8336e-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8336e-136">Example</span></span>

 <span data-ttu-id="8336e-137">Hier volgt een voor beeld van een opdracht knooppunt waarin de knoop punten voor de verschillende secties van het Help-onderwerp van de cmdlet zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="8336e-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8336e-138">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8336e-138">See Also</span></span>

 [<span data-ttu-id="8336e-139">De naam en samen vatting van de cmdlet toevoegen</span><span class="sxs-lookup"><span data-stu-id="8336e-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-140">De gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="8336e-141">De syntaxis van een Help-onderwerp toevoegen aan een cmdlet</span><span class="sxs-lookup"><span data-stu-id="8336e-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-142">Para meters toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="8336e-143">Invoer typen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-144">Retour waarden toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-145">Opmerkingen toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-146">Voor beelden toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-147">Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="8336e-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="8336e-148">Windows Power shell SDK</span><span class="sxs-lookup"><span data-stu-id="8336e-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)