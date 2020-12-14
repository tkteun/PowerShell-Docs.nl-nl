---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 041ef2d5b5541c250b98003099fe58018df155c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705390"
---
# <span data-ttu-id="bd30a-102">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bd30a-102">Set-CimInstance</span></span>

## <span data-ttu-id="bd30a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="bd30a-103">SYNOPSIS</span></span>
<span data-ttu-id="bd30a-104">Wijzigt een CIM-exemplaar op een CIM-server door het aanroepen van de methode ModifyInstance van de CIM-klasse.</span><span class="sxs-lookup"><span data-stu-id="bd30a-104">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="bd30a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="bd30a-105">SYNTAX</span></span>

### <span data-ttu-id="bd30a-106">CimInstanceComputerSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="bd30a-106">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bd30a-107">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="bd30a-107">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bd30a-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="bd30a-108">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="bd30a-109">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="bd30a-109">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="bd30a-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="bd30a-110">DESCRIPTION</span></span>

<span data-ttu-id="bd30a-111">Met deze cmdlet wordt een CIM-exemplaar op een CIM-server gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-111">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="bd30a-112">Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="bd30a-112">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="bd30a-113">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="bd30a-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="bd30a-114">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="bd30a-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="bd30a-115">Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="bd30a-115">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="bd30a-116">Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="bd30a-116">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="bd30a-117">Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter **CimSession** of **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="bd30a-117">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="bd30a-118">Dit is niet zeer gebruikelijk.</span><span class="sxs-lookup"><span data-stu-id="bd30a-118">This is not very common.</span></span>

## <span data-ttu-id="bd30a-119">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="bd30a-119">EXAMPLES</span></span>

### <span data-ttu-id="bd30a-120">Voor beeld 1: het CIM-exemplaar instellen</span><span class="sxs-lookup"><span data-stu-id="bd30a-120">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="bd30a-121">In dit voor beeld wordt de waarde van de eigenschap **VariableValue** ingesteld op **ABCD** met behulp van de **query** parameter.</span><span class="sxs-lookup"><span data-stu-id="bd30a-121">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="bd30a-122">U kunt exemplaren die overeenkomen met een WQL-query (Windows Management Instrumentation Query Language) wijzigen.</span><span class="sxs-lookup"><span data-stu-id="bd30a-122">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="bd30a-123">Voor beeld 2: de CIM-instantie-eigenschap instellen met behulp van de pijp lijn</span><span class="sxs-lookup"><span data-stu-id="bd30a-123">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="bd30a-124">In dit voor beeld wordt het CIM-exemplaar object opgehaald dat is gefilterd door de **query** parameter met behulp van de `Get-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd30a-124">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="bd30a-125">`Set-CimInstance`Met de cmdlet wordt de waarde van de eigenschap **VariableValue** gewijzigd in **ABCD**.</span><span class="sxs-lookup"><span data-stu-id="bd30a-125">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd**.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="bd30a-126">Voor beeld 3: de eigenschap CIM-exemplaar instellen met behulp van een invoer object</span><span class="sxs-lookup"><span data-stu-id="bd30a-126">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="bd30a-127">In dit voor beeld worden de CIM-exemplaar objecten die worden gefilterd door de query parameter in naar een variabele `$x` die `Get-CimInstance` wordt gebruikt, opgehaald en wordt de inhoud van de variabele door gegeven aan de `Set-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd30a-127">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="bd30a-128">`Set-CimInstance` wijzigt vervolgens de eigenschap **VariableValue** in **eenwaarde**.</span><span class="sxs-lookup"><span data-stu-id="bd30a-128">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue**.</span></span> <span data-ttu-id="bd30a-129">Omdat de para meter **PassThru** wordt gebruikt, wordt in dit voor beeld een gewijzigd CIM-exemplaar object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-129">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="bd30a-130">Voor beeld 4: de eigenschap CIM-exemplaar instellen</span><span class="sxs-lookup"><span data-stu-id="bd30a-130">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="bd30a-131">In dit voor beeld wordt het CIM-exemplaar object dat in de **query** parameter is opgegeven, opgehaald in een variabele `$x` met de `Get-CimInstance` cmdlet en wordt de waarde van de eigenschap **VariableValue** van het object gewijzigd in gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-131">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="bd30a-132">Het object CIM-exemplaar wordt vervolgens opgeslagen met de `Set-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd30a-132">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="bd30a-133">Omdat de para meter **PassThru** wordt gebruikt, wordt in dit voor beeld een gewijzigd CIM-exemplaar object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-133">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="bd30a-134">Voor beeld 5: de lijst met CIM-instanties weer geven die u kunt wijzigen met behulp van WhatIf</span><span class="sxs-lookup"><span data-stu-id="bd30a-134">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="bd30a-135">In dit voor beeld wordt gebruikgemaakt van de algemene para meter **WhatIf** om op te geven dat de wijziging niet moet worden uitgevoerd, maar alleen output wat er zou gebeuren als deze is uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-135">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="bd30a-136">Voor beeld 6: het CIM-exemplaar instellen na bevestiging van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="bd30a-136">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="bd30a-137">In dit voor beeld wordt de gemeen schappelijke **para meter** gebruikt om op te geven dat de wijziging alleen moet worden uitgevoerd na de bevestiging van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="bd30a-137">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="bd30a-138">Voor beeld 7: het gemaakte CIM-exemplaar instellen</span><span class="sxs-lookup"><span data-stu-id="bd30a-138">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="bd30a-139">In dit voor beeld wordt een CIM-exemplaar met de opgegeven eigenschappen gemaakt met de `New-CimInstance` cmdlet en wordt de inhoud ervan opgehaald in een variabele `$x` .</span><span class="sxs-lookup"><span data-stu-id="bd30a-139">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="bd30a-140">De variabele wordt vervolgens door gegeven aan de `Set-CimInstance` cmdlet, waarmee de waarde van de eigenschap **VariableValue** wordt gewijzigd in **eenwaarde**.</span><span class="sxs-lookup"><span data-stu-id="bd30a-140">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue**.</span></span>
<span data-ttu-id="bd30a-141">Omdat de para meter **PassThru** wordt gebruikt, wordt in dit voor beeld een gewijzigd CIM-exemplaar object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-141">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="bd30a-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd30a-142">PARAMETERS</span></span>

