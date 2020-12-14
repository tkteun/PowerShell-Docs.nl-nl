---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: 1217e07d09213d7c0e223129207c085b9ba2d48d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705404"
---
# <span data-ttu-id="f37c8-102">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="f37c8-102">Invoke-CimMethod</span></span>

## <span data-ttu-id="f37c8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="f37c8-103">SYNOPSIS</span></span>
<span data-ttu-id="f37c8-104">Hiermee wordt een methode van een CIM-klasse aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="f37c8-104">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="f37c8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="f37c8-105">SYNTAX</span></span>

### <span data-ttu-id="f37c8-106">ClassNameComputerSet (standaard)</span><span class="sxs-lookup"><span data-stu-id="f37c8-106">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f37c8-107">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-107">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f37c8-108">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-108">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f37c8-109">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-109">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f37c8-110">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-110">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f37c8-111">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-111">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="f37c8-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-112">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f37c8-113">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-113">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f37c8-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-114">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f37c8-115">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="f37c8-115">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f37c8-116">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="f37c8-116">DESCRIPTION</span></span>

<span data-ttu-id="f37c8-117">De `Invoke-CimMethod` cmdlet roept een methode aan van een CIM-klasse of CIM-exemplaar met behulp van de naam/waarde-paren die zijn opgegeven met de para meter **Arguments** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-117">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="f37c8-118">Als de para meter **input object** niet is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="f37c8-118">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f37c8-119">Als de para meter **ComputerName** noch de para meter **CimSession** is opgegeven, werkt deze cmdlet op lokale Windows Management Instrumentation (WMI) met behulp van een component object model (com)-sessie.</span><span class="sxs-lookup"><span data-stu-id="f37c8-119">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="f37c8-120">Als de para meter **ComputerName** of de para meter **CimSession** is opgegeven, werkt deze cmdlet voor de CIM-server die is opgegeven door de para meter **ComputerName** of de para meter **CimSession** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-120">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="f37c8-121">Als de para meter **input object** is opgegeven, werkt de cmdlet op een van de volgende manieren:</span><span class="sxs-lookup"><span data-stu-id="f37c8-121">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="f37c8-122">Als de para meter **ComputerName** of de para meter **CimSession** niet is opgegeven, gebruikt deze cmdlet de CIM-sessie of computer naam van het invoer object.</span><span class="sxs-lookup"><span data-stu-id="f37c8-122">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="f37c8-123">Als u de para meter **ComputerName** of de para meter **CimSession** opgeeft, gebruikt deze cmdlet de waarde van de para meter **CimSession** of **ComputerName** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-123">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="f37c8-124">Dit is geen gebruikelijk scenario.</span><span class="sxs-lookup"><span data-stu-id="f37c8-124">This is not a common scenario.</span></span>

## <span data-ttu-id="f37c8-125">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="f37c8-125">EXAMPLES</span></span>

### <span data-ttu-id="f37c8-126">Voor beeld 1: een methode aanroepen</span><span class="sxs-lookup"><span data-stu-id="f37c8-126">Example 1: Invoke a method</span></span>

<span data-ttu-id="f37c8-127">In dit voor beeld wordt de methode **Terminate** van de klasse **Win32_Process** aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="f37c8-127">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="f37c8-128">Voor beeld 2: een methode aanroepen met een CIM instance-object</span><span class="sxs-lookup"><span data-stu-id="f37c8-128">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="f37c8-129">In dit voor beeld wordt het CIM-exemplaar object opgehaald en opgeslagen in een variabele `$x` met de naam met behulp van de `Get-CimInstance` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f37c8-129">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="f37c8-130">De inhoud van de variabele wordt vervolgens gebruikt als de **input object** voor de `Invoke-CimMethod` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f37c8-130">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="f37c8-131">De methode **GetOwner** wordt aangeroepen voor de **CimInstance**.</span><span class="sxs-lookup"><span data-stu-id="f37c8-131">The **GetOwner** method is invoked for the **CimInstance**.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="f37c8-132">Voor beeld 3: een statische methode aanroepen met behulp van argumenten</span><span class="sxs-lookup"><span data-stu-id="f37c8-132">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="f37c8-133">In dit voor beeld wordt de **Create** -methode aangeroepen met de para meter **Arguments** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-133">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="f37c8-134">Voor beeld 4: validatie aan de client zijde</span><span class="sxs-lookup"><span data-stu-id="f37c8-134">Example 4: Client-side validation</span></span>

