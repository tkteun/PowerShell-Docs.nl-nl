---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 468b0e62925774fb838263b9bd9aea6a74151b5f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/23/2020
ms.locfileid: "93251460"
---
# <span data-ttu-id="99381-103">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="99381-103">Get-CimInstance</span></span>

## <span data-ttu-id="99381-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="99381-104">SYNOPSIS</span></span>
<span data-ttu-id="99381-105">Hiermee worden de CIM-exemplaren van een klasse opgehaald van een CIM-server.</span><span class="sxs-lookup"><span data-stu-id="99381-105">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="99381-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="99381-106">SYNTAX</span></span>

### <span data-ttu-id="99381-107">ClassNameComputerSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="99381-107">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="99381-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="99381-108">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="99381-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="99381-109">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="99381-110">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="99381-110">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="99381-111">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="99381-111">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="99381-112">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="99381-112">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="99381-113">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="99381-113">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="99381-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="99381-114">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="99381-115">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="99381-115">DESCRIPTION</span></span>

<span data-ttu-id="99381-116">De `Get-CimInstance` cmdlet haalt de CIM-exemplaren van een klasse van een CIM-server op.</span><span class="sxs-lookup"><span data-stu-id="99381-116">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="99381-117">U kunt de naam van de klasse of een query voor deze cmdlet opgeven.</span><span class="sxs-lookup"><span data-stu-id="99381-117">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="99381-118">Deze cmdlet retourneert een of meer CIM-instantie objecten die een moment opname van de CIM-exemplaren vertegenwoordigen die aanwezig zijn op de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="99381-118">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="99381-119">Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="99381-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="99381-120">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="99381-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="99381-121">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="99381-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="99381-122">Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="99381-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="99381-123">Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="99381-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="99381-124">Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter CimSession of **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="99381-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="99381-125">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="99381-125">EXAMPLES</span></span>

