---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: ed458e7f58ebb61611e2fd9e60430a7330087e8a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705859"
---
# <span data-ttu-id="f2bde-102">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="f2bde-102">Get-Acl</span></span>

## <span data-ttu-id="f2bde-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f2bde-103">SYNOPSIS</span></span>
<span data-ttu-id="f2bde-104">Hiermee haalt u de security descriptor voor een resource, zoals een bestand of register sleutel.</span><span class="sxs-lookup"><span data-stu-id="f2bde-104">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="f2bde-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f2bde-105">SYNTAX</span></span>

### <span data-ttu-id="f2bde-106">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="f2bde-106">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="f2bde-107">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="f2bde-107">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f2bde-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="f2bde-108">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="f2bde-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f2bde-109">DESCRIPTION</span></span>

<span data-ttu-id="f2bde-110">De `Get-Acl` cmdlet haalt objecten op die de security descriptor van een bestand of resource vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-110">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="f2bde-111">De security descriptor bevat de toegangs beheer lijsten (Acl's) van de resource.</span><span class="sxs-lookup"><span data-stu-id="f2bde-111">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="f2bde-112">In de ACL worden de machtigingen opgegeven die gebruikers en gebruikers groepen hebben om toegang te krijgen tot de resource.</span><span class="sxs-lookup"><span data-stu-id="f2bde-112">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="f2bde-113">Vanaf Windows Power Shell 3,0 kunt u de para meter **input object** gebruiken `Get-Acl` om de security descriptor van objecten te verkrijgen die geen pad hebben.</span><span class="sxs-lookup"><span data-stu-id="f2bde-113">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="f2bde-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f2bde-114">EXAMPLES</span></span>

### <span data-ttu-id="f2bde-115">Voor beeld 1: een ACL ophalen voor een map</span><span class="sxs-lookup"><span data-stu-id="f2bde-115">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="f2bde-116">In dit voor beeld wordt de security descriptor van de `C:\Windows` map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2bde-116">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="f2bde-117">Voor beeld 2: een ACL voor een map ophalen met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="f2bde-117">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="f2bde-118">In dit voor beeld worden het Power shell-pad en de SDDL opgehaald voor alle `.log` bestanden in de `C:\Windows` map waarvan de naam begint met `s` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-118">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="f2bde-119">De opdracht gebruikt de `Get-Acl` cmdlet om objecten op te halen die de security descriptors van elk logboek bestand vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-119">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="f2bde-120">Er wordt een pijplijn operator ( `|` ) gebruikt om de resultaten naar de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-120">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="f2bde-121">De opdracht gebruikt de **eigenschaps** parameter van `Format-List` om alleen de **PsPath** -en **SDDL** -eigenschappen van elk security descriptor-object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f2bde-121">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="f2bde-122">Lijsten worden vaak gebruikt in Power shell, omdat lange waarden worden afgekapt in tabellen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-122">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="f2bde-123">De **SDDL** -waarden zijn waardevol voor systeem beheerders, omdat ze eenvoudige teken reeksen zijn die alle gegevens in de security descriptor bevatten.</span><span class="sxs-lookup"><span data-stu-id="f2bde-123">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="f2bde-124">Ze zijn zo eenvoudig te passeren en op te slaan, en ze kunnen worden geparseerd wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="f2bde-124">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="f2bde-125">Voor beeld 3: het aantal controle vermeldingen voor een ACL ophalen</span><span class="sxs-lookup"><span data-stu-id="f2bde-125">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="f2bde-126">In dit voor beeld worden de security descriptors opgehaald van de `.log` bestanden in de `C:\Windows` map waarvan de naam begint met `s` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-126">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="f2bde-127">De **controle** parameter wordt gebruikt voor het ophalen van de controle records uit de SACL in het security descriptor.</span><span class="sxs-lookup"><span data-stu-id="f2bde-127">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="f2bde-128">Vervolgens wordt de `ForEach-Object` cmdlet gebruikt voor het tellen van het aantal controle records dat aan elk bestand is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="f2bde-128">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="f2bde-129">Het resultaat is een lijst met getallen voor het aantal controle records voor elk logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="f2bde-129">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="f2bde-130">Voor beeld 4: een ACL ophalen voor een register sleutel</span><span class="sxs-lookup"><span data-stu-id="f2bde-130">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="f2bde-131">In dit voor beeld wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van de Control-subsleutel ( `HKLM:\SYSTEM\CurrentControlSet\Control` ) van het REGI ster op te halen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-131">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="f2bde-132">De para meter **Path** geeft u de controle-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="f2bde-132">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="f2bde-133">Met de pijplijn operator ( `|` ) wordt de security descriptor door gegeven die `Get-Acl` wordt opgehaald met de `Format-List` opdracht. Hiermee worden de eigenschappen van de security descriptor als een lijst opgemaakt zodat ze gemakkelijk te lezen zijn.</span><span class="sxs-lookup"><span data-stu-id="f2bde-133">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="f2bde-134">Voor beeld 5: een ACL ophalen met behulp van **input object**</span><span class="sxs-lookup"><span data-stu-id="f2bde-134">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="f2bde-135">In dit voor beeld wordt de para meter **input object** van gebruikt `Get-Acl` om de security descriptor van een object voor een opslag subsysteem op te halen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-135">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="f2bde-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f2bde-136">PARAMETERS</span></span>

