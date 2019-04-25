---
title: Het toevoegen van parameterinformatie | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083362"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="48234-102">Parametergegevens toevoegen</span><span class="sxs-lookup"><span data-stu-id="48234-102">How to Add Parameter Information</span></span>

<span data-ttu-id="48234-103">In deze sectie wordt beschreven hoe u inhoud die wordt weergegeven in de sectie PARAMETERS van de cmdlet Help-onderwerp toevoegen.</span><span class="sxs-lookup"><span data-stu-id="48234-103">This section describes how to add content that is displayed in the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="48234-104">De sectie PARAMETERS van het Help-onderwerp geeft een lijst van elk van de parameters van de cmdlet en biedt een gedetailleerde beschrijving van elke parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-104">The PARAMETERS section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="48234-105">De inhoud van de sectie PARAMETERS moet consistent zijn met de inhoud van de sectie syntaxis van het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="48234-105">The content of the PARAMETERS section should be consistent with the content of the SYNTAX section of the Help topic.</span></span> <span data-ttu-id="48234-106">Het is de verantwoordelijkheid van de Help-auteur om ervoor te zorgen dat zowel de syntaxis en Parameters knooppunt dezelfde XML-elementen bevatten.</span><span class="sxs-lookup"><span data-stu-id="48234-106">It is the responsibility of the Help author to make sure that both the Syntax and Parameters node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="48234-107">Voor een volledige weergave van een Help-bestand, open een van de dll-Help.xml-bestanden zich in de installatiemap van Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48234-107">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="48234-108">Bijvoorbeeld, worden de inhoud van het bestand Microsoft.PowerShell.Commands.Management.dll Help.xml bevat voor verschillende van de Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="48234-108">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="48234-109">Parameters toevoegen</span><span class="sxs-lookup"><span data-stu-id="48234-109">To Add Parameters</span></span>

1. <span data-ttu-id="48234-110">Open het cmdlet Help-bestand en zoek het knooppunt van de opdracht voor de cmdlet die u documenteert.</span><span class="sxs-lookup"><span data-stu-id="48234-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="48234-111">Als u een nieuwe cmdlet die u moet maken van een nieuwe opdracht knooppunt toevoegt.</span><span class="sxs-lookup"><span data-stu-id="48234-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="48234-112">Het Help-bestand bevat een knooppunt van de opdracht voor elke cmdlet die u Help-inhoud voor biedt.</span><span class="sxs-lookup"><span data-stu-id="48234-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="48234-113">Hier volgt een voorbeeld van een lege opdracht-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

2. <span data-ttu-id="48234-114">Zoek het knooppunt beschrijving en toevoegen van een knooppunt Parameters zoals hieronder wordt weergegeven in het knooppunt opdracht.</span><span class="sxs-lookup"><span data-stu-id="48234-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span> <span data-ttu-id="48234-115">Slechts één knooppunt van de Parameters is toegestaan en dan onmiddellijk het knooppunt syntaxis moet volgen.</span><span class="sxs-lookup"><span data-stu-id="48234-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. <span data-ttu-id="48234-116">In het knooppunt Parameters toevoegen een parameterknooppunt voor alle parameters van de cmdlet, zoals hieronder weergegeven.</span><span class="sxs-lookup"><span data-stu-id="48234-116">Within the Parameters node, add a Parameter node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="48234-117">In dit voorbeeld wordt een parameterknooppunt toegevoegd voor de drie parameters.</span><span class="sxs-lookup"><span data-stu-id="48234-117">In this example, a Parameter node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="48234-118">Omdat dit de dezelfde XML-labels die worden gebruikt in het knooppunt syntaxis en omdat de parameters die hier is opgegeven moeten overeenkomen met de parameters die zijn opgegeven door de syntaxis van knooppunt zijn, kunt u de Parameter-knooppunten van het knooppunt syntaxis kopiëren en plak deze in het knooppunt Parameters.</span><span class="sxs-lookup"><span data-stu-id="48234-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="48234-119">Echter, moet u slechts één exemplaar van een parameterknooppunt kopiëren, zelfs als de parameter is opgegeven meerdere parametersets, in de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="48234-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

