---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 59b7ea7f675d72dd90d970306c60107bd3f1de87
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705479"
---
# <span data-ttu-id="9c1bc-102">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="9c1bc-102">New-ItemProperty</span></span>

## <span data-ttu-id="9c1bc-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9c1bc-103">SYNOPSIS</span></span>
<span data-ttu-id="9c1bc-104">Hiermee maakt u een nieuwe eigenschap voor een item en stelt u de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-104">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="9c1bc-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9c1bc-105">SYNTAX</span></span>

### <span data-ttu-id="9c1bc-106">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="9c1bc-106">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c1bc-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c1bc-107">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9c1bc-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9c1bc-108">DESCRIPTION</span></span>

<span data-ttu-id="9c1bc-109">De `New-ItemProperty` cmdlet maakt een nieuwe eigenschap voor een opgegeven item en stelt de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-109">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="9c1bc-110">Deze cmdlet wordt doorgaans gebruikt om nieuwe register waarden te maken, omdat register waarden eigenschappen van een register sleutel item zijn.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-110">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="9c1bc-111">Met deze cmdlet worden geen eigenschappen aan een object toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-111">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="9c1bc-112">Gebruik de cmdlet om een eigenschap toe te voegen aan een exemplaar van een object `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-112">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="9c1bc-113">Als u een eigenschap wilt toevoegen aan alle objecten van een bepaald type, wijzigt u het Types.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-113">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="9c1bc-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9c1bc-114">EXAMPLES</span></span>

### <span data-ttu-id="9c1bc-115">Voor beeld 1: een register vermelding toevoegen</span><span class="sxs-lookup"><span data-stu-id="9c1bc-115">Example 1: Add a registry entry</span></span>

<span data-ttu-id="9c1bc-116">Met deze opdracht wordt een nieuwe register vermelding ' NoOfEmployees ' toegevoegd aan de sleutel ' mijn bedrijf ' van de component ' HKLM: \ software '.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-116">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="9c1bc-117">Met de eerste opdracht wordt de para meter **Path** gebruikt om het pad van de register sleutel ' mijn bedrijf ' op te geven.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-117">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="9c1bc-118">Hierbij wordt de para meter **name** gebruikt om een naam op te geven voor de vermelding en de para meter **waarde** om de waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-118">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="9c1bc-119">Met de tweede opdracht wordt de `Get-ItemProperty` cmdlet gebruikt om de nieuwe register vermelding te bekijken.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-119">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

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

### <span data-ttu-id="9c1bc-120">Voor beeld 2: een register vermelding toevoegen aan een sleutel</span><span class="sxs-lookup"><span data-stu-id="9c1bc-120">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="9c1bc-121">Met deze opdracht wordt een nieuwe register vermelding toegevoegd aan een register sleutel.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-121">This command adds a new registry entry to a registry key.</span></span>
<span data-ttu-id="9c1bc-122">Als u de sleutel wilt opgeven, wordt een pijplijn operator ( `|` ) gebruikt om een object te verzenden dat de sleutel naar vertegenwoordigt `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-122">To specify the key, it uses a pipeline operator (`|`) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="9c1bc-123">Het eerste deel van de opdracht gebruikt de `Get-Item` cmdlet om de register sleutel ' mijn bedrijf ' op te halen.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-123">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span>
<span data-ttu-id="9c1bc-124">De pijplijn operator verzendt de resultaten van de opdracht naar `New-ItemProperty` , waarmee de nieuwe register vermelding ("NoOfLocations") en de waarde (3) wordt toegevoegd aan de sleutel "mijn bedrijf".</span><span class="sxs-lookup"><span data-stu-id="9c1bc-124">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="9c1bc-125">Deze opdracht werkt omdat de functie voor het binden van para meters van Power shell het pad van het object koppelt `RegistryKey` dat `Get-Item` retourneert met de para meter **LiteralPath** van `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-125">This command works because the parameter-binding feature of PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="9c1bc-126">Zie [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-126">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="9c1bc-127">Voor beeld 3: een waarde met meerdere teken reeksen in het REGI ster maken met behulp van een Here-String</span><span class="sxs-lookup"><span data-stu-id="9c1bc-127">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="9c1bc-128">In dit voor beeld wordt een waarde met meerdere teken reeksen gemaakt met behulp van een hier-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-128">This example creates a MultiString value using a Here-String.</span></span>

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

