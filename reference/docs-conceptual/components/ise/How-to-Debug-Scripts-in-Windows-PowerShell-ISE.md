---
ms.date: 01/02/2020
keywords: Power shell, cmdlet
title: Fouten opsporen in scripts in Windows PowerShell ISE
ms.openlocfilehash: c5da80f3e0e013448533c80bbe1957a301be38f5
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737114"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Fouten opsporen in scripts in Windows PowerShell ISE

In dit artikel wordt beschreven hoe u fouten kunt opsporen in scripts op een lokale computer met behulp van Windows Power shell Integrated Scripting Environment (ISE) Visual Debug-functies.

## <a name="how-to-manage-breakpoints"></a>Onderbrekings punten beheren

Een onderbrekings punt is een aangewezen plaats in een script waar u de bewerking wilt onderbreken, zodat u de huidige status van de variabelen en de omgeving waarin uw script wordt uitgevoerd, kunt onderzoeken.
Zodra het script is onderbroken door een onderbrekings punt, kunt u opdrachten uitvoeren in het console venster om de status van uw script te controleren. U kunt variabelen uitvoeren of andere opdrachten uit te voeren. U kunt zelfs de waarde wijzigen van variabelen die zichtbaar zijn voor de context van het script dat momenteel wordt uitgevoerd. Nadat u hebt onderzocht wat u wilt zien, kunt u de werking van het script hervatten.

U kunt drie typen onderbrekings punten instellen in de Windows Power shell-omgeving voor fout opsporing:

1. **Onderbrekings punt van regel**. Het script wordt gepauzeerd wanneer de aangewezen regel wordt bereikt tijdens de werking van het script

1. **Onderbrekings punt van variabele.** Het script wordt onderbroken wanneer de waarde van de aangewezen variabele wordt gewijzigd.

1. **Opdracht onderbrekings punt.** Het script wordt onderbroken wanneer de aangewezen opdracht wordt uitgevoerd tijdens de werking van het script. Het kan para meters bevatten voor het verder filteren van het onderbrekings punt tot alleen de gewenste bewerking. De opdracht kan ook een functie zijn die u hebt gemaakt.

Van deze opties kunt u in de omgeving Windows PowerShell ISE fout opsporing alleen regel onderbrekingen instellen met behulp van het menu of de sneltoetsen. De andere twee typen onderbrekings punten kunnen worden ingesteld, maar ze worden ingesteld vanuit het console venster met behulp van de cmdlet [set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md) . In deze sectie wordt beschreven hoe u fout opsporing in Windows PowerShell ISE kunt uitvoeren met behulp van de menu's die beschikbaar zijn, en voert u een breder scala van opdrachten uit vanuit het console venster met behulp van scripts.

### <a name="to-set-a-breakpoint"></a>Een onderbrekingspunt instellen

Een onderbrekings punt kan alleen in een script worden ingesteld nadat het is opgeslagen. Klik met de rechter muisknop op de regel waar u een regel onderbrekings punt wilt instellen en klik vervolgens op **onderbrekings punt in**-en uitschakelen. Of klik op de regel waar u een regel onderbrekings punt wilt instellen en druk op <kbd>F9</kbd> of Klik in het menu **fout opsporing** op **onderbrekings punt in**-en uitschakelen.

Het volgende script is een voor beeld van hoe u een variabele-onderbrekings punt vanuit het console venster kunt instellen met behulp van de cmdlet [set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md) .

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Alle onderbrekings punten weer geven

Geeft alle onderbrekings punten in de huidige Windows Power shell-sessie weer.

Klik in het menu **fout opsporing** op **lijst onderbrekings punten**. Het volgende script is een voor beeld van hoe u alle onderbrekings punten in het console venster kunt weer geven met behulp van de cmdlet [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) .

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Een onderbrekings punt verwijderen

Als u een onderbrekings punt verwijdert, wordt dit verwijderd.

