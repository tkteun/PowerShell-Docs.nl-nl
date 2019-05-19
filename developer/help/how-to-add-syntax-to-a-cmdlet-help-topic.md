---
title: Syntaxis toevoegen aan een Cmdlet Help-onderwerp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855136"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="7a699-102">Syntaxis toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="7a699-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7a699-103">Voordat u begint met de code van het XML-bestand voor het syntaxisschema in de cmdlet Help-bestand, lees deze sectie als u een helder beeld van het type van de gegevens die u moet opgeven, zoals de parameterkenmerken en hoe die gegevens wordt weergegeven in het syntaxisschema...</span><span class="sxs-lookup"><span data-stu-id="7a699-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="7a699-104">Parameterkenmerken</span><span class="sxs-lookup"><span data-stu-id="7a699-104">Parameter Attributes</span></span>

- <span data-ttu-id="7a699-105">Vereist</span><span class="sxs-lookup"><span data-stu-id="7a699-105">Required</span></span>

  - <span data-ttu-id="7a699-106">Indien waar, kan de parameter moet worden weergegeven in alle opdrachten die gebruikmaken van de parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7a699-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="7a699-107">Indien onwaar, wordt de parameter is optioneel in alle opdrachten die gebruikmaken van de parameter is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7a699-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="7a699-108">Positie</span><span class="sxs-lookup"><span data-stu-id="7a699-108">Position</span></span>

  - <span data-ttu-id="7a699-109">Als de naam, is de parameternaam is vereist.</span><span class="sxs-lookup"><span data-stu-id="7a699-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="7a699-110">Als positionele, is de parameternaam van de is optioneel.</span><span class="sxs-lookup"><span data-stu-id="7a699-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="7a699-111">Wanneer deze wordt weggelaten, wordt de waarde van parameter moet in de opgegeven positie in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7a699-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="7a699-112">Bijvoorbeeld, als de waarde positie = "1", de parameterwaarde moet het eerste of de enige naamloze parameterwaarde in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7a699-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="7a699-113">Pijpleidinginvoer</span><span class="sxs-lookup"><span data-stu-id="7a699-113">Pipeline Input</span></span>

  - <span data-ttu-id="7a699-114">Als de waarde true (ByValue), kunt u invoer voor de parameter doorgeven.</span><span class="sxs-lookup"><span data-stu-id="7a699-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="7a699-115">De invoer is gekoppeld met ("gebonden aan") met de parameter, zelfs als de naam van de eigenschap het objecttype komt niet overeen met het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="7a699-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="7a699-116">De Windows PowerShell? onderdelen van de parameter-binding probeert te converteren van de invoer naar het juiste type en mislukt de opdracht alleen als het type kan niet worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="7a699-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="7a699-117">Slechts één parameter in een parameterset kan worden gekoppeld met de waarde.</span><span class="sxs-lookup"><span data-stu-id="7a699-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="7a699-118">Als de waarde true (ByPropertyName), kunt u invoer voor de parameter doorgeven.</span><span class="sxs-lookup"><span data-stu-id="7a699-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="7a699-119">De invoer is gekoppeld aan de parameter alleen als de parameternaam overeenkomt met de naam van een eigenschap van het invoerobject.</span><span class="sxs-lookup"><span data-stu-id="7a699-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="7a699-120">Bijvoorbeeld, als de parameternaam is `Path`, doorgesluisd naar de cmdlet objecten zijn gekoppeld aan deze parameter alleen als het object een eigenschap met de naam pad heeft.</span><span class="sxs-lookup"><span data-stu-id="7a699-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="7a699-121">Als true (ByValue, ByPropertyName), u kunt de invoer voor de parameter doorgeven door de naam van de eigenschap of door de waarde.</span><span class="sxs-lookup"><span data-stu-id="7a699-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="7a699-122">Slechts één parameter in een parameterset kan worden gekoppeld met de waarde.</span><span class="sxs-lookup"><span data-stu-id="7a699-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="7a699-123">Als het ONWAAR is, kunt u kunt geen invoer voor deze parameter doorsluizen.</span><span class="sxs-lookup"><span data-stu-id="7a699-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="7a699-124">Bij globbing</span><span class="sxs-lookup"><span data-stu-id="7a699-124">Globbing</span></span>

  - <span data-ttu-id="7a699-125">Indien waar, kan de tekst dat de gebruiker van het type voor de waarde van parameter mag jokertekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="7a699-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="7a699-126">Als het ONWAAR is, kan niet de tekst dat de gebruiker van het type voor de waarde van parameter jokertekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="7a699-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="7a699-127">Parameter Waardekenmerken</span><span class="sxs-lookup"><span data-stu-id="7a699-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="7a699-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="7a699-128">Required</span></span>

  - <span data-ttu-id="7a699-129">Indien waar, kan de opgegeven waarde moet worden gebruikt wanneer u gebruikmaakt van de parameter in een opdracht.</span><span class="sxs-lookup"><span data-stu-id="7a699-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="7a699-130">Indien onwaar, wordt de waarde van parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="7a699-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="7a699-131">Een waarde is doorgaans optioneel alleen wanneer deze een van verschillende geldige waarden voor een parameter, zoals een opsommingstype.</span><span class="sxs-lookup"><span data-stu-id="7a699-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="7a699-132">Het vereiste kenmerk van een parameterwaarde wijkt af van het vereiste kenmerk van een parameter.</span><span class="sxs-lookup"><span data-stu-id="7a699-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="7a699-133">Het vereiste kenmerk van een parameter geeft aan of de parameter (en de waarde ervan) inbegrepen zijn moeten bij het aanroepen van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a699-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="7a699-134">Het vereiste kenmerk van een parameterwaarde wordt daarentegen gebruikt alleen wanneer de parameter is opgenomen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7a699-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="7a699-135">Hiermee wordt aangegeven of de betreffende waarde moet worden gebruikt met de parameter.</span><span class="sxs-lookup"><span data-stu-id="7a699-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="7a699-136">Normaal gesproken parameterwaarden die tijdelijke aanduidingen zijn zijn vereist en parameterwaarden die letterlijke zijn zijn niet vereist, omdat ze een van verschillende waarden die kunnen worden gebruikt met de parameter.</span><span class="sxs-lookup"><span data-stu-id="7a699-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="7a699-137">Verzamelen van informatie over syntaxis</span><span class="sxs-lookup"><span data-stu-id="7a699-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="7a699-138">Beginnen met de cmdletnaam van de.</span><span class="sxs-lookup"><span data-stu-id="7a699-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="7a699-139">Lijst met alle parameters van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7a699-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="7a699-140">Typ een streepje (ook wel bekend als een 'dash' of 'min-teken' (45 ASCII) voordat u de parameternaam van elke.</span><span class="sxs-lookup"><span data-stu-id="7a699-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="7a699-141">Tussen de parameters in parametersets (sommige cmdlets hebben slechts één parameter ingesteld).</span><span class="sxs-lookup"><span data-stu-id="7a699-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="7a699-142">In dit voorbeeld de Get-Tech heeft cmdlet twee parametersets.</span><span class="sxs-lookup"><span data-stu-id="7a699-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="7a699-143">Elke parameter is ingesteld met de cmdletnaam van de start.</span><span class="sxs-lookup"><span data-stu-id="7a699-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="7a699-144">Lijst met de eerste standaardparameter.</span><span class="sxs-lookup"><span data-stu-id="7a699-144">List the default parameter set first.</span></span> <span data-ttu-id="7a699-145">De standaardparameter is opgegeven door de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="7a699-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="7a699-146">Voor elke parameter is ingesteld, eerst een lijst met de unieke parameter, tenzij er positionele parameters die moeten worden eerst weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7a699-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="7a699-147">In het vorige voorbeeld, de naam en ID-parameters zijn unieke parameters voor de twee parametersets (elke parameterset moet hebben één parameter die uniek is voor deze parameter is ingesteld).</span><span class="sxs-lookup"><span data-stu-id="7a699-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="7a699-148">Dit maakt het gemakkelijker voor gebruikers om te bepalen wat ze nodig hebben om op te geven voor de parameter parameter ingesteld.</span><span class="sxs-lookup"><span data-stu-id="7a699-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="7a699-149">Worden de parameters in de volgorde waarin ze moeten worden weergegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7a699-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="7a699-150">Als de volgorde niet van belang, worden gerelateerde parameters beschreven die samen of eerst een lijst met de meest gebruikte parameters.</span><span class="sxs-lookup"><span data-stu-id="7a699-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="7a699-151">Zorg ervoor dat u de parameters WhatIf en Bevestig als de cmdlet shouldprocess wordt overgeslagen ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="7a699-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="7a699-152">De algemene parameters (zoals uitgebreid, foutopsporing en ErrorAction) in het diagram syntaxis niet aanbieden.</span><span class="sxs-lookup"><span data-stu-id="7a699-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="7a699-153">De `Get-Help` cmdlet toegevoegd die informatie voor u, wanneer deze wordt weergegeven het Help-onderwerp.</span><span class="sxs-lookup"><span data-stu-id="7a699-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="7a699-154">De parameterwaarden toevoegen.</span><span class="sxs-lookup"><span data-stu-id="7a699-154">Add the parameter values.</span></span> <span data-ttu-id="7a699-155">In Windows PowerShell?, parameterwaarden worden vertegenwoordigd door hun .NET-type.</span><span class="sxs-lookup"><span data-stu-id="7a699-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="7a699-156">Echter, de naam van het worden afgekort, zoals 'tekenreeks' voor System.String.</span><span class="sxs-lookup"><span data-stu-id="7a699-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="7a699-157">Typen afkorten, zolang de betekenis daarvan uitgeschakeld, zoals 'tekenreeks' voor System.String en 'integer' voor System.Int32 is.</span><span class="sxs-lookup"><span data-stu-id="7a699-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="7a699-158">Lijst van alle waarden van inventarisaties, zoals de - parameter van het type in het vorige voorbeeld, dat kan worden ingesteld op 'basic' of 'Geavanceerd'.</span><span class="sxs-lookup"><span data-stu-id="7a699-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="7a699-159">Verwissel de parameters, zoals - lijst in het vorige voorbeeld, bevatten geen waarden.</span><span class="sxs-lookup"><span data-stu-id="7a699-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="7a699-160">Punthaken toevoegen aan parameterwaarden die tijdelijke aanduiding, in vergelijking met de parameterwaarden die letterlijke tekenreeksen zijn.</span><span class="sxs-lookup"><span data-stu-id="7a699-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="7a699-161">Zet de volgende optionele parameters en hun waarden tussen vierkante haken.</span><span class="sxs-lookup"><span data-stu-id="7a699-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="7a699-162">Tussen de namen van de volgende optionele parameters (voor positionele parameters) tussen vierkante haken.</span><span class="sxs-lookup"><span data-stu-id="7a699-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="7a699-163">De naam op voor parameters die positionele, zoals de parameter Name in het volgende voorbeeld zijn, hoeft niet te worden opgenomen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="7a699-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="7a699-164">Als een parameterwaarde meerdere waarden, zoals een lijst met namen in de parameter Name van een set van vierkante haken meteen volgt op de waarde van parameter toevoegen bevatten kan.</span><span class="sxs-lookup"><span data-stu-id="7a699-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="7a699-165">Als de gebruiker uit parameters of parameterwaarden kiezen kan, plaats, zoals het typeparameter, de keuze tussen accolades en scheidt u deze met de exclusieve OR symbol(;).</span><span class="sxs-lookup"><span data-stu-id="7a699-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="7a699-166">Als de parameterwaarde bepaalde opmaak gebruiken moet, zoals aanhalingstekens of haakjes weergegeven in de indeling in de syntaxis.</span><span class="sxs-lookup"><span data-stu-id="7a699-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="7a699-167">Het Syntaxisschema XML-code</span><span class="sxs-lookup"><span data-stu-id="7a699-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="7a699-168">Het knooppunt van de syntaxis van het XML-bestand begint onmiddellijk na het knooppunt beschrijving, dat eindigt op de \</maml:description > tag.</span><span class="sxs-lookup"><span data-stu-id="7a699-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="7a699-169">Zie voor meer informatie over het verzamelen van de gegevens die worden gebruikt in het syntaxisschema [verzamelen van informatie over de syntaxis](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="7a699-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="7a699-170">Toevoegen van een knooppunt syntaxis</span><span class="sxs-lookup"><span data-stu-id="7a699-170">Adding a Syntax Node</span></span>

<span data-ttu-id="7a699-171">Het syntaxisschema weergegeven in de cmdlet Help-onderwerp is gegenereerd op basis van de gegevens in het knooppunt van de syntaxis van het XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="7a699-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="7a699-172">Het knooppunt syntaxis is ingesloten in een paar als \<opdrachtsyntaxis: > tags.</span><span class="sxs-lookup"><span data-stu-id="7a699-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="7a699-173">Met elke parameter ingesteld van de ingesloten in een paar van de cmdlet \<opdracht: syntaxitem > tags.</span><span class="sxs-lookup"><span data-stu-id="7a699-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="7a699-174">Er is geen limiet voor het aantal \<opdracht: syntaxitem > tags die u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="7a699-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="7a699-175">Het volgende voorbeeld ziet een knooppunt syntaxis met de syntaxis van de item-knooppunten gedurende twee parametersets.</span><span class="sxs-lookup"><span data-stu-id="7a699-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="7a699-176">De Cmdlet-naam toe te voegen aan de Parameter instellen gegevens</span><span class="sxs-lookup"><span data-stu-id="7a699-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="7a699-177">Elke parameterset van de cmdlet is opgegeven in een knooppunt van het item syntaxis.</span><span class="sxs-lookup"><span data-stu-id="7a699-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="7a699-178">Elk knooppunt van het item syntaxis begint met een paar \<maml:name >-labels die de naam van de cmdlet bevatten.</span><span class="sxs-lookup"><span data-stu-id="7a699-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="7a699-179">Het volgende voorbeeld bevat een knooppunt syntaxis met de syntaxis van de item-knooppunten gedurende twee parametersets.</span><span class="sxs-lookup"><span data-stu-id="7a699-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a><span data-ttu-id="7a699-180">Parameters toe te voegen</span><span class="sxs-lookup"><span data-stu-id="7a699-180">Adding Parameters</span></span>

<span data-ttu-id="7a699-181">Elke parameter toegevoegd aan de syntaxis van de item-knooppunt is opgegeven in een paar \<opdrachtparameter: > tags.</span><span class="sxs-lookup"><span data-stu-id="7a699-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="7a699-182">U moet een tweetal \<opdrachtparameter: > tags voor elke parameter die is opgenomen in de parameter is ingesteld, met uitzondering van de algemene parameters die worden geleverd door Windows PowerShell?</span><span class="sxs-lookup"><span data-stu-id="7a699-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="7a699-183">De kenmerken van het openen \<opdrachtparameter: > tag te bepalen hoe de parameter in het syntaxisschema wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7a699-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="7a699-184">Zie voor informatie over de parameterkenmerken, [Parameterkenmerken](#parameter-attributes).</span><span class="sxs-lookup"><span data-stu-id="7a699-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="7a699-185">De \<opdrachtparameter: > tag ondersteunt een onderliggend element \<maml:description > waarvan de inhoud wordt nooit weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7a699-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="7a699-186">De beschrijvingen van de parameters zijn opgegeven in de parameterknooppunt van het XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="7a699-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="7a699-187">Om te voorkomen dat inconsistenties tussen de informatie in de syntaxis van de instanties en de parameterknooppunt, laat de (\<maml:description > of laat het veld leeg.</span><span class="sxs-lookup"><span data-stu-id="7a699-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="7a699-188">Het volgende voorbeeld bevat een knooppunt van het item syntaxis voor een parameter met twee parameters instellen.</span><span class="sxs-lookup"><span data-stu-id="7a699-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
