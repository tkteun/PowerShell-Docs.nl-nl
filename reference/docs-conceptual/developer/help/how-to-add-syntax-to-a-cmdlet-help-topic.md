---
title: Syntaxis toevoegen aan een Help-onderwerp over cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 0210b5ed3104777541692a0e78e7d3b16f9c8256
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353268"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a><span data-ttu-id="40598-102">Syntaxis toevoegen aan een Help-onderwerp voor cmdlets</span><span class="sxs-lookup"><span data-stu-id="40598-102">How to Add Syntax to a Cmdlet Help Topic</span></span>

<span data-ttu-id="40598-103">Voordat u begint met het coderen van de XML voor het syntaxis diagram in het Help-bestand van de cmdlet, leest u deze sectie om een duidelijk beeld te krijgen van het soort gegevens dat u moet opgeven, zoals de parameter kenmerken en hoe die gegevens worden weer gegeven in het syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="40598-103">Before you start to code the XML for the syntax diagram in the cmdlet Help file, read this section to get a clear picture of the kind of data you need to provide, such as the parameter attributes, and how that data is displayed in the syntax diagram..</span></span>

### <a name="parameter-attributes"></a><span data-ttu-id="40598-104">Parameter kenmerken</span><span class="sxs-lookup"><span data-stu-id="40598-104">Parameter Attributes</span></span>

- <span data-ttu-id="40598-105">Vereist</span><span class="sxs-lookup"><span data-stu-id="40598-105">Required</span></span>

  - <span data-ttu-id="40598-106">Als deze eigenschap waar is, moet de para meter worden weer gegeven in alle opdrachten die gebruikmaken van de para meter set.</span><span class="sxs-lookup"><span data-stu-id="40598-106">If true, the parameter must appear in all commands that use the parameter set.</span></span>

  - <span data-ttu-id="40598-107">Als false is ingesteld, is de para meter optioneel in alle opdrachten die gebruikmaken van de parameterset.</span><span class="sxs-lookup"><span data-stu-id="40598-107">If false, the parameter is optional in all commands that use the parameter set.</span></span>

- <span data-ttu-id="40598-108">Positie</span><span class="sxs-lookup"><span data-stu-id="40598-108">Position</span></span>

  - <span data-ttu-id="40598-109">Als u een naam opgeeft, is de parameter naam vereist.</span><span class="sxs-lookup"><span data-stu-id="40598-109">If named, the parameter name is required.</span></span>

  - <span data-ttu-id="40598-110">Als positioneel is, is de naam van de para meter optioneel.</span><span class="sxs-lookup"><span data-stu-id="40598-110">If positional, the parameter name is optional.</span></span> <span data-ttu-id="40598-111">Wanneer deze is wegge laten, moet de waarde van de para meter in de opgegeven positie in de opdracht staan.</span><span class="sxs-lookup"><span data-stu-id="40598-111">When it is omitted, the parameter value must be in the specified position in the command.</span></span> <span data-ttu-id="40598-112">Als de waarde bijvoorbeeld position = "1" is, moet de waarde van de para meter de eerste of enige niet-genaamde parameter waarde in de opdracht zijn.</span><span class="sxs-lookup"><span data-stu-id="40598-112">For example, if the value is position="1", the parameter value must be the first or only unnamed parameter value in the command.</span></span>

