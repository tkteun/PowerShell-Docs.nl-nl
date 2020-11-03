---
description: Hierin wordt uitgelegd hoe u een aanpassen hoe Power shell invoer leest bij de console prompt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 143fa763c109b5645f992c3bb0a3097a8b2d9e90
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252147"
---
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="92948-104">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="92948-104">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="92948-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="92948-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="92948-106">Hierin wordt uitgelegd hoe u een aanpassen hoe Power shell invoer leest bij de console prompt.</span><span class="sxs-lookup"><span data-stu-id="92948-106">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="92948-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="92948-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="92948-108">Vanuit Windows Power Shell 3,0 kunt u een functie schrijven met de naam PSConsoleHostReadLine die de standaard wijze overschrijft dat de console-invoer wordt verwerkt.</span><span class="sxs-lookup"><span data-stu-id="92948-108">Starting in Windows PowerShell 3.0, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="92948-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="92948-109">EXAMPLES</span></span>

<span data-ttu-id="92948-110">In het volgende voor beeld wordt Klad blok gestart en wordt de invoer opgehaald van een tekst bestand dat de gebruiker maakt:</span><span class="sxs-lookup"><span data-stu-id="92948-110">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

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

### <a name="remarks"></a><span data-ttu-id="92948-111">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="92948-111">REMARKS</span></span>

<span data-ttu-id="92948-112">Power shell leest standaard invoer van de-console in wat ook wel ' gekookte modus ' is, waarbij het subsysteem Windows console alle toetsaanslagen, F7 menu's en andere invoer verwerkt.</span><span class="sxs-lookup"><span data-stu-id="92948-112">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="92948-113">Wanneer u op ENTER of TAB drukt, haalt Power shell de tekst op die u tot dat punt hebt getypt.</span><span class="sxs-lookup"><span data-stu-id="92948-113">When you press Enter or Tab, PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="92948-114">Er is geen manier om te weten dat u CTRL-R, CTRL-A, CTRL-E of andere sleutels hebt ingedrukt voordat u op ENTER of TAB drukt. In Windows Power Shell 3,0 lost dit probleem op met de PSConsoleHostReadLine-functie.</span><span class="sxs-lookup"><span data-stu-id="92948-114">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell 3.0, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="92948-115">Wanneer u een functie met de naam PSConsoleHostReadline in de Power shell-console host definieert, roept Power shell die functie aan in plaats van het invoer mechanisme ' gekookte modus '.</span><span class="sxs-lookup"><span data-stu-id="92948-115">When you define a function named PSConsoleHostReadline in the PowerShell console host, PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="92948-116">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="92948-116">SEE ALSO</span></span>

[<span data-ttu-id="92948-117">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="92948-117">about_Prompts</span></span>](about_Prompts.md)

