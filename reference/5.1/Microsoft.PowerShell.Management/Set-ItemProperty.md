---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ItemProperty
ms.openlocfilehash: cbd1229721650823d9780517934c40a2287f4227
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692672"
---
# <span data-ttu-id="f8ca1-103">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="f8ca1-103">Set-ItemProperty</span></span>

## <span data-ttu-id="f8ca1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f8ca1-104">SYNOPSIS</span></span>
<span data-ttu-id="f8ca1-105">Hiermee wordt de waarde van een eigenschap van een item gemaakt of gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-105">Creates or changes the value of a property of an item.</span></span>

## <span data-ttu-id="f8ca1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f8ca1-106">SYNTAX</span></span>

### <span data-ttu-id="f8ca1-107">propertyValuePathSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="f8ca1-107">propertyValuePathSet (Default)</span></span>

```
Set-ItemProperty [-Path] <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="f8ca1-108">propertyPSObjectPathSet</span><span class="sxs-lookup"><span data-stu-id="f8ca1-108">propertyPSObjectPathSet</span></span>

```
Set-ItemProperty [-Path] <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="f8ca1-109">propertyValueLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="f8ca1-109">propertyValueLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> [-Name] <String> [-Value] <Object> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="f8ca1-110">propertyPSObjectLiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="f8ca1-110">propertyPSObjectLiteralPathSet</span></span>

```
Set-ItemProperty -LiteralPath <String[]> -InputObject <PSObject> [-PassThru] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="f8ca1-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f8ca1-111">DESCRIPTION</span></span>

<span data-ttu-id="f8ca1-112">Met de `Set-ItemProperty` cmdlet wordt de waarde van de eigenschap van het opgegeven item gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-112">The `Set-ItemProperty` cmdlet changes the value of the property of the specified item.</span></span> <span data-ttu-id="f8ca1-113">U kunt de-cmdlet gebruiken om de eigenschappen van items te bepalen of te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-113">You can use the cmdlet to establish or change the properties of items.</span></span> <span data-ttu-id="f8ca1-114">U kunt bijvoorbeeld gebruiken `Set-ItemProperty` om de waarde van de eigenschap **IsReadOnly** van een File-object in te stellen op `$True` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-114">For example, you can use `Set-ItemProperty` to set the value of the **IsReadOnly** property of a file object to `$True`.</span></span>

<span data-ttu-id="f8ca1-115">U kunt ook gebruiken `Set-ItemProperty` om register waarden en-gegevens te maken en te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-115">You also use `Set-ItemProperty` to create and change registry values and data.</span></span>
<span data-ttu-id="f8ca1-116">U kunt bijvoorbeeld een nieuwe register vermelding toevoegen aan een sleutel en de waarde ervan instellen of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-116">For example, you can add a new registry entry to a key and establish or change its value.</span></span>

## <span data-ttu-id="f8ca1-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f8ca1-117">EXAMPLES</span></span>

### <span data-ttu-id="f8ca1-118">Voor beeld 1: een eigenschap van een bestand instellen</span><span class="sxs-lookup"><span data-stu-id="f8ca1-118">Example 1: Set a property of a file</span></span>

<span data-ttu-id="f8ca1-119">Met deze opdracht wordt de waarde van de eigenschap **IsReadOnly** van het bestand ' final.doc ' ingesteld op ' True '.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-119">This command sets the value of the **IsReadOnly** property of the "final.doc" file to "true".</span></span> <span data-ttu-id="f8ca1-120">Het **pad** wordt gebruikt om het bestand op te geven, de **naam** op te geven van de naam van de eigenschap en de **waarde** para meter om de nieuwe waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-120">It uses **Path** to specify the file, **Name** to specify the name of the property, and the **Value** parameter to specify the new value.</span></span>

<span data-ttu-id="f8ca1-121">Het bestand is een **System. io. file info** -object en **IsReadOnly** is slechts een van de eigenschappen ervan.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-121">The file is a **System.IO.FileInfo** object and **IsReadOnly** is just one of its properties.</span></span>
<span data-ttu-id="f8ca1-122">Als u alle eigenschappen wilt weer geven, typt u `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-122">To see all of the properties, type `Get-Item C:\GroupFiles\final.doc | Get-Member -MemberType Property`.</span></span>

