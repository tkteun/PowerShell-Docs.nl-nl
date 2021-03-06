---
ms.date: 08/14/2018
title: Kennismaking met Windows PowerShell ISE
description: De Power shell-ISE is een hosttoepassing voor Windows Power shell waarmee u-opdrachten kunt uitvoeren en scripts voor schrijven, testen en fouten opspoort in één grafische gebruikers interface op basis van Windows.
ms.openlocfilehash: ab2b11e5d81933b166d404c0b24c96aa73253895
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663608"
---
# <a name="the-windows-powershell-ise"></a>De Windows PowerShell ISE

De Windows Power shell Integrated Scripting Environment (ISE) is een hosttoepassing voor Windows Power shell. In de ISE kunt u-opdrachten uitvoeren en scripts schrijven, testen en fouten opsporen in één op Windows gebaseerde grafische gebruikers interface. De ISE biedt bewerkingen op meerdere regels, tabblad voltooiing, syntaxis kleuren, selectief uitvoeren, context gevoelige Help en ondersteuning voor talen die van rechts naar links worden geschreven. Menu opdrachten en sneltoetsen worden toegewezen aan veel van de taken die u in de Windows Power shell-console zou uitvoeren. Wanneer u bijvoorbeeld fouten opspoort in een script in de ISE, kunt u met de rechter muisknop op een regel code in het deel venster bewerken klikken om een onderbrekings punt in te stellen.

## <a name="support"></a>Ondersteuning

De ISE is voor het eerst geïntroduceerd in Windows Power shell v2 en is opnieuw ontworpen met Power Shell v3. De ISE wordt ondersteund in alle ondersteunde versies van Windows Power shell tot en met Windows Power shell V 5.1.

> [!NOTE]
> De Power shell-ISE is niet langer beschikbaar voor het ontwikkelen van actieve functies. Als onderdeel van Windows-verzen ding wordt het officieel ondersteund voor beveiligings updates en onderhoud met hoge prioriteit.
> Er zijn momenteel geen abonnementen om de ISE van Windows te verwijderen.
>
> Er is geen ondersteuning voor de ISE in Power shell V6 en verder. Gebruikers die op zoek zijn naar vervanging voor ISE, moeten [Visual Studio code](https://code.visualstudio.com/) gebruiken met de [Power shell-extensie](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="key-features"></a>Belangrijkste functies

De belangrijkste functies in Windows PowerShell ISE zijn onder andere:

- Meerdere regels bewerken: als u een lege regel wilt invoegen onder de huidige regel in het opdracht venster, drukt u op <kbd>SHIFT</kbd> + <kbd>Enter</kbd>.
- Selectief uitvoeren: als u een gedeelte van een script wilt uitvoeren, selecteert u de tekst die u wilt uitvoeren en klikt u vervolgens op de knop **script uitvoeren** . Of druk op <kbd>F5</kbd>.
- Context gevoelige Help: Typ `Invoke-Item` en druk op <kbd>F1</kbd>. Het Help-bestand wordt geopend in het artikel voor de `Invoke-Item` cmdlet.

Met de Windows PowerShell ISE kunt u bepaalde aspecten van het uiterlijk aanpassen. Het bevat ook een eigen Windows Power shell-profiel script.

## <a name="to-start-the-windows-powershell-ise"></a>De Windows PowerShell ISE starten

Klik op **Start** , selecteer **Windows Power shell** en klik vervolgens op **Windows PowerShell ISE** .
U kunt ook `powershell_ise.exe` een wille keurige opdracht shell of in het vak uitvoeren typen.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Als u hulp wilt krijgen in de Windows PowerShell ISE

Klik in het menu **Help** op **Help van Windows Power shell** . Of druk op <kbd>F1</kbd>. In het bestand dat wordt geopend, worden Windows PowerShell ISE en Windows Power shell beschreven, inclusief alle Help-informatie die beschikbaar is via de `Get-Help` cmdlet.
