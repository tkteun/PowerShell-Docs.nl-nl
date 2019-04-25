---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Processen beheren met proces-cmdlets
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: 741a3464bce6284c4933384398c4e9ddcca2572c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058706"
---
# <a name="managing-processes-with-process-cmdlets"></a>Processen beheren met proces-cmdlets

U kunt de proces-cmdlets in Windows PowerShell gebruiken voor het beheren van lokale en externe processen in Windows PowerShell.

## <a name="getting-processes-get-process"></a>Processen ophalen (Get-Process)

Uitvoeren als u de processen die op de lokale computer worden uitgevoerd, een **Get-Process** zonder parameters.

U kunt bepaalde processen krijgen door hun procesnamen of proces-id's op te geven. De volgende opdracht wordt het actieve proces:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Hoewel het normaal dat cmdlets voor het geen gegevens ophalen in sommige gevallen, als u een proces door de proces-id, **Get-Process** een fout wordt gegenereerd als er geen overeenkomsten gevonden omdat het gebruikelijke doel is om op te halen van een bekende proces dat wordt uitgevoerd. Als er geen proces met deze Id, is het waarschijnlijk dat de Id onjuist is of het proces van belang is al afgesloten:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

U kunt de parameter Name van de cmdlet Get-Process gebruiken om op te geven van een subset van de processen op basis van de procesnaam. De parameter Name kunnen meerdere namen in een door komma's gescheiden lijst en deze ondersteunt het gebruik van jokertekens gebruikt, zodat u de naam van patronen kunt typen.

Bijvoorbeeld, haalt de volgende opdracht proces waarvan de namen beginnen met "ex."

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Omdat de System.Diagnostics.Process .NET-klasse de basis voor Windows PowerShell-processen vormt, volgt enkele van de conventies die worden gebruikt door System.Diagnostics.Process. Een van de overeenkomsten is de procesnaam voor een uitvoerbaar bestand bevat nooit de ".exe' aan het einde van de naam van uitvoerbaar bestand.

**Get-Process** accepteert ook meerdere waarden voor de parameter Name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

U kunt de parameter ComputerName van Get-Process gebruiken om op te halen van processen op externe computers. Bijvoorbeeld, de volgende opdracht uit de PowerShell-processen opgehaald op de lokale computer (vertegenwoordigd door 'localhost') en op twee externe computers.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

De computernamen van de zijn niet zichtbaar zijn in deze weer te geven, maar ze worden opgeslagen in de eigenschap computernaam van de proces-objecten waarmee Get-Process worden geretourneerd. De volgende opdracht maakt gebruik van de cmdlet Format-Table om weer te geven van de proces-ID, de procesnaam en de computernaam (ComputerName) eigenschappen van de proces-objecten.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

De eigenschap MachineName met deze opdracht complexere toegevoegd aan de standaard Get-Process-weergave.

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

## <a name="stopping-processes-stop-process"></a>Beëindigen van processen (Stop-proces)

Windows PowerShell biedt u flexibiliteit voor processen weergeven, maar hoe zit het stoppen van een proces?

De **Stop-Process** cmdlet gebruikt een naam of Id om op te geven van een proces dat u wilt stoppen. De mogelijkheid om te beëindigen van processen, is afhankelijk van uw machtigingen. Bepaalde processen kunnen niet worden gestopt. Bijvoorbeeld, als u probeert om de niet-actieve proces te stoppen, krijgt u een fout opgetreden:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

U kunt ook afdwingen dat met u wordt gevraagd de **bevestigen** parameter. Deze parameter is vooral handig als u een jokerteken gebruiken bij het opgeven van de procesnaam, omdat u mogelijk per ongeluk dat overeenkomt met bepaalde processen die u niet wilt stoppen:

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

Bewerken van een complex proces is mogelijk met behulp van enkele van de cmdlets filteren-object. Omdat een procesobject een reageert-eigenschap die is ingesteld op true heeft wanneer deze niet meer reageert, kunt u voorkomen dat alle responsieve toepassingen met de volgende opdracht:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

U kunt dezelfde benadering gebruiken in andere gevallen. Stel bijvoorbeeld dat een secundaire melding gebied toepassing automatisch wordt uitgevoerd wanneer gebruikers een andere toepassing starten. U merkt mogelijk dat deze niet correct in Terminal Services-sessies werkt, maar u nog steeds wilt behouden blijft in sessies die worden uitgevoerd op de fysieke computer-console. Sessies die zijn verbonden met het bureaublad van de fysieke computer altijd hebben een sessie-ID van 0 is, kunt u voorkomen dat alle exemplaren van het proces dat zich in andere sessies met **Where-Object** en het proces **SessionId** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

De cmdlet Stop-Process beschikt niet over een parameter ComputerName. Als u wilt een opdracht voor stoppen proces uitvoeren op een externe computer, moet u daarom, gebruikt u de cmdlet Invoke-Command. Bijvoorbeeld, als u wilt stoppen de PowerShell-proces op de externe computer Server01, typt u:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Alle andere Windows PowerShell-sessies te stoppen

Het is mogelijk soms handig kunnen stop alle actieve Windows PowerShell-sessies dan de huidige sessie. Als een sessie te veel resources worden gebruikt, of niet toegankelijk is (deze kan worden uitgevoerd op afstand of in een andere bureaublad-sessiehost), kunt u mogelijk niet rechtstreeks te stoppen. Als u wilt alle actieve sessies te stoppen, maar kan de huidige sessie worden beëindigd in plaats daarvan.

Elke Windows PowerShell-sessie heeft een omgevingsvariabele PID met de Id van de Windows PowerShell-proces. U kunt de $PID op basis van de Id van elke sessie controleren en alleen Windows PowerShell-sessies met een andere id op. De volgende opdracht in de pijplijn gebruikt hiervoor en retourneert de lijst van beëindigde sessies (vanwege het gebruik van de **PassThru** parameter):

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

## <a name="starting-debugging-and-waiting-for-processes"></a>Starten, foutopsporing en wachten op processen

Windows PowerShell ook wordt geleverd met cmdlets voor het starten (of opnieuw starten), een proces voor foutopsporing en wachten op een proces is voltooid voordat u een opdracht uitvoert. Zie het help-onderwerp van de cmdlet voor elke cmdlet voor informatie over deze cmdlets.

## <a name="see-also"></a>Zie ook

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Wait-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
