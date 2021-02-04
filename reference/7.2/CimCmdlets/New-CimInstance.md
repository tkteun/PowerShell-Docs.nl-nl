---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: d81117ad6885d660e31f031bd8134096db91b7da
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705400"
---
# <span data-ttu-id="d776f-102">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d776f-102">New-CimInstance</span></span>

## <span data-ttu-id="d776f-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="d776f-103">SYNOPSIS</span></span>
<span data-ttu-id="d776f-104">Hiermee maakt u een CIM-exemplaar.</span><span class="sxs-lookup"><span data-stu-id="d776f-104">Creates a CIM instance.</span></span>

## <span data-ttu-id="d776f-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="d776f-105">SYNTAX</span></span>

### <span data-ttu-id="d776f-106">ClassNameComputerSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="d776f-106">ClassNameComputerSet (Default)</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d776f-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="d776f-107">ClassNameSessionSet</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d776f-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="d776f-108">ResourceUriSessionSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d776f-109">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="d776f-109">ResourceUriComputerSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d776f-110">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="d776f-110">CimClassSessionSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d776f-111">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="d776f-111">CimClassComputerSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d776f-112">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="d776f-112">DESCRIPTION</span></span>

<span data-ttu-id="d776f-113">`New-CimInstance`Met de cmdlet maakt u een instantie van een CIM-klasse op basis van de klassedefinitie op de lokale computer of een externe computer.</span><span class="sxs-lookup"><span data-stu-id="d776f-113">The `New-CimInstance` cmdlet creates an instance of a CIM class based on the class definition on either the local computer or a remote computer.</span></span> <span data-ttu-id="d776f-114">Standaard `New-CimInstance` maakt de cmdlet een instantie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="d776f-114">By default, the `New-CimInstance` cmdlet creates an instance on the local computer.</span></span>

## <span data-ttu-id="d776f-115">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="d776f-115">EXAMPLES</span></span>

### <span data-ttu-id="d776f-116">Voor beeld 1: een exemplaar van een CIM-klasse maken</span><span class="sxs-lookup"><span data-stu-id="d776f-116">Example 1: Create an instance of a CIM class</span></span>

<span data-ttu-id="d776f-117">In dit voor beeld wordt een exemplaar gemaakt van een CIM-klasse met de naam win32_environment in de naam ruimte root/cimv2 op de computer.</span><span class="sxs-lookup"><span data-stu-id="d776f-117">This example creates an instance of a CIM Class named win32_environment in the root/cimv2 namespace on the computer.</span></span>

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

<span data-ttu-id="d776f-118">Er wordt geen validatie aan de client zijde uitgevoerd als de klasse niet bestaat, de eigenschappen onjuist zijn of als de server de aanroep weigert.</span><span class="sxs-lookup"><span data-stu-id="d776f-118">No client side validation is performed if the class does not exist, the properties are wrong, or if the server rejects the call.</span></span> <span data-ttu-id="d776f-119">Als het exemplaar is gemaakt, wordt het zojuist gemaakte exemplaar uitgevoerd met de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d776f-119">If the instance is created successfully, the cmdlet outputs the newly created instance.</span></span>

### <span data-ttu-id="d776f-120">Voor beeld 2: een exemplaar van een CIM-klasse maken met behulp van een klassen schema</span><span class="sxs-lookup"><span data-stu-id="d776f-120">Example 2: Create an instance of a CIM class using a class schema</span></span>