- <span data-ttu-id="40598-113">Pijplijn invoer</span><span class="sxs-lookup"><span data-stu-id="40598-113">Pipeline Input</span></span>

  - <span data-ttu-id="40598-114">Indien waar (ByValue), kunt u invoer door sluizen naar de para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-114">If true (ByValue), you can pipe input to the parameter.</span></span> <span data-ttu-id="40598-115">De invoer is gekoppeld aan (' gebonden aan ') de para meter, zelfs als de naam van de eigenschap en het object type niet overeenkomen met het verwachte type.</span><span class="sxs-lookup"><span data-stu-id="40598-115">The input is associated with ("bound to") the parameter even if the property name and the object type do not match the expected type.</span></span> <span data-ttu-id="40598-116">De Windows Power shell? onderdelen voor parameter binding proberen de invoer te converteren naar het juiste type en de opdracht wordt alleen uitgevoerd als het type niet kan worden geconverteerd.</span><span class="sxs-lookup"><span data-stu-id="40598-116">The Windows PowerShell? parameter binding components try to convert the input to the correct type and fail the command only when the type cannot be converted.</span></span> <span data-ttu-id="40598-117">Er kan slechts één para meter in een parameterset worden gekoppeld door een waarde.</span><span class="sxs-lookup"><span data-stu-id="40598-117">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="40598-118">Indien waar (ByPropertyName), kunt u invoer door sluizen naar de para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-118">If true (ByPropertyName), you can pipe input to the parameter.</span></span> <span data-ttu-id="40598-119">De invoer wordt echter alleen gekoppeld aan de para meter als de parameter naam overeenkomt met de naam van een eigenschap van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="40598-119">However, the input is associated with the parameter only when the parameter name matches the name of a property of the input object.</span></span> <span data-ttu-id="40598-120">Als de parameter naam bijvoorbeeld is `Path`, worden objecten die naar de cmdlet zijn geleid, alleen aan die para meter gekoppeld wanneer het object een eigenschap met de naam pad heeft.</span><span class="sxs-lookup"><span data-stu-id="40598-120">For example, if the parameter name is `Path`, objects piped to the cmdlet are associated with that parameter only when the object has a property named path.</span></span>

  - <span data-ttu-id="40598-121">Indien waar (ByValue, ByPropertyName), kunt u de invoer van een pipe naar de para meter door geven door de naam van de eigenschap of de waarde.</span><span class="sxs-lookup"><span data-stu-id="40598-121">If true (ByValue, ByPropertyName), you can pipe input to the parameter either by property name or by value.</span></span> <span data-ttu-id="40598-122">Er kan slechts één para meter in een parameterset worden gekoppeld door een waarde.</span><span class="sxs-lookup"><span data-stu-id="40598-122">Only one parameter in a parameter set can be associated by value.</span></span>

  - <span data-ttu-id="40598-123">Als deze eigenschap onwaar is, kunt u geen invoer van de sluis naar deze para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-123">If false, you cannot pipe input to this parameter.</span></span>

- <span data-ttu-id="40598-124">Globbing</span><span class="sxs-lookup"><span data-stu-id="40598-124">Globbing</span></span>

  - <span data-ttu-id="40598-125">Als deze eigenschap waar is, kan de tekst die de gebruiker voor de parameter waarde typt joker tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="40598-125">If true, the text that the user types for the parameter value can include wildcard characters.</span></span>

  - <span data-ttu-id="40598-126">Indien onwaar, kan de tekst die de gebruiker voor de parameter waarde typt geen joker tekens bevatten.</span><span class="sxs-lookup"><span data-stu-id="40598-126">If false, the text that the user types for the parameter value cannot include wildcard characters.</span></span>

### <a name="parameter-value-attributes"></a><span data-ttu-id="40598-127">Kenmerken van parameter waarden</span><span class="sxs-lookup"><span data-stu-id="40598-127">Parameter Value Attributes</span></span>

- <span data-ttu-id="40598-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="40598-128">Required</span></span>

  - <span data-ttu-id="40598-129">Indien waar, moet de opgegeven waarde worden gebruikt wanneer u de para meter in een opdracht gebruikt.</span><span class="sxs-lookup"><span data-stu-id="40598-129">If true, the specified value must be used whenever using the parameter in a command.</span></span>

  - <span data-ttu-id="40598-130">Als false is ingesteld, is de waarde van de para meter optioneel.</span><span class="sxs-lookup"><span data-stu-id="40598-130">If false, the parameter value is optional.</span></span> <span data-ttu-id="40598-131">Normaal gesp roken is een waarde alleen optioneel wanneer het een van de geldige waarden voor een para meter is, zoals in een opgesomd type.</span><span class="sxs-lookup"><span data-stu-id="40598-131">Typically, a value is optional only when it is one of several valid values for a parameter, such as in an enumerated type.</span></span>

