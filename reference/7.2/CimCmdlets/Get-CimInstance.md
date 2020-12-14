---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 0e4a148601f3ef2212f9c97128c54258906106d7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705537"
---
# <span data-ttu-id="fccf9-102">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fccf9-102">Get-CimInstance</span></span>

## <span data-ttu-id="fccf9-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fccf9-103">SYNOPSIS</span></span>
<span data-ttu-id="fccf9-104">Hiermee worden de CIM-exemplaren van een klasse opgehaald van een CIM-server.</span><span class="sxs-lookup"><span data-stu-id="fccf9-104">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="fccf9-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fccf9-105">SYNTAX</span></span>

### <span data-ttu-id="fccf9-106">ClassNameComputerSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="fccf9-106">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="fccf9-107">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-107">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="fccf9-108">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-108">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="fccf9-109">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-109">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="fccf9-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-110">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="fccf9-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-111">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="fccf9-112">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-112">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="fccf9-113">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="fccf9-113">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="fccf9-114">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fccf9-114">DESCRIPTION</span></span>

<span data-ttu-id="fccf9-115">De `Get-CimInstance` cmdlet haalt de CIM-exemplaren van een klasse van een CIM-server op.</span><span class="sxs-lookup"><span data-stu-id="fccf9-115">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="fccf9-116">U kunt de naam van de klasse of een query voor deze cmdlet opgeven.</span><span class="sxs-lookup"><span data-stu-id="fccf9-116">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="fccf9-117">Deze cmdlet retourneert een of meer CIM-instantie objecten die een moment opname van de CIM-exemplaren vertegenwoordigen die aanwezig zijn op de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="fccf9-117">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="fccf9-118">Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="fccf9-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="fccf9-119">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="fccf9-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="fccf9-120">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="fccf9-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="fccf9-121">Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="fccf9-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="fccf9-122">Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="fccf9-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="fccf9-123">Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter CimSession of **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="fccf9-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="fccf9-124">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fccf9-124">EXAMPLES</span></span>

