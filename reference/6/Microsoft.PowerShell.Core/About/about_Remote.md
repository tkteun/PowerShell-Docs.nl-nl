---
description: Hierin wordt beschreven hoe u externe opdrachten uitvoert in Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: 04c297f849a30ddabecec98a5a2250b8d9b3fbfa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252253"
---
# <a name="about-remote"></a>Over externe

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u externe opdrachten uitvoert in Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

U kunt externe opdrachten uitvoeren op één computer of op meerdere computers door een tijdelijke of permanente verbinding te gebruiken. U kunt ook een interactieve sessie met één externe computer starten.

In dit onderwerp wordt een reeks voor beelden weer gegeven om u te laten zien hoe u verschillende typen externe opdrachten kunt uitvoeren. Nadat u deze basis opdrachten hebt uitgevoerd, raadpleegt u de Help-onderwerpen met een beschrijving van elke cmdlet die wordt gebruikt in deze opdrachten. In de onderwerpen vindt u de details en wordt uitgelegd hoe u de opdrachten kunt aanpassen om te voldoen aan uw behoeften.

Opmerking: als u externe communicatie met Power shell wilt gebruiken, moeten de lokale en externe computers worden geconfigureerd voor externe toegang. Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie.

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>EEN INTERACTIEVE SESSIE STARTEN (ENTER-PSSESSION)

De eenvoudigste manier om externe opdrachten uit te voeren is het starten van een interactieve sessie met een externe computer.

Wanneer de sessie wordt gestart, worden de opdrachten die u typt op de externe computer uitgevoerd, net zoals u ze rechtstreeks op de externe computer hebt getypt. U kunt verbinding maken met slechts één computer in elke interactieve sessie.

Als u een interactieve sessie wilt starten, gebruikt u de cmdlet Enter-PSSession. Met de volgende opdracht wordt een interactieve sessie gestart met de Server01-computer:

```powershell
Enter-PSSession Server01
```

De opdracht prompt wordt gewijzigd om aan te geven dat u verbinding hebt met de Server01-computer.

```
Server01\PS>
```

U kunt nu opdrachten op de Server01-computer typen.

Als u de interactieve sessie wilt beëindigen, typt u:

```powershell
Exit-PSSession
```

Zie Enter-PSSession voor meer informatie.

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>CMDLETS GEBRUIKEN DIE DE PARA METER COMPUTERNAME HEBBEN OM EXTERNE GEGEVENS OP TE HALEN

Verschillende cmdlets hebben de para meter ComputerName waarmee u objecten van externe computers kunt ophalen.

Omdat deze cmdlets geen gebruikmaken van op WS-Management gebaseerde externe communicatie met Power shell, kunt u de para meter ComputerName van deze cmdlets gebruiken op elke computer waarop Power shell wordt uitgevoerd. De computers hoeven niet te worden geconfigureerd voor externe communicatie met Power shell en de computers hoeven niet te voldoen aan de systeem vereisten voor externe communicatie.

De volgende cmdlets hebben de para meter computername:

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

Met de volgende opdracht worden bijvoorbeeld de services op de externe computer Server01 opgehaald:

```powershell
Get-Service -ComputerName Server01
```

Doorgaans hebben cmdlets die ondersteuning bieden voor externe toegang zonder speciale configuratie een **ComputerName** -para meter en geen **sessie** parameter hebben. Als u deze cmdlets wilt vinden in uw sessie, typt u:

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>EEN EXTERNE OPDRACHT UITVOEREN

Als u andere opdrachten op externe computers wilt uitvoeren, gebruikt u de cmdlet Invoke-Command.

Als u één opdracht of enkele niet-gerelateerde opdrachten wilt uitvoeren, gebruikt u de para meter ComputerName van Invoke-Command om de externe computers op te geven. Gebruik de para meter script Block om de opdracht op te geven.

Met de volgende opdracht wordt bijvoorbeeld een Get-Culture-opdracht uitgevoerd op de computer Server01.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

De para meter ComputerName is ontworpen voor situaties waarin u één opdracht of meerdere niet-gerelateerde opdrachten op een of meer computers uitvoert. Gebruik de para meter Session om een permanente verbinding met een externe computer tot stand te brengen.

