---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: e14ba6db4f5e93c6e2c1824ce845f82720616bc5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706243"
---
# <span data-ttu-id="73bc2-102">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="73bc2-102">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="73bc2-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="73bc2-103">SYNOPSIS</span></span>
<span data-ttu-id="73bc2-104">Hiermee haalt u de CIM-exemplaren op die zijn verbonden met een specifiek CIM-exemplaar door een koppeling.</span><span class="sxs-lookup"><span data-stu-id="73bc2-104">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="73bc2-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="73bc2-105">SYNTAX</span></span>

### <span data-ttu-id="73bc2-106">Computerset (standaard)</span><span class="sxs-lookup"><span data-stu-id="73bc2-106">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="73bc2-107">Sessieset</span><span class="sxs-lookup"><span data-stu-id="73bc2-107">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="73bc2-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="73bc2-108">DESCRIPTION</span></span>

<span data-ttu-id="73bc2-109">De `Get-CimAssociatedInstance` cmdlet haalt de CIM-instanties op die zijn verbonden met een specifiek CIM-exemplaar, het bron exemplaar, door een koppeling.</span><span class="sxs-lookup"><span data-stu-id="73bc2-109">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="73bc2-110">In een koppeling heeft elk CIM-exemplaar een benoemde rol en hetzelfde CIM-exemplaar kan deel nemen aan een koppeling in verschillende rollen.</span><span class="sxs-lookup"><span data-stu-id="73bc2-110">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="73bc2-111">Als de para meter input object niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="73bc2-111">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="73bc2-112">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="73bc2-112">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="73bc2-113">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="73bc2-113">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="73bc2-114">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="73bc2-114">EXAMPLES</span></span>

### <span data-ttu-id="73bc2-115">Voor beeld 1: alle gekoppelde exemplaren van een specifiek exemplaar ophalen</span><span class="sxs-lookup"><span data-stu-id="73bc2-115">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="73bc2-116">Met deze reeks opdrachten worden de exemplaren van de klasse met de naam Win32_LogicalDisk opgehaald en worden de gegevens opgeslagen in een variabele `$disk` met de naam met behulp van de `Get-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73bc2-116">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="73bc2-117">Het eerste exemplaar van de logische schijf in de variabele wordt vervolgens gebruikt als het invoer object voor de `Get-CimAssociatedInstance` cmdlet om alle gekoppelde CIM-exemplaren van het opgegeven CIM-exemplaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="73bc2-117">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="73bc2-118">Voor beeld 2: alle gekoppelde exemplaren van een specifiek type ophalen</span><span class="sxs-lookup"><span data-stu-id="73bc2-118">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="73bc2-119">Met deze reeks opdrachten worden alle exemplaren van de klasse **Win32_LogicalDisk** opgehaald en opgeslagen in een variabele met de naam `$disk` .</span><span class="sxs-lookup"><span data-stu-id="73bc2-119">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="73bc2-120">Het eerste exemplaar van de logische schijf in de variabele wordt vervolgens gebruikt als het invoer object voor de `Get-CimAssociatedInstance` cmdlet om alle gekoppelde exemplaren op te halen die zijn gekoppeld via de opgegeven koppelings klasse **Win32_DiskPartition**.</span><span class="sxs-lookup"><span data-stu-id="73bc2-120">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition**.</span></span>

### <span data-ttu-id="73bc2-121">Voor beeld 3: alle gekoppelde exemplaren ophalen via een kwalificatie van een specifieke klasse</span><span class="sxs-lookup"><span data-stu-id="73bc2-121">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

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

<span data-ttu-id="73bc2-122">Met deze reeks opdrachten worden de services opgehaald die afhankelijk zijn van de WMI-service en opgeslagen in een variabele met de naam `$s` .</span><span class="sxs-lookup"><span data-stu-id="73bc2-122">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="73bc2-123">De naam van de koppelings klasse voor de **Win32_DependentService** wordt opgehaald met de `Get-CimClass` cmdlet door een **koppeling** op te geven als de kwalificatie en vervolgens met $s aan de cmdlet wordt door gegeven `Get-CimAssociatedInstance` om alle gekoppelde exemplaren van de opgehaalde Association-klasse op te halen.</span><span class="sxs-lookup"><span data-stu-id="73bc2-123">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="73bc2-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="73bc2-124">PARAMETERS</span></span>

### <span data-ttu-id="73bc2-125">-Association</span><span class="sxs-lookup"><span data-stu-id="73bc2-125">-Association</span></span>

<span data-ttu-id="73bc2-126">Hiermee geeft u de naam van de koppelings klasse op.</span><span class="sxs-lookup"><span data-stu-id="73bc2-126">Specifies the name of the association class.</span></span> <span data-ttu-id="73bc2-127">Als u deze para meter niet opgeeft, retourneert de cmdlet alle bestaande koppelings objecten van elk type.</span><span class="sxs-lookup"><span data-stu-id="73bc2-127">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="73bc2-128">Als klasse A bijvoorbeeld is gekoppeld aan klasse B via twee koppelingen, AB1 en AB2, dan kan deze para meter worden gebruikt om het type koppeling op te geven, hetzij AB1 of AB2.</span><span class="sxs-lookup"><span data-stu-id="73bc2-128">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

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

### <span data-ttu-id="73bc2-129">-CimSession</span><span class="sxs-lookup"><span data-stu-id="73bc2-129">-CimSession</span></span>

