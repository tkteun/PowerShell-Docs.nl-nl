---
description: Beschrijft hoe u externe opdrachten in PowerShell kunt uitvoeren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: ad7ccd24c6e9642283e4ea9d1fb04bac40a6b11b
ms.sourcegitcommit: 2b1059dd18ae4ec4f350479185c156748649b4ab
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/14/2021
ms.locfileid: "107390111"
---
# <a name="about-remote"></a>Over extern

## <a name="short-description"></a>KORTE BESCHRIJVING
Beschrijft hoe u externe opdrachten in PowerShell kunt uitvoeren.

## <a name="long-description"></a>LANGE BESCHRIJVING

U kunt externe opdrachten uitvoeren op één computer of op meerdere computers met behulp van een tijdelijke of permanente verbinding. U kunt ook een interactieve sessie starten met één externe computer.

In dit onderwerp vindt u een reeks voorbeelden die u laten zien hoe u verschillende typen externe opdrachten kunt uitvoeren. Nadat u deze basisopdrachten hebt geprobeerd, leest u de Help-onderwerpen waarin elke cmdlet wordt beschreven die in deze opdrachten wordt gebruikt. In de onderwerpen vindt u de details en wordt uitgelegd hoe u de opdrachten kunt aanpassen aan uw behoeften.

Opmerking: als u externe toegang van PowerShell wilt gebruiken, moeten de lokale en externe computers zijn geconfigureerd voor externe toegang. Zie voor meer informatie [about_Remote_Requirements](about_Remote_Requirements.md).

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>EEN INTERACTIEVE SESSIE STARTEN (ENTER-PSSESSION)

De eenvoudigste manier om externe opdrachten uit te voeren, is door een interactieve sessie te starten met een externe computer.

Wanneer de sessie wordt gestart, worden de opdrachten die u typt uitgevoerd op de externe computer, net zoals u ze rechtstreeks op de externe computer hebt getypt. U kunt in elke interactieve sessie verbinding maken met slechts één computer.

Als u een interactieve sessie wilt starten, gebruikt u Enter-PSSession cmdlet . Met de volgende opdracht start u een interactieve sessie met de computer Server01:

```powershell
Enter-PSSession Server01
```

De opdrachtprompt wordt gewijzigd om aan te geven dat u bent verbonden met de computer Server01.

```
Server01\PS>
```

U kunt nu opdrachten typen op de computer Server01.

Typ het volgende om de interactieve sessie te beëindigen:

```powershell
Exit-PSSession
```

Zie Enter-PSSession voor meer informatie.

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>CMDLETS GEBRUIKEN DIE EEN COMPUTERNAME-PARAMETER HEBBEN OM EXTERNE GEGEVENS OP TE HALEN

Verschillende cmdlets hebben een ComputerName parameter waarmee u objecten van externe computers.

Omdat deze cmdlets geen op WS Management gebaseerde PowerShell-remoting gebruiken, kunt u de parameter ComputerName van deze cmdlets gebruiken op elke computer met PowerShell. De computers hoeft niet te worden geconfigureerd voor het op de markt houden van powershell en de computers moeten niet voldoen aan de systeemvereisten voor remoting.

De volgende cmdlets hebben een ComputerName-parameter:

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

Met de volgende opdracht worden bijvoorbeeld de services op de externe server01-computer opgeslagen:

```powershell
Get-Service -ComputerName Server01
```

Cmdlets die ondersteuning bieden voor remoting zonder speciale configuratie hebben doorgaans een **ComputerName-parameter** en hebben geen **sessieparameter.** Als u wilt zoeken naar deze cmdlets in uw sessie, typt u:

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>EEN EXTERNE OPDRACHT UITVOEREN

Als u andere opdrachten wilt uitvoeren op externe computers, gebruikt u Invoke-Command cmdlet .

Als u één opdracht of een paar niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de parameter ComputerName van Invoke-Command om de externe computers op te geven. Gebruik de parameter ScriptBlock om de opdracht op te geven.

Met de volgende opdracht wordt bijvoorbeeld een Get-Culture uitgevoerd op de computer Server01.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

De ComputerName parameter is ontworpen voor situaties waarin u één opdracht of een aantal niet-gerelateerde opdrachten op een of meer computers uitvoeren. Als u een permanente verbinding met een externe computer tot stand wilt brengen, gebruikt u de parameter Sessie.

