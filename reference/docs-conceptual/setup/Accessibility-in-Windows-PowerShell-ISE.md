---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Toegankelijkheid in Windows PowerShell ISE
ms.assetid: a078f9d1-dd6b-4323-b16d-0622cd993aa8
ms.openlocfilehash: 65d159905660f4f3e025b385626679e02a785fd7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="accessibility-in-windows-powershell-ise"></a>Toegankelijkheid in Windows PowerShell ISE

Dit onderwerp beschrijft de toegankelijkheidsfuncties van Windows PowerShell Integrated Scripting Environment (ISE) die handig zijn wellicht.

* [Het wijzigen van de grootte en locatie van de Console en het Script deelvensters](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Sneltoetsen voor het bewerken van tekst](#keyboard-shortcuts-for-editing-text)
* [Sneltoetsen voor het uitvoeren van scripts](#keyboard-shortcuts-for-running-scripts)
* [Sneltoetsen voor de weergave aanpassen](#keyboard-shortcuts-for-customizing-the-view)
* [Sneltoetsen voor foutopsporing in scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Sneltoetsen voor Windows PowerShell-tabbladen](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Sneltoetsen voor het starten en afsluiten](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft streeft ernaar om zijn producten en diensten gebruiksvriendelijker te maken voor iedereen. De volgende onderwerpen bevatten informatie over de functies, producten en services die Windows PowerShell ISE beter toegankelijk voor mensen met beperkingen.

Windows PowerShell ISE ondersteunt hoog contrast modus. Voor visueel gehinderd onderbrekingspunt informatie is beschikbaar via de cmdlets voor het beheren van onderbrekingspunten, zoals [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) en [Set PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Voor meer informatie Zie 'How to onderbrekingspunten beheren' in [hoe fouten opsporen in Scripts in de Windows PowerShell ISE](../core-powershell/ise/How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Naast de toegankelijkheidsfuncties en hulpprogramma's in Microsoft Windows maken maken de volgende functies Windows PowerShell ISE toegankelijker voor mensen met een handicap:

- Sneltoetsen gebruiken

- De kleur tabel syntaxis en de mogelijkheid diverse andere om kleurinstellingen te wijzigen met behulp van de [$psISE.Options](https://technet.microsoft.com/en-us/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) scripting-object.

- Wijziging van de tekst

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Het wijzigen van de grootte en locatie van de Console en het Script deelvensters

De volgende stappen kunt u de grootte en locatie van het consolevenster en het scriptvenster wijzigen. Wanneer u de Windows PowerShell ISE opnieuw opent, wordt de grootte en locatie aangebrachte wijzigingen blijven behouden.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Aan de scriptvenster en consolevenster vergroten of verkleinen

1. De aanwijzer laat op de regel splitsen tussen de Script-veld en het consolevenster.

2. Wanneer de muisaanwijzer in een dubbele pijl verandert, sleept u de rand om de grootte van het deelvenster te wijzigen.

### <a name="to-move-the-script-pane-and-console-pane"></a>De scriptvenster en consolevenster verplaatsen

Voer een van de volgende handelingen uit:

- Verplaatst u het scriptvenster boven het consolevenster **CTRL + 1** of klik op de werkbalk op de **weergeven Script deelvenster eerste** pictogram, of in de **weergave** menu, klikt u op **weergeven Deelvenster boven script**.

- Verplaatst u het scriptvenster rechts van het consolevenster **CTRL + 2** of klik op de werkbalk op de **weergeven Script deelvenster rechts** pictogram, of in de **weergave** menu klikt u op **Geven scriptvenster**.

- Als u wilt het scriptvenster maximaliseren, drukt u op **CTRL + 3** of klik op de werkbalk de **weergeven Script deelvenster gemaximaliseerd** pictogram, of in de **weergave** menu, klikt u op **Script weergeven Deelvenster gemaximaliseerd**.

- Als u wilt het consolevenster maximaliseren en verberg de scriptvenster aan de rechterkant rand van de rij met tabs, klikt u op de **scriptvenster verbergen** pictogram in de **weergave** menu, klikt u op te heffen de **scriptvenster weergeven** menuoptie.

- Als u wilt het scriptvenster weergeven wanneer het consolevenster gemaximaliseerd, aan de rechterkant rand van de rij met tabs, klikt u op de **scriptvenster weergeven** pictogram, of in de **weergave** menu, schakel de **Script weergeven Deelvenster** menuoptie.

## <a name="keyboard-shortcuts-for-editing-text"></a>Sneltoetsen voor het bewerken van tekst

U kunt de volgende sneltoetsen gebruiken wanneer u tekst bewerkt.

|Actie|Sneltoetsen gebruiken|Gebruik in|
|----------|----------------------|----------|
|**Kopiëren**|Ctrl + C|Script-veld-consolevenster|
|**Knippen**|CTRL + X|Script-veld-consolevenster|
|**Zoeken in een Script**|CTRL+F|Scriptvenster|
|**Volgende zoeken in een Script**|F3|Scriptvenster|
|**Vorige in Script zoeken**|SHIFT+F3|Scriptvenster|
|**Paste**|Ctrl + V|Script-veld-consolevenster|
|**Redo**|CTRL + Y|Script-veld-consolevenster|
|**Vervang in Script**|CTRL + H|Scriptvenster|
|**Opslaan**|CTRL+S|Scriptvenster|
|**Alles selecteren**|Ctrl + A|Script-veld-consolevenster|
|**Undo**|CTRL + Z|Script-veld-consolevenster|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Sneltoetsen voor het uitvoeren van scripts

U kunt de volgende sneltoetsen gebruiken bij het uitvoeren van scripts in de Script-veld.

|Actie|Sneltoets|
|----------|---------------------|
|**Nieuw**|CTRL + N|
|**Open**|CTRL + O|
|**Run**|F5|
|**Selectie uitvoeren**|F8|
|**Uitvoering stoppen**|CTRL + BREAK. CTRL + C kan worden gebruikt wanneer de context niet-ambigue is (Er is geen tekst geselecteerd).|
|**Tabblad** (naar het volgende script)|CTRL + TAB **Opmerking:** tabblad naar het volgende script werkt alleen als u één PowerShell tabblad openen, of wanneer er meer dan één PowerShell tabblad is geopend, maar de focus in het scriptvenster is.|
|**Tabblad** (naar vorige script)|CTRL + SHIFT + TAB **Opmerking:** tabblad naar vorige script werkt wanneer u hebt slechts één PowerShell tabblad geopend, of als er meer dan één PowerShell tabblad is geopend en de focus is in de Script-veld.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Sneltoetsen voor de weergave aanpassen

U kunt de volgende sneltoetsen gebruiken voor het aanpassen van de weergave in Windows PowerShell ISE. Ze zijn toegankelijk vanaf de deelvensters in de toepassing.

|Actie|Sneltoets|
|----------|---------------------|
|**Ga naar het consolevenster**|CTRL + D|
|**Ga naar scriptvenster**|CTRL + I|
|**Scriptvenster weergeven**|CTRL + R|
|**Scriptvenster verbergen**|CTRL + R|
||
|**Script-veld omhoog verplaatsen**|CTRL + 1|
|**Scriptvenster rechts verplaatsen**|CTRL + 2|
|**Scriptvenster maximaliseren**|CTRL + 3|
|**Inzoomen**|CTRL + PLUSTEKEN (+)|
|**Uitzoomen**|CTRL + MINTEKEN|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Sneltoetsen voor foutopsporing in scripts

U kunt de volgende sneltoetsen gebruiken wanneer u fouten opsporen in scripts.

|Actie|Sneltoets|Gebruik in|
|----------|---------------------|----------|
|**Run/Continue**|F5|Scriptvenster wanneer foutopsporing van een script|
|**In stap**|F11|Scriptvenster wanneer foutopsporing van een script|
|**Stap Over**|F10|Scriptvenster wanneer foutopsporing van een script|
|**Stap uit**|SHIFT+F11|Scriptvenster wanneer foutopsporing van een script|
|**Aanroepstack weergeven**|CTRL + SHIFT + D|Scriptvenster wanneer foutopsporing van een script|
|**Lijst met onderbrekingspunten**|CTRL + SHIFT + L|Scriptvenster wanneer foutopsporing van een script|
|**Toggle Breakpoint**|F9|Scriptvenster wanneer foutopsporing van een script|
|**Verwijder alle onderbrekingspunten**|CTRL + SHIFT + F9|Scriptvenster wanneer foutopsporing van een script|
|**Stop de foutopsporing**|SHIFT+F5|Scriptvenster wanneer foutopsporing van een script|

> ![Opmerking](../core-powershell/web-access/images/Note.jpeg)**Opmerking**
>
> U kunt ook de sneltoetsen die is ontworpen voor de Windows PowerShell-console wanneer u fouten opsporen in scripts in Windows PowerShell ISE gebruiken. Voor het gebruik van deze snelkoppelingen, moet u de snelkoppeling typt in het consolevenster en druk op ENTER.

|Actie|Sneltoets|Gebruik in|
|----------|---------------------|----------|
|**Doorgaan**|C|-Consolevenster, als u fouten opspoort een script|
|**In stap**|S|-Consolevenster, als u fouten opspoort een script|
|**Stap Over**|V|-Consolevenster, als u fouten opspoort een script|
|**Stap uit**|O|-Consolevenster, als u fouten opspoort een script|
|**Herhaal de laatste opdracht** (voor stap naar of stap Over)|ENTER|-Consolevenster, als u fouten opspoort een script|
|**Aanroepstack weergeven**|K|-Consolevenster, als u fouten opspoort een script|
|**Stop de foutopsporing**|Q|-Consolevenster, als u fouten opspoort een script|
|**Lijst van het Script**|L|-Consolevenster, als u fouten opspoort een script|
|**Console weergeven Debug-opdrachten**|H of?|-Consolevenster, als u fouten opspoort een script|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Sneltoetsen voor Windows PowerShell-tabbladen

U kunt de volgende sneltoetsen gebruiken wanneer u Windows PowerShell-tabbladen.

|Actie|Sneltoets|
|----------|---------------------|
|**Tabblad PowerShell sluiten**|CTRL + W|
|**Nieuw PowerShell-tabblad**|CTRL + T|
|**Vorige PowerShell-tabblad**|CTRL + SHIFT + TAB. Deze sneltoets werkt alleen als er geen bestanden geopend op elk tabblad PowerShell zijn.|
|**Volgende Windows PowerShell-tabblad**|CTRL + TAB. Deze sneltoets werkt alleen als er geen bestanden geopend op elk tabblad PowerShell zijn.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Sneltoetsen voor het starten en afsluiten

U kunt de volgende sneltoetsen gebruiken om de Windows PowerShell-console (PowerShell.exe) te starten of om af te sluiten van Windows PowerShell ISE.

|Actie|Sneltoets|
|----------|---------------------|
|**Exit**|ALT+F4|
|**Start PowerShell.exe** (Windows PowerShell-console)|CTRL + SHIFT + P|

## <a name="see-also"></a>Zie ook

- [Introducing the Windows PowerShell ISE](../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)