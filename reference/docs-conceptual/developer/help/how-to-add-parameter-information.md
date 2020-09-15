---
title: Parametergegevens toevoegen
ms.date: 09/12/2016
ms.openlocfilehash: 15d0194a1d5449c65977703faf245e449d75d176
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893387"
---
# <a name="how-to-add-parameter-information"></a><span data-ttu-id="5e354-102">Parametergegevens toevoegen</span><span class="sxs-lookup"><span data-stu-id="5e354-102">How to Add Parameter Information</span></span>

<span data-ttu-id="5e354-103">In deze sectie wordt beschreven hoe u inhoud kunt toevoegen die wordt weer gegeven in de sectie **para meters** van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e354-103">This section describes how to add content that is displayed in the **PARAMETERS** section of the cmdlet Help topic.</span></span> <span data-ttu-id="5e354-104">De sectie **para meters** van het Help-onderwerp bevat een lijst met alle para meters van de cmdlet en een gedetailleerde beschrijving van elke para meter.</span><span class="sxs-lookup"><span data-stu-id="5e354-104">The **PARAMETERS** section of the Help topic lists each of the parameters of the cmdlet and provides a detailed description of each parameter.</span></span>

<span data-ttu-id="5e354-105">De inhoud van de **para meters** sectie moet consistent zijn met de inhoud van de sectie **syntaxis** van het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="5e354-105">The content of the **PARAMETERS** section should be consistent with the content of the **SYNTAX** section of the Help topic.</span></span> <span data-ttu-id="5e354-106">Het is de verantwoordelijkheid van de Help-auteur om ervoor te zorgen dat zowel de **syntaxis** als het **para meters** -knoop punt vergelijk bare XML-elementen bevatten.</span><span class="sxs-lookup"><span data-stu-id="5e354-106">It is the responsibility of the Help author to make sure that both the **Syntax** and **Parameters** node contain similar XML elements.</span></span>

> [!NOTE]
> <span data-ttu-id="5e354-107">Als u een volledig overzicht van een Help-bestand wilt weer geven, opent u een van de `dll-Help.xml` bestanden die zich in de installatie directory van Power shell bevinden.</span><span class="sxs-lookup"><span data-stu-id="5e354-107">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the PowerShell installation directory.</span></span> <span data-ttu-id="5e354-108">Het `Microsoft.PowerShell.Commands.Management.dll-Help.xml` bestand bevat bijvoorbeeld inhoud voor verschillende Power shell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5e354-108">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="to-add-parameters"></a><span data-ttu-id="5e354-109">Para meters toevoegen</span><span class="sxs-lookup"><span data-stu-id="5e354-109">To Add Parameters</span></span>

1. <span data-ttu-id="5e354-110">Open het Help-bestand van de cmdlet en zoek het knoop punt opdracht voor de cmdlet die u wilt documenteren.</span><span class="sxs-lookup"><span data-stu-id="5e354-110">Open the cmdlet Help file and locate the Command node for the cmdlet you are documenting.</span></span> <span data-ttu-id="5e354-111">Als u een nieuwe cmdlet toevoegt, moet u een nieuw opdracht knooppunt maken.</span><span class="sxs-lookup"><span data-stu-id="5e354-111">If you are adding a new cmdlet you will need to create a new Command node.</span></span> <span data-ttu-id="5e354-112">Uw Help-bestand bevat een opdracht knooppunt voor elke cmdlet waarvoor u Help-inhoud voor maakt.</span><span class="sxs-lookup"><span data-stu-id="5e354-112">Your Help file will contain a Command node for each cmdlet that you are providing Help content for.</span></span> <span data-ttu-id="5e354-113">Hier volgt een voor beeld van een leeg opdracht knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5e354-113">Here is an example of a blank Command node.</span></span>

    ```xml
    <command:command>
    </command:command>
    ```

