---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Fouten opsporen in scripts in Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30953402"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Fouten opsporen in scripts in Windows PowerShell ISE

Dit artikel wordt beschreven hoe u fouten opsporen in scripts op een lokale computer met behulp van de visuele foutopsporing functies voor Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Onderbrekingspunten beheren

Een onderbrekingspunt is een aangewezen plaats in een script waar u de bewerking dat wilt te onderbreken, zodat u kunt controleren dat de huidige status van de variabelen en de omgeving waarin het script wordt uitgevoerd. Nadat het script is onderbroken door een onderbrekingspunt, kunt u opdrachten uitvoeren in het consolevenster de status van uw script te onderzoeken.  U kunt uitvoer variabelen of andere opdrachten uitvoeren. De waarde van eventuele variabelen die zichtbaar voor de context van het script dat wordt uitgevoerd zijn, kunt u ook wijzigen. Nadat u hebt onderzocht wat u wilt zien, kunt u de werking van het script hervatten.

U kunt drie soorten onderbrekingspunten instellen in de Windows PowerShell-foutopsporingsomgeving:

1. **Regel onderbrekingspunt**. Het script wordt onderbroken wanneer de aangewezen regel wordt bereikt tijdens de bewerking van het script

2. **Variabele onderbrekingspunt.** Het script wordt onderbroken wanneer de waarde van de aangewezen variabele wordt gewijzigd.

3. **Opdracht onderbrekingspunt.** Het script wordt onderbroken wanneer de opgegeven opdracht wordt uitgevoerd tijdens de bewerking van het script. Parameters voor het verder filteren het onderbrekingspunt moet alleen de gewenste bewerking kan bevatten. De opdracht kan ook worden voor een functie die u hebt gemaakt.

Deze waarden in de Windows PowerShell ISE foutopsporingsomgeving kunnen alleen regel onderbrekingspunten worden ingesteld met behulp van het menu of de sneltoetsen. De andere twee soorten onderbrekingspunten kunnen worden ingesteld, maar ze worden ingesteld van het consolevenster met behulp van de [Set PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet. Deze sectie wordt beschreven hoe u kunt taken voor foutopsporing in Windows PowerShell ISE uitvoeren met behulp van de menu's, indien beschikbaar, en een breed scala aan opdrachten uitvoeren vanaf het consolevenster met behulp van scripts.

### <a name="to-set-a-breakpoint"></a>Een onderbrekingspunt instellen

Pas nadat deze is opgeslagen, kan er een onderbrekingspunt in een script worden ingesteld. Met de rechtermuisknop op de regel waar u een regel onderbrekingspunt instellen en klik vervolgens op **onderbrekingspunt**. Of klik op de regel waar u stelt een onderbrekingspunt regel en druk op **F9** of Ga naar de **Debug** menu, klikt u op **onderbrekingspunt**.

Het volgende script is een voorbeeld van hoe u een variabele onderbrekingspunt van het consolevenster instellen met behulp van kunt de [Set PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Lijst van alle onderbrekingspunten

Geeft alle onderbrekingspunten in de huidige Windows PowerShell-sessie.

Op de **Debug** menu, klikt u op **lijst onderbrekingspunten**. Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten van het consolevenster weergeven met behulp van kunt de [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Een onderbrekingspunt verwijderen

Een onderbrekingspunt verwijderen, wordt deze verwijderd.

Als u denkt u het later opnieuw gebruiken dat, kunt u mogelijk wilt [uitschakelen van een onderbrekingspunt](#disable-a-breakpoint) deze in plaats daarvan.
Met de rechtermuisknop op de regel waar u een onderbrekingspunt verwijderen en klik vervolgens op **onderbrekingspunt**.
Of klik op de regel waar u wilt een onderbrekingspunt verwijderen en klik op de **Debug** menu, klikt u op **onderbrekingspunt**.
Het volgende script is een voorbeeld van een onderbrekingspunt met een opgegeven ID van het consolevenster verwijderen met behulp van de [verwijderen PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Verwijder alle onderbrekingspunten

Verwijderen van alle onderbrekingspunten gedefinieerd in de huidige sessie op de **Debug** menu, klikt u op **onderbrekingspunten verwijderen**.

Het volgende script is een voorbeeld van hoe alle onderbrekingspunten verwijderen uit het consolevenster met behulp van de [verwijderen PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Een onderbrekingspunt uitschakelen

Een onderbrekingspunt uitschakelen wordt niet verwijderd. het uitgeschakeld totdat deze is ingeschakeld.  Met de rechtermuisknop op de regel waar u een onderbrekingspunt uitschakelen en klik vervolgens op als wilt uitschakelen op een specifieke regel onderbrekingspunt, **onderbrekingspunt uitschakelen**. Of klik op de regel waar u wilt een onderbrekingspunt uitschakelen en druk op **F9** of Ga naar de **Debug** menu, klikt u op **onderbrekingspunt uitschakelen**. Het volgende script is een voorbeeld van hoe u een onderbrekingspunt met een opgegeven ID van het consolevenster verwijderen met behulp van kunt de [uitschakelen PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Alle onderbrekingspunten uitschakelen

Een onderbrekingspunt uitschakelen wordt niet verwijderd. het uitgeschakeld totdat deze is ingeschakeld.  Alle onderbrekingspunten uitschakelen in de huidige sessie op de **Debug** menu, klikt u op **alle onderbrekingspunten uitschakelen**. Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten van het consolevenster uitschakelen met behulp van kunt de [uitschakelen PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Een onderbrekingspunt inschakelen

Om een specifieke onderbrekingspunt, met de rechtermuisknop op de regel waar u een onderbrekingspunt inschakelen en klik vervolgens op **onderbrekingspunt inschakelen**. Of klik op de regel waar u wilt een onderbrekingspunt inschakelen en druk vervolgens op **F9** of Ga naar de **Debug** menu, klikt u op **onderbrekingspunt inschakelen**. Het volgende script is een voorbeeld van hoe u specifieke onderbrekingspunten van het consolevenster inschakelen met behulp van kunt de [inschakelen PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Alle onderbrekingspunten inschakelen

U alle onderbrekingspunten gedefinieerd in de huidige sessie op de **Debug** menu, klikt u op **alle onderbrekingspunten**. Het volgende script is een voorbeeld van hoe u alle onderbrekingspunten van het consolevenster inschakelen met behulp van kunt de [inschakelen PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Het beheren van een sessie voor foutopsporing

Voordat u foutopsporing, moet u een of meer onderbrekingspunten instellen. U kunt een onderbrekingspunt niet instellen, tenzij het script dat u fouten wilt opsporen wordt opgeslagen. Zie voor instructies over hoe u kunt geen onderbrekingspunt instellen [onderbrekingspunten beheren](#how-to-manage-breakpoints) of [Set PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). Nadat u foutopsporing hebt gestart, kunt u een script niet bewerken, totdat u stopt met het opsporen van fouten. Een script met een of meer onderbrekingspunten die zijn ingesteld, wordt automatisch opgeslagen voordat deze wordt uitgevoerd.

### <a name="to-start-debugging"></a>Foutopsporing te starten

Druk op **F5** of klik op de werkbalk op de **-Script uitvoeren** pictogram, of op de **Debug** menu klikt u op **uitvoeren/doorgaan**. Het script wordt uitgevoerd totdat de eerste onderbrekingspunt aangetroffen. Deze bewerking daar pauzeert en markeert u de regel waarop het programma is onderbroken.

### <a name="to-continue-debugging"></a>Om door te gaan met het opsporen van fouten

Druk op **F5** of klik op de werkbalk op de **-Script uitvoeren** pictogram, of op de **fouten opsporen in** menu, klikt u op **uitvoeren/doorgaan** of typ in het consolevenster **C** en druk vervolgens op **ENTER**. Dit zorgt ervoor dat het script om door te gaan naar het volgende onderbrekingspunt of aan het einde van het script uitgevoerd als er geen verdere onderbrekingspunten optreden.

### <a name="to-view-the-call-stack"></a>De aanroepstack weergeven

De aanroepstack geeft de huidige locatie in het script wordt uitgevoerd. Als het script wordt uitgevoerd in een functie die is aangeroepen door een andere functie, vervolgens die wordt weergegeven in de weergave door extra rijen in de uitvoer. De onderste rij worden het oorspronkelijke script en de regel weergegeven in het waarin een functie is aangeroepen. De volgende regel geeft die functie en de regel in het waarin een andere functie mogelijk is aangeroepen.  De bovenste rij geeft de huidige context van de huidige regel waarop het onderbrekingspunt is ingesteld.

Terwijl onderbroken, om te zien van de huidige aanroepstack, drukt u op **CTRL + SHIFT + D** of Ga naar de **Debug** menu, klikt u op **weergave Call Stack** of typ in het consolevenster **K**  en druk vervolgens op **ENTER**.

### <a name="to-stop-debugging"></a>Foutopsporing stoppen

Druk op **SHIFT F5** of Ga naar de **Debug** menu, klikt u op **foutopsporingsprogramma stopt**, of typ in het consolevenster **Q** en druk vervolgens op  **Voer**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Het overslaan, stap en stap uit tijdens het opsporen van fouten

Stap voor stap is het proces van één instructie tegelijk uitvoeren. U kunt stoppen op een regel code en de waarde van variabelen en de status van het systeem controleren. De volgende tabel worden algemene taken voor foutopsporing zoals via doorlopen, selecteert u en selecteert u uit.

| Foutopsporing van taak | Beschrijving | Het uitvoeren van deze in de PowerShell ISE |
| --- | --- | --- |
| **In stap** | De huidige instructie worden uitgevoerd en stopt bij de volgende instructie. Als de huidige instructie een functie of script aanroep, wordt de foutopsporingsprogramma stappen in deze functie of script is, anders wordt gestopt bij de volgende instructie. | Druk op **F11** of Ga naar de **Debug** menu, klikt u op **stap**, of typ in het consolevenster **S** en druk op **ENTER**. |
| **Stap Over** | De huidige instructie worden uitgevoerd en stopt bij de volgende instructie. Als de huidige instructie is een functie of script aanroep, wordt het foutopsporingsprogramma wordt uitgevoerd de hele functie of het script en stopt bij de volgende instructie na de functieaanroep. | Druk op **F10** of Ga naar de **Debug** menu, klikt u op **stap Over**, of typ in het consolevenster **V** en druk op **ENTER**. |
| **Stap uit** | Stap buiten de huidige functie en één niveau als de functie is genest. Als het script in de hoofdtekst is uitgevoerd met het einde of voor het volgende onderbrekingspunt. De overgeslagen instructies zijn uitgevoerd, maar niet via met interval. | Druk op **SHIFT + F11**, of op de **Debug** menu, klikt u op **stap uit**, of typ in het consolevenster **O** en druk op **ENTER**. |
| **Doorgaan** | Kan worden uitgevoerd bij het einde of voor het volgende onderbrekingspunt blijft. De overgeslagen functies en aanroepen zijn wordt uitgevoerd, maar wordt niet gevolgd door. | Druk op **F5** of Ga naar de **Debug** menu, klikt u op **uitvoeren/doorgaan**, of typ in het consolevenster **C** en druk op **ENTER**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>De waarden van variabelen weergeven tijdens het opsporen van fouten

U kunt de huidige waarden van variabelen weergeven in het script tijdens het doorlopen van de code.

### <a name="to-display-the-values-of-standard-variables"></a>Om de waarden van standaard variabelen weer te geven

Gebruik een van de volgende methoden:

- In het scriptvenster de muisaanwijzer op de variabele in op de waarde wordt weergegeven als knopinfo.

- Typ in het consolevenster de naam van variabele en druk op **ENTER**.

Alle deelvensters in ISE zich altijd in dezelfde scope. Terwijl u fouten van een script opspoort, moet de opdrachten die u in het consolevenster typt uitgevoerd daarom in script-bereik. Hiermee kunt u het consolevenster gebruiken om te zoeken naar de waarden van variabelen en functies die zijn gedefinieerd in het script alleen aanroepen.

### <a name="to-display-the-values-of-automatic-variables"></a>Om de waarden van automatische variabelen weer te geven

De bovenstaande methode kunt u de waarde van bijna alle variabelen worden weergegeven terwijl u fouten een script opspoort. Deze methoden werkt echter niet voor de volgende automatische variabelen.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Als u probeert om de waarde van een van deze variabelen weer te geven, krijgt u de waarde van die variabele voor in een interne pijplijn het foutopsporingsprogramma wordt gebruikt, niet de waarde van de variabele in het script. U kunt omzeilen dit voor een aantal variabelen ($_, $Input $MyInvocation, $PSBoundParameters en $Args) met behulp van de volgende methode:

1. In het script moet u de waarde van de automatische variabele toewijzen aan een nieuwe variabele.

2. De waarde van de nieuwe variabele weergeven door de muiswijzer op de nieuwe variabele in het scriptvenster of door de nieuwe variabele in het consolevenster in te voeren.

Bijvoorbeeld, zodat de waarde van de variabele $MyInvocation in het script de waarde toewijzen aan een nieuwe variabele, zoals $scriptname, en vervolgens de muisaanwijzer of typt u de variabele $scriptname om de waarde ervan weer te geven.

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