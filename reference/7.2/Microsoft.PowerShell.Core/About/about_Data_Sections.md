---
description: Hierin worden gegevens secties uitgelegd, die teken reeksen en andere alleen-lezen gegevens van script logica isoleren.
Locale: en-US
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_data_sections?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Data_Sections
ms.openlocfilehash: 1f2a0bae0721bc9adf5b3ba92d5be32d21306a46
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879147"
---
# <a name="about-data-sections"></a><span data-ttu-id="53a83-103">Gegevens secties</span><span class="sxs-lookup"><span data-stu-id="53a83-103">About Data Sections</span></span>

## <a name="short-description"></a><span data-ttu-id="53a83-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="53a83-104">Short Description</span></span>
<span data-ttu-id="53a83-105">Hierin worden gegevens secties uitgelegd, die teken reeksen en andere alleen-lezen gegevens van script logica isoleren.</span><span class="sxs-lookup"><span data-stu-id="53a83-105">Explains Data sections, which isolate text strings and other read-only data from script logic.</span></span>

## <a name="long-description"></a><span data-ttu-id="53a83-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="53a83-106">Long Description</span></span>

<span data-ttu-id="53a83-107">Scripts die zijn ontworpen voor Power shell kunnen een of meer gegevens secties hebben die alleen gegevens bevatten.</span><span class="sxs-lookup"><span data-stu-id="53a83-107">Scripts that are designed for PowerShell can have one or more Data sections that contain only data.</span></span> <span data-ttu-id="53a83-108">U kunt een of meer gegevens secties in een script, functie of geavanceerde functie toevoegen.</span><span class="sxs-lookup"><span data-stu-id="53a83-108">You can include one or more Data sections in any script, function, or advanced function.</span></span> <span data-ttu-id="53a83-109">De inhoud van de sectie gegevens is beperkt tot een opgegeven subset van de Power shell-script taal.</span><span class="sxs-lookup"><span data-stu-id="53a83-109">The content of the Data section is restricted to a specified subset of the PowerShell scripting language.</span></span>

<span data-ttu-id="53a83-110">Het scheiden van gegevens uit code logica maakt het gemakkelijker om zowel logica als gegevens te identificeren en beheren.</span><span class="sxs-lookup"><span data-stu-id="53a83-110">Separating data from code logic makes it easier to identify and manage both logic and data.</span></span> <span data-ttu-id="53a83-111">U kunt hiermee afzonderlijke bron bestanden voor teken reeksen gebruiken voor tekst, zoals fout berichten en Help-teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="53a83-111">It lets you have separate string resource files for text, such as error messages and Help strings.</span></span> <span data-ttu-id="53a83-112">Ook wordt de code logica geïsoleerd, waardoor beveiligings-en validatie tests worden vergemakkelijkt.</span><span class="sxs-lookup"><span data-stu-id="53a83-112">It also isolates the code logic, which facilitates security and validation tests.</span></span>

<span data-ttu-id="53a83-113">In Power shell wordt de sectie gegevens gebruikt voor het ondersteunen van script intertalen.</span><span class="sxs-lookup"><span data-stu-id="53a83-113">In PowerShell, the Data section is used to support script internationalization.</span></span>
<span data-ttu-id="53a83-114">U kunt gegevens secties gebruiken om het gemakkelijker te maken om teken reeksen te isoleren, te zoeken en te verwerken die worden vertaald in veel talen van de gebruikers interface (UI).</span><span class="sxs-lookup"><span data-stu-id="53a83-114">You can use Data sections to make it easier to isolate, locate, and process strings that will be translated into many user interface (UI) languages.</span></span>

