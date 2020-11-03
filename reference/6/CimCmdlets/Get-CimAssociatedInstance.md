---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: adf6c1ac6f6f9288233d530b7ea2101f4b7688e4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251503"
---
# <span data-ttu-id="a6921-103">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="a6921-103">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="a6921-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="a6921-104">SYNOPSIS</span></span>
<span data-ttu-id="a6921-105">Hiermee haalt u de CIM-exemplaren op die zijn verbonden met een specifiek CIM-exemplaar door een koppeling.</span><span class="sxs-lookup"><span data-stu-id="a6921-105">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="a6921-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="a6921-106">SYNTAX</span></span>

### <span data-ttu-id="a6921-107">Computerset (standaard)</span><span class="sxs-lookup"><span data-stu-id="a6921-107">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="a6921-108">Sessieset</span><span class="sxs-lookup"><span data-stu-id="a6921-108">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="a6921-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="a6921-109">DESCRIPTION</span></span>

<span data-ttu-id="a6921-110">De `Get-CimAssociatedInstance` cmdlet haalt de CIM-instanties op die zijn verbonden met een specifiek CIM-exemplaar, het bron exemplaar, door een koppeling.</span><span class="sxs-lookup"><span data-stu-id="a6921-110">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="a6921-111">In een koppeling heeft elk CIM-exemplaar een benoemde rol en hetzelfde CIM-exemplaar kan deel nemen aan een koppeling in verschillende rollen.</span><span class="sxs-lookup"><span data-stu-id="a6921-111">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="a6921-112">Als de para meter input object niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="a6921-112">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="a6921-113">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="a6921-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="a6921-114">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="a6921-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="a6921-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="a6921-115">EXAMPLES</span></span>

### <span data-ttu-id="a6921-116">Voor beeld 1: alle gekoppelde exemplaren van een specifiek exemplaar ophalen</span><span class="sxs-lookup"><span data-stu-id="a6921-116">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="a6921-117">Met deze reeks opdrachten worden de exemplaren van de klasse met de naam Win32_LogicalDisk opgehaald en worden de gegevens opgeslagen in een variabele `$disk` met de naam met behulp van de `Get-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6921-117">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="a6921-118">Het eerste exemplaar van de logische schijf in de variabele wordt vervolgens gebruikt als het invoer object voor de `Get-CimAssociatedInstance` cmdlet om alle gekoppelde CIM-exemplaren van het opgegeven CIM-exemplaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="a6921-118">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="a6921-119">Voor beeld 2: alle gekoppelde exemplaren van een specifiek type ophalen</span><span class="sxs-lookup"><span data-stu-id="a6921-119">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="a6921-120">Met deze reeks opdrachten worden alle exemplaren van de klasse **Win32_LogicalDisk** opgehaald en opgeslagen in een variabele met de naam `$disk` .</span><span class="sxs-lookup"><span data-stu-id="a6921-120">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="a6921-121">Het eerste exemplaar van de logische schijf in de variabele wordt vervolgens gebruikt als het invoer object voor de `Get-CimAssociatedInstance` cmdlet om alle gekoppelde exemplaren op te halen die zijn gekoppeld via de opgegeven koppelings klasse **Win32_DiskPartition**.</span><span class="sxs-lookup"><span data-stu-id="a6921-121">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition**.</span></span>

### <span data-ttu-id="a6921-122">Voor beeld 3: alle gekoppelde exemplaren ophalen via een kwalificatie van een specifieke klasse</span><span class="sxs-lookup"><span data-stu-id="a6921-122">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

<span data-ttu-id="a6921-123">Met deze reeks opdrachten worden de services opgehaald die afhankelijk zijn van de WMI-service en opgeslagen in een variabele met de naam `$s` .</span><span class="sxs-lookup"><span data-stu-id="a6921-123">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="a6921-124">De naam van de koppelings klasse voor de **Win32_DependentService** wordt opgehaald met de `Get-CimClass` cmdlet door een **koppeling** op te geven als de kwalificatie en vervolgens met $s aan de cmdlet wordt door gegeven `Get-CimAssociatedInstance` om alle gekoppelde exemplaren van de opgehaalde Association-klasse op te halen.</span><span class="sxs-lookup"><span data-stu-id="a6921-124">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="a6921-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a6921-125">PARAMETERS</span></span>

### <span data-ttu-id="a6921-126">-Association</span><span class="sxs-lookup"><span data-stu-id="a6921-126">-Association</span></span>

<span data-ttu-id="a6921-127">Hiermee geeft u de naam van de koppelings klasse op.</span><span class="sxs-lookup"><span data-stu-id="a6921-127">Specifies the name of the association class.</span></span> <span data-ttu-id="a6921-128">Als u deze para meter niet opgeeft, retourneert de cmdlet alle bestaande koppelings objecten van elk type.</span><span class="sxs-lookup"><span data-stu-id="a6921-128">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="a6921-129">Als klasse A bijvoorbeeld is gekoppeld aan klasse B via twee koppelingen, AB1 en AB2, dan kan deze para meter worden gebruikt om het type koppeling op te geven, hetzij AB1 of AB2.</span><span class="sxs-lookup"><span data-stu-id="a6921-129">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="a6921-130">-CimSession</span></span>