<span data-ttu-id="f37c8-135">In dit voor beeld wordt validatie aan de client zijde uitgevoerd voor de methode **xyz** door een **CimClass** -object door te geven aan `Invoke-CimMethod` .</span><span class="sxs-lookup"><span data-stu-id="f37c8-135">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="f37c8-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f37c8-136">PARAMETERS</span></span>

### <span data-ttu-id="f37c8-137">-Argumenten</span><span class="sxs-lookup"><span data-stu-id="f37c8-137">-Arguments</span></span>

<span data-ttu-id="f37c8-138">Hiermee geeft u de para meters op die worden door gegeven aan de aangeroepen methode.</span><span class="sxs-lookup"><span data-stu-id="f37c8-138">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="f37c8-139">Geef de waarden voor deze para meter op als naam/waarde-paren, opgeslagen in een hash-tabel.</span><span class="sxs-lookup"><span data-stu-id="f37c8-139">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="f37c8-140">De volg orde van de ingevoerde waarden is niet belang rijk.</span><span class="sxs-lookup"><span data-stu-id="f37c8-140">The order of the values entered isn't important.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-141">-CimClass</span><span class="sxs-lookup"><span data-stu-id="f37c8-141">-CimClass</span></span>

<span data-ttu-id="f37c8-142">Hiermee geeft u een CIM-klasse-object op dat een CIM-klassen definitie op de server vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="f37c8-142">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="f37c8-143">Gebruik deze para meter bij het aanroepen van een statische methode van een klasse.</span><span class="sxs-lookup"><span data-stu-id="f37c8-143">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="f37c8-144">U kunt de `Get-CimClass` cmdlet gebruiken om een klassedefinitie van de server op te halen.</span><span class="sxs-lookup"><span data-stu-id="f37c8-144">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="f37c8-145">Als u deze para meter gebruikt, worden de validaties van het schema aan de client zijde verbeterd.</span><span class="sxs-lookup"><span data-stu-id="f37c8-145">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-146">-CimSession</span><span class="sxs-lookup"><span data-stu-id="f37c8-146">-CimSession</span></span>

<span data-ttu-id="f37c8-147">De opdracht wordt uitgevoerd met behulp van de opgegeven CIM-sessie.</span><span class="sxs-lookup"><span data-stu-id="f37c8-147">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="f37c8-148">Voer een variabele in die de CIM-sessie bevat of een opdracht die de CIM-sessie, zoals de `New-CimSession` of cmdlets, maakt of ontvangt `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="f37c8-148">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="f37c8-149">Zie [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f37c8-149">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-150">-ClassName</span><span class="sxs-lookup"><span data-stu-id="f37c8-150">-ClassName</span></span>

<span data-ttu-id="f37c8-151">Hiermee geeft u de naam op van de CIM-klasse waarvoor de bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f37c8-151">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="f37c8-152">Deze para meter wordt alleen gebruikt voor statische methoden.</span><span class="sxs-lookup"><span data-stu-id="f37c8-152">This parameter is only used for static methods.</span></span> <span data-ttu-id="f37c8-153">U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.</span><span class="sxs-lookup"><span data-stu-id="f37c8-153">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-154">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="f37c8-154">-ComputerName</span></span>

<span data-ttu-id="f37c8-155">Hiermee geeft u de naam op van de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="f37c8-155">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="f37c8-156">U kunt een Fully Qualified Domain Name (FQDN), een NetBIOS-naam of een IP-adres opgeven.</span><span class="sxs-lookup"><span data-stu-id="f37c8-156">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="f37c8-157">Wanneer u deze para meter gebruikt, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="f37c8-157">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="f37c8-158">Anders voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="f37c8-158">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="f37c8-159">Verbinding maken met behulp van een CIM-sessie voor betere prestaties wanneer er meerdere bewerkingen worden uitgevoerd op dezelfde computer.</span><span class="sxs-lookup"><span data-stu-id="f37c8-159">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-160">-Input object</span><span class="sxs-lookup"><span data-stu-id="f37c8-160">-InputObject</span></span>

<span data-ttu-id="f37c8-161">Hiermee geeft u een CIM-exemplaar object op dat als invoer moet worden gebruikt om een methode aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="f37c8-161">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="f37c8-162">Deze para meter kan alleen worden gebruikt voor het aanroepen van instantie-methoden.</span><span class="sxs-lookup"><span data-stu-id="f37c8-162">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="f37c8-163">Voor het aanroepen van klasse statische methoden gebruikt u de para meter **Class** of de para meter **CimClass** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-163">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

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

### <span data-ttu-id="f37c8-164">-MethodName</span><span class="sxs-lookup"><span data-stu-id="f37c8-164">-MethodName</span></span>

<span data-ttu-id="f37c8-165">Hiermee geeft u de naam op van de CIM-methode die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="f37c8-165">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="f37c8-166">Deze para meter is verplicht en mag niet null of leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="f37c8-166">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="f37c8-167">Voor het aanroepen van een statische methode van een CIM-klasse gebruikt u de **className** of de **CimClass** -para meter.</span><span class="sxs-lookup"><span data-stu-id="f37c8-167">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-168">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="f37c8-168">-Namespace</span></span>

<span data-ttu-id="f37c8-169">Hiermee geeft u de naam ruimte voor de CIM-bewerking op.</span><span class="sxs-lookup"><span data-stu-id="f37c8-169">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="f37c8-170">De standaard naam ruimte is **root-cimv2**.</span><span class="sxs-lookup"><span data-stu-id="f37c8-170">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="f37c8-171">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="f37c8-171">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-172">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="f37c8-172">-OperationTimeoutSec</span></span>

<span data-ttu-id="f37c8-173">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="f37c8-173">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="f37c8-174">Standaard is de waarde 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f37c8-174">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="f37c8-175">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de standaard time-out voor het opnieuw proberen van drie minuten, kunnen netwerk storingen die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld.</span><span class="sxs-lookup"><span data-stu-id="f37c8-175">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="f37c8-176">-Query uitvoeren</span><span class="sxs-lookup"><span data-stu-id="f37c8-176">-Query</span></span>

<span data-ttu-id="f37c8-177">Hiermee geeft u een query op die moet worden uitgevoerd op de CIM-server.</span><span class="sxs-lookup"><span data-stu-id="f37c8-177">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="f37c8-178">Een methode wordt aangeroepen voor de instanties die zijn ontvangen als resultaat van de query.</span><span class="sxs-lookup"><span data-stu-id="f37c8-178">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="f37c8-179">U kunt het query dialect opgeven met behulp van de para meter **QueryDialect** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-179">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="f37c8-180">Als de opgegeven waarde dubbele aanhalings tekens ( `"` ), enkele aanhalings tekens ( `'` ) of een back slash ( `\` ) bevat, moet u deze tekens weglaten door ze te voorzien van een back slash ( `\` )-teken.</span><span class="sxs-lookup"><span data-stu-id="f37c8-180">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="f37c8-181">Als de opgegeven waarde gebruikmaakt van de WQL LIKE-operator, moet u de volgende tekens door geven tussen vier Kante haken ( `[]` ): procent ( `%` ), onderstrepings teken () `_` of vier Kante haak openen ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="f37c8-181">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

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

### <span data-ttu-id="f37c8-182">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="f37c8-182">-QueryDialect</span></span>

<span data-ttu-id="f37c8-183">Hiermee geeft u de query taal op die wordt gebruikt voor de query parameter.</span><span class="sxs-lookup"><span data-stu-id="f37c8-183">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="f37c8-184">De acceptabele waarden voor deze para meter zijn: **WQL** of **CQL**.</span><span class="sxs-lookup"><span data-stu-id="f37c8-184">The acceptable values for this parameter are: **WQL** or **CQL**.</span></span>

<span data-ttu-id="f37c8-185">De standaard waarde is **WQL**.</span><span class="sxs-lookup"><span data-stu-id="f37c8-185">The default value is **WQL**.</span></span>

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

