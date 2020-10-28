---
ms.date: 09/13/2016
ms.topic: reference
title: Het Help-bestand voor cmdlets maken
description: Het Help-bestand voor cmdlets maken
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659090"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="e78c9-103">Het Help-bestand voor cmdlets maken</span><span class="sxs-lookup"><span data-stu-id="e78c9-103">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="e78c9-104">In deze sectie wordt beschreven hoe u een geldig XML-bestand maakt dat inhoud bevat voor Help-onderwerpen over de Windows Power shell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-104">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="e78c9-105">In deze sectie wordt beschreven hoe u het Help-bestand kunt benoemen, hoe u de juiste XML-headers kunt toevoegen en hoe u knoop punten kunt toevoegen die de verschillende secties van de cmdlet Help-inhoud bevatten.</span><span class="sxs-lookup"><span data-stu-id="e78c9-105">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="e78c9-106">Als u een volledig overzicht van een Help-bestand wilt weer geven, opent u een van de `dll-Help.xml` bestanden die zich in de installatiemap van Windows Power shell bevinden.</span><span class="sxs-lookup"><span data-stu-id="e78c9-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="e78c9-107">Het `Microsoft.PowerShell.Commands.Management.dll-Help.xml` bestand bevat bijvoorbeeld inhoud voor verschillende Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e78c9-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="e78c9-108">Een Help-bestand voor cmdlets maken</span><span class="sxs-lookup"><span data-stu-id="e78c9-108">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="e78c9-109">Maak een tekst bestand en sla dit op met UTF8-code ring.</span><span class="sxs-lookup"><span data-stu-id="e78c9-109">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="e78c9-110">De bestands naam moet de volgende indeling hebben, zodat deze door Windows Power shell kan worden gedetecteerd als een cmdlet-Help-bestand.</span><span class="sxs-lookup"><span data-stu-id="e78c9-110">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="e78c9-111">Voeg de volgende XML-headers toe aan het tekst bestand.</span><span class="sxs-lookup"><span data-stu-id="e78c9-111">Add the following XML headers to the text file.</span></span> <span data-ttu-id="e78c9-112">Houd er rekening mee dat het bestand wordt gevalideerd op basis van het MAML-schema (micro soft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="e78c9-112">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="e78c9-113">Power shell biedt momenteel geen hulpprogram ma's om het bestand te valideren.</span><span class="sxs-lookup"><span data-stu-id="e78c9-113">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="e78c9-114">Voeg een **opdracht** knooppunt toe aan het Help-bestand van de cmdlet voor elke cmdlet in de assembly.</span><span class="sxs-lookup"><span data-stu-id="e78c9-114">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="e78c9-115">Elk knoop punt in het **opdracht** knooppunt heeft betrekking op de verschillende secties van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-115">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="e78c9-116">De volgende tabel bevat het XML-element voor elk knoop punt, gevolgd door een beschrijving van elk knoop punt.</span><span class="sxs-lookup"><span data-stu-id="e78c9-116">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="e78c9-117">Knooppunt</span><span class="sxs-lookup"><span data-stu-id="e78c9-117">Node</span></span>           |                                                                                                     <span data-ttu-id="e78c9-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e78c9-118">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="e78c9-119">Hiermee voegt u inhoud toe voor de secties naam en samen VATTING van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-119">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-120">Zie [de naam en samen vatting van de cmdlet toevoegen](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-120">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="e78c9-121">Hiermee voegt u inhoud toe voor de sectie Beschrijving van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-121">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-122">Zie [de gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-a-cmdlet-description.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-122">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="e78c9-123">Hiermee voegt u inhoud toe voor de sectie syntaxis van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-123">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-124">Zie [syntaxis toevoegen aan een Help-onderwerp](./how-to-add-syntax-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-124">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="e78c9-125">Voegt inhoud toe aan de sectie para METERs van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-125">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-126">Zie [para meters toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-parameter-information.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-126">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="e78c9-127">Hiermee voegt u inhoud toe voor de sectie invoer van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-127">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-128">Zie [invoer typen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-input-types-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-128">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="e78c9-129">Hiermee voegt u inhoud toe voor de sectie OUTPUTs van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-129">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-130">Zie [retour waarden toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-return-values-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-130">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="e78c9-131">Hiermee voegt u inhoud toe voor de sectie Notities van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-131">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-132">Zie [opmerkingen toevoegen aan een Help-onderwerp voor cmdlets](./how-to-add-notes-to-a-cmdlet-help-topic.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="e78c9-132">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="e78c9-133">Hiermee voegt u inhoud toe voor de sectie voor beelden van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-133">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-134">Zie voor meer informatie voor [beelden toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="e78c9-134">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="e78c9-135">Hiermee voegt u inhoud toe aan de sectie verwante koppelingen van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e78c9-135">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="e78c9-136">Zie voor meer informatie [Verwante koppelingen toevoegen aan een Help-onderwerp over cmdlets](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="e78c9-136">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="e78c9-137">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e78c9-137">Example</span></span>

 <span data-ttu-id="e78c9-138">Hier volgt een voor beeld van een **opdracht** knooppunt waarin de knoop punten voor de verschillende secties van het Help-onderwerp van de cmdlet zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="e78c9-138">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e78c9-139">Zie ook</span><span class="sxs-lookup"><span data-stu-id="e78c9-139">See Also</span></span>

 [<span data-ttu-id="e78c9-140">De naam en samen vatting van de cmdlet toevoegen</span><span class="sxs-lookup"><span data-stu-id="e78c9-140">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-141">De gedetailleerde beschrijving toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-141">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="e78c9-142">Syntaxis toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-142">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-143">Para meters toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-143">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="e78c9-144">Invoertypen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-144">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-145">Retourwaarden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-145">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-146">Opmerkingen toevoegen aan een Help-onderwerp over cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-146">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-147">Voorbeelden toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-147">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-148">Gerelateerde koppelingen toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="e78c9-148">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="e78c9-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e78c9-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
