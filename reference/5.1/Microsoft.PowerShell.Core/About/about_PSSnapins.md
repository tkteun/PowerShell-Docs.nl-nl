---
description: Hierin worden de Windows Power shell-modules beschreven en wordt uitgelegd hoe u deze kunt gebruiken en beheren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252595"
---
# <a name="about-pssnapins"></a><span data-ttu-id="eba76-104">Over PSSnapins</span><span class="sxs-lookup"><span data-stu-id="eba76-104">About PSSnapins</span></span>

## <a name="short-description"></a><span data-ttu-id="eba76-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="eba76-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="eba76-106">Hierin worden de Windows Power shell-modules beschreven en wordt uitgelegd hoe u deze kunt gebruiken en beheren.</span><span class="sxs-lookup"><span data-stu-id="eba76-106">Describes  Windows PowerShell snap-ins and shows how to use and manage them.</span></span>

## <a name="long-description"></a><span data-ttu-id="eba76-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="eba76-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="eba76-108">Een Windows Power shell-module is een Microsoft .NET Framework-assembly die Windows Power shell-providers en- \/ cmdlets bevat.</span><span class="sxs-lookup"><span data-stu-id="eba76-108">A Windows PowerShell snap-in is a Microsoft .NET Framework assembly that contains Windows PowerShell providers and\/or cmdlets.</span></span> <span data-ttu-id="eba76-109">Windows Power shell bevat een set basis modules, maar u kunt de kracht en waarde van Windows Power shell uitbreiden door modules toe te voegen die providers en cmdlets bevatten die u maakt of van anderen haalt.</span><span class="sxs-lookup"><span data-stu-id="eba76-109">Windows PowerShell includes a set of basic snap-ins, but you can extend the power and value of Windows PowerShell by adding snap-ins that contain providers and cmdlets that you create or get from others.</span></span>

<span data-ttu-id="eba76-110">Wanneer u een module toevoegt, zijn de cmdlets en providers die deze bevat, onmiddellijk beschikbaar voor gebruik in de huidige sessie, maar de wijziging is alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eba76-110">When you add a snap-in, the cmdlets and providers that it contains are immediately available for use in the current session, but the change affects only the current session.</span></span>

<span data-ttu-id="eba76-111">Als u de module wilt toevoegen aan alle toekomstige sessies, slaat u deze op in uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="eba76-111">To add the snap-in to all future sessions, save it in your Windows PowerShell profile.</span></span> <span data-ttu-id="eba76-112">U kunt ook de cmdlet Export-Console gebruiken om de namen van modules op te slaan in een console bestand en deze vervolgens te gebruiken in toekomstige sessies.</span><span class="sxs-lookup"><span data-stu-id="eba76-112">You can also use the Export-Console cmdlet to save the snap-in names to a console file and then use it in future sessions.</span></span> <span data-ttu-id="eba76-113">U kunt zelfs meerdere console bestanden opslaan, elk met een andere set modules.</span><span class="sxs-lookup"><span data-stu-id="eba76-113">You can even save multiple console files, each with a different set of snap-ins.</span></span>

<span data-ttu-id="eba76-114">Opmerking: Windows Power shell-modules (PSSnapins) zijn beschikbaar voor gebruik in Windows Power Shell 3,0 en Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="eba76-114">NOTE: Windows PowerShell snap-ins (PSSnapins) are available for use in Windows PowerShell 3.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="eba76-115">Ze zijn mogelijk gewijzigd of niet beschikbaar in latere versies.</span><span class="sxs-lookup"><span data-stu-id="eba76-115">They might be altered or unavailable in subsequent versions.</span></span> <span data-ttu-id="eba76-116">Gebruik modules om Windows Power shell-cmdlets en-providers te verpakken.</span><span class="sxs-lookup"><span data-stu-id="eba76-116">To package Windows PowerShell cmdlets and providers, use modules.</span></span> <span data-ttu-id="eba76-117">Zie [een Windows Power shell-module schrijven](/powershell/scripting/developer/module/writing-a-windows-powershell-module)voor meer informatie over het maken van modules en het omzetten van modules in modules.</span><span class="sxs-lookup"><span data-stu-id="eba76-117">For information about creating modules and converting snap-ins to modules, see [Writing a Windows PowerShell Module](/powershell/scripting/developer/module/writing-a-windows-powershell-module).</span></span>