## <a name="how-to-create-a-persistent-connection-pssession"></a>EEN PERMANENTE VERBINDING MAKEN (PSSESSION)

Wanneer u de para meter ComputerName van de cmdlet Invoke-Command gebruikt, brengt Windows Power shell een verbinding tot stand voor de opdracht. Vervolgens wordt de verbinding gesloten wanneer de opdracht is voltooid. Alle variabelen of functies die in de opdracht zijn gedefinieerd, gaan verloren.

Als u een permanente verbinding met een externe computer wilt maken, gebruikt u de cmdlet New-PSSession. Met de volgende opdracht maakt u bijvoorbeeld PSSessions op de Server01-en Server02-computers, waarna de PSSessions wordt opgeslagen in de variabele $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>OPDRACHTEN UITVOEREN IN EEN PSSESSION

Met een PSSession kunt u een reeks externe opdrachten uitvoeren die gegevens delen, zoals functies, aliassen en de waarden van variabelen. Voor het uitvoeren van opdrachten in een PSSession gebruikt u de para meter Session van de cmdlet Invoke-Command.

De volgende opdracht gebruikt bijvoorbeeld de cmdlet Invoke-Command om een Get-Process opdracht uit te voeren in de PSSessions op de computers Server01 en Server02.
Met de opdracht worden de processen in een $p variabele in elke PSSession opgeslagen.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

Omdat de PSSession een permanente verbinding gebruikt, kunt u een andere opdracht uitvoeren in dezelfde PSSession die gebruikmaakt van de variabele $p. Met de volgende opdracht wordt het aantal processen geteld dat is opgeslagen in $p.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>EEN EXTERNE OPDRACHT UITVOEREN OP MEERDERE COMPUTERS

Als u een externe opdracht op meerdere computers wilt uitvoeren, typt u alle computer namen in de waarde van de para meter ComputerName van invoke-Command. Scheid de namen met komma's.

Met de volgende opdracht wordt bijvoorbeeld een Get-Culture-opdracht uitgevoerd op drie computers:

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

U kunt ook een opdracht uitvoeren in meerdere PSSessions. Met de volgende opdrachten maakt u PSSessions op de Server01-, Server02-en Server03-computers en voert u vervolgens een Get-Culture opdracht uit in elk van de PSSessions.

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

Als u de lokale computer lijst van computers wilt opnemen, typt u de naam van de lokale computer, typt u een punt (.) of typt u localhost.

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>EEN SCRIPT UITVOEREN OP EXTERNE COMPUTERS

Als u een lokaal script op externe computers wilt uitvoeren, gebruikt u de para meter FilePath van invoke-Command.

Met de volgende opdracht wordt bijvoorbeeld het Sample.ps1 script uitgevoerd op de computers S1 en S2:

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

De resultaten van het script worden teruggestuurd naar de lokale computer. U hoeft geen bestanden te kopiëren.

## <a name="how-to-stop-a-remote-command"></a>EEN EXTERNE OPDRACHT STOPPEN

Als u een opdracht wilt onderbreken, drukt u op CTRL + C. De Interrupt-aanvraag wordt door gegeven aan de externe computer waarop de externe opdracht wordt beëindigd.

## <a name="for-more-information"></a>VOOR MEER INFORMATIE

- Zie [about_Remote_Requirements](about_Remote_Requirements.md)voor meer informatie over de systeem vereisten voor externe toegang.

- Zie [about_Remote_Output](about_Remote_Output.md)voor hulp bij het format teren van externe uitvoer.

- Zie [about_Remote_FAQ](about_Remote_FAQ.md)voor meer informatie over de werking van externe gegevens, speciale configuraties, beveiligings problemen en andere veelgestelde vragen.

- Zie about_Remote_Troubleshooting voor hulp bij het oplossen van externe fouten.

- Zie [about_PSSessions](about_PSSessions.md)voor meer informatie over PSSessions en permanente verbindingen.

- Zie [about_Jobs](about_Jobs.md)voor meer informatie over Power shell-achtergrond taken.

## <a name="keywords"></a>WOORD

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