1. <span data-ttu-id="5e354-114">Zoek in het opdracht knooppunt het knoop punt beschrijving en voeg een para meters-knoop punt toe, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5e354-114">Within the Command node, locate the Description node and add a Parameters node as shown below.</span></span>
   <span data-ttu-id="5e354-115">Er is slechts één para meters-knoop punt toegestaan en het moet onmiddellijk volgen op het syntaxis knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5e354-115">Only one Parameters node is allowed, and it should immediately follow the Syntax node.</span></span>

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. <span data-ttu-id="5e354-116">Voeg binnen het knoop punt para meters een **parameter** knooppunt toe voor elke para meter van de cmdlet, zoals hieronder wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5e354-116">Within the Parameters node, add a **Parameter** node for each parameter of the cmdlet as shown below.</span></span>

   <span data-ttu-id="5e354-117">In dit voor beeld wordt een **parameter** knooppunt toegevoegd voor drie para meters.</span><span class="sxs-lookup"><span data-stu-id="5e354-117">In this example, a **Parameter** node is added for three parameters.</span></span>

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   <span data-ttu-id="5e354-118">Omdat dit dezelfde XML-tags zijn die worden gebruikt in het syntaxis knooppunt, en omdat de para meters die hier zijn opgegeven, moeten overeenkomen met de para meters die zijn opgegeven door het syntaxis knooppunt, kunt u de parameter knooppunten van het syntaxis knooppunt kopiëren en plakken in het knoop punt para meters.</span><span class="sxs-lookup"><span data-stu-id="5e354-118">Because these are the same XML tags that are used in the Syntax node, and because the parameters specified here must match the parameters specified by the Syntax node, you can copy the Parameter nodes from the Syntax node and paste them into the Parameters node.</span></span> <span data-ttu-id="5e354-119">Zorg er echter voor dat u slechts één exemplaar van een parameter knooppunt kopieert, zelfs als de para meter in meerdere parameter sets in de syntaxis is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="5e354-119">However, be sure to copy only one instance of a Parameter node, even if the parameter is specified in multiple parameter sets in the syntax.</span></span>

1. <span data-ttu-id="5e354-120">Stel voor elk parameter knooppunt de kenmerk waarden in waarmee de kenmerken van elke para meter worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="5e354-120">For each Parameter node, set the attribute values that define the characteristics of each parameter.</span></span> <span data-ttu-id="5e354-121">Deze kenmerken bevatten het volgende: vereist, globbing, pipelineinput en positie.</span><span class="sxs-lookup"><span data-stu-id="5e354-121">These attributes include the following: required, globbing, pipelineinput, and position.</span></span>

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

1. <span data-ttu-id="5e354-122">Voeg voor elk parameter knooppunt de naam van de para meter toe.</span><span class="sxs-lookup"><span data-stu-id="5e354-122">For each Parameter node, add the name of the parameter.</span></span> <span data-ttu-id="5e354-123">Hier volgt een voor beeld van de parameter naam die is toegevoegd aan het parameter knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5e354-123">Here is an example of the parameter name added to the Parameter node.</span></span>

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. <span data-ttu-id="5e354-124">Voeg voor elk **parameter** knooppunt de beschrijving van de para meter toe.</span><span class="sxs-lookup"><span data-stu-id="5e354-124">For each **Parameter** node, add the description of the parameter.</span></span> <span data-ttu-id="5e354-125">Hier volgt een voor beeld van de parameter beschrijving die wordt toegevoegd aan het **parameter** knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5e354-125">Here is an example of the parameter description added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="5e354-126">Voeg voor elk **parameter** knooppunt het .net-type van de para meter toe.</span><span class="sxs-lookup"><span data-stu-id="5e354-126">For each **Parameter** node, add the .NET type of the parameter.</span></span> <span data-ttu-id="5e354-127">Het parameter type wordt samen met de parameter naam weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5e354-127">The parameter type is displayed along with the parameter name.</span></span>

   <span data-ttu-id="5e354-128">Hier volgt een voor beeld van het para meter .NET-type dat is toegevoegd aan het **parameter** knooppunt.</span><span class="sxs-lookup"><span data-stu-id="5e354-128">Here is an example of the parameter .NET type added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="5e354-129">Voeg voor elk **parameter** knooppunt de standaard waarde van de para meter toe.</span><span class="sxs-lookup"><span data-stu-id="5e354-129">For each **Parameter** node, add the default value of the parameter.</span></span> <span data-ttu-id="5e354-130">De volgende zin wordt toegevoegd aan de parameter beschrijving wanneer de inhoud wordt weer gegeven: **DefaultValue** is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="5e354-130">The following sentence is added to the parameter description when the content is displayed: **DefaultValue** is the default.</span></span>

   <span data-ttu-id="5e354-131">Hier volgt een voor beeld van de standaard waarde voor de para meter wordt toegevoegd aan het knoop punt **para meter** .</span><span class="sxs-lookup"><span data-stu-id="5e354-131">Here is an example of the parameter default value is added to the **Parameter** node.</span></span>

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

1. <span data-ttu-id="5e354-132">Voeg een mogelijk waarden knooppunt toe voor elke para meter met meerdere waarden.</span><span class="sxs-lookup"><span data-stu-id="5e354-132">For each Parameter that has multiple values, add a possible values node.</span></span>

   <span data-ttu-id="5e354-133">Hier volgt een voor beeld van het knoop punt van een mogelijke waarden waarmee twee mogelijke waarden voor de para meter worden gedefinieerd</span><span class="sxs-lookup"><span data-stu-id="5e354-133">Here is an example of the of a possible values node that defines two possible values for the parameter</span></span>

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

