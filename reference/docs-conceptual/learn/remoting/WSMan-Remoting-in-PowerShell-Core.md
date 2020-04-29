---
title: Externe communicatie van WS-Management (WSMan) in PowerShell Core
description: Externe communicatie in Power shell core met behulp van WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/22/2020
ms.locfileid: "62058876"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Externe communicatie van WS-Management (WSMan) in PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructies voor het maken van een extern eind punt

Het Power shell core-pakket voor Windows bevat een WinRM-invoeg`pwrshplugin.dll`toepassing () en een installatie`Install-PowerShellRemoting.ps1`script ( `$PSHome`) in.
Met deze bestanden kunnen Power shell binnenkomende Power shell-externe verbindingen accepteren wanneer het eind punt is opgegeven.

### <a name="motivation"></a>Motivatie

Een installatie van Power shell kan Power shell-sessies tot stand `New-PSSession` brengen `Enter-PSSession`met externe computers met behulp van en.
Voor het accepteren van binnenkomende Power shell-externe verbindingen, moet de gebruiker een extern eind punt voor WinRM maken.
Dit is een expliciet opt-in-scenario waarbij de gebruiker Install-PowerShellRemoting. ps1 uitvoert om het WinRM-eind punt te maken.
Het installatie script is een oplossing voor de korte termijn totdat we extra functionaliteit toevoegen `Enable-PSRemoting` om dezelfde actie uit te voeren.
Zie issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193)voor meer informatie.

### <a name="script-actions"></a>Script acties

Het script

1. Hiermee maakt u een map voor de invoeg toepassing in`$env:windir\System32\PowerShell`
1. Kopieert pwrshplugin. dll naar die locatie
1. Hiermee genereert u een configuratie bestand
1. Registreert deze invoeg toepassing met WinRM

### <a name="registration"></a>Registratie

Het script moet worden uitgevoerd binnen een Power shell-sessie op beheerders niveau en kan in twee modi worden uitgevoerd.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Uitgevoerd door het instantie van Power shell dat wordt geregistreerd

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Uitgevoerd door een ander exemplaar van Power shell namens het exemplaar dat wordt geregistreerd

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Bijvoorbeeld:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**Opmerking:** Het externe registratie script zal WinRM opnieuw opstarten, zodat alle bestaande PSRP-sessies onmiddellijk worden beëindigd nadat het script is uitgevoerd. Als deze wordt uitgevoerd tijdens een externe sessie, wordt de verbinding verbroken.

## <a name="how-to-connect-to-the-new-endpoint"></a>Verbinding maken met het nieuwe eind punt

Maak een Power shell-sessie met het nieuwe Power shell `-ConfigurationName "some endpoint name"`-eind punt door op te geven. Als u vanuit bovenstaand voor beeld verbinding wilt maken met het Power shell-exemplaar, gebruikt u een van de volgende opties:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Houd er `New-PSSession` rekening `Enter-PSSession` mee dat en aanroepen die niet `-ConfigurationName` worden opgegeven, het standaard-Power `microsoft.powershell`shell-eind punt zijn.