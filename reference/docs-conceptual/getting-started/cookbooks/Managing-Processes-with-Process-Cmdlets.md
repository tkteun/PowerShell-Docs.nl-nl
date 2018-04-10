---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Processen beheren met proces-cmdlets
ms.assetid: 5038f612-d149-4698-8bbb-999986959e31
ms.openlocfilehash: d6d7daa810dce2d476566e4d30f03cc95bf730e6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="managing-processes-with-process-cmdlets"></a>Processen beheren met proces-cmdlets

U kunt de proces-cmdlets in Windows PowerShell gebruiken voor het beheren van lokale en externe processen in Windows PowerShell.

## <a name="getting-processes-get-process"></a>Processen ophalen (Get-Process)

Uitvoeren als u de processen die worden uitgevoerd op de lokale computer, een **Get-Process** zonder parameters.

U kunt bepaalde processen ophalen door hun procesnamen of proces-id's te geven. De volgende opdracht wordt het actieve proces:

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

Hoewel het normaal voor cmdlets retourneren geen gegevens in sommige gevallen is wanneer u een proces met de proces-id opgeeft **Get-Process** wordt een fout gegenereerd als het geen overeenkomsten gevonden omdat het gebruikelijke doel voor het ophalen van een bekende proces dat wordt uitgevoerd. Als er geen proces met die Id, is het waarschijnlijk dat de Id onjuist is of het proces van belang is al afgesloten:

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

De parameter Name van de cmdlet Get-Process kunt u een subset van de processen op basis van de procesnaam opgeven. De parameter Name kunt meerdere namen in een door komma's gescheiden lijst en daarmee het gebruik van jokertekens, zodat u kunt bestandsnaampatronen typen.

Bijvoorbeeld de volgende opdracht opgehaald proces waarvan de naam begint met 'ex'.

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

Omdat de klasse .NET System.Diagnostics.Process de basis voor Windows PowerShell-processen vormt, volgt een aantal van de overeenkomsten die wordt gebruikt door System.Diagnostics.Process. Een van deze conventies is de procesnaam voor een uitvoerbaar bestand bevat nooit de '.exe' aan het einde van het uitvoerbare bestand.

**Get-Process** ook accepteert meerdere waarden voor de parameter Name.

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

U kunt de parameter ComputerName van Get-Process gebruiken om op te halen van processen op externe computers. Bijvoorbeeld, opgehaald van de PowerShell-processen op de lokale computer (vertegenwoordigd door 'localhost') in de volgende opdracht en op twee externe computers.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

De computernamen zijn niet duidelijk in deze informatie wilt weergeven, maar ze worden opgeslagen in de eigenschap computernaam van de proces-objecten die Get-Process retourneert. De volgende opdracht maakt gebruik van de cmdlet Format-Table de proces-ID, de procesnaam en de computernaam (ComputerName) wilt weergeven van de proces-objecten.

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

De eigenschap MachineName deze complexere opdracht toegevoegd aan de standaard Get-Process-weergave.

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $() {$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a>Stoppen (Stop-proces)-processen

Windows PowerShell biedt flexibiliteit voor processen weergeven, maar hoe zit het stoppen van een proces?

De **Stop-Process** cmdlet heeft een naam of Id om op te geven van een proces dat u wilt stoppen. De mogelijkheid om te stoppen processen is afhankelijk van uw machtigingen. Bepaalde processen kunnen niet worden gestopt. Haal bijvoorbeeld als u probeert om de niet-actieve proces te stoppen, een fout opgetreden:

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

U kunt ook afdwingen te vragen met de **bevestigen** parameter. Deze parameter is vooral handig als u een jokerteken gebruiken bij het opgeven van de procesnaam omdat u mogelijk per ongeluk overeenkomt met bepaalde processen die u niet wilt stoppen:

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

Complex proces manipulatie is mogelijk met behulp van een deel van het object voor het filteren van cmdlets. Omdat een procesobject een reageren-eigenschap die is ingesteld op true heeft wanneer reageert niet meer, kunt u alle responsieve toepassingen met de volgende opdracht te stoppen:

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

In andere situaties kunt u dezelfde aanpak. Stel bijvoorbeeld dat een toepassing van de gebied secundaire melding wordt automatisch uitgevoerd wanneer gebruikers een andere toepassing starten. U merkt dat dit niet goed in Terminal Services-sessies werkt, maar u toch wilt behouden blijft in sessies die worden uitgevoerd op de fysieke computer-console. Sessies altijd verbonden met het bureaublad van de fysieke computer hebben een sessie-ID 0, kunt u alle exemplaren van het proces die zich in andere sessies met stoppen **Where-Object** en het proces **SessionId** :

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

De cmdlet Stop-Process beschikt niet over een parameter ComputerName. Daarom een stopopdracht-proces op een externe computer uitgevoerd, moet u de cmdlet Invoke-Command gebruiken. Bijvoorbeeld, als u wilt stoppen het PowerShell-proces op de externe computer Server01, typt u:

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a>Alle andere Windows PowerShell-sessies te stoppen

Tijd tot tijd mogelijk handig om te voorkomen dat alle actieve Windows PowerShell-sessies dan de huidige sessie. Als een sessie te veel bronnen of niet toegankelijk is (dit kan worden uitgevoerd op afstand of in een ander bureaublad-sessiehost), mogelijk niet rechtstreeks te stoppen. Als u probeert alle actieve sessies te stoppen, maar worden de huidige sessie beëindigd in plaats daarvan.

Elke Windows PowerShell-sessie heeft een omgevingsvariabele PID met de Id van de Windows PowerShell-proces. U kunt de $PID tegen de Id van elke sessie controleren en alleen Windows PowerShell-sessies waarvoor een andere Id. beëindigen De volgende opdracht in de pijplijn wordt dit en retourneert de lijst met beëindigde sessies (vanwege het gebruik van de **PassThru** parameter):

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

Windows PowerShell ook wordt geleverd met cmdlets (of opnieuw instellen), een proces voor foutopsporing en wachttijd voor een proces te voltooien voordat een opdracht uit te voeren. Zie het help-onderwerp van de cmdlet voor elke cmdlet voor informatie over deze cdmlets.

## <a name="see-also"></a>Zie ook

- [Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)
- [Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)
- [Start-Process](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [Wait-Process](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [Debug-Process](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)