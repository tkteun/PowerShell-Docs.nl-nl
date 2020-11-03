---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: b1ee17e09a85c7f8afd3b41e7f9fb8b8dd5f019e
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249701"
---
# <span data-ttu-id="aa426-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="aa426-103">New-ItemProperty</span></span>

## <span data-ttu-id="aa426-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="aa426-104">SYNOPSIS</span></span>
<span data-ttu-id="aa426-105">Hiermee maakt u een nieuwe eigenschap voor een item en stelt u de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="aa426-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="aa426-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="aa426-106">SYNTAX</span></span>

### <span data-ttu-id="aa426-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="aa426-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aa426-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aa426-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aa426-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="aa426-109">DESCRIPTION</span></span>

<span data-ttu-id="aa426-110">De `New-ItemProperty` cmdlet maakt een nieuwe eigenschap voor een opgegeven item en stelt de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="aa426-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="aa426-111">Deze cmdlet wordt doorgaans gebruikt om nieuwe register waarden te maken, omdat register waarden eigenschappen van een register sleutel item zijn.</span><span class="sxs-lookup"><span data-stu-id="aa426-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="aa426-112">Met deze cmdlet worden geen eigenschappen aan een object toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="aa426-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="aa426-113">Gebruik de cmdlet om een eigenschap toe te voegen aan een exemplaar van een object `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="aa426-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="aa426-114">Als u een eigenschap wilt toevoegen aan alle objecten van een bepaald type, wijzigt u het Types.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="aa426-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="aa426-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="aa426-115">EXAMPLES</span></span>

### <span data-ttu-id="aa426-116">Voor beeld 1: een register vermelding toevoegen</span><span class="sxs-lookup"><span data-stu-id="aa426-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="aa426-117">Met deze opdracht wordt een nieuwe register vermelding ' NoOfEmployees ' toegevoegd aan de sleutel ' mijn bedrijf ' van de component ' HKLM: \ software '.</span><span class="sxs-lookup"><span data-stu-id="aa426-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="aa426-118">Met de eerste opdracht wordt de para meter **Path** gebruikt om het pad van de register sleutel ' mijn bedrijf ' op te geven.</span><span class="sxs-lookup"><span data-stu-id="aa426-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="aa426-119">Hierbij wordt de para meter **name** gebruikt om een naam op te geven voor de vermelding en de para meter **waarde** om de waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="aa426-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="aa426-120">Met de tweede opdracht wordt de `Get-ItemProperty` cmdlet gebruikt om de nieuwe register vermelding te bekijken.</span><span class="sxs-lookup"><span data-stu-id="aa426-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

```powershell
New-ItemProperty -Path "HKLM:\Software\MyCompany" -Name "NoOfEmployees" -Value 822
Get-ItemProperty "HKLM:\Software\MyCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\mycompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : mycompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 822
```