<span data-ttu-id="53a83-115">De sectie gegevens is een Power Shell 2,0-functie.</span><span class="sxs-lookup"><span data-stu-id="53a83-115">The Data section is a PowerShell 2.0 feature.</span></span> <span data-ttu-id="53a83-116">Scripts met gegevens secties kunnen niet zonder revisie worden uitgevoerd in Power shell 1,0.</span><span class="sxs-lookup"><span data-stu-id="53a83-116">Scripts with Data sections will not run in PowerShell 1.0 without revision.</span></span>

### <a name="syntax"></a><span data-ttu-id="53a83-117">Syntax</span><span class="sxs-lookup"><span data-stu-id="53a83-117">Syntax</span></span>

<span data-ttu-id="53a83-118">De syntaxis voor een gegevens sectie is als volgt:</span><span class="sxs-lookup"><span data-stu-id="53a83-118">The syntax for a Data section is as follows:</span></span>

```
DATA [<variable-name>] [-supportedCommand <cmdlet-name>] {
    <Permitted content>
}
```

<span data-ttu-id="53a83-119">Het sleutel woord data is vereist.</span><span class="sxs-lookup"><span data-stu-id="53a83-119">The Data keyword is required.</span></span> <span data-ttu-id="53a83-120">Het is niet hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="53a83-120">It is not case-sensitive.</span></span> <span data-ttu-id="53a83-121">De toegestane inhoud is beperkt tot de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="53a83-121">The permitted content is limited to the following elements:</span></span>

- <span data-ttu-id="53a83-122">Alle Power shell-Opera Tors, behalve `-match`</span><span class="sxs-lookup"><span data-stu-id="53a83-122">All PowerShell operators, except `-match`</span></span>
- <span data-ttu-id="53a83-123">`If`, `Else` en- `ElseIf` instructies</span><span class="sxs-lookup"><span data-stu-id="53a83-123">`If`, `Else`, and `ElseIf` statements</span></span>
- <span data-ttu-id="53a83-124">De volgende automatische variabelen: `$PsCulture` , `$PsUICulture` , `$True` , `$False` en `$Null`</span><span class="sxs-lookup"><span data-stu-id="53a83-124">The following automatic variables: `$PsCulture`, `$PsUICulture`, `$True`, `$False`, and `$Null`</span></span>
- <span data-ttu-id="53a83-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="53a83-125">Comments</span></span>
- <span data-ttu-id="53a83-126">Pipelines</span><span class="sxs-lookup"><span data-stu-id="53a83-126">Pipelines</span></span>
- <span data-ttu-id="53a83-127">Instructies gescheiden door punt komma's ( `;` )</span><span class="sxs-lookup"><span data-stu-id="53a83-127">Statements separated by semicolons (`;`)</span></span>
- <span data-ttu-id="53a83-128">Letterlijke waarden, zoals de volgende:</span><span class="sxs-lookup"><span data-stu-id="53a83-128">Literals, such as the following:</span></span>

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

- <span data-ttu-id="53a83-129">Cmdlets die zijn toegestaan in een gegevens sectie.</span><span class="sxs-lookup"><span data-stu-id="53a83-129">Cmdlets that are permitted in a Data section.</span></span> <span data-ttu-id="53a83-130">Standaard is alleen de `ConvertFrom-StringData` cmdlet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="53a83-130">By default, only the `ConvertFrom-StringData` cmdlet is permitted.</span></span>
- <span data-ttu-id="53a83-131">Cmdlets die u in een gegevens sectie toestaat met behulp van de `-SupportedCommand` para meter.</span><span class="sxs-lookup"><span data-stu-id="53a83-131">Cmdlets that you permit in a Data section by using the `-SupportedCommand` parameter.</span></span>

