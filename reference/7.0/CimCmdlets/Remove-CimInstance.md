---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: 9c81affc709ed6fd2fc18b7252215909cb49613a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251564"
---
# <span data-ttu-id="f0b59-103">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f0b59-103">Remove-CimInstance</span></span>

## <span data-ttu-id="f0b59-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f0b59-104">SYNOPSIS</span></span>
<span data-ttu-id="f0b59-105">Hiermee verwijdert u een CIM-exemplaar van een computer.</span><span class="sxs-lookup"><span data-stu-id="f0b59-105">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="f0b59-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f0b59-106">SYNTAX</span></span>

### <span data-ttu-id="f0b59-107">CimInstanceComputerSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="f0b59-107">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0b59-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="f0b59-108">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0b59-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="f0b59-109">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f0b59-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="f0b59-110">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f0b59-111">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f0b59-111">DESCRIPTION</span></span>

<span data-ttu-id="f0b59-112">Met deze cmdlet wordt een CIM-exemplaar van een CIM-server verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-112">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="f0b59-113">U kunt opgeven dat het CIM-exemplaar moet worden verwijderd met behulp van een CIM-instantie object dat wordt opgehaald door de `Get-CimInstance` cmdlet of door een query op te geven.</span><span class="sxs-lookup"><span data-stu-id="f0b59-113">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="f0b59-114">Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="f0b59-114">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f0b59-115">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="f0b59-115">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="f0b59-116">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="f0b59-116">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="f0b59-117">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f0b59-117">EXAMPLES</span></span>

### <span data-ttu-id="f0b59-118">Voor beeld 1: het CIM-exemplaar verwijderen</span><span class="sxs-lookup"><span data-stu-id="f0b59-118">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="f0b59-119">In dit voor beeld gebruikt u de **query** parameter om CIM-instanties te verwijderen uit de klasse met de naam **Win32_Environment** die beginnen met de teken reeks **TestVar** .</span><span class="sxs-lookup"><span data-stu-id="f0b59-119">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="f0b59-120">Voor beeld 2: het CIM-exemplaar verwijderen met een CIM instance-object</span><span class="sxs-lookup"><span data-stu-id="f0b59-120">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="f0b59-121">In dit voor beeld worden de CIM-exemplaar objecten die worden gefilterd door de **query** parameter opgehaald en opgeslagen in een variabele `$var` met de `Get-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0b59-121">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="f0b59-122">De inhoud van de variabele wordt vervolgens door gegeven aan de `Remove-CimInstance` cmdlet, waardoor de CIM-instanties worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-122">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="f0b59-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0b59-123">PARAMETERS</span></span>

### <span data-ttu-id="f0b59-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="f0b59-124">-CimSession</span></span>

<span data-ttu-id="f0b59-125">De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="f0b59-125">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="f0b59-126">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de `New-CimSession` of cmdlets, maakt of ontvangt `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="f0b59-126">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="f0b59-127">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0b59-127">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f0b59-128">-ComputerName</span></span>

<span data-ttu-id="f0b59-129">Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f0b59-129">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="f0b59-130">U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="f0b59-130">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="f0b59-131">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="f0b59-131">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="f0b59-132">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="f0b59-132">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="f0b59-133">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="f0b59-133">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-134">-Input object</span><span class="sxs-lookup"><span data-stu-id="f0b59-134">-InputObject</span></span>

<span data-ttu-id="f0b59-135">Hiermee geeft u een CIM-exemplaar object op dat van de CIM-server moet worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-135">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="f0b59-136">Het object dat aan de cmdlet is door gegeven, is niet gewijzigd, alleen het exemplaar in de CIM-server wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-136">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-137">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="f0b59-137">-Namespace</span></span>

<span data-ttu-id="f0b59-138">Hiermee geeft u de naam ruimte voor de CIM-bewerking op.</span><span class="sxs-lookup"><span data-stu-id="f0b59-138">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="f0b59-139">De standaard naam ruimte is **root-cimv2**.</span><span class="sxs-lookup"><span data-stu-id="f0b59-139">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="f0b59-140">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="f0b59-140">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-141">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f0b59-141">-OperationTimeoutSec</span></span>

<span data-ttu-id="f0b59-142">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="f0b59-142">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="f0b59-143">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f0b59-143">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="f0b59-144">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="f0b59-144">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-145">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="f0b59-145">-Query</span></span>

<span data-ttu-id="f0b59-146">Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="f0b59-146">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="f0b59-147">U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="f0b59-147">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="f0b59-148">Als de opgegeven waarde dubbele aanhalings tekens ( `"` ), enkele aanhalings tekens ( `'` ) of een back slash ( `\` ) bevat, moet u deze tekens weglaten door ze te voorzien van een back slash ( `\` )-teken.</span><span class="sxs-lookup"><span data-stu-id="f0b59-148">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="f0b59-149">Als de opgegeven waarde gebruikmaakt van de WQL LIKE-operator, moet u de volgende tekens door geven tussen vier Kante haken ( `[]` ): procent ( `%` ), onderstrepings teken () `_` of vier Kante haak openen ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="f0b59-149">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-150">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="f0b59-150">-QueryDialect</span></span>

<span data-ttu-id="f0b59-151">Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter.</span><span class="sxs-lookup"><span data-stu-id="f0b59-151">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="f0b59-152">De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**.</span><span class="sxs-lookup"><span data-stu-id="f0b59-152">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="f0b59-153">De standaard waarde is **WQL**.</span><span class="sxs-lookup"><span data-stu-id="f0b59-153">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="f0b59-154">-ResourceUri</span></span>

<span data-ttu-id="f0b59-155">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="f0b59-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="f0b59-156">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f0b59-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f0b59-157">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="f0b59-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="f0b59-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f0b59-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="f0b59-159">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="f0b59-160">ResourceURI kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter ComputerName, waarmee een CIM-sessie wordt gemaakt met behulp van WSMan.</span><span class="sxs-lookup"><span data-stu-id="f0b59-160">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="f0b59-161">Als u deze para meter opgeeft zonder de para meter ComputerName op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, treedt er een fout op omdat het DCOM-protocol de para meter ResourceURI niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="f0b59-161">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="f0b59-162">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0b59-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f0b59-163">-Confirm</span></span>

<span data-ttu-id="f0b59-164">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f0b59-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f0b59-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f0b59-165">-WhatIf</span></span>

<span data-ttu-id="f0b59-166">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f0b59-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f0b59-167">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f0b59-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f0b59-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0b59-168">CommonParameters</span></span>

<span data-ttu-id="f0b59-169">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0b59-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0b59-170">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f0b59-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0b59-171">INVOER</span><span class="sxs-lookup"><span data-stu-id="f0b59-171">INPUTS</span></span>

### <span data-ttu-id="f0b59-172">Geen</span><span class="sxs-lookup"><span data-stu-id="f0b59-172">None</span></span>

<span data-ttu-id="f0b59-173">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="f0b59-173">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="f0b59-174">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f0b59-174">OUTPUTS</span></span>

### <span data-ttu-id="f0b59-175">Geen</span><span class="sxs-lookup"><span data-stu-id="f0b59-175">None</span></span>

<span data-ttu-id="f0b59-176">Deze cmdlet produceert geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="f0b59-176">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="f0b59-177">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f0b59-177">NOTES</span></span>

## <span data-ttu-id="f0b59-178">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f0b59-178">RELATED LINKS</span></span>

[<span data-ttu-id="f0b59-179">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f0b59-179">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="f0b59-180">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f0b59-180">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="f0b59-181">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f0b59-181">Set-CimInstance</span></span>](Set-CimInstance.md)