### <span data-ttu-id="aa426-121">Voor beeld 2: een register vermelding toevoegen aan een sleutel</span><span class="sxs-lookup"><span data-stu-id="aa426-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="aa426-122">Met deze opdracht wordt een nieuwe register vermelding toegevoegd aan een register sleutel.</span><span class="sxs-lookup"><span data-stu-id="aa426-122">This command adds a new registry entry to a registry key.</span></span>
<span data-ttu-id="aa426-123">Als u de sleutel wilt opgeven, wordt een pijplijn operator ( `|` ) gebruikt om een object te verzenden dat de sleutel naar vertegenwoordigt `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="aa426-123">To specify the key, it uses a pipeline operator (`|`) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="aa426-124">Het eerste deel van de opdracht gebruikt de `Get-Item` cmdlet om de register sleutel ' mijn bedrijf ' op te halen.</span><span class="sxs-lookup"><span data-stu-id="aa426-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span>
<span data-ttu-id="aa426-125">De pijplijn operator verzendt de resultaten van de opdracht naar `New-ItemProperty` , waarmee de nieuwe register vermelding ("NoOfLocations") en de waarde (3) wordt toegevoegd aan de sleutel "mijn bedrijf".</span><span class="sxs-lookup"><span data-stu-id="aa426-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="aa426-126">Deze opdracht werkt omdat de functie voor het binden van para meters van Power shell het pad van het object koppelt `RegistryKey` dat `Get-Item` retourneert met de para meter **LiteralPath** van `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="aa426-126">This command works because the parameter-binding feature of PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="aa426-127">Zie [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa426-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="aa426-128">Voor beeld 3: een waarde met meerdere teken reeksen in het REGI ster maken met behulp van een Here-String</span><span class="sxs-lookup"><span data-stu-id="aa426-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="aa426-129">In dit voor beeld wordt een waarde met meerdere teken reeksen gemaakt met behulp van een hier-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="aa426-129">This example creates a MultiString value using a Here-String.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'HereString' -PropertyType MultiString -Value @"
This is text which contains newlines
It can also contain "quoted" strings
"@
$newValue.multistring
```

```output
This is text which contains newlines
It can also contain "quoted" strings
```

### <span data-ttu-id="aa426-130">Voor beeld 4: een waarde met meerdere teken reeksen in het REGI ster maken met een matrix</span><span class="sxs-lookup"><span data-stu-id="aa426-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="aa426-131">In het voor beeld ziet u hoe u een matrix met waarden gebruikt om de waarde te maken `MultiString` .</span><span class="sxs-lookup"><span data-stu-id="aa426-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="aa426-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aa426-132">PARAMETERS</span></span>

### <span data-ttu-id="aa426-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="aa426-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="aa426-134">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="aa426-134">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="aa426-135">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aa426-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-136">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="aa426-136">-Exclude</span></span>

<span data-ttu-id="aa426-137">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="aa426-137">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="aa426-138">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="aa426-138">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="aa426-139">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="aa426-139">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="aa426-140">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="aa426-140">Wildcard characters are permitted.</span></span> <span data-ttu-id="aa426-141">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="aa426-141">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aa426-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="aa426-142">-Filter</span></span>

<span data-ttu-id="aa426-143">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="aa426-143">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="aa426-144">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="aa426-144">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="aa426-145">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="aa426-145">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="aa426-146">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="aa426-146">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aa426-147">-Force</span><span class="sxs-lookup"><span data-stu-id="aa426-147">-Force</span></span>

<span data-ttu-id="aa426-148">Hiermee wordt de cmdlet gedwongen een eigenschap te maken voor een object dat niet kan worden gebruikt door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="aa426-148">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="aa426-149">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="aa426-149">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="aa426-150">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa426-150">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-151">-Include</span><span class="sxs-lookup"><span data-stu-id="aa426-151">-Include</span></span>

<span data-ttu-id="aa426-152">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="aa426-152">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="aa426-153">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="aa426-153">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="aa426-154">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="aa426-154">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="aa426-155">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="aa426-155">Wildcard characters are permitted.</span></span> <span data-ttu-id="aa426-156">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="aa426-156">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aa426-157">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="aa426-157">-LiteralPath</span></span>

<span data-ttu-id="aa426-158">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="aa426-158">Specifies a path to one or more locations.</span></span> <span data-ttu-id="aa426-159">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="aa426-159">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="aa426-160">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="aa426-160">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="aa426-161">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="aa426-161">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="aa426-162">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="aa426-162">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="aa426-163">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa426-163">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-164">-Name</span><span class="sxs-lookup"><span data-stu-id="aa426-164">-Name</span></span>

<span data-ttu-id="aa426-165">Hiermee geeft u een naam op voor de nieuwe eigenschap.</span><span class="sxs-lookup"><span data-stu-id="aa426-165">Specifies a name for the new property.</span></span>
<span data-ttu-id="aa426-166">Als de eigenschap een register vermelding is, geeft deze para meter de naam van het item aan.</span><span class="sxs-lookup"><span data-stu-id="aa426-166">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-167">-Path</span><span class="sxs-lookup"><span data-stu-id="aa426-167">-Path</span></span>

<span data-ttu-id="aa426-168">Hiermee geeft u het pad van het item.</span><span class="sxs-lookup"><span data-stu-id="aa426-168">Specifies the path of the item.</span></span>
<span data-ttu-id="aa426-169">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="aa426-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="aa426-170">Met deze para meter wordt het item geïdentificeerd waaraan deze cmdlet de nieuwe eigenschap toevoegt.</span><span class="sxs-lookup"><span data-stu-id="aa426-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aa426-171">-Property type</span><span class="sxs-lookup"><span data-stu-id="aa426-171">-PropertyType</span></span>

<span data-ttu-id="aa426-172">Hiermee geeft u het type eigenschap op dat met deze cmdlet wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="aa426-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="aa426-173">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="aa426-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="aa426-174">**Teken reeks** : Hiermee geeft u een teken reeks met een null-waarde op.</span><span class="sxs-lookup"><span data-stu-id="aa426-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="aa426-175">Gelijk aan **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="aa426-175">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="aa426-176">**ExpandString** : Hiermee geeft u een teken reeks met een null-waarde eindigen die niet-uitgevouwen verwijzingen bevat naar omgevings variabelen die worden uitgebreid wanneer de waarde wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="aa426-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="aa426-177">Gelijk aan **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="aa426-177">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="aa426-178">**Binary** : Hiermee worden binaire gegevens in een wille keurig formulier opgegeven.</span><span class="sxs-lookup"><span data-stu-id="aa426-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="aa426-179">Gelijk aan **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="aa426-179">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="aa426-180">**DWORD** : Hiermee geeft u een 32-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="aa426-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="aa426-181">Gelijk aan **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="aa426-181">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="aa426-182">Meerdere **teken reeksen** : Hiermee geeft u een matrix van teken reeksen met een null-waarde die is beëindigd door twee null-tekens.</span><span class="sxs-lookup"><span data-stu-id="aa426-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="aa426-183">Gelijk aan **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="aa426-183">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="aa426-184">**Qword** : Hiermee geeft u een 64-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="aa426-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="aa426-185">Gelijk aan **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="aa426-185">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="aa426-186">**Onbekend** : Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="aa426-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-187">-Waarde</span><span class="sxs-lookup"><span data-stu-id="aa426-187">-Value</span></span>

<span data-ttu-id="aa426-188">Geeft de waarde van de eigenschap aan.</span><span class="sxs-lookup"><span data-stu-id="aa426-188">Specifies the property value.</span></span>
<span data-ttu-id="aa426-189">Als de eigenschap een register vermelding is, geeft deze para meter de waarde van het item aan.</span><span class="sxs-lookup"><span data-stu-id="aa426-189">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-190">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aa426-190">-Confirm</span></span>

<span data-ttu-id="aa426-191">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aa426-191">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-192">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aa426-192">-WhatIf</span></span>

<span data-ttu-id="aa426-193">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="aa426-193">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="aa426-194">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aa426-194">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aa426-195">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aa426-195">CommonParameters</span></span>

<span data-ttu-id="aa426-196">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="aa426-196">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="aa426-197">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa426-197">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="aa426-198">INVOER</span><span class="sxs-lookup"><span data-stu-id="aa426-198">INPUTS</span></span>

### <span data-ttu-id="aa426-199">Geen</span><span class="sxs-lookup"><span data-stu-id="aa426-199">None</span></span>

<span data-ttu-id="aa426-200">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa426-200">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="aa426-201">UITVOER</span><span class="sxs-lookup"><span data-stu-id="aa426-201">OUTPUTS</span></span>

### <span data-ttu-id="aa426-202">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="aa426-202">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="aa426-203">`New-ItemProperty` retourneert een aangepast object dat de nieuwe eigenschap bevat.</span><span class="sxs-lookup"><span data-stu-id="aa426-203">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="aa426-204">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="aa426-204">NOTES</span></span>

<span data-ttu-id="aa426-205">`New-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="aa426-205">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="aa426-206">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="aa426-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="aa426-207">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aa426-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="aa426-208">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="aa426-208">RELATED LINKS</span></span>

[<span data-ttu-id="aa426-209">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-209">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="aa426-210">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-210">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="aa426-211">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-211">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="aa426-212">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-212">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="aa426-213">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-213">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="aa426-214">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-214">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="aa426-215">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="aa426-215">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="aa426-216">about_Providers</span><span class="sxs-lookup"><span data-stu-id="aa426-216">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