<span data-ttu-id="73bc2-130">De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="73bc2-130">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="73bc2-131">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie maakt of ontvangt, zoals `New-CimSession` of `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="73bc2-131">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="73bc2-132">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73bc2-132">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="73bc2-133">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="73bc2-133">-ComputerName</span></span>

<span data-ttu-id="73bc2-134">Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="73bc2-134">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="73bc2-135">U kunt een Fully Qualified Domain Name (FQDN) of een NetBIOS-naam opgeven.</span><span class="sxs-lookup"><span data-stu-id="73bc2-135">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="73bc2-136">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="73bc2-136">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="73bc2-137">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="73bc2-137">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="73bc2-138">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="73bc2-138">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="73bc2-139">-Input object</span><span class="sxs-lookup"><span data-stu-id="73bc2-139">-InputObject</span></span>

<span data-ttu-id="73bc2-140">Hiermee geeft u de invoer voor deze cmdlet op.</span><span class="sxs-lookup"><span data-stu-id="73bc2-140">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="73bc2-141">U kunt deze para meter gebruiken, of u kunt de invoer door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="73bc2-141">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

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

### <span data-ttu-id="73bc2-142">-Alleen-alleen</span><span class="sxs-lookup"><span data-stu-id="73bc2-142">-KeyOnly</span></span>

<span data-ttu-id="73bc2-143">Retourneert objecten waarvoor alleen sleutel eigenschappen zijn ingevuld.</span><span class="sxs-lookup"><span data-stu-id="73bc2-143">Returns objects with only key properties populated.</span></span> <span data-ttu-id="73bc2-144">Dit vermindert de hoeveelheid gegevens die via het netwerk wordt overgedragen.</span><span class="sxs-lookup"><span data-stu-id="73bc2-144">This reduces the amount of data that is transferred over the network.</span></span>

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

### <span data-ttu-id="73bc2-145">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="73bc2-145">-Namespace</span></span>

<span data-ttu-id="73bc2-146">Hiermee geeft u de naam ruimte voor de CIM-bewerking op.</span><span class="sxs-lookup"><span data-stu-id="73bc2-146">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="73bc2-147">De standaard naam ruimte is root-cimv2.</span><span class="sxs-lookup"><span data-stu-id="73bc2-147">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="73bc2-148">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="73bc2-148">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="73bc2-149">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="73bc2-149">-OperationTimeoutSec</span></span>

<span data-ttu-id="73bc2-150">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="73bc2-150">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="73bc2-151">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="73bc2-151">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="73bc2-152">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="73bc2-152">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="73bc2-153">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="73bc2-153">-ResourceUri</span></span>

<span data-ttu-id="73bc2-154">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="73bc2-154">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="73bc2-155">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="73bc2-155">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="73bc2-156">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="73bc2-156">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="73bc2-157">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="73bc2-157">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="73bc2-158">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="73bc2-158">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="73bc2-159">**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.</span><span class="sxs-lookup"><span data-stu-id="73bc2-159">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="73bc2-160">Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, treedt er een fout op omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="73bc2-160">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="73bc2-161">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="73bc2-161">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="73bc2-162">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="73bc2-162">-ResultClassName</span></span>

<span data-ttu-id="73bc2-163">Hiermee geeft u de naam van de klasse van de gekoppelde exemplaren.</span><span class="sxs-lookup"><span data-stu-id="73bc2-163">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="73bc2-164">Een CIM-exemplaar kan worden gekoppeld aan een of meer CIM-exemplaren.</span><span class="sxs-lookup"><span data-stu-id="73bc2-164">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="73bc2-165">Alle bijbehorende CIM-instanties worden geretourneerd als u de naam van de resultaat klasse niet opgeeft.</span><span class="sxs-lookup"><span data-stu-id="73bc2-165">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="73bc2-166">Standaard is de waarde van deze para meter Null en alle bijbehorende CIM-instanties worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="73bc2-166">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="73bc2-167">U kunt de koppelings resultaten filteren zodat deze overeenkomen met de naam van een specifieke klasse.</span><span class="sxs-lookup"><span data-stu-id="73bc2-167">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="73bc2-168">Er wordt gefilterd op de-server.</span><span class="sxs-lookup"><span data-stu-id="73bc2-168">Filtering happens on the server.</span></span> <span data-ttu-id="73bc2-169">Als deze para meter niet wordt opgegeven, worden `Get-CIMAssociatedInstance` alle bestaande koppelingen geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="73bc2-169">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="73bc2-170">Als klasse A bijvoorbeeld is gekoppeld aan klassen B, C en D, dan kan deze para meter worden gebruikt om de uitvoer te beperken tot een specifiek type (B, C of D).</span><span class="sxs-lookup"><span data-stu-id="73bc2-170">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

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

### <span data-ttu-id="73bc2-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="73bc2-171">CommonParameters</span></span>

<span data-ttu-id="73bc2-172">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="73bc2-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="73bc2-173">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="73bc2-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="73bc2-174">INVOER</span><span class="sxs-lookup"><span data-stu-id="73bc2-174">INPUTS</span></span>

### <span data-ttu-id="73bc2-175">Geen</span><span class="sxs-lookup"><span data-stu-id="73bc2-175">None</span></span>

<span data-ttu-id="73bc2-176">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="73bc2-176">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="73bc2-177">UITVOER</span><span class="sxs-lookup"><span data-stu-id="73bc2-177">OUTPUTS</span></span>

### <span data-ttu-id="73bc2-178">System. object</span><span class="sxs-lookup"><span data-stu-id="73bc2-178">System.Object</span></span>

<span data-ttu-id="73bc2-179">Met deze cmdlet wordt een object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="73bc2-179">This cmdlet returns an object.</span></span>

## <span data-ttu-id="73bc2-180">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="73bc2-180">NOTES</span></span>

## <span data-ttu-id="73bc2-181">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="73bc2-181">RELATED LINKS</span></span>

[<span data-ttu-id="73bc2-182">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="73bc2-182">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="73bc2-183">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="73bc2-183">Get-CimInstance</span></span>](get-ciminstance.md)

