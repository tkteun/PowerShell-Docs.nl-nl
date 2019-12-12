---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Processen beheren met proces-cmdlets
ms.openlocfilehash: 0962290327a02141f582acdf168143dee14ac60a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030189"
---
# <a name="managing-processes-with-process-cmdlets"></a>Processen beheren met proces-cmdlets

U kunt de proces-cmdlets in Windows Power shell gebruiken voor het beheren van lokale en externe processen in Windows Power shell.

## <a name="getting-processes-get-process"></a>Processen ophalen (Get-proces)

Als u de processen wilt ophalen die worden uitgevoerd op de lokale computer, voert u een **Get-process** zonder para meters uit.

U kunt bepaalde processen verkrijgen door hun proces namen of proces-Id's op te geven. Met de volgende opdracht wordt het inactief proces opgehaald:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Hoewel het normaal is voor cmdlets om geen gegevens in bepaalde situaties te retour neren, wordt bij het opgeven van een proces door de proces **-** process een fout gegenereerd als er geen overeenkomsten worden gevonden, omdat het gebruikelijk is om een bekend actief proces op te halen. Als er geen proces met die id is, is het waarschijnlijk dat de id onjuist is of dat het proces van belang al is afgesloten:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

U kunt de para meter name van de cmdlet Get-process gebruiken om een subset van processen op te geven op basis van de proces naam. De para meter name kan meerdere namen in een lijst met door komma's gescheiden waarden hebben en ondersteunt het gebruik van joker tekens, zodat u naam patronen kunt typen.

Met de volgende opdracht wordt bijvoorbeeld proces uitgevoerd waarvan de naam begint met ' ex '.

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Omdat de klasse .NET System. Diagnostics. process de basis is voor Windows Power shell-processen, worden enkele van de conventies gevolgd door System. Diagnostics. process. Een van deze conventies is dat de proces naam voor een uitvoerbaar bestand nooit de '. exe ' bevat aan het einde van de naam van het uitvoer bare bestand.

**Get-process** accepteert ook meerdere waarden voor de para meter name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

U kunt de para meter ComputerName van Get-process gebruiken om processen op externe computers op te halen. Met de volgende opdracht worden bijvoorbeeld de Power shell-processen op de lokale computer (aangeduid door ' localhost ') en op twee externe computers.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

De computer namen zijn niet duidelijk in deze weer gave, maar ze worden opgeslagen in de eigenschap MachineName van de proces objecten die ophalen-process retourneert. De volgende opdracht maakt gebruik van de indeling-tabel-cmdlet om de eigenschappen proces-ID, naam van de proces naam en MachineName (ComputerName) van de proces objecten weer te geven.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

Met deze complexere opdracht wordt de eigenschap MachineName toegevoegd aan de standaard Get-process-weer gave.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Processen stoppen (Stop proces)

Windows Power shell biedt u flexibiliteit voor het weer geven van processen, maar over het stoppen van een proces?

Voor de cmdlet **Stop-process** wordt een naam of id gebruikt om een proces op te geven dat u wilt stoppen. De mogelijkheid om processen te stoppen, is afhankelijk van uw machtigingen. Sommige processen kunnen niet worden gestopt. Als u bijvoorbeeld probeert het inactieve proces te stoppen, krijgt u een fout melding:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

U kunt er ook voor zorgen dat u wordt gevraagd om te vragen met de para meter **confirm** . Deze para meter is met name handig als u een Joker teken gebruikt voor het opgeven van de naam van het proces, omdat u per ongeluk een aantal processen wilt afleiden die u niet wilt stoppen:

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

Het maken van complexe processen is mogelijk met enkele van de object Filter-cmdlets. Omdat een proces object een reagerende eigenschap heeft die waar is wanneer deze niet meer reageert, kunt u alle niet-reagerende toepassingen stoppen met de volgende opdracht:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

U kunt dezelfde benadering gebruiken in andere situaties. Stel bijvoorbeeld dat een tweede toepassing voor het systeemvak automatisch wordt uitgevoerd wanneer gebruikers een andere toepassing starten. Het kan voor komen dat dit niet goed werkt in Terminal Services sessies, maar dat u deze nog steeds wilt behouden in sessies die worden uitgevoerd op de fysieke computer console. Sessies die zijn verbonden met het bureau blad van de fysieke computer hebben altijd een sessie-ID van 0, zodat u alle exemplaren van het proces dat zich in andere sessies bevindt, kunt stoppen met behulp van **where-object** en het proces, **SessionId**:

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

De cmdlet stop-Process heeft geen ComputerName-para meter. Daarom moet u de cmdlet invoke-opdracht gebruiken om de opdracht stop process uit te voeren op een externe computer. Als u bijvoorbeeld het Power Shell-proces op de externe computer Server01 wilt stoppen, typt u:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Alle andere Windows Power shell-sessies stoppen

Het kan af en toe handig zijn om alle actieve Windows Power shell-sessies te stoppen, behalve de huidige sessie. Als een sessie te veel bronnen gebruikt of niet toegankelijk is (mogelijk op afstand of in een andere bureaublad sessie), is het mogelijk dat u deze niet rechtstreeks kunt stoppen. Als u probeert alle actieve sessies te stoppen, kan de huidige sessie echter worden beëindigd.

Elke Windows Power shell-sessie heeft een omgevings variabele die de id van het Windows Power Shell-proces bevat. U kunt de $PID controleren op basis van de id van elke sessie en alleen Windows Power shell-sessies met een andere id beëindigen. De volgende opdracht pijp lijn doet dit en retourneert de lijst met beëindigde sessies (vanwege het gebruik van de para meter **PassThru** ):

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a>Starten, fouten opsporen en wachten op processen

Windows Power shell wordt ook geleverd met cmdlets om een proces te starten (of opnieuw te starten), fouten op te sporen en te wachten totdat een proces is voltooid voordat een opdracht wordt uitgevoerd. Zie het Help-onderwerp voor cmdlets voor elke cmdlet voor meer informatie over deze cmdlets.

## <a name="see-also"></a>Zie ook

- [Get-process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stoppen-proces [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Start-process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Wacht proces](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Debug-proces](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-opdracht](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