<span data-ttu-id="40598-132">Het vereiste kenmerk van een parameter waarde wijkt af van het vereiste kenmerk van een para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-132">The Required attribute of a parameter value is different from the Required attribute of a parameter.</span></span>

<span data-ttu-id="40598-133">Het vereiste kenmerk van een para meter geeft aan of de para meter (en de bijbehorende waarde) moet worden opgenomen bij het aanroepen van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40598-133">The required attribute of a parameter indicates whether the parameter (and its value) must be included when invoking the cmdlet.</span></span> <span data-ttu-id="40598-134">Daarentegen wordt het vereiste kenmerk van een parameter waarde alleen gebruikt wanneer de para meter in de opdracht wordt opgenomen.</span><span class="sxs-lookup"><span data-stu-id="40598-134">In contrast, the required attribute of a parameter value is used only when the parameter is included in the command.</span></span> <span data-ttu-id="40598-135">Hiermee wordt aangegeven of de desbetreffende waarde moet worden gebruikt met de para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-135">It indicates whether that particular value must be used with the parameter.</span></span>

<span data-ttu-id="40598-136">Normaal gesp roken zijn parameter waarden die tijdelijke aanduidingen zijn vereist en parameter waarden die letterlijk zijn, niet vereist, omdat ze een van verschillende waarden zijn die kunnen worden gebruikt met de para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-136">Typically, parameter values that are placeholders are required and parameter values that are literal are not required, because they are one of several values that might be used with the parameter.</span></span>

### <a name="gathering-syntax-information"></a><span data-ttu-id="40598-137">Syntaxis informatie verzamelen</span><span class="sxs-lookup"><span data-stu-id="40598-137">Gathering Syntax Information</span></span>

1. <span data-ttu-id="40598-138">Begin met de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40598-138">Start with the cmdlet name.</span></span>

   ```
   SYNTAX
       Get-Tech
   ```

2. <span data-ttu-id="40598-139">Een lijst met alle para meters van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40598-139">List all the parameters of the cmdlet.</span></span> <span data-ttu-id="40598-140">Typ een streepje (ook wel ' streepje ' of ' minteken ' (ASCII 45) voor elke parameter naam.</span><span class="sxs-lookup"><span data-stu-id="40598-140">Type a dash (also known as a "dash" or "minus sign" (ASCII 45) before each parameter name.</span></span> <span data-ttu-id="40598-141">De para meters in parameter sets scheiden (sommige cmdlets hebben mogelijk slechts één para meter ingesteld).</span><span class="sxs-lookup"><span data-stu-id="40598-141">Separate the parameters into parameter sets (some cmdlets may have only one parameter set).</span></span> <span data-ttu-id="40598-142">In dit voor beeld heeft de cmdlet Get-tech twee parameter sets.</span><span class="sxs-lookup"><span data-stu-id="40598-142">In this example the Get-Tech cmdlet has two parameter sets.</span></span>

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   <span data-ttu-id="40598-143">Start elke set para meters met de naam van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40598-143">Start each parameter set with the cmdlet name.</span></span>

   <span data-ttu-id="40598-144">Geef eerst de standaard parameterset weer.</span><span class="sxs-lookup"><span data-stu-id="40598-144">List the default parameter set first.</span></span> <span data-ttu-id="40598-145">De standaard parameter wordt opgegeven door de cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="40598-145">The default parameter is specified by the cmdlet class.</span></span>

   <span data-ttu-id="40598-146">Geef voor elke parameterset eerst de unieke para meter weer, tenzij er positionele para meters zijn die eerst moeten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="40598-146">For each parameter set, list its unique parameter first, unless there are positional parameters that must appear first.</span></span> <span data-ttu-id="40598-147">In het vorige voor beeld zijn de para meters name en ID unieke para meters voor de twee parameter sets (elke parameterset moet één para meter hebben die uniek is voor die para meter set).</span><span class="sxs-lookup"><span data-stu-id="40598-147">In the previous example, the Name and ID parameters are unique parameters for the two parameter sets (each parameter set must have one parameter that is unique to that parameter set).</span></span> <span data-ttu-id="40598-148">Dit maakt het gemakkelijker voor gebruikers om te identificeren welke para meter ze moeten opgeven voor de parameterset.</span><span class="sxs-lookup"><span data-stu-id="40598-148">This makes it easier for users to identify what parameter they need to supply for the parameter set.</span></span>

   <span data-ttu-id="40598-149">Vermeld de para meters in de volg orde waarin ze moeten worden weer gegeven in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="40598-149">List the parameters in the order that they should appear in the command.</span></span> <span data-ttu-id="40598-150">Als de volg orde niet van belang is, geeft u verwante para meters samen of geeft u de meest gebruikte para meters weer.</span><span class="sxs-lookup"><span data-stu-id="40598-150">If the order does not matter, list related parameters together, or list the most frequently used parameters first.</span></span>

   <span data-ttu-id="40598-151">Zorg ervoor dat u de WhatIf en de para meters bevestigt als de cmdlet ShouldProcess ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="40598-151">Be sure to list the WhatIf and Confirm parameters if the cmdlet supports ShouldProcess.</span></span>

   <span data-ttu-id="40598-152">Vermeld de algemene para meters (zoals uitgebreid, fout opsporing en error Action) niet in uw syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="40598-152">Do not list the common parameters (such as Verbose, Debug, and ErrorAction) in your syntax diagram.</span></span> <span data-ttu-id="40598-153">Met de cmdlet `Get-Help` wordt deze informatie voor u toegevoegd wanneer het Help-onderwerp wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="40598-153">The `Get-Help` cmdlet adds that information for you when it displays the Help topic.</span></span>

