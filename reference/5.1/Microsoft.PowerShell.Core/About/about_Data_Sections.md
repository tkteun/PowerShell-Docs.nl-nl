---
description: Hierin worden gegevens secties uitgelegd, die teken reeksen en andere alleen-lezen gegevens van script logica isoleren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: d45339bae42b1131e1dfb9618413a34e250a578e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252821"
---
# <a name="about-data-sections"></a><span data-ttu-id="cdaa5-104">Gegevens secties</span><span class="sxs-lookup"><span data-stu-id="cdaa5-104">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="cdaa5-105">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="cdaa5-105">Short Description</span></span>
<span data-ttu-id="cdaa5-106">Hierin worden gegevens secties uitgelegd, die teken reeksen en andere alleen-lezen gegevens van script logica isoleren.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-106">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="cdaa5-107">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="cdaa5-107">Long Description</span></span>

<span data-ttu-id="cdaa5-108">Scripts die zijn ontworpen voor Power shell kunnen een of meer gegevens secties hebben die alleen gegevens bevatten.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-108">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="cdaa5-109">U kunt een of meer gegevens secties in een script, functie of geavanceerde functie toevoegen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-109">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="cdaa5-110">De inhoud van de sectie gegevens is beperkt tot een opgegeven subset van de Power shell-script taal.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-110">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="cdaa5-111">Het scheiden van gegevens uit code logica maakt het gemakkelijker om zowel logica als gegevens te identificeren en beheren.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-111">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="cdaa5-112">U kunt hiermee afzonderlijke bron bestanden voor teken reeksen gebruiken voor tekst, zoals fout berichten en Help-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-112">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="cdaa5-113">Ook wordt de code logica geïsoleerd, waardoor beveiligings-en validatie tests worden vergemakkelijkt.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-113">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="cdaa5-114">In Power shell wordt de sectie gegevens gebruikt voor het ondersteunen van script intertalen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-114">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="cdaa5-115">U kunt gegevens secties gebruiken om het gemakkelijker te maken om teken reeksen te isoleren, te zoeken en te verwerken die worden vertaald in veel talen van de gebruikers interface (UI).</span><span class="sxs-lookup"><span data-stu-id="cdaa5-115">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="cdaa5-116">De sectie gegevens is een Power Shell 2,0-functie.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-116">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="cdaa5-117">Scripts met gegevens secties kunnen niet zonder revisie worden uitgevoerd in Power shell 1,0.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-117">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="cdaa5-118">Syntax</span><span class="sxs-lookup"><span data-stu-id="cdaa5-118">Syntax</span></span>

<span data-ttu-id="cdaa5-119">De syntaxis voor een gegevens sectie is als volgt:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-119">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="cdaa5-120">Het sleutel woord data is vereist.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-120">The Data keyword is required.</span></span> <span data-ttu-id="cdaa5-121">Het is niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-121">It is not case-sensitive.</span></span> <span data-ttu-id="cdaa5-122">De toegestane inhoud is beperkt tot de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-122">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="cdaa5-123">Alle Power shell-Opera Tors, behalve `-match`</span><span class="sxs-lookup"><span data-stu-id="cdaa5-123">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="cdaa5-124">`If`, `Else` en- `ElseIf` instructies</span><span class="sxs-lookup"><span data-stu-id="cdaa5-124">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="cdaa5-125">De volgende automatische variabelen: `$PsCulture` , `$PsUICulture` , `$True` , `$False` en `$Null`</span><span class="sxs-lookup"><span data-stu-id="cdaa5-125">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="cdaa5-126">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="cdaa5-126">Comments</span></span>
- <span data-ttu-id="cdaa5-127">Pijplijnen</span><span class="sxs-lookup"><span data-stu-id="cdaa5-127">Pipelines</span></span>
- <span data-ttu-id="cdaa5-128">Instructies gescheiden door punt komma's ( `;` )</span><span class="sxs-lookup"><span data-stu-id="cdaa5-128">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="cdaa5-129">Letterlijke waarden, zoals de volgende:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-129">Literals, such as the following:</span></span>

  ```powershell
  a
  1
  1,2,3
  "PowerShell 2.0"
  @( "red", "green", "blue" )
  @{ a = 0x1; b = "great"; c ="script" }
  [XML] @'
  <p> Hello, World </p>
  '@
  ```