Als u denkt dat u het later opnieuw wilt gebruiken, kunt u overwegen [een onderbrekings punt](#disable-a-breakpoint) in plaats daarvan uit te scha kelen. Klik met de rechter muisknop op de regel waar u een onderbrekings punt wilt verwijderen en klik vervolgens op **ToggleBreakpoint**.
Of klik op de regel waar u een onderbrekings punt wilt verwijderen en klik in het menu **fout opsporing** op **onderbrekings punt in-/uitschakelen**. Het volgende script is een voor beeld van het verwijderen van een onderbrekings punt met een opgegeven ID vanuit het console venster met behulp van de cmdlet [Remove-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Remove-PSBreakpoint.md) .

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Alle onderbrekings punten verwijderen

Als u alle onderbrekings punten die in de huidige sessie zijn gedefinieerd, wilt verwijderen, klikt u in het menu **fout opsporing** op **alle onderbrekings punten verwijderen**.

Het volgende script is een voor beeld van het verwijderen van alle onderbrekings punten vanuit het console venster met behulp van de cmdlet [Remove-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Remove-PSBreakpoint.md) .

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Een onderbrekings punt uitschakelen

Als u een onderbrekings punt uitschakelt, wordt deze niet verwijderd. het wordt uitgeschakeld totdat deze is ingeschakeld. Als u een specifieke regel onderbreking wilt uitschakelen, klikt u met de rechter muisknop op de regel waar u een onderbrekings punt wilt uitschakelen en klikt u vervolgens op **onderbrekings punt uitschakelen**. Of klik op de regel waar u een onderbrekings punt wilt uitschakelen en druk op <kbd>F9</kbd> of Klik in het menu **fout opsporing** op **onderbrekings punt uitschakelen**. Het volgende script is een voor beeld van hoe u een onderbrekings punt met een opgegeven ID uit het console venster kunt verwijderen met de cmdlet [Disable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Disable-PSBreakpoint.md) .

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Alle onderbrekings punten uitschakelen

Als u een onderbrekings punt uitschakelt, wordt deze niet verwijderd. het wordt uitgeschakeld totdat deze is ingeschakeld. Als u alle onderbrekings punten in de huidige sessie wilt uitschakelen, klikt u in het menu **fout opsporing** op **alle onderbrekings punten uitschakelen**. Het volgende script is een voor beeld van hoe u alle onderbrekings punten vanuit het console venster kunt uitschakelen met behulp van de cmdlet [Disable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Disable-PSBreakpoint.md) .

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Een onderbrekings punt inschakelen

Als u een specifieke onderbrekings punt wilt inschakelen, klikt u met de rechter muisknop op de regel waar u een onderbrekings punt wilt inschakelen en klikt u vervolgens op **onderbrekings punt inschakelen**. Of klik op de regel waar u een onderbrekings punt wilt inschakelen en druk op <kbd>F9</kbd> of Klik in het menu **fout opsporing** op **onderbrekings punt inschakelen**. Het volgende script is een voor beeld van hoe u specifieke onderbrekings punten vanuit het console venster kunt inschakelen met behulp van de cmdlet [Enable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Enable-PSBreakpoint.md) .

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Alle onderbrekings punten inschakelen

Als u alle onderbrekings punten die in de huidige sessie zijn gedefinieerd, wilt inschakelen, klikt u in het menu **fout opsporing** op **alle onderbrekings punten inschakelen**. Het volgende script is een voor beeld van hoe u alle onderbrekings punten vanuit het console venster kunt inschakelen met behulp van de cmdlet [Enable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Enable-PSBreakpoint.md) .

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Een foutopsporingssessie beheren

Voordat u de fout opsporing start, moet u een of meer onderbrekings punten instellen. U kunt geen onderbrekings punt instellen, tenzij het script waarvoor u fouten wilt opsporen, wordt opgeslagen. Zie voor instructies over het instellen van een onderbrekings punt, [onderbrekings punten](#how-to-manage-breakpoints) of [set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)beheren.
Nadat u de fout opsporing hebt gestart, kunt u een script pas bewerken nadat u de fout opsporing hebt gestopt. Een script met een of meer onderbrekings punten wordt automatisch opgeslagen voordat het wordt uitgevoerd.

### <a name="to-start-debugging"></a>Fout opsporing starten

Druk op <kbd>F5</kbd> of klik op de werk balk op het pictogram **script uitvoeren** of Klik in het menu **fout opsporing** op **uitvoeren/door gaan**. Het script wordt uitgevoerd totdat het eerste onderbrekings punt wordt aangetroffen. Hiermee wordt de bewerking gepauzeerd en wordt de regel gemarkeerd waarop deze wordt onderbroken.

### <a name="to-continue-debugging"></a>Fout opsporing voortzetten

Druk op <kbd>F5</kbd> of klik op de werk balk op het pictogram **script uitvoeren** of Klik in het menu **fout opsporing** op **uitvoeren/door gaan** of, in het deel venster console, typ `C` en druk op <kbd>Enter</kbd>. Dit zorgt ervoor dat het script wordt voortgezet op het volgende onderbrekings punt of aan het einde van het script als er geen verdere onderbrekings punten worden gevonden.

### <a name="to-view-the-call-stack"></a>De aanroep stack weer geven

In de aanroep stack wordt de huidige uitvoerings locatie in het script weer gegeven. Als het script wordt uitgevoerd in een functie die is aangeroepen door een andere functie, wordt deze in de uitvoer weer gegeven op extra rijen. In de onderste rij worden het oorspronkelijke script en de regel weer gegeven waarin een functie is aangeroepen. Bij de volgende regel omhoog ziet u die functie en de regel waarin een andere functie mogelijk is aangeroepen. In de bovenste rij wordt de huidige context van de huidige regel weer gegeven waarop het onderbrekings punt is ingesteld.

Als u de huidige aanroep stack wilt weer geven, drukt u op <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd> of klikt u in het menu **fout opsporing** op **aanroep stack weer geven** of in het deel venster console, typt u `K` en drukt u vervolgens op <kbd>Enter</kbd>.

### <a name="to-stop-debugging"></a>Fout opsporing stoppen

Druk op <kbd>SHIFT</kbd>+<kbd>F5</kbd> of Klik in het menu **debug** op **debugger stoppen**of typ `Q` in het console venster en druk op <kbd>Enter</kbd>.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Stap over, Step Into en uitstappen tijdens het opsporen van fouten

Step ping is het proces van het uitvoeren van één instructie per keer. U kunt stoppen met een regel code en de waarden van variabelen en de status van het systeem onderzoeken. In de volgende tabel worden veelvoorkomende fout opsporingsgegevens beschreven, zoals het door lopen, door lopen en uitstappen.

| Fout opsporen taak |                                                                                                                   Beschrijving                                                                                                                    |                                                      Hoe u dit kunt doen in Power shell ISE                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Stap in**  | Voert de huidige instructie uit en stopt bij de volgende instructie. Als de huidige instructie een functie of script aanroep is, worden de stappen voor het fout opsporingsprogramma in die functie of dit script uitgevoerd, anders stopt het met de volgende instructie.                      | Druk op <kbd>F11</kbd> of Klik in het menu **fout opsporing** op **stap in**of typ `S` in het deel venster console en druk op <kbd>Enter</kbd>.                 |
| **Stap over**  | Voert de huidige instructie uit en stopt bij de volgende instructie. Als de huidige instructie een functie of script aanroep is, voert het fout opsporingsprogramma de volledige functie of het script uit en stopt het met de volgende instructie na de functie aanroep. | Druk op <kbd>F10</kbd> of Klik in het menu **fout opsporing** op **stap over**, of typ `V` in het console venster en druk op <kbd>Enter</kbd>.                 |
| **Stap uit**   | Stappen van de huidige functie en één niveau omhoog als de functie is genest. In de hoofd tekst wordt het script uitgevoerd naar het einde of naar het volgende onderbrekings punt. De overgeslagen instructies worden uitgevoerd, maar niet getrapt via.                   | Druk op <kbd>SHIFT</kbd>+<kbd>F11</kbd>of Klik in het menu **fout opsporing** op **stap uit**of typ `O` in het console venster en druk op <kbd>Enter</kbd>. |
| **Doen**   | Gaat verder met de uitvoering naar het einde of naar het volgende onderbrekings punt. De overgeslagen functies en aanroepen worden uitgevoerd, maar niet door lopen.                                                                                                          | Druk op <kbd>F5</kbd> of Klik in het menu **fout opsporing** op **uitvoeren/door gaan**of typ `C` in het deel venster console en druk op <kbd>Enter</kbd>.               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>De waarden van variabelen weer geven tijdens fout opsporing

U kunt de huidige waarden van variabelen in het script weer geven tijdens het door lopen van de code.

### <a name="to-display-the-values-of-standard-variables"></a>De waarden van standaard variabelen weer geven

Hanteer één van de volgende methoden:

- Beweeg de muis aanwijzer over de variabele in het deel venster script om de waarde weer te geven als knop info.

- Typ de naam van de variabele in het console venster en druk op <kbd>Enter</kbd>.

Alle deel Vensters in ISE vallen altijd binnen hetzelfde bereik. Daarom kunt u tijdens het opsporen van fouten in een script de opdrachten die u in het console venster typt, uitvoeren in het bereik script. Hiermee kunt u het console venster gebruiken om de waarden van variabelen te vinden en functies aan te roepen die alleen in het script zijn gedefinieerd.

### <a name="to-display-the-values-of-automatic-variables"></a>De waarden van automatische variabelen weer geven

U kunt de voor gaande methode gebruiken om de waarde van vrijwel alle variabelen weer te geven tijdens het opsporen van fouten in een script. Deze methoden werken echter niet voor de volgende automatische variabelen.

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

Als u probeert de waarde van een van deze variabelen weer te geven, krijgt u de waarde van die variabele voor in een interne pijp lijn die wordt gebruikt door het fout opsporingsprogramma, niet de waarde van de variabele in het script. U kunt dit voor enkele variabelen (`$_`, `$Input`, `$MyInvocation`, `$PSBoundParameters`en `$Args`) omzeilen met behulp van de volgende methode:

1. Wijs in het script de waarde van de automatische variabele toe aan een nieuwe variabele.

1. Geef de waarde van de nieuwe variabele weer door de muis aanwijzer over de nieuwe variabele in het Script venster te bewegen of door de nieuwe variabele in het console venster te typen.

Als u bijvoorbeeld de waarde van de variabele `$MyInvocation` wilt weer geven, wijst u in het script de waarde toe aan een nieuwe variabele, zoals `$scriptName`, houdt u de muis aanwijzer over of typt u de `$scriptName` variabele om de waarde ervan weer te geven.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Zie ook

- [Kennismaking met Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