4. <span data-ttu-id="48234-120">Stel de kenmerkwaarden weer die de eigenschappen van elke parameter definiëren voor elk knooppunt Parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="48234-121">Deze kenmerken zijn onder andere het volgende: Bij globbing, pipelineinput en positie nodig.</span><span class="sxs-lookup"><span data-stu-id="48234-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. <span data-ttu-id="48234-122">Voeg de naam van de parameter voor elk knooppunt Parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="48234-123">Hier volgt een voorbeeld van de naam van de parameter toegevoegd aan de Parameter-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. <span data-ttu-id="48234-124">Voor elk knooppunt Parameter, de beschrijving van de parameter toevoegen</span><span class="sxs-lookup"><span data-stu-id="48234-124">For each Parameter node, add the description of the parameter.</span></span> <span data-ttu-id="48234-125">Hier volgt een voorbeeld van de beschrijving van de parameter toegevoegd aan de Parameter-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-125">Here is an example of the parameter description added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. <span data-ttu-id="48234-126">Voor elk knooppunt Parameter toevoegen het .NET Framework-type van de parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-126">For each Parameter node, add the .NET Framework type of the parameter.</span></span> <span data-ttu-id="48234-127">Het parametertype wordt weergegeven, samen met de naam van de parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="48234-128">Hier volgt een voorbeeld van het parametertype van de .NET Framework toegevoegd aan de Parameter-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-128">Here is an example of the parameter .NET Framework type added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. <span data-ttu-id="48234-129">Voor elk knooppunt Parameter toevoegen de standaardwaarde van de parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-129">For each Parameter node, add the default value of the parameter.</span></span> <span data-ttu-id="48234-130">De volgende zin is toegevoegd aan de beschrijving van de parameter wanneer de inhoud wordt weergegeven: "DefaultValue" is de standaardinstelling.</span><span class="sxs-lookup"><span data-stu-id="48234-130">The following sentence is added to the parameter description when the content is displayed: "DefaultValue" is the default.</span></span>

   <span data-ttu-id="48234-131">Hier volgt een voorbeeld van de standaardwaarde voor de parameter wordt toegevoegd aan de Parameter-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-131">Here is an example of the parameter default value is added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. <span data-ttu-id="48234-132">Voor elke Parameter die meerdere waarden heeft, moet u een mogelijke waarden-knooppunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="48234-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="48234-133">Hier volgt een voorbeeld van de van een knooppunt mogelijke waarden die twee mogelijke waarden voor de parameter definieert</span><span class="sxs-lookup"><span data-stu-id="48234-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="48234-134">Hier volgen enkele dingen om te onthouden wanneer parameters toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="48234-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="48234-135">De kenmerken van de parameter worden niet weergegeven in alle weergaven van de cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="48234-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="48234-136">Echter, worden deze weergegeven in een tabel die de parameter-omschrijving te volgen wanneer de gebruiker wordt gevraagd voor de volledige (Get-Help \<cmdletname >-volledige) of Parameter (Get-Help \<cmdletname >-parameter) weergave van het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="48234-136">However, they are displayed in a table following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