<span data-ttu-id="d776f-121">In dit voor beeld wordt een CIM-klassen object opgehaald en opgeslagen in een variabele met de naam `$class` .</span><span class="sxs-lookup"><span data-stu-id="d776f-121">This example retrieves a CIM class object and stores it in a variable named `$class`.</span></span> <span data-ttu-id="d776f-122">De inhoud van de variabele wordt vervolgens door gegeven aan de `New-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d776f-122">The contents of the variable are then passed to the `New-CimInstance` cmdlet.</span></span>

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### <span data-ttu-id="d776f-123">Voor beeld 3: een dynamisch exemplaar maken op de client</span><span class="sxs-lookup"><span data-stu-id="d776f-123">Example 3: Create a dynamic instance on the client</span></span>

<span data-ttu-id="d776f-124">In dit voor beeld wordt een dynamisch exemplaar gemaakt van een CIM-klasse met de naam **Win32_Process** op de client computer zonder het exemplaar van de server op te halen.</span><span class="sxs-lookup"><span data-stu-id="d776f-124">This example creates a dynamic instance of a CIM class named **Win32_Process** on the client computer without getting the instance from the server.</span></span> <span data-ttu-id="d776f-125">De nieuwe instantie wordt opgeslagen in de variabele `$a` .</span><span class="sxs-lookup"><span data-stu-id="d776f-125">The new instance is stored in the variable `$a`.</span></span> <span data-ttu-id="d776f-126">Dit dynamische exemplaar kan worden gebruikt om bewerkingen uit te voeren als het exemplaar met deze sleutel op de server bestaat.</span><span class="sxs-lookup"><span data-stu-id="d776f-126">This dynamic instance can be used to perform operations if the instance with this key exists on the server.</span></span>

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

<span data-ttu-id="d776f-127">De `Get-CimInstance` cmdlet haalt vervolgens een bepaald enkel exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="d776f-127">The `Get-CimInstance` cmdlet then retrieves a particular single instance.</span></span> <span data-ttu-id="d776f-128">De `Invoke-CimMethod` cmdlet roept de methode **GetOwner** aan voor het opgehaalde exemplaar.</span><span class="sxs-lookup"><span data-stu-id="d776f-128">The `Invoke-CimMethod` cmdlet calls the **GetOwner** method on the retrieved instance.</span></span>

### <span data-ttu-id="d776f-129">Voor beeld 4: een exemplaar maken voor een CIM-klasse van een specifieke naam ruimte</span><span class="sxs-lookup"><span data-stu-id="d776f-129">Example 4: Create an instance for a CIM class of a specific namespace</span></span>

<span data-ttu-id="d776f-130">In dit voor beeld wordt een instantie van een CIM-klasse met de naam **MSFT_Something** in de naam ruimte **root/ergens** opgehaald en opgeslagen in een variabele met de naam `$class` .</span><span class="sxs-lookup"><span data-stu-id="d776f-130">This example gets an instance of a CIM class named **MSFT_Something** in the namespace **root/somewhere** and stores it in a variable named `$class`.</span></span> <span data-ttu-id="d776f-131">De variabele wordt door gegeven aan de `New-CimInstance` cmdlet om een nieuw CIM-exemplaar te maken en de validatie aan de client zijde op het nieuwe exemplaar uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d776f-131">The variable is passed to the `New-CimInstance` cmdlet to create a new CIM instance and perform client side validations on the new instance.</span></span>

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

<span data-ttu-id="d776f-132">In dit voor beeld wordt met behulp van de para meter **CimClass** in plaats van de para meter **className** gecontroleerd of **Prop1** en **Prop2** werkelijk bestaan en dat de sleutels correct zijn gemarkeerd.</span><span class="sxs-lookup"><span data-stu-id="d776f-132">In this example, using the **CimClass** parameter instead of the **ClassName** parameter validates that **Prop1** and **Prop2** actually exist and that the keys are marked correctly.</span></span>

<span data-ttu-id="d776f-133">U kunt de para meter **ComputerName** of **CimSession** niet gebruiken met de para meter **ClientOnly** .</span><span class="sxs-lookup"><span data-stu-id="d776f-133">You cannot use the **ComputerName** or **CimSession** parameter with the **ClientOnly** parameter.</span></span>

## <span data-ttu-id="d776f-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d776f-134">PARAMETERS</span></span>

### <span data-ttu-id="d776f-135">-CimClass</span><span class="sxs-lookup"><span data-stu-id="d776f-135">-CimClass</span></span>

<span data-ttu-id="d776f-136">Hiermee geeft u een CIM-klasse-object op dat het type van het exemplaar vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="d776f-136">Specifies a CIM class object that represents the type of the instance.</span></span> <span data-ttu-id="d776f-137">Gebruik de `Get-CimClass` cmdlet om de klassen declaratie van een computer op te halen.</span><span class="sxs-lookup"><span data-stu-id="d776f-137">Use the `Get-CimClass` cmdlet to retrieve the class declaration from a computer.</span></span> <span data-ttu-id="d776f-138">Als u deze para meter gebruikt, worden de validaties van het schema aan de client zijde verbeterd.</span><span class="sxs-lookup"><span data-stu-id="d776f-138">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-139">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d776f-139">-CimSession</span></span>

<span data-ttu-id="d776f-140">De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="d776f-140">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="d776f-141">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de `New-CimSession` of cmdlets, maakt of ontvangt `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="d776f-141">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="d776f-142">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d776f-142">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-143">-ClassName</span><span class="sxs-lookup"><span data-stu-id="d776f-143">-ClassName</span></span>

