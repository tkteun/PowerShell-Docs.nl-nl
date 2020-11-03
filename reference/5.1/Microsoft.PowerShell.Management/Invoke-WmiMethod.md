---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/invoke-wmimethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WmiMethod
ms.openlocfilehash: e9743488e86429e5cc3252162e51268a7978b79d
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2020
ms.locfileid: "93251431"
---
# <span data-ttu-id="b62d9-103">Invoke-WmiMethod</span><span class="sxs-lookup"><span data-stu-id="b62d9-103">Invoke-WmiMethod</span></span>

## <span data-ttu-id="b62d9-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="b62d9-104">SYNOPSIS</span></span>
<span data-ttu-id="b62d9-105">WMI-methoden aanroept.</span><span class="sxs-lookup"><span data-stu-id="b62d9-105">Calls WMI methods.</span></span>

## <span data-ttu-id="b62d9-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="b62d9-106">SYNTAX</span></span>

### <span data-ttu-id="b62d9-107">klasse (standaard)</span><span class="sxs-lookup"><span data-stu-id="b62d9-107">class (Default)</span></span>

```
Invoke-WmiMethod [-Class] <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b62d9-108">object</span><span class="sxs-lookup"><span data-stu-id="b62d9-108">object</span></span>

```
Invoke-WmiMethod -InputObject <ManagementObject> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b62d9-109">leertraject</span><span class="sxs-lookup"><span data-stu-id="b62d9-109">path</span></span>

```
Invoke-WmiMethod -Path <String> [-Name] <String> [-ArgumentList <Object[]>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b62d9-110">WQLQuery</span><span class="sxs-lookup"><span data-stu-id="b62d9-110">WQLQuery</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b62d9-111">query</span><span class="sxs-lookup"><span data-stu-id="b62d9-111">query</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b62d9-112">list</span><span class="sxs-lookup"><span data-stu-id="b62d9-112">list</span></span>

```
Invoke-WmiMethod [-Name] <String> [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b62d9-113">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="b62d9-113">DESCRIPTION</span></span>

<span data-ttu-id="b62d9-114">De `Invoke-WmiMethod` cmdlet roept de methoden van de Windows Management Instrumentation-objecten (WMI) aan.</span><span class="sxs-lookup"><span data-stu-id="b62d9-114">The `Invoke-WmiMethod` cmdlet calls the methods of Windows Management Instrumentation (WMI) objects.</span></span>

<span data-ttu-id="b62d9-115">Nieuwe Common Information Model (CIM)-cmdlets, geïntroduceerd in Windows Power Shell 3,0, voeren dezelfde taken uit als de WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b62d9-115">New Common Information Model (CIM) cmdlets, introduced in Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="b62d9-116">De CIM-cmdlets voldoen aan de WS-Management (WSMan)-standaarden en met de CIM-standaard, waardoor de-cmdlets dezelfde technieken kunnen gebruiken voor het beheren van Windows-computers en die met andere besturings systemen.</span><span class="sxs-lookup"><span data-stu-id="b62d9-116">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage Windows computers and those running other operating systems.</span></span> <span data-ttu-id="b62d9-117">In plaats van met kunt `Invoke-WmiMethod` u ook [invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md)gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b62d9-117">Instead of using `Invoke-WmiMethod`, consider using [Invoke-CimMethod](../cimcmdlets/invoke-cimmethod.md).</span></span>

## <span data-ttu-id="b62d9-118">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="b62d9-118">EXAMPLES</span></span>

### <span data-ttu-id="b62d9-119">Voor beeld 1: de vereiste volg orde van WMI-objecten weer geven</span><span class="sxs-lookup"><span data-stu-id="b62d9-119">Example 1: List the required order of WMI objects</span></span>

```powershell
([wmiclass]'Win32_Volume').GetMethodParameters('Format')
```

```Output
__GENUS           : 2
__CLASS           : __PARAMETERS
__SUPERCLASS      :
__DYNASTY         : __PARAMETERS
__RELPATH         :
__PROPERTY_COUNT  : 6
__DERIVATION      : {}
__SERVER          :
__NAMESPACE       :
__PATH            :
ClusterSize       : 0
EnableCompression : False
FileSystem        : NTFS
Label             :
QuickFormat       : False
Version           : 0
PSComputerName    :
```

<span data-ttu-id="b62d9-120">Met deze opdracht wordt een lijst weer gegeven met de vereiste volg orde van de objecten.</span><span class="sxs-lookup"><span data-stu-id="b62d9-120">This command lists the required order of the objects.</span></span> <span data-ttu-id="b62d9-121">Voor het aanroepen van WMI in Power Shell 3,0 wijkt af van alternatieve methoden en vereist dat object waarden in een specifieke volg orde worden ingevoerd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-121">To invoke WMI in PowerShell 3.0 differs from alternate methods, and requires that object values are entered in a specific order.</span></span>

### <span data-ttu-id="b62d9-122">Voor beeld 2: een exemplaar van een toepassing starten</span><span class="sxs-lookup"><span data-stu-id="b62d9-122">Example 2: Start an instance of an application</span></span>

```powershell
([Wmiclass]'Win32_Process').GetMethodParameters('Create')
```

```Output
__GENUS                   : 2
__CLASS                   : __PARAMETERS
__SUPERCLASS              :
__DYNASTY                 : __PARAMETERS
__RELPATH                 :
__PROPERTY_COUNT          : 3
__DERIVATION              : {}
__SERVER                  :
__NAMESPACE               :
__PATH                    :
CommandLine               :
CurrentDirectory          :
ProcessStartupInformation :
PSComputerName            :
```

```powershell
Invoke-WmiMethod -Path win32_process -Name create -ArgumentList notepad.exe
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 2
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ProcessId        : 11312
ReturnValue      : 0
PSComputerName   :
```

<span data-ttu-id="b62d9-123">Met deze opdracht start u een exemplaar van Klad blok door de `Create` methode van de **Win32_Process** -klasse aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="b62d9-123">This command starts an instance of Notepad by calling the `Create` method of the **Win32_Process** class.</span></span>

<span data-ttu-id="b62d9-124">De eigenschap **returnValue** wordt gevuld met een 0 en de eigenschap **ProcessID** wordt gevuld met een geheel getal (het nummer van de volgende proces-id) als de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b62d9-124">The **ReturnValue** property is populated with a 0, and the **ProcessId** property is populated with an integer (the next process ID number) if the command is completed.</span></span>

### <span data-ttu-id="b62d9-125">Voor beeld 3: de naam van een bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="b62d9-125">Example 3: Rename a file</span></span>

```powershell
Invoke-WmiMethod -Path "CIM_DataFile.Name='C:\scripts\test.txt'" -Name Rename -ArgumentList "C:\scripts\test_bu.txt"
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
ReturnValue      : 0
```

<span data-ttu-id="b62d9-126">Met deze opdracht wordt de naam van een bestand gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-126">This command renames a file.</span></span> <span data-ttu-id="b62d9-127">De para meter **Path** wordt gebruikt om te verwijzen naar een exemplaar van de klasse **CIM_DataFile** .</span><span class="sxs-lookup"><span data-stu-id="b62d9-127">It uses the **Path** parameter to reference an instance of the **CIM_DataFile** class.</span></span> <span data-ttu-id="b62d9-128">Vervolgens wordt de methode Rename toegepast op dat specifieke exemplaar.</span><span class="sxs-lookup"><span data-stu-id="b62d9-128">Then, it applies the Rename method to that particular instance.</span></span>

<span data-ttu-id="b62d9-129">De eigenschap **returnValue** wordt gevuld met een 0 als de opdracht is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b62d9-129">The **ReturnValue** property is populated with a 0 if the command is completed.</span></span>

### <span data-ttu-id="b62d9-130">Voor beeld 4: een matrix met waarden door geven met `-ArgumentList`</span><span class="sxs-lookup"><span data-stu-id="b62d9-130">Example 4: Passing an array of values using `-ArgumentList`</span></span>

<span data-ttu-id="b62d9-131">Een voor beeld van het gebruik van een matrix met objecten `$binSD` gevolgd door een `$null` waarde.</span><span class="sxs-lookup"><span data-stu-id="b62d9-131">An example using an array of objects `$binSD` followed by a `$null` value.</span></span>

```powershell
$acl = get-acl test.txt
$binSD = $acl.GetSecurityDescriptorBinaryForm()
Invoke-WmiMethod -class Win32_SecurityDescriptorHelper -Name BinarySDToSDDL -ArgumentList $binSD, $null
```

## <span data-ttu-id="b62d9-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b62d9-132">PARAMETERS</span></span>

### <span data-ttu-id="b62d9-133">-Argument List</span><span class="sxs-lookup"><span data-stu-id="b62d9-133">-ArgumentList</span></span>

<span data-ttu-id="b62d9-134">Hiermee geeft u de para meters op die worden door gegeven aan de aangeroepen methode.</span><span class="sxs-lookup"><span data-stu-id="b62d9-134">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="b62d9-135">De waarde van deze para meter moet een matrix met objecten zijn en moet worden weer gegeven in de volg orde die wordt vereist door de aangeroepen methode.</span><span class="sxs-lookup"><span data-stu-id="b62d9-135">The value of this parameter must be an array of objects, and they must appear in the order required by the called method.</span></span> <span data-ttu-id="b62d9-136">`Invoke-CimCommand`Deze beperkingen gelden niet voor de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b62d9-136">The `Invoke-CimCommand` cmdlet does not have these limitations.</span></span>

<span data-ttu-id="b62d9-137">Als u de volg orde wilt bepalen waarin deze objecten worden weer gegeven, voert u de `GetMethodParameters()` methode uit op de WMI-klasse, zoals in voor beeld 1, aan het einde van dit onderwerp.</span><span class="sxs-lookup"><span data-stu-id="b62d9-137">To determine the order in which to list those objects, run the `GetMethodParameters()` method on the WMI class, as illustrated in Example 1, near the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b62d9-138">Als de eerste waarde een matrix is die meer dan één element bevat, is een tweede waarde van $null vereist.</span><span class="sxs-lookup"><span data-stu-id="b62d9-138">If the first value is an array that contains more than one element, a second value of $null is required.</span></span> <span data-ttu-id="b62d9-139">Anders wordt er een fout gegenereerd, zoals ' kan een object van het type System. byte niet converteren naar het type ' System. array '. '.</span><span class="sxs-lookup"><span data-stu-id="b62d9-139">Otherwise, the command generates an error, such as "Unable to cast object of type 'System.Byte' to type 'System.Array'.".</span></span> <span data-ttu-id="b62d9-140">Zie voor beeld 4 hierboven.</span><span class="sxs-lookup"><span data-stu-id="b62d9-140">See example 4 above.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: class, object, path
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-141">-AsJob</span><span class="sxs-lookup"><span data-stu-id="b62d9-141">-AsJob</span></span>

<span data-ttu-id="b62d9-142">Geeft aan dat met deze cmdlet de opdracht wordt uitgevoerd als een achtergrond taak.</span><span class="sxs-lookup"><span data-stu-id="b62d9-142">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="b62d9-143">Gebruik deze para meter om opdrachten uit te voeren die lange tijd duren om te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b62d9-143">Use this parameter to run commands that take a long time to finish.</span></span>

<span data-ttu-id="b62d9-144">Wanneer u de para meter **AsJob** gebruikt, retourneert de opdracht een object dat de achtergrond taak vertegenwoordigt en wordt vervolgens de opdracht prompt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="b62d9-144">When you use the **AsJob** parameter, the command returns an object that represents the background job and then displays the command prompt.</span></span> <span data-ttu-id="b62d9-145">U kunt in de sessie blijven werken terwijl de taak is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b62d9-145">You can continue to work in the session while the job finishes.</span></span> <span data-ttu-id="b62d9-146">Als `Invoke-WmiMethod` wordt gebruikt voor een externe computer, wordt de taak gemaakt op de lokale computer en worden de resultaten van externe computers automatisch teruggestuurd naar de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b62d9-146">If `Invoke-WmiMethod` is used against a remote computer, the job is created on the local computer, and the results from remote computers are automatically returned to the local computer.</span></span> <span data-ttu-id="b62d9-147">Als u de taak wilt beheren, gebruikt u de cmdlets die het zelfstandige taak onderdeel (de taak-cmdlets) bevatten.</span><span class="sxs-lookup"><span data-stu-id="b62d9-147">To manage the job, use the cmdlets that contain the Job noun (the Job cmdlets).</span></span> <span data-ttu-id="b62d9-148">Gebruik de cmdlet Receive-Job om de taak resultaten te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="b62d9-148">To get the job results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="b62d9-149">Als u deze para meter met externe computers wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang.</span><span class="sxs-lookup"><span data-stu-id="b62d9-149">To use this parameter with remote computers, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="b62d9-150">Daarnaast moet u Windows Power shell starten met de optie als administrator uitvoeren in Windows Vista en latere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="b62d9-150">Additionally, you must start Windows PowerShell by using the Run as administrator option in Windows Vista and later versions of Windows.</span></span> <span data-ttu-id="b62d9-151">Zie about_Remote_Requirements voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b62d9-151">For more information, see about_Remote_Requirements.</span></span>

<span data-ttu-id="b62d9-152">Zie about_Jobs en about_Remote_Jobs voor meer informatie over Windows Power shell-achtergrond taken.</span><span class="sxs-lookup"><span data-stu-id="b62d9-152">For more information about Windows PowerShell background jobs, see about_Jobs and about_Remote_Jobs.</span></span>

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

### <span data-ttu-id="b62d9-153">-Verificatie</span><span class="sxs-lookup"><span data-stu-id="b62d9-153">-Authentication</span></span>

<span data-ttu-id="b62d9-154">Hiermee geeft u het verificatie niveau op dat moet worden gebruikt met de WMI-verbinding.</span><span class="sxs-lookup"><span data-stu-id="b62d9-154">Specifies the authentication level to be used with the WMI connection.</span></span> <span data-ttu-id="b62d9-155">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b62d9-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b62d9-156">-1: ongewijzigd</span><span class="sxs-lookup"><span data-stu-id="b62d9-156">-1: Unchanged</span></span>
- <span data-ttu-id="b62d9-157">0: standaard</span><span class="sxs-lookup"><span data-stu-id="b62d9-157">0: Default</span></span>
- <span data-ttu-id="b62d9-158">1: geen (er is geen verificatie uitgevoerd.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-158">1: None (No authentication in performed.)</span></span>
- <span data-ttu-id="b62d9-159">2: verbinding maken (verificatie wordt alleen uitgevoerd wanneer de client een relatie tot stand brengt met de toepassing.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-159">2: Connect (Authentication is performed only when the client establishes a relationship with the application.)</span></span>
- <span data-ttu-id="b62d9-160">3: aanroep (verificatie wordt alleen uitgevoerd aan het begin van elke aanroep wanneer de toepassing de aanvraag ontvangt.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-160">3: Call (Authentication is performed only at the beginning of each call when the application receives the request.)</span></span>
- <span data-ttu-id="b62d9-161">4: pakket (verificatie wordt uitgevoerd op alle gegevens die van de client worden ontvangen.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-161">4: Packet (Authentication is performed on all the data that is received from the client.)</span></span>
- <span data-ttu-id="b62d9-162">5: PacketIntegrity (alle gegevens die worden overgebracht tussen de client en de toepassing worden geverifieerd en geverifieerd.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-162">5: PacketIntegrity (All the data that is transferred between the client and the application is authenticated and verified.)</span></span>
- <span data-ttu-id="b62d9-163">6: PacketPrivacy (de eigenschappen van de andere authenticatie niveaus worden gebruikt en alle gegevens worden versleuteld.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-163">6: PacketPrivacy (The properties of the other authentication levels are used, and all the data is encrypted.)</span></span>

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-164">-Authority</span><span class="sxs-lookup"><span data-stu-id="b62d9-164">-Authority</span></span>

<span data-ttu-id="b62d9-165">Hiermee geeft u de instantie op die moet worden gebruikt om de WMI-verbinding te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="b62d9-165">Specifies the authority to use to authenticate the WMI connection.</span></span> <span data-ttu-id="b62d9-166">U kunt standaard Windows NT LAN Manager (NTLM) of Kerberos-verificatie opgeven.</span><span class="sxs-lookup"><span data-stu-id="b62d9-166">You can specify standard Windows NT LAN Manager (NTLM) or Kerberos authentication.</span></span> <span data-ttu-id="b62d9-167">Als u NTLM wilt gebruiken, stelt u de instelling van de instantie in op ntlmdomain: \<DomainName\> , waarbij \<DomainName\> een geldige NTLM-domein naam wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-167">To use NTLM, set the authority setting to ntlmdomain:\<DomainName\>, where \<DomainName\> identifies a valid NTLM domain name.</span></span> <span data-ttu-id="b62d9-168">Als u Kerberos wilt gebruiken, geeft u Kerberos op: \<DomainName\ServerName\> .</span><span class="sxs-lookup"><span data-stu-id="b62d9-168">To use Kerberos, specify kerberos:\<DomainName\ServerName\>.</span></span> <span data-ttu-id="b62d9-169">U kunt de instelling van de instantie niet toevoegen wanneer u verbinding maakt met de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b62d9-169">You cannot include the authority setting when you connect to the local computer.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-170">-Klasse</span><span class="sxs-lookup"><span data-stu-id="b62d9-170">-Class</span></span>

<span data-ttu-id="b62d9-171">Hiermee geeft u de WMI-klasse op die een statische methode bevat die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b62d9-171">Specifies the WMI class that contains a static method to call.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-172">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b62d9-172">-ComputerName</span></span>

<span data-ttu-id="b62d9-173">Geeft als een teken reeks matrix de computers waarop deze cmdlet de opdracht uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b62d9-173">Specifies, as a string array, the computers that this cmdlet runs the command on.</span></span> <span data-ttu-id="b62d9-174">Standaard is dit de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b62d9-174">The default is the local computer.</span></span>

<span data-ttu-id="b62d9-175">Typ de NetBIOS-naam, een IP-adres of een Fully Qualified Domain Name van een of meer computers.</span><span class="sxs-lookup"><span data-stu-id="b62d9-175">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more computers.</span></span> <span data-ttu-id="b62d9-176">Als u de lokale computer wilt opgeven, typt u de naam van de computer, een punt (.) of localhost.</span><span class="sxs-lookup"><span data-stu-id="b62d9-176">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="b62d9-177">Deze para meter is niet gebaseerd op externe communicatie met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="b62d9-177">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="b62d9-178">U kunt de para meter **ComputerName** ook gebruiken als uw computer niet is geconfigureerd om externe opdrachten uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b62d9-178">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-179">-Credential</span><span class="sxs-lookup"><span data-stu-id="b62d9-179">-Credential</span></span>

<span data-ttu-id="b62d9-180">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="b62d9-180">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="b62d9-181">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b62d9-181">The default is the current user.</span></span> <span data-ttu-id="b62d9-182">Typ een gebruikers naam, zoals `User01` , `Domain01\User01` of `User@Contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="b62d9-182">Type a user name, such as `User01`, `Domain01\User01`, or `User@Contoso.com`.</span></span> <span data-ttu-id="b62d9-183">U kunt ook een **PSCredential** -object invoeren, zoals een object dat wordt geretourneerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="b62d9-183">Or, enter a **PSCredential** object, such as an object that is returned by the Get-Credential cmdlet.</span></span> <span data-ttu-id="b62d9-184">Wanneer u een gebruikers naam typt, wordt u gevraagd een wacht woord op te vragen.</span><span class="sxs-lookup"><span data-stu-id="b62d9-184">When you type a user name, you will be prompted for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-185">-EnableAllPrivileges</span><span class="sxs-lookup"><span data-stu-id="b62d9-185">-EnableAllPrivileges</span></span>

<span data-ttu-id="b62d9-186">Hiermee wordt aangegeven dat met deze cmdlet alle bevoegdheden van de huidige gebruiker worden ingeschakeld voordat de opdracht de WMI-aanroep uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b62d9-186">Indicates that this cmdlet enables all the privileges of the current user before the command makes the WMI call.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-187">-Imitatie</span><span class="sxs-lookup"><span data-stu-id="b62d9-187">-Impersonation</span></span>

<span data-ttu-id="b62d9-188">Hiermee geeft u het imitatie niveau op dat moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="b62d9-188">Specifies the impersonation level to use.</span></span> <span data-ttu-id="b62d9-189">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="b62d9-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b62d9-190">0: standaard (leest het lokale REGI ster voor het standaard imitatie niveau, dat meestal is ingesteld op ' 3: impersonate '.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-190">0: Default (Reads the local registry for the default impersonation level, which is usually set to "3: Impersonate".)</span></span>
- <span data-ttu-id="b62d9-191">1: anoniem (Hiermee worden de referenties van de aanroep functie verborgen.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-191">1: Anonymous (Hides the credentials of the caller.)</span></span>
- <span data-ttu-id="b62d9-192">2: identificeren (Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-192">2: Identify (Allows objects to query the credentials of the caller.)</span></span>
- <span data-ttu-id="b62d9-193">3: imiteren (toestaan dat objecten de referenties van de aanroeper gebruiken.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-193">3: Impersonate (Allows objects to use the credentials of the caller.)</span></span>
- <span data-ttu-id="b62d9-194">4: delegeren (toestaan dat objecten andere objecten de referenties van de aanroep functie gebruiken.)</span><span class="sxs-lookup"><span data-stu-id="b62d9-194">4: Delegate (Allows objects to permit other objects to use the credentials of the caller.)</span></span>

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-195">-Input object</span><span class="sxs-lookup"><span data-stu-id="b62d9-195">-InputObject</span></span>

<span data-ttu-id="b62d9-196">Hiermee geeft u een **ManagementObject** -object moet worden gebruikt als invoer.</span><span class="sxs-lookup"><span data-stu-id="b62d9-196">Specifies a **ManagementObject** object to use as input.</span></span> <span data-ttu-id="b62d9-197">Als deze para meter wordt gebruikt, worden alle andere para meters, met uitzonde ring **van de para** meters en **argumenten** , genegeerd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-197">When this parameter is used, all other parameters except the **Flag** and **Argument** parameters are ignored.</span></span>

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-198">-Land instellingen</span><span class="sxs-lookup"><span data-stu-id="b62d9-198">-Locale</span></span>

<span data-ttu-id="b62d9-199">Hiermee geeft u de voorkeurs land instelling voor WMI-objecten.</span><span class="sxs-lookup"><span data-stu-id="b62d9-199">Specifies the preferred locale for WMI objects.</span></span> <span data-ttu-id="b62d9-200">Geef de waarde van de para meter **locale** op als een matrix in de `MS_<LCID>` notatie in de gewenste volg orde.</span><span class="sxs-lookup"><span data-stu-id="b62d9-200">Specify the value of the **Locale** parameter as an array in the `MS_<LCID>` format in the preferred order.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-201">-Name</span><span class="sxs-lookup"><span data-stu-id="b62d9-201">-Name</span></span>

<span data-ttu-id="b62d9-202">Hiermee geeft u de naam op van de methode die moet worden aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b62d9-202">Specifies the name of the method to be invoked.</span></span> <span data-ttu-id="b62d9-203">Deze para meter is verplicht en mag niet null of leeg zijn.</span><span class="sxs-lookup"><span data-stu-id="b62d9-203">This parameter is mandatory and cannot be null or empty.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-204">-Naam ruimte</span><span class="sxs-lookup"><span data-stu-id="b62d9-204">-Namespace</span></span>

<span data-ttu-id="b62d9-205">In combi natie met de para meter **Class** geeft deze para meter de naam ruimte van de WMI-opslag plaats waar de WMI-klasse of het object waarnaar wordt verwezen, zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="b62d9-205">When used with the **Class** parameter, this parameter specifies the WMI repository namespace where the referenced WMI class or object is located.</span></span>

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-206">-Path</span><span class="sxs-lookup"><span data-stu-id="b62d9-206">-Path</span></span>

<span data-ttu-id="b62d9-207">Hiermee wordt het WMI-objectpad van een WMI-klasse opgegeven of het WMI-objectpad van een exemplaar van een WMI-klasse.</span><span class="sxs-lookup"><span data-stu-id="b62d9-207">Specifies the WMI object path of a WMI class, or specifies the WMI object path of an instance of a WMI class.</span></span> <span data-ttu-id="b62d9-208">De klasse of het exemplaar dat u opgeeft, moet de-methode bevatten die is opgegeven in de para meter **name** .</span><span class="sxs-lookup"><span data-stu-id="b62d9-208">The class or the instance that you specify must contain the method that is specified in the **Name** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-209">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b62d9-209">-ThrottleLimit</span></span>

<span data-ttu-id="b62d9-210">Hiermee geeft u een vertragings waarde voor het aantal WMI-bewerkingen dat tegelijkertijd kan worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-210">Specifies a throttle value for the number of WMI operations that can be executed simultaneously.</span></span>
<span data-ttu-id="b62d9-211">Deze para meter wordt gebruikt in combi natie met de para meter **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="b62d9-211">This parameter is used together with the **AsJob** parameter.</span></span> <span data-ttu-id="b62d9-212">De beperkings limiet geldt alleen voor de huidige opdracht, niet voor de sessie of voor de computer.</span><span class="sxs-lookup"><span data-stu-id="b62d9-212">The throttle limit applies only to the current command, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b62d9-213">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b62d9-213">-Confirm</span></span>

<span data-ttu-id="b62d9-214">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b62d9-214">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b62d9-215">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b62d9-215">-WhatIf</span></span>

<span data-ttu-id="b62d9-216">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b62d9-216">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b62d9-217">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-217">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b62d9-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b62d9-218">CommonParameters</span></span>

<span data-ttu-id="b62d9-219">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b62d9-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b62d9-220">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="b62d9-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b62d9-221">INVOER</span><span class="sxs-lookup"><span data-stu-id="b62d9-221">INPUTS</span></span>

### <span data-ttu-id="b62d9-222">Geen</span><span class="sxs-lookup"><span data-stu-id="b62d9-222">None</span></span>

<span data-ttu-id="b62d9-223">Deze cmdlet accepteert geen invoer.</span><span class="sxs-lookup"><span data-stu-id="b62d9-223">This cmdlet does not accept any input.</span></span>

## <span data-ttu-id="b62d9-224">UITVOER</span><span class="sxs-lookup"><span data-stu-id="b62d9-224">OUTPUTS</span></span>

### <span data-ttu-id="b62d9-225">Geen</span><span class="sxs-lookup"><span data-stu-id="b62d9-225">None</span></span>

<span data-ttu-id="b62d9-226">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b62d9-226">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b62d9-227">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="b62d9-227">NOTES</span></span>

## <span data-ttu-id="b62d9-228">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="b62d9-228">RELATED LINKS</span></span>

[<span data-ttu-id="b62d9-229">Get-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b62d9-229">Get-WSManInstance</span></span>](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[<span data-ttu-id="b62d9-230">Invoke-WSManAction</span><span class="sxs-lookup"><span data-stu-id="b62d9-230">Invoke-WSManAction</span></span>](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[<span data-ttu-id="b62d9-231">New-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b62d9-231">New-WSManInstance</span></span>](../Microsoft.WsMan.Management/New-WSManInstance.md)

[<span data-ttu-id="b62d9-232">Remove-WSManInstance</span><span class="sxs-lookup"><span data-stu-id="b62d9-232">Remove-WSManInstance</span></span>](../Microsoft.WsMan.Management/Remove-WSManInstance.md)

[<span data-ttu-id="b62d9-233">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b62d9-233">Get-WmiObject</span></span>](Get-WmiObject.md)

[<span data-ttu-id="b62d9-234">Remove-WmiObject</span><span class="sxs-lookup"><span data-stu-id="b62d9-234">Remove-WmiObject</span></span>](Remove-WmiObject.md)

[<span data-ttu-id="b62d9-235">Set-WmiInstance</span><span class="sxs-lookup"><span data-stu-id="b62d9-235">Set-WmiInstance</span></span>](Set-WmiInstance.md)
