---
title: Werken met WMI
description: Power Shell heeft cmdlets voor het werken met WMI sinds het begin.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 119bb3381ee55c70340da89d1c0690d84b3e70d2
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216128"
---
# <a name="chapter-7---working-with-wmi"></a><span data-ttu-id="97e68-103">Hoofd stuk 7: werken met WMI</span><span class="sxs-lookup"><span data-stu-id="97e68-103">Chapter 7 - Working with WMI</span></span>

## <a name="wmi-and-cim"></a><span data-ttu-id="97e68-104">WMI en CIM</span><span class="sxs-lookup"><span data-stu-id="97e68-104">WMI and CIM</span></span>

<span data-ttu-id="97e68-105">Power shell wordt standaard geleverd met-cmdlets voor het werken met andere technologieën zoals Windows Management Instrumentation (WMI).</span><span class="sxs-lookup"><span data-stu-id="97e68-105">PowerShell ships by default with cmdlets for working with other technologies such as Windows Management Instrumentation (WMI).</span></span> <span data-ttu-id="97e68-106">Er zijn verschillende systeem eigen WMI-cmdlets die beschikbaar zijn in Power shell zonder dat u extra software of modules hoeft te installeren.</span><span class="sxs-lookup"><span data-stu-id="97e68-106">There are several native WMI cmdlets that exist in PowerShell without having to install any additional software or modules.</span></span>

<span data-ttu-id="97e68-107">Power Shell heeft cmdlets voor het werken met WMI sinds het begin.</span><span class="sxs-lookup"><span data-stu-id="97e68-107">PowerShell has had cmdlets for working with WMI since the beginning.</span></span> <span data-ttu-id="97e68-108">`Get-Command` kan worden gebruikt om te bepalen welke WMI-cmdlets bestaan in Power shell.</span><span class="sxs-lookup"><span data-stu-id="97e68-108">`Get-Command` can be used to determine what WMI cmdlets exist in PowerShell.</span></span> <span data-ttu-id="97e68-109">De volgende resultaten zijn afkomstig van mijn Windows 10 Lab-computer waarop Power shell versie 5,1 wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="97e68-109">The following results are from my Windows 10 lab environment computer that is running PowerShell version 5.1.</span></span> <span data-ttu-id="97e68-110">De resultaten kunnen variëren, afhankelijk van de Power shell-versie die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="97e68-110">Your results may differ depending on what PowerShell version you're running.</span></span>

```powershell
Get-Command -Noun WMI*
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-WmiObject                                      3.1.0.0    Microsof...
Cmdlet          Invoke-WmiMethod                                   3.1.0.0    Microsof...
Cmdlet          Register-WmiEvent                                  3.1.0.0    Microsof...
Cmdlet          Remove-WmiObject                                   3.1.0.0    Microsof...
Cmdlet          Set-WmiInstance                                    3.1.0.0    Microsof...
```

<span data-ttu-id="97e68-111">Common Information Model (CIM)-cmdlets zijn geïntroduceerd in Power shell versie 3,0.</span><span class="sxs-lookup"><span data-stu-id="97e68-111">Common Information Model (CIM) cmdlets were introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="97e68-112">De CIM-cmdlets zijn zodanig ontworpen dat ze kunnen worden gebruikt op zowel Windows-als niet-Windows-machines.</span><span class="sxs-lookup"><span data-stu-id="97e68-112">The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines.</span></span> <span data-ttu-id="97e68-113">De WMI-cmdlets zijn afgeschaft, zodat u aanbeveling hebt om de CIM-cmdlets te gebruiken in plaats van de oudere WMI.</span><span class="sxs-lookup"><span data-stu-id="97e68-113">The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.</span></span>

<span data-ttu-id="97e68-114">De CIM-cmdlets zijn allemaal opgenomen in een module.</span><span class="sxs-lookup"><span data-stu-id="97e68-114">The CIM cmdlets are all contained within a module.</span></span> <span data-ttu-id="97e68-115">Als u een lijst met de CIM-cmdlets wilt ophalen, gebruikt u `Get-Command` de para meter **module** , zoals in het volgende voor beeld wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="97e68-115">To obtain a list of the CIM cmdlets, use `Get-Command` with the **Module** parameter as shown in the following example.</span></span>