<span data-ttu-id="a6921-131">De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="a6921-131">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="a6921-132">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie maakt of ontvangt, zoals `New-CimSession` of `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="a6921-132">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="a6921-133">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a6921-133">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a6921-134">-ComputerName</span></span>

<span data-ttu-id="a6921-135">Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="a6921-135">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="a6921-136">U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="a6921-136">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="a6921-137">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="a6921-137">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="a6921-138">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="a6921-138">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="a6921-139">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="a6921-139">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-140">-Input object</span><span class="sxs-lookup"><span data-stu-id="a6921-140">-InputObject</span></span>

<span data-ttu-id="a6921-141">Hiermee geeft u de invoer voor deze cmdlet op.</span><span class="sxs-lookup"><span data-stu-id="a6921-141">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="a6921-142">U kunt deze para meter gebruiken, of u kunt de invoer door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6921-142">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-143">-Alleen-alleen</span><span class="sxs-lookup"><span data-stu-id="a6921-143">-KeyOnly</span></span>

<span data-ttu-id="a6921-144">Retourneert objecten waarvoor alleen sleutel eigenschappen zijn ingevuld.</span><span class="sxs-lookup"><span data-stu-id="a6921-144">Returns objects with only key properties populated.</span></span> <span data-ttu-id="a6921-145">Dit vermindert de hoeveelheid gegevens die via het netwerk wordt overgedragen.</span><span class="sxs-lookup"><span data-stu-id="a6921-145">This reduces the amount of data that is transferred over the network.</span></span>

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

### <span data-ttu-id="a6921-146">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="a6921-146">-Namespace</span></span>

<span data-ttu-id="a6921-147">Hiermee geeft u de naam ruimte voor de CIM-bewerking op.</span><span class="sxs-lookup"><span data-stu-id="a6921-147">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="a6921-148">De standaard naam ruimte is root-cimv2.</span><span class="sxs-lookup"><span data-stu-id="a6921-148">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="a6921-149">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="a6921-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="a6921-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="a6921-151">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="a6921-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="a6921-152">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="a6921-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="a6921-153">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="a6921-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="a6921-154">-ResourceUri</span></span>

<span data-ttu-id="a6921-155">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="a6921-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="a6921-156">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="a6921-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="a6921-157">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="a6921-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="a6921-158">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="a6921-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="a6921-159">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="a6921-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="a6921-160">**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.</span><span class="sxs-lookup"><span data-stu-id="a6921-160">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="a6921-161">Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, treedt er een fout op omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="a6921-161">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="a6921-162">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="a6921-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a6921-163">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="a6921-163">-ResultClassName</span></span>

<span data-ttu-id="a6921-164">Hiermee geeft u de naam van de klasse van de gekoppelde exemplaren.</span><span class="sxs-lookup"><span data-stu-id="a6921-164">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="a6921-165">Een CIM-exemplaar kan worden gekoppeld aan een of meer CIM-exemplaren.</span><span class="sxs-lookup"><span data-stu-id="a6921-165">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="a6921-166">Alle bijbehorende CIM-instanties worden geretourneerd als u de naam van de resultaat klasse niet opgeeft.</span><span class="sxs-lookup"><span data-stu-id="a6921-166">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="a6921-167">Standaard is de waarde van deze para meter Null en alle bijbehorende CIM-instanties worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a6921-167">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="a6921-168">U kunt de koppelings resultaten filteren zodat deze overeenkomen met de naam van een specifieke klasse.</span><span class="sxs-lookup"><span data-stu-id="a6921-168">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="a6921-169">Er wordt gefilterd op de-server.</span><span class="sxs-lookup"><span data-stu-id="a6921-169">Filtering happens on the server.</span></span> <span data-ttu-id="a6921-170">Als deze para meter niet wordt opgegeven, worden `Get-CIMAssociatedInstance` alle bestaande koppelingen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a6921-170">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="a6921-171">Als klasse A bijvoorbeeld is gekoppeld aan klassen B, C en D, dan kan deze para meter worden gebruikt om de uitvoer te beperken tot een specifiek type (B, C of D).</span><span class="sxs-lookup"><span data-stu-id="a6921-171">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

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

### <span data-ttu-id="a6921-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a6921-172">CommonParameters</span></span>

<span data-ttu-id="a6921-173">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a6921-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a6921-174">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="a6921-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a6921-175">INVOER</span><span class="sxs-lookup"><span data-stu-id="a6921-175">INPUTS</span></span>

### <span data-ttu-id="a6921-176">Geen</span><span class="sxs-lookup"><span data-stu-id="a6921-176">None</span></span>

<span data-ttu-id="a6921-177">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="a6921-177">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="a6921-178">UITVOER</span><span class="sxs-lookup"><span data-stu-id="a6921-178">OUTPUTS</span></span>

### <span data-ttu-id="a6921-179">System. object</span><span class="sxs-lookup"><span data-stu-id="a6921-179">System.Object</span></span>

<span data-ttu-id="a6921-180">Met deze cmdlet wordt een object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="a6921-180">This cmdlet returns an object.</span></span>

## <span data-ttu-id="a6921-181">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="a6921-181">NOTES</span></span>

## <span data-ttu-id="a6921-182">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="a6921-182">RELATED LINKS</span></span>

[<span data-ttu-id="a6921-183">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="a6921-183">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="a6921-184">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a6921-184">Get-CimInstance</span></span>](get-ciminstance.md)
