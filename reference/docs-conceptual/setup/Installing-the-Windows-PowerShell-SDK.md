---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De Windows PowerShell SDK installeren
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893535"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="b500a-103">De Windows PowerShell SDK installeren</span><span class="sxs-lookup"><span data-stu-id="b500a-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="b500a-104">Het volgende onderwerp wordt beschreven hoe u de PowerShell SDK installeren op verschillende versies van Windows.</span><span class="sxs-lookup"><span data-stu-id="b500a-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="b500a-105">Windows PowerShell 3.0 installeren SDK voor Windows 8 en WindowsServer 2012</span><span class="sxs-lookup"><span data-stu-id="b500a-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="b500a-106">Windows PowerShell 3.0 wordt automatisch geïnstalleerd met Windows 8 en Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="b500a-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="b500a-107">U kunt bovendien downloaden en de assembly-verwijzingen voor Windows PowerShell 3.0 installeren als onderdeel van de SDK voor Windows 8.</span><span class="sxs-lookup"><span data-stu-id="b500a-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="b500a-108">Deze assembly's kunnen u voor het schrijven van cmdlets en providers host programma's voor Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="b500a-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="b500a-109">Wanneer u de Windows SDK voor Windows 8 installeert, de Windows PowerShell-assembly's worden automatisch geïnstalleerd in de map van de assembly reference in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="b500a-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="b500a-110">Zie voor meer informatie de [site voor het downloaden van Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="b500a-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="b500a-111">Windows PowerShell-codevoorbeelden zijn ook beschikbaar in het midden-ontwikkeling.</span><span class="sxs-lookup"><span data-stu-id="b500a-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="b500a-112">Zie voor meer informatie de pagina van de voorbeeld Desktop code op de [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="b500a-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="b500a-113">Windows PowerShell 3.0 is bovendien achterwaarts compatibel met de SDK van Windows PowerShell 2.0, waaronder een aantal voorbeelden van code.</span><span class="sxs-lookup"><span data-stu-id="b500a-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="b500a-114">Zie hieronder voor meer informatie over het downloaden van de SDK van Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="b500a-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="b500a-115">(Houd er rekening mee de 2.0 codevoorbeelden zijn compatibel met Windows 8 en Windows PowerShell 3.0, niet u Windows PowerShell 2.0 op een Windows 8-platform installeren.)</span><span class="sxs-lookup"><span data-stu-id="b500a-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="b500a-116">Windows PowerShell 3.0 installeren SDK voor Windows 7 en Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b500a-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="b500a-117">Windows 7 en Windows Server 2008 R2 hebben automatisch PowerShell 2.0 is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="b500a-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="b500a-118">Bovendien kunt u PowerShell 3.0 installeren op deze systemen.</span><span class="sxs-lookup"><span data-stu-id="b500a-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="b500a-119">(Zie voor meer informatie, [Windows PowerShell installeren](Installing-Windows-PowerShell.md).).</span><span class="sxs-lookup"><span data-stu-id="b500a-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="b500a-120">Zoals hierboven beschreven, kunt u ook de Windows 8 SDK installeren op Windows 7 en Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="b500a-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="b500a-121">Installatie van Windows PowerShell 2.0 SDK voor Windows 7, Vista, XP, Server 2003 en Server 2008</span><span class="sxs-lookup"><span data-stu-id="b500a-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="b500a-122">De Windows PowerShell 2.0 SDK biedt de referentie-assembly's die nodig zijn voor het schrijven van cmdlets, providers en hosting van toepassingen en C#-voorbeeldcode die kan worden gebruikt als startpunt wanneer u begint met het schrijven van code biedt.</span><span class="sxs-lookup"><span data-stu-id="b500a-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="b500a-123">Zie voor het installeren van deze SDK [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span><span class="sxs-lookup"><span data-stu-id="b500a-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="b500a-124">Assembly-verwijzingen</span><span class="sxs-lookup"><span data-stu-id="b500a-124">Reference assemblies</span></span>

<span data-ttu-id="b500a-125">Assembly-verwijzingen worden standaard geïnstalleerd op de volgende locatie: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="b500a-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="b500a-126">Code die is samengesteld op basis van de Windows PowerShell 2.0-assembly's kan niet worden geladen in de Windows PowerShell 1.0-installaties.</span><span class="sxs-lookup"><span data-stu-id="b500a-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="b500a-127">Code die is samengesteld op basis van de Windows PowerShell 1.0-assembly's kan echter worden geladen in de Windows PowerShell 2.0-installaties.</span><span class="sxs-lookup"><span data-stu-id="b500a-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="b500a-128">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="b500a-128">Samples</span></span>

<span data-ttu-id="b500a-129">Voorbeelden van code worden standaard geïnstalleerd op de volgende locatie: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="b500a-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="b500a-130">De volgende secties bevatten een korte beschrijving van wat elke voorbeeld doet.</span><span class="sxs-lookup"><span data-stu-id="b500a-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="b500a-131">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="b500a-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="b500a-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="b500a-132">GetProcessSample01</span></span>

<span data-ttu-id="b500a-133">Laat zien hoe u een eenvoudige cmdlet die worden opgehaald van alle processen op de lokale computer schrijft.</span><span class="sxs-lookup"><span data-stu-id="b500a-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="b500a-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="b500a-134">GetProcessSample02</span></span>

<span data-ttu-id="b500a-135">Laat zien hoe u parameters toevoegt aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b500a-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="b500a-136">De cmdlet heeft een of meer procesnamen en retourneert de overeenkomende processen.</span><span class="sxs-lookup"><span data-stu-id="b500a-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="b500a-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="b500a-137">GetProcessSample03</span></span>

<span data-ttu-id="b500a-138">Laat zien hoe u parameters die invoer van de pijplijn toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b500a-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="b500a-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="b500a-139">GetProcessSample04</span></span>

<span data-ttu-id="b500a-140">Laat zien hoe afsluitfouten worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="b500a-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="b500a-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="b500a-141">GetProcessSample05</span></span>

<span data-ttu-id="b500a-142">Laat zien hoe u een lijst weergeven met de opgegeven processen.</span><span class="sxs-lookup"><span data-stu-id="b500a-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="b500a-143">ObjectSelecteren</span><span class="sxs-lookup"><span data-stu-id="b500a-143">SelectObject</span></span>

<span data-ttu-id="b500a-144">Laat zien hoe het schrijven van een filter om alleen bepaalde objecten te selecteren.</span><span class="sxs-lookup"><span data-stu-id="b500a-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="b500a-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="b500a-145">SelectString</span></span>

<span data-ttu-id="b500a-146">Laat zien hoe om te zoeken naar bestanden voor de opgegeven patronen.</span><span class="sxs-lookup"><span data-stu-id="b500a-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="b500a-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="b500a-147">StopProcessSample01</span></span>

<span data-ttu-id="b500a-148">Laat zien hoe u voor het implementeren van een *PassThru* parameter en het aanvragen van feedback van gebruikers op aanroepen naar de [shouldprocess wordt overgeslagen](/dotnet/api/system.management.automation.cmdlet.shouldprocess) en [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methoden.</span><span class="sxs-lookup"><span data-stu-id="b500a-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="b500a-149">Gebruikers opgeven de *PassThru* parameter wanneer ze afdwingen dat de cmdlet wilt retourneert een object</span><span class="sxs-lookup"><span data-stu-id="b500a-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="b500a-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="b500a-150">StopProcessSample02</span></span>

<span data-ttu-id="b500a-151">Laat zien hoe u een specifiek proces beëindigen.</span><span class="sxs-lookup"><span data-stu-id="b500a-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="b500a-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="b500a-152">StopProcessSample03</span></span>

<span data-ttu-id="b500a-153">Laat zien hoe om te declareren aliassen voor de parameters en hoe u ondersteuning voor jokertekens.</span><span class="sxs-lookup"><span data-stu-id="b500a-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="b500a-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="b500a-154">StopProcessSample04</span></span>

<span data-ttu-id="b500a-155">Laat zien hoe u declareren parametersets, het object dat de cmdlet wordt gebruikt als invoer en het opgeven van de standaardparameter ingesteld voor het gebruik.</span><span class="sxs-lookup"><span data-stu-id="b500a-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="b500a-156">Voorbeelden van externe toegang</span><span class="sxs-lookup"><span data-stu-id="b500a-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="b500a-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="b500a-157">RemoteRunspace01</span></span>

<span data-ttu-id="b500a-158">Laat zien hoe het maken van een externe runspace die wordt gebruikt om een externe verbinding te maken.</span><span class="sxs-lookup"><span data-stu-id="b500a-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="b500a-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="b500a-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="b500a-160">Laat zien hoe u een van de groep van een externe runspace en hoe u meerdere opdrachten gelijktijdig uitgevoerd met behulp van deze groep.</span><span class="sxs-lookup"><span data-stu-id="b500a-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="b500a-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="b500a-161">Serialization01</span></span>

<span data-ttu-id="b500a-162">Laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat gegevens uit de geselecteerde openbare eigenschappen van deze klasse wordt behouden in de serialisatie/deserialisatie.</span><span class="sxs-lookup"><span data-stu-id="b500a-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="b500a-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="b500a-163">Serialization02</span></span>

<span data-ttu-id="b500a-164">Laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat de informatie van de instantie van deze klasse is behouden in de serialisatie/deserialisatie wanneer de gegevens niet beschikbaar in de openbare eigenschappen van de klasse zijn.</span><span class="sxs-lookup"><span data-stu-id="b500a-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="b500a-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="b500a-165">Serialization03</span></span>

<span data-ttu-id="b500a-166">Laat zien hoe om te kijken naar een bestaande .NET-klasse en zorg ervoor dat de exemplaren van deze klasse en afgeleide klassen worden gedeserialiseerd (gereactiveerd) in live .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="b500a-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="b500a-167">Voorbeelden van gebeurtenis</span><span class="sxs-lookup"><span data-stu-id="b500a-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="b500a-168">Event01</span><span class="sxs-lookup"><span data-stu-id="b500a-168">Event01</span></span>

<span data-ttu-id="b500a-169">Laat zien hoe u een cmdlet voor gebeurtenisregistratie maakt die is afgeleid van ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="b500a-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="b500a-170">Event02</span><span class="sxs-lookup"><span data-stu-id="b500a-170">Event02</span></span>

<span data-ttu-id="b500a-171">Laat zien hoe laat zien hoe u voor het ontvangen van meldingen van Windows PowerShell-gebeurtenissen die worden gegenereerd op externe computers aan.</span><span class="sxs-lookup"><span data-stu-id="b500a-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="b500a-172">Hierbij de PSEventReceived gebeurtenis die toegankelijk is via de [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) klasse.</span><span class="sxs-lookup"><span data-stu-id="b500a-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="b500a-173">Voorbeelden van de toepassing die als host fungeert</span><span class="sxs-lookup"><span data-stu-id="b500a-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="b500a-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="b500a-174">Runspace01</span></span>

<span data-ttu-id="b500a-175">Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchroon.</span><span class="sxs-lookup"><span data-stu-id="b500a-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="b500a-176">De [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert [proces](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objecten voor elk proces dat wordt uitgevoerd op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="b500a-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="b500a-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="b500a-177">Runspace02</span></span>

<span data-ttu-id="b500a-178">Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse om uit te voeren de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) en [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchroon.</span><span class="sxs-lookup"><span data-stu-id="b500a-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="b500a-179">De [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet retourneert [proces](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objecten voor elk proces dat wordt uitgevoerd op de lokale computer en de `Sort-Object` sorteert de objecten op basis van hun [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b500a-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="b500a-180">De resultaten van deze opdrachten wordt weergegeven met behulp van een [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) besturingselement.</span><span class="sxs-lookup"><span data-stu-id="b500a-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="b500a-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="b500a-181">Runspace03</span></span>

<span data-ttu-id="b500a-182">Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse voor synchrone uitvoering van een script, en hoe u voor het afhandelen van niet-afsluitfouten.</span><span class="sxs-lookup"><span data-stu-id="b500a-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="b500a-183">Het script een lijst van procesnamen ontvangt en haalt vervolgens deze processen.</span><span class="sxs-lookup"><span data-stu-id="b500a-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="b500a-184">De resultaten van het script, met inbegrip van eventuele niet-afsluitfouten fouten die zijn gegenereerd wanneer het script is uitgevoerd, worden weergegeven in een consolevenster weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b500a-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="b500a-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="b500a-185">Runspace04</span></span>

<span data-ttu-id="b500a-186">Laat zien hoe u de [PowerShell](/dotnet/api/system.management.automation.powershell) klasse voor het uitvoeren van opdrachten, en hoe u afsluitende catch-fouten die worden gegenereerd wanneer de opdrachten uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b500a-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="b500a-187">Twee opdrachten worden uitgevoerd en de laatste opdracht wordt een parameterargument dat is niet geldig doorgegeven.</span><span class="sxs-lookup"><span data-stu-id="b500a-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="b500a-188">Als gevolg hiervan geen objecten worden geretourneerd en wordt er een afsluitfout wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b500a-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="b500a-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="b500a-189">Runspace05</span></span>

<span data-ttu-id="b500a-190">Laat zien hoe u een module toevoegen aan een [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object zodat de cmdlet van de module beschikbaar is wanneer de runspace wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="b500a-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="b500a-191">De module biedt u een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample01 voorbeeld](https://technet.microsoft.com/library/ff602028.aspx)) die synchroon wordt uitgevoerd met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span><span class="sxs-lookup"><span data-stu-id="b500a-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="b500a-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="b500a-192">Runspace06</span></span>

<span data-ttu-id="b500a-193">Laat zien hoe een module toevoegt een [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object zodat de module wordt geladen wanneer de runspace wordt geopend.</span><span class="sxs-lookup"><span data-stu-id="b500a-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="b500a-194">De module biedt een cmdlet Get-Proc (gedefinieerd door de [GetProcessSample02 voorbeeld](https://technet.microsoft.com/library/ff602027.aspx)) die synchroon wordt uitgevoerd met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span><span class="sxs-lookup"><span data-stu-id="b500a-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="b500a-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="b500a-195">Runspace07</span></span>

<span data-ttu-id="b500a-196">Laat zien hoe u een runspace maken en vervolgens die runspace twee cmdlets synchroon worden uitgevoerd met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span><span class="sxs-lookup"><span data-stu-id="b500a-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="b500a-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="b500a-197">Runspace08</span></span>

<span data-ttu-id="b500a-198">Laat zien hoe u opdrachten en argumenten toevoegen aan de pijplijn met een [PowerShell](/dotnet/api/system.management.automation.powershell) object en hoe u de opdrachten synchroon worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b500a-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="b500a-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="b500a-199">Runspace09</span></span>

<span data-ttu-id="b500a-200">Laat zien hoe u een script toevoegen aan de pijplijn met een [PowerShell](/dotnet/api/system.management.automation.powershell) object en hoe u kunt het script asynchroon uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b500a-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="b500a-201">Gebeurtenissen worden gebruikt voor het afhandelen van de uitvoer van het script.</span><span class="sxs-lookup"><span data-stu-id="b500a-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="b500a-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="b500a-202">Runspace10</span></span>

<span data-ttu-id="b500a-203">Laat zien hoe u een initiële standaard sessiestatus gebruikt, maakt het toevoegen van een cmdlet voor de [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), over het maken van een runspace die gebruikmaakt van de sessiestatus van de eerste en hoe u de opdracht uitvoert met behulp van een [PowerShell](/dotnet/api/system.management.automation.powershell)object.</span><span class="sxs-lookup"><span data-stu-id="b500a-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="b500a-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="b500a-204">Runspace11</span></span>

<span data-ttu-id="b500a-205">Laat zien hoe u de [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) klasse te maken van een proxy-opdracht die een bestaande cmdlet-aanroepen, maar Hiermee beperkt u de set beschikbare parameters.</span><span class="sxs-lookup"><span data-stu-id="b500a-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="b500a-206">De proxy-opdracht wordt vervolgens toegevoegd aan een eerste sessiestatus die wordt gebruikt voor het maken van een beperkte runspace.</span><span class="sxs-lookup"><span data-stu-id="b500a-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="b500a-207">Dit betekent dat de gebruiker toegang heeft tot de functionaliteit van de cmdlet alleen via de proxy-opdracht.</span><span class="sxs-lookup"><span data-stu-id="b500a-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="b500a-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="b500a-208">PowerShell01</span></span>

<span data-ttu-id="b500a-209">Laat zien hoe u het maken van een beperkte runspace met een [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span><span class="sxs-lookup"><span data-stu-id="b500a-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="b500a-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="b500a-210">PowerShell02</span></span>

<span data-ttu-id="b500a-211">Ziet u hoe u een pool runspace gelijktijdig meerdere opdrachten uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b500a-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="b500a-212">Voorbeelden van host</span><span class="sxs-lookup"><span data-stu-id="b500a-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="b500a-213">Host01</span><span class="sxs-lookup"><span data-stu-id="b500a-213">Host01</span></span>

<span data-ttu-id="b500a-214">Laat zien hoe u een hosttoepassing die gebruikmaakt van een aangepaste host implementeert.</span><span class="sxs-lookup"><span data-stu-id="b500a-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="b500a-215">In dit voorbeeld wordt een runspace gemaakt die gebruikmaakt van de aangepaste host, en vervolgens de [PowerShell](/dotnet/api/system.management.automation.powershell) API wordt gebruikt om uit te voeren een script waarmee "afsluiten" wordt aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="b500a-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="b500a-216">De hosttoepassing wordt vervolgens kijkt naar de uitvoer van het script en de resultaten het tekstvenster.</span><span class="sxs-lookup"><span data-stu-id="b500a-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="b500a-217">Host02</span><span class="sxs-lookup"><span data-stu-id="b500a-217">Host02</span></span>

<span data-ttu-id="b500a-218">Laat zien hoe het schrijven van een hosttoepassing die gebruikmaakt van de Windows PowerShell-runtime, samen met een aangepaste host-implementatie.</span><span class="sxs-lookup"><span data-stu-id="b500a-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="b500a-219">De hosttoepassing wordt de cultuur van de host ingesteld op Duits, wordt uitgevoerd de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -cmdlet en geeft de resultaten op als u ze ziet met behulp van pwrsh.exe en vervolgens af te drukken om de huidige datum en tijd in het Duits.</span><span class="sxs-lookup"><span data-stu-id="b500a-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="b500a-220">Host03</span><span class="sxs-lookup"><span data-stu-id="b500a-220">Host03</span></span>

<span data-ttu-id="b500a-221">Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="b500a-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="b500a-222">Host04</span><span class="sxs-lookup"><span data-stu-id="b500a-222">Host04</span></span>

<span data-ttu-id="b500a-223">Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="b500a-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="b500a-224">Weergave prompts die toestaan dat de gebruiker om op te geven meerdere mogelijkheden biedt ook ondersteuning voor deze hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="b500a-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="b500a-225">Host05</span><span class="sxs-lookup"><span data-stu-id="b500a-225">Host05</span></span>

<span data-ttu-id="b500a-226">Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="b500a-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="b500a-227">Deze hosttoepassing biedt ook ondersteuning voor aanroepen naar externe computers met behulp van de [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) en [afsluiten PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b500a-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="b500a-228">Host06</span><span class="sxs-lookup"><span data-stu-id="b500a-228">Host06</span></span>

<span data-ttu-id="b500a-229">Laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="b500a-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="b500a-230">Dit voorbeeld wordt bovendien de Tokenizer-API's gebruikt om op te geven van de kleur van de tekst die is ingevoerd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b500a-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="b500a-231">Voorbeelden van provider</span><span class="sxs-lookup"><span data-stu-id="b500a-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="b500a-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="b500a-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="b500a-233">Laat zien hoe u een providerklasse die is afgeleid rechtstreeks van declareert de [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) klasse.</span><span class="sxs-lookup"><span data-stu-id="b500a-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="b500a-234">Het is hier opgenomen voor de volledigheid.</span><span class="sxs-lookup"><span data-stu-id="b500a-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="b500a-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="b500a-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="b500a-236">Laat zien hoe u overschrijven de [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) en [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methoden voor de ondersteuning van aanroepen naar de `New-PSDrive` en `Remove-PSDrive` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b500a-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="b500a-237">De providerklasse in dit voorbeeld is afgeleid van de [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) klasse.</span><span class="sxs-lookup"><span data-stu-id="b500a-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="b500a-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="b500a-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="b500a-239">Laat zien hoe u overschrijven de [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) en [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methoden voor de ondersteuning van aanroepen naar de `Get-Item` en `Set-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b500a-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="b500a-240">De providerklasse in dit voorbeeld is afgeleid van de [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasse.</span><span class="sxs-lookup"><span data-stu-id="b500a-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="b500a-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="b500a-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="b500a-242">Laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Copy-Item`, `Get-ChildItem`, `New-Item`, en `Remove-Item` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b500a-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="b500a-243">Deze methoden moeten worden uitgevoerd wanneer het gegevensarchief bevat items die containers zijn.</span><span class="sxs-lookup"><span data-stu-id="b500a-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="b500a-244">Een container is een groep van onderliggende items onder een gemeenschappelijk bovenliggend item.</span><span class="sxs-lookup"><span data-stu-id="b500a-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="b500a-245">De providerklasse in dit voorbeeld is afgeleid van de [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klasse.</span><span class="sxs-lookup"><span data-stu-id="b500a-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="b500a-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="b500a-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="b500a-247">Laat zien hoe u containermethoden ter ondersteuning van aanroepen naar overschrijven de `Move-Item` en `Join-Path` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b500a-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="b500a-248">Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft om items in een container te verplaatsen en als het gegevensarchief geneste containers bevat.</span><span class="sxs-lookup"><span data-stu-id="b500a-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="b500a-249">De providerklasse in dit voorbeeld is afgeleid van de [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasse.</span><span class="sxs-lookup"><span data-stu-id="b500a-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="b500a-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="b500a-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="b500a-251">Laat zien hoe u inhoud methoden ter ondersteuning van aanroepen naar overschrijven de `Clear-Content`, `Get-Content`, en `Set-Content` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b500a-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="b500a-252">Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief.</span><span class="sxs-lookup"><span data-stu-id="b500a-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="b500a-253">De providerklasse in dit voorbeeld is afgeleid van de [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klasse en implementeert de [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span><span class="sxs-lookup"><span data-stu-id="b500a-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>