### <span data-ttu-id="bd30a-143">-CimSession</span><span class="sxs-lookup"><span data-stu-id="bd30a-143">-CimSession</span></span>

<span data-ttu-id="bd30a-144">De cmdlets worden uitgevoerd op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="bd30a-144">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="bd30a-145">Voer een computer naam of een sessie object in, zoals de uitvoer van een- `New-CimSession` of- `Get-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bd30a-145">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

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

### <span data-ttu-id="bd30a-146">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bd30a-146">-ComputerName</span></span>

<span data-ttu-id="bd30a-147">Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="bd30a-147">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="bd30a-148">U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="bd30a-148">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="bd30a-149">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="bd30a-149">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="bd30a-150">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="bd30a-150">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="bd30a-151">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="bd30a-151">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="bd30a-152">-Input object</span><span class="sxs-lookup"><span data-stu-id="bd30a-152">-InputObject</span></span>

<span data-ttu-id="bd30a-153">Hiermee geeft u een CIM-exemplaar object op dat moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="bd30a-153">Specifies a CIM instance object to use as input.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bd30a-154">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="bd30a-154">-Namespace</span></span>

<span data-ttu-id="bd30a-155">Hiermee geeft u de naam ruimte voor de CIM-bewerking op.</span><span class="sxs-lookup"><span data-stu-id="bd30a-155">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="bd30a-156">De standaard naam ruimte is root-cimv2.</span><span class="sxs-lookup"><span data-stu-id="bd30a-156">The default namespace is root/cimv2.</span></span> <span data-ttu-id="bd30a-157">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="bd30a-157">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd30a-158">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="bd30a-158">-OperationTimeoutSec</span></span>

<span data-ttu-id="bd30a-159">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="bd30a-159">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="bd30a-160">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="bd30a-160">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="bd30a-161">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="bd30a-161">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="bd30a-162">-PassThru</span><span class="sxs-lookup"><span data-stu-id="bd30a-162">-PassThru</span></span>

<span data-ttu-id="bd30a-163">Retourneert een object dat het item vertegenwoordigt waarmee u werkt.</span><span class="sxs-lookup"><span data-stu-id="bd30a-163">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="bd30a-164">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="bd30a-164">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="bd30a-165">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bd30a-165">-Property</span></span>

<span data-ttu-id="bd30a-166">Hiermee geeft u de eigenschappen van het CIM-exemplaar op als een hash-tabel (met behulp van naam/waarde-paren).</span><span class="sxs-lookup"><span data-stu-id="bd30a-166">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="bd30a-167">Alleen de eigenschappen die zijn opgegeven met deze para meter, worden gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-167">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="bd30a-168">Andere eigenschappen van het CIM-exemplaar worden niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-168">Other properties of the CIM instance are not changed.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd30a-169">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="bd30a-169">-Query</span></span>

<span data-ttu-id="bd30a-170">Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server om CIM-instanties op te halen waarop de cmdlet moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-170">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="bd30a-171">U kunt het query dialect opgeven met behulp van de para meter QueryDialect.</span><span class="sxs-lookup"><span data-stu-id="bd30a-171">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="bd30a-172">Als de opgegeven waarde dubbele aanhalings tekens ( `"` ), enkele aanhalings tekens ( `'` ) of een back slash ( `\` ) bevat, moet u deze tekens weglaten door ze te voorzien van een back slash ( `\` )-teken.</span><span class="sxs-lookup"><span data-stu-id="bd30a-172">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="bd30a-173">Als de opgegeven waarde gebruikmaakt van de WQL **like** -operator, moet u de volgende tekens door geven tussen vier Kante haken ( `[]` ): procent ( `%` ), onderstrepings teken () `_` of vier Kante haak openen ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="bd30a-173">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd30a-174">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="bd30a-174">-QueryDialect</span></span>