### <span data-ttu-id="f2bde-137">-Audit</span><span class="sxs-lookup"><span data-stu-id="f2bde-137">-Audit</span></span>

<span data-ttu-id="f2bde-138">Hiermee haalt u de controle gegevens voor de security descriptor op uit de SACL (System Access Control List).</span><span class="sxs-lookup"><span data-stu-id="f2bde-138">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="f2bde-139">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="f2bde-139">-Exclude</span></span>

<span data-ttu-id="f2bde-140">De opgegeven items worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="f2bde-140">Omits the specified items.</span></span> <span data-ttu-id="f2bde-141">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f2bde-141">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f2bde-142">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-142">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f2bde-143">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f2bde-143">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f2bde-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="f2bde-144">-Filter</span></span>

<span data-ttu-id="f2bde-145">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="f2bde-145">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="f2bde-146">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f2bde-146">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f2bde-147">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="f2bde-147">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="f2bde-148">Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2bde-148">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="f2bde-149">-Include</span><span class="sxs-lookup"><span data-stu-id="f2bde-149">-Include</span></span>

<span data-ttu-id="f2bde-150">Hiermee worden alleen de opgegeven items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2bde-150">Gets only the specified items.</span></span> <span data-ttu-id="f2bde-151">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="f2bde-151">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="f2bde-152">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-152">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="f2bde-153">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f2bde-153">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="f2bde-154">-Path</span><span class="sxs-lookup"><span data-stu-id="f2bde-154">-Path</span></span>

<span data-ttu-id="f2bde-155">Hiermee geeft u het pad naar een resource.</span><span class="sxs-lookup"><span data-stu-id="f2bde-155">Specifies the path to a resource.</span></span> <span data-ttu-id="f2bde-156">`Get-Acl` Hiermee wordt de security descriptor opgehaald van de resource die wordt aangegeven door het pad.</span><span class="sxs-lookup"><span data-stu-id="f2bde-156">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="f2bde-157">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="f2bde-157">Wildcards are permitted.</span></span> <span data-ttu-id="f2bde-158">Als u de para meter **Path** weglaat, `Get-Acl` wordt de security descriptor van de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2bde-158">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="f2bde-159">De parameter naam ("pad") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="f2bde-159">The parameter name ("Path") is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f2bde-160">-Input object</span><span class="sxs-lookup"><span data-stu-id="f2bde-160">-InputObject</span></span>