### <span data-ttu-id="fccf9-125">Voor beeld 1: de CIM-instanties van een opgegeven klasse ophalen</span><span class="sxs-lookup"><span data-stu-id="fccf9-125">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="fccf9-126">In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_Process** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fccf9-126">This example retrieves the CIM instances of a class named **Win32_Process**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="fccf9-127">Voor beeld 2: een lijst met naam ruimten van een WMI-server ophalen</span><span class="sxs-lookup"><span data-stu-id="fccf9-127">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="fccf9-128">In dit voor beeld wordt een lijst met naam ruimten in de **hoofd** naam ruimte op een WMI-server opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fccf9-128">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="fccf9-129">Voor beeld 3: instanties van een klasse die is gefilterd, ophalen met behulp van een query</span><span class="sxs-lookup"><span data-stu-id="fccf9-129">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="fccf9-130">In dit voor beeld worden alle CIM-instanties opgehaald die beginnen met de letter **P** van een klasse met de naam **Win32_Process** met behulp van de query die is opgegeven door een **query** parameter.</span><span class="sxs-lookup"><span data-stu-id="fccf9-130">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="fccf9-131">Voor beeld 4: instanties van een klasse die worden gefilterd, ophalen met behulp van een klassen naam en een filter expressie</span><span class="sxs-lookup"><span data-stu-id="fccf9-131">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="fccf9-132">In dit voor beeld worden alle CIM-instanties opgehaald die beginnen met de letter **P** van een klasse met de naam **Win32_Process** met behulp van de para meter filter.</span><span class="sxs-lookup"><span data-stu-id="fccf9-132">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="fccf9-133">Voor beeld 5: de CIM-instanties ophalen waarvoor alleen sleutel eigenschappen zijn ingevuld</span><span class="sxs-lookup"><span data-stu-id="fccf9-133">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="fccf9-134">In dit voor beeld wordt een nieuw CIM-exemplaar in het geheugen gemaakt voor een klasse met de naam **Win32_Process** met de sleutel eigenschap `@{ "Handle"=0 }` en wordt deze opgeslagen in een variabele met de naam `$x` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-134">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="fccf9-135">De variabele wordt door gegeven als een CIM-exemplaar aan de `Get-CimInstance` cmdlet om een bepaald exemplaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-135">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="fccf9-136">Voor beeld 6: CIM-instanties ophalen en opnieuw gebruiken</span><span class="sxs-lookup"><span data-stu-id="fccf9-136">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="fccf9-137">In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_Process** opgehaald en opgeslagen in de variabelen `$x` en `$y` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-137">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="fccf9-138">De variabele `$x` wordt vervolgens opgemaakt in een tabel die alleen de eigenschappen **name** en **KernelModeTime** bevat, de tabel die is ingesteld op **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="fccf9-138">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize**.</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="fccf9-139">Voor beeld 7: CIM-instanties ophalen van een externe computer</span><span class="sxs-lookup"><span data-stu-id="fccf9-139">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="fccf9-140">In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_ComputerSystem** opgehaald van de externe computers met de naam **Server01** en **Server02**.</span><span class="sxs-lookup"><span data-stu-id="fccf9-140">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="fccf9-141">Voor beeld 8: alleen de sleutel eigenschappen ophalen, in plaats van alle eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fccf9-141">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="fccf9-142">In dit voor beeld worden alleen de sleutel eigenschappen opgehaald, waardoor de grootte van het object en het netwerk verkeer wordt verminderd.</span><span class="sxs-lookup"><span data-stu-id="fccf9-142">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="fccf9-143">Voor beeld 9: er wordt slechts een subset van eigenschappen opgehaald, in plaats van alle eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fccf9-143">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="fccf9-144">In dit voor beeld wordt slechts een subset van eigenschappen opgehaald, waardoor de grootte van het object en het netwerk verkeer wordt verminderd.</span><span class="sxs-lookup"><span data-stu-id="fccf9-144">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="fccf9-145">Het exemplaar dat is opgehaald met de para meter **Property** kan worden gebruikt om andere CIM-bewerkingen uit te voeren, bijvoorbeeld `Set-CimInstance` of `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-145">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="fccf9-146">Voor beeld 10: het CIM-exemplaar met behulp van CIM-sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="fccf9-146">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="fccf9-147">In dit voor beeld wordt een CIM-sessie gemaakt op de computers met de naam **Server01** en **Server02** met behulp van de- `New-CimSession` cmdlet en worden de sessie gegevens opgeslagen in een variabele met de naam `$s` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-147">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="fccf9-148">De inhoud van de variabele wordt vervolgens door gegeven aan met `Get-CimInstance` behulp van de para meter **CimSession** om de CIM-exemplaren van de klasse met de naam **Win32_ComputerSystem** op te halen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-148">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem**.</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="fccf9-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fccf9-149">PARAMETERS</span></span>

### <span data-ttu-id="fccf9-150">-CimSession</span><span class="sxs-lookup"><span data-stu-id="fccf9-150">-CimSession</span></span>

<span data-ttu-id="fccf9-151">Hiermee geeft u de CIM-sessie op die moet worden gebruikt voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fccf9-151">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="fccf9-152">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de- `New-CimSession` of-cmdlets, maakt of ontvangt `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-152">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="fccf9-153">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fccf9-153">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-154">-ClassName</span><span class="sxs-lookup"><span data-stu-id="fccf9-154">-ClassName</span></span>

<span data-ttu-id="fccf9-155">Hiermee geeft u de naam op van de CIM-klasse waarvoor de CIM-exemplaren moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fccf9-155">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="fccf9-156">U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.</span><span class="sxs-lookup"><span data-stu-id="fccf9-156">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-157">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fccf9-157">-ComputerName</span></span>

<span data-ttu-id="fccf9-158">Hiermee geeft u de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="fccf9-158">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="fccf9-159">U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.</span><span class="sxs-lookup"><span data-stu-id="fccf9-159">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="fccf9-160">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="fccf9-160">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="fccf9-161">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="fccf9-161">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="fccf9-162">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, kunt u verbinding maken met behulp van een CIM-sessie voor betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="fccf9-162">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-163">-Filter</span><span class="sxs-lookup"><span data-stu-id="fccf9-163">-Filter</span></span>