### <a name="finding-snap-ins"></a><span data-ttu-id="eba76-118">MODULES ZOEKEN</span><span class="sxs-lookup"><span data-stu-id="eba76-118">FINDING SNAP-INS</span></span>

<span data-ttu-id="eba76-119">Als u een lijst wilt weer geven van de Windows Power shell-modules op uw computer, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-119">To get a list of the  Windows PowerShell snap-ins on your computer, type:</span></span>

```powershell
Get-PSSnapin
```

<span data-ttu-id="eba76-120">Als u de module voor elke Windows Power shell-provider wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-120">To get the snap-in for each  Windows PowerShell provider, type:</span></span>

```powershell
Get-PSProvider | Format-List name, pssnapin
```

<span data-ttu-id="eba76-121">Als u een lijst met de cmdlets in een Windows Power shell-module wilt ophalen, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-121">To get a list of the cmdlets in a  Windows PowerShell snap-in, type:</span></span>

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a><span data-ttu-id="eba76-122">EEN MODULE INSTALLEREN</span><span class="sxs-lookup"><span data-stu-id="eba76-122">INSTALLING A SNAP-IN</span></span>

<span data-ttu-id="eba76-123">De ingebouwde modules worden geregistreerd in het systeem en toegevoegd aan de standaard sessie wanneer u Windows Power shell start.</span><span class="sxs-lookup"><span data-stu-id="eba76-123">The built-in snap-ins are registered in the system and added to the default session when you start Windows PowerShell.</span></span> <span data-ttu-id="eba76-124">U moet echter de modules registreren die u maakt of van anderen verkrijgt en vervolgens de modules aan uw sessie toevoegen.</span><span class="sxs-lookup"><span data-stu-id="eba76-124">However, you have to register snap-ins that you create or obtain from others and then add the snap-ins to your session.</span></span>

### <a name="registering-a-snap-in"></a><span data-ttu-id="eba76-125">EEN MODULE REGISTREREN</span><span class="sxs-lookup"><span data-stu-id="eba76-125">REGISTERING A SNAP-IN</span></span>

<span data-ttu-id="eba76-126">Een Windows Power shell-module is een programma dat is geschreven in een .NET Framework taal die in een. dll-bestand is gecompileerd.</span><span class="sxs-lookup"><span data-stu-id="eba76-126">A Windows PowerShell snap-in is a program written in a .NET Framework language that is compiled into a .dll file.</span></span> <span data-ttu-id="eba76-127">Als u de providers en cmdlets in een module wilt gebruiken, moet u eerst de module registreren (Voeg deze toe aan het REGI ster).</span><span class="sxs-lookup"><span data-stu-id="eba76-127">To use the providers and cmdlets in a snap-in, you must first register the snap-in (add it to the registry).</span></span>