<span data-ttu-id="d776f-144">Hiermee geeft u de naam op van de CIM-klasse waarvan de bewerking een exemplaar maakt.</span><span class="sxs-lookup"><span data-stu-id="d776f-144">Specifies the name of the CIM class of which the operation creates an instance.</span></span> <span data-ttu-id="d776f-145">Opmerking: u kunt het volt ooien van het tabblad gebruiken om door de lijst met klassen te bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.</span><span class="sxs-lookup"><span data-stu-id="d776f-145">NOTE: You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="d776f-146">-ClientOnly</span><span class="sxs-lookup"><span data-stu-id="d776f-146">-ClientOnly</span></span>

<span data-ttu-id="d776f-147">Geeft aan dat het exemplaar alleen wordt gemaakt in Power shell zonder naar de CIM-server te gaan.</span><span class="sxs-lookup"><span data-stu-id="d776f-147">Indicates that the instance is only created in PowerShell without going to the CIM server.</span></span> <span data-ttu-id="d776f-148">U kunt deze para meter gebruiken om een CIM-exemplaar in het geheugen te maken voor gebruik in volgende Power shell-bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="d776f-148">You can use this parameter to create an in-memory CIM instance for use in subsequent PowerShell operations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-149">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d776f-149">-ComputerName</span></span>

<span data-ttu-id="d776f-150">Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="d776f-150">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="d776f-151">U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.</span><span class="sxs-lookup"><span data-stu-id="d776f-151">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="d776f-152">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WSMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="d776f-152">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WSMan protocol.</span></span>

<span data-ttu-id="d776f-153">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="d776f-153">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="d776f-154">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, levert het verbinden met behulp van een CIM-sessie betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="d776f-154">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-155">-Sleutel</span><span class="sxs-lookup"><span data-stu-id="d776f-155">-Key</span></span>

<span data-ttu-id="d776f-156">Hiermee geeft u de eigenschappen op die als sleutels worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d776f-156">Specifies the properties that are used as keys.</span></span> <span data-ttu-id="d776f-157">**CimSession** en **ComputerName** kunnen niet worden gebruikt als de **sleutel** is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="d776f-157">**CimSession** and **ComputerName** cannot be used when **Key** is specified.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-158">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="d776f-158">-Namespace</span></span>

<span data-ttu-id="d776f-159">Hiermee geeft u de naam ruimte van de klasse voor het nieuwe exemplaar.</span><span class="sxs-lookup"><span data-stu-id="d776f-159">Specifies the namespace of the class for the new instance.</span></span> <span data-ttu-id="d776f-160">De standaard naam ruimte is **root-cimv2**.</span><span class="sxs-lookup"><span data-stu-id="d776f-160">The default namespace is **root/cimv2**.</span></span>
<span data-ttu-id="d776f-161">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="d776f-161">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-162">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="d776f-162">-OperationTimeoutSec</span></span>

