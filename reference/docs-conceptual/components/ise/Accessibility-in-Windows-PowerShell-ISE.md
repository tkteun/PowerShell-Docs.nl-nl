---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Toegankelijkheid in Windows PowerShell ISE
ms.openlocfilehash: 416b18dd492ca04d98b5adf9f7f0f88ea495740a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030648"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Toegankelijkheid in Windows PowerShell ISE

Dit onderwerp bevat een beschrijving van de toegankelijkheids functies van Windows Power shell Integrated Scripting Environment (ISE) die u mogelijk nuttig vindt.

* [De grootte en locatie van de console en script deel vensters wijzigen](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
* [Sneltoetsen voor het bewerken van tekst](#keyboard-shortcuts-for-editing-text)
* [Sneltoetsen voor het uitvoeren van scripts](#keyboard-shortcuts-for-running-scripts)
* [Sneltoetsen voor het aanpassen van de weer gave](#keyboard-shortcuts-for-customizing-the-view)
* [Sneltoetsen voor fout opsporing in scripts](#keyboard-shortcuts-for-debugging-scripts)
* [Sneltoetsen voor Windows Power shell-tabbladen](#keyboard-shortcuts-for-windows-powershell-tabs)
* [Sneltoetsen voor het starten en afsluiten](#keyboard-shortcuts-for-starting-and-exiting)

Microsoft streeft ernaar om zijn producten en diensten gebruiksvriendelijker te maken voor iedereen. De volgende onderwerpen bevatten informatie over de functies, producten en services die Windows PowerShell ISE toegankelijker maken voor mensen met een handicap.

Windows PowerShell ISE ondersteunt de modus Hoog contrast. Voor visueel gehandicapten is informatie over onderbrekings punten beschikbaar via de cmdlets voor het beheren van onderbrekings punten, zoals [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) en [set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Zie voor meer informatie ' onderbrekings punten beheren ' in [de Windows PowerShell ISE fouten opsporen in scripts](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md). Naast de toegankelijkheids functies en-hulpprogram ma's in micro soft Windows maken de volgende functies Windows PowerShell ISE meer toegankelijk voor mensen met een handicap:

- Sneltoetsen

- De syntaxis kleur tabel en de mogelijkheid om verschillende andere kleur instellingen te wijzigen met behulp van het script object [$psISE. options](https://technet.microsoft.com/library/75e2a76f-f3d1-490b-ad5d-e3829946aabb) .

- Teken grootte wijzigen

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>De grootte en locatie van de console en script deel vensters wijzigen

U kunt de volgende stappen gebruiken om de grootte en locatie van het console venster en het Script venster te wijzigen. Wanneer u de Windows PowerShell ISE opnieuw opent, blijven de grootte-en locatie wijzigingen die u hebt aangebracht bewaard.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Het formaat van het Script venster en het console venster wijzigen

1. Houd de muis aanwijzer stil op de gesplitste lijn tussen het Script venster en het console venster.

2. Wanneer de muis aanwijzer verandert in een twee puntige pijl, sleept u de rand om de grootte van het deel venster te wijzigen.

### <a name="to-move-the-script-pane-and-console-pane"></a>Het Script venster en het console venster verplaatsen

Voer een van de volgende handelingen uit:

- Als u het Script venster boven het console venster wilt verplaatsen, drukt u op **CTRL + 1** of klikt u op de werk balk op het bovenste pictogram van het **Script venster weer geven** of klikt u in het menu **weer gave** op **Script venster bovenaan weer geven**.

- Als u het Script venster naar de rechter kant van het console venster wilt verplaatsen, drukt u op **CTRL + 2** of klikt u op de werk balk op het pictogram **Script venster rechts tonen** of in het menu **weer gave** op **Script venster rechts weer geven**.

- Om het deel venster script te maximaliseren, drukt u op **CTRL + 3** of klikt u op de werk balk op het **deel venster script weer geven pictogram gemaximaliseerd** , of klikt u in het menu **weer gave** op **Script venster gemaximaliseerd weer geven**.

- Als u het console venster wilt maximaliseren en het deel venster script wilt verbergen, klikt u op het **deel venster script verbergen** in het menu **weer gave** en schakelt u de optie **script paneel weer geven** uit.

- Als u het Script venster wilt weer geven wanneer het console venster is gemaximaliseerd, klikt u aan de rechter kant van de rij met tabbladen op het **deel venster script weer geven** of in het menu **weer gave** op de menu optie **script deel venster weer** geven te selecteren.

## <a name="keyboard-shortcuts-for-editing-text"></a>Sneltoetsen voor het bewerken van tekst

U kunt de volgende sneltoetsen gebruiken bij het bewerken van tekst.

|Actie|Sneltoetsen|Gebruiken in|
|----------|----------------------|----------|
|**Copy**|Ctrl + C|Script venster, console venster|
|**Verminderen**|CTRL + X|Script venster, console venster|
|**Zoeken in script**|CTRL+F|Script venster|
|**Volgende zoeken in script**|F3|Script venster|
|**Vorige zoeken in script**|SHIFT + F3|Script venster|
|**Plakken**|Ctrl + V|Script venster, console venster|
|**Redo**|CTRL + Y|Script venster, console venster|
|**Vervangen in script**|CTRL + H|Script venster|
|**Opslaan**|CTRL+S|Script venster|
|**Alles selecteren**|Ctrl + A|Script venster, console venster|
|**Opdracht**|CTRL + Z|Script venster, console venster|

## <a name="keyboard-shortcuts-for-running-scripts"></a>Sneltoetsen voor het uitvoeren van scripts

U kunt de volgende sneltoetsen gebruiken voor het uitvoeren van scripts in het Script-venster.

|Actie|Sneltoets|
|----------|---------------------|
|**Nieuw**|CTRL + N|
|**Lopend**|CTRL + O|
|**Uitvoeren**|F5|
|**Selectie uitvoeren**|F8|
|**Uitvoering stoppen**|CTRL + onderbreken. CTRL + C kan worden gebruikt wanneer de context ondubbelzinnig is (als er geen tekst is geselecteerd).|
|**Tabblad** (naar volgend script)|CTRL + TAB **Note:** tab naar volgende script werkt alleen wanneer er één Power shell-tabblad is geopend of als u meer dan één Power shell-tabblad hebt geopend, maar de focus is in het Script-venster.|
|**Tab** (naar het vorige script)|CTRL + SHIFT + TAB **Opmerking:** tab naar vorig script werkt wanneer er slechts één Power shell-tabblad is geopend, of als u meer dan één Power shell-tabblad hebt geopend en de focus in het Script-venster wordt weer geven.|

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Sneltoetsen voor het aanpassen van de weer gave

U kunt de volgende sneltoetsen gebruiken om de weer gave in Windows PowerShell ISE aan te passen. Ze zijn toegankelijk vanuit alle deel Vensters in de toepassing.

|Actie|Sneltoets|
|----------|---------------------|
|**Naar het console venster gaan**|CTRL+D|
|**Naar het Script venster gaan**|CTRL + I|
|**Script venster weer geven**|CTRL + R|
|**Script venster verbergen**|CTRL + R|
||
|**Script paneel omhoog verplaatsen**|CTRL+1|
|**Script venster naar rechts verplaatsen**|CTRL+2|
|**Script venster maximaliseren**|CTRL+3|
|**Inzoomen**|CTRL + PLUS TEKEN|
|**Uitzoomen**|CTRL + MINTEKEN|

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Sneltoetsen voor fout opsporing in scripts

U kunt de volgende sneltoetsen gebruiken bij het opsporen van fouten in scripts.

|Actie|Sneltoets|Gebruiken in|
|----------|---------------------|----------|
|**Uitvoeren/door gaan**|F5|Script-deel venster bij fout opsporing van een script|
|**Stap in**|F11|Script-deel venster bij fout opsporing van een script|
|**Stap over**|F10|Script-deel venster bij fout opsporing van een script|
|**Stap uit**|SHIFT + F11|Script-deel venster bij fout opsporing van een script|
|**Aanroep stack weer geven**|CTRL + SHIFT + D|Script-deel venster bij fout opsporing van een script|
|**Onderbrekings punten weer geven**|CTRL + SHIFT + L|Script-deel venster bij fout opsporing van een script|
|**Onderbrekings punt in-/uitschakelen**|F9|Script-deel venster bij fout opsporing van een script|
|**Alle onderbrekings punten verwijderen**|CTRL + SHIFT + F9|Script-deel venster bij fout opsporing van een script|
|**Fout opsporing stoppen**|SHIFT + F5|Script-deel venster bij fout opsporing van een script|

> [!NOTE]
>
> U kunt ook de sneltoetsen gebruiken die zijn ontworpen voor de Windows Power shell-console wanneer u fouten opspoort in scripts in Windows PowerShell ISE. Als u deze sneltoetsen wilt gebruiken, moet u de snelkoppeling in het console venster typen en op ENTER drukken.

|Actie|Sneltoets|Gebruiken in|
|----------|---------------------|----------|
|**Doen**|C|Console venster, bij fout opsporing van een script|
|**Stap in**|S|Console venster, bij fout opsporing van een script|
|**Stap over**|V|Console venster, bij fout opsporing van een script|
|**Stap uit**|O|Console venster, bij fout opsporing van een script|
|**Laatste opdracht herhalen** (voor stap in of stap voor)|ENTER|Console venster, bij fout opsporing van een script|
|**Aanroep stack weer geven**|K|Console venster, bij fout opsporing van een script|
|**Fout opsporing stoppen**|Q|Console venster, bij fout opsporing van een script|
|**Het script weer geven**|L|Console venster, bij fout opsporing van een script|
|**Opties voor fout opsporing in console weer geven**|H of?|Console venster, bij fout opsporing van een script|

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Sneltoetsen voor Windows Power shell-tabbladen

U kunt de volgende sneltoetsen gebruiken wanneer u Windows Power shell-tabbladen gebruikt.

|Actie|Sneltoets|
|----------|---------------------|
|**Tabblad Power shell sluiten**|CTRL + W|
|**Nieuw Power shell-tabblad**|CTRL+T|
|**Vorig Power shell-tabblad**|CTRL + SHIFT + TAB. Deze snelkoppeling werkt alleen als er geen bestanden zijn geopend op een Power shell-tabblad.|
|**Volgende Windows Power shell-tabblad**|CTRL + TAB. Deze snelkoppeling werkt alleen als er geen bestanden zijn geopend op een Power shell-tabblad.|

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Sneltoetsen voor het starten en afsluiten

U kunt de volgende sneltoetsen gebruiken om de Windows Power shell-console (Power shell. exe) te starten of Windows PowerShell ISE af te sluiten.

|Actie|Sneltoets|
|----------|---------------------|
|**Afsluiten**|ALT+F4|
|**Power shell. exe starten** (Windows Power shell-console)|CTRL + SHIFT + P|

## <a name="see-also"></a>Zie ook

[Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