```powershell
Get-Command -Module CimCmdlets
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Get-CimAssociatedInstance                          1.0.0.0    CimCmdlets
Cmdlet          Get-CimClass                                       1.0.0.0    CimCmdlets
Cmdlet          Get-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          Get-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          Import-BinaryMiLog                                 1.0.0.0    CimCmdlets
Cmdlet          Invoke-CimMethod                                   1.0.0.0    CimCmdlets
Cmdlet          New-CimInstance                                    1.0.0.0    CimCmdlets
Cmdlet          New-CimSession                                     1.0.0.0    CimCmdlets
Cmdlet          New-CimSessionOption                               1.0.0.0    CimCmdlets
Cmdlet          Register-CimIndicationEvent                        1.0.0.0    CimCmdlets
Cmdlet          Remove-CimInstance                                 1.0.0.0    CimCmdlets
Cmdlet          Remove-CimSession                                  1.0.0.0    CimCmdlets
Cmdlet          Set-CimInstance                                    1.0.0.0    CimCmdlets
```

<span data-ttu-id="97e68-116">Met de CIM-cmdlets kunt u nog steeds met WMI werken, dus niet verwarren wanneer iemand de instructie maakt wanneer ik WMI Zoek met de Power shell-cmdlets...</span><span class="sxs-lookup"><span data-stu-id="97e68-116">The CIM cmdlets still allow you to work with WMI so don't be confused when someone makes the statement "When I query WMI with the PowerShell CIM cmdlets..."</span></span>

<span data-ttu-id="97e68-117">Zoals eerder vermeld, is WMI een afzonderlijke technologie van Power shell en gebruikt u alleen de CIM-cmdlets voor toegang tot WMI.</span><span class="sxs-lookup"><span data-stu-id="97e68-117">As I previously mentioned, WMI is a separate technology from PowerShell and you're just using the CIM cmdlets for accessing WMI.</span></span> <span data-ttu-id="97e68-118">Mogelijk vindt u een oud VBScript waarin WMI Query Language (WQL) wordt gebruikt om een query uit te zoeken op WMI, zoals in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="97e68-118">You may find an old VBScript that uses WMI Query Language (WQL) to query WMI such as in the following example.</span></span>

```vb
strComputer = "."
Set objWMIService = GetObject("winmgmts:" _
    & "{impersonationLevel=impersonate}!\\" & strComputer & "\root\cimv2")

Set colBIOS = objWMIService.ExecQuery _
    ("Select * from Win32_BIOS")

For each objBIOS in colBIOS
    Wscript.Echo "Manufacturer: " & objBIOS.Manufacturer
    Wscript.Echo "Name: " & objBIOS.Name
    Wscript.Echo "Serial Number: " & objBIOS.SerialNumber
    Wscript.Echo "SMBIOS Version: " & objBIOS.SMBIOSBIOSVersion
    Wscript.Echo "Version: " & objBIOS.Version
Next
```

<span data-ttu-id="97e68-119">U kunt de WQL-query uit die VBScript halen en deze gebruiken met de cmdlet zonder dat u wijzigingen hoeft aan te brengen `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="97e68-119">You can take the WQL query from that VBScript and use it with the `Get-CimInstance` cmdlet without any modifications.</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_BIOS'
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="97e68-120">Dat is niet hoe ik Norma liter een query uitvoeren op WMI met Power shell.</span><span class="sxs-lookup"><span data-stu-id="97e68-120">That's not how I typically query WMI with PowerShell.</span></span> <span data-ttu-id="97e68-121">Maar dit werkt wel en u kunt eenvoudig bestaande VBScripts migreren naar Power shell.</span><span class="sxs-lookup"><span data-stu-id="97e68-121">But it does work and allows you to easily migrate existing VBScripts to PowerShell.</span></span> <span data-ttu-id="97e68-122">Gebruik de volgende syntaxis wanneer ik een one-line-bewerking start om te zoeken in WMI.</span><span class="sxs-lookup"><span data-stu-id="97e68-122">When I start out writing a one-liner to query WMI, I use the following syntax.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 3810-1995-1654-4615-2295-2755-89
Version           : VRTUAL - 4001628
```

