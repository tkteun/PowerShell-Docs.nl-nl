---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 6b862ad6bada3035551d35d592183db5805b232f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250513"
---
# <span data-ttu-id="54343-103">Get-Acl</span><span class="sxs-lookup"><span data-stu-id="54343-103">Get-Acl</span></span>

## <span data-ttu-id="54343-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="54343-104">SYNOPSIS</span></span>
<span data-ttu-id="54343-105">Hiermee haalt u de security descriptor voor een resource, zoals een bestand of register sleutel.</span><span class="sxs-lookup"><span data-stu-id="54343-105">Gets the security descriptor for a resource, such as a file or registry key.</span></span>

## <span data-ttu-id="54343-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="54343-106">SYNTAX</span></span>

### <span data-ttu-id="54343-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="54343-107">ByPath (Default)</span></span>

```
Get-Acl [[-Path] <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="54343-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="54343-108">ByInputObject</span></span>

```
Get-Acl -InputObject <PSObject> [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

### <span data-ttu-id="54343-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="54343-109">ByLiteralPath</span></span>

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-AllCentralAccessPolicies] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="54343-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="54343-110">DESCRIPTION</span></span>

<span data-ttu-id="54343-111">De `Get-Acl` cmdlet haalt objecten op die de security descriptor van een bestand of resource vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="54343-111">The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="54343-112">De security descriptor bevat de toegangs beheer lijsten (Acl's) van de resource.</span><span class="sxs-lookup"><span data-stu-id="54343-112">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="54343-113">In de ACL worden de machtigingen opgegeven die gebruikers en gebruikers groepen hebben om toegang te krijgen tot de resource.</span><span class="sxs-lookup"><span data-stu-id="54343-113">The ACL specifies the permissions that users and user groups have to access the resource.</span></span>

<span data-ttu-id="54343-114">Vanaf Windows Power Shell 3,0 kunt u de para meter **input object** gebruiken `Get-Acl` om de security descriptor van objecten te verkrijgen die geen pad hebben.</span><span class="sxs-lookup"><span data-stu-id="54343-114">Beginning in Windows PowerShell 3.0, you can use the **InputObject** parameter of `Get-Acl` to get the security descriptor of objects that do not have a path.</span></span>

## <span data-ttu-id="54343-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="54343-115">EXAMPLES</span></span>

### <span data-ttu-id="54343-116">Voor beeld 1: een ACL ophalen voor een map</span><span class="sxs-lookup"><span data-stu-id="54343-116">Example 1- Get an ACL for a folder</span></span>

<span data-ttu-id="54343-117">In dit voor beeld wordt de security descriptor van de `C:\Windows` map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="54343-117">This example gets the security descriptor of the `C:\Windows` directory.</span></span>

```powershell
Get-Acl C:\Windows
```

### <span data-ttu-id="54343-118">Voor beeld 2: een ACL voor een map ophalen met behulp van joker tekens</span><span class="sxs-lookup"><span data-stu-id="54343-118">Example 2 - Get an ACL for a folder using wildcards</span></span>

<span data-ttu-id="54343-119">In dit voor beeld worden het Power shell-pad en de SDDL opgehaald voor alle `.log` bestanden in de `C:\Windows` map waarvan de naam begint met `s` .</span><span class="sxs-lookup"><span data-stu-id="54343-119">This example gets the PowerShell path and SDDL for all of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

<span data-ttu-id="54343-120">De opdracht gebruikt de `Get-Acl` cmdlet om objecten op te halen die de security descriptors van elk logboek bestand vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="54343-120">The command uses the `Get-Acl` cmdlet to get objects representing the security descriptors of each log file.</span></span> <span data-ttu-id="54343-121">Er wordt een pijplijn operator ( `|` ) gebruikt om de resultaten naar de cmdlet te verzenden `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="54343-121">It uses a pipeline operator (`|`) to send the results to the `Format-List` cmdlet.</span></span> <span data-ttu-id="54343-122">De opdracht gebruikt de **eigenschaps** parameter van `Format-List` om alleen de **PsPath** -en **SDDL** -eigenschappen van elk security descriptor-object weer te geven.</span><span class="sxs-lookup"><span data-stu-id="54343-122">The command uses the **Property** parameter of `Format-List` to display only the **PsPath** and **SDDL** properties of each security descriptor object.</span></span>

<span data-ttu-id="54343-123">Lijsten worden vaak gebruikt in Power shell, omdat lange waarden worden afgekapt in tabellen.</span><span class="sxs-lookup"><span data-stu-id="54343-123">Lists are often used in PowerShell, because long values appear truncated in tables.</span></span>

<span data-ttu-id="54343-124">De **SDDL** -waarden zijn waardevol voor systeem beheerders, omdat ze eenvoudige teken reeksen zijn die alle gegevens in de security descriptor bevatten.</span><span class="sxs-lookup"><span data-stu-id="54343-124">The **SDDL** values are valuable to system administrators, because they are simple text strings that contain all of the information in the security descriptor.</span></span> <span data-ttu-id="54343-125">Ze zijn zo eenvoudig te passeren en op te slaan, en ze kunnen worden geparseerd wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="54343-125">As such, they are easy to pass and store, and they can be parsed when needed.</span></span>

### <span data-ttu-id="54343-126">Voor beeld 3: het aantal controle vermeldingen voor een ACL ophalen</span><span class="sxs-lookup"><span data-stu-id="54343-126">Example 3 - Get count of Audit entries for an ACL</span></span>

<span data-ttu-id="54343-127">In dit voor beeld worden de security descriptors opgehaald van de `.log` bestanden in de `C:\Windows` map waarvan de naam begint met `s` .</span><span class="sxs-lookup"><span data-stu-id="54343-127">This example gets the security descriptors of the `.log` files in the `C:\Windows` directory whose names begin with `s`.</span></span>

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

<span data-ttu-id="54343-128">De **controle** parameter wordt gebruikt voor het ophalen van de controle records uit de SACL in het security descriptor.</span><span class="sxs-lookup"><span data-stu-id="54343-128">It uses the **Audit** parameter to get the audit records from the SACL in the security descriptor.</span></span>
<span data-ttu-id="54343-129">Vervolgens wordt de `ForEach-Object` cmdlet gebruikt voor het tellen van het aantal controle records dat aan elk bestand is gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="54343-129">Then it uses the `ForEach-Object` cmdlet to count the number of audit records associated with each file.</span></span> <span data-ttu-id="54343-130">Het resultaat is een lijst met getallen voor het aantal controle records voor elk logboek bestand.</span><span class="sxs-lookup"><span data-stu-id="54343-130">The result is a list of numbers representing the number of audit records for each log file.</span></span>

### <span data-ttu-id="54343-131">Voor beeld 4: een ACL ophalen voor een register sleutel</span><span class="sxs-lookup"><span data-stu-id="54343-131">Example 4 - Get an ACL for a registry key</span></span>

<span data-ttu-id="54343-132">In dit voor beeld wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van de Control-subsleutel ( `HKLM:\SYSTEM\CurrentControlSet\Control` ) van het REGI ster op te halen.</span><span class="sxs-lookup"><span data-stu-id="54343-132">This example uses the `Get-Acl` cmdlet to get the security descriptor of the Control subkey (`HKLM:\SYSTEM\CurrentControlSet\Control`) of the registry.</span></span>

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

<span data-ttu-id="54343-133">De para meter **Path** geeft u de controle-subsleutel.</span><span class="sxs-lookup"><span data-stu-id="54343-133">The **Path** parameter specifies the Control subkey.</span></span> <span data-ttu-id="54343-134">Met de pijplijn operator ( `|` ) wordt de security descriptor door gegeven die `Get-Acl` wordt opgehaald met de `Format-List` opdracht. Hiermee worden de eigenschappen van de security descriptor als een lijst opgemaakt zodat ze gemakkelijk te lezen zijn.</span><span class="sxs-lookup"><span data-stu-id="54343-134">The pipeline operator (`|`) passes the security descriptor that `Get-Acl` gets to the `Format-List` command, which formats the properties of the security descriptor as a list so that they are easy to read.</span></span>

### <span data-ttu-id="54343-135">Voor beeld 5: een ACL ophalen met behulp van **input object**</span><span class="sxs-lookup"><span data-stu-id="54343-135">Example 5 - Get an ACL using **InputObject**</span></span>

<span data-ttu-id="54343-136">In dit voor beeld wordt de para meter **input object** van gebruikt `Get-Acl` om de security descriptor van een object voor een opslag subsysteem op te halen.</span><span class="sxs-lookup"><span data-stu-id="54343-136">This example uses the **InputObject** parameter of `Get-Acl` to get the security descriptor of a storage subsystem object.</span></span>

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## <span data-ttu-id="54343-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="54343-137">PARAMETERS</span></span>

### <span data-ttu-id="54343-138">-Audit</span><span class="sxs-lookup"><span data-stu-id="54343-138">-Audit</span></span>

<span data-ttu-id="54343-139">Hiermee haalt u de controle gegevens voor de security descriptor op uit de SACL (System Access Control List).</span><span class="sxs-lookup"><span data-stu-id="54343-139">Gets the audit data for the security descriptor from the system access control list (SACL).</span></span>

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

### <span data-ttu-id="54343-140">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="54343-140">-Exclude</span></span>

<span data-ttu-id="54343-141">De opgegeven items worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="54343-141">Omits the specified items.</span></span> <span data-ttu-id="54343-142">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="54343-142">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="54343-143">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="54343-143">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="54343-144">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="54343-144">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="54343-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="54343-145">-Filter</span></span>

<span data-ttu-id="54343-146">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="54343-146">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="54343-147">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="54343-147">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="54343-148">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="54343-148">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="54343-149">Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="54343-149">Filters are more efficient than other parameters, because the provider applies them when getting the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="54343-150">-Include</span><span class="sxs-lookup"><span data-stu-id="54343-150">-Include</span></span>

<span data-ttu-id="54343-151">Hiermee worden alleen de opgegeven items opgehaald.</span><span class="sxs-lookup"><span data-stu-id="54343-151">Gets only the specified items.</span></span> <span data-ttu-id="54343-152">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="54343-152">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="54343-153">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="54343-153">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="54343-154">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="54343-154">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="54343-155">-Path</span><span class="sxs-lookup"><span data-stu-id="54343-155">-Path</span></span>

<span data-ttu-id="54343-156">Hiermee geeft u het pad naar een resource.</span><span class="sxs-lookup"><span data-stu-id="54343-156">Specifies the path to a resource.</span></span> <span data-ttu-id="54343-157">`Get-Acl` Hiermee wordt de security descriptor opgehaald van de resource die wordt aangegeven door het pad.</span><span class="sxs-lookup"><span data-stu-id="54343-157">`Get-Acl` gets the security descriptor of the resource indicated by the path.</span></span> <span data-ttu-id="54343-158">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="54343-158">Wildcards are permitted.</span></span> <span data-ttu-id="54343-159">Als u de para meter **Path** weglaat, `Get-Acl` wordt de security descriptor van de huidige map opgehaald.</span><span class="sxs-lookup"><span data-stu-id="54343-159">If you omit the **Path** parameter, `Get-Acl` gets the security descriptor of the current directory.</span></span>

<span data-ttu-id="54343-160">De parameter naam ("pad") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="54343-160">The parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="54343-161">-AllCentralAccessPolicies</span><span class="sxs-lookup"><span data-stu-id="54343-161">-AllCentralAccessPolicies</span></span>

<span data-ttu-id="54343-162">Haalt informatie op over alle centrale toegangs beleidsregels die zijn ingeschakeld op de computer.</span><span class="sxs-lookup"><span data-stu-id="54343-162">Gets information about all central access policies that are enabled on the computer.</span></span>

<span data-ttu-id="54343-163">Vanaf Windows Server 2012 kunnen beheerders Active Directory en groepsbeleid gebruiken om centraal toegangs beleid in te stellen voor gebruikers en groepen.</span><span class="sxs-lookup"><span data-stu-id="54343-163">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="54343-164">Zie [Dynamic Access Control: scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="54343-164">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="54343-165">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="54343-165">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="54343-166">-Input object</span><span class="sxs-lookup"><span data-stu-id="54343-166">-InputObject</span></span>

<span data-ttu-id="54343-167">Hiermee wordt de security descriptor voor het opgegeven object opgehaald.</span><span class="sxs-lookup"><span data-stu-id="54343-167">Gets the security descriptor for the specified object.</span></span> <span data-ttu-id="54343-168">Voer een variabele in die het object of een opdracht bevat die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="54343-168">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="54343-169">U kunt een object, met uitzonde ring van een pad, niet door sluizen naar `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="54343-169">You cannot pipe an object, other than a path, to `Get-Acl`.</span></span> <span data-ttu-id="54343-170">Gebruik in plaats daarvan de para meter **input object** expliciet in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="54343-170">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="54343-171">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="54343-171">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="54343-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="54343-172">-LiteralPath</span></span>

<span data-ttu-id="54343-173">Hiermee geeft u het pad naar een resource.</span><span class="sxs-lookup"><span data-stu-id="54343-173">Specifies the path to a resource.</span></span> <span data-ttu-id="54343-174">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="54343-174">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="54343-175">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="54343-175">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="54343-176">Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="54343-176">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="54343-177">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="54343-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="54343-178">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="54343-178">This parameter is introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="54343-179">-UseTransaction</span><span class="sxs-lookup"><span data-stu-id="54343-179">-UseTransaction</span></span>

<span data-ttu-id="54343-180">Hiermee wordt de opdracht opgenomen in de actieve transactie.</span><span class="sxs-lookup"><span data-stu-id="54343-180">Includes the command in the active transaction.</span></span>
<span data-ttu-id="54343-181">Deze parameter is alleen geldig wanneer een transactie wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="54343-181">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="54343-182">Zie about_Transactions voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="54343-182">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="54343-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54343-183">CommonParameters</span></span>

<span data-ttu-id="54343-184">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54343-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54343-185">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="54343-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="54343-186">INVOER</span><span class="sxs-lookup"><span data-stu-id="54343-186">INPUTS</span></span>

### <span data-ttu-id="54343-187">System. String</span><span class="sxs-lookup"><span data-stu-id="54343-187">System.String</span></span>

<span data-ttu-id="54343-188">U kunt een teken reeks met een pad naar door sluizen `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="54343-188">You can pipe a string that contains a path to `Get-Acl`.</span></span>

## <span data-ttu-id="54343-189">UITVOER</span><span class="sxs-lookup"><span data-stu-id="54343-189">OUTPUTS</span></span>

### <span data-ttu-id="54343-190">System. Security. AccessControl. FileSecurity, System. Security. AccessControl. DirectorySecurity, System. Security. AccessControl. RegistrySecurity</span><span class="sxs-lookup"><span data-stu-id="54343-190">System.Security.AccessControl.FileSecurity, System.Security.AccessControl.DirectorySecurity, System.Security.AccessControl.RegistrySecurity</span></span>

<span data-ttu-id="54343-191">`Get-Acl` retourneert een-object dat de door u opgehaalde Acl's vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="54343-191">`Get-Acl` returns an object that represents the ACLs that it gets.</span></span> <span data-ttu-id="54343-192">Het object type is afhankelijk van het type toegangs beheer lijst.</span><span class="sxs-lookup"><span data-stu-id="54343-192">The object type depends upon the ACL type.</span></span>

## <span data-ttu-id="54343-193">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="54343-193">NOTES</span></span>

<span data-ttu-id="54343-194">`Get-Acl`Geeft standaard het Power shell-pad naar de resource ( `<provider>::<resource-path>` ), de eigenaar van de resource en ' toegang ', een lijst (matrix) van de vermeldingen voor toegangs beheer in de discretionaire toegangs beheer lijst (DACL) voor de bron.</span><span class="sxs-lookup"><span data-stu-id="54343-194">By default, `Get-Acl` displays the PowerShell path to the resource (`<provider>::<resource-path>`), the owner of the resource, and "Access", a list (array) of the access control entries in the discretionary access control list (DACL) for the resource.</span></span> <span data-ttu-id="54343-195">De lijst met DACL'S wordt beheerd door de resource-eigenaar.</span><span class="sxs-lookup"><span data-stu-id="54343-195">The DACL list is controlled by the resource owner.</span></span>

<span data-ttu-id="54343-196">Wanneer u het resultaat opmaakt als een lijst, ( `Get-Acl | Format-List` ) naast het pad, de eigenaar en de toegangs lijst, worden in Power shell de volgende eigenschappen en eigenschaps waarden weer gegeven:</span><span class="sxs-lookup"><span data-stu-id="54343-196">When you format the result as a list, (`Get-Acl | Format-List`), in addition to the path, owner, and access list, PowerShell displays the following properties and property values:</span></span>

- <span data-ttu-id="54343-197">**Groep** : de beveiligings groep van de eigenaar.</span><span class="sxs-lookup"><span data-stu-id="54343-197">**Group** : The security group of the owner.</span></span>
- <span data-ttu-id="54343-198">**Controle** : een lijst (matrix) van vermeldingen in de System Access Control List (SACL).</span><span class="sxs-lookup"><span data-stu-id="54343-198">**Audit** :  A list (array) of entries in the system access control list (SACL).</span></span> <span data-ttu-id="54343-199">De SACL specificeert de typen toegangs pogingen waarvoor Windows controle records genereert.</span><span class="sxs-lookup"><span data-stu-id="54343-199">The SACL specifies the types of access attempts for which Windows generates audit records.</span></span>
- <span data-ttu-id="54343-200">**SDDL** : de security descriptor van de resource die wordt weer gegeven in een enkele teken reeks in de Security Descriptor Definition Language-indeling.</span><span class="sxs-lookup"><span data-stu-id="54343-200">**Sddl** : The security descriptor of the resource displayed in a single text string in Security Descriptor Definition Language format.</span></span> <span data-ttu-id="54343-201">Power Shell maakt gebruik van de **GetSddlForm** -methode van security descriptors om deze gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="54343-201">PowerShell uses the **GetSddlForm** method of security descriptors to get this data.</span></span>

<span data-ttu-id="54343-202">Omdat `Get-Acl` het bestands systeem en register providers worden ondersteund, kunt u gebruiken `Get-Acl` om de ACL van bestandssysteem objecten, zoals bestanden en mappen, en register objecten, zoals register sleutels en vermeldingen, weer te geven.</span><span class="sxs-lookup"><span data-stu-id="54343-202">Because `Get-Acl` is supported by the file system and registry providers, you can use `Get-Acl` to view the ACL of file system objects, such as files and directories, and registry objects, such as registry keys and entries.</span></span>

## <span data-ttu-id="54343-203">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="54343-203">RELATED LINKS</span></span>

[<span data-ttu-id="54343-204">Set-ACL</span><span class="sxs-lookup"><span data-stu-id="54343-204">Set-Acl</span></span>](Set-Acl.md)