<span data-ttu-id="d776f-163">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="d776f-163">Specifies the amount of time that the cmdlet waits for a response from the CIM server.</span></span> <span data-ttu-id="d776f-164">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d776f-164">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span> <span data-ttu-id="d776f-165">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="d776f-165">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="d776f-166">-Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d776f-166">-Property</span></span>

<span data-ttu-id="d776f-167">Hiermee geeft u de eigenschappen van het CIM-exemplaar op met behulp van een hash-tabel (naam/waarde-paren).</span><span class="sxs-lookup"><span data-stu-id="d776f-167">Specifies the properties of the CIM instance using a hash table (name-value pairs).</span></span>

<span data-ttu-id="d776f-168">Als u de para meter **CimClass** opgeeft, `New-CimInstance` voert de cmdlet een validatie van eigenschappen op de client uit om ervoor te zorgen dat de opgegeven eigenschappen consistent zijn met de klassen declaratie op de-server.</span><span class="sxs-lookup"><span data-stu-id="d776f-168">If you specify the **CimClass** parameter, then the `New-CimInstance` cmdlet performs a property validation on the client to make sure that the properties specified are consistent with the class declaration on the server.</span></span> <span data-ttu-id="d776f-169">Als de para meter **CimClass** niet is opgegeven, wordt de eigenschaps validatie uitgevoerd op de server.</span><span class="sxs-lookup"><span data-stu-id="d776f-169">If the **CimClass** parameter is not specified, then the property validation is done on the server.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-170">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="d776f-170">-ResourceUri</span></span>

<span data-ttu-id="d776f-171">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="d776f-171">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="d776f-172">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d776f-172">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="d776f-173">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="d776f-173">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="d776f-174">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="d776f-174">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="d776f-175">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="d776f-175">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="d776f-176">**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.</span><span class="sxs-lookup"><span data-stu-id="d776f-176">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="d776f-177">Als u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of als u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, krijgt u een fout melding omdat het DCOM-protocol de para meter **ResourceURI** niet ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="d776f-177">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="d776f-178">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="d776f-178">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d776f-179">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d776f-179">-Confirm</span></span>

<span data-ttu-id="d776f-180">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d776f-180">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d776f-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d776f-181">-WhatIf</span></span>

<span data-ttu-id="d776f-182">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="d776f-182">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="d776f-183">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d776f-183">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d776f-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d776f-184">CommonParameters</span></span>

<span data-ttu-id="d776f-185">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d776f-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d776f-186">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d776f-186">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d776f-187">INVOER</span><span class="sxs-lookup"><span data-stu-id="d776f-187">INPUTS</span></span>

### <span data-ttu-id="d776f-188">Geen</span><span class="sxs-lookup"><span data-stu-id="d776f-188">None</span></span>

<span data-ttu-id="d776f-189">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="d776f-189">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="d776f-190">UITVOER</span><span class="sxs-lookup"><span data-stu-id="d776f-190">OUTPUTS</span></span>

### <span data-ttu-id="d776f-191">System. object</span><span class="sxs-lookup"><span data-stu-id="d776f-191">System.Object</span></span>

<span data-ttu-id="d776f-192">Met deze cmdlet wordt een object geretourneerd dat de informatie van het CIM-exemplaar bevat.</span><span class="sxs-lookup"><span data-stu-id="d776f-192">This cmdlet returns an object that contains the CIM instance information.</span></span>

## <span data-ttu-id="d776f-193">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="d776f-193">NOTES</span></span>

## <span data-ttu-id="d776f-194">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="d776f-194">RELATED LINKS</span></span>

[<span data-ttu-id="d776f-195">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="d776f-195">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="d776f-196">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d776f-196">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="d776f-197">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d776f-197">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="d776f-198">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d776f-198">Set-CimInstance</span></span>](Set-CimInstance.md)