## <a name="how-to-create-a-persistent-connection-pssession"></a>EEN PERMANENTE VERBINDING MAKEN (PSSESSION)

Wanneer u de parameter ComputerName van de cmdlet Invoke-Command, maakt Windows PowerShell alleen een verbinding voor de opdracht. Vervolgens wordt de verbinding gesloten wanneer de opdracht is voltooid. Variabelen of functies die zijn gedefinieerd in de opdracht gaan verloren.

Als u een permanente verbinding met een externe computer wilt maken, gebruikt u New-PSSession cmdlet . Met de volgende opdracht maakt u bijvoorbeeld PSSessions op de computers Server01 en Server02 en slaat u de PSSessions vervolgens op in de $s variabele.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>OPDRACHTEN UITVOEREN IN EEN PSSESSION

Met een PSSession kunt u een reeks externe opdrachten uitvoeren die gegevens delen, zoals functies, aliassen en de waarden van variabelen. Als u opdrachten wilt uitvoeren in een PSSession, gebruikt u de parameter Session van Invoke-Command cmdlet.

Met de volgende opdracht wordt bijvoorbeeld de cmdlet Invoke-Command gebruikt om een Get-Process-opdracht uit te voeren in de PSSessions op de computers Server01 en Server02.
De opdracht slaat de processen op in een $p variabele in elke PSSession.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

Omdat de PSSession een permanente verbinding gebruikt, kunt u een andere opdracht uitvoeren in dezelfde PSSession die gebruikmaakt van de $p variabele. Met de volgende opdracht wordt het aantal processen geteld dat is opgeslagen in $p.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>EEN EXTERNE OPDRACHT UITVOEREN OP MEERDERE COMPUTERS

Als u een externe opdracht wilt uitvoeren op meerdere computers, typt u alle computernamen in de waarde van de parameter ComputerName van Invoke-Command. Scheid de namen met komma's.

Met de volgende opdracht wordt bijvoorbeeld een Get-Culture uitgevoerd op drie computers:

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

U kunt ook een opdracht uitvoeren in meerdere PSSessions. Met de volgende opdrachten maakt u PSSessions op de computers Server01, Server02 en Server03 en voert u vervolgens een Get-Culture-opdracht uit in elk van de PSSessions.

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

Als u de lokale computerlijst met computers wilt opnemen, typt u de naam van de lokale computer, typt u een punt (.) of typt u 'localhost'.

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>EEN SCRIPT UITVOEREN OP EXTERNE COMPUTERS

Als u een lokaal script wilt uitvoeren op externe computers, gebruikt u de parameter FilePath van Invoke-Command.

Met de volgende opdracht wordt bijvoorbeeld het Sample.ps1 uitgevoerd op de S1- en S2-computers:

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

De resultaten van het script worden geretourneerd naar de lokale computer. U hoeft geen bestanden te kopiëren.

## <a name="how-to-stop-a-remote-command"></a>EEN EXTERNE OPDRACHT STOPPEN

Als u een opdracht wilt onderbreken, drukt u op CTRL +C. De interruptaanvraag wordt doorgegeven aan de externe computer waar de externe opdracht wordt beëindigd.

## <a name="for-more-information"></a>VOOR MEER INFORMATIE

- Zie voor meer informatie over de systeemvereisten voor remoting [about_Remote_Requirements.](about_Remote_Requirements.md)

- Zie voor hulp bij het opmaken van [externe uitvoer about_Remote_Output.](about_Remote_Output.md)

- Zie voor meer informatie over hoe externe toegang werkt, het beheren van externe gegevens, speciale configuraties, beveiligingsproblemen en andere veelgestelde [about_Remote_FAQ.](about_Remote_FAQ.md)

- Zie voor hulp bij het oplossen van fouten bij het oplossen [van about_Remote_Troubleshooting.](about_Remote_Troubleshooting.md)

- Zie voor meer informatie over PSSessions en permanente verbindingen [about_PSSessions.](about_PSSessions.md)

- Zie voor meer informatie over PowerShell-achtergrondtaken [about_Jobs.](about_Jobs.md)

## <a name="keywords"></a>Zoekwoorden

about_Remoting

## <a name="see-also"></a>ZIE OOK

[about_PSSessions](about_PSSessions.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_FAQ](about_Remote_FAQ.md)

[about_Remote_TroubleShooting](about_Remote_TroubleShooting.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-opdracht](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

