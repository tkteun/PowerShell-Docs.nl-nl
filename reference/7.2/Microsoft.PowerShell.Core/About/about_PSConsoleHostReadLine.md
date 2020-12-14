---
description: Hierin wordt uitgelegd hoe u een aanpassen hoe Power shell invoer leest bij de console prompt.
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 2f69cd4c0c8f65f4a963eae561647d6de30a067e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706087"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt uitgelegd hoe u een aanpassen hoe Power shell invoer leest bij de console prompt.

## <a name="long-description"></a>LANGE BESCHRIJVING

Vanuit Windows Power Shell 3,0 kunt u een functie schrijven met de naam PSConsoleHostReadLine die de standaard wijze overschrijft dat de console-invoer wordt verwerkt.

### <a name="examples"></a>VOORBEELDEN

In het volgende voor beeld wordt Klad blok gestart en wordt de invoer opgehaald van een tekst bestand dat de gebruiker maakt:

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a>OPMERKINGEN

Power shell leest standaard invoer van de-console in wat ook wel ' gekookte modus ' is, waarbij het subsysteem Windows console alle toetsaanslagen, F7 menu's en andere invoer verwerkt. Wanneer u op ENTER of TAB drukt, haalt Power shell de tekst op die u tot dat punt hebt getypt. Er is geen manier om te weten dat u CTRL-R, CTRL-A, CTRL-E of andere sleutels hebt ingedrukt voordat u op ENTER of TAB drukt. In Windows Power Shell 3,0 lost dit probleem op met de PSConsoleHostReadLine-functie. Wanneer u een functie met de naam PSConsoleHostReadline in de Power shell-console host definieert, roept Power shell die functie aan in plaats van het invoer mechanisme ' gekookte modus '.

### <a name="see-also"></a>ZIE OOK

[about_Prompts](about_Prompts.md)

