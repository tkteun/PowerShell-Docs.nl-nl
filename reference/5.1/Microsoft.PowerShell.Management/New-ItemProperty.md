---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ItemProperty
ms.openlocfilehash: 2569f4778f54f6cdad22e10cf92e727b73c323e3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250596"
---
# <span data-ttu-id="02417-103">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="02417-103">New-ItemProperty</span></span>

## <span data-ttu-id="02417-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="02417-104">SYNOPSIS</span></span>
<span data-ttu-id="02417-105">Hiermee maakt u een nieuwe eigenschap voor een item en stelt u de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="02417-105">Creates a new property for an item and sets its value.</span></span>

## <span data-ttu-id="02417-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="02417-106">SYNTAX</span></span>

### <span data-ttu-id="02417-107">Pad (standaard)</span><span class="sxs-lookup"><span data-stu-id="02417-107">Path (Default)</span></span>

```
New-ItemProperty [-Path] <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="02417-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="02417-108">LiteralPath</span></span>

```
New-ItemProperty -LiteralPath <String[]> [-Name] <String> [-PropertyType <String>] [-Value <Object>] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="02417-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="02417-109">DESCRIPTION</span></span>

<span data-ttu-id="02417-110">De `New-ItemProperty` cmdlet maakt een nieuwe eigenschap voor een opgegeven item en stelt de waarde ervan in.</span><span class="sxs-lookup"><span data-stu-id="02417-110">The `New-ItemProperty` cmdlet creates a new property for a specified item and sets its value.</span></span>
<span data-ttu-id="02417-111">Deze cmdlet wordt doorgaans gebruikt om nieuwe register waarden te maken, omdat register waarden eigenschappen van een register sleutel item zijn.</span><span class="sxs-lookup"><span data-stu-id="02417-111">Typically, this cmdlet is used to create new registry values, because registry values are properties of a registry key item.</span></span>

<span data-ttu-id="02417-112">Met deze cmdlet worden geen eigenschappen aan een object toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="02417-112">This cmdlet does not add properties to an object.</span></span>

- <span data-ttu-id="02417-113">Gebruik de cmdlet om een eigenschap toe te voegen aan een exemplaar van een object `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="02417-113">To add a property to an instance of an object, use the `Add-Member` cmdlet.</span></span>
- <span data-ttu-id="02417-114">Als u een eigenschap wilt toevoegen aan alle objecten van een bepaald type, wijzigt u het Types.ps1XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="02417-114">To add a property to all objects of a particular type, modify the Types.ps1xml file.</span></span>

## <span data-ttu-id="02417-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="02417-115">EXAMPLES</span></span>

### <span data-ttu-id="02417-116">Voor beeld 1: een register vermelding toevoegen</span><span class="sxs-lookup"><span data-stu-id="02417-116">Example 1: Add a registry entry</span></span>

<span data-ttu-id="02417-117">Met deze opdracht wordt een nieuwe register vermelding ' NoOfEmployees ' toegevoegd aan de sleutel ' mijn bedrijf ' van de component ' HKLM: \ software '.</span><span class="sxs-lookup"><span data-stu-id="02417-117">This command adds a new registry entry, "NoOfEmployees", to the "MyCompany" key of the "HKLM:\Software hive".</span></span>

<span data-ttu-id="02417-118">Met de eerste opdracht wordt de para meter **Path** gebruikt om het pad van de register sleutel ' mijn bedrijf ' op te geven.</span><span class="sxs-lookup"><span data-stu-id="02417-118">The first command uses the **Path** parameter to specify the path of the "MyCompany" registry key.</span></span>
<span data-ttu-id="02417-119">Hierbij wordt de para meter **name** gebruikt om een naam op te geven voor de vermelding en de para meter **waarde** om de waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="02417-119">It uses the **Name** parameter to specify a name for the entry and the **Value** parameter to specify its value.</span></span>

<span data-ttu-id="02417-120">Met de tweede opdracht wordt de `Get-ItemProperty` cmdlet gebruikt om de nieuwe register vermelding te bekijken.</span><span class="sxs-lookup"><span data-stu-id="02417-120">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span>

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

### <span data-ttu-id="02417-121">Voor beeld 2: een register vermelding toevoegen aan een sleutel</span><span class="sxs-lookup"><span data-stu-id="02417-121">Example 2: Add a registry entry to a key</span></span>

<span data-ttu-id="02417-122">Met deze opdracht wordt een nieuwe register vermelding toegevoegd aan een register sleutel.</span><span class="sxs-lookup"><span data-stu-id="02417-122">This command adds a new registry entry to a registry key.</span></span> <span data-ttu-id="02417-123">Als u de sleutel wilt opgeven, gebruikt deze een pijplijn operator (|) om een object te verzenden dat de sleutel naar vertegenwoordigt `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="02417-123">To specify the key, it uses a pipeline operator (|) to send an object that represents the key to `New-ItemProperty`.</span></span>