<span data-ttu-id="97e68-123">Als ik alleen het serie nummer wil, kan ik de uitvoer door sluizen naar `Select-Object` en alleen de eigenschap **serialnumber** opgeven.</span><span class="sxs-lookup"><span data-stu-id="97e68-123">If I only want the serial number, I can pipe the output to `Select-Object` and specify only the **SerialNumber** property.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS | Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="97e68-124">Standaard zijn er verschillende eigenschappen die worden opgehaald achter de scènes die nooit worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="97e68-124">By default, there are several properties that are retrieved behind the scenes that are never used.</span></span>
<span data-ttu-id="97e68-125">Het is mogelijk niet erg belang rijk bij het uitvoeren van query's op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="97e68-125">It may not matter much when querying WMI on the local computer.</span></span> <span data-ttu-id="97e68-126">Maar zodra u het uitvoeren van een query op externe computers hebt gestart, is het niet alleen extra verwerkings tijd om die informatie te retour neren, maar ook aanvullende informatie die nodig is om over het netwerk te halen.</span><span class="sxs-lookup"><span data-stu-id="97e68-126">But once you start querying remote computers, it's not only additional processing time to return that information, but also additional unnecessary information to have to pull across the network.</span></span> <span data-ttu-id="97e68-127">`Get-CimInstance` heeft een **eigenschaps** parameter die de opgehaalde informatie beperkt.</span><span class="sxs-lookup"><span data-stu-id="97e68-127">`Get-CimInstance` has a **Property** parameter that limits the information that's retrieved.</span></span> <span data-ttu-id="97e68-128">Hierdoor wordt de query op WMI efficiënter.</span><span class="sxs-lookup"><span data-stu-id="97e68-128">This makes the query to WMI more efficient.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -Property SerialNumber
```

```Output
SerialNumber
------------
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="97e68-129">De vorige resultaten hebben een object geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="97e68-129">The previous results returned an object.</span></span> <span data-ttu-id="97e68-130">Als u een eenvoudige teken reeks wilt retour neren, gebruikt u de para meter **ExpandProperty** .</span><span class="sxs-lookup"><span data-stu-id="97e68-130">To return a simple string, use the **ExpandProperty** parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber |
Select-Object -ExpandProperty SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

<span data-ttu-id="97e68-131">U kunt ook de syntaxis met gestippelde opmaak gebruiken om een eenvoudige teken reeks te retour neren.</span><span class="sxs-lookup"><span data-stu-id="97e68-131">You could also use the dotted style of syntax to return a simple string.</span></span> <span data-ttu-id="97e68-132">Dit elimineert de nood zaak om te pipeen `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="97e68-132">This eliminates the need to pipe to `Select-Object`.</span></span>

```powershell
(Get-CimInstance -ClassName Win32_BIOS -Property SerialNumber).SerialNumber
```

```Output
3810-1995-1654-4615-2295-2755-89
```

## <a name="query-remote-computers-with-the-cim-cmdlets"></a><span data-ttu-id="97e68-133">Query's uitvoeren op externe computers met de CIM-cmdlets</span><span class="sxs-lookup"><span data-stu-id="97e68-133">Query Remote Computers with the CIM cmdlets</span></span>

<span data-ttu-id="97e68-134">Er wordt nog steeds Power shell uitgevoerd als lokale beheerder die een domein gebruiker is.</span><span class="sxs-lookup"><span data-stu-id="97e68-134">I'm still running PowerShell as a local admin who is a domain user.</span></span> <span data-ttu-id="97e68-135">Wanneer ik via de cmdlet gegevens van een externe computer probeer op te vragen `Get-CimInstance` , krijg ik een fout bericht over geweigerde toegang.</span><span class="sxs-lookup"><span data-stu-id="97e68-135">When I try to query information from a remote computer using the `Get-CimInstance` cmdlet, I receive an access denied error message.</span></span>

```powershell
Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
```

```Output
Get-CimInstance : Access is denied.
At line:1 char:1
+ Get-CimInstance -ComputerName dc01 -ClassName Win32_BIOS
+ ``````````````````````````````````````````````````````~~
    + CategoryInfo          : PermissionDenied: (root\cimv2:Win32_BIOS:String) [Get-CimI
   nstance], CimException
    + FullyQualifiedErrorId : HRESULT 0x80070005,Microsoft.Management.Infrastructure.Cim
   Cmdlets.GetCimInstanceCommand
    + PSComputerName        : dc01
