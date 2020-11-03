---
description: Hierin wordt uitgelegd hoe u het PowerShell_Ise.exe opdracht regel programma gebruikt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_ise_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Ise_exe
ms.openlocfilehash: c7500eb6d8586b9dca568edc4e805c577e94bec4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252764"
---
# <a name="about-powershell-iseexe"></a><span data-ttu-id="6f8c3-104">Informatie over Power shell-Ise.exe</span><span class="sxs-lookup"><span data-stu-id="6f8c3-104">About PowerShell Ise.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="6f8c3-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6f8c3-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="6f8c3-106">Hierin wordt uitgelegd hoe u het PowerShell_Ise.exe opdracht regel programma gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-106">Explains how to use the PowerShell_Ise.exe command-line tool.</span></span>

## <a name="long-description"></a><span data-ttu-id="6f8c3-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="6f8c3-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="6f8c3-108">PowerShell_Ise.exe start een ISE-sessie (Integrated Scripting Environment) van Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-108">PowerShell_Ise.exe starts a Windows PowerShell Integrated Scripting Environment (ISE) session.</span></span> <span data-ttu-id="6f8c3-109">U kunt dit uitvoeren in Cmd.exe en in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-109">You can run it in Cmd.exe and in Windows PowerShell.</span></span>

<span data-ttu-id="6f8c3-110">Als u PowerShell_ISE.exe wilt uitvoeren, typt u PowerShell_ISE.exe, PowerShell_ISE of ISE.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-110">To run PowerShell_ISE.exe, type PowerShell_ISE.exe, PowerShell_ISE, or ISE.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f8c3-111">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="6f8c3-111">SYNTAX</span></span>

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a><span data-ttu-id="6f8c3-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6f8c3-112">PARAMETERS</span></span>

### <a name="-file"></a><span data-ttu-id="6f8c3-113">-Bestand</span><span class="sxs-lookup"><span data-stu-id="6f8c3-113">-File</span></span>

<span data-ttu-id="6f8c3-114">Hiermee opent u de opgegeven bestanden in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-114">Opens the specified files in Windows PowerShell ISE.</span></span> <span data-ttu-id="6f8c3-115">De parameter naam ("-file") is optioneel.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-115">The parameter name ("-File") is optional.</span></span> <span data-ttu-id="6f8c3-116">Als u meer dan één bestand wilt weer geven, geeft u één teken reeks tussen aanhalings tekens op.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-116">To list more than one file, enter one text string enclosed in quotation marks.</span></span> <span data-ttu-id="6f8c3-117">Gebruik komma's om de bestands namen in de teken reeks van elkaar te scheiden.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-117">Use commas to separate the file names within the string.</span></span>

<span data-ttu-id="6f8c3-118">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="6f8c3-118">For example:</span></span>

<span data-ttu-id="6f8c3-119">PowerShell_ISE-bestand File1.ps1, File2.ps1, File3.xml.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-119">PowerShell_ISE -File "File1.ps1,File2.ps1,File3.xml".</span></span>

<span data-ttu-id="6f8c3-120">Spaties tussen de bestands namen zijn toegestaan in Windows Power shell, maar worden mogelijk niet correct geïnterpreteerd door andere Program ma's, zoals Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-120">Spaces between the file names are permitted in Windows PowerShell, but might not be interpreted correctly by other programs, such as Cmd.exe.</span></span>

<span data-ttu-id="6f8c3-121">U kunt deze para meter gebruiken om elk tekst bestand te openen, met inbegrip van Windows Power shell-script bestanden en XML-bestanden.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-121">You can use this parameter to open any text file, including Windows PowerShell script files and XML files.</span></span>

### <a name="-mta"></a><span data-ttu-id="6f8c3-122">-MTA</span><span class="sxs-lookup"><span data-stu-id="6f8c3-122">-Mta</span></span>