<span data-ttu-id="fccf9-164">Hiermee geeft u een WHERE-component moet worden gebruikt als een filter.</span><span class="sxs-lookup"><span data-stu-id="fccf9-164">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="fccf9-165">Geef de component op in de **WQL** of de **CQL** -query taal.</span><span class="sxs-lookup"><span data-stu-id="fccf9-165">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="fccf9-166">Neem het `WHERE` sleutel woord niet op in de waarde van de para meter.</span><span class="sxs-lookup"><span data-stu-id="fccf9-166">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-167">-Input object</span><span class="sxs-lookup"><span data-stu-id="fccf9-167">-InputObject</span></span>

<span data-ttu-id="fccf9-168">Hiermee geeft u een CIM-exemplaar object op dat moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="fccf9-168">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="fccf9-169">Als u al met een CIM-instantie object werkt, kunt u deze para meter gebruiken om het object CIM-exemplaar door te geven om de meest recente moment opname van de CIM-server op te halen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-169">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="fccf9-170">Wanneer u een CIM-instantie object als invoer `Get-CimInstance` doorgeeft, retourneert het object van de server met behulp van een CIM-bewerking ophalen in plaats van een opsommings-of query bewerking.</span><span class="sxs-lookup"><span data-stu-id="fccf9-170">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="fccf9-171">Het gebruik van een CIM-bewerking ophalen is efficiënter dan wanneer alle instanties worden opgehaald en vervolgens worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="fccf9-171">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="fccf9-172">Als de CIM-klasse de Get-bewerking niet implementeert, wordt er een fout geretourneerd door de para meter **input object** op te geven.</span><span class="sxs-lookup"><span data-stu-id="fccf9-172">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-173">-Alleen-alleen</span><span class="sxs-lookup"><span data-stu-id="fccf9-173">-KeyOnly</span></span>

<span data-ttu-id="fccf9-174">Geeft aan dat alleen objecten met de sleutel eigenschappen worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fccf9-174">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="fccf9-175">Het opgeven van de para meter **alleen** waarde beperkt de hoeveelheid gegevens die via het netwerk worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-175">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="fccf9-176">Gebruik de **alleen** -sleutel parameter alleen een klein deel van het object dat kan worden gebruikt voor andere bewerkingen, zoals de-of- `Set-CimInstance` `Get-CimAssociatedInstance` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="fccf9-176">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-177">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="fccf9-177">-Namespace</span></span>

<span data-ttu-id="fccf9-178">Hiermee geeft u de naam ruimte van de CIM-klasse op.</span><span class="sxs-lookup"><span data-stu-id="fccf9-178">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="fccf9-179">De standaard naam ruimte is **root-cimv2**.</span><span class="sxs-lookup"><span data-stu-id="fccf9-179">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="fccf9-180">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="fccf9-180">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-181">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="fccf9-181">-OperationTimeoutSec</span></span>

<span data-ttu-id="fccf9-182">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="fccf9-182">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="fccf9-183">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fccf9-183">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="fccf9-184">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="fccf9-184">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="fccf9-185">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fccf9-185">-Property</span></span>

<span data-ttu-id="fccf9-186">Hiermee geeft u een set exemplaar eigenschappen op die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fccf9-186">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="fccf9-187">Gebruik deze para meter als u de grootte van het geretourneerde object wilt verkleinen, hetzij in het geheugen of via het netwerk.</span><span class="sxs-lookup"><span data-stu-id="fccf9-187">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="fccf9-188">Het geretourneerde object bevat ook de sleutel eigenschappen, zelfs als u deze niet hebt weer gegeven met de para meter **Property** .</span><span class="sxs-lookup"><span data-stu-id="fccf9-188">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="fccf9-189">Andere eigenschappen van de klasse zijn aanwezig, maar ze worden niet ingevuld.</span><span class="sxs-lookup"><span data-stu-id="fccf9-189">Other properties of the class are present but they are not populated.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-190">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="fccf9-190">-Query</span></span>

