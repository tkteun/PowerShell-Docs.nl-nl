---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-PSSnapin
ms.openlocfilehash: 5adba912d91369250ee9891ee2bb2ca0f8cba796
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93249982"
---
# <span data-ttu-id="70603-103">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="70603-103">Add-PSSnapin</span></span>

## <span data-ttu-id="70603-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="70603-104">SYNOPSIS</span></span>
<span data-ttu-id="70603-105">Hiermee voegt u een of meer Windows Power shell-modules toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-105">Adds one or more Windows PowerShell snap-ins to the current session.</span></span>

## <span data-ttu-id="70603-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="70603-106">SYNTAX</span></span>

```
Add-PSSnapin [-Name] <String[]> [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="70603-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="70603-107">DESCRIPTION</span></span>

<span data-ttu-id="70603-108">De `Add-PSSnapin` cmdlet voegt geregistreerde Windows Power shell-modules toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-108">The `Add-PSSnapin` cmdlet adds registered Windows PowerShell snap-ins to the current session.</span></span> <span data-ttu-id="70603-109">Nadat de modules zijn toegevoegd, kunt u de cmdlets en providers gebruiken die door de modules worden ondersteund in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-109">After the snap-ins are added, you can use the cmdlets and providers that the snap-ins support in the current session.</span></span>

<span data-ttu-id="70603-110">Als u de module wilt toevoegen aan alle toekomstige Windows Power shell-sessies, voegt u een `Add-PSSnapin` opdracht toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="70603-110">To add the snap-in to all future Windows PowerShell sessions, add an `Add-PSSnapin` command to your Windows PowerShell profile.</span></span> <span data-ttu-id="70603-111">Zie [about_Profiles](about/about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="70603-111">For more information, see [about_Profiles](about/about_Profiles.md).</span></span>

<span data-ttu-id="70603-112">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Windows Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="70603-112">Beginning in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="70603-113">De uitzonde ring is **micro soft. Power shell. core** , een module (PSSnapin).</span><span class="sxs-lookup"><span data-stu-id="70603-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="70603-114">Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="70603-115">Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de cmdlet Import-Module gebruiken om ze te importeren.</span><span class="sxs-lookup"><span data-stu-id="70603-115">Modules are imported automatically on first use and you can use the Import-Module cmdlet to import them.</span></span>

## <span data-ttu-id="70603-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="70603-116">EXAMPLES</span></span>

### <span data-ttu-id="70603-117">Voor beeld 1: modules toevoegen</span><span class="sxs-lookup"><span data-stu-id="70603-117">Example 1: Add snap-ins</span></span>

```powershell
PS C:\> Add-PSSnapIn -Name Microsoft.Exchange, Microsoft.Windows.AD
```

<span data-ttu-id="70603-118">Met deze opdracht worden de modules micro soft Exchange en Active Directory toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-118">This command adds the Microsoft Exchange and Active Directory snap-ins to the current session.</span></span>

### <span data-ttu-id="70603-119">Voor beeld 2: alle geregistreerde modules toevoegen</span><span class="sxs-lookup"><span data-stu-id="70603-119">Example 2: Add all the registered snap-ins</span></span>

```powershell
PS C:\> Get-PSSnapin -Registered | Add-PSSnapin -Passthru
```

<span data-ttu-id="70603-120">Met deze opdracht worden alle geregistreerde Windows Power shell-modules toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-120">This command adds all of the registered Windows PowerShell snap-ins to the session.</span></span> <span data-ttu-id="70603-121">Er wordt gebruikgemaakt van de cmdlet Get-PSSnapin met de para meter **geregistreerd** om objecten op te halen die elk van de geregistreerde modules vertegenwoordigen. Met de pijplijn operator (|) wordt het resultaat door gegeven aan `Add-PSSnapin` , waardoor ze aan de sessie worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="70603-121">It uses the Get-PSSnapin cmdlet with the **Registered** parameter to get objects representing each of the registered snap-ins. The pipeline operator (|) passes the result to `Add-PSSnapin`, which adds them to the session.</span></span> <span data-ttu-id="70603-122">De para meter **PassThru** retourneert objecten die elk van de toegevoegde modules vertegenwoordigen.</span><span class="sxs-lookup"><span data-stu-id="70603-122">The **PassThru** parameter returns objects that represent each of the added snap-ins.</span></span>

### <span data-ttu-id="70603-123">Voor beeld 3: een module registreren en toevoegen</span><span class="sxs-lookup"><span data-stu-id="70603-123">Example 3: Register a snap-in and add it</span></span>

<span data-ttu-id="70603-124">Met de eerste opdracht worden modules opgehaald die zijn toegevoegd aan de huidige sessie, waaronder de modules die worden geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="70603-124">The first command gets snap-ins that have been added to the current session that include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="70603-125">In dit voor beeld wordt ManagementFeatures niet geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="70603-125">In this example, ManagementFeatures is not returned.</span></span> <span data-ttu-id="70603-126">Dit geeft aan dat deze niet is toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-126">This indicates that it has not been added to the session.</span></span>

<span data-ttu-id="70603-127">Met de tweede opdracht worden modules opgehaald die op uw systeem zijn geregistreerd, inclusief de modules die al zijn toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-127">The second command gets snap-ins that have been registered on your system, which includes those that have already been added to the session.</span></span> <span data-ttu-id="70603-128">De module bevat geen invoeg toepassingen die worden geïnstalleerd met Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="70603-128">It does not include the snap-ins that are installed with Windows PowerShell.</span></span> <span data-ttu-id="70603-129">In dit geval retourneert de opdracht geen modules. Dit geeft aan dat de ManagementFeatures-module niet is geregistreerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="70603-129">In this case, the command does not return any snap-ins. This indicates that the ManagementFeatures snapin has not been registered on the system.</span></span>

<span data-ttu-id="70603-130">Met de derde opdracht maakt u een alias, InstallUtil, voor het pad van het InstallUtil-hulp programma in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70603-130">The third command creates an alias, installutil, for the path of the InstallUtil tool in .NET Framework.</span></span>

<span data-ttu-id="70603-131">De vierde opdracht maakt gebruik van het InstallUtil-hulp programma om de module te registreren.</span><span class="sxs-lookup"><span data-stu-id="70603-131">The fourth command uses the InstallUtil tool to register the snap-in.</span></span> <span data-ttu-id="70603-132">Met de opdracht geeft u het pad op van ManagementCmdlets.dll, de bestands naam of module van de module.</span><span class="sxs-lookup"><span data-stu-id="70603-132">The command specifies the path of ManagementCmdlets.dll, the filename or module name of the snap-in.</span></span>

<span data-ttu-id="70603-133">De vijfde opdracht is hetzelfde als de tweede opdracht.</span><span class="sxs-lookup"><span data-stu-id="70603-133">The fifth command is the same as the second command.</span></span> <span data-ttu-id="70603-134">Deze keer gebruikt u deze om te controleren of de module ManagementCmdlets is geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="70603-134">This time, you use it to verify that the ManagementCmdlets snap-in is registered.</span></span>

<span data-ttu-id="70603-135">De zesde opdracht gebruikt de `Add-PSSnapin` cmdlet om de module ManagementFeatures toe te voegen aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-135">The sixth command uses the `Add-PSSnapin` cmdlet to add the ManagementFeatures snap-in to the session.</span></span> <span data-ttu-id="70603-136">Hiermee geeft u de naam van de module, ManagementFeatures, niet de bestands naam.</span><span class="sxs-lookup"><span data-stu-id="70603-136">It specifies the name of the snap-in, ManagementFeatures, not the file name.</span></span>

<span data-ttu-id="70603-137">Om te controleren of de module aan de sessie is toegevoegd, gebruikt de zevende opdracht de **module** parameter van de cmdlet Get-Command.</span><span class="sxs-lookup"><span data-stu-id="70603-137">To verify that the snap-in is added to the session, the seventh command uses the **Module** parameter of the Get-Command cmdlet.</span></span> <span data-ttu-id="70603-138">Hiermee worden de items weer gegeven die zijn toegevoegd aan de sessie door een module of module.</span><span class="sxs-lookup"><span data-stu-id="70603-138">It displays the items that were added to the session by a snap-in or module.</span></span>

<span data-ttu-id="70603-139">U kunt ook de eigenschap **PSSnapin** van het object gebruiken dat door de `Get-Command` cmdlet wordt geretourneerd om de module of module te vinden waarin een cmdlet afkomstig is.</span><span class="sxs-lookup"><span data-stu-id="70603-139">You can also use the **PSSnapin** property of the object that the `Get-Command` cmdlet returns to find the snap-in or module in which a cmdlet originated.</span></span> <span data-ttu-id="70603-140">De achtste opdracht maakt gebruik van de punt notatie om de waarde van de eigenschap PSSnapin van de cmdlet Set-Alias te vinden.</span><span class="sxs-lookup"><span data-stu-id="70603-140">The eighth command uses dot notation to find the value of the PSSnapin property of the Set-Alias cmdlet.</span></span>

```powershell
PS C:\> Get-PSSnapin
PS C:\> Get-PSSnapin -Registered
PS C:\> Set-Alias installutil $env:windir\Microsoft.NET\Framework\v2.0.50727\installutil.exe
PS C:\> installutil C:\Dev\Management\ManagementCmdlets.dll
PS C:\> Get-PSSnapin -Registered
PS C:\> add-pssnapin ManagementFeatures
PS C:\> Get-Command -Module ManagementFeatures
PS C:\> (Get-Command Set-Alias).pssnapin
```

<span data-ttu-id="70603-141">In dit voor beeld wordt het proces van het registreren van een module op uw systeem gedemonstreerd en vervolgens toegevoegd aan uw sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-141">This example demonstrates the process of registering a snap-in on your system and then adding it to your session.</span></span> <span data-ttu-id="70603-142">Er wordt gebruikgemaakt van ManagementFeatures, een fictieve module die is geïmplementeerd in een bestand met de naam ManagementCmdlets.dll.</span><span class="sxs-lookup"><span data-stu-id="70603-142">It uses ManagementFeatures, a fictitious snap-in implemented in a file that is named ManagementCmdlets.dll.</span></span>

## <span data-ttu-id="70603-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70603-143">PARAMETERS</span></span>

### <span data-ttu-id="70603-144">-Name</span><span class="sxs-lookup"><span data-stu-id="70603-144">-Name</span></span>

<span data-ttu-id="70603-145">Hiermee geeft u de naam van de module.</span><span class="sxs-lookup"><span data-stu-id="70603-145">Specifies the name of the snap-in.</span></span> <span data-ttu-id="70603-146">Dit is de naam, niet de Assemblyname of de module.</span><span class="sxs-lookup"><span data-stu-id="70603-146">This is the Name, not the AssemblyName or ModuleName.</span></span> <span data-ttu-id="70603-147">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="70603-147">Wildcards are permitted.</span></span>

<span data-ttu-id="70603-148">Als u de namen van de geregistreerde modules op uw systeem wilt zoeken, typt u `Get-PSSnapin -Registered` .</span><span class="sxs-lookup"><span data-stu-id="70603-148">To find the names of the registered snap-ins on your system, type `Get-PSSnapin -Registered`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="70603-149">-PassThru</span><span class="sxs-lookup"><span data-stu-id="70603-149">-PassThru</span></span>

<span data-ttu-id="70603-150">Geeft aan dat deze cmdlet een object retourneert dat elke toegevoegde module vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="70603-150">Indicates that this cmdlet returns an object that represents each added snap-in.</span></span> <span data-ttu-id="70603-151">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="70603-151">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="70603-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70603-152">CommonParameters</span></span>

<span data-ttu-id="70603-153">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70603-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70603-154">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="70603-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70603-155">INVOER</span><span class="sxs-lookup"><span data-stu-id="70603-155">INPUTS</span></span>

### <span data-ttu-id="70603-156">Geen</span><span class="sxs-lookup"><span data-stu-id="70603-156">None</span></span>
<span data-ttu-id="70603-157">U kunt geen objecten naar deze cmdlet pipeen.</span><span class="sxs-lookup"><span data-stu-id="70603-157">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="70603-158">UITVOER</span><span class="sxs-lookup"><span data-stu-id="70603-158">OUTPUTS</span></span>

### <span data-ttu-id="70603-159">Geen of System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="70603-159">None or System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="70603-160">Met deze cmdlet wordt een PSSnapInInfo-object geretourneerd dat de module vertegenwoordigt als u de para meter **PassThru** opgeeft.</span><span class="sxs-lookup"><span data-stu-id="70603-160">This cmdlet returns a PSSnapInInfo object that represents the snap-in if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="70603-161">Anders wordt met deze cmdlet geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="70603-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="70603-162">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="70603-162">NOTES</span></span>

* <span data-ttu-id="70603-163">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die met Windows Power shell zijn geïnstalleerd, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="70603-163">Beginning in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="70603-164">In Windows Power Shell 2,0, en in host-Program ma's die oudere sessies maken in latere versies van Windows Power shell, worden de kern opdrachten verpakt in modules (PSSnapins).</span><span class="sxs-lookup"><span data-stu-id="70603-164">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins (PSSnapins).</span></span> <span data-ttu-id="70603-165">De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module.</span><span class="sxs-lookup"><span data-stu-id="70603-165">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="70603-166">Externe sessies, zoals computers die zijn gestart door de New-PSSession cmdlet, zijn ook oudere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="70603-166">Also, remote sessions, such as those started by the New-PSSession cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="70603-167">Zie de [methode CreateDefault2](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) in de MSDN-bibliotheek voor meer informatie over de **CreateDefault2** -methode voor het maken van nieuwere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="70603-167">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

* <span data-ttu-id="70603-168">Zie [about_PSSnapins](About/about_PSSnapins.md) en [een Windows Power shell-module maken](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in)voor meer informatie over modules.</span><span class="sxs-lookup"><span data-stu-id="70603-168">For more information about snap-ins, see [about_PSSnapins](About/about_PSSnapins.md) and [How to Create a Windows PowerShell Snap-in](/powershell/scripting/developer/cmdlet/how-to-create-a-windows-powershell-snap-in).</span></span>
* <span data-ttu-id="70603-169">`Add-PSSnapin` Hiermee wordt de module alleen toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="70603-169">`Add-PSSnapin` adds the snap-in only to the current session.</span></span> <span data-ttu-id="70603-170">Als u de module wilt toevoegen aan alle Windows Power shell-sessies, voegt u deze toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="70603-170">To add the snap-in to all Windows PowerShell sessions, add it to your Windows PowerShell profile.</span></span> <span data-ttu-id="70603-171">Zie about_Profiles voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="70603-171">For more information, see about_Profiles.</span></span>
* <span data-ttu-id="70603-172">U kunt elke module die is geregistreerd met behulp van het hulp programma voor installatie van Microsoft .NET Framework toevoegen.</span><span class="sxs-lookup"><span data-stu-id="70603-172">You can add any snap-in that has been registered using the Microsoft .NET Framework install utility.</span></span> <span data-ttu-id="70603-173">Zie voor meer informatie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="70603-173">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>
* <span data-ttu-id="70603-174">Als u een lijst wilt weer geven met modules die zijn geregistreerd op uw computer, typt u `Get-PSSnapin -Registered` .</span><span class="sxs-lookup"><span data-stu-id="70603-174">To get a list of snap-ins that are registered on your computer, type `Get-PSSnapin -Registered`.</span></span>
* <span data-ttu-id="70603-175">Voordat u een module toevoegt, `Add-PSSnapin` controleert u de versie van de module om te controleren of deze compatibel is met de huidige versie van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="70603-175">Before adding a snap-in, `Add-PSSnapin` checks the version of the snap-in to verify that it is compatible with the current version of Windows PowerShell.</span></span> <span data-ttu-id="70603-176">Als de invoeg toepassing de versie controle mislukt, wordt een fout gerapporteerd in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="70603-176">If the snap-in fails the version check, Windows PowerShell reports an error.</span></span>

## <span data-ttu-id="70603-177">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="70603-177">RELATED LINKS</span></span>

[<span data-ttu-id="70603-178">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="70603-178">Get-PSSnapin</span></span>](Get-PSSnapin.md)

[<span data-ttu-id="70603-179">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="70603-179">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