### <span data-ttu-id="9c1bc-129">Voor beeld 4: een waarde met meerdere teken reeksen in het REGI ster maken met een matrix</span><span class="sxs-lookup"><span data-stu-id="9c1bc-129">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="9c1bc-130">In het voor beeld ziet u hoe u een matrix met waarden gebruikt om de waarde te maken `MultiString` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-130">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="9c1bc-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c1bc-131">PARAMETERS</span></span>

### <span data-ttu-id="9c1bc-132">-Credential</span><span class="sxs-lookup"><span data-stu-id="9c1bc-132">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9c1bc-133">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-133">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9c1bc-134">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-134">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9c1bc-135">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="9c1bc-135">-Exclude</span></span>

<span data-ttu-id="9c1bc-136">Hiermee geeft u als een teken reeks matrix een item of items die met deze cmdlet worden uitgesloten in de bewerking.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-136">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="9c1bc-137">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-137">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9c1bc-138">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-138">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="9c1bc-139">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-139">Wildcard characters are permitted.</span></span> <span data-ttu-id="9c1bc-140">De **exclude** -para meter is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-140">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9c1bc-141">-Filter</span><span class="sxs-lookup"><span data-stu-id="9c1bc-141">-Filter</span></span>

<span data-ttu-id="9c1bc-142">Hiermee geeft u een filter op om de para meter **Path** te kwalificeren.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-142">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="9c1bc-143">De [File System](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) -provider is de enige geïnstalleerde Power shell-provider die het gebruik van filters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-143">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="9c1bc-144">U kunt de syntaxis voor de filter taal van het **Bestands systeem** in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)vinden.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-144">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="9c1bc-145">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-145">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="9c1bc-146">-Force</span><span class="sxs-lookup"><span data-stu-id="9c1bc-146">-Force</span></span>

<span data-ttu-id="9c1bc-147">Hiermee wordt de cmdlet gedwongen een eigenschap te maken voor een object dat niet kan worden gebruikt door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-147">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="9c1bc-148">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-148">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="9c1bc-149">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-149">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="9c1bc-150">-Include</span><span class="sxs-lookup"><span data-stu-id="9c1bc-150">-Include</span></span>

<span data-ttu-id="9c1bc-151">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-151">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="9c1bc-152">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="9c1bc-153">Voer een element of patroon van een pad in, zoals `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-153">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="9c1bc-154">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-154">Wildcard characters are permitted.</span></span> <span data-ttu-id="9c1bc-155">De para meter **include** is alleen effectief wanneer de inhoud van een item wordt opgenomen, zoals `C:\Windows\*` , waarbij het Joker teken de inhoud van de `C:\Windows` map bevat.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-155">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="9c1bc-156">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c1bc-156">-LiteralPath</span></span>