<span data-ttu-id="6f8c3-123">Start Windows PowerShell ISE met behulp van een Apartment met meerdere threads.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-123">Starts Windows PowerShell ISE using a multi-threaded apartment.</span></span> <span data-ttu-id="6f8c3-124">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-124">This parameter is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="6f8c3-125">Apartment met één thread (STA) is de standaard waarde.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-125">Single-threaded apartment (STA) is the default.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="6f8c3-126">-Geen profiel</span><span class="sxs-lookup"><span data-stu-id="6f8c3-126">-NoProfile</span></span>

<span data-ttu-id="6f8c3-127">Voert geen Windows Power shell-profielen uit.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-127">Does not run Windows PowerShell profiles.</span></span> <span data-ttu-id="6f8c3-128">Standaard worden Windows Power shell-profielen in elke sessie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-128">By default, Windows PowerShell profiles are run in every session.</span></span>

<span data-ttu-id="6f8c3-129">Deze para meter wordt aanbevolen wanneer u gedeelde inhoud schrijft, zoals functies en scripts die worden uitgevoerd op systemen met verschillende profielen.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-129">This parameter is recommended when you are writing shared content, such as functions and scripts that will be run on systems with different profiles.</span></span>
<span data-ttu-id="6f8c3-130">Zie [about_Profiles](about_Profiles.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-130">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="-help---"></a><span data-ttu-id="6f8c3-131">-Help-?,/?</span><span class="sxs-lookup"><span data-stu-id="6f8c3-131">-Help -?, /?</span></span>

<span data-ttu-id="6f8c3-132">Geeft Help weer voor PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-132">Displays help for PowerShell_ISE.exe.</span></span>

## <a name="examples"></a><span data-ttu-id="6f8c3-133">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="6f8c3-133">EXAMPLES</span></span>

<span data-ttu-id="6f8c3-134">Deze opdrachten beginnen Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-134">These commands start Windows PowerShell ISE.</span></span> <span data-ttu-id="6f8c3-135">De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-135">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

<span data-ttu-id="6f8c3-136">Met deze opdrachten wordt het Get-Profile.ps1 script in Windows PowerShell ISE geopend.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-136">These commands open the Get-Profile.ps1 script in Windows PowerShell ISE.</span></span>
<span data-ttu-id="6f8c3-137">De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-137">The commands are equivalent and can be used interchangeably.</span></span>

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

<span data-ttu-id="6f8c3-138">Met deze opdracht wordt de Get-Backups.ps1-en Get-BackupInstance.ps1-scripts in Windows PowerShell ISE geopend.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-138">This command opens the Get-Backups.ps1 and Get-BackupInstance.ps1 scripts in Windows PowerShell ISE.</span></span> <span data-ttu-id="6f8c3-139">Als u meer dan één bestand wilt openen, gebruikt u een komma om de bestands namen van elkaar te scheiden en plaatst u de volledige bestands naam tussen aanhalings tekens.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-139">To open more than one file, use a comma to separate the file names and enclose the entire file name value in quotation marks.</span></span>

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

<span data-ttu-id="6f8c3-140">Met deze opdracht wordt Windows PowerShell ISE zonder profielen gestart.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-140">This command starts Windows PowerShell ISE with no profiles.</span></span>

```
PS C:> ISE -NoProfile
```

<span data-ttu-id="6f8c3-141">Met deze opdracht krijgt u hulp bij PowerShell_ISE.exe.</span><span class="sxs-lookup"><span data-stu-id="6f8c3-141">This command gets help for PowerShell_ISE.exe.</span></span>

```
PS C:> ISE -help
```

## <a name="see-also"></a><span data-ttu-id="6f8c3-142">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="6f8c3-142">SEE ALSO</span></span>

[<span data-ttu-id="6f8c3-143">about_PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="6f8c3-143">about_PowerShell.exe</span></span>](about_PowerShell_exe.md)

[<span data-ttu-id="6f8c3-144">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="6f8c3-144">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)

[<span data-ttu-id="6f8c3-145">Windows Power shell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="6f8c3-145">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