- <span data-ttu-id="48234-137">De beschrijving van de parameter is een van de belangrijkste onderdelen van een cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="48234-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="48234-138">De beschrijving moet kort, evenals grondig.</span><span class="sxs-lookup"><span data-stu-id="48234-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="48234-139">Vergeet ook niet als de beschrijving van de parameter te lang is, zoals wanneer twee parameters met elkaar communiceren, u meer inhoud in de sectie met opmerkingen van de cmdlet Help-onderwerp toevoegen kunt.</span><span class="sxs-lookup"><span data-stu-id="48234-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="48234-140">De beschrijving van de parameter biedt twee soorten informatie.</span><span class="sxs-lookup"><span data-stu-id="48234-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="48234-141">Wat de cmdlet doet wanneer de parameter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="48234-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="48234-142">Welke een geldige waarde is voor de parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="48234-143">Omdat de parameterwaarden worden uitgedrukt als .NET Framework-objecten, moeten gebruikers meer informatie over deze waarden dan ze net als in een traditionele Help voor de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="48234-143">Because the parameter values are expressed as .NET Framework objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="48234-144">De gebruiker zien welk type gegevens dat de parameter is ontworpen om te accepteren en voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="48234-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="48234-145">De standaardwaarde van de parameter is de waarde die wordt gebruikt als de parameter niet is opgegeven op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="48234-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="48234-146">Houd er rekening mee dat de standaardwaarde optioneel is en is niet nodig voor bepaalde parameters, zoals vereiste parameters.</span><span class="sxs-lookup"><span data-stu-id="48234-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="48234-147">U moet echter een standaardwaarde voor de meeste optionele parameters opgeven.</span><span class="sxs-lookup"><span data-stu-id="48234-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="48234-148">De standaardwaarde helpt de gebruiker om het effect van het gebruik van de parameter niet te begrijpen.</span><span class="sxs-lookup"><span data-stu-id="48234-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="48234-149">De standaardwaarde zeer specifiek, beschrijven, zoals het 'huidige directory' of de 'Windows PowerShell installatiemap ($pshome)' voor een pad zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="48234-149">Describe the default value very specifically, such as the "Current directory" or the "Windows PowerShell installation directory ($pshome)" for an optional path.</span></span> <span data-ttu-id="48234-150">U kunt ook een zin dat de standaard, zoals de volgende zin gebruikt beschrijft voor het schrijven de `PassThru` parameter: "Als PassThru gebruikt, niet opgegeven is, de cmdlet geeft niet de objecten in de pijplijn."</span><span class="sxs-lookup"><span data-stu-id="48234-150">You can also write a sentence that describes the default, such as the following sentence used for the `PassThru` parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span>  <span data-ttu-id="48234-151">Ook, omdat de waarde wordt weergegeven naast de naam van het veld '**standaardwaarde**", hoeft u niet de term 'standaardwaarde' in de vermelding opnemen.</span><span class="sxs-lookup"><span data-stu-id="48234-151">Also, because the value is displayed opposite the field name "**Default value**", you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="48234-152">De standaardwaarde van de parameter wordt niet weergegeven in alle weergaven van de cmdlet Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="48234-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="48234-153">Maar deze wordt weergegeven in een tabel (samen met de parameterkenmerken) de beschrijving van de parameter wanneer de gebruiker wordt gevraagd voor de volledige (Get-Help \<cmdletname >-volledige) of Parameter (Get-Help \<cmdletname >-parameter) weergeven in het onderwerp.</span><span class="sxs-lookup"><span data-stu-id="48234-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the Full (Get-Help \<cmdletname> -full) or Parameter (Get-Help \<cmdletname> -parameter) view of the topic.</span></span>

<span data-ttu-id="48234-154">Het volgende XML-bestand bevat een combinatie van een `<dev:defaultValue>` tags toegevoegd aan de `<command:parameter>` knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span> <span data-ttu-id="48234-155">U ziet dat de standaardwaarde onmiddellijk na de afsluitende volgt `</command:parameterValue>` tag (als de waarde van parameter is opgegeven) of de afsluitende `</maml:description>` code van de beschrijving van de parameter.</span><span class="sxs-lookup"><span data-stu-id="48234-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="48234-156">de naam.</span><span class="sxs-lookup"><span data-stu-id="48234-156">name.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

<span data-ttu-id="48234-157">Voeg waarden toe voor typen die zijn geïnventariseerd</span><span class="sxs-lookup"><span data-stu-id="48234-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="48234-158">Als de parameter meerdere waarden of van een opsommingstype heeft, kunt u een optionele \<dev:possibleValues > knooppunt.</span><span class="sxs-lookup"><span data-stu-id="48234-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="48234-159">Dit knooppunt kunt u een naam en beschrijving voor meerdere waarden opgeven.</span><span class="sxs-lookup"><span data-stu-id="48234-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="48234-160">Houd er rekening mee dat de beschrijvingen van de opsommingswaarden niet in een van de standaard Help weergaven die worden weergegeven weergegeven worden door de `Get-Help` cmdlet, maar andere viewers Help kunnen deze inhoud weergeven in hun visie.</span><span class="sxs-lookup"><span data-stu-id="48234-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="48234-161">De volgende XML bevat een `<dev:possibleValues>` knooppunt met twee waarden die zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="48234-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```