<span data-ttu-id="02417-124">Het eerste deel van de opdracht gebruikt de `Get-Item` cmdlet om de register sleutel ' mijn bedrijf ' op te halen.</span><span class="sxs-lookup"><span data-stu-id="02417-124">The first part of the command uses the `Get-Item` cmdlet to get the "MyCompany" registry key.</span></span> <span data-ttu-id="02417-125">De pijplijn operator verzendt de resultaten van de opdracht naar `New-ItemProperty` , waarmee de nieuwe register vermelding ("NoOfLocations") en de waarde (3) wordt toegevoegd aan de sleutel "mijn bedrijf".</span><span class="sxs-lookup"><span data-stu-id="02417-125">The pipeline operator sends the results of the command to `New-ItemProperty`, which adds the new registry entry ("NoOfLocations"), and its value (3), to the "MyCompany" key.</span></span>

```powershell
Get-Item -Path "HKLM:\Software\MyCompany" | New-ItemProperty -Name NoOfLocations -Value 3
```

<span data-ttu-id="02417-126">Deze opdracht werkt omdat de functie voor het binden van para meters van Windows Power shell het pad van het object koppelt `RegistryKey` dat `Get-Item` retourneert met de para meter **LiteralPath** van `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="02417-126">This command works because the parameter-binding feature of Windows PowerShell associates the path of the `RegistryKey` object that `Get-Item` returns with the **LiteralPath** parameter of `New-ItemProperty`.</span></span> <span data-ttu-id="02417-127">Zie [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02417-127">For more information, see [about_Pipelines](../Microsoft.PowerShell.Core/About/about_pipelines.md).</span></span>

### <span data-ttu-id="02417-128">Voor beeld 3: een waarde met meerdere teken reeksen in het REGI ster maken met behulp van een Here-String</span><span class="sxs-lookup"><span data-stu-id="02417-128">Example 3: Create a MultiString value in the registry using a Here-String</span></span>

<span data-ttu-id="02417-129">In dit voor beeld wordt een waarde met meerdere teken reeksen gemaakt met behulp van een hier-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="02417-129">This example creates a MultiString value using a Here-String.</span></span>

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

### <span data-ttu-id="02417-130">Voor beeld 4: een waarde met meerdere teken reeksen in het REGI ster maken met een matrix</span><span class="sxs-lookup"><span data-stu-id="02417-130">Example 4: Create a MultiString value in the registry using an array</span></span>

<span data-ttu-id="02417-131">In het voor beeld ziet u hoe u een matrix met waarden gebruikt om de waarde te maken `MultiString` .</span><span class="sxs-lookup"><span data-stu-id="02417-131">The example shows how to use an array of values to create the `MultiString` value.</span></span>

```powershell
$newValue = New-ItemProperty -Path "HKLM:\SOFTWARE\ContosoCompany\" -Name 'MultiString' -PropertyType MultiString -Value ('a','b','c')
$newValue.multistring[0]
```

```output
a
```

## <span data-ttu-id="02417-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="02417-132">PARAMETERS</span></span>

### <span data-ttu-id="02417-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="02417-133">-Credential</span></span>

<span data-ttu-id="02417-134">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="02417-134">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="02417-135">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="02417-135">The default is the current user.</span></span>

<span data-ttu-id="02417-136">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02417-136">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="02417-137">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="02417-137">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="02417-138">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="02417-138">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="02417-139">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02417-139">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="02417-140">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="02417-140">-Exclude</span></span>

<span data-ttu-id="02417-141">Hiermee geeft u als een teken reeks matrix een eigenschap of eigenschap op die met deze cmdlet wordt uitgesloten van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="02417-141">Specifies, as a string array, a property or property that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="02417-142">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="02417-142">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="02417-143">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="02417-143">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="02417-144">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02417-144">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="02417-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="02417-145">-Filter</span></span>

<span data-ttu-id="02417-146">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="02417-146">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="02417-147">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="02417-147">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="02417-148">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="02417-148">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="02417-149">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="02417-149">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="02417-150">-Force</span><span class="sxs-lookup"><span data-stu-id="02417-150">-Force</span></span>

<span data-ttu-id="02417-151">Hiermee wordt de cmdlet gedwongen een eigenschap te maken voor een object dat niet kan worden gebruikt door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="02417-151">Forces the cmdlet to create a property on an object that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="02417-152">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="02417-152">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="02417-153">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02417-153">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="02417-154">-Include</span><span class="sxs-lookup"><span data-stu-id="02417-154">-Include</span></span>

<span data-ttu-id="02417-155">Hiermee wordt een teken reeks matrix opgegeven, een item of items die met deze cmdlet in de bewerking zijn opgenomen.</span><span class="sxs-lookup"><span data-stu-id="02417-155">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="02417-156">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="02417-156">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="02417-157">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="02417-157">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="02417-158">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="02417-158">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="02417-159">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="02417-159">-LiteralPath</span></span>

<span data-ttu-id="02417-160">Hiermee geeft u het pad op naar de huidige locatie van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="02417-160">Specifies the path to the current location of the property.</span></span>
<span data-ttu-id="02417-161">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="02417-161">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="02417-162">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="02417-162">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="02417-163">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="02417-163">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="02417-164">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="02417-164">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="02417-165">-Name</span><span class="sxs-lookup"><span data-stu-id="02417-165">-Name</span></span>

<span data-ttu-id="02417-166">Hiermee geeft u een naam op voor de nieuwe eigenschap.</span><span class="sxs-lookup"><span data-stu-id="02417-166">Specifies a name for the new property.</span></span>
<span data-ttu-id="02417-167">Als de eigenschap een register vermelding is, geeft deze para meter de naam van het item aan.</span><span class="sxs-lookup"><span data-stu-id="02417-167">If the property is a registry entry, this parameter specifies the name of the entry.</span></span>

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

### <span data-ttu-id="02417-168">-Path</span><span class="sxs-lookup"><span data-stu-id="02417-168">-Path</span></span>

<span data-ttu-id="02417-169">Hiermee geeft u het pad van het item.</span><span class="sxs-lookup"><span data-stu-id="02417-169">Specifies the path of the item.</span></span>
<span data-ttu-id="02417-170">Met deze para meter wordt het item geïdentificeerd waaraan deze cmdlet de nieuwe eigenschap toevoegt.</span><span class="sxs-lookup"><span data-stu-id="02417-170">This parameter identifies the item to which this cmdlet adds the new property.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="02417-171">-Property type</span><span class="sxs-lookup"><span data-stu-id="02417-171">-PropertyType</span></span>

<span data-ttu-id="02417-172">Hiermee geeft u het type eigenschap op dat met deze cmdlet wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="02417-172">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="02417-173">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="02417-173">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="02417-174">**Teken reeks** : Hiermee geeft u een teken reeks met een null-waarde op.</span><span class="sxs-lookup"><span data-stu-id="02417-174">**String** : Specifies a null-terminated string.</span></span> <span data-ttu-id="02417-175">Gelijk aan **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="02417-175">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="02417-176">**ExpandString** : Hiermee geeft u een teken reeks met een null-waarde eindigen die niet-uitgevouwen verwijzingen bevat naar omgevings variabelen die worden uitgebreid wanneer de waarde wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="02417-176">**ExpandString** : Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="02417-177">Gelijk aan **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="02417-177">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="02417-178">**Binary** : Hiermee worden binaire gegevens in een wille keurig formulier opgegeven.</span><span class="sxs-lookup"><span data-stu-id="02417-178">**Binary** : Specifies binary data in any form.</span></span> <span data-ttu-id="02417-179">Gelijk aan **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="02417-179">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="02417-180">**DWORD** : Hiermee geeft u een 32-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="02417-180">**DWord** : Specifies a 32-bit binary number.</span></span> <span data-ttu-id="02417-181">Gelijk aan **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="02417-181">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="02417-182">Meerdere **teken reeksen** : Hiermee geeft u een matrix van teken reeksen met een null-waarde die is beëindigd door twee null-tekens.</span><span class="sxs-lookup"><span data-stu-id="02417-182">**MultiString** : Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="02417-183">Gelijk aan **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="02417-183">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="02417-184">**Qword** : Hiermee geeft u een 64-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="02417-184">**Qword** : Specifies a 64-bit binary number.</span></span> <span data-ttu-id="02417-185">Gelijk aan **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="02417-185">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="02417-186">**Onbekend** : Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="02417-186">**Unknown** : Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

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

### <span data-ttu-id="02417-187">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="02417-187">-UseTransaction</span></span>

<span data-ttu-id="02417-188">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="02417-188">Includes the command in the active transaction.</span></span>
<span data-ttu-id="02417-189">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02417-189">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="02417-190">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02417-190">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="02417-191">-Waarde</span><span class="sxs-lookup"><span data-stu-id="02417-191">-Value</span></span>

<span data-ttu-id="02417-192">Geeft de waarde van de eigenschap aan.</span><span class="sxs-lookup"><span data-stu-id="02417-192">Specifies the property value.</span></span>
<span data-ttu-id="02417-193">Als de eigenschap een register vermelding is, geeft deze para meter de waarde van het item aan.</span><span class="sxs-lookup"><span data-stu-id="02417-193">If the property is a registry entry, this parameter specifies the value of the entry.</span></span>

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

### <span data-ttu-id="02417-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="02417-194">-Confirm</span></span>

<span data-ttu-id="02417-195">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02417-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="02417-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="02417-196">-WhatIf</span></span>

<span data-ttu-id="02417-197">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="02417-197">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="02417-198">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="02417-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="02417-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="02417-199">CommonParameters</span></span>

<span data-ttu-id="02417-200">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="02417-200">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="02417-201">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02417-201">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="02417-202">INVOER</span><span class="sxs-lookup"><span data-stu-id="02417-202">INPUTS</span></span>

### <span data-ttu-id="02417-203">Geen</span><span class="sxs-lookup"><span data-stu-id="02417-203">None</span></span>

<span data-ttu-id="02417-204">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="02417-204">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="02417-205">UITVOER</span><span class="sxs-lookup"><span data-stu-id="02417-205">OUTPUTS</span></span>

### <span data-ttu-id="02417-206">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="02417-206">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="02417-207">`New-ItemProperty` retourneert een aangepast object dat de nieuwe eigenschap bevat.</span><span class="sxs-lookup"><span data-stu-id="02417-207">`New-ItemProperty` returns a custom object that contains the new property.</span></span>

## <span data-ttu-id="02417-208">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="02417-208">NOTES</span></span>

<span data-ttu-id="02417-209">`New-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="02417-209">`New-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="02417-210">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="02417-210">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="02417-211">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="02417-211">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="02417-212">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="02417-212">RELATED LINKS</span></span>

[<span data-ttu-id="02417-213">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-213">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="02417-214">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-214">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="02417-215">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-215">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="02417-216">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-216">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="02417-217">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-217">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="02417-218">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-218">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="02417-219">Set-item Property</span><span class="sxs-lookup"><span data-stu-id="02417-219">Set-ItemProperty</span></span>](Set-ItemProperty.md)

[<span data-ttu-id="02417-220">about_Providers</span><span class="sxs-lookup"><span data-stu-id="02417-220">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
