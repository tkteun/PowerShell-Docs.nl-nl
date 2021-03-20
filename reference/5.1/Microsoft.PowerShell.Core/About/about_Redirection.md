---
description: Hierin wordt uitgelegd hoe u de uitvoer omleidt van Power shell naar tekst bestanden.
Locale: en-US
ms.date: 03/18/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_redirection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Redirection
ms.openlocfilehash: e12514fed8e126dcffb80536b252e19ab3ffa697
ms.sourcegitcommit: 16a02ae47d1a85b01692101aa0aa6e91e1ba398e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104726618"
---
# <a name="about-redirection"></a>Over omleiding

## <a name="short-description"></a>Korte beschrijving
Hierin wordt uitgelegd hoe u de uitvoer omleidt van Power shell naar tekst bestanden.

## <a name="long-description"></a>Lange beschrijving

Power shell verzendt standaard uitvoer naar de Power shell-host. Doorgaans is dit de console toepassing. U kunt de uitvoer echter omleiden naar een tekst bestand en u kunt de fout uitvoer omleiden naar de normale uitvoer stroom.

U kunt de volgende methoden gebruiken om uitvoer om te leiden:

- Gebruik de `Out-File` cmdlet, waarmee de uitvoer van de opdracht wordt verzonden naar een tekst bestand.
  Normaal gesp roken gebruikt u de `Out-File` cmdlet wanneer u de para meters, zoals de `Encoding` ,, `Force` `Width` of `NoClobber` para meters, moet gebruiken.

- Gebruik de `Tee-Object` cmdlet, waarmee de uitvoer van de opdracht naar een tekst bestand wordt verzonden en vervolgens naar de pijp lijn wordt verzonden.

- Gebruik de omleidings operatoren voor Power shell. Het gebruik van de omleidings operator met een bestands doel is functioneel equivalent aan leidingen zonder `Out-File` extra para meters.

Zie [about_Output_Streams](about_Output_Streams.md)voor meer informatie over stromen.

### <a name="redirectable-output-streams"></a>Omgeleide uitvoer stromen

Power shell ondersteunt omleiding van de volgende uitvoer stromen.

| Bitsnelheid # |      Beschrijving       | Geïntroduceerd in  |    Cmdlet schrijven     |
| -------- | ---------------------- | -------------- | ------------------- |
| 1        | **Geslaagd** Bitsnelheid     | Power Shell 2,0 | `Write-Output`      |
| 2        | **Fout** Bitsnelheid       | Power Shell 2,0 | `Write-Error`       |
| 3        | **Waarschuwing** Bitsnelheid     | PowerShell 3.0 | `Write-Warning`     |
| 4        | **Uitgebreid** Bitsnelheid     | PowerShell 3.0 | `Write-Verbose`     |
| 5        | **Fouten opsporen** Bitsnelheid       | PowerShell 3.0 | `Write-Debug`       |
| 6        | **Gegevens** Bitsnelheid | PowerShell 5.0 | `Write-Information` |
| *        | Alle streams            | PowerShell 3.0 |                     |

Er is ook een **voortgangs** stroom in Power shell, maar de omleiding wordt niet ondersteund.

> [!IMPORTANT]
> De **slagen** -en **fout** stromen zijn vergelijkbaar met de stdin-en stderr-streams van andere shells. Stdin is echter niet verbonden met de Power shell-pijp lijn voor invoer.

### <a name="powershell-redirection-operators"></a>Omleidings operatoren voor Power shell

De Power shell-omleidings operatoren zijn als volgt, waarbij `n` het stroom nummer wordt aangeduid. De **geslaagde** stroom ( `1` ) is de standaard waarde als er geen stroom is opgegeven.

| Operator |                         Beschrijving                         | Syntax |
| -------- | ----------------------------------------------------------- | ------ |
| `>`      | De opgegeven stroom naar een bestand verzenden.                            | `n>`   |
| `>>`     | De opgegeven stroom aan een bestand **toevoegen** .                      | `n>>`  |
| `>&1`    | _Leidt_ de opgegeven stroom om naar de **succes** stroom. | `n>&1` |