<span data-ttu-id="53a83-132">Wanneer u de `ConvertFrom-StringData` cmdlet gebruikt in een gegevens gedeelte, kunt u de sleutel-waardeparen insluiten in teken reeksen met één of dubbele aanhalings tekens of in een enkele of dubbele aanhalings teken reeksen.</span><span class="sxs-lookup"><span data-stu-id="53a83-132">When you use the `ConvertFrom-StringData` cmdlet in a Data section, you can enclose the key-value pairs in single-quoted or double-quoted strings or in single-quoted or double-quoted here-strings.</span></span> <span data-ttu-id="53a83-133">Teken reeksen die variabelen en subexpressies bevatten, moeten echter worden inge sloten in teken reeksen met enkele aanhalings tekens of in een enkele aanhalings teken, zodat de variabelen niet worden uitgevouwen en de subexpressies niet uitvoerbaar zijn.</span><span class="sxs-lookup"><span data-stu-id="53a83-133">However, strings that contain variables and subexpressions must be enclosed in single-quoted strings or in single-quoted here-strings so that the variables are not expanded and the subexpressions are not executable.</span></span>

### <a name="-supportedcommand"></a><span data-ttu-id="53a83-134">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="53a83-134">-SupportedCommand</span></span>

<span data-ttu-id="53a83-135">`-SupportedCommand`Met de para meter kunt u aangeven dat een cmdlet of functie alleen gegevens genereert.</span><span class="sxs-lookup"><span data-stu-id="53a83-135">The `-SupportedCommand` parameter allows you to indicate that a cmdlet or function generates only data.</span></span> <span data-ttu-id="53a83-136">Het is ontworpen om gebruikers toe te staan cmdlets en functies op te zetten in een gegevens sectie die ze hebben geschreven of getest.</span><span class="sxs-lookup"><span data-stu-id="53a83-136">It is designed to allow users to include cmdlets and functions in a data section that they have written or tested.</span></span>

<span data-ttu-id="53a83-137">De waarde van `-SupportedCommand` is een door komma's gescheiden lijst met een of meer cmdlets of functie namen.</span><span class="sxs-lookup"><span data-stu-id="53a83-137">The value of `-SupportedCommand` is a comma-separated list of one or more cmdlet or function names.</span></span>

<span data-ttu-id="53a83-138">De volgende gegevens sectie bevat bijvoorbeeld een door de gebruiker geschreven cmdlet, `Format-Xml` waarmee gegevens in een XML-bestand worden opgemaakt:</span><span class="sxs-lookup"><span data-stu-id="53a83-138">For example, the following data section includes a user-written cmdlet, `Format-Xml`, that formats data in an XML file:</span></span>

```powershell
DATA -supportedCommand Format-Xml
{
    Format-Xml -Strings string1, string2, string3
}
```

### <a name="using-a-data-section"></a><span data-ttu-id="53a83-139">Een gegevens sectie gebruiken</span><span class="sxs-lookup"><span data-stu-id="53a83-139">Using a Data Section</span></span>

<span data-ttu-id="53a83-140">Als u de inhoud van een gegevens sectie wilt gebruiken, wijst u deze toe aan een variabele en gebruikt u een variabele notatie voor toegang tot de inhoud.</span><span class="sxs-lookup"><span data-stu-id="53a83-140">To use the content of a Data section, assign it to a variable and use variable notation to access the content.</span></span>

<span data-ttu-id="53a83-141">De volgende gegevens sectie bevat bijvoorbeeld een `ConvertFrom-StringData` opdracht waarmee de hier-teken reeks wordt omgezet in een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="53a83-141">For example, the following data section contains a `ConvertFrom-StringData` command that converts the here-string into a hash table.</span></span> <span data-ttu-id="53a83-142">De hash-tabel is toegewezen aan de `$TextMsgs` variabele.</span><span class="sxs-lookup"><span data-stu-id="53a83-142">The hash table is assigned to the `$TextMsgs` variable.</span></span>

<span data-ttu-id="53a83-143">De `$TextMsgs` variabele maakt geen deel uit van de sectie gegevens.</span><span class="sxs-lookup"><span data-stu-id="53a83-143">The `$TextMsgs` variable is not part of the data section.</span></span>

