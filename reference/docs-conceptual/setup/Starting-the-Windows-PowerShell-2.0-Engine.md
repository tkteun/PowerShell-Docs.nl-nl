---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: De Windows PowerShell 2.0-engine starten
ms.assetid: edafc2fa-7576-49c2-bbba-9336f4bcfc28
ms.openlocfilehash: 618745ff4865dd046acf46487e87c3ca0e324f95
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/25/2018
---
# <a name="starting-the-windows-powershell-20-engine"></a>De Windows PowerShell 2.0-engine starten

Deze sectie wordt uitgelegd hoe u start de Engine voor Windows PowerShell 2.0 op Windows 8.1, Windows Server 2012 R2, Windows 8 en Windows Server 2012, waaronder de Engine voor Windows PowerShell 2.0 en op andere systemen op welke Windows PowerShell 2.0, Windows PowerShell 3.0 en Windows PowerShell 4.0 zijn geïnstalleerd.

Windows PowerShell 4.0 en Windows PowerShell 3.0 zijn ontworpen voor achterwaartse compatibiliteit met Windows PowerShell 2.0. Cmdlets, providers-modules, modules en scripts die zijn geschreven voor Windows PowerShell 2.0 worden uitgevoerd in Windows PowerShell 4.0 en Windows PowerShell 3.0 ongewijzigd. Echter, vanwege een wijziging in de runtime activering-beleid in Microsoft .NET Framework 4, Windows PowerShell-host-programma's die zijn geschreven voor Windows PowerShell 2.0 en gecompileerd met Common Language Runtime (CLR) 2.0 kunnen niet worden uitgevoerd zonder aanpassingen in Windows PowerShell 3.0 of Windows PowerShell 4.0, worden gecompileerd met CLR-4.0. De Engine voor Windows PowerShell 2.0 is bedoeld om te worden alleen gebruikt als een bestaand script of hostprogramma kan niet worden uitgevoerd omdat deze niet compatibel met Windows PowerShell 4.0, Windows PowerShell 3.0 of Microsoft .NET Framework 4 is. Dergelijke gevallen worden zelden verwacht.

Veel programma waarvoor de Engine voor Windows PowerShell 2.0 wordt automatisch gestart. Deze instructies worden vermeld voor de zeldzame situaties waarin u moet de engine voor het handmatig wordt gestart.

## <a name="installing-and-enabling-required-programs"></a>Installeren en inschakelen van vereiste programma 's

Voordat u begint de Engine voor Windows PowerShell 2.0, schakel de Windows PowerShell 2.0-Engine en Microsoft .NET Framework 3.5 met Service Pack 1. Zie voor instructies [Windows PowerShell installeren](Installing-Windows-PowerShell.md).

Systemen waarop [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) of Windows Management Framework 3.0 zijn geïnstalleerd. alle vereiste onderdelen. Er is geen verdere configuratie vereist. Voor informatie over het installeren van [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881) of Windows Management Framework 3.0, Zie [Windows PowerShell installeren](Installing-Windows-PowerShell.md).

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Het starten van de Windows PowerShell 2.0-Engine

Wanneer u Windows PowerShell Start wordt standaard de nieuwste versie gestart. U start Windows PowerShell met de Windows PowerShell 2.0-Engine, de versie-parameter van PowerShell.exe te gebruiken. U kunt de opdracht uitvoeren bij een opdrachtprompt, met inbegrip van Windows PowerShell en Cmd.exe.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Een externe sessie starten met de Windows PowerShell 2.0-Engine

Als u wilt uitvoeren van de Windows PowerShell 2.0-Engine in een externe sessie, een sessieconfiguratie (ook wel bekend als een ' eindpunt') te maken op de externe computer die door de Engine voor Windows PowerShell 2.0 wordt geladen. De sessieconfiguratie van de wordt opgeslagen op de externe computer en kan worden gebruikt door een geautoriseerde gebruiker om sessies die gebruikmaken van de Windows PowerShell 2.0-Engine te maken.

Dit is een geavanceerde taak die gewoonlijk wordt uitgevoerd door een systeembeheerder.

De volgende procedure wordt de **PSVersion** parameter van de [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet voor het maken van een sessieconfiguratie die gebruikmaakt van de Windows PowerShell 2.0-Engine. U kunt ook de **PowerShellVersion** parameter van de [nieuw PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet voor het maken van een sessie-configuratiebestand voor een sessie die door de Engine voor Windows PowerShell 2.0 wordt geladen en u kunt de **PSVersion** parameter van de [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) parameter om de sessieconfiguratie van een voor het gebruik van de Windows PowerShell 2.0-Engine te wijzigen.

Zie voor meer informatie over configuratiebestanden sessie [about_Session_Configuration_Files](https://technet.microsoft.com/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8). Zie voor informatie over sessieconfiguraties, zoals setup en beveiliging, [about_Session_Configurations [v4]](https://technet.microsoft.com/library/a2fbe12a-350c-4d04-be50-24102824e3ab).

#### <a name="to-start-a-remote-windows-powershell-20-session"></a>Een externe Windows PowerShell 2.0-sessie starten

1. Voor het maken van een sessieconfiguratie waarvoor de Engine voor Windows PowerShell 2.0 gebruikt de **PSVersion** parameter van de [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) cmdlet met de waarde '2.0'. Deze opdracht uitvoeren op de computer op 'server-side'- of ontvangende kant van de verbinding.

   De volgende voorbeeldopdracht maakt de PS2-sessieconfiguratie op de computer Server01. Om deze opdracht uitvoert, start u Windows PowerShell 4.0 of Windows PowerShell 3.0 met de **als administrator uitvoeren** optie.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

2. Gebruik voor het maken van een sessie op de computer Server01 die gebruikmaakt van de sessieconfiguratie PS2 de **ConfigurationName** parameter van cmdlets die het maken van een externe sessie, zoals de [New-PSSession](https://technet.microsoft.com/library/76f6628c-054c-4eda-ba7a-a6f28daaa26f) cmdlet.

   Wanneer een sessie die gebruikmaakt van de sessieconfiguratie van de wordt gestart, wordt automatisch de Windows PowerShell 2.0-Engine geladen in de sessie.

   De volgende opdracht wordt een sessie op de computer Server01 die gebruikmaakt van de configuratie van de PS2-sessie gestart. De opdracht wordt de sessie opgeslagen in de variabele $s.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Een achtergrondtaak starten met de Windows PowerShell 2.0-Engine

Voor het starten van een achtergrondtaak met de Windows PowerShell 2.0-Engine, gebruiken de **PSVersion** parameter van de [starttaak](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) cmdlet.

De volgende opdracht begint een achtergrondtaak met de Windows PowerShell 2.0-Engine

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Zie voor meer informatie over achtergrondtaken [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).