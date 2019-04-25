---
title: Externe communicatie van WS-Management (WSMan) in PowerShell Core
description: Externe communicatie in PowerShell Core met behulp van WSMan
ms.date: 08/06/2018
ms.openlocfilehash: e5f00128bc8ebc1b432cc77a5896a9e09d684109
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058876"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>Externe communicatie van WS-Management (WSMan) in PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instructies voor het maken van een eindpunt voor externe toegang

De PowerShell Core-pakket voor Windows bevat een WinRM-invoegtoepassing (`pwrshplugin.dll`) en een script voor installatie (`Install-PowerShellRemoting.ps1`) in `$PSHome`.
Deze bestanden inschakelen PowerShell om te accepteren van binnenkomende PowerShell externe verbindingen wanneer het eindpunt is opgegeven.

### <a name="motivation"></a>Motivatie

Een installatie van PowerShell kan tot stand brengen met externe computers met behulp van PowerShell-sessies `New-PSSession` en `Enter-PSSession`.
Als u wilt inschakelen om binnenkomende PowerShell externe verbindingen te accepteren, moet de gebruiker een WinRM voor externe toegang-eindpunt maken.
Dit is een expliciete opt-in-scenario waarin de gebruiker wordt uitgevoerd met Install-PowerShellRemoting.ps1 om de WinRM-eindpunt te maken.
Het script voor installatie is een oplossing op korte termijn vooralsnog kunt aanvullende functionaliteit voor `Enable-PSRemoting` de dezelfde actie uit te voeren.
Zie voor meer informatie, probleem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Scriptacties

Het script

1. Hiermee maakt u een map voor de invoegtoepassing binnen `$env:windir\System32\PowerShell`
1. Pwrshplugin.dll aan die locatie opgehaald
1. Genereert een configuratiebestand
1. Registers die invoegtoepassing met WinRM

### <a name="registration"></a>Registratie

Het script moet worden uitgevoerd binnen een beheerder op serverniveau PowerShell-sessie en wordt uitgevoerd in twee modi.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Uitgevoerd door het exemplaar van PowerShell die geregistreerd

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Uitgevoerd door een ander exemplaar van PowerShell namens het exemplaar dat wordt geregistreerd

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Bijvoorbeeld:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**OPMERKING:** Het script voor de registratie voor externe toegang wordt opnieuw opgestart van WinRM, zodat alle bestaande PSRP-sessies wordt beëindigd zodra het script wordt uitgevoerd. Als tijdens een sessie op afstand uitvoert, wordt deze beëindigd als de verbinding.

## <a name="how-to-connect-to-the-new-endpoint"></a>Verbinding maken met het nieuwe eindpunt

Een PowerShell-sessie naar de nieuwe PowerShell-eindpunt maken door op te geven `-ConfigurationName "some endpoint name"`. Voor verbinding met de PowerShell-sessie uit het bovenstaande voorbeeld, een te gebruiken:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Houd er rekening mee dat `New-PSSession` en `Enter-PSSession` aanroepen die niet opgeeft `-ConfigurationName` heeft betrekking op het standaardeindpunt PowerShell `microsoft.powershell`.