<span data-ttu-id="f8ca1-123">De `$true` Automatische variabele vertegenwoordigt de waarde ' True '.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-123">The `$true` automatic variable represents a value of "TRUE".</span></span>
<span data-ttu-id="f8ca1-124">Zie [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-124">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
Set-ItemProperty -Path C:\GroupFiles\final.doc -Name IsReadOnly -Value $true
```

### <span data-ttu-id="f8ca1-125">Voor beeld 2: een register vermelding en-waarde maken</span><span class="sxs-lookup"><span data-stu-id="f8ca1-125">Example 2: Create a registry entry and value</span></span>

<span data-ttu-id="f8ca1-126">In dit voor beeld ziet u hoe u kunt gebruiken `Set-ItemProperty` om een nieuwe register vermelding te maken en een waarde aan de vermelding toe te wijzen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-126">This example shows how to use `Set-ItemProperty` to create a new registry entry and to assign a value to the entry.</span></span> <span data-ttu-id="f8ca1-127">Hiermee wordt de vermelding ' NoOfEmployees ' gemaakt in de sleutel ' ContosoCompany ' in de sleutel ' HKLM\Software ' en wordt de waarde ervan ingesteld op 823.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-127">It creates the "NoOfEmployees" entry in the "ContosoCompany" key in "HKLM\Software" key and sets its value to 823.</span></span>

<span data-ttu-id="f8ca1-128">Omdat Register vermeldingen worden beschouwd als eigenschappen van de register sleutels, die items zijn, kunt u gebruiken `Set-ItemProperty` om Register vermeldingen te maken en om hun waarden te bepalen en te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-128">Because registry entries are considered to be properties of the registry keys, which are items, you use `Set-ItemProperty` to create registry entries, and to establish and change their values.</span></span>

<span data-ttu-id="f8ca1-129">Met de eerste opdracht wordt de register vermelding gemaakt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-129">The first command creates the registry entry.</span></span>
<span data-ttu-id="f8ca1-130">Het **pad** wordt gebruikt om het pad van het `HKLM:` station en de sleutel ' Software\MyCompany ' op te geven.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-130">It uses **Path** to specify the path of the `HKLM:` drive and the "Software\MyCompany" key.</span></span>
<span data-ttu-id="f8ca1-131">De opdracht gebruikt de **naam** om de naam en **waarde** van het item op te geven om een waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-131">The command uses **Name** to specify the entry name and **Value** to specify a value.</span></span>

<span data-ttu-id="f8ca1-132">Met de tweede opdracht wordt de `Get-ItemProperty` cmdlet gebruikt om de nieuwe register vermelding te bekijken.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-132">The second command uses the `Get-ItemProperty` cmdlet to see the new registry entry.</span></span> <span data-ttu-id="f8ca1-133">Als u de `Get-Item` `Get-ChildItem` cmdlets of gebruikt, worden de vermeldingen niet weer gegeven omdat ze eigenschappen van een sleutel, geen items of onderliggende items zijn.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-133">If you use the `Get-Item` or `Get-ChildItem` cmdlets, the entries do not appear because they are properties of a key, not items or child items.</span></span>

<span data-ttu-id="f8ca1-134">Met de derde opdracht wordt de waarde van de vermelding **NoOfEmployees** gewijzigd in 824.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-134">The third command changes the value of the **NoOfEmployees** entry to 824.</span></span>

<span data-ttu-id="f8ca1-135">U kunt ook de- `New-ItemProperty` cmdlet gebruiken om de register vermelding en de waarde ervan te maken en vervolgens `Set-ItemProperty` de waarde te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-135">You can also use the `New-ItemProperty` cmdlet to create the registry entry and its value and then use `Set-ItemProperty` to change the value.</span></span>

<span data-ttu-id="f8ca1-136">Typ voor meer informatie over het `HKLM:` station `Get-Help Get-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-136">For more information about the `HKLM:` drive, type `Get-Help Get-PSDrive`.</span></span>
<span data-ttu-id="f8ca1-137">Als u meer informatie wilt over het gebruik van Power shell voor het beheren van het REGI ster, typt u `Get-Help Registry` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-137">For more information about how to use PowerShell to manage the registry, type `Get-Help Registry`.</span></span>

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 823
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 823

```

```powershell
Set-ItemProperty -Path "HKLM:\Software\ContosoCompany" -Name "NoOfEmployees" -Value 824
Get-ItemProperty -Path "HKLM:\Software\ContosoCompany"
```

```output
PSPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software\contosocompany
PSParentPath  : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\software
PSChildName   : contosocompany
PSDrive       : HKLM
PSProvider    : Microsoft.PowerShell.Core\Registry
NoOfLocations : 2
NoOfEmployees : 824
```

### <span data-ttu-id="f8ca1-138">Voor beeld 3: een item wijzigen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="f8ca1-138">Example 3: Modify an item by using the pipeline</span></span>

<span data-ttu-id="f8ca1-139">Deze opdrachten laten zien hoe u een pijplijn operator () kunt gebruiken `|` voor het verzenden van een item naar `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-139">These commands show how to use a pipeline operator (`|`) to send an item to `Set-ItemProperty`.</span></span>

<span data-ttu-id="f8ca1-140">Het eerste deel van de opdracht wordt gebruikt `Get-ChildItem` om een object op te halen dat het bestand ' Weekly.txt ' vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-140">The first part of the command uses `Get-ChildItem` to get an object that represents the "Weekly.txt" file.</span></span>
<span data-ttu-id="f8ca1-141">De opdracht maakt gebruik van een pijplijn operator om het bestands object naar te verzenden `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-141">The command uses a pipeline operator to send the file object to `Set-ItemProperty`.</span></span>
<span data-ttu-id="f8ca1-142">De `Set-ItemProperty` opdracht maakt gebruik van de para meters **name** en **Value** om de eigenschap en de nieuwe waarde op te geven.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-142">The `Set-ItemProperty` command uses the **Name** and **Value** parameters to specify the property and its new value.</span></span>

<span data-ttu-id="f8ca1-143">Deze opdracht is gelijk aan het gebruik van de para meter **input object** om het object op te geven dat `Get-ChildItem` wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-143">This command is equivalent to using the **InputObject** parameter to specify the object that `Get-ChildItem` gets.</span></span>

```powershell
Get-ChildItem weekly.txt | Set-ItemProperty -Name IsReadOnly -Value $True
```

## <span data-ttu-id="f8ca1-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f8ca1-144">PARAMETERS</span></span>

### <span data-ttu-id="f8ca1-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="f8ca1-145">-Credential</span></span>

<span data-ttu-id="f8ca1-146">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-146">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="f8ca1-147">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-147">The default is the current user.</span></span>

<span data-ttu-id="f8ca1-148">Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de `Get-Credential` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-148">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>
<span data-ttu-id="f8ca1-149">Als u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-149">If you type a user name, you are prompted for a password.</span></span>

> [!NOTE]
> <span data-ttu-id="f8ca1-150">Deze para meter wordt niet ondersteund door providers die zijn geïnstalleerd met Power shell.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-150">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="f8ca1-151">Gebruik [invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md)om een andere gebruiker te imiteren of uw referenties te verhogen wanneer u deze cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-151">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="f8ca1-152">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="f8ca1-152">-Exclude</span></span>

<span data-ttu-id="f8ca1-153">Hiermee geeft u de items op waarop de cmdlet niet van toepassing is en die alle andere bevat.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-153">Specifies those items upon which the cmdlet does not act, and includes all others.</span></span>
<span data-ttu-id="f8ca1-154">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-154">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="f8ca1-155">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-155">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="f8ca1-156">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-156">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f8ca1-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="f8ca1-157">-Filter</span></span>

<span data-ttu-id="f8ca1-158">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-158">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="f8ca1-159">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-159">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="f8ca1-160">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-160">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="f8ca1-161">Filters zijn efficiënter dan andere para meters, omdat deze door de provider worden toegepast wanneer de cmdlet de objecten ophaalt in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-161">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f8ca1-162">-Force</span><span class="sxs-lookup"><span data-stu-id="f8ca1-162">-Force</span></span>

<span data-ttu-id="f8ca1-163">Hiermee wordt de cmdlet gedwongen een eigenschap in te stellen voor items die anders niet toegankelijk zijn voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-163">Forces the cmdlet to set a property on items that cannot otherwise be accessed by the user.</span></span>
<span data-ttu-id="f8ca1-164">De implementatie varieert van provider tot provider.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-164">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="f8ca1-165">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-165">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="f8ca1-166">-Include</span><span class="sxs-lookup"><span data-stu-id="f8ca1-166">-Include</span></span>

<span data-ttu-id="f8ca1-167">Hiermee geeft u alleen de items op waarvoor de cmdlet reageert, waarbij alle andere worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-167">Specifies only those items upon which the cmdlet acts, which excludes all others.</span></span>
<span data-ttu-id="f8ca1-168">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-168">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="f8ca1-169">Voer een element of patroon van een pad in, zoals \*. txt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-169">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="f8ca1-170">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-170">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f8ca1-171">-Input object</span><span class="sxs-lookup"><span data-stu-id="f8ca1-171">-InputObject</span></span>

<span data-ttu-id="f8ca1-172">Hiermee geeft u het object op dat de eigenschappen bevat die met deze cmdlet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-172">Specifies the object that has the properties that this cmdlet changes.</span></span>
<span data-ttu-id="f8ca1-173">Voer een variabele in die het object of een opdracht bevat die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-173">Enter a variable that contains the object or a command that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: propertyPSObjectPathSet, propertyPSObjectLiteralPathSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f8ca1-174">-LiteralPath</span></span>

<span data-ttu-id="f8ca1-175">Hiermee geeft u een pad van de eigenschap item op.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-175">Specifies a path of the item property.</span></span>
<span data-ttu-id="f8ca1-176">In tegens telling tot de para meter **Path** wordt de waarde van **LiteralPath** precies zo gebruikt als deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-176">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="f8ca1-177">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-177">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="f8ca1-178">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-178">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="f8ca1-179">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValueLiteralPathSet, propertyPSObjectLiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-180">-Name</span><span class="sxs-lookup"><span data-stu-id="f8ca1-180">-Name</span></span>

<span data-ttu-id="f8ca1-181">Hiermee geeft u de naam van de eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-181">Specifies the name of the property.</span></span>

```yaml
Type: System.String
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-182">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f8ca1-182">-PassThru</span></span>

<span data-ttu-id="f8ca1-183">Retourneert een object dat de eigenschap item vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-183">Returns an object that represents the item property.</span></span>
<span data-ttu-id="f8ca1-184">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-184">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-185">-Path</span><span class="sxs-lookup"><span data-stu-id="f8ca1-185">-Path</span></span>

<span data-ttu-id="f8ca1-186">Hiermee geeft u het pad op van de items waarvan de eigenschap moet worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-186">Specifies the path of the items with the property to modify.</span></span>

```yaml
Type: System.String[]
Parameter Sets: propertyValuePathSet, propertyPSObjectPathSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-187">-Type</span><span class="sxs-lookup"><span data-stu-id="f8ca1-187">-Type</span></span>

<span data-ttu-id="f8ca1-188">**Type** is een dynamische para meter die de register provider aan de `Set-ItemProperty` cmdlet toevoegt.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-188">**Type** is a dynamic parameter that the Registry provider adds to the `Set-ItemProperty` cmdlet.</span></span>
<span data-ttu-id="f8ca1-189">Deze para meter werkt alleen in de register stations.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-189">This parameter only works in the registry drives.</span></span>

<span data-ttu-id="f8ca1-190">Hiermee geeft u het type eigenschap op dat met deze cmdlet wordt toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-190">Specifies the type of property that this cmdlet adds.</span></span>
<span data-ttu-id="f8ca1-191">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="f8ca1-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f8ca1-192">**Teken reeks**: Hiermee geeft u een teken reeks met een null-waarde op.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-192">**String**: Specifies a null-terminated string.</span></span> <span data-ttu-id="f8ca1-193">Gelijk aan **REG_SZ**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-193">Equivalent to **REG_SZ**.</span></span>
- <span data-ttu-id="f8ca1-194">**ExpandString**: Hiermee geeft u een teken reeks met een null-waarde eindigen die niet-uitgevouwen verwijzingen bevat naar omgevings variabelen die worden uitgebreid wanneer de waarde wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-194">**ExpandString**: Specifies a null-terminated string that contains unexpanded references to environment variables that are expanded when the value is retrieved.</span></span> <span data-ttu-id="f8ca1-195">Gelijk aan **REG_EXPAND_SZ**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-195">Equivalent to **REG_EXPAND_SZ**.</span></span>
- <span data-ttu-id="f8ca1-196">**Binary**: Hiermee worden binaire gegevens in een wille keurig formulier opgegeven.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-196">**Binary**: Specifies binary data in any form.</span></span> <span data-ttu-id="f8ca1-197">Gelijk aan **REG_BINARY**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-197">Equivalent to **REG_BINARY**.</span></span>
- <span data-ttu-id="f8ca1-198">**DWORD**: Hiermee geeft u een 32-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-198">**DWord**: Specifies a 32-bit binary number.</span></span> <span data-ttu-id="f8ca1-199">Gelijk aan **REG_DWORD**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-199">Equivalent to **REG_DWORD**.</span></span>
- <span data-ttu-id="f8ca1-200">Meerdere **teken reeksen**: Hiermee geeft u een matrix van teken reeksen met een null-waarde die is beëindigd door twee null-tekens.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-200">**MultiString**: Specifies an array of null-terminated strings terminated by two null characters.</span></span>
  <span data-ttu-id="f8ca1-201">Gelijk aan **REG_MULTI_SZ**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-201">Equivalent to **REG_MULTI_SZ**.</span></span>
- <span data-ttu-id="f8ca1-202">**Qword**: Hiermee geeft u een 64-bits binair getal op.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-202">**Qword**: Specifies a 64-bit binary number.</span></span> <span data-ttu-id="f8ca1-203">Gelijk aan **REG_QWORD**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-203">Equivalent to **REG_QWORD**.</span></span>
- <span data-ttu-id="f8ca1-204">**Onbekend**: Hiermee wordt een niet-ondersteund gegevens type van het REGI ster aangegeven, zoals **REG_RESOURCE_LIST**.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-204">**Unknown**: Indicates an unsupported registry data type, such as **REG_RESOURCE_LIST**.</span></span>

```yaml
Type: RegistryValueKind
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-205">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="f8ca1-205">-UseTransaction</span></span>

<span data-ttu-id="f8ca1-206">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-206">Includes the command in the active transaction.</span></span>
<span data-ttu-id="f8ca1-207">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-207">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="f8ca1-208">Zie [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-208">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-209">-Waarde</span><span class="sxs-lookup"><span data-stu-id="f8ca1-209">-Value</span></span>

<span data-ttu-id="f8ca1-210">Hiermee geeft u de waarde van de eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-210">Specifies the value of the property.</span></span>

```yaml
Type: Object
Parameter Sets: propertyValuePathSet, propertyValueLiteralPathSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f8ca1-211">-Confirm</span></span>

<span data-ttu-id="f8ca1-212">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-212">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f8ca1-213">-WhatIf</span></span>

<span data-ttu-id="f8ca1-214">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-214">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f8ca1-215">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-215">The cmdlet is not run.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f8ca1-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f8ca1-216">CommonParameters</span></span>

<span data-ttu-id="f8ca1-217">Deze cmdlet biedt ondersteuning voor de algemene para meters: `-Debug` , `-ErrorAction` , `-ErrorVariable` , `-InformationAction` , `-InformationVariable` , `-OutVariable` , `-OutBuffer` , `-PipelineVariable` , `-Verbose` , `-WarningAction` en `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-217">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="f8ca1-218">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-218">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f8ca1-219">INVOER</span><span class="sxs-lookup"><span data-stu-id="f8ca1-219">INPUTS</span></span>

### <span data-ttu-id="f8ca1-220">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f8ca1-220">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f8ca1-221">U kunt objecten door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-221">You can pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="f8ca1-222">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f8ca1-222">OUTPUTS</span></span>

### <span data-ttu-id="f8ca1-223">Geen, System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f8ca1-223">None, System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f8ca1-224">Met deze cmdlet wordt een **PSCustomObject** -object gegenereerd dat het item vertegenwoordigt dat is gewijzigd en de nieuwe eigenschaps waarde als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-224">This cmdlet generates a **PSCustomObject** object that represents the item that was changed and its new property value, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f8ca1-225">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-225">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f8ca1-226">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f8ca1-226">NOTES</span></span>

<span data-ttu-id="f8ca1-227">`Set-ItemProperty` is ontworpen om te werken met de gegevens die door elke provider worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-227">`Set-ItemProperty` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="f8ca1-228">Als u een lijst wilt weer geven van de providers die beschikbaar zijn in uw sessie, typt u `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="f8ca1-228">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="f8ca1-229">Zie [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f8ca1-229">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="f8ca1-230">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f8ca1-230">RELATED LINKS</span></span>

[<span data-ttu-id="f8ca1-231">Wissen-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-231">Clear-ItemProperty</span></span>](Clear-ItemProperty.md)

[<span data-ttu-id="f8ca1-232">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-232">Copy-ItemProperty</span></span>](Copy-ItemProperty.md)

[<span data-ttu-id="f8ca1-233">Get-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-233">Get-ItemProperty</span></span>](Get-ItemProperty.md)

[<span data-ttu-id="f8ca1-234">Verplaatsen-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-234">Move-ItemProperty</span></span>](Move-ItemProperty.md)

[<span data-ttu-id="f8ca1-235">Nieuw-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-235">New-ItemProperty</span></span>](New-ItemProperty.md)

[<span data-ttu-id="f8ca1-236">Verwijderen-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-236">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="f8ca1-237">Naam wijzigen-item Property</span><span class="sxs-lookup"><span data-stu-id="f8ca1-237">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)
