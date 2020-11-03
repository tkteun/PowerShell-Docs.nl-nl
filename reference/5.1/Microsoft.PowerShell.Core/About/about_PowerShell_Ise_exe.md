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
# <a name="about-powershell-iseexe"></a>Informatie over Power shell-Ise.exe

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt uitgelegd hoe u het PowerShell_Ise.exe opdracht regel programma gebruikt.

## <a name="long-description"></a>LANGE BESCHRIJVING

PowerShell_Ise.exe start een ISE-sessie (Integrated Scripting Environment) van Windows Power shell. U kunt dit uitvoeren in Cmd.exe en in Windows Power shell.

Als u PowerShell_ISE.exe wilt uitvoeren, typt u PowerShell_ISE.exe, PowerShell_ISE of ISE.

## <a name="syntax"></a>SYNTAXIS

```
PowerShell_Ise[.exe]
PowerShell_ISE[.exe]
ISE[.exe]
[-File]<FilePath[]> [-NoProfile] [-MTA]
-Help | ? | -? | /? Displays the syntax and describes the command-line switches.
```

## <a name="parameters"></a>PARAMETERS

### <a name="-file"></a>-Bestand

Hiermee opent u de opgegeven bestanden in Windows PowerShell ISE. De parameter naam ("-file") is optioneel. Als u meer dan één bestand wilt weer geven, geeft u één teken reeks tussen aanhalings tekens op. Gebruik komma's om de bestands namen in de teken reeks van elkaar te scheiden.

Bijvoorbeeld:

PowerShell_ISE-bestand File1.ps1, File2.ps1, File3.xml.

Spaties tussen de bestands namen zijn toegestaan in Windows Power shell, maar worden mogelijk niet correct geïnterpreteerd door andere Program ma's, zoals Cmd.exe.

U kunt deze para meter gebruiken om elk tekst bestand te openen, met inbegrip van Windows Power shell-script bestanden en XML-bestanden.

### <a name="-mta"></a>-MTA

Start Windows PowerShell ISE met behulp van een Apartment met meerdere threads. Deze para meter is geïntroduceerd in Windows Power Shell 3,0. Apartment met één thread (STA) is de standaard waarde.

### <a name="-noprofile"></a>-Geen profiel

Voert geen Windows Power shell-profielen uit. Standaard worden Windows Power shell-profielen in elke sessie uitgevoerd.

Deze para meter wordt aanbevolen wanneer u gedeelde inhoud schrijft, zoals functies en scripts die worden uitgevoerd op systemen met verschillende profielen.
Zie [about_Profiles](about_Profiles.md)voor meer informatie.

### <a name="-help---"></a>-Help-?,/?

Geeft Help weer voor PowerShell_ISE.exe.

## <a name="examples"></a>VOORBEELDEN

Deze opdrachten beginnen Windows PowerShell ISE. De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.

```
PS C:> PowerShell_ISE.exe
PS C:> PowerShell_ISE
PS C:> ISE
```

Met deze opdrachten wordt het Get-Profile.ps1 script in Windows PowerShell ISE geopend.
De opdrachten zijn gelijkwaardig en kunnen door elkaar worden gebruikt.

```
PS C:> PowerShell_ISE.exe -File .\Get-Profile.ps1
PS C:> ISE -File .\Get-Profile.ps1
PS C:> ISE .\Get-Profile.ps1
```

Met deze opdracht wordt de Get-Backups.ps1-en Get-BackupInstance.ps1-scripts in Windows PowerShell ISE geopend. Als u meer dan één bestand wilt openen, gebruikt u een komma om de bestands namen van elkaar te scheiden en plaatst u de volledige bestands naam tussen aanhalings tekens.

```
PS C:> ISE -File ".\Get-Backups.ps1,Get-BackupInstance.ps1"
```

Met deze opdracht wordt Windows PowerShell ISE zonder profielen gestart.

```
PS C:> ISE -NoProfile
```

Met deze opdracht krijgt u hulp bij PowerShell_ISE.exe.

```
PS C:> ISE -help
```

## <a name="see-also"></a>ZIE OOK

[about_PowerShell.exe](about_PowerShell_exe.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)

[Windows Power shell Integrated Scripting Environment (ISE)](/powershell/scripting/windows-powershell/ise/introducing-the-windows-powershell-ise)