<span data-ttu-id="bd30a-175">Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter.</span><span class="sxs-lookup"><span data-stu-id="bd30a-175">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="bd30a-176">De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**.</span><span class="sxs-lookup"><span data-stu-id="bd30a-176">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="bd30a-177">De standaard waarde is **WQL**.</span><span class="sxs-lookup"><span data-stu-id="bd30a-177">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd30a-178">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="bd30a-178">-ResourceUri</span></span>

<span data-ttu-id="bd30a-179">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="bd30a-179">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="bd30a-180">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="bd30a-180">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="bd30a-181">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="bd30a-181">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="bd30a-182">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="bd30a-182">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="bd30a-183">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-183">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="bd30a-184">ResourceURI kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter ComputerName, waarmee een CIM-sessie wordt gemaakt met behulp van WSMan.</span><span class="sxs-lookup"><span data-stu-id="bd30a-184">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="bd30a-185">Als u deze para meter opgeeft zonder de para meter ComputerName op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter ResourceURI niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="bd30a-185">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="bd30a-186">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-186">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="bd30a-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bd30a-187">-Confirm</span></span>

<span data-ttu-id="bd30a-188">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bd30a-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bd30a-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bd30a-189">-WhatIf</span></span>

<span data-ttu-id="bd30a-190">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="bd30a-190">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bd30a-191">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="bd30a-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bd30a-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd30a-192">CommonParameters</span></span>

<span data-ttu-id="bd30a-193">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd30a-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd30a-194">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd30a-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bd30a-195">INVOER</span><span class="sxs-lookup"><span data-stu-id="bd30a-195">INPUTS</span></span>

### <span data-ttu-id="bd30a-196">Micro soft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="bd30a-196">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="bd30a-197">UITVOER</span><span class="sxs-lookup"><span data-stu-id="bd30a-197">OUTPUTS</span></span>

### <span data-ttu-id="bd30a-198">Micro soft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="bd30a-198">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="bd30a-199">Wanneer de para meter **PassThru** is opgegeven, retourneert deze cmdlet een gewijzigd object CIM-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="bd30a-199">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="bd30a-200">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="bd30a-200">NOTES</span></span>

## <span data-ttu-id="bd30a-201">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="bd30a-201">RELATED LINKS</span></span>

[<span data-ttu-id="bd30a-202">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bd30a-202">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="bd30a-203">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bd30a-203">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="bd30a-204">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bd30a-204">Remove-CimInstance</span></span>](remove-ciminstance.md)