### <span data-ttu-id="99381-126">Voor beeld 1: de CIM-instanties van een opgegeven klasse ophalen</span><span class="sxs-lookup"><span data-stu-id="99381-126">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="99381-127">In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_Process** opgehaald.</span><span class="sxs-lookup"><span data-stu-id="99381-127">This example retrieves the CIM instances of a class named **Win32_Process**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="99381-128">Voor beeld 2: een lijst met naam ruimten van een WMI-server ophalen</span><span class="sxs-lookup"><span data-stu-id="99381-128">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="99381-129">In dit voor beeld wordt een lijst met naam ruimten in de **hoofd** naam ruimte op een WMI-server opgehaald.</span><span class="sxs-lookup"><span data-stu-id="99381-129">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="99381-130">Voor beeld 3: instanties van een klasse die is gefilterd, ophalen met behulp van een query</span><span class="sxs-lookup"><span data-stu-id="99381-130">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="99381-131">In dit voor beeld worden alle CIM-instanties opgehaald die beginnen met de letter **P** van een klasse met de naam **Win32_Process** met behulp van de query die is opgegeven door een **query** parameter.</span><span class="sxs-lookup"><span data-stu-id="99381-131">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="99381-132">Voor beeld 4: instanties van een klasse die worden gefilterd, ophalen met behulp van een klassen naam en een filter expressie</span><span class="sxs-lookup"><span data-stu-id="99381-132">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="99381-133">In dit voor beeld worden alle CIM-instanties opgehaald die beginnen met de letter **P** van een klasse met de naam **Win32_Process** met behulp van de para meter filter.</span><span class="sxs-lookup"><span data-stu-id="99381-133">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="99381-134">Voor beeld 5: de CIM-instanties ophalen waarvoor alleen sleutel eigenschappen zijn ingevuld</span><span class="sxs-lookup"><span data-stu-id="99381-134">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="99381-135">In dit voor beeld wordt een nieuw CIM-exemplaar in het geheugen gemaakt voor een klasse met de naam **Win32_Process** met de sleutel eigenschap `@{ "Handle"=0 }` en wordt deze opgeslagen in een variabele met de naam `$x` .</span><span class="sxs-lookup"><span data-stu-id="99381-135">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="99381-136">De variabele wordt door gegeven als een CIM-exemplaar aan de `Get-CimInstance` cmdlet om een bepaald exemplaar op te halen.</span><span class="sxs-lookup"><span data-stu-id="99381-136">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="99381-137">Voor beeld 6: CIM-instanties ophalen en opnieuw gebruiken</span><span class="sxs-lookup"><span data-stu-id="99381-137">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="99381-138">In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_Process** opgehaald en opgeslagen in de variabelen `$x` en `$y` .</span><span class="sxs-lookup"><span data-stu-id="99381-138">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="99381-139">De variabele `$x` wordt vervolgens opgemaakt in een tabel die alleen de eigenschappen **name** en **KernelModeTime** bevat, de tabel die is ingesteld op **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="99381-139">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize**.</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="99381-140">Voor beeld 7: CIM-instanties ophalen van een externe computer</span><span class="sxs-lookup"><span data-stu-id="99381-140">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="99381-141">In dit voor beeld worden de CIM-exemplaren van een klasse met de naam **Win32_ComputerSystem** opgehaald van de externe computers met de naam **Server01** en **Server02**.</span><span class="sxs-lookup"><span data-stu-id="99381-141">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02**.</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="99381-142">Voor beeld 8: alleen de sleutel eigenschappen ophalen, in plaats van alle eigenschappen</span><span class="sxs-lookup"><span data-stu-id="99381-142">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="99381-143">In dit voor beeld worden alleen de sleutel eigenschappen opgehaald, waardoor de grootte van het object en het netwerk verkeer wordt verminderd.</span><span class="sxs-lookup"><span data-stu-id="99381-143">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="99381-144">Voor beeld 9: er wordt slechts een subset van eigenschappen opgehaald, in plaats van alle eigenschappen</span><span class="sxs-lookup"><span data-stu-id="99381-144">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="99381-145">In dit voor beeld wordt slechts een subset van eigenschappen opgehaald, waardoor de grootte van het object en het netwerk verkeer wordt verminderd.</span><span class="sxs-lookup"><span data-stu-id="99381-145">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="99381-146">Het exemplaar dat is opgehaald met de para meter **Property** kan worden gebruikt om andere CIM-bewerkingen uit te voeren, bijvoorbeeld `Set-CimInstance` of `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="99381-146">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="99381-147">Voor beeld 10: het CIM-exemplaar met behulp van CIM-sessie ophalen</span><span class="sxs-lookup"><span data-stu-id="99381-147">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="99381-148">In dit voor beeld wordt een CIM-sessie gemaakt op de computers met de naam **Server01** en **Server02** met behulp van de- `New-CimSession` cmdlet en worden de sessie gegevens opgeslagen in een variabele met de naam `$s` .</span><span class="sxs-lookup"><span data-stu-id="99381-148">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="99381-149">De inhoud van de variabele wordt vervolgens door gegeven aan met `Get-CimInstance` behulp van de para meter **CimSession** om de CIM-exemplaren van de klasse met de naam **Win32_ComputerSystem** op te halen.</span><span class="sxs-lookup"><span data-stu-id="99381-149">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem**.</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="99381-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="99381-150">PARAMETERS</span></span>

### <span data-ttu-id="99381-151">-CimSession</span><span class="sxs-lookup"><span data-stu-id="99381-151">-CimSession</span></span>

