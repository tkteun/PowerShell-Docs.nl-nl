---
description: Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: bef005f47583523f69a8b25651eb0ee5bfc5b224
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195854"
---
# <a name="about-throw"></a>Over throw

## <a name="short-description"></a>Korte beschrijving
Hierin wordt het sleutel woord throw beschreven, waarmee een afsluit fout wordt gegenereerd.

## <a name="long-description"></a>Lange beschrijving

Het sleutel woord throw veroorzaakt een afsluit fout. U kunt het sleutel woord throw gebruiken om de verwerking van een opdracht, functie of script te stoppen.

U kunt bijvoorbeeld het sleutel woord throw in het script blok van een if-instructie gebruiken om te reageren op een voor waarde of in het blok catch van een try-catch-finally-instructie. U kunt ook het sleutel woord throw in een parameter declaratie gebruiken om een functie parameter verplicht te maken.

Het sleutel woord throw kan elk object genereren, zoals een gebruikers bericht teken reeks of het object dat de fout heeft veroorzaakt.

## <a name="syntax"></a>Syntax

De syntaxis van het sleutel woord throw is als volgt:

```powershell
throw [<expression>]
```

De expressie in de syntaxis van de throw is optioneel. Wanneer de instructie throw niet wordt weer gegeven in een catch-blok en geen expressie bevat, wordt er een ScriptHalted-fout gegenereerd.

```powershell
C:\PS> throw

Exception: ScriptHalted
```

Als het sleutel woord throw wordt gebruikt in een catch-blok zonder expressie, wordt de huidige RuntimeException opnieuw gegenereerd. Zie about_Try_Catch_Finally voor meer informatie.

## <a name="throwing-a-string"></a>Een teken reeks activeren

De optionele expressie in een instructie throw kan een teken reeks zijn, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
C:\PS> throw "This is an error."

Exception: This is an error.
```

## <a name="throwing-other-objects"></a>Andere objecten activeren

De expressie kan ook een object zijn dat het object genereert dat het Power Shell-proces vertegenwoordigt, zoals wordt weer gegeven in het volgende voor beeld:

```powershell
C:\PS> throw (get-process Pwsh)

Exception: System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh) System.Diagnostics.Process (pwsh)
```

U kunt de eigenschap target object van het object ErrorRecord in de variabele $error Automatic gebruiken om de fout te onderzoeken.

```powershell
C:\PS> $error[0].targetobject

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    125   174.44     229.57      23.61    1548   2 pwsh
     63    44.07      81.95       1.75    1732   2 pwsh
     63    43.32      77.65       1.48    9092   2 pwsh
```

U kunt ook een ErrorRecord-object of een .NET-uitzonde ring genereren. In het volgende voor beeld wordt het sleutel woord throw gebruikt voor het genereren van een System. FormatException-object.

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

OperationStopped: One of the identified items was in an invalid format.
```

## <a name="the-resulting-error"></a>De resulterende fout

Met het sleutel woord throw kan een ErrorRecord-object worden gegenereerd. De eigenschap Exception van het object ErrorRecord bevat een RuntimeException-object. De rest van het ErrorRecord-object en het RuntimeException-object verschillen met het object dat het sleutel woord throw genereert.

Het RunTimeException-object wordt verpakt in een ErrorRecord-object en het ErrorRecord-object wordt automatisch opgeslagen in de variabele $Error Automatic.

## <a name="using-throw-to-create-a-mandatory-parameter"></a>Een verplichte para meter maken met behulp van throw

In tegens telling tot eerdere versies van Power shell, moet u het sleutel woord throw niet gebruiken voor de validatie van de para meters. Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md) op de juiste manier.

## <a name="see-also"></a>Zie ook

- [about_Break](about_Break.md)
- [about_Continue](about_Continue.md)
- [about_Scopes](about_Scopes.md)
- [about_Trap](about_Trap.md)
- [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