```

<span data-ttu-id="97e68-136">Veel mensen hebben problemen met de beveiliging van Power shell, maar de waarheid is dat u precies dezelfde machtigingen hebt in Power shell als in de gebruikers interface.</span><span class="sxs-lookup"><span data-stu-id="97e68-136">Many people have security concerns when it comes to PowerShell, but the truth is you have exactly the same permissions in PowerShell as you do in the GUI.</span></span> <span data-ttu-id="97e68-137">Niet meer en niet minder.</span><span class="sxs-lookup"><span data-stu-id="97e68-137">No more and no less.</span></span> <span data-ttu-id="97e68-138">Het probleem in het vorige voor beeld is dat de gebruiker die Power shell uitvoert, geen rechten heeft om de WMI-gegevens van de DC01-server op te vragen.</span><span class="sxs-lookup"><span data-stu-id="97e68-138">The problem in the previous example is that the user running PowerShell doesn't have rights to query WMI information from the DC01 server.</span></span> <span data-ttu-id="97e68-139">Ik kan Power shell opnieuw starten als een domein beheerder omdat deze geen `Get-CimInstance` para meter **Credential** heeft.</span><span class="sxs-lookup"><span data-stu-id="97e68-139">I could relaunch PowerShell as a domain administrator since `Get-CimInstance` doesn't have a **Credential** parameter.</span></span> <span data-ttu-id="97e68-140">Maar u kunt het beste een vertrouwens relatie geven, omdat vervolgens alles wat ik uit Power shell uitvoer, wordt uitgevoerd als een domein beheerder. Dit kan gevaarlijk zijn uit veiligheids oogpunt, afhankelijk van de situatie.</span><span class="sxs-lookup"><span data-stu-id="97e68-140">But, trust me, that isn't a good idea because then anything that I run from PowerShell would be running as a domain admin. That could be dangerous from a security standpoint depending on the situation.</span></span>

<span data-ttu-id="97e68-141">Met behulp van het principe van minimale bevoegdheden moet ik via de para meter Credential naar mijn domein beheerders account met behulp van de **referentie** parameter, als er een opdracht is.</span><span class="sxs-lookup"><span data-stu-id="97e68-141">Using the principle of least privilege, I elevate to my domain admin account on a per command basis using the **Credential** parameter, if a command has one.</span></span> <span data-ttu-id="97e68-142">`Get-CimInstance` heeft geen **referentie** parameter, zodat de oplossing in dit scenario eerst een **CimSession** maakt.</span><span class="sxs-lookup"><span data-stu-id="97e68-142">`Get-CimInstance` doesn't have a **Credential** parameter so the solution in this scenario is to create a **CimSession** first.</span></span> <span data-ttu-id="97e68-143">Vervolgens gebruikt u de **CimSession** in plaats van een computer naam voor het OPVRAGEN van WMI op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="97e68-143">Then I use the **CimSession** instead of a computer name to query WMI on the remote computer.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName dc01 -Credential (Get-Credential)
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="97e68-144">De CIM-sessie is opgeslagen in een variabele met de naam `$CimSession` .</span><span class="sxs-lookup"><span data-stu-id="97e68-144">The CIM session was stored in a variable named `$CimSession`.</span></span> <span data-ttu-id="97e68-145">U kunt ook de `Get-Credential` cmdlet tussen haakjes opgeven, zodat deze eerst wordt uitgevoerd, waarbij u wordt gevraagd naar alternatieve referenties voordat u de nieuwe sessie maakt.</span><span class="sxs-lookup"><span data-stu-id="97e68-145">Notice that I also specified the `Get-Credential` cmdlet in parentheses so that it executes first, prompting me for alternate credentials, before creating the new session.</span></span> <span data-ttu-id="97e68-146">In dit hoofd stuk ziet u een een efficiëntere manier om alternatieve referenties op te geven, maar is het belang rijk dat u dit basis concept kent voordat u het complex maakt.</span><span class="sxs-lookup"><span data-stu-id="97e68-146">I'll show you another more efficient way to specify alternate credentials later in this chapter, but it's important to understand this basic concept before making it more complicated.</span></span>

<span data-ttu-id="97e68-147">De CIM-sessie die in het vorige voor beeld is gemaakt, kan nu worden gebruikt met de `Get-CimInstance` cmdlet voor het opvragen van de BIOS-gegevens van WMI op de externe computer.</span><span class="sxs-lookup"><span data-stu-id="97e68-147">The CIM session created in the previous example can now be used with the `Get-CimInstance` cmdlet to query the BIOS information from WMI on the remote computer.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01
```