<span data-ttu-id="eba76-128">De meeste modules bevatten een installatie programma (een exe-of MSI-bestand) dat het dll-bestand voor u registreert.</span><span class="sxs-lookup"><span data-stu-id="eba76-128">Most snap-ins include an installation program (an .exe or .msi file) that registers the .dll file for you.</span></span> <span data-ttu-id="eba76-129">Als u echter een module ontvangt als een dll-bestand, kunt u deze registreren op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="eba76-129">However, if you receive a snap-in as a .dll file, you can register it on your system.</span></span> <span data-ttu-id="eba76-130">Zie [cmdlets, providers en hosttoepassingen registreren](https://go.microsoft.com/fwlink/?LinkID=143619) in de MSDN-bibliotheek voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eba76-130">For more information, see [How to Register Cmdlets, Providers, and Host Applications](https://go.microsoft.com/fwlink/?LinkID=143619) in the MSDN library.</span></span>

<span data-ttu-id="eba76-131">Als u alle geregistreerde modules op uw systeem wilt ophalen of als u wilt controleren of een module is geregistreerd, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-131">To get all the registered snap-ins on your system or to verify that a snap-in is registered, type:</span></span>

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a><span data-ttu-id="eba76-132">DE MODULE TOEVOEGEN AAN DE HUIDIGE SESSIE</span><span class="sxs-lookup"><span data-stu-id="eba76-132">ADDING THE SNAP-IN TO THE CURRENT SESSION</span></span>

<span data-ttu-id="eba76-133">Gebruik de cmdlet Add-PsSnapin om een geregistreerde module toe te voegen aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="eba76-133">To add a registered snap-in to the current session, use the Add-PsSnapin cmdlet.</span></span> <span data-ttu-id="eba76-134">Als u bijvoorbeeld de module Microsoft SQL Server wilt toevoegen aan de sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-134">For example, to add the Microsoft SQL Server snap-in to the session, type:</span></span>

```powershell
Add-PSSnapin sql
```

<span data-ttu-id="eba76-135">Nadat de opdracht is voltooid, zijn de providers en cmdlets in de module beschikbaar in de sessie.</span><span class="sxs-lookup"><span data-stu-id="eba76-135">After the command is completed, the providers and cmdlets in the snap-in are available in the session.</span></span> <span data-ttu-id="eba76-136">Ze zijn echter alleen beschikbaar in de huidige sessie, tenzij u ze opslaat.</span><span class="sxs-lookup"><span data-stu-id="eba76-136">However, they are available only in the current session unless you save them.</span></span>

### <a name="saving-the-snap-ins"></a><span data-ttu-id="eba76-137">DE MODULES OPSLAAN</span><span class="sxs-lookup"><span data-stu-id="eba76-137">SAVING THE SNAP-INS</span></span>

<span data-ttu-id="eba76-138">Als u een module in toekomstige Windows Power shell-sessies wilt gebruiken, voegt u de opdracht Add-PsSnapin toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="eba76-138">To use a snap-in in future Windows PowerShell sessions, add the Add-PsSnapin command to your Windows PowerShell profile.</span></span> <span data-ttu-id="eba76-139">Of Exporteer de module namen naar een console bestand.</span><span class="sxs-lookup"><span data-stu-id="eba76-139">Or, export the snap-in names to a console file.</span></span>

<span data-ttu-id="eba76-140">Als u de Add-PSSnapin opdracht aan uw profiel toevoegt, is deze beschikbaar in alle toekomstige Windows Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="eba76-140">If you add the Add-PSSnapin command to your profile, it is available in all future Windows PowerShell sessions.</span></span> <span data-ttu-id="eba76-141">Als u de namen van de modules in uw sessie exporteert, kunt u het export bestand alleen gebruiken als u de modules nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="eba76-141">If you export the names of the snap-ins in your session, you can use the export file only when you need the snap-ins.</span></span>

<span data-ttu-id="eba76-142">Als u de Add-PsSnapin opdracht wilt toevoegen aan uw Windows Power shell-profiel, opent u uw profiel, plakt of typt u de opdracht en slaat u het profiel op.</span><span class="sxs-lookup"><span data-stu-id="eba76-142">To add the Add-PsSnapin command to your Windows PowerShell profile, open your profile, paste or type the command, and then save the profile.</span></span> <span data-ttu-id="eba76-143">Zie about_Profiles voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eba76-143">For more information, see about_Profiles.</span></span>

<span data-ttu-id="eba76-144">Gebruik de cmdlet Export-Console om de modules op te slaan vanuit een sessie in het console bestand (. psc1).</span><span class="sxs-lookup"><span data-stu-id="eba76-144">To save the snap-ins from a session in console file (.psc1), use the Export-Console cmdlet.</span></span> <span data-ttu-id="eba76-145">Als u bijvoorbeeld de modules in de huidige sessie configuratie wilt opslaan in het NewConsole. psc1-bestand in de huidige map, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-145">For example, to save the snap-ins in the current session configuration to the NewConsole.psc1 file in the current directory, type:</span></span>

```powershell
Export-Console NewConsole
```

<span data-ttu-id="eba76-146">Zie voor meer informatie exporteren-console.</span><span class="sxs-lookup"><span data-stu-id="eba76-146">For more information, see Export-Console.</span></span>

### <a name="opening-windows-powershell-with-a-console-file"></a><span data-ttu-id="eba76-147">WINDOWS POWER SHELL OPENEN MET EEN CONSOLE BESTAND</span><span class="sxs-lookup"><span data-stu-id="eba76-147">OPENING WINDOWS POWERSHELL WITH A CONSOLE FILE</span></span>

<span data-ttu-id="eba76-148">Als u een console bestand wilt gebruiken dat de module bevat, start u Windows Power shell (PowerShell.exe) vanaf de opdracht prompt in Cmd.exe of in een andere Windows Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="eba76-148">To use a console file that includes the snap-in, start Windows PowerShell (PowerShell.exe) from the command prompt in Cmd.exe or in another Windows PowerShell session.</span></span> <span data-ttu-id="eba76-149">Gebruik de para meter PsConsoleFile om het console bestand op te geven dat de module bevat.</span><span class="sxs-lookup"><span data-stu-id="eba76-149">Use the PsConsoleFile parameter to specify the console file that includes the snap-in.</span></span> <span data-ttu-id="eba76-150">Met de volgende opdracht wordt bijvoorbeeld Windows Power shell gestart met het console bestand NewConsole. psc1:</span><span class="sxs-lookup"><span data-stu-id="eba76-150">For example, the following command starts Windows PowerShell with the NewConsole.psc1 console file:</span></span>

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

<span data-ttu-id="eba76-151">De providers en cmdlets in de module zijn nu beschikbaar voor gebruik in de sessie.</span><span class="sxs-lookup"><span data-stu-id="eba76-151">The providers and cmdlets in the snapin are now available for use in the session.</span></span>

### <a name="removing-a-snap-in"></a><span data-ttu-id="eba76-152">EEN MODULE VERWIJDEREN</span><span class="sxs-lookup"><span data-stu-id="eba76-152">REMOVING A SNAP-IN</span></span>

<span data-ttu-id="eba76-153">Als u een Windows Power shell-module uit de huidige sessie wilt verwijderen, gebruikt u de cmdlet Remove-PsSnapin.</span><span class="sxs-lookup"><span data-stu-id="eba76-153">To remove a Windows PowerShell snap-in from the current session, use the Remove-PsSnapin cmdlet.</span></span> <span data-ttu-id="eba76-154">Als u bijvoorbeeld de module SQL Server wilt verwijderen uit de huidige sessie, typt u:</span><span class="sxs-lookup"><span data-stu-id="eba76-154">For example, to remove the SQL Server snap-in from the current session, type:</span></span>

```powershell
Remove-PSSnapin sql
```

<span data-ttu-id="eba76-155">Met deze cmdlet wordt de module uit de sessie verwijderd.</span><span class="sxs-lookup"><span data-stu-id="eba76-155">This cmdlet removes the snap-in from the session.</span></span> <span data-ttu-id="eba76-156">De module is nog geladen, maar de providers en cmdlets die worden ondersteund, zijn niet meer beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="eba76-156">The snap-in is still loaded, but the providers and cmdlets that it supports are no longer available.</span></span>

### <a name="built-in-commands"></a><span data-ttu-id="eba76-157">INGEBOUWDE OPDRACHTEN</span><span class="sxs-lookup"><span data-stu-id="eba76-157">BUILT-IN COMMANDS</span></span>

<span data-ttu-id="eba76-158">In Windows Power Shell 2,0 en in oudere host-Program ma's in Windows Power Shell 3,0 en hoger, worden de ingebouwde opdrachten die met Windows Power shell zijn geïnstalleerd, verpakt in modules die automatisch aan elke Windows Power shell-sessie worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="eba76-158">In Windows PowerShell 2.0 and in older-style host programs in Windows PowerShell 3.0 and later, the built-in commands that are installed with Windows PowerShell are packaged in snap-ins that are added automatically to every Windows PowerShell session.</span></span>

<span data-ttu-id="eba76-159">Vanaf Windows Power Shell 3,0, in nieuwere-stijl hostgroepen, waarmee sessies worden gestart met behulp van de methode InitialSessionState. CreateDefault2. de ingebouwde opdrachten zijn verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="eba76-159">Beginning in Windows PowerShell 3.0, in newer-style host programs -- those that start sessions by using the InitialSessionState.CreateDefault2 method -- the built-in commands are packaged in modules.</span></span> <span data-ttu-id="eba76-160">De uitzonde ring is micro soft. Power shell. core, dat altijd als een module wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="eba76-160">The exception is Microsoft.PowerShell.Core, which always appears as a snap-in.</span></span> <span data-ttu-id="eba76-161">De kern module is standaard opgenomen in elke sessie.</span><span class="sxs-lookup"><span data-stu-id="eba76-161">The Core snap-in is included in every session by default.</span></span> <span data-ttu-id="eba76-162">De ingebouwde modules worden automatisch geladen bij het eerste gebruik.</span><span class="sxs-lookup"><span data-stu-id="eba76-162">The built-in modules are loaded automatically on first-use.</span></span>

<span data-ttu-id="eba76-163">Opmerking: externe sessies, met inbegrip van sessies die zijn gestart met behulp van de cmdlet New-PSSession, zijn oudere sessies waarin de ingebouwde opdrachten zijn verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="eba76-163">NOTE: Remote sessions, including sessions that are started by using the New-PSSession cmdlet, are older-style sessions in which the built-in commands are packaged in snap-ins.</span></span>

<span data-ttu-id="eba76-164">De volgende modules (of modules) worden geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="eba76-164">The following snap-ins (or modules) are installed with Windows PowerShell.</span></span>

- <span data-ttu-id="eba76-165">Micro soft. Power shell. core: bevat providers en cmdlets die worden gebruikt voor het beheren van de basis functies van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="eba76-165">Microsoft.PowerShell.Core - Contains providers and cmdlets used to manage the basic features of Windows PowerShell.</span></span> <span data-ttu-id="eba76-166">Het bevat het bestands systeem, het REGI ster, de alias, de omgeving, de functie en de variabele providers en de basis-cmdlets zoals Get-Help, Get-Command en Get-History.</span><span class="sxs-lookup"><span data-stu-id="eba76-166">It includes the FileSystem, Registry, Alias, Environment, Function, and Variable providers and basic cmdlets like Get-Help, Get-Command, and Get-History.</span></span>

- <span data-ttu-id="eba76-167">Micro soft. Power shell. host-bevat cmdlets die worden gebruikt door de Windows Power shell-host, zoals Start-Transcript en stop-transcript.</span><span class="sxs-lookup"><span data-stu-id="eba76-167">Microsoft.PowerShell.Host - Contains cmdlets used by the Windows PowerShell host, such as Start-Transcript and Stop-Transcript.</span></span>

- <span data-ttu-id="eba76-168">Micro soft. Power shell. Management-bevat cmdlets, zoals Get-Service en Get-ChildItem die worden gebruikt voor het beheren van Windows-functies.</span><span class="sxs-lookup"><span data-stu-id="eba76-168">Microsoft.PowerShell.Management - Contains cmdlets such as Get-Service and Get-ChildItem that are used to manage Windows-based features.</span></span>

- <span data-ttu-id="eba76-169">Micro soft. Power shell. Security: bevat de certificaat provider en cmdlets die worden gebruikt voor het beheren van Windows Power shell-beveiliging, zoals Get-ACL, Get-AuthenticodeSignature en ConvertTo-SecureString.</span><span class="sxs-lookup"><span data-stu-id="eba76-169">Microsoft.PowerShell.Security - Contains the Certificate provider and cmdlets used to manage Windows PowerShell security, such as Get-Acl, Get-AuthenticodeSignature, and ConvertTo-SecureString.</span></span>

- <span data-ttu-id="eba76-170">Micro soft. Power shell. Utility: bevat cmdlets die worden gebruikt voor het bewerken van objecten en gegevens, zoals Get-member, write-host en Format-list.</span><span class="sxs-lookup"><span data-stu-id="eba76-170">Microsoft.PowerShell.Utility - Contains cmdlets used to manipulate objects and data, such as Get-Member, Write-Host, and Format-List.</span></span>

- <span data-ttu-id="eba76-171">Micro soft. WSMan. Management: bevat de WSMan-provider en-cmdlets waarmee de Windows Remote Management-service wordt beheerd, zoals Connect-WSMan en Enable-WSManCredSSP.</span><span class="sxs-lookup"><span data-stu-id="eba76-171">Microsoft.WSMan.Management - Contains the WSMan provider and cmdlets that manage the Windows Remote Management service, such as Connect-WSMan and Enable-WSManCredSSP.</span></span>

## <a name="logging-snap-in-events"></a><span data-ttu-id="eba76-172">GEBEURTENISSEN VAN MODULE LOGBOEK REGISTRATIE</span><span class="sxs-lookup"><span data-stu-id="eba76-172">LOGGING SNAP-IN EVENTS</span></span>

<span data-ttu-id="eba76-173">Vanaf Windows Power Shell 3,0 kunt u uitvoerings gebeurtenissen vastleggen voor de cmdlets in Windows Power shell-modules en-modules door de eigenschap LogPipelineExecutionDetails van modules en modules in te stellen op TRUE.</span><span class="sxs-lookup"><span data-stu-id="eba76-173">Beginning in Windows PowerShell 3.0, you can record execution events for the cmdlets in Windows PowerShell modules and snap-ins by setting the LogPipelineExecutionDetails property of modules and snap-ins to TRUE.</span></span> <span data-ttu-id="eba76-174">Zie [about_EventLogs](about_EventLogs.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="eba76-174">For more information, see [about_EventLogs](about_EventLogs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eba76-175">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="eba76-175">SEE ALSO</span></span>

[<span data-ttu-id="eba76-176">Add-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="eba76-176">Add-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[<span data-ttu-id="eba76-177">Get-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="eba76-177">Get-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[<span data-ttu-id="eba76-178">Remove-PsSnapin</span><span class="sxs-lookup"><span data-stu-id="eba76-178">Remove-PsSnapin</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[<span data-ttu-id="eba76-179">Exporteren-console</span><span class="sxs-lookup"><span data-stu-id="eba76-179">Export-Console</span></span>](xref:Microsoft.PowerShell.Core.Export-Console)

[<span data-ttu-id="eba76-180">Get-Command</span><span class="sxs-lookup"><span data-stu-id="eba76-180">Get-Command</span></span>](xref:Microsoft.PowerShell.Core.Get-Command)

[<span data-ttu-id="eba76-181">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="eba76-181">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="eba76-182">about_Modules</span><span class="sxs-lookup"><span data-stu-id="eba76-182">about_Modules</span></span>](about_Modules.md)

## <a name="keywords"></a><span data-ttu-id="eba76-183">WOORD</span><span class="sxs-lookup"><span data-stu-id="eba76-183">KEYWORDS</span></span>

<span data-ttu-id="eba76-184">about_Snapins, about_Snap_ins, about_Snap-invoeg toepassingen</span><span class="sxs-lookup"><span data-stu-id="eba76-184">about_Snapins, about_Snap_ins, about_Snap-ins</span></span>