- <span data-ttu-id="cdaa5-130">Cmdlets die zijn toegestaan in een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-130">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="cdaa5-131">Standaard is alleen de `ConvertFrom-StringData` cmdlet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-131">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="cdaa5-132">Cmdlets die u in een gegevens sectie toestaat met behulp van de `-SupportedCommand` para meter.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-132">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="cdaa5-133">Wanneer u de `ConvertFrom-StringData` cmdlet gebruikt in een gegevens gedeelte, kunt u de sleutel-waardeparen insluiten in teken reeksen met één of dubbele aanhalings tekens of in een enkele of dubbele aanhalings teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-133">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="cdaa5-134">Teken reeksen die variabelen en subexpressies bevatten, moeten echter worden inge sloten in teken reeksen met enkele aanhalings tekens of in een enkele aanhalings teken, zodat de variabelen niet worden uitgevouwen en de subexpressies niet uitvoerbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-134">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="cdaa5-135">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="cdaa5-135">-SupportedCommand</span></span>

<span data-ttu-id="cdaa5-136">`-SupportedCommand`Met de para meter kunt u aangeven dat een cmdlet of functie alleen gegevens genereert.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-136">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="cdaa5-137">Het is ontworpen om gebruikers toe te staan cmdlets en functies op te zetten in een gegevens sectie die ze hebben geschreven of getest.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-137">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="cdaa5-138">De waarde van `-SupportedCommand` is een door komma's gescheiden lijst met een of meer cmdlets of functie namen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-138">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="cdaa5-139">De volgende gegevens sectie bevat bijvoorbeeld een door de gebruiker geschreven cmdlet, `Format-XML` waarmee gegevens in een XML-bestand worden opgemaakt:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-139">For example, the following data section includes a user-written cmdlet, `Format-XML`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="cdaa5-140">Een gegevens sectie gebruiken</span><span class="sxs-lookup"><span data-stu-id="cdaa5-140">Using a Data Section</span></span>

<span data-ttu-id="cdaa5-141">Als u de inhoud van een gegevens sectie wilt gebruiken, wijst u deze toe aan een variabele en gebruikt u een variabele notatie voor toegang tot de inhoud.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-141">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="cdaa5-142">De volgende gegevens sectie bevat bijvoorbeeld een `ConvertFrom-StringData` opdracht waarmee de hier-teken reeks wordt omgezet in een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-142">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="cdaa5-143">De hash-tabel is toegewezen aan de `$TextMsgs` variabele.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-143">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="cdaa5-144">De `$TextMsgs` variabele maakt geen deel uit van de sectie gegevens.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-144">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="cdaa5-145">Gebruik de volgende opdrachten om toegang te krijgen tot de sleutels en waarden in hash-tabel in `$TextMsgs` .</span><span class="sxs-lookup"><span data-stu-id="cdaa5-145">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="cdaa5-146">U kunt ook de naam van de variabele in de definitie van de sectie gegevens plaatsen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-146">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="cdaa5-147">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-147">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="cdaa5-148">Het resultaat is hetzelfde als in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-148">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="cdaa5-149">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="cdaa5-149">Examples</span></span>

<span data-ttu-id="cdaa5-150">Eenvoudige gegevens reeksen.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-150">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="cdaa5-151">Teken reeksen die toegestane variabelen bevatten.</span><span class="sxs-lookup"><span data-stu-id="cdaa5-151">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="cdaa5-152">Een hier geciteerde teken reeks die gebruikmaakt van de `ConvertFrom-StringData` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-152">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="cdaa5-153">Een dubbele aanhalings teken reeks die gebruikmaakt van de `ConvertFrom-StringData` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-153">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="cdaa5-154">Een gegevens sectie die een door de gebruiker geschreven cmdlet bevat waarmee gegevens worden gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="cdaa5-154">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="cdaa5-155">Zie ook</span><span class="sxs-lookup"><span data-stu-id="cdaa5-155">See Also</span></span>

[<span data-ttu-id="cdaa5-156">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="cdaa5-156">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="cdaa5-157">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="cdaa5-157">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="cdaa5-158">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="cdaa5-158">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="cdaa5-159">about_If</span><span class="sxs-lookup"><span data-stu-id="cdaa5-159">about_If</span></span>](about_If.md)

[<span data-ttu-id="cdaa5-160">about_Operators</span><span class="sxs-lookup"><span data-stu-id="cdaa5-160">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="cdaa5-161">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="cdaa5-161">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="cdaa5-162">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="cdaa5-162">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="cdaa5-163">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="cdaa5-163">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="cdaa5-164">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="cdaa5-164">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