<span data-ttu-id="9c1bc-157">Hiermee geeft u een pad naar een of meer locaties.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-157">Specifies a path to one or more locations.</span></span> <span data-ttu-id="9c1bc-158">De waarde van **LiteralPath** wordt precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-158">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="9c1bc-159">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-159">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="9c1bc-160">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-160">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9c1bc-161">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-161">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="9c1bc-162">Zie [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-162">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="9c1bc-163">-Name</span><span class="sxs-lookup"><span data-stu-id="9c1bc-163">-Name</span></span>

<span data-ttu-id="9c1bc-164">Hiermee geeft u een naam op voor de nieuwe eigenschap.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-164">Specifies a name for the new property.</span></span>
<span data-ttu-id="9c1bc-165">Als de eigenschap een register vermelding is, geeft deze para meter de naam van het item aan.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-165">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

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

### <span data-ttu-id="9c1bc-166">-Path</span><span class="sxs-lookup"><span data-stu-id="9c1bc-166">-Path</span></span>

<span data-ttu-id="9c1bc-167">Hiermee geeft u het pad van het item.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-167">Specifies the path of the item.</span></span>
<span data-ttu-id="9c1bc-168">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-168">Wildcard characters are permitted.</span></span>
<span data-ttu-id="9c1bc-169">Met deze para meter wordt het item geïdentificeerd waaraan deze cmdlet de nieuwe eigenschap toevoegt.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-169">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

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

### <span data-ttu-id="9c1bc-170">-Property type</span><span class="sxs-lookup"><span data-stu-id="9c1bc-170">-PropertyType</span></span>

<span data-ttu-id="9c1bc-171">Hiermee geeft u het type eigenschap op dat met deze cmdlet wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-171">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="9c1bc-172">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="9c1bc-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9c1bc-173">**Teken reeks**: Hiermee geeft u een teken reeks met een null-waarde op.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-173">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="9c1bc-174">Gelijk aan **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-174">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="9c1bc-175">**ExpandString**: Hiermee geeft u een teken reeks met een null-waarde eindigen die niet-uitgevouwen verwijzingen bevat naar omgevings variabelen die worden uitgebreid wanneer de waarde wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-175">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="9c1bc-176">Gelijk aan **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-176">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="9c1bc-177">**Binary**: Hiermee worden binaire gegevens in een wille keurig formulier opgegeven.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-177">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="9c1bc-178">Gelijk aan **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-178">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="9c1bc-179">**DWORD**: Hiermee geeft u een 32-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-179">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="9c1bc-180">Gelijk aan **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-180">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="9c1bc-181">Meerdere **teken reeksen**: Hiermee geeft u een matrix van teken reeksen met een null-waarde die is beëindigd door twee null-tekens.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-181">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="9c1bc-182">Gelijk aan **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-182">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="9c1bc-183">**Qword**: Hiermee geeft u een 64-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-183">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="9c1bc-184">Gelijk aan **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-184">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="9c1bc-185">**Onbekend**: Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-185">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

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

### <span data-ttu-id="9c1bc-186">-Waarde</span><span class="sxs-lookup"><span data-stu-id="9c1bc-186">-Value</span></span>

<span data-ttu-id="9c1bc-187">Geeft de waarde van de eigenschap aan.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-187">Specifies the property value.</span></span>
<span data-ttu-id="9c1bc-188">Als de eigenschap een register vermelding is, geeft deze para meter de waarde van het item aan.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-188">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

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

### <span data-ttu-id="9c1bc-189">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c1bc-189">-Confirm</span></span>

<span data-ttu-id="9c1bc-190">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-190">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c1bc-191">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c1bc-191">-WhatIf</span></span>

<span data-ttu-id="9c1bc-192">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-192">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9c1bc-193">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-193">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c1bc-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c1bc-194">CommonParameters</span></span>

<span data-ttu-id="9c1bc-195">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-195">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="9c1bc-196">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-196">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="9c1bc-197">INVOER</span><span class="sxs-lookup"><span data-stu-id="9c1bc-197">INPUTS</span></span>

### <span data-ttu-id="9c1bc-198">Geen</span><span class="sxs-lookup"><span data-stu-id="9c1bc-198">None</span></span>

<span data-ttu-id="9c1bc-199">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-199">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9c1bc-200">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9c1bc-200">OUTPUTS</span></span>

### <span data-ttu-id="9c1bc-201">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="9c1bc-201">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="9c1bc-202">`New-ItemProperty` retourneert een aangepast object dat de nieuwe eigenschap bevat.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-202">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="9c1bc-203">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9c1bc-203">NOTES</span></span>

<span data-ttu-id="9c1bc-204">`New-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-204">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="9c1bc-205">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="9c1bc-205">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="9c1bc-206">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9c1bc-206">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="9c1bc-207">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9c1bc-207">RELATED LINKS</span></span>

[<span data-ttu-id="9c1bc-208">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-208">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="9c1bc-209">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-209">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="9c1bc-210">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-210">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="9c1bc-211">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-211">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="9c1bc-212">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-212">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="9c1bc-213">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-213">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="9c1bc-214">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="9c1bc-214">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="9c1bc-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9c1bc-215">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

