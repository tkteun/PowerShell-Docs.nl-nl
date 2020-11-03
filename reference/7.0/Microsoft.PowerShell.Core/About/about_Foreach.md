---
description: Beschrijft een taal opdracht die u kunt gebruiken om alle items in een verzameling items te door lopen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_foreach?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach
ms.openlocfilehash: 42cea9f61330e16adcad0ad543acca21e35d5ca8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252884"
---
# <a name="about-foreach"></a>Over ForEach

## <a name="short-description"></a>Korte beschrijving
Beschrijft een taal opdracht die u kunt gebruiken om alle items in een verzameling items te door lopen.

## <a name="long-description"></a>Lange beschrijving

De `Foreach` instructie (ook wel een `Foreach` lus genoemd) is een taal constructie voor het stapsgewijs door lopen van een reeks waarden in een verzameling items.

Het eenvoudigste en meest gang bare type verzameling dat u kunt door bladeren, is een matrix.
Binnen een `Foreach` lus is het gebruikelijk om een of meer opdrachten uit te voeren voor elk item in een matrix.

## <a name="syntax"></a>Syntax

Hieronder ziet u de `ForEach` syntaxis:

```
foreach ($<item> in $<collection>){<statement list>}
```

Het deel van de `ForEach` instructie tussen haakjes vertegenwoordigt een variabele en een verzameling die moet worden herhaald. Power Shell maakt de variabele `$<item>` automatisch wanneer de `Foreach` lus wordt uitgevoerd. Vóór elke iteratie door de lus wordt de variabele ingesteld op een waarde in de verzameling.
Het blok dat volgt `Foreach` op een instructie `{<statement list>}` bevat een reeks opdrachten die moeten worden uitgevoerd voor elk item in een verzameling.

### <a name="examples"></a>Voorbeelden

`Foreach`Met de lus in het volgende voor beeld worden de waarden in de matrix weer gegeven `$letterArray` .

```powershell
$letterArray = "a","b","c","d"
foreach ($letter in $letterArray)
{
  Write-Host $letter
}
```

In dit voor beeld `$letterArray` wordt de matrix gemaakt en geïnitialiseerd met de teken reeks waarden `"a"` , `"b"` , `"c"` en `"d"` . De eerste keer `Foreach` dat de instructie wordt uitgevoerd, wordt de `$letter` variabele ingesteld op het eerste item in `$letterArray` ( `"a"` ). Vervolgens wordt de cmdlet gebruikt `Write-Host` om de letter a weer te geven. De volgende keer door de lus, `$letter` is ingesteld op `"b"` , enzovoort. Wanneer de `Foreach` lus de letter d weergeeft, wordt de lus door Power shell afgesloten.

De volledige `Foreach` instructie moet op één regel worden weer gegeven om deze uit te voeren als een opdracht in de Power shell-opdracht prompt. De volledige `Foreach` instructie hoeft niet op één regel te worden weer gegeven als u in plaats daarvan de opdracht in een. ps1-script bestand plaatst.

`Foreach` instructies kunnen ook worden gebruikt in combi natie met cmdlets die een verzameling items retour neren. In het volgende voor beeld wordt de instructie foreach stapsgewijs door de lijst met items weer gegeven die door de cmdlet worden geretourneerd `Get-ChildItem` .

```powershell
foreach ($file in Get-ChildItem)
{
  Write-Host $file
}
```

U kunt het voor beeld verfijnen met behulp van een `If` instructie om de geretourneerde resultaten te beperken. In het volgende voor beeld `Foreach` voert de instructie dezelfde herhalings bewerking uit als in het vorige voor beeld, maar wordt een `If` instructie toegevoegd om de resultaten te beperken tot bestanden die groter zijn dan 100 KB (KB):

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
  }
}
```

In dit voor beeld `Foreach` gebruikt de lus een eigenschap van de `$file` variabele om een vergelijkings bewerking () uit te voeren `$file.length -gt 100KB` . De `$file` variabele bevat alle eigenschappen in het object dat door de cmdlet wordt geretourneerd `Get-ChildItem` . Daarom kunt u meer dan alleen een bestands naam retour neren.
In het volgende voor beeld retourneert Power shell de lengte en de tijd van laatste toegang in de instructie lijst:

```powershell
foreach ($file in Get-ChildItem)
{
  if ($file.length -gt 100KB)
  {
    Write-Host $file
    Write-Host $file.length
    Write-Host $file.lastaccesstime
  }
}
```

In dit voor beeld bent u niet beperkt tot het uitvoeren van één opdracht in een instructie lijst.

U kunt ook een variabele buiten een `Foreach` lus gebruiken en de variabele in de lus ophogen. In het volgende voor beeld worden bestanden geteld met een grootte van 100 KB:

```powershell
$i = 0
foreach ($file in Get-ChildItem) {
  if ($file.length -gt 100KB) {
    Write-Host $file "file size:" ($file.length / 1024).ToString("F0") KB
    $i = $i + 1
  }
}

if ($i -ne 0) {
  Write-Host
  Write-Host $i " file(s) over 100 KB in the current directory."
}
else {
  Write-Host "No files greater than 100 KB in the current directory."
}
```

In het vorige voor beeld `$i` is de variabele ingesteld op `0` buiten de lus en wordt de variabele in de lus verhoogd voor elk gevonden bestand dat groter is dan 100 kB. Wanneer de lus wordt afgesloten, wordt `If` met een instructie de waarde van het `$i` aantal bestanden in 100 KB weer gegeven. Of er wordt een bericht weer gegeven waarin wordt vermeld dat er geen bestanden meer dan 100 KB zijn gevonden.

In het vorige voor beeld ziet u ook hoe u de bestands lengte kunt indelen:

```powershell
($file.length / 1024).ToString("F0")
```

De waarde wordt gedeeld door 1.024 voor het weer geven van de resultaten in kB in plaats van bytes, en de resulterende waarde wordt vervolgens opgemaakt met de specificatie van de vaste-komma indeling om decimale waarden uit het resultaat te verwijderen. Met de 0 wordt de indelings aanduiding geen decimale posities weer gegeven.

In het volgende voor beeld worden met de gedefinieerde functie Power shell-scripts en script modules geparseerd en wordt de locatie van de functies die zijn opgenomen in. In het voor beeld ziet u hoe u de `MoveNext` methode (die `skip X` op een lus werkt `For` ) en de `Current` eigenschap van de `$foreach` variabele binnen een foreach-script blok gebruikt. De functie voor beeld kan functies vinden in een script, zelfs als er sprake is van ongebruikelijke of niet-consistente functie definities die meerdere regels omvatten.

Zie [using enumeraties](about_Automatic_Variables.md#using-enumerators)voor meer informatie.

```powershell
function Get-FunctionPosition {
  [CmdletBinding()]
  [OutputType('FunctionPosition')]
  param(
    [Parameter(Position = 0, Mandatory,
      ValueFromPipeline, ValueFromPipelineByPropertyName)]
    [ValidateNotNullOrEmpty()]
    [Alias('PSPath')]
    [System.String[]]
    $Path
  )

  process {
    try {
      $filesToProcess = if ($_ -is [System.IO.FileSystemInfo]) {
        $_
      } else {
        $filesToProcess = Get-Item -Path $Path
      }
      $parser = [System.Management.Automation.Language.Parser]
      foreach ($item in $filesToProcess) {
        if ($item.PSIsContainer -or
            $item.Extension -notin @('.ps1', '.psm1')) {
          continue
        }
        $tokens = $errors = $null
        $ast = $parser::ParseFile($item.FullName, ([REF]$tokens),
          ([REF]$errors))
        if ($errors) {
          $msg = "File '{0}' has {1} parser errors." -f $item.FullName,
            $errors.Count
          Write-Warning $msg
        }
        :tokenLoop foreach ($token in $tokens) {
          if ($token.Kind -ne 'Function') {
            continue
          }
          $position = $token.Extent.StartLineNumber
          do {
            if (-not $foreach.MoveNext()) {
              break tokenLoop
            }
            $token = $foreach.Current
          } until ($token.Kind -in @('Generic', 'Identifier'))
          $functionPosition = [pscustomobject]@{
            Name       = $token.Text
            LineNumber = $position
            Path       = $item.FullName
          }
          Add-Member -InputObject $functionPosition `
            -TypeName FunctionPosition -PassThru
        }
      }
    }
    catch {
      throw
    }
  }
}
```

## <a name="see-also"></a>ZIE OOK

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_If](about_If.md)

[ForEach-object](xref:Microsoft.PowerShell.Core.ForEach-Object)