```powershell
$TextMsgs = DATA {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="53a83-144">Gebruik de volgende opdrachten om toegang te krijgen tot de sleutels en waarden in hash-tabel in `$TextMsgs` .</span><span class="sxs-lookup"><span data-stu-id="53a83-144">To access the keys and values in hash table in `$TextMsgs`, use the following commands.</span></span>

```powershell
$TextMsgs.Text001
$TextMsgs.Text002
```

<span data-ttu-id="53a83-145">U kunt ook de naam van de variabele in de definitie van de sectie gegevens plaatsen.</span><span class="sxs-lookup"><span data-stu-id="53a83-145">Alternately, you can put the variable name in the definition of the Data section.</span></span> <span data-ttu-id="53a83-146">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="53a83-146">For example:</span></span>

```powershell
DATA TextMsgs {
    ConvertFrom-StringData -StringData @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}

$TextMsgs
```

<span data-ttu-id="53a83-147">Het resultaat is hetzelfde als in het vorige voor beeld.</span><span class="sxs-lookup"><span data-stu-id="53a83-147">The result is the same as the previous example.</span></span>

```Output
Name                           Value
----                           -----
Text001                        Windows 7
Text002                        Windows Server 2008 R2
```

### <a name="examples"></a><span data-ttu-id="53a83-148">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="53a83-148">Examples</span></span>

<span data-ttu-id="53a83-149">Eenvoudige gegevens reeksen.</span><span class="sxs-lookup"><span data-stu-id="53a83-149">Simple data strings.</span></span>

```powershell
DATA {
    "Thank you for using my PowerShell Organize.pst script."
    "It is provided free of charge to the community."
    "I appreciate your comments and feedback."
}
```

<span data-ttu-id="53a83-150">Teken reeksen die toegestane variabelen bevatten.</span><span class="sxs-lookup"><span data-stu-id="53a83-150">Strings that include permitted variables.</span></span>

```powershell
DATA {
    if ($null) {
        "To get help for this cmdlet, type get-help new-dictionary."
    }
}
```

<span data-ttu-id="53a83-151">Een hier geciteerde teken reeks die gebruikmaakt van de `ConvertFrom-StringData` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="53a83-151">A single-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA {
    ConvertFrom-StringData -stringdata @'
Text001 = Windows 7
Text002 = Windows Server 2008 R2
'@
}
```

<span data-ttu-id="53a83-152">Een dubbele aanhalings teken reeks die gebruikmaakt van de `ConvertFrom-StringData` cmdlet:</span><span class="sxs-lookup"><span data-stu-id="53a83-152">A double-quoted here-string that uses the `ConvertFrom-StringData` cmdlet:</span></span>

```powershell
DATA  {
    ConvertFrom-StringData -stringdata @"
Msg1 = To start, press any key.
Msg2 = To exit, type "quit".
"@
}
```

<span data-ttu-id="53a83-153">Een gegevens sectie die een door de gebruiker geschreven cmdlet bevat waarmee gegevens worden gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="53a83-153">A data section that includes a user-written cmdlet that generates data:</span></span>

```powershell
DATA -supportedCommand Format-XML {
    Format-Xml -strings string1, string2, string3
}
```

## <a name="see-also"></a><span data-ttu-id="53a83-154">Zie ook</span><span class="sxs-lookup"><span data-stu-id="53a83-154">See Also</span></span>

[<span data-ttu-id="53a83-155">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="53a83-155">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="53a83-156">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="53a83-156">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="53a83-157">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="53a83-157">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="53a83-158">about_If</span><span class="sxs-lookup"><span data-stu-id="53a83-158">about_If</span></span>](about_If.md)

[<span data-ttu-id="53a83-159">about_Operators</span><span class="sxs-lookup"><span data-stu-id="53a83-159">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="53a83-160">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="53a83-160">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="53a83-161">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="53a83-161">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="53a83-162">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="53a83-162">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="53a83-163">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="53a83-163">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