<span data-ttu-id="97e68-148">Er zijn verschillende extra voor delen voor het gebruik van CIM-sessies in plaats van alleen een computer naam op te geven.</span><span class="sxs-lookup"><span data-stu-id="97e68-148">There are several additional benefits to using CIM sessions instead of just specifying a computer name.</span></span> <span data-ttu-id="97e68-149">Wanneer u meerdere query's uitvoert op dezelfde computer, is het gebruik van een CIM-sessie efficiënter dan het gebruik van de computer naam voor elke query.</span><span class="sxs-lookup"><span data-stu-id="97e68-149">When running multiple queries to the same computer, using a CIM session is more efficient than using the computer name for each query.</span></span> <span data-ttu-id="97e68-150">Als u een CIM-sessie maakt, wordt de verbinding slechts eenmaal ingesteld.</span><span class="sxs-lookup"><span data-stu-id="97e68-150">Creating a CIM session only sets up the connection once.</span></span>
<span data-ttu-id="97e68-151">Vervolgens gebruiken meerdere query's diezelfde sessie om informatie op te halen.</span><span class="sxs-lookup"><span data-stu-id="97e68-151">Then, multiple queries use that same session to retrieve information.</span></span> <span data-ttu-id="97e68-152">Als u de computer naam gebruikt, moeten de cmdlets de verbinding met elke afzonderlijke query instellen en afbreken.</span><span class="sxs-lookup"><span data-stu-id="97e68-152">Using the computer name requires the cmdlets to set up and tear down the connection with each individual query.</span></span>

<span data-ttu-id="97e68-153">De `Get-CimInstance` cmdlet maakt standaard gebruik van het WSMan-protocol, wat betekent dat de externe computer Power shell-versie 3,0 of hoger nodig heeft om verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="97e68-153">The `Get-CimInstance` cmdlet uses the WSMan protocol by default, which means the remote computer needs PowerShell version 3.0 or higher to connect.</span></span> <span data-ttu-id="97e68-154">Het is in werkelijkheid niet de Power shell-versie die van belang is, de stack versie.</span><span class="sxs-lookup"><span data-stu-id="97e68-154">It's actually not the PowerShell version that matters, it's the stack version.</span></span> <span data-ttu-id="97e68-155">De stack versie kan worden bepaald met behulp van de `Test-WSMan` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97e68-155">The stack version can be determined using the `Test-WSMan` cmdlet.</span></span>
<span data-ttu-id="97e68-156">Dit moet versie 3,0 zijn.</span><span class="sxs-lookup"><span data-stu-id="97e68-156">It needs to be version 3.0.</span></span> <span data-ttu-id="97e68-157">Dat is de versie die u vindt in Power shell versie 3,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="97e68-157">That's the version you'll find with PowerShell version 3.0 and higher.</span></span>

```powershell
Test-WSMan -ComputerName dc01
```

```Output
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd
ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd
ProductVendor   : Microsoft Corporation
ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 3.0
```