<span data-ttu-id="f2bde-161">Hiermee wordt de security descriptor voor het opgegeven object opgehaald.</span><span class="sxs-lookup"><span data-stu-id="f2bde-161">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="f2bde-162">Voer een variabele in die het object of een opdracht bevat die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="f2bde-162">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="f2bde-163">U kunt een object, met uitzonde ring van een pad, niet door sluizen naar `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-163">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="f2bde-164">Gebruik in plaats daarvan de para meter **input object** expliciet in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="f2bde-164">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="f2bde-165">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2bde-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f2bde-166">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f2bde-166">-LiteralPath</span></span>

<span data-ttu-id="f2bde-167">Hiermee geeft u het pad naar een resource.</span><span class="sxs-lookup"><span data-stu-id="f2bde-167">Specifies the path to a resource.</span></span> <span data-ttu-id="f2bde-168">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="f2bde-168">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f2bde-169">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="f2bde-169">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f2bde-170">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="f2bde-170">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f2bde-171">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-171">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="f2bde-172">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f2bde-172">This parameter is introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2bde-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2bde-173">CommonParameters</span></span>

<span data-ttu-id="f2bde-174">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2bde-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2bde-175">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f2bde-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2bde-176">INVOER</span><span class="sxs-lookup"><span data-stu-id="f2bde-176">INPUTS</span></span>

### <span data-ttu-id="f2bde-177">System. String</span><span class="sxs-lookup"><span data-stu-id="f2bde-177">System.String</span></span>

<span data-ttu-id="f2bde-178">U kunt een teken reeks met een pad naar door sluizen `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="f2bde-178">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="f2bde-179">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f2bde-179">OUTPUTS</span></span>

### <span data-ttu-id="f2bde-180">System. Security. AccessControl. FileSecurity, System. Security. AccessControl. DirectorySecurity, System. Security. AccessControl. RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="f2bde-180">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="f2bde-181">`Get-Acl` retourneert een-object dat de door u opgehaalde Acl's vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f2bde-181">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="f2bde-182">Het object type is afhankelijk van het type toegangs beheer lijst.</span><span class="sxs-lookup"><span data-stu-id="f2bde-182">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="f2bde-183">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f2bde-183">NOTES</span></span>

<span data-ttu-id="f2bde-184">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="f2bde-184">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="f2bde-185">`Get-Acl`Geeft standaard het Power shell-pad naar de resource ( `<provider>::<resource-path>` ), de eigenaar van de resource en ' toegang ', een lijst (matrix) van de vermeldingen voor toegangs beheer in de discretionaire toegangs beheer lijst (DACL) voor de bron.</span><span class="sxs-lookup"><span data-stu-id="f2bde-185">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="f2bde-186">De lijst met DACL'S wordt beheerd door de resource-eigenaar.</span><span class="sxs-lookup"><span data-stu-id="f2bde-186">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="f2bde-187">Wanneer u het resultaat opmaakt als een lijst, ( `Get-Acl | Format-List` ) naast het pad, de eigenaar en de toegangs lijst, worden in Power shell de volgende eigenschappen en eigenschaps waarden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="f2bde-187">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="f2bde-188">**Groep**: de beveiligings groep van de eigenaar.</span><span class="sxs-lookup"><span data-stu-id="f2bde-188">**Group**: The security group of the owner.</span></span>
- <span data-ttu-id="f2bde-189">**Controle**: een lijst (matrix) van vermeldingen in de System Access Control List (SACL).</span><span class="sxs-lookup"><span data-stu-id="f2bde-189">**Audit**:  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="f2bde-190">De SACL specificeert de typen toegangs pogingen waarvoor Windows controle records genereert.</span><span class="sxs-lookup"><span data-stu-id="f2bde-190">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="f2bde-191">**SDDL**: de security descriptor van de resource die wordt weer gegeven in een enkele teken reeks in de Security Descriptor Definition Language-indeling.</span><span class="sxs-lookup"><span data-stu-id="f2bde-191">**Sddl**: The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="f2bde-192">Power Shell maakt gebruik van de **GetSddlForm** -methode van security descriptors om deze gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="f2bde-192">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="f2bde-193">Omdat `Get-Acl` het bestands systeem en register providers worden ondersteund, kunt u gebruiken `Get-Acl` om de ACL van bestandssysteem objecten, zoals bestanden en mappen, en register objecten, zoals register sleutels en vermeldingen, weer te geven.</span><span class="sxs-lookup"><span data-stu-id="f2bde-193">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="f2bde-194">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f2bde-194">RELATED LINKS</span></span>

[<span data-ttu-id="f2bde-195">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="f2bde-195">Set-Acl</span></span>](Set-Acl.md)