3. <span data-ttu-id="40598-154">Voeg de parameter waarden toe.</span><span class="sxs-lookup"><span data-stu-id="40598-154">Add the parameter values.</span></span> <span data-ttu-id="40598-155">In Windows Power shell? worden parameter waarden vertegenwoordigd door hun .NET-type.</span><span class="sxs-lookup"><span data-stu-id="40598-155">In Windows PowerShell?, parameter values are represented by their .NET type.</span></span> <span data-ttu-id="40598-156">De type naam kan echter worden afgekort, zoals "teken reeks" voor System. String.</span><span class="sxs-lookup"><span data-stu-id="40598-156">However, the type name can be abbreviated, such as "string" for System.String.</span></span>

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   <span data-ttu-id="40598-157">Afkorting typen zolang de betekenis ervan duidelijk is, zoals "teken reeks" voor System. String en "int" voor System. Int32.</span><span class="sxs-lookup"><span data-stu-id="40598-157">Abbreviate types as long as their meaning is clear, such as "string" for System.String and "int" for System.Int32.</span></span>

   <span data-ttu-id="40598-158">Een lijst met alle waarden van opsommingen, zoals de para meter-type in het vorige voor beeld, die kan worden ingesteld op ' Basic ' of ' Advanced '.</span><span class="sxs-lookup"><span data-stu-id="40598-158">List all values of enumerations, such as the -type parameter in the previous example, which can be set to "basic" or "advanced".</span></span>

   <span data-ttu-id="40598-159">Switch-para meters, zoals-List in het vorige voor beeld, hebben geen waarden.</span><span class="sxs-lookup"><span data-stu-id="40598-159">Switch parameters, such as -list in the previous example, do not have values.</span></span>

