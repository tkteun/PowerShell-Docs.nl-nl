---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: De Windows PowerShell 2.0-engine starten
ms.openlocfilehash: 824077008d2dcfd707e977d2112f0882d07a8aca
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811070"
---
# <a name="starting-the-windows-powershell-20-engine"></a>De Windows PowerShell 2.0-engine starten

In deze sectie wordt uitgelegd hoe u de Windows Power Shell 2,0-Engine start op Windows 8,1, Windows Server 2012 R2, Windows 8 en Windows Server 2012, waaronder de Windows Power Shell 2,0-engine, en op andere systemen waarop Windows Power Shell 2,0, Windows Power Shell 3,0 en Windows Power Shell 4,0 zijn geïnstalleerd.

Windows Power Shell 4,0 en Windows Power Shell 3,0 zijn ontworpen om achterwaarts compatibel te zijn met Windows Power Shell 2,0. Cmdlets, providers, modules, modules en scripts die zijn geschreven voor Windows Power Shell 2,0, worden ongewijzigd uitgevoerd in Windows Power Shell 4,0 en Windows Power Shell 3,0. Vanwege een wijziging in het runtime-activerings beleid in Microsoft .NET Framework 4 worden Windows Power shell-host-Program ma's die zijn geschreven voor Windows Power Shell 2,0 en gecompileerd met common language runtime (CLR) 2,0 niet uitgevoerd zonder aanpassing in Windows Power Shell 3,0 of Windows Power Shell 4,0, die zijn gecompileerd met CLR-4,0. De Windows Power Shell 2,0-engine is alleen bedoeld voor gebruik wanneer een bestaand script of hostprogramma niet kan worden uitgevoerd omdat het niet compatibel is met Windows Power Shell 4,0, Windows Power Shell 3,0 of Microsoft .NET Framework 4. Dergelijke gevallen worden naar verwachting zeldzaam.

Veel Program ma's die de Windows Power Shell 2,0-engine nodig hebben, worden automatisch gestart. Deze instructies zijn opgenomen in zeldzame gevallen waarin u de engine hand matig moet starten.

## <a name="installing-and-enabling-required-programs"></a>Vereiste Program Ma's installeren en inschakelen

Voordat u de Windows Power Shell 2,0-Engine start, schakelt u de Windows Power Shell 2,0-engine in en Microsoft .NET Framework 3,5 met Service Pack 1. Zie [Windows Power Shell installeren](../install/Installing-Windows-PowerShell.md)voor instructies.

Systemen waarop Windows Management Framework 4,0 of Windows Management Framework 3,0 zijn geïnstalleerd, hebben alle vereiste onderdelen. U hoeft verder niets te configureren. Zie [Windows Power Shell installeren](../install/Installing-Windows-PowerShell.md)voor meer informatie over het installeren van [windows Management Framework 4,0](https://go.microsoft.com/fwlink/?LinkID=293881) of Windows Management Framework 3,0.

## <a name="how-to-start-the-windows-powershell-20-engine"></a>De Windows Power Shell 2,0-engine starten

Wanneer u Windows Power shell start, wordt standaard de nieuwste versie gestart. Als u Windows Power shell met de Windows Power Shell 2,0-engine wilt starten, gebruikt u de versie parameter van Power shell. exe. U kunt de opdracht uitvoeren vanaf een opdracht prompt, waaronder Windows Power shell en cmd. exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Een externe sessie starten met de Windows Power Shell 2,0-engine

Als u de Windows Power Shell 2,0-engine wilt uitvoeren in een externe sessie, maakt u een sessie configuratie (ook wel een ' eind punt ' genoemd) op de externe computer die de Windows Power Shell 2,0-engine laadt. De sessie configuratie wordt opgeslagen op de externe computer en kan worden gebruikt door een geautoriseerde gebruiker om sessies te maken die gebruikmaken van de Windows Power Shell 2,0-engine.

Dit is een geavanceerde taak die meestal wordt uitgevoerd door een systeem beheerder.

In de volgende procedure wordt de para meter **PSVersion** van de cmdlet [REGI ster-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) gebruikt om een sessie configuratie te maken die gebruikmaakt van de Windows Power Shell 2,0-engine. U kunt ook de para meter **PowerShellVersion** van de cmdlet [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) gebruiken om een sessie configuratie bestand te maken voor een sessie die de Windows Power Shell 2,0-engine laadt en u kunt de **PSVersion** -para meter van de para meter [set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) gebruiken om een sessie configuratie te wijzigen voor het gebruik van de Windows Power Shell 2,0-engine.

Zie [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8)voor meer informatie over sessie configuratie bestanden. Zie [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab)voor meer informatie over de configuratie van sessies, met inbegrip van Setup en beveiliging.

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Een externe Windows Power Shell 2,0-sessie starten

1. Als u een sessie configuratie wilt maken waarvoor de Windows Power Shell 2,0-engine is vereist, gebruikt u de para meter **PSVersion** van de cmdlet [REGI ster-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) met de waarde "2,0". Voer deze opdracht uit op de computer aan de server zijde of het ontvangende einde van de verbinding.

   Met de volgende voorbeeld opdracht wordt de PS2-sessie configuratie op de Server01-computer gemaakt. Als u deze opdracht wilt uitvoeren, start u Windows Power Shell 4,0 of Windows Power Shell 3,0 met de optie **als administrator uitvoeren** .

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Als u een sessie op de Server01-computer wilt maken die gebruikmaakt van de PS2-sessie configuratie, gebruikt u de para meter **configuratiepad** van cmdlets die een externe sessie maken, zoals de cmdlet [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) .

   Wanneer een sessie die gebruikmaakt van de sessie configuratie wordt gestart, wordt de Windows Power Shell 2,0-engine automatisch in de sessie geladen.

   Met de volgende opdracht wordt een sessie gestart op de Server01-computer die gebruikmaakt van de PS2-sessie configuratie. Met de opdracht wordt de sessie opgeslagen in de variabele $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Een achtergrond taak starten met de Windows Power Shell 2,0-engine

Als u een achtergrond taak wilt starten met de Windows Power Shell 2,0-engine, gebruikt u de para meter **PSVersion** van de cmdlet [Start-job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) .

Met de volgende opdracht wordt een achtergrond taak gestart met de Windows Power Shell 2,0-engine

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Zie [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs)voor meer informatie over achtergrond taken.