<span data-ttu-id="99381-152">Hiermee geeft u de CIM-sessie op die moet worden gebruikt voor deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="99381-152">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="99381-153">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de- `New-CimSession` of-cmdlets, maakt of ontvangt `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="99381-153">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="99381-154">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="99381-154">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

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

### <span data-ttu-id="99381-155">-ClassName</span><span class="sxs-lookup"><span data-stu-id="99381-155">-ClassName</span></span>

<span data-ttu-id="99381-156">Hiermee geeft u de naam op van de CIM-klasse waarvoor de CIM-exemplaren moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="99381-156">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="99381-157">U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.</span><span class="sxs-lookup"><span data-stu-id="99381-157">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="99381-158">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="99381-158">-ComputerName</span></span>

<span data-ttu-id="99381-159">Hiermee geeft u de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="99381-159">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="99381-160">U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.</span><span class="sxs-lookup"><span data-stu-id="99381-160">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="99381-161">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="99381-161">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="99381-162">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="99381-162">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="99381-163">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, kunt u verbinding maken met behulp van een CIM-sessie voor betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="99381-163">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

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

### <span data-ttu-id="99381-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="99381-164">-Filter</span></span>

<span data-ttu-id="99381-165">Hiermee geeft u een WHERE-component moet worden gebruikt als een filter.</span><span class="sxs-lookup"><span data-stu-id="99381-165">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="99381-166">Geef de component op in de **WQL** of de **CQL** -query taal.</span><span class="sxs-lookup"><span data-stu-id="99381-166">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="99381-167">Neem het `WHERE` sleutel woord niet op in de waarde van de para meter.</span><span class="sxs-lookup"><span data-stu-id="99381-167">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

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

### <span data-ttu-id="99381-168">-Input object</span><span class="sxs-lookup"><span data-stu-id="99381-168">-InputObject</span></span>

<span data-ttu-id="99381-169">Hiermee geeft u een CIM-exemplaar object op dat moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="99381-169">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="99381-170">Als u al met een CIM-instantie object werkt, kunt u deze para meter gebruiken om het object CIM-exemplaar door te geven om de meest recente moment opname van de CIM-server op te halen.</span><span class="sxs-lookup"><span data-stu-id="99381-170">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="99381-171">Wanneer u een CIM-instantie object als invoer `Get-CimInstance` doorgeeft, retourneert het object van de server met behulp van een CIM-bewerking ophalen in plaats van een opsommings-of query bewerking.</span><span class="sxs-lookup"><span data-stu-id="99381-171">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="99381-172">Het gebruik van een CIM-bewerking ophalen is efficiënter dan wanneer alle instanties worden opgehaald en vervolgens worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="99381-172">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="99381-173">Als de CIM-klasse de Get-bewerking niet implementeert, wordt er een fout geretourneerd door de para meter **input object** op te geven.</span><span class="sxs-lookup"><span data-stu-id="99381-173">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

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

### <span data-ttu-id="99381-174">-Alleen-alleen</span><span class="sxs-lookup"><span data-stu-id="99381-174">-KeyOnly</span></span>

<span data-ttu-id="99381-175">Geeft aan dat alleen objecten met de sleutel eigenschappen worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="99381-175">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="99381-176">Het opgeven van de para meter **alleen** waarde beperkt de hoeveelheid gegevens die via het netwerk worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="99381-176">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="99381-177">Gebruik de **alleen** -sleutel parameter alleen een klein deel van het object dat kan worden gebruikt voor andere bewerkingen, zoals de-of- `Set-CimInstance` `Get-CimAssociatedInstance` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="99381-177">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

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

### <span data-ttu-id="99381-178">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="99381-178">-Namespace</span></span>

<span data-ttu-id="99381-179">Hiermee geeft u de naam ruimte van de CIM-klasse op.</span><span class="sxs-lookup"><span data-stu-id="99381-179">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="99381-180">De standaard naam ruimte is **root-cimv2**.</span><span class="sxs-lookup"><span data-stu-id="99381-180">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="99381-181">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="99381-181">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="99381-182">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="99381-182">-OperationTimeoutSec</span></span>

<span data-ttu-id="99381-183">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="99381-183">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="99381-184">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="99381-184">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="99381-185">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="99381-185">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="99381-186">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="99381-186">-Property</span></span>

<span data-ttu-id="99381-187">Hiermee geeft u een set exemplaar eigenschappen op die moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="99381-187">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="99381-188">Gebruik deze para meter als u de grootte van het geretourneerde object wilt verkleinen, hetzij in het geheugen of via het netwerk.</span><span class="sxs-lookup"><span data-stu-id="99381-188">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="99381-189">Het geretourneerde object bevat ook de sleutel eigenschappen, zelfs als u deze niet hebt weer gegeven met de para meter **Property** .</span><span class="sxs-lookup"><span data-stu-id="99381-189">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="99381-190">Andere eigenschappen van de klasse zijn aanwezig, maar ze worden niet ingevuld.</span><span class="sxs-lookup"><span data-stu-id="99381-190">Other properties of the class are present but they are not populated.</span></span>

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

### <span data-ttu-id="99381-191">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="99381-191">-Query</span></span>

<span data-ttu-id="99381-192">Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="99381-192">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="99381-193">Als de opgegeven waarde dubbele aanhalings tekens `"` , enkele aanhalings tekens `'` of een back slash bevat `\` , moet u deze tekens weglaten door ze voor te plaatsen met het back slash-teken.</span><span class="sxs-lookup"><span data-stu-id="99381-193">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="99381-194">Als de opgegeven waarde gebruikmaakt van de WQL **like** -operator, moet u de volgende tekens door geven tussen vier Kante haken `[]` : percentage `%` , onderstrepings teken `_` of vier kant haakje openen `[` .</span><span class="sxs-lookup"><span data-stu-id="99381-194">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="99381-195">U kunt geen meta gegevens query gebruiken om een lijst met klassen of een gebeurtenis query op te halen.</span><span class="sxs-lookup"><span data-stu-id="99381-195">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="99381-196">Als u een lijst met klassen wilt ophalen, gebruikt u de `Get-CimClass` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="99381-196">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="99381-197">Gebruik de cmdlet om een gebeurtenis query op te halen `Register-CimIndicationEvent` .</span><span class="sxs-lookup"><span data-stu-id="99381-197">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="99381-198">U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="99381-198">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

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

### <span data-ttu-id="99381-199">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="99381-199">-QueryDialect</span></span>

<span data-ttu-id="99381-200">Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter.</span><span class="sxs-lookup"><span data-stu-id="99381-200">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="99381-201">De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**.</span><span class="sxs-lookup"><span data-stu-id="99381-201">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span> <span data-ttu-id="99381-202">De standaard waarde is **WQL**.</span><span class="sxs-lookup"><span data-stu-id="99381-202">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="99381-203">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="99381-203">-ResourceUri</span></span>

<span data-ttu-id="99381-204">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="99381-204">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="99381-205">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="99381-205">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="99381-206">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="99381-206">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="99381-207">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="99381-207">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="99381-208">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="99381-208">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="99381-209">**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.</span><span class="sxs-lookup"><span data-stu-id="99381-209">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="99381-210">Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="99381-210">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="99381-211">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="99381-211">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="99381-212">-Recente</span><span class="sxs-lookup"><span data-stu-id="99381-212">-Shallow</span></span>

<span data-ttu-id="99381-213">Geeft aan dat de instanties van een klasse worden geretourneerd zonder de exemplaren van onderliggende klassen op te nemen.</span><span class="sxs-lookup"><span data-stu-id="99381-213">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="99381-214">De cmdlet retourneert standaard de exemplaren van een klasse en de onderliggende klassen.</span><span class="sxs-lookup"><span data-stu-id="99381-214">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

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

### <span data-ttu-id="99381-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99381-215">CommonParameters</span></span>

<span data-ttu-id="99381-216">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="99381-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99381-217">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="99381-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99381-218">INVOER</span><span class="sxs-lookup"><span data-stu-id="99381-218">INPUTS</span></span>

### <span data-ttu-id="99381-219">Micro soft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="99381-219">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="99381-220">Deze cmdlet accepteert een invoer object dat is opgegeven met de para meter input object.</span><span class="sxs-lookup"><span data-stu-id="99381-220">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="99381-221">UITVOER</span><span class="sxs-lookup"><span data-stu-id="99381-221">OUTPUTS</span></span>

### <span data-ttu-id="99381-222">Micro soft. Management. Infrastructure. CimInstance</span><span class="sxs-lookup"><span data-stu-id="99381-222">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="99381-223">Met deze cmdlet worden een of meer CIM-instantie objecten geretourneerd die een moment opname van de CIM-exemplaren op de CIM-server vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="99381-223">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="99381-224">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="99381-224">NOTES</span></span>

## <span data-ttu-id="99381-225">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="99381-225">RELATED LINKS</span></span>

[<span data-ttu-id="99381-226">Format-Table</span><span class="sxs-lookup"><span data-stu-id="99381-226">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="99381-227">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="99381-227">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="99381-228">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="99381-228">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="99381-229">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="99381-229">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="99381-230">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="99381-230">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="99381-231">REGI ster-CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="99381-231">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="99381-232">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="99381-232">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="99381-233">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="99381-233">Set-CimInstance</span></span>](Set-CimInstance.md)