4. <span data-ttu-id="40598-160">U kunt punt haken toevoegen aan parameter waarden die een tijdelijke aanduiding zijn, vergeleken met parameter waarden die letterlijke tekens zijn.</span><span class="sxs-lookup"><span data-stu-id="40598-160">Add angle brackets to parameters values that are placeholder, as compared to parameter values that are literals.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. <span data-ttu-id="40598-161">Plaats optionele para meters en hun graad tussen vier Kante haken.</span><span class="sxs-lookup"><span data-stu-id="40598-161">Enclose optional parameters and their vales in square brackets.</span></span>

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. <span data-ttu-id="40598-162">Plaats namen van optionele para meters (voor positionele para meters) tussen vier Kante haken.</span><span class="sxs-lookup"><span data-stu-id="40598-162">Enclose optional parameters names (for positional parameters) in square brackets.</span></span> <span data-ttu-id="40598-163">De naam van para meters die positioneel zijn, zoals de para meter name in het volgende voor beeld, hoeft niet te worden opgenomen in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="40598-163">The name for parameters that are positional, such as the Name parameter in the following example, do not have to be included in the command.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. <span data-ttu-id="40598-164">Als een parameter waarde meerdere waarden kan bevatten, zoals een lijst met namen in de para meter name, voegt u een paar rechte haken toe direct na de waarde van de para meter.</span><span class="sxs-lookup"><span data-stu-id="40598-164">If a parameter value can contain multiple values, such as a list of names in the Name parameter, add a pair of square brackets directly following the parameter value.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. <span data-ttu-id="40598-165">Als de gebruiker kan kiezen uit para meters of parameter waarden, zoals de type para meter, plaatst u de keuzes tussen accolades en scheidt u deze met de exclusieve of symbool (;).</span><span class="sxs-lookup"><span data-stu-id="40598-165">If the user can choose from parameters or parameter values, such as the Type parameter, enclose the choices in curly brackets and separate them with the exclusive OR symbol(;).</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. <span data-ttu-id="40598-166">Als de parameter waarde specifieke opmaak moet gebruiken, zoals aanhalings tekens of haakjes, geeft u de notatie in de syntaxis weer.</span><span class="sxs-lookup"><span data-stu-id="40598-166">If the parameter value must use specific formatting, such as quotation marks or parentheses, show the format in the syntax.</span></span>

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a><span data-ttu-id="40598-167">De XML van het syntaxis diagram coderen</span><span class="sxs-lookup"><span data-stu-id="40598-167">Coding the Syntax Diagram XML</span></span>

