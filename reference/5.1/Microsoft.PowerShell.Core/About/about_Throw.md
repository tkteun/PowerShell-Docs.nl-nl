---
description: Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: e573722154fff99363b26806064ec17c8903bfd8
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194176"
---
# <a name="about-throw"></a>Over throw

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.

## <a name="long-description"></a>LANGE BESCHRIJVING

Het sleutel woord throw veroorzaakt een afsluit fout. U kunt het sleutel woord throw gebruiken om de verwerking van een opdracht, functie of script te stoppen.

U kunt bijvoorbeeld het sleutel woord throw in het script blok van een if-instructie gebruiken om te reageren op een voor waarde of in het blok catch van een try-catch-finally-instructie. U kunt ook het sleutel woord throw in een parameter declaratie gebruiken om een functie parameter verplicht te maken.

Het sleutel woord throw kan elk object genereren, zoals een gebruikers bericht teken reeks of het object dat de fout heeft veroorzaakt.

## <a name="syntax"></a>SYNTAXIS

De syntaxis van het sleutel woord throw is als volgt:

```powershell
throw [<expression>]
```

De expressie in de syntaxis van de throw is optioneel. Wanneer de instructie throw niet wordt weer gegeven in een catch-blok en geen expressie bevat, wordt er een ScriptHalted-fout gegenereerd.

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

Als het sleutel woord throw wordt gebruikt in een catch-blok zonder expressie, wordt de huidige RuntimeException opnieuw gegenereerd. Zie about_Try_Catch_Finally voor meer informatie.

## <a name="throwing-a-string"></a>EEN TEKEN REEKS ACTIVEREN

De optionele expressie in een instructie throw kan een teken reeks zijn, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a>ANDERE OBJECTEN ACTIVEREN

De expressie kan ook een object zijn dat het object genereert dat het Power Shell-proces vertegenwoordigt, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

U kunt de eigenschap target object van het object ErrorRecord in de variabele $error Automatic gebruiken om de fout te onderzoeken.

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

U kunt ook een ErrorRecord-object of een Microsoft .NET Framework-uitzonde ring genereren. In het volgende voor beeld wordt het sleutel woord throw gebruikt voor het genereren van een System. FormatException-object.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a>RESULTERENDE FOUT

Met het sleutel woord throw kan een ErrorRecord-object worden gegenereerd. De eigenschap Exception van het object ErrorRecord bevat een RuntimeException-object. De rest van het ErrorRecord-object en het RuntimeException-object verschillen met het object dat het sleutel woord throw genereert.

Het RunTimeException-object wordt verpakt in een ErrorRecord-object en het ErrorRecord-object wordt automatisch opgeslagen in de variabele $Error Automatic.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>EEN VERPLICHTE PARA METER MAKEN MET BEHULP VAN THROW

U kunt het sleutel woord throw gebruiken om een functie parameter verplicht te maken.

Dit is een alternatief voor het gebruik van de verplichte para meter van het sleutel woord para meter. Wanneer u de verplichte para meter gebruikt, vraagt het systeem de gebruiker om de vereiste parameter waarde. Wanneer u het sleutel woord throw gebruikt, wordt de opdracht gestopt en wordt de fout record weer gegeven.

Het sleutel woord throw in de subexpressie van para meters maakt bijvoorbeeld de para meter Path een vereiste para meter in de functie.

In dit geval genereert het sleutel woord throw een bericht teken reeks, maar het is de aanwezigheid van het sleutel woord throw waarmee de afsluit fout wordt gegenereerd als de para meter Path niet is opgegeven. De expressie die volgt op throw is optioneel.

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a>ZIE OOK

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