> [!NOTE]
> In tegens telling tot sommige UNIX-shells kunt u alleen andere streams omleiden naar de stroom van **slagen** .

## <a name="examples"></a>Voorbeelden

### <a name="example-1-redirect-errors-and-output-to-a-file"></a>Voor beeld 1: fouten omleiden en uitvoer naar een bestand

Dit voor beeld wordt uitgevoerd `dir` op één item dat slaagt en dat een fout bevat.

```powershell
dir 'C:\', 'fakepath' 2>&1 > .\dir.log
```

De functie wordt gebruikt `2>&1` om de **fout** stroom om te leiden naar de stroom die is **gelukt** en `>` om de resulterende **geslaagde** stroom te verzenden naar een bestand met de naam `dir.log`

### <a name="example-2-send-all-success-stream-data-to-a-file"></a>Voor beeld 2: alle geslaagde stroom gegevens naar een bestand verzenden

In dit voor beeld worden alle **geslaagde** stroom gegevens verzonden naar een bestand met de naam `script.log` .

```powershell
.\script.ps1 > script.log
```

### <a name="example-3-send-success-warning-and-error-streams-to-a-file"></a>Voor beeld 3: geslaagde, waarschuwings-en fout stromen naar een bestand verzenden

Dit voor beeld laat zien hoe u omleidings operatoren kunt combi neren om een gewenst resultaat te krijgen.

```powershell
&{
   Write-Warning "hello"
   Write-Error "hello"
   Write-Output "hi"
} 3>&1 2>&1 > C:\Temp\redirection.log
```

- `3>&1` leidt de **waarschuwing** over naar de stroom voor **geslaagde** gegevens.
- `2>&1` Hiermee wordt de **fout** stroom omgeleid naar de stroom voor **geslaagde** verzen ding (die nu alle **waarschuwingen** voor de gegevens stroom bevat)
- `>` Hiermee wordt de stroom voor het **slagen** (die nu zowel **waarschuwings** -als **fout** stromen bevat) omgeleid naar een bestand met `C:\temp\redirection.log` de naam.

### <a name="example-4-redirect-all-streams-to-a-file"></a>Voor beeld 4: alle streams omleiden naar een bestand

In dit voor beeld wordt alle stromen uitvoer verzonden vanuit een script dat wordt aangeroepen `script.ps1` naar een bestand met de naam `script.log`

```powershell
.\script.ps1 *> script.log
```

### <a name="example-5-suppress-all-write-host-and-information-stream-data"></a>Voor beeld 5: alle Write-Host-en informatie stroom gegevens onderdrukken

In dit voor beeld worden alle gegevens streamgegevens onderdrukt. Zie [Write-host](xref:Microsoft.PowerShell.Utility.Write-Host) en [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) (Engelstalig) voor meer informatie over de **gegevens** stroom-cmdlets

```powershell
&{
   Write-Host "Hello"
   Write-Information "Hello" -InformationAction Continue
} 6> $null
```

### <a name="example-6-show-the-effect-of-action-preferences"></a>Voor beeld 6: het effect van actie voorkeuren weer geven

Voor keur variabelen en-para meters voor acties kunnen veranderen wat naar een bepaalde stroom wordt geschreven. Het script in dit voor beeld laat zien hoe de waarde van `$ErrorActionPreference` invloed heeft op wat **er** naar de fout stroom wordt geschreven.

```powershell
$ErrorActionPreference = 'Continue'
$ErrorActionPreference > log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'SilentlyContinue'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Stop'
$ErrorActionPreference >> log.txt
Try {
    get-item /not-here 2>&1 >> log.txt
}
catch {
    "`tError caught!" >> log.txt
}
$ErrorActionPreference = 'Ignore'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Inquire'
$ErrorActionPreference >> log.txt
get-item /not-here 2>&1 >> log.txt

$ErrorActionPreference = 'Continue'
```

Wanneer het script wordt uitgevoerd, ontvangt u een melding wanneer `$ErrorActionPreference` is ingesteld op `Inquire` .

```powershell
PS C:\temp> .\test.ps1