<span data-ttu-id="fccf9-191">Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="fccf9-191">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="fccf9-192">Als de opgegeven waarde dubbele aanhalings tekens `"` , enkele aanhalings tekens `'` of een back slash bevat `\` , moet u deze tekens weglaten door ze voor te plaatsen met het back slash-teken.</span><span class="sxs-lookup"><span data-stu-id="fccf9-192">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="fccf9-193">Als de opgegeven waarde gebruikmaakt van de WQL **like** -operator, moet u de volgende tekens door geven tussen vier Kante haken `[]` : percentage `%` , onderstrepings teken `_` of vier kant haakje openen `[` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-193">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="fccf9-194">U kunt geen meta gegevens query gebruiken om een lijst met klassen of een gebeurtenis query op te halen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-194">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="fccf9-195">Als u een lijst met klassen wilt ophalen, gebruikt u de `Get-CimClass` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fccf9-195">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="fccf9-196">Gebruik de cmdlet om een gebeurtenis query op te halen `Register-CimIndicationEvent` .</span><span class="sxs-lookup"><span data-stu-id="fccf9-196">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="fccf9-197">U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="fccf9-197">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-198">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="fccf9-198">-QueryDialect</span></span>

<span data-ttu-id="fccf9-199">Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter.</span><span class="sxs-lookup"><span data-stu-id="fccf9-199">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="fccf9-200">De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**.</span><span class="sxs-lookup"><span data-stu-id="fccf9-200">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="fccf9-201">De standaard waarde is **WQL**.</span><span class="sxs-lookup"><span data-stu-id="fccf9-201">The default value is **WQL**.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-202">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="fccf9-202">-ResourceUri</span></span>

<span data-ttu-id="fccf9-203">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="fccf9-203">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="fccf9-204">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="fccf9-204">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="fccf9-205">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="fccf9-205">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="fccf9-206">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="fccf9-206">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="fccf9-207">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="fccf9-207">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="fccf9-208">**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.</span><span class="sxs-lookup"><span data-stu-id="fccf9-208">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="fccf9-209">Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="fccf9-209">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="fccf9-210">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="fccf9-210">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-211">-Recente</span><span class="sxs-lookup"><span data-stu-id="fccf9-211">-Shallow</span></span>

<span data-ttu-id="fccf9-212">Geeft aan dat de instanties van een klasse worden geretourneerd zonder de exemplaren van onderliggende klassen op te nemen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-212">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="fccf9-213">De cmdlet retourneert standaard de exemplaren van een klasse en de onderliggende klassen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-213">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fccf9-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fccf9-214">CommonParameters</span></span>

<span data-ttu-id="fccf9-215">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fccf9-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fccf9-216">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fccf9-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fccf9-217">INVOER</span><span class="sxs-lookup"><span data-stu-id="fccf9-217">INPUTS</span></span>

### <span data-ttu-id="fccf9-218">CIM-instantie</span><span class="sxs-lookup"><span data-stu-id="fccf9-218">CIM Instance</span></span>

<span data-ttu-id="fccf9-219">Deze cmdlet accepteert een invoer object dat is opgegeven met de para meter input object.</span><span class="sxs-lookup"><span data-stu-id="fccf9-219">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="fccf9-220">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fccf9-220">OUTPUTS</span></span>

### <span data-ttu-id="fccf9-221">CIM-instantie</span><span class="sxs-lookup"><span data-stu-id="fccf9-221">CIM Instance</span></span>

<span data-ttu-id="fccf9-222">Met deze cmdlet worden een of meer CIM-instantie objecten geretourneerd die een moment opname van de CIM-exemplaren op de CIM-server vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="fccf9-222">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="fccf9-223">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fccf9-223">NOTES</span></span>

## <span data-ttu-id="fccf9-224">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fccf9-224">RELATED LINKS</span></span>

[<span data-ttu-id="fccf9-225">Format-Table</span><span class="sxs-lookup"><span data-stu-id="fccf9-225">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="fccf9-226">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="fccf9-226">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="fccf9-227">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="fccf9-227">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="fccf9-228">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="fccf9-228">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="fccf9-229">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fccf9-229">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="fccf9-230">REGI ster-CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="fccf9-230">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="fccf9-231">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fccf9-231">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="fccf9-232">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="fccf9-232">Set-CimInstance</span></span>](Set-CimInstance.md)