<span data-ttu-id="97e68-158">De oudere WMI-cmdlets gebruiken het DCOM-protocol, dat compatibel is met oudere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="97e68-158">The older WMI cmdlets use the DCOM protocol, which is compatible with older versions of Windows.</span></span> <span data-ttu-id="97e68-159">DCOM wordt doorgaans geblokkeerd door de firewall op nieuwere versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="97e68-159">But DCOM is typically blocked by the firewall on newer versions of Windows.</span></span> <span data-ttu-id="97e68-160">`New-CimSessionOption`Met de cmdlet kunt u een DCOM-protocol verbinding maken voor gebruik met `New-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="97e68-160">The `New-CimSessionOption` cmdlet allows you to create a DCOM protocol connection for use with `New-CimSession`.</span></span> <span data-ttu-id="97e68-161">Op deze manier kan de `Get-CimInstance` cmdlet worden gebruikt om te communiceren met windows 2000 Server-versies als verouderd.</span><span class="sxs-lookup"><span data-stu-id="97e68-161">This allows the `Get-CimInstance` cmdlet to be used to communicate with versions of Windows as old as Windows Server 2000.</span></span> <span data-ttu-id="97e68-162">Dit betekent ook dat Power shell niet is vereist op de externe computer wanneer de `Get-CimInstance` cmdlet wordt gebruikt met een CimSession die is geconfigureerd voor het gebruik van het DCOM-protocol.</span><span class="sxs-lookup"><span data-stu-id="97e68-162">This also means that PowerShell is not required on the remote computer when using the `Get-CimInstance` cmdlet with a CimSession that's configured to use the DCOM protocol.</span></span>

<span data-ttu-id="97e68-163">Maak de DCOM-protocol optie met de `New-CimSessionOption` cmdlet en sla deze op in een variabele.</span><span class="sxs-lookup"><span data-stu-id="97e68-163">Create the DCOM protocol option using the `New-CimSessionOption` cmdlet and store it in a variable.</span></span>

```powershell
$DCOM = New-CimSessionOption -Protocol Dcom
```

<span data-ttu-id="97e68-164">Voor efficiëntie kunt u uw domein beheerder of verhoogde referenties in een variabele opslaan, zodat u deze niet voortdurend hoeft in te voeren voor elke opdracht.</span><span class="sxs-lookup"><span data-stu-id="97e68-164">For efficiency, you can store your domain administrator or elevated credentials in a variable so you don't have to constantly enter them for each command.</span></span>

```powershell
$Cred = Get-Credential
```

```Output
cmdlet Get-Credential at command pipeline position 1
Supply values for the following parameters:
Credential
```

<span data-ttu-id="97e68-165">Ik heb een server met de naam SQL03 waarop Windows Server 2008 (niet-R2) wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="97e68-165">I have a server named SQL03 that runs Windows Server 2008 (non-R2).</span></span> <span data-ttu-id="97e68-166">Het is het nieuwste Windows Server-besturings systeem waarop Power shell niet standaard is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="97e68-166">It's the newest Windows Server operating system that doesn't have PowerShell installed by default.</span></span>

<span data-ttu-id="97e68-167">Een **CimSession** maken voor SQL03 met behulp van het DCOM-protocol.</span><span class="sxs-lookup"><span data-stu-id="97e68-167">Create a **CimSession** to SQL03 using the DCOM protocol.</span></span>

```powershell
$CimSession = New-CimSession -ComputerName sql03 -SessionOption $DCOM -Credential $Cred
```

<span data-ttu-id="97e68-168">In de vorige opdracht is deze keer de variabele opgegeven met de naam `$Cred` voor de para meter **Credential** in plaats van deze hand matig opnieuw in te voeren.</span><span class="sxs-lookup"><span data-stu-id="97e68-168">Notice in the previous command, this time I specified the variable named `$Cred` as the value for the **Credential** parameter instead of having to enter them manually again.</span></span>

<span data-ttu-id="97e68-169">De uitvoer van de query is hetzelfde, ongeacht het gebruikte onderliggende protocol.</span><span class="sxs-lookup"><span data-stu-id="97e68-169">The output of the query is the same regardless of the underlying protocol being used.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="97e68-170">De `Get-CimSession` cmdlet wordt gebruikt om te zien welke **CimSessions** momenteel zijn verbonden en welke protocollen ze gebruiken.</span><span class="sxs-lookup"><span data-stu-id="97e68-170">The `Get-CimSession` cmdlet is used to see what **CimSessions** are currently connected and what protocols they're using.</span></span>

```powershell
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : 80742787-e38e-41b1-a7d7-fa1369cf1402
ComputerName : dc01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : 8fcabd81-43cf-4682-bd53-ccce1e24aecb
ComputerName : sql03
Protocol     : DCOM
```

<span data-ttu-id="97e68-171">Haal de eerder gemaakte **CimSessions** op in een variabele met de naam en sla deze op `$CimSession` .</span><span class="sxs-lookup"><span data-stu-id="97e68-171">Retrieve and store both of the previously created **CimSessions** in a variable named `$CimSession`.</span></span>

```powershell
$CimSession = Get-CimSession
```

<span data-ttu-id="97e68-172">Een query uitvoeren op beide computers met één opdracht, een met het WSMan-protocol en de andere met DCOM.</span><span class="sxs-lookup"><span data-stu-id="97e68-172">Query both of the computers with one command, one using the WSMan protocol and the other one with DCOM.</span></span>

```powershell
Get-CimInstance -CimSession $CimSession -ClassName Win32_BIOS
```

```Output
SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 0986-6980-3916-0512-6608-8243-13
Version           : VRTUAL - 4001628
PSComputerName    : dc01