Confirm
Cannot find path 'C:\not-here' because it does not exist.
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): H
Get-Item: C:\temp\test.ps1:23
Line |
  23 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | The running command stopped because the user selected the Stop option.
```

Wanneer we het logboek bestand onderzoeken, zien we het volgende:

```
PS C:\temp> Get-Content .\log.txt
Continue

Get-Item: C:\temp\test.ps1:3
Line |
   3 |  get-item /not-here 2>&1 >> log.txt
     |  ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     | Cannot find path 'C:\not-here' because it does not exist.

SilentlyContinue
Stop
    Error caught!
Ignore
Inquire
```

## <a name="notes"></a>Notities

De omleidings operatoren die geen gegevens toevoegen ( `>` en `n>` ) overschrijven de huidige inhoud van het opgegeven bestand zonder waarschuwing.

Als het bestand echter een alleen-lezen, verborgen of systeem bestand is, **mislukt** de omleiding. De Opera tors voor omleidingen ( `>>` en `n>>` ) worden niet naar een alleen-lezen bestand geschreven, maar ze voegen inhoud toe aan een systeem of een verborgen bestand.

Als u de omleiding van inhoud wilt afdwingen naar een alleen-lezen, verborgen of systeem bestand, gebruikt u de `Out-File` cmdlet met de `Force` para meter.

Wanneer u naar bestanden schrijft, gebruiken de omleidings operatoren `UTF8NoBOM` code ring. Als het bestand een andere code ring heeft, is de uitvoer mogelijk niet correct ingedeeld. Als u naar bestanden met een andere code ring wilt schrijven, gebruikt u de `Out-File` cmdlet met de `Encoding` para meter.

### <a name="potential-confusion-with-comparison-operators"></a>Mogelijke Verwar ring met vergelijkings operatoren

De `>` operator kan niet worden verward met de vergelijkings operator [groter dan](about_Comparison_Operators.md#-gt--ge--lt-and--le) (vaak aangeduid als `>` in andere programmeer talen).

Afhankelijk van de objecten die worden vergeleken, is het mogelijk dat de uitvoer met de juiste indeling wordt `>` weer gegeven (omdat 36 niet groter is dan 42).

```powershell
PS> if (36 > 42) { "true" } else { "false" }
false
```

Een controle van het lokale bestands systeem kan echter zien dat een bestand `42` met de naam is geschreven, met de inhoud `36` .

```powershell
PS> dir

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
------          1/02/20  10:10 am              3 42

PS> cat 42
36
```

Er wordt geprobeerd om de omgekeerde vergelijking `<` (kleiner dan) te gebruiken, wat een systeem fout levert:

```powershell
PS> if (36 < 42) { "true" } else { "false" }
At line:1 char:8
+ if (36 < 42) { "true" } else { "false" }
+        ~
The '<' operator is reserved for future use.
    + CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
    + FullyQualifiedErrorId : RedirectionNotSupported
```

Als numerieke vergelijking de vereiste bewerking is, `-lt` en deze `-gt` moet worden gebruikt. Zie de `-gt` operator in [about_Comparison_Operators](about_Comparison_Operators.md#-gt--ge--lt-and--le)voor meer informatie.

## <a name="see-also"></a>Zie ook

- [Out-file](xref:Microsoft.PowerShell.Utility.Out-File)
- [T-object](xref:Microsoft.PowerShell.Utility.Tee-Object)
- [Schrijf fouten opsporen](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Schrijf fout](xref:Microsoft.PowerShell.Utility.Write-Error)
- [Write-host](xref:Microsoft.PowerShell.Utility.Write-Host)
- [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)
- [Write-output](xref:Microsoft.PowerShell.Utility.Write-Output)
- [Schrijf voortgang](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [Write-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [Waarschuwing voor schrijven](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [about_Output_Streams](about_Output_Streams.md)
- [about_Operators](about_Operators.md)
- [about_Command_Syntax](about_Command_Syntax.md)
- [about_Path_Syntax](about_Path_Syntax.md)
