---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: De Windows Power Shell 2,0-engine gebruiken
ms.openlocfilehash: e00fb71c7fc32f5b48bc17ef5b25f910a846c893
ms.sourcegitcommit: 1748b2bdfae81d98097962c6c25c25df4bced1d8
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84262610"
---
# <a name="using-the-windows-powershell-20-engine"></a>De Windows Power Shell 2,0-engine gebruiken

Windows Power shell is ontworpen om achterwaarts compatibel te zijn met eerdere versies. Cmdlets, providers, modules, modules en scripts die zijn geschreven voor Windows Power Shell 2,0, worden ongewijzigd uitgevoerd in nieuwere versies van Windows Power shell. Microsoft .NET Framework 4 heeft echter het runtime-activerings beleid gewijzigd.
Windows Power shell-host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en gecompileerd met common language runtime (CLR) 2,0 kunnen niet zonder aanpassing worden uitgevoerd in nieuwe versies van Windows Power shell die zijn gecompileerd met CLR 4,0 (of hoger).

De Windows Power Shell 2,0-engine is alleen bedoeld voor gebruik wanneer een bestaand script of hostprogramma niet kan worden uitgevoerd, omdat het niet compatibel is met Windows Power shell 5,1. Voor beelden hiervan zijn oudere versies van Exchange-of SQL Server-modules. Dergelijke gevallen worden naar verwachting zeldzaam.

Veel Program ma's die de Windows Power Shell 2,0-engine nodig hebben, worden automatisch gestart. Deze instructies zijn opgenomen in zeldzame gevallen waarin u de engine hand matig moet starten.

## <a name="deprecation-and-security-concerns"></a>Problemen met afschaffing en beveiliging

Windows Power Shell 2,0 is afgeschaft in augustus 2017. Zie de [aankondiging][] in het Power shell-blog voor meer informatie.

Er ontbreken in Windows Power Shell 2,0 een aanzienlijke hoeveelheid aan de functies voor beveiliging en beveiliging die zijn toegevoegd in versie 3, 4 en 5. We raden u ten zeerste aan gebruikers niet te gebruiken als ze dit kunnen helpen. Zie voor meer informatie [een vergelijking van shell-en script taal beveiliging][] en [Power shell ♥ het blauwe team][blueteam].

## <a name="installing-and-enabling-required-programs"></a>Vereiste Program Ma's installeren en inschakelen

Voordat u de Windows Power Shell 2,0-Engine start, schakelt u de Windows Power Shell 2,0-engine in en Microsoft .NET Framework 3,5 met Service Pack 1. Zie [Windows Power Shell installeren][]voor instructies.

Systemen waarop Windows Management Framework 3,0 of hoger is geïnstalleerd, hebben alle vereiste onderdelen. U hoeft verder niets te configureren. Zie [WMF installeren en configureren][]voor meer informatie over het installeren van Windows Management Framework.

## <a name="how-to-start-the-windows-powershell-20-engine"></a>De Windows Power Shell 2,0-engine starten

Wanneer u Windows Power shell start, wordt standaard de nieuwste versie gestart. Als u Windows Power shell met de Windows Power Shell 2,0-engine wilt starten, gebruikt u de versie parameter van `PowerShell.exe` . U kunt de opdracht uitvoeren vanaf een opdracht prompt, waaronder Windows Power shell en cmd. exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Een externe sessie starten met de Windows Power Shell 2,0-engine

Als u de Windows Power Shell 2,0-engine wilt uitvoeren in een externe sessie, maakt u een sessie configuratie (ook wel een _eind punt_genoemd) op de externe computer die de Windows power Shell 2,0-engine laadt. De sessie configuratie wordt opgeslagen op de externe computer en kan worden gebruikt door een geautoriseerde gebruiker om sessies te maken die gebruikmaken van de Windows Power Shell 2,0-engine.

Dit is een geavanceerde taak die meestal wordt uitgevoerd door een systeem beheerder.

In de volgende procedure wordt de para meter **PSVersion** van de cmdlet [REGI ster-PSSessionConfiguration][] gebruikt om een sessie configuratie te maken die gebruikmaakt van de Windows Power Shell 2,0-engine. U kunt ook de para meter **PowerShellVersion** van de cmdlet [New-PSSessionConfigurationFile][] gebruiken om een sessie configuratie bestand te maken voor een sessie die de Windows Power Shell 2,0-engine laadt en u kunt de **PSVersion** -para meter van de para meter [set-PSSessionConfiguration][] gebruiken om een sessie configuratie te wijzigen voor het gebruik van de Windows Power Shell 2,0-engine.

Zie [about_Session_Configuration_Files][]voor meer informatie over sessie configuratie bestanden.
Zie [about_Session_Configurations][]voor meer informatie over de configuratie van sessies, met inbegrip van Setup en beveiliging.

### <a name="to-start-a-remote-windows-powershell-20-session"></a>Een externe Windows Power Shell 2,0-sessie starten

1. Als u een sessie configuratie wilt maken waarvoor de Windows Power Shell 2,0-engine vereist is, gebruikt u de para meter **PSVersion** van de `Register-PSSessionConfiguration` cmdlet met de waarde `2.0` .
   Voer deze opdracht uit op de computer aan de server zijde of het ontvangende einde van de verbinding.

   Met de volgende voorbeeld opdracht wordt de PS2-sessie configuratie op de Server01-computer gemaakt. Als u deze opdracht wilt uitvoeren, start u Windows Power shell met de optie **als administrator uitvoeren** .

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. Als u een sessie op de Server01-computer wilt maken die gebruikmaakt van de PS2-sessie configuratie, gebruikt u de para meter **configuratiepad** van cmdlets die een externe sessie maken, zoals de cmdlet New-PSSession.

   Wanneer een sessie die gebruikmaakt van de sessie configuratie wordt gestart, wordt de Windows Power Shell 2,0-engine automatisch in de sessie geladen.

   Met de volgende opdracht wordt een sessie gestart op de Server01-computer die gebruikmaakt van de PS2-sessie configuratie. Met de opdracht wordt de sessie opgeslagen in de `$s` variabele.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Een achtergrond taak starten met de Windows Power Shell 2,0-engine

Als u een achtergrond taak wilt starten met de Windows Power Shell 2,0-engine, gebruikt u de para meter **PSVersion** van de cmdlet [Start-job][] .

Met de volgende opdracht wordt een achtergrond taak gestart met de Windows Power Shell 2,0-engine

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Zie [about_Jobs][]voor meer informatie over achtergrond taken.

<!-- link references -->
[Announcement]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Een vergelijking van de beveiliging van shell-en script taal]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Windows PowerShell installeren]: install/Installing-Windows-PowerShell.md
[WMF installeren en configureren]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfiguration
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Begin taak]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