SMBIOSBIOSVersion : 090006
Manufacturer      : American Megatrends Inc.
Name              : Intel(R) Xeon(R) CPU E3-1505M v5 @ 2.80GHz
SerialNumber      : 7237-7483-8873-8926-7271-5004-86
Version           : VRTUAL - 4001628
PSComputerName    : sql03
```

<span data-ttu-id="97e68-173">Ik heb talloze blog artikelen geschreven over de WMI-en CIM-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="97e68-173">I've written numerous blog articles about the WMI and CIM cmdlets.</span></span> <span data-ttu-id="97e68-174">Een van de meest nuttige voor waarden is over een functie die ik heb gemaakt om automatisch te bepalen of WSMan of DCOM moet worden gebruikt en de CIM-sessie automatisch instellen zonder dat deze hand matig moet worden uitgesteld.</span><span class="sxs-lookup"><span data-stu-id="97e68-174">One of the most useful ones is about a function that I created to automatically determine if WSMan or DCOM should be used and set up the CIM session automatically without having to figure out which one manually.</span></span> <span data-ttu-id="97e68-175">Dit blog artikel heet [Power shell-functie voor het maken van CimSessions op externe computers met terugval naar DCOM][].</span><span class="sxs-lookup"><span data-stu-id="97e68-175">That blog article is titled [PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom][].</span></span>

<span data-ttu-id="97e68-176">Wanneer u klaar bent met de CIM-sessies, moet u deze verwijderen met de `Remove-CimSession` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97e68-176">When you're finished with the CIM sessions, you should remove them with the `Remove-CimSession` cmdlet.</span></span> <span data-ttu-id="97e68-177">Als u alle CIM-sessies wilt verwijderen, hoeft u alleen maar naar de pipe `Get-CimSession` te verplaatsen `Remove-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="97e68-177">To remove all CIM sessions, simply pipe `Get-CimSession` to `Remove-CimSession`.</span></span>

```powershell
Get-CimSession | Remove-CimSession
```

## <a name="summary"></a><span data-ttu-id="97e68-178">Samenvatting</span><span class="sxs-lookup"><span data-stu-id="97e68-178">Summary</span></span>

<span data-ttu-id="97e68-179">In dit hoofd stuk hebt u geleerd hoe u Power shell gebruikt voor het werken met WMI op lokale en externe computers.</span><span class="sxs-lookup"><span data-stu-id="97e68-179">In this chapter, you've learned about using PowerShell to work with WMI on both local and remote computers.</span></span> <span data-ttu-id="97e68-180">U hebt ook geleerd hoe u de CIM-cmdlets gebruikt om te werken met externe computers met het WSMan-of DCOM-protocol.</span><span class="sxs-lookup"><span data-stu-id="97e68-180">You've also learned how to use the CIM cmdlets to work with remote computers with both the WSMan or DCOM protocol.</span></span>