<span data-ttu-id="5e354-134">Hier volgen enkele dingen die u moet onthouden wanneer u para meters toevoegt.</span><span class="sxs-lookup"><span data-stu-id="5e354-134">Here are some things to remember when adding parameters.</span></span>

- <span data-ttu-id="5e354-135">De kenmerken van de para meter worden niet weer gegeven in alle weer gaven van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e354-135">The attributes of the parameter are not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="5e354-136">Ze worden echter weer gegeven in een tabel die volgt op de parameter beschrijving wanneer de gebruiker de **volledige** ( `Get-Help <cmdletname> -full` ) of de **para meter** ( `Get-Help <cmdletname> -parameter` )-weer gave van het onderwerp vraagt.</span><span class="sxs-lookup"><span data-stu-id="5e354-136">However, they are displayed in a table following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help <cmdletname> -parameter`) view of the topic.</span></span>

- <span data-ttu-id="5e354-137">De parameter beschrijving is een van de belangrijkste onderdelen van een Help-onderwerp voor cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5e354-137">The parameter description is one of the most important parts of a cmdlet Help topic.</span></span> <span data-ttu-id="5e354-138">De beschrijving moet kort en uitgebreid zijn.</span><span class="sxs-lookup"><span data-stu-id="5e354-138">The description should be brief, as well as thorough.</span></span> <span data-ttu-id="5e354-139">Houd er ook rekening mee dat als de parameter beschrijving te lang wordt, bijvoorbeeld wanneer twee para meters met elkaar communiceren, kunt u meer inhoud toevoegen in de sectie Notities van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e354-139">Also, remember that if the parameter description becomes too long, such as when two parameters interact with each other, you can add more content in the NOTES section of the cmdlet Help topic.</span></span>

  <span data-ttu-id="5e354-140">De parameter beschrijving biedt twee soorten informatie.</span><span class="sxs-lookup"><span data-stu-id="5e354-140">The parameter description provides two types of information.</span></span>

- <span data-ttu-id="5e354-141">Wat de cmdlet doet wanneer de para meter wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="5e354-141">What the cmdlet does when the parameter is used.</span></span>

- <span data-ttu-id="5e354-142">Wat een geldige waarde voor de para meter is.</span><span class="sxs-lookup"><span data-stu-id="5e354-142">What a legal value is for the parameter.</span></span>

- <span data-ttu-id="5e354-143">Omdat de parameter waarden worden uitgedrukt als .NET-objecten, hebben gebruikers meer informatie nodig over deze waarden dan in een traditionele opdracht regel-Help.</span><span class="sxs-lookup"><span data-stu-id="5e354-143">Because the parameter values are expressed as .NET objects, users need more information about these values than they would in a traditional command-line Help.</span></span> <span data-ttu-id="5e354-144">Vertel de gebruiker welk type gegevens de para meter is ontworpen om te accepteren, en neem voor beelden op.</span><span class="sxs-lookup"><span data-stu-id="5e354-144">Tell the user what type of data the parameter is designed to accept, and include examples.</span></span>

<span data-ttu-id="5e354-145">De standaard waarde van de para meter is de waarde die wordt gebruikt als de para meter niet is opgegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="5e354-145">The default value of the parameter is the value that is used if the parameter is not specified on the command line.</span></span> <span data-ttu-id="5e354-146">Houd er rekening mee dat de standaard waarde Optioneel is en niet nodig is voor sommige para meters, zoals de vereiste para meters.</span><span class="sxs-lookup"><span data-stu-id="5e354-146">Note that the default value is optional, and is not needed for some parameters, such as required parameters.</span></span> <span data-ttu-id="5e354-147">U moet echter een standaard waarde opgeven voor de meeste optionele para meters.</span><span class="sxs-lookup"><span data-stu-id="5e354-147">However, you should specify a default value for most optional parameters.</span></span>

