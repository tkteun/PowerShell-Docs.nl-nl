---
description: Hierin wordt uitgelegd hoe u een aanpassen hoe Power shell invoer leest bij de console prompt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 3c5f629471ce2a4315e3e90f2baec86dfda1506b
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253166"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin wordt uitgelegd hoe u een aanpassen hoe Power shell invoer leest bij de console prompt.

## <a name="long-description"></a>LANGE BESCHRIJVING

Vanuit Windows Power Shell v3 kunt u een functie schrijven met de naam PSConsoleHostReadLine die de standaard wijze overschrijft dat de console-invoer wordt verwerkt.

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

Power shell leest standaard invoer van de-console in wat ook wel ' gekookte modus ' is, waarbij het subsysteem Windows console alle toetsaanslagen, F7 menu's en andere invoer verwerkt. Wanneer u op ENTER of TAB drukt, wordt door Windows Power shell de tekst opgehaald die u tot dat punt hebt getypt. Er is geen manier om te weten dat u CTRL-R, CTRL-A, CTRL-E of andere sleutels hebt ingedrukt voordat u op ENTER of TAB drukt. In Windows Power shell versie 3 is dit probleem opgelost met de functie PSConsoleHostReadLine. Wanneer u een functie definieert met de naam PSConsoleHostReadline in de Windows Power shell-console-host, roept Windows Power shell die functie aan in plaats van het invoer mechanisme ' gekookte modus '.

### <a name="see-also"></a>ZIE OOK

[about_Prompts](about_Prompts.md)
