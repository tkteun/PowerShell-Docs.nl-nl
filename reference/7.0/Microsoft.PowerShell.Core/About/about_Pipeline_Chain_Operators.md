---
description: Beschrijft het koppelen van pijp lijnen met `&&` de `||` Opera tors en in Power shell.
ms.date: 09/30/2019
schema: 2.0.0
Locale: en-US
keywords: powershell,cmdlet
title: about_Pipeline_Chain_Operators
ms.openlocfilehash: 107d5eacb7b9629a42d5eef53e0c7c66a522f32e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252703"
---
# <a name="about-pipeline-chain-operators"></a>Over pijplijn keten operators

## <a name="short-description"></a>Korte beschrijving

Beschrijft het koppelen van pijp lijnen met `&&` de `||` Opera tors en in Power shell.

## <a name="long-description"></a>Lange beschrijving

Vanaf Power shell 7 implementeert Power shell de `&&` `||` Opera tors en om pijp lijnen voorwaardelijk te koppelen. Deze opera tors zijn bekend in Power shell als *Opera tors voor pipeline-ketens* en zijn vergelijkbaar met [en-of-lijsten](https://pubs.opengroup.org/onlinepubs/009695399/utilities/xcu_chap02.html#tag_02_09_03) in POSIX-shells zoals bash, zsh en sh, evenals [voorwaardelijke verwerkings symbolen](/previous-versions/windows/it-pro/windows-xp/bb490954(v=technet.10)#using-multiple-commands-and-conditional-processing-symbols) in de Windows-opdracht shell (cmd.exe).

De `&&` operator voert de rechter pijplijn uit, als de pijplijn is geslaagd. De operator voert daarentegen `||` de rechter pijp lijn uit als de linker pijp lijn is mislukt.

Deze opera tors gebruiken `$?` de `$LASTEXITCODE` variabelen en om te bepalen of een pijp lijn is mislukt. Hierdoor kunt u ze gebruiken met systeem eigen opdrachten en niet alleen met cmdlets of functies. Bijvoorbeeld:

```powershell
# Create an SSH key pair - if successful copy the public key to clipboard
ssh-keygen -t rsa -b 2048 && Get-Content -Raw ~\.ssh\id_rsa.pub | clip
```

### <a name="examples"></a>Voorbeelden

#### <a name="two-successful-commands"></a>Twee geslaagde opdrachten

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

#### <a name="first-command-fails-causing-second-not-to-be-executed"></a>Eerste opdracht mislukt, waardoor de tweede niet wordt uitgevoerd

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

#### <a name="first-command-succeeds-so-the-second-command-is-not-executed"></a>De eerste opdracht is geslaagd, waardoor de tweede opdracht niet wordt uitgevoerd

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

#### <a name="first-command-fails-so-the-second-command-is-executed"></a>De eerste opdracht mislukt, dus de tweede opdracht wordt uitgevoerd

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error: Bad
Second
```

Pijp lijn geslaagd wordt gedefinieerd door de waarde van de `$?` variabele, die Power shell automatisch instelt nadat een pijp lijn is uitgevoerd op basis van de uitvoerings status.
Dit betekent dat de Opera tors voor pijplijn keten de volgende gelijkwaardigheid hebben:

```powershell
Test-Command '1' && Test-Command '2'
```

werkt hetzelfde als

```powershell
Test-Command '1'; if ($?) { Test-Command '2' }
```

en

```powershell
Test-Command '1' || Test-Command '2'
```

werkt hetzelfde als

```powershell
Test-Command '1'; if (-not $?) { Test-Command '2' }
```

### <a name="assignment-from-pipeline-chains"></a>Toewijzing van pijp lijn ketens

Wanneer u een variabele toewijst vanuit een pijplijn keten, neemt de samen voeging van alle pijp lijnen in de keten toe:

```powershell
$result = Write-Output '1' && Write-Output '2'
$result
```

```Output
1
2
```

Als er een fout optreedt tijdens het beëindigen van een script tijdens toewijzing vanuit een pijplijn keten, mislukt de toewijzing:

```powershell
try
{
    $result = Write-Output 'Value' && $(throw 'Bad')
}
catch
{
    # Do nothing, just squash the error
}

"Result: $result"
```

```Output
Result:
```

### <a name="operator-syntax-and-precedence"></a>Operator syntaxis en prioriteit

In tegens telling tot andere opera tors `&&` en `||` op pijp lijnen, in plaats van op expressies zoals `+` of `-and` , bijvoorbeeld.

`&&` en `||` hebben een lagere prioriteit dan sluizen ( `|` ) of omleiding ( `>` ), maar een hogere prioriteit dan de taak operators ( `&` ), de toewijzing ( `=` ) of een punt komma ( `;` ). Dit betekent dat pijp lijnen in een pijplijn keten afzonderlijk kunnen worden omgeleid en dat volledige pijplijn ketens kunnen worden geachtergrondd, toegewezen aan variabelen of gescheiden als-instructies.

Als u de syntaxis met een lagere prioriteit wilt gebruiken in een pijplijn keten, overweeg dan het gebruik van haakjes `(...)` .
Als u een instructie wilt insluiten in een pijplijn keten, kunt u ook een subexpressie `$(...)` gebruiken.
Dit kan handig zijn voor het combi neren van systeem eigen opdrachten met controle stroom:

```powershell
foreach ($file in 'file1','file2','file3')
{
    # When find succeeds, the loop breaks
    find $file && Write-Output "Found $file" && $(break)
}
```

```Output
find: file1: No such file or directory
file2
Found file2
```

Vanaf Power shell 7 is het gedrag van deze syntaxis gewijzigd, zodat het `$?` is ingesteld op verwachting als een opdracht is geslaagd of mislukt tussen haakjes of een subexpressie.

Net als de meeste andere opera tors in Power shell `&&` en `||` zijn ook *links gekoppeld* , wat betekent dat ze aan de linkerkant worden gegroepeerd. Bijvoorbeeld:

```powershell
Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist" && Get-Content -Raw ./file.txt
```

wordt als volgt gegroepeerd:

```
[Get-ChildItem -Path ./file.txt || Write-Error "file.txt does not exist"] && Get-Content -Raw ./file.txt
```

komt overeen met:

```powershell
Get-ChildItem -Path ./file.txt

if (-not $?) { Write-Error "file.txt does not exist" }

if ($?) { Get-Content -Raw ./file.txt }
```

### <a name="error-interaction"></a>Fout interactie

Opera tors voor pijplijn ketens nemen geen fouten op. Wanneer een instructie in een pijplijn keten een script beëindigt, wordt de pijplijn keten beëindigd.

Bijvoorbeeld:

```powershell
$(throw 'Bad') || Write-Output '2'
```

```Output
Exception: Bad
```

Zelfs wanneer de fout is opgetreden, wordt de pipeline-keten nog steeds beëindigd:

```powershell
try
{
    $(throw 'Bad') || Write-Output '2'
}
catch
{
    Write-Output "Caught: $_"
}
Write-Output 'Done'
```

```Output
Caught: Bad
Done
```

Als een fout niet wordt beëindigd of als er alleen een pijp lijn wordt beëindigd, blijft de pijplijn keten de waarde van `$?` :

```powershell
function Test-NonTerminatingError
{
    [CmdletBinding()]
    param()

    $exception = [System.Exception]::new('BAD')
    $errorId = 'BAD'
    $errorCategory = 'NotSpecified'

    $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

    $PSCmdlet.WriteError($errorRecord)
}

Test-NonTerminatingError || Write-Output 'Second'
```

```Output
Test-NonTerminatingError: BAD
Second
```

### <a name="chaining-pipelines-rather-than-commands"></a>Pijp lijnen koppelen in plaats van opdrachten

Pijplijn keten operators op basis van hun naam kunnen worden gebruikt voor het koppelen van pijp lijnen, in plaats van alleen op opdrachten. Dit komt overeen met het gedrag van andere shells, maar het *kan lastig zijn om het volgende te* bepalen:

```powershell
function Test-NotTwo
{
    [CmdletBinding()]
    param(
      [Parameter(ValueFromPipeline)]
      $Input
    )

    process
    {
        if ($Input -ne 2)
        {
            return $Input
        }

        $exception = [System.Exception]::new('Input is 2')
        $errorId = 'InputTwo'
        $errorCategory = 'InvalidData'

        $errorRecord = [System.Management.Automation.ErrorRecord]::new($exception, $errorId, $errorCategory, $null)

        $PSCmdlet.WriteError($errorRecord)
    }
}

1,2,3 | Test-NotTwo && Write-Output 'All done!'
```

```Output
1
Test-NotTwo : Input is 2
3
```

Houd er rekening mee dat `Write-Output 'All done!'` niet wordt uitgevoerd, omdat er `Test-NotTwo` een fout is opgetreden bij het genereren van de niet-afsluit fouten.

## <a name="see-also"></a>Zie ook

- [about_Operators](about_Operators.md)
- [about_Automatic_Variables](about_Automatic_Variables.md)
- [about_pipelines](about_pipelines.md)