<span data-ttu-id="40598-168">Het syntaxis knooppunt van de XML begint direct na het knoop punt beschrijving, dat eindigt op de \</maml: Description > tag.</span><span class="sxs-lookup"><span data-stu-id="40598-168">The syntax node of the XML begins immediately after the description node, which ends with the \</maml:description> tag.</span></span> <span data-ttu-id="40598-169">Zie voor meer informatie over het verzamelen van de gegevens die worden gebruikt in het syntaxis diagram [syntaxis gegevens verzamelen](#gathering-syntax-information).</span><span class="sxs-lookup"><span data-stu-id="40598-169">For information about gathering the data used in the syntax diagram, see [Gathering Syntax Information](#gathering-syntax-information).</span></span>

### <a name="adding-a-syntax-node"></a><span data-ttu-id="40598-170">Een syntaxis knooppunt toevoegen</span><span class="sxs-lookup"><span data-stu-id="40598-170">Adding a Syntax Node</span></span>

<span data-ttu-id="40598-171">Het syntaxis diagram dat in het Help-onderwerp van de cmdlet wordt weer gegeven, wordt gegenereerd op basis van de gegevens in het syntaxis knooppunt van de XML.</span><span class="sxs-lookup"><span data-stu-id="40598-171">The syntax diagram displayed in the cmdlet Help topic is generated from the data in the syntax node of the XML.</span></span> <span data-ttu-id="40598-172">Het syntaxis knooppunt bevindt zich in een paar als \<opdracht: syntaxis > Tags.</span><span class="sxs-lookup"><span data-stu-id="40598-172">The syntax node is enclosed in a pair if \<command:syntax> tags.</span></span> <span data-ttu-id="40598-173">Met elk van de para meters van de cmdlet, Inge sloten in een paar \<opdracht: syntaxitem > Tags.</span><span class="sxs-lookup"><span data-stu-id="40598-173">With each parameter set of the cmdlet enclosed in a pair of \<command:syntaxitem> tags.</span></span> <span data-ttu-id="40598-174">Er is geen limiet voor het aantal \<opdracht: syntaxitem > Tags die u kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="40598-174">There is no limit to the number of \<command:syntaxitem> tags that you can add.</span></span>

<span data-ttu-id="40598-175">In het volgende voor beeld ziet u een syntaxis knooppunt met syntaxis item knooppunten voor twee parameter sets.</span><span class="sxs-lookup"><span data-stu-id="40598-175">The following example shows a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a><span data-ttu-id="40598-176">De naam van de cmdlet toevoegen aan de para meter set data</span><span class="sxs-lookup"><span data-stu-id="40598-176">Adding the Cmdlet Name to the Parameter Set Data</span></span>

<span data-ttu-id="40598-177">Elke parameterset van de cmdlet is opgegeven in een knoop punt syntaxis item.</span><span class="sxs-lookup"><span data-stu-id="40598-177">Each parameter set of the cmdlet is specified in a syntax item node.</span></span> <span data-ttu-id="40598-178">Elk knoop punt met een syntaxis item begint met een paar \<maml: name > Tags die de naam van de cmdlet bevatten.</span><span class="sxs-lookup"><span data-stu-id="40598-178">Each syntax item node begins with a pair of \<maml:name> tags that include the name of the cmdlet.</span></span>

<span data-ttu-id="40598-179">Het volgende voor beeld bevat een syntaxis knooppunt met syntaxis item knooppunten voor twee parameter sets.</span><span class="sxs-lookup"><span data-stu-id="40598-179">The following example includes a syntax node that has syntax item nodes for two parameter sets.</span></span>

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

### <a name="adding-parameters"></a><span data-ttu-id="40598-180">Para meters toevoegen</span><span class="sxs-lookup"><span data-stu-id="40598-180">Adding Parameters</span></span>

<span data-ttu-id="40598-181">Elke para meter die wordt toegevoegd aan het knoop punt syntaxis item, wordt opgegeven in een paar \<opdracht: para meter > Tags.</span><span class="sxs-lookup"><span data-stu-id="40598-181">Each parameter added to the syntax item node is specified within a pair of \<command:parameter> tags.</span></span> <span data-ttu-id="40598-182">U hebt een combi natie van \<opdracht: para meter > Tags voor elke para meter die is opgenomen in de parameterset, met uitzonde ring van de algemene para meters die worden geleverd door Windows Power shell?.</span><span class="sxs-lookup"><span data-stu-id="40598-182">You need a pair of \<command:parameter> tags for each parameter included in the parameter set, with the exception of the common parameters that are provided by Windows PowerShell?.</span></span>

<span data-ttu-id="40598-183">De kenmerken van de opdracht voor het openen van \<: para meter > tag bepalen hoe de para meter wordt weer gegeven in het syntaxis diagram.</span><span class="sxs-lookup"><span data-stu-id="40598-183">The attributes of the opening \<command:parameter> tag determine how the parameter appears in the syntax diagram.</span></span> <span data-ttu-id="40598-184">Zie [para meter Attributes](#parameter-attributes)(Engelstalig) voor meer informatie over parameter kenmerken.</span><span class="sxs-lookup"><span data-stu-id="40598-184">For information on parameter attributes, see [Parameter Attributes](#parameter-attributes).</span></span>

> [!NOTE]
> <span data-ttu-id="40598-185">De \<opdracht: para meter > tag ondersteunt een onderliggend element \<maml: Beschrijving > waarvan de inhoud nooit wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="40598-185">The \<command:parameter> tag supports a child element \<maml:description> whose content is never displayed.</span></span> <span data-ttu-id="40598-186">De parameter beschrijvingen worden opgegeven in het parameter knooppunt van de XML.</span><span class="sxs-lookup"><span data-stu-id="40598-186">The parameter descriptions are specified in the parameter node of the XML.</span></span> <span data-ttu-id="40598-187">Als u inconsistenties wilt voor komen tussen de gegevens in het syntaxis-item bodes en het parameter knooppunt, laat u de (\<maml: Beschrijving > weg, of laat u het leeg.</span><span class="sxs-lookup"><span data-stu-id="40598-187">To avoid inconsistencies between the information in the syntax item bodes and the parameter node, omit the (\<maml:description> or leave it empty.</span></span>

<span data-ttu-id="40598-188">Het volgende voor beeld bevat een syntaxis item-knoop punt voor een parameterset met twee para meters.</span><span class="sxs-lookup"><span data-stu-id="40598-188">The following example includes a syntax item node for a parameter set with two parameters.</span></span>

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
