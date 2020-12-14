---
description: Hierin wordt beschreven hoe u de uitvoer van externe opdrachten kunt interpreteren en opmaken.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 476afc62089795d22002ece05c7ce2bf53994237
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705312"
---
# <a name="about-remote-output"></a>Over externe uitvoer

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u de uitvoer van externe opdrachten kunt interpreteren en opmaken.

## <a name="long-description"></a>LANGE BESCHRIJVING

De uitvoer van een opdracht die is uitgevoerd op een externe computer kan eruitzien als uitvoer van dezelfde opdracht die wordt uitgevoerd op een lokale computer, maar er zijn een aantal belang rijke verschillen.

In dit onderwerp wordt uitgelegd hoe u de uitvoer van opdrachten die op externe computers worden uitgevoerd, kunt interpreteren, opmaken en weer geven.

## <a name="displaying-the-computer-name"></a>DE COMPUTER NAAM WORDT WEER GEGEVEN

Wanneer u de cmdlet Invoke-Command gebruikt om een opdracht uit te voeren op een externe computer, retourneert de opdracht een object dat de naam bevat van de computer die de gegevens heeft gegenereerd. De naam van de externe computer wordt opgeslagen in de eigenschap PSComputerName.

Voor veel opdrachten wordt de PSComputerName standaard weer gegeven. Met de volgende opdracht wordt bijvoorbeeld een Get-Culture-opdracht uitgevoerd op twee externe computers: Server01 en Server02. De uitvoer, die hieronder wordt weer gegeven, bevat de namen van de externe computers waarop de opdracht is uitgevoerd.

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

U kunt de para meter HideComputerName van Invoke-Command gebruiken om de eigenschap PSComputerName te verbergen. Deze para meter is bedoeld voor opdrachten voor het verzamelen van gegevens van slechts één externe computer.

Met de volgende opdracht wordt een Get-Culture-opdracht uitgevoerd op de externe computer Server01. De para meter HideComputerName wordt gebruikt om de eigenschap PSComputerName en gerelateerde eigenschappen te verbergen.

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

U kunt ook de eigenschap PSComputerName weer geven als deze niet standaard wordt weer gegeven.

De volgende opdrachten gebruiken bijvoorbeeld de cmdlet Format-Table om de eigenschap PSComputerName toe te voegen aan de uitvoer van een externe Get-Date opdracht.

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a>DE EIGENSCHAP MACHINENAME WEER GEVEN

Verschillende cmdlets, waaronder Get-proces, Get-service en Get-EventLog, hebben een ComputerName-para meter waarmee de objecten op een externe computer worden opgehaald.
Deze cmdlets gebruiken geen externe communicatie van Power shell, dus u kunt ze zelfs gebruiken op computers die niet zijn geconfigureerd voor externe communicatie in Windows Power shell.

De objecten die met deze cmdlets worden opgehaald, bevatten de naam van de externe computer in de eigenschap MachineName. (Deze objecten hebben geen eigenschap PSComputerName.)

Met deze opdracht wordt bijvoorbeeld het Power Shell-proces op de externe computers Server01 en Server02. De standaard weergave bevat niet de eigenschap MachineName.

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

U kunt de cmdlet Format-Table gebruiken om de eigenschap MachineName van de proces objecten weer te geven.

Met de volgende opdracht worden bijvoorbeeld de processen opgeslagen in de variabele $p en vervolgens een pijplijn operator (|) gebruikt om de processen in $p naar de Format-Table opdracht te verzenden. De opdracht gebruikt de eigenschaps parameter van Format-Table om de eigenschap MachineName op te geven in de weer gave.

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

Met de volgende complexe opdracht wordt de eigenschap MachineName toegevoegd aan de standaard proces weergave. Hash-tabellen worden gebruikt om berekende eigenschappen op te geven. Gelukkig hoeft u deze niet te begrijpen om het te gebruiken.

(Houd er rekening mee dat de apostroffen ['] het voortzettings teken is.)

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a>GEDESERIALISEERD OBJECTEN

Wanneer u externe opdrachten uitvoert die uitvoer genereren, wordt de uitvoer van de opdracht naar de lokale computer verzonden via het netwerk.

Omdat de meeste Live Microsoft .NET Framework-objecten (zoals de objecten die Power shell-cmdlets retour neren) niet via het netwerk kunnen worden verzonden, zijn de live-objecten ' geserialiseerd '. Met andere woorden, de live-objecten worden geconverteerd naar XML-representaties van het object en de bijbehorende eigenschappen. Vervolgens wordt het geserialiseerde XML-object via het netwerk verzonden.

Op de lokale computer ontvangt Power shell het geserialiseerde XML-object en wordt het ' deserialiseren ' door het XML-object te converteren naar een standaard .NET Framework-object.

Het gedeserialiseerd object is echter geen live-object. Het is een moment opname van het object op het moment dat het is geserialiseerd en bevat eigenschappen, maar geen methoden. U kunt deze objecten in Power shell gebruiken en beheren, zoals het door geven van de objecten in pijp lijnen, het weer geven van geselecteerde eigenschappen en het opmaken ervan.

De meeste gedeserialiseerd objecten worden automatisch opgemaakt voor weer gave door vermeldingen in de XML-bestanden van Types.ps1XML of Format.ps1. Het is echter mogelijk dat de lokale computer geen indelings bestanden heeft voor alle gedeserialiseerd objecten die op een externe computer zijn gegenereerd. Wanneer objecten niet zijn opgemaakt, worden alle eigenschappen van elk object weer gegeven in de-console in een lijst met stromen.

Wanneer objecten niet automatisch worden opgemaakt, kunt u de opmaak-cmdlets, zoals Format-Table of opmaak lijst, gebruiken om de geselecteerde eigenschappen in te delen en weer te geven. U kunt ook de cmdlet Out-GridView gebruiken om de objecten in een tabel weer te geven.

Als u een opdracht uitvoert op een externe computer die cmdlets gebruikt die u niet op uw lokale computer hebt, zijn de objecten die de opdracht retourneert mogelijk niet correct ingedeeld omdat u niet beschikt over de indeling van de bestanden voor die objecten op uw computer. Gebruik de cmdlets Get-FormatData en Export-FormatData om gegevens op te halen van een andere computer.

Sommige object typen, zoals DirectoryInfo-objecten en GUID'S, worden weer omgezet in live-objecten wanneer ze worden ontvangen. Voor deze objecten is geen speciale verwerking of opmaak vereist.

## <a name="ordering-the-results"></a>DE RESULTATEN BEST ELLEN

De volg orde van de computer namen in de para meter ComputerName van cmdlets bepaalt de volg orde waarin Power shell verbinding maakt met de externe computers. De resultaten worden echter weer gegeven in de volg orde waarin de lokale computer deze ontvangt. Dit kan een andere volg orde zijn.

Gebruik de cmdlet Sort-Object om de volg orde van de resultaten te wijzigen. U kunt sorteren op de eigenschap PSComputerName of MachineName. U kunt ook sorteren op een andere eigenschap van het object, zodat de resultaten van verschillende computers worden omgevallen.

## <a name="see-also"></a>ZIE OOK

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table)

[Get-Process](xref:Microsoft.PowerShell.Management.Get-Process)

[Get-Service](xref:Microsoft.PowerShell.Management.Get-Service)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object)

