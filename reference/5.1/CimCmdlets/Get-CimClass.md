---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: e5700af4ff3f238d347e2c367416af08caf148ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250066"
---
# <span data-ttu-id="fbefb-103">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="fbefb-103">Get-CimClass</span></span>

## <span data-ttu-id="fbefb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="fbefb-104">SYNOPSIS</span></span>
<span data-ttu-id="fbefb-105">Hiermee wordt een lijst met CIM-klassen in een specifieke naam ruimte opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fbefb-105">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="fbefb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="fbefb-106">SYNTAX</span></span>

### <span data-ttu-id="fbefb-107">Computerset (standaard)</span><span class="sxs-lookup"><span data-stu-id="fbefb-107">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="fbefb-108">Sessieset</span><span class="sxs-lookup"><span data-stu-id="fbefb-108">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="fbefb-109">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fbefb-109">DESCRIPTION</span></span>

<span data-ttu-id="fbefb-110">De `Get-CimClass` cmdlet haalt een lijst met CIM-klassen op in een specifieke naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="fbefb-110">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="fbefb-111">Als er geen klassen naam is opgegeven, retourneert de cmdlet alle klassen in de naam ruimte.</span><span class="sxs-lookup"><span data-stu-id="fbefb-111">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="fbefb-112">In tegens telling tot een CIM-instantie bevatten CIM-klassen niet de CIM-sessie of de computer naam van waaruit ze worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fbefb-112">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="fbefb-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="fbefb-113">EXAMPLES</span></span>

### <span data-ttu-id="fbefb-114">Voor beeld 1: alle klassedefinities ophalen</span><span class="sxs-lookup"><span data-stu-id="fbefb-114">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="fbefb-115">In dit voor beeld worden alle klassedefinities in het **hoofd-cimv2** van de naam ruimte opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fbefb-115">This example gets all the class definitions under the namespace **root/cimv2**.</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="fbefb-116">Voor beeld 2: de klassen met een specifieke naam ophalen</span><span class="sxs-lookup"><span data-stu-id="fbefb-116">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="fbefb-117">In dit voor beeld worden de klassen met de woord **schijf** in hun naam opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fbefb-117">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="fbefb-118">Voor beeld 3: de klassen met een specifieke methode naam ophalen</span><span class="sxs-lookup"><span data-stu-id="fbefb-118">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="fbefb-119">In dit voor beeld worden de klassen opgehaald die beginnen met de naam **Win32** en een methode naam hebben die begint met een **term**.</span><span class="sxs-lookup"><span data-stu-id="fbefb-119">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term**.</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="fbefb-120">Voor beeld 4: de klassen met een specifieke eigenschaps naam ophalen</span><span class="sxs-lookup"><span data-stu-id="fbefb-120">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="fbefb-121">In dit voor beeld worden de klassen opgehaald die beginnen met de naam **Win32** en beschikken over een eigenschap met de naam **handle**.</span><span class="sxs-lookup"><span data-stu-id="fbefb-121">This example gets the classes that start with the name **Win32** and have a property named **Handle**.</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="fbefb-122">Voor beeld 5: de klassen met een specifieke kwalificatie naam ophalen</span><span class="sxs-lookup"><span data-stu-id="fbefb-122">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="fbefb-123">In dit voor beeld worden de klassen opgehaald die beginnen met de naam **Win32** , het woord **Disk** in hun namen bevatten en de opgegeven kwalificatie **koppeling** hebben.</span><span class="sxs-lookup"><span data-stu-id="fbefb-123">This example gets the classes that start with the name **Win32** , contain the word **Disk** in their names and have the specified qualifier **Association**.</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="fbefb-124">Voor beeld 6: de klassedefinities van een specifieke naam ruimte ophalen</span><span class="sxs-lookup"><span data-stu-id="fbefb-124">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="fbefb-125">In dit voor beeld worden de klassedefinities opgehaald die het woord **net** in hun namen bevatten van de opgegeven naam ruimte **root/standardCimv2**.</span><span class="sxs-lookup"><span data-stu-id="fbefb-125">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2**.</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="fbefb-126">Voor beeld 7: de klassedefinities ophalen van een externe server</span><span class="sxs-lookup"><span data-stu-id="fbefb-126">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="fbefb-127">In dit voor beeld worden de klassedefinities opgehaald die de woord **schijf** in hun namen bevatten van de opgegeven externe servers **Server01** en **Server02**.</span><span class="sxs-lookup"><span data-stu-id="fbefb-127">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02**.</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="fbefb-128">Voor beeld 8: de klassen ophalen met behulp van een CIM-sessie</span><span class="sxs-lookup"><span data-stu-id="fbefb-128">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="fbefb-129">Met deze reeks opdrachten maakt u een sessie met meerdere computers en slaat u deze op in een variabele `$s` met de `New-CimSession` cmdlet. vervolgens worden de klassen met de `Get-CimClass` cmdlet opgehaald.</span><span class="sxs-lookup"><span data-stu-id="fbefb-129">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="fbefb-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fbefb-130">PARAMETERS</span></span>

### <span data-ttu-id="fbefb-131">-CimSession</span><span class="sxs-lookup"><span data-stu-id="fbefb-131">-CimSession</span></span>

<span data-ttu-id="fbefb-132">Voert de cmdlet uit in een externe sessie of op een externe computer.</span><span class="sxs-lookup"><span data-stu-id="fbefb-132">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="fbefb-133">Voer een computer naam of een sessie object in, zoals de uitvoer van een- `New-CimSession` of- `Get-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fbefb-133">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="fbefb-134">De standaard waarde is de huidige sessie op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="fbefb-134">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="fbefb-135">-ClassName</span><span class="sxs-lookup"><span data-stu-id="fbefb-135">-ClassName</span></span>

<span data-ttu-id="fbefb-136">Hiermee geeft u de naam op van de CIM-klasse waarvoor de bewerking moet worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="fbefb-136">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="fbefb-137">U kunt met behulp van het tabblad volt ooien door de lijst met klassen bladeren, omdat Power shell een lijst met klassen van de lokale WMI-server krijgt om een lijst met klasse-namen te bieden.</span><span class="sxs-lookup"><span data-stu-id="fbefb-137">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fbefb-138">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="fbefb-138">-ComputerName</span></span>

<span data-ttu-id="fbefb-139">Hiermee geeft u de computer waarop u de CIM-bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="fbefb-139">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="fbefb-140">U kunt een Fully Qualified Domain Name (FQDN) een NetBIOS-naam of een IP-adres opgeven.</span><span class="sxs-lookup"><span data-stu-id="fbefb-140">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="fbefb-141">Als u deze para meter opgeeft, maakt de cmdlet een tijdelijke sessie met de opgegeven computer met behulp van het WsMan-protocol.</span><span class="sxs-lookup"><span data-stu-id="fbefb-141">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="fbefb-142">Als u deze para meter niet opgeeft, voert de cmdlet de bewerking uit op de lokale computer met behulp van Component Object Model (COM).</span><span class="sxs-lookup"><span data-stu-id="fbefb-142">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="fbefb-143">Als er meerdere bewerkingen worden uitgevoerd op dezelfde computer, biedt het gebruik van een CIM-sessie betere prestaties.</span><span class="sxs-lookup"><span data-stu-id="fbefb-143">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fbefb-144">-MethodName</span><span class="sxs-lookup"><span data-stu-id="fbefb-144">-MethodName</span></span>

<span data-ttu-id="fbefb-145">Zoekt de klassen die een methode hebben die overeenkomt met deze naam.</span><span class="sxs-lookup"><span data-stu-id="fbefb-145">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="fbefb-146">U kunt joker tekens gebruiken met deze para meter.</span><span class="sxs-lookup"><span data-stu-id="fbefb-146">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fbefb-147">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="fbefb-147">-Namespace</span></span>

<span data-ttu-id="fbefb-148">Hiermee geeft u de naam ruimte voor de CIM-bewerking op.</span><span class="sxs-lookup"><span data-stu-id="fbefb-148">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="fbefb-149">De standaard naam ruimte is **root-cimv2**.</span><span class="sxs-lookup"><span data-stu-id="fbefb-149">The default namespace is **root/cimv2**.</span></span> <span data-ttu-id="fbefb-150">U kunt met behulp van tab volt ooien door de lijst met naam ruimten bladeren, omdat Power shell een lijst met naam ruimten van de lokale WMI-server krijgt om de lijst met naam ruimten op te geven.</span><span class="sxs-lookup"><span data-stu-id="fbefb-150">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fbefb-151">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="fbefb-151">-OperationTimeoutSec</span></span>

<span data-ttu-id="fbefb-152">Hiermee geeft u de hoeveelheid tijd op die de cmdlet wacht op een reactie van de computer.</span><span class="sxs-lookup"><span data-stu-id="fbefb-152">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="fbefb-153">Standaard is de waarde van deze para meter 0, wat betekent dat de cmdlet de standaard time-outwaarde voor de server gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fbefb-153">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="fbefb-154">Als de para meter **OperationTimeoutSec** is ingesteld op een waarde die kleiner is dan de robuuste time-out voor de verbinding opnieuw proberen 3 minuten, kunnen netwerk fouten die langer zijn dan de waarde van de para meter **OperationTimeoutSec** , niet worden hersteld, omdat er een time-out optreedt voor de bewerking op de server voordat de client opnieuw verbinding kan maken.</span><span class="sxs-lookup"><span data-stu-id="fbefb-154">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="fbefb-155">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="fbefb-155">-PropertyName</span></span>

<span data-ttu-id="fbefb-156">Zoekt de klassen die een eigenschap hebben die overeenkomt met deze naam.</span><span class="sxs-lookup"><span data-stu-id="fbefb-156">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="fbefb-157">U kunt joker tekens gebruiken met deze para meter.</span><span class="sxs-lookup"><span data-stu-id="fbefb-157">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="fbefb-158">-Kwalificatienaam</span><span class="sxs-lookup"><span data-stu-id="fbefb-158">-QualifierName</span></span>

<span data-ttu-id="fbefb-159">Hiermee worden klassen gefilterd op klassen niveau kwalificatie naam.</span><span class="sxs-lookup"><span data-stu-id="fbefb-159">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="fbefb-160">U kunt joker tekens gebruiken met deze para meter.</span><span class="sxs-lookup"><span data-stu-id="fbefb-160">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="fbefb-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbefb-161">CommonParameters</span></span>

<span data-ttu-id="fbefb-162">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fbefb-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbefb-163">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fbefb-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fbefb-164">INVOER</span><span class="sxs-lookup"><span data-stu-id="fbefb-164">INPUTS</span></span>

### <span data-ttu-id="fbefb-165">Geen</span><span class="sxs-lookup"><span data-stu-id="fbefb-165">None</span></span>

<span data-ttu-id="fbefb-166">Deze cmdlet accepteert geen invoer objecten.</span><span class="sxs-lookup"><span data-stu-id="fbefb-166">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="fbefb-167">UITVOER</span><span class="sxs-lookup"><span data-stu-id="fbefb-167">OUTPUTS</span></span>

### <span data-ttu-id="fbefb-168">Micro soft. Management. Infrastructure. CimClass</span><span class="sxs-lookup"><span data-stu-id="fbefb-168">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="fbefb-169">Met deze cmdlet wordt een CIM-klasse-object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="fbefb-169">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="fbefb-170">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="fbefb-170">NOTES</span></span>

## <span data-ttu-id="fbefb-171">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="fbefb-171">RELATED LINKS</span></span>

[<span data-ttu-id="fbefb-172">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="fbefb-172">New-CimSession</span></span>](New-CimSession.md)