<span data-ttu-id="5e354-148">De standaard waarde helpt de gebruiker bij het begrijpen van het effect van het gebruik van de para meter.</span><span class="sxs-lookup"><span data-stu-id="5e354-148">The default value helps the user to understand the effect of not using the parameter.</span></span> <span data-ttu-id="5e354-149">Beschrijf de standaard waarde zeer specifiek, zoals de ' huidige map ' of de ' Power shell-installatiemap ( `$PSHOME` ) ' voor een optioneel pad.</span><span class="sxs-lookup"><span data-stu-id="5e354-149">Describe the default value very specifically, such as the "Current directory" or the "PowerShell installation directory (`$PSHOME`)" for an optional path.</span></span> <span data-ttu-id="5e354-150">U kunt ook een zin schrijven waarin de standaard waarde wordt beschreven, zoals de volgende zin die wordt gebruikt voor de para meter **PassThru** : "als PassThru niet is opgegeven, geeft de cmdlet geen objecten uit de pijp lijn."</span><span class="sxs-lookup"><span data-stu-id="5e354-150">You can also write a sentence that describes the default, such as the following sentence used for the **PassThru** parameter: "If PassThru is not specified, the cmdlet does not pass objects down the pipeline."</span></span> <span data-ttu-id="5e354-151">Omdat de waarde tegenover de **standaard waarde**van de veld naam wordt weer gegeven, hoeft u niet de term ' standaard waarde ' in de vermelding op te geven.</span><span class="sxs-lookup"><span data-stu-id="5e354-151">Also, because the value is displayed opposite the field name **Default value**, you do not need to include the term "default value" in the entry.</span></span>

<span data-ttu-id="5e354-152">De standaard waarde van de para meter wordt niet weer gegeven in alle weer gaven van het Help-onderwerp van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e354-152">The default value of the parameter is not displayed in all views of the cmdlet Help topic.</span></span> <span data-ttu-id="5e354-153">Het wordt echter weer gegeven in een tabel (samen met de parameter kenmerken), gevolgd door de parameter beschrijving wanneer de gebruiker de **volledige** ( `Get-Help <cmdletname> -full` ) of de **para meter** ( `Get-Help
<cmdletname> -parameter` )-weer gave van het onderwerp vraagt.</span><span class="sxs-lookup"><span data-stu-id="5e354-153">However, it is displayed in a table (along with the parameter attributes) following the parameter description when the user asks for the **Full** (`Get-Help <cmdletname> -full`) or **Parameter** (`Get-Help
<cmdletname> -parameter`) view of the topic.</span></span>

<span data-ttu-id="5e354-154">In het volgende XML-bestand ziet `<dev:defaultValue>` u een paar tags die zijn toegevoegd aan het `<command:parameter>` knoop punt.</span><span class="sxs-lookup"><span data-stu-id="5e354-154">The following XML shows a pair of `<dev:defaultValue>` tags added to the `<command:parameter>` node.</span></span>
<span data-ttu-id="5e354-155">U ziet dat de standaard waarde direct na het afsluitende `</command:parameterValue>` label wordt gevolgd (wanneer de parameter waarde is opgegeven) of de afsluit `</maml:description>` code van de parameter beschrijving.</span><span class="sxs-lookup"><span data-stu-id="5e354-155">Notice that the default value follows immediately after the closing `</command:parameterValue>` tag (when the parameter value is specified) or the closing `</maml:description>` tag of the parameter description.</span></span> <span data-ttu-id="5e354-156">naam.</span><span class="sxs-lookup"><span data-stu-id="5e354-156">name.</span></span>

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

<span data-ttu-id="5e354-157">Waarden voor opgesomde typen toevoegen</span><span class="sxs-lookup"><span data-stu-id="5e354-157">Add Values for Enumerated Types</span></span>

<span data-ttu-id="5e354-158">Als de para meter meerdere waarden of waarden van een opgesomd type heeft, kunt u een optioneel \<dev:possibleValues> knoop punt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5e354-158">If the parameter has multiple values or values of an enumerated type, you can use an optional \<dev:possibleValues> node.</span></span> <span data-ttu-id="5e354-159">Met dit knoop punt kunt u een naam en beschrijving voor meerdere waarden opgeven.</span><span class="sxs-lookup"><span data-stu-id="5e354-159">This node allows you to specify a name and description for multiple values.</span></span>

<span data-ttu-id="5e354-160">Houd er rekening mee dat de beschrijvingen van de opgesomde waarden niet worden weer gegeven in een van de standaard Help-weer gaven die worden weer gegeven door de `Get-Help` cmdlet, maar dat andere Help-viewers deze inhoud kunnen weer geven in hun weer gaven.</span><span class="sxs-lookup"><span data-stu-id="5e354-160">Be aware that the descriptions of the enumerated values do not appear in any of the default Help views displayed by the `Get-Help` cmdlet, but other Help viewers may display this content in their views.</span></span>

<span data-ttu-id="5e354-161">In het volgende XML-bestand ziet u een `<dev:possibleValues>` knoop punt met twee opgegeven waarden.</span><span class="sxs-lookup"><span data-stu-id="5e354-161">The following XML shows a `<dev:possibleValues>` node with two values specified.</span></span>

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
