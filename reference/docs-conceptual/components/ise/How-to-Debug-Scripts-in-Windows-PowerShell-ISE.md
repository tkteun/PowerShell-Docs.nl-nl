---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Fouten opsporen in scripts in Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086864"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Fouten opsporen in scripts in Windows PowerShell ISE

In dit artikel wordt beschreven hoe u fouten opsporen in scripts op een lokale computer met behulp van de visuele foutopsporing functies voor Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Over het beheren van onderbrekingspunten

Een onderbrekingspunt is een aangewezen plaats in een script waar u graag bewerking te onderbreken, zodat u kunt controleren dat de huidige status van de variabelen en de omgeving waarin het script wordt uitgevoerd. Nadat het script is onderbroken door een onderbrekingspunt, kunt u opdrachten uitvoeren in het consolevenster het onderzoeken van de status van uw script.  U kunt variabelen uitvoer of andere opdrachten uitvoeren. De waarde van eventuele variabelen die zichtbaar voor de context van het script op dat moment wordt uitgevoerd zijn, kunt u zelfs wijzigen. Nadat u hebt gecontroleerd wat u wilt zien, kunt u de werking van het script kunt hervatten.

U kunt drie soorten onderbrekingspunten instellen in de Windows PowerShell-foutopsporing omgeving:

1. **Onderbrekingspunt regel**. Het script wordt onderbroken wanneer de opgegeven regel is bereikt tijdens de bewerking van het script

2. **Variabele onderbrekingspunt.** Het script wordt onderbroken wanneer de waarde van de opgegeven variabele wordt gewijzigd.

3. **Opdracht onderbrekingspunt.** Het script wordt onderbroken wanneer de opgegeven opdracht wordt uitgevoerd tijdens de bewerking van het script. Parameters voor het verder het onderbrekingspunt moet alleen de bewerking die u wilt filteren kan bevatten. De opdracht kan ook worden voor een functie die u hebt gemaakt.