## <a name="review"></a><span data-ttu-id="97e68-181">Beoordelen</span><span class="sxs-lookup"><span data-stu-id="97e68-181">Review</span></span>

1. <span data-ttu-id="97e68-182">Wat is het verschil in de WMI-en CIM-cmdlets?</span><span class="sxs-lookup"><span data-stu-id="97e68-182">What is the difference in the WMI and CIM cmdlets?</span></span>
1. <span data-ttu-id="97e68-183">Welk protocol `Get-CimInstance` gebruikt de cmdlet standaard?</span><span class="sxs-lookup"><span data-stu-id="97e68-183">By default, what protocol does the `Get-CimInstance` cmdlet use?</span></span>
1. <span data-ttu-id="97e68-184">Wat zijn de voor delen van het gebruik van een CIM-sessie in plaats van een computer naam op te geven `Get-CimInstance` ?</span><span class="sxs-lookup"><span data-stu-id="97e68-184">What are some of the benefits of using a CIM session instead of specifying a computer name with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="97e68-185">Hoe kunt u een ander ander protocol dan de standaard instelling opgeven voor gebruik met `Get-CimInstance` ?</span><span class="sxs-lookup"><span data-stu-id="97e68-185">How do you specify an alternate protocol other than the default one for use with `Get-CimInstance`?</span></span>
1. <span data-ttu-id="97e68-186">Hoe sluit of verwijdert u CIM-sessies?</span><span class="sxs-lookup"><span data-stu-id="97e68-186">How do you close or remove CIM sessions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="97e68-187">Aanbevolen documentatie</span><span class="sxs-lookup"><span data-stu-id="97e68-187">Recommended Reading</span></span>

- <span data-ttu-id="97e68-188">[about_WMI][]</span><span class="sxs-lookup"><span data-stu-id="97e68-188">[about_WMI][]</span></span>
- <span data-ttu-id="97e68-189">[about_WMI_Cmdlets][]</span><span class="sxs-lookup"><span data-stu-id="97e68-189">[about_WMI_Cmdlets][]</span></span>
- <span data-ttu-id="97e68-190">[about_WQL][]</span><span class="sxs-lookup"><span data-stu-id="97e68-190">[about_WQL][]</span></span>
- <span data-ttu-id="97e68-191">[CimCmdlets-module][]</span><span class="sxs-lookup"><span data-stu-id="97e68-191">[CimCmdlets Module][]</span></span>
- <span data-ttu-id="97e68-192">[Video: CIM-cmdlets en CIM-sessies gebruiken][]</span><span class="sxs-lookup"><span data-stu-id="97e68-192">[Video: Using CIM Cmdlets and CIM Sessions][]</span></span>

<!-- link references -->
[about_WMI]: /powershell/module/microsoft.powershell.core/about/about_wmi
[about_WMI_Cmdlets]: /powershell/module/microsoft.powershell.core/about/about_wmi_cmdlets
[about_WQL]: /powershell/module/microsoft.powershell.core/about/about_wql
[CimCmdlets-module]: /powershell/module/cimcmdlets/
[CimCmdlets Module]: /powershell/module/cimcmdlets/
[Video: CIM-cmdlets en CIM-sessies gebruiken]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Video: Using CIM Cmdlets and CIM Sessions]: https://mikefrobbins.com/2013/09/12/phillyposh-user-group-meeting-presentation-follow-up-powershell-second-hop-problem-with-cimsessions/
[Power shell-functie voor het maken van CimSessions op externe computers met terugval naar DCOM]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
[PowerShell Function to Create CimSessions to Remote Computers with Fallback to Dcom]: https://mikefrobbins.com/2014/08/28/powershell-function-to-create-cimsessions-to-remote-computers-with-fallback-to-dcom/