### <span data-ttu-id="f37c8-186">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="f37c8-186">-ResourceUri</span></span>

<span data-ttu-id="f37c8-187">Hiermee geeft u de URI (Uniform Resource Identifier) van de resource klasse of het exemplaar op.</span><span class="sxs-lookup"><span data-stu-id="f37c8-187">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="f37c8-188">De URI wordt gebruikt om een specifiek type bron, zoals schijven of processen, op een computer te identificeren.</span><span class="sxs-lookup"><span data-stu-id="f37c8-188">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="f37c8-189">Een URI bestaat uit een voor voegsel en een pad naar een bron.</span><span class="sxs-lookup"><span data-stu-id="f37c8-189">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="f37c8-190">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="f37c8-190">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="f37c8-191">Als u deze para meter niet opgeeft, wordt standaard de DMTF-standaard resource-URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` gebruikt en wordt de naam van de klasse eraan toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="f37c8-191">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="f37c8-192">**ResourceURI** kan alleen worden gebruikt met CIM-sessies die zijn gemaakt met het WSMan-protocol, of bij het opgeven van de para meter **ComputerName** , waarmee een CIM-sessie wordt gemaakt met behulp van wsman.</span><span class="sxs-lookup"><span data-stu-id="f37c8-192">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="f37c8-193">Wanneer u deze para meter opgeeft zonder de para meter **ComputerName** op te geven, of wanneer u een CIM-sessie opgeeft die is gemaakt met DCOM-protocol, wordt er een fout melding weer geven.</span><span class="sxs-lookup"><span data-stu-id="f37c8-193">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="f37c8-194">Het DCOM-protocol biedt geen ondersteuning voor de para meter **ResourceURI** .</span><span class="sxs-lookup"><span data-stu-id="f37c8-194">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="f37c8-195">Als zowel de para meter **ResourceUri** als de **filter** parameter zijn opgegeven, wordt de **filter** parameter genegeerd.</span><span class="sxs-lookup"><span data-stu-id="f37c8-195">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f37c8-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f37c8-196">-Confirm</span></span>

<span data-ttu-id="f37c8-197">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f37c8-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f37c8-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f37c8-198">-WhatIf</span></span>

<span data-ttu-id="f37c8-199">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="f37c8-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f37c8-200">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="f37c8-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f37c8-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f37c8-201">CommonParameters</span></span>

<span data-ttu-id="f37c8-202">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f37c8-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f37c8-203">Zie [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f37c8-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="f37c8-204">INVOER</span><span class="sxs-lookup"><span data-stu-id="f37c8-204">INPUTS</span></span>

### <span data-ttu-id="f37c8-205">CIM-klasse</span><span class="sxs-lookup"><span data-stu-id="f37c8-205">CIM class</span></span>

<span data-ttu-id="f37c8-206">Met deze cmdlet wordt een CIM-klasse geaccepteerd als invoer object.</span><span class="sxs-lookup"><span data-stu-id="f37c8-206">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="f37c8-207">CIM-instantie</span><span class="sxs-lookup"><span data-stu-id="f37c8-207">CIM instance</span></span>

<span data-ttu-id="f37c8-208">Met deze cmdlet wordt een CIM-exemplaar geaccepteerd als invoer object.</span><span class="sxs-lookup"><span data-stu-id="f37c8-208">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="f37c8-209">UITVOER</span><span class="sxs-lookup"><span data-stu-id="f37c8-209">OUTPUTS</span></span>

### <span data-ttu-id="f37c8-210">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="f37c8-210">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="f37c8-211">Met deze cmdlet wordt een object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="f37c8-211">This cmdlet returns an object.</span></span>

## <span data-ttu-id="f37c8-212">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="f37c8-212">NOTES</span></span>

## <span data-ttu-id="f37c8-213">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="f37c8-213">RELATED LINKS</span></span>

[<span data-ttu-id="f37c8-214">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="f37c8-214">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="f37c8-215">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="f37c8-215">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="f37c8-216">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="f37c8-216">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="f37c8-217">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="f37c8-217">New-CimSession</span></span>](New-CimSession.md)