Deze in de omgeving van de Windows PowerShell ISE-foutopsporing, kunnen alleen regel onderbrekingspunten worden ingesteld met behulp van het menu of de sneltoetsen. De andere twee typen onderbrekingspunten kunnen worden ingesteld, maar ze worden ingesteld van het consolevenster met behulp van de [Set PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet. Deze sectie wordt beschreven hoe u taken voor foutopsporing in Windows PowerShell ISE uitvoeren met behulp van de menu's, indien beschikbaar, en een groot aantal opdrachten uitvoeren vanaf het consolevenster met behulp van scripts.

### <a name="to-set-a-breakpoint"></a>Een onderbrekingspunt instellen

Pas nadat deze is opgeslagen, kan er een onderbrekingspunt in een script worden ingesteld. Met de rechtermuisknop op de regel waar u Stel een onderbrekingspunt regel en klik vervolgens op **onderbrekingspunt**. Of klik op de regel waar u om in te stellen van een onderbrekingspunt regel en druk op **F9** of Ga naar de **Debug** menu, klikt u op **onderbrekingspunt**.

Het volgende script is een voorbeeld van hoe u een onderbrekingspunt in de variabele van het consolevenster instellen met behulp van kunt de [Set PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Lijst van alle onderbrekingspunten

Geeft alle onderbrekingspunten in de huidige Windows PowerShell-sessie.

Op de **Debug** menu, klikt u op **lijst onderbrekingspunten**. Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten in het consolevenster weergeven met behulp van kunt de [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Een onderbrekingspunt verwijderen

Een onderbrekingspunt verwijderen, wordt deze verwijderd.

Als u denkt u het later opnieuw gebruiken dat, moet u mogelijk wilt [uitschakelen van een onderbrekingspunt](#disable-a-breakpoint) deze in plaats daarvan.
Met de rechtermuisknop op de regel waar u een onderbrekingspunt verwijderen en klik vervolgens op **onderbrekingspunt**.
Of klik op de regel waar u wilt een onderbrekingspunt verwijderen en klik op de **Debug** menu, klikt u op **onderbrekingspunt**.
Het volgende script is een voorbeeld van hoe u een onderbrekingspunt met een opgegeven ID van het consolevenster verwijderen met behulp van de [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Verwijder alle onderbrekingspunten

Verwijderen van alle onderbrekingspunten die zijn gedefinieerd in de huidige sessie op de **Debug** menu, klikt u op **onderbrekingspunten verwijderen**.

Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten uit het consolevenster verwijdert met behulp van de [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Een onderbrekingspunt uitschakelen

Uitschakelen van een onderbrekingspunt wordt niet verwijderd. deze uitgeschakeld totdat deze is ingeschakeld.  Als u wilt een onderbrekingspunt specifieke regel uitschakelen, met de rechtermuisknop op de regel waar u een onderbrekingspunt uitschakelen en klik vervolgens op **onderbrekingspunt uitschakelen**. Of klik op de regel waar u wilt een onderbrekingspunt uitschakelen en druk op **F9** of Ga naar de **Debug** menu, klikt u op **onderbrekingspunt uitschakelen**. Het volgende script is een voorbeeld van hoe u een onderbrekingspunt met een opgegeven ID van het consolevenster verwijderen met behulp van kunt de [uitschakelen PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Alle onderbrekingspunten uitschakelen

Uitschakelen van een onderbrekingspunt wordt niet verwijderd. deze uitgeschakeld totdat deze is ingeschakeld.  Alle onderbrekingspunten uitschakelen in de huidige sessie op de **Debug** menu, klikt u op **alle onderbrekingspunten uitschakelen**. Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten in het consolevenster uitschakelen met behulp van kunt de [uitschakelen PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Een onderbrekingspunt inschakelen

Als u wilt inschakelen op een specifieke onderbrekingspunt, met de rechtermuisknop op de regel waar u een onderbrekingspunt inschakelen en klik vervolgens op **onderbrekingspunt inschakelen**. Of klik op de regel waar u wilt een onderbrekingspunt inschakelen en druk vervolgens op **F9** of Ga naar de **Debug** menu, klikt u op **onderbrekingspunt inschakelen**. Het volgende script is een voorbeeld van hoe u specifieke onderbrekingspunten in het consolevenster inschakelen met behulp van kunt de [inschakelen PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Alle onderbrekingspunten inschakelen

Om in te schakelen van alle onderbrekingspunten die zijn gedefinieerd in de huidige sessie op de **Debug** menu, klikt u op **alle onderbrekingspunten**. Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten in het consolevenster inschakelen met behulp van kunt de [inschakelen PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Over het beheren van een sessie voor foutopsporing

Voordat u begint met het opsporen van fouten, moet u een of meer onderbrekingspunten instellen. U kunt een onderbrekingspunt niet instellen als het script dat u fouten wilt opsporen wordt opgeslagen. Zie voor instructies over hoe u een onderbrekingspunt instellen, [over het beheren van onderbrekingspunten](#how-to-manage-breakpoints) of [Set PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Nadat u foutopsporing hebt gestart, kunt u een script niet bewerken totdat u stop de foutopsporing. Een script met een of meer onderbrekingspunten instellen wordt automatisch opgeslagen voordat deze wordt uitgevoerd.

### <a name="to-start-debugging"></a>Foutopsporing te starten

Druk op **F5** of klik op de werkbalk op de **-Script uitvoeren** pictogram, of op de **Debug** menu klikt u op **uitvoeren/doorgaan**. Het script wordt uitgevoerd totdat het eerste onderbrekingspunt worden aangetroffen. Deze bewerking daar pauzeert en markeert u de regel waarop het programma is onderbroken.

### <a name="to-continue-debugging"></a>Om door te gaan met het opsporen van fouten

Druk op **F5** of klik op de werkbalk op de **-Script uitvoeren** pictogram, of op de **Debug** menu, klikt u op **uitvoeren/doorgaan** of typ in het consolevenster **C** en druk vervolgens op **ENTER**. Dit zorgt ervoor dat het script om door te gaan naar het volgende onderbrekingspunt bereikt of aan het einde van het script wordt uitgevoerd als er geen verdere onderbrekingspunten optreden.

### <a name="to-view-the-call-stack"></a>Om de aanroepstack weer te geven

De aanroepstack geeft de huidige locatie van de uitvoering in het script. Als het script wordt uitgevoerd in een functie die door een andere functie is aangeroepen, klikt u vervolgens die wordt weergegeven in de weergave door extra rijen in de uitvoer. De onderste rij geeft het oorspronkelijke script en de regel in het waarin een functie is aangeroepen. De volgende regel geeft die functie en de regel in het waarin een andere functie mogelijk hebben aangeroepen.  De bovenste rij geeft de huidige context van de huidige regel waarop het onderbrekingspunt is ingesteld.

Terwijl onderbroken, om te zien van de huidige aanroepstack, drukt u op **CTRL + SHIFT + D** of Ga naar de **Debug** menu, klikt u op **weergave Call Stack** of typ in het consolevenster **K**  en druk vervolgens op **ENTER**.

### <a name="to-stop-debugging"></a>Om te stoppen met het opsporen van fouten

Druk op **SHIFT-F5** of Ga naar de **fouten opsporen in** menu, klikt u op **foutopsporingsprogramma stopt**, of typ in het consolevenster **Q** en druk vervolgens op  **Voer**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Stap over, binnengaat en stap uit tijdens het opsporen van fouten

Stap voor stap is het proces van het uitvoeren van één instructie tegelijkertijd. U kunt stoppen op een regel code, en bekijk de waarden van variabelen en de status van het systeem. De volgende tabel beschrijft de algemene taken voor foutopsporing, zoals stapsgewijs via, schemas en stapsgewijs uit.

| Debugging Task | Description | Het doel wordt gerealiseerd wel in PowerShell ISE |
| --- | --- | --- |
| **Stap in** | De huidige instructie uitgevoerd en vervolgens bij de volgende instructie wordt gestopt. Als de huidige instructie een functie of scriptaanroep, wordt het foutopsporingsprogramma stappen in deze functie of het script is, anders wordt gestopt bij de volgende instructie. | Druk op **F11** of Ga naar de **fouten opsporen in** menu, klikt u op **stap**, of typ in het consolevenster **S** en druk op **ENTER**. |
| **Stap Over** | De huidige instructie uitgevoerd en vervolgens bij de volgende instructie wordt gestopt. Als de huidige instructie is een functie of scriptaanroep, wordt het foutopsporingsprogramma voert de gehele functie of het script en wordt gestopt bij de volgende instructie na de aanroep van de functie. | Druk op **F10** of Ga naar de **Debug** menu, klikt u op **stap Over**, of typ in het consolevenster **V** en druk op **ENTER**. |
| **Stap uit** | Stap uit de huidige functie en Eén niveau als de functie is genest. Als in de hoofdtekst, het script is uitgevoerd naar het einde of naar het volgende onderbrekingspunt bereikt. De overgeslagen instructies zijn uitgevoerd, maar niet via getrapte. | Druk op **SHIFT + F11**, of op de **Debug** menu, klikt u op **stap uit**, of typ in het consolevenster **O** en druk op **ENTER**. |
| **Doorgaan** | Verder kan worden uitgevoerd naar het einde of naar het volgende onderbrekingspunt bereikt. De overgeslagen functies en aanroepen uitgevoerd, maar niet via getrapte. | Druk op **F5** of Ga naar de **Debug** menu, klikt u op **uitvoeren/doorgaan**, of typ in het consolevenster **C** en druk op **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Hoe de waarden van variabelen weergeven tijdens het opsporen van fouten

U kunt de huidige waarden van variabelen in het script weergeven tijdens het doorlopen van de code.

### <a name="to-display-the-values-of-standard-variables"></a>Om weer te geven van de waarden van variabelen voor de standard

Gebruik een van de volgende methoden:

- In het scriptvenster de muisaanwijzer over de variabele om de waarde ervan als knopinfo weer te geven.

- Typ in het consolevenster de naam van variabele en druk op **ENTER**.

Alle vensters in ISE zich altijd in hetzelfde bereik. Daardoor worden tijdens de foutopsporing een script, de opdrachten die u in het consolevenster typt uitgevoerd binnen het bereik van script. Hiermee kunt u het consolevenster gebruiken om te zoeken naar de waarden van variabelen en functies die zijn gedefinieerd alleen in het script aanroepen.

### <a name="to-display-the-values-of-automatic-variables"></a>Om de waarden van automatische variabelen weer te geven

U kunt de bovenstaande methode gebruiken om weer te geven van de waarde van bijna alle variabelen tijdens de foutopsporing van een script. Deze methoden werken echter niet voor de volgende automatische variabelen.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Als u probeert om de waarde van een van deze variabelen weer te geven, krijgt u de waarde van die variabele voor in een interne pijplijn het foutopsporingsprogramma-gebruikt, niet de waarde van de variabele in het script. U kunt dit voorkomen werken voor enkele variabelen ($_, $Input, $MyInvocation, $PSBoundParameters en $Args) met behulp van de volgende methode:

1. In het script, moet u de waarde van de automatische variabele toewijzen aan een nieuwe variabele.

2. De waarde van de nieuwe variabele weergeven door de muiswijzer op de nieuwe variabele in het scriptvenster of door te typen van de nieuwe variabele in het consolevenster.

Bijvoorbeeld, als de waarde van de variabele $MyInvocation in het script weergeven, de waarde toewijzen aan een nieuwe variabele, zoals $scriptname, en vervolgens Beweeg de muisaanwijzer over of typt u de variabele $scriptname om de waarde ervan weer te geven.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Zie ook

- [Kennismaking met Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)