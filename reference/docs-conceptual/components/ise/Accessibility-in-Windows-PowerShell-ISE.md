---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Toegankelijkheid in Windows PowerShell ISE
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 78a001dbe43a0b005d10a817e05e4cc7a72f5bd0
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403972"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Toegankelijkheid in Windows PowerShell ISE

Dit onderwerp beschrijft de toegankelijkheidsfuncties van Windows PowerShell Integrated Scripting Environment (ISE) die handig zijn wellicht.

* [Het wijzigen van de grootte en locatie van de Console en het Script deelvensters](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Sneltoetsen voor het bewerken van tekst](#keyboard-shortcuts-for-editing-text)
* [Sneltoetsen voor het uitvoeren van scripts](#keyboard-shortcuts-for-running-scripts)
* [Sneltoetsen voor het aanpassen van de weergave](#keyboard-shortcuts-for-customizing-the-view)
* [Sneltoetsen voor fouten opsporen in scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Sneltoetsen voor Windows PowerShell-tabbladen](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Sneltoetsen voor het starten en afsluiten](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft streeft ernaar om zijn producten en diensten gebruiksvriendelijker te maken voor iedereen. De volgende onderwerpen bevatten informatie over de functies, producten en services die Windows PowerShell ISE beter toegankelijk voor mensen met beperkingen.

Hoog contrast biedt ondersteuning voor Windows PowerShell ISE. Voor de slechtzienden onderbrekingspunt informatie is beschikbaar via de cmdlets voor het beheren van onderbrekingspunten, zoals [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) en [Set PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Zie voor meer informatie. 'Over het beheren van onderbrekingspunten' in [How to Debug Scripts in de Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Naast de toegankelijkheidsfuncties en hulpprogramma's in Microsoft Windows maken maken de volgende functies van Windows PowerShell ISE toegankelijker voor mensen met een handicap:

- Sneltoetsen

- Syntaxis kleur tabel en de mogelijkheid om verschillende andere om kleurinstellingen te wijzigen met behulp van de [$psISE.Options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) scripting-object.

- Grootte wijzigen van tekst

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Het wijzigen van de grootte en locatie van de Console en het Script deelvensters

De volgende stappen kunt u de locatie van het consolevenster en het scriptvenster en de grootte wijzigen. Wanneer u de Windows PowerShell ISE opnieuw opent, wordt de grootte en locatie aangebrachte wijzigingen worden bewaard.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Formaat van het scriptvenster en consolevenster

1. De muisaanwijzer op de regel splitsen tussen het scriptvenster en consolevenster onderbreken.

2. Wanneer de muisaanwijzer in een dubbele pijl verandert, Sleep de rand om de grootte van het deelvenster te wijzigen.

### <a name="to-move-the-script-pane-and-console-pane"></a>Het scriptvenster en consolevenster verplaatsen

Voer een van de volgende handelingen uit:

- Voor het verplaatsen van het scriptvenster boven het consolevenster, drukt u op **CTRL + 1** of klik op de werkbalk op de **Script deelvenster-bovenaan weergeven** pictogram, of in de **weergave** menu, klikt u op **weergeven Deelvenster boven script**.

- Voor het verplaatsen van het scriptvenster aan de rechterkant van het consolevenster, drukt u op **CTRL + 2** of klik op de werkbalk op de **weergeven Script deelvenster rechts** pictogram, of in de **weergave** in het menu klikt u op **Geven scriptvenster**.

- Voor maximale het scriptvenster, drukt u op **CTRL + 3** of klik op de werkbalk op de **weergeven Script deelvenster gemaximaliseerd** pictogram, of in de **weergave** menu, klikt u op **Script weergeven Deelvenster gemaximaliseerd**.

- Als u wilt het consolevenster te maximaliseren en verbergen van het scriptvenster, aan de rechterkant rand van de rij met tabs, klikt u op de **scriptvenster verbergen** pictogram in de **weergave** menu, klikt u op te heffen de **scriptvenster weergeven** menu-optie.

- Als u wilt het scriptvenster weergeven wanneer het consolevenster is gemaximaliseerd, klikt u op de rand uiterst rechts van de rij met tabs, klikt u op de **scriptvenster weergeven** pictogram, of in de **weergave** menu, klik op de **Script weergeven Deelvenster** menu-optie.

## <a name="keyboard-shortcuts-for-editing-text"></a>Sneltoetsen voor het bewerken van tekst

U kunt de volgende sneltoetsen gebruiken wanneer u tekst kunt bewerken.

|Actie|Sneltoetsen|Gebruik in|
|----------|----------------------|----------|
|**Kopiëren**|Ctrl + C|Scriptvenster, consolevenster|
|**Knippen**|CTRL + X|Scriptvenster, consolevenster|
|**Zoeken in Script**|CTRL+F|Scriptvenster|
|**Volgende zoeken in Script**|F3|Scriptvenster|
|**Vorige in Script zoeken**|SHIFT + F3|Scriptvenster|
|**Plakken**|Ctrl + V|Scriptvenster, consolevenster|
|**Redo**|CTRL + Y|Scriptvenster, consolevenster|
|**Vervang in Script**|CTRL + H|Scriptvenster|
|**Opslaan**|CTRL+S|Scriptvenster|
|**Alles selecteren**|Ctrl + A|Scriptvenster, consolevenster|
|**Ongedaan maken**|CTRL + Z|Scriptvenster, consolevenster|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Sneltoetsen voor het uitvoeren van scripts

U kunt de volgende sneltoetsen gebruiken bij het uitvoeren van scripts in het scriptvenster.

|Actie|Sneltoets|
|----------|---------------------|
|**Nieuw**|CTRL + N|
|**Open**|CTRL + O|
|**Uitvoeren**|F5|
|**Selectie uitvoeren**|F8|
|**Uitvoering stoppen**|CTRL + BREAK. CTRL + C kan worden gebruikt wanneer de context ondubbelzinnig is (als er geen tekst geselecteerd).|
|**Tabblad** (naar het volgende script)|CTRL + TAB **Opmerking:** Tabblad naar het volgende script werkt alleen wanneer u een eenmalige PowerShell-tabblad openen, of als u meer dan één PowerShell-tabblad openen, maar de focus zich in het scriptvenster.|
|**Tabblad** (naar het vorige script)|CTRL + SHIFT + TAB **Opmerking:** Tabblad naar het vorige script werkt wanneer u slechts één PowerShell-tabblad openen, of als er meer dan één PowerShell-tabblad openen en de focus zich in het scriptvenster.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Sneltoetsen voor het aanpassen van de weergave

U kunt de volgende sneltoetsen gebruiken om aan te passen van de weergave in Windows PowerShell ISE. Ze zijn toegankelijk is vanaf de deelvensters in de toepassing.

|Actie|Sneltoets|
|----------|---------------------|
|**Ga naar het consolevenster**|CTRL + D|
|**Ga naar scriptvenster**|CTRL + I|
|**Het scriptvenster weergeven**|CTRL + R|
|**Scriptvenster verbergen**|CTRL + R|
||
|**Scriptvenster omhoog verplaatsen**|CTRL + 1|
|**Naar rechts verplaatsen scriptvenster**|CTRL + 2|
|**Scriptvenster maximaliseren**|CTRL + 3|
|**Inzoomen**|CTRL + PLUSTEKEN (+)|
|**Uitzoomen**|CTRL + MINTEKEN|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Sneltoetsen voor fouten opsporen in scripts

U kunt de volgende sneltoetsen gebruiken wanneer u fouten opsporen in scripts.

|Actie|Sneltoets|Gebruik in|
|----------|---------------------|----------|
|**/ Doorgaan met uitvoeren**|F5|Scriptvenster, bij het opsporen van fouten in een script|
|**Stap in**|F11|Scriptvenster, bij het opsporen van fouten in een script|
|**Stap Over**|F10|Scriptvenster, bij het opsporen van fouten in een script|
|**Stap uit**|SHIFT + F11|Scriptvenster, bij het opsporen van fouten in een script|
|**Aanroepstack weergeven**|CTRL + SHIFT + D|Scriptvenster, bij het opsporen van fouten in een script|
|**Lijst met onderbrekingspunten**|CTRL + SHIFT + L|Scriptvenster, bij het opsporen van fouten in een script|
|**Onderbrekingspunt in-/ uitschakelen**|F9|Scriptvenster, bij het opsporen van fouten in een script|
|**Verwijder alle onderbrekingspunten**|CTRL + SHIFT + F9|Scriptvenster, bij het opsporen van fouten in een script|
|**Foutopsporingsprogramma stopt**|SHIFT + F5|Scriptvenster, bij het opsporen van fouten in een script|

> [!NOTE]
>
> U kunt ook de sneltoetsen die is ontworpen voor de Windows PowerShell-console wanneer u fouten opsporen in scripts in Windows PowerShell ISE gebruiken. Voor het gebruik van deze snelkoppelingen, moet u de snelkoppeling naar de typen in het consolevenster en druk op ENTER.

|Actie|Sneltoets|Gebruik in|
|----------|---------------------|----------|
|**Doorgaan**|C|Consolevenster bij het opsporen van fouten in een script|
|**Stap in**|S|Consolevenster bij het opsporen van fouten in een script|
|**Stap Over**|V|Consolevenster bij het opsporen van fouten in een script|
|**Stap uit**|O|Consolevenster bij het opsporen van fouten in een script|
|**Herhaal de laatste opdracht** (voor stap of stap Over)|ENTER|Consolevenster bij het opsporen van fouten in een script|
|**Aanroepstack weergeven**|K|Consolevenster bij het opsporen van fouten in een script|
|**Stop de foutopsporing**|Q|Consolevenster bij het opsporen van fouten in een script|
|**Overzicht van het Script**|L|Consolevenster bij het opsporen van fouten in een script|
|**Console Debug-opdrachten weergeven**|H of?|Consolevenster bij het opsporen van fouten in een script|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Sneltoetsen voor Windows PowerShell-tabbladen

U kunt de volgende sneltoetsen gebruiken wanneer u Windows PowerShell-tabbladen.

|Actie|Sneltoets|
|----------|---------------------|
|**PowerShell-tabblad sluiten**|CTRL + W|
|**Nieuwe PowerShell-tabblad**|CTRL + T|
|**Vorige PowerShell-tabblad**|CTRL + SHIFT + TAB. Met deze snelkoppeling werkt alleen als er geen bestanden geopend op een PowerShell-tabblad zijn.|
|**Volgende Windows PowerShell-tabblad**|CTRL + TAB. Met deze snelkoppeling werkt alleen als er geen bestanden geopend op een PowerShell-tabblad zijn.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Sneltoetsen voor het starten en afsluiten

U kunt de volgende sneltoetsen gebruiken om de Windows PowerShell-console (PowerShell.exe) te starten of om Windows PowerShell ISE af te sluiten.

|Actie|Sneltoets|
|----------|---------------------|
|**Afsluiten**|ALT+F4|
|**Start PowerShell.exe** (Windows PowerShell-console)|CTRL + SHIFT + P|

## <a name="see-also"></a>Zie ook

[Maak kennis met de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)