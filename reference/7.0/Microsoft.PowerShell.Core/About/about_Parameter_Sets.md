---
description: Hierin wordt beschreven hoe u in geavanceerde functies parameter sets definieert en gebruikt.
title: about_Parameter_Sets
ms.date: 01/05/2021
ms.openlocfilehash: 8f3a33345a8e2fa19810c8ebd527d9a7dca7dec5
ms.sourcegitcommit: eb7ad1850550032880f5529b4e4281514cba1673
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/06/2021
ms.locfileid: "97917814"
---
# <a name="about-parameter-sets"></a>Over parameter sets

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u in geavanceerde functies parameter sets definieert en gebruikt.

## <a name="long-description"></a>LANGE BESCHRIJVING

Power shell gebruikt parameter sets waarmee u één functie kunt schrijven die verschillende acties voor verschillende scenario's kan uitvoeren. Met parameter sets kunt u verschillende para meters voor de gebruiker beschikbaar maken. En om andere informatie te retour neren op basis van de para meters die door de gebruiker zijn opgegeven.

## <a name="parameter-set-requirements"></a>Vereisten voor de parameterset

De volgende vereisten zijn van toepassing op alle parameter sets.

- Elke parameterset moet een unieke combi natie van para meters hebben. Indien mogelijk moet ten minste één van de unieke para meters een verplichte para meter zijn.

- Een parameterset met meerdere positionele para meters moet unieke posities definiëren voor elke para meter. Er kunnen niet twee positionele para meters dezelfde positie opgeven.

- Slechts één para meter in een set kan het `ValueFromPipeline` tref woord declareren met een waarde van `true` . Meerdere para meters kunnen het `ValueFromPipelineByPropertyName` sleutel woord definiëren met een waarde van `true` .

- Als er geen parameterset voor een para meter is opgegeven, hoort de para meter bij alle parameter sets.

> [!NOTE]
> Er is een limiet van 32 parameter sets.

## <a name="default-parameter-sets"></a>Standaard parameters sets

Als er meerdere parameter sets zijn gedefinieerd, `DefaultParameterSetName` geeft het sleutel woord van het kenmerk **CmdletBinding** de standaard parameterset.
Power shell gebruikt de standaard parameterset wanneer de ingestelde para meter niet kan worden bepaald op basis van de gegevens die aan de opdracht worden gegeven. Zie [about_functions_cmdletbindingattribute](about_functions_cmdletbindingattribute.md)voor meer informatie over het kenmerk **CmdletBinding** .

## <a name="declaring-parameter-sets"></a>Parameter sets declareren

Als u een parameterset wilt maken, moet u het `ParameterSetName` tref woord van het **parameter** kenmerk voor elke para meter in de parameterset opgeven. Voor para meters die bij meerdere parameter sets horen, voegt u een **parameter** kenmerk toe voor elke parameterset.

Met het **parameter** kenmerk kunt u de para meter op verschillende manieren definiëren voor elke parameterset. U kunt bijvoorbeeld een para meter definiëren als verplicht in de ene set en optioneel in een andere. Elke parameterset moet echter ten minste één unieke para meter bevatten.

Para meters die geen toegewezen parameterset naam hebben, behoren tot alle parameter sets.

### <a name="example"></a>Voorbeeld

De volgende voorbeeld functie telt de nummer regels, tekens en woorden in een tekst bestand. Met para meters kunt u opgeven welke waarden u wilt retour neren en welke bestanden u wilt meten. Er zijn vier parameters sets gedefinieerd:

- Pad
- PathAll
- LiteralPath
- LiteralPathAll

```powershell
function Measure-Lines {
    [CmdletBinding(DefaultParameterSetName = 'Path')]
    param (
        [Parameter(Mandatory = $true,
            ParameterSetName = 'Path',
            HelpMessage = 'Enter one or more filenames',
            Position = 0)]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'PathAll',
            Position = 0)]
        [string[]]$Path,

        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [Parameter(Mandatory = $true,
            ParameterSetName = 'LiteralPath',
            HelpMessage = 'Enter a single filename',
            ValueFromPipeline = $true)]
        [string]$LiteralPath,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Lines,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Words,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'LiteralPath')]
        [switch]$Characters,

        [Parameter(Mandatory = $true, ParameterSetName = 'PathAll')]
        [Parameter(Mandatory = $true, ParameterSetName = 'LiteralPathAll')]
        [switch]$All,

        [Parameter(ParameterSetName = 'Path')]
        [Parameter(ParameterSetName = 'PathAll')]
        [switch]$Recurse
    )

    begin {
        if ($All) {
            $Lines = $Words = $Characters = $true
        }
        elseif (($Words -eq $false) -and ($Characters -eq $false)) {
            $Lines = $true
        }

        if ($Path) {
            $Files = Get-ChildItem -Path $Path -Recurse:$Recurse
        }
        else {
            $Files = Get-ChildItem -LiteralPath $LiteralPath
        }
    }
    process {
        foreach ($file in $Files) {
            $result = [ordered]@{ }
            $result.Add('File', $file.fullname)

            $content = Get-Content -LiteralPath $file.fullname

            if ($Lines) { $result.Add('Lines', $content.Length) }

            if ($Words) {
                $wc = 0
                foreach ($line in $content) { $wc += $line.split(' ').Length }
                $result.Add('Words', $wc)
            }

            if ($Characters) {
                $cc = 0
                foreach ($line in $content) { $cc += $line.Length }
                $result.Add('Characters', $cc)
            }

            New-Object -TypeName psobject -Property $result
        }
    }
}
```

Elke parameterset moet een unieke para meter of een unieke combi natie van para meters hebben. De `Path` `PathAll` para meters en zijn vergelijkbaar, maar de para meter **all** is uniek voor de `PathAll` parameterset. Hetzelfde geldt voor de `LiteralPath` `LiteralPathAll` para meters en. Hoewel de para `PathAll` meter en `LiteralPathAll` beide de para meter **all** hebben, worden deze door de para meters **Path** en **LiteralPath** onderscheiden.

Gebruik `Get-Command -Syntax` toont de syntaxis van elke parameterset. De naam van de parameterset wordt echter niet weer gegeven. In het volgende voor beeld ziet u welke para meters in elke parameterset kunnen worden gebruikt.

```powershell
(Get-Command Measure-Lines).ParameterSets |
  Select-Object -Property @{n='ParameterSetName';e={$_.name}},
    @{n='Parameters';e={$_.ToString()}}
```

```Output
ParameterSetName Parameters
---------------- ----------
Path             [-Path] <string[]> [-Lines] [-Words] [-Characters] [-Recurse] [<CommonParameters>]
PathAll          [-Path] <string[]> -All [-Recurse] [<CommonParameters>]
LiteralPath      -LiteralPath <string> [-Lines] [-Words] [-Characters] [<CommonParameters>]
LiteralPathAll   -LiteralPath <string> -All [<CommonParameters>]
```

### <a name="parameter-sets-in-action"></a>Parameter sets in actie

In dit voor beeld gebruiken we de `PathAll` para meter set.

```powershell
Measure-Lines test* -All
```

```Output
File                       Lines Words Characters
----                       ----- ----- ----------
C:\temp\test\test.help.txt    31   562       2059
C:\temp\test\test.md          30  1527       3224
C:\temp\test\test.ps1          3     3         79
C:\temp\test\test[1].txt      31   562       2059
```
