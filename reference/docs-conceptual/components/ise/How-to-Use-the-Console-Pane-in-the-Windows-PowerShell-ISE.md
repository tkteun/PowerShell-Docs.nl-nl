---
ms.date: 01/02/2020
keywords: Power shell, cmdlet
title: Het consolevenster gebruiken in Windows PowerShell ISE
ms.openlocfilehash: f0ef07e410ed494f5732eab360c4e050c9c09a7f
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736144"
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a>Het consolevenster gebruiken in Windows PowerShell ISE

Het console venster in de Windows Power shell Integrated Scripting Environment (ISE) werkt precies hetzelfde als het zelfstandige Windows PowerShell ISE-console venster.

Als u een opdracht wilt uitvoeren in het console venster, typt u een opdracht en drukt u vervolgens op <kbd>Enter</kbd>. Als u meerdere opdrachten wilt invoeren die u wilt uitvoeren, typt u <kbd>SHIFT</kbd>+<kbd>invoeren</kbd> tussen de opdrachten. Zie [Tab-aanvulling gebruiken in het Script venster en console venster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) voor meer informatie over het typen van opdrachten.

Als u een opdracht wilt stoppen, klikt u op de werk balk op **Stop bewerking**of drukt u op <kbd>CTRL</kbd>+- <kbd>einde</kbd>. U kunt ook <kbd>CTRL</kbd>+<kbd>C</kbd> gebruiken om een opdracht te stoppen als de context ondubbelzinnig is. Als er bijvoorbeeld tekst in het huidige deel venster is geselecteerd, wordt de Kopieer bewerking door <kbd>CTRL</kbd>+<kbd>C</kbd> toegewezen.

Vanaf Windows Power Shell v3 is het deel venster uitvoer gecombineerd met het console venster. Dit heeft als voor deel dat u werkt als de zelfstandige Windows Power shell-console en elimineert de verschillen in procedures die nodig waren toen ze gescheiden werden. U kunt:

- Selecteer en Kopieer tekst vanuit het console venster naar het klem bord om te plakken in een ander venster. Als u tekst wilt selecteren, klikt u in het deel venster uitvoer op de muis en houdt u de muis aanwijzer over de tekst die u wilt vastleggen. U kunt ook de pijl toetsen van de cursor gebruiken terwijl u <kbd>SHIFT</kbd> ingedrukt houdt om tekst te selecteren. Druk vervolgens op <kbd>CTRL</kbd>+<kbd>C</kbd> of op het pictogram **kopiëren** op de werk balk.

- De geselecteerde tekst op de huidige cursor positie plakken. Klik op het pictogram **Plakken** op de werk balk.

- Alle tekst in het console venster wissen. Als u het console venster wilt wissen, klikt u op het pictogram **console selectie vakje** op de werk balk of voert u de opdracht uit `Clear-Host` of de alias `cls`.

## <a name="see-also"></a>Zie ook

- [Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
