---
ms.date: 12/19/2019
title: Toegankelijkheid in Windows PowerShell ISE
description: Dit onderwerp bevat een beschrijving van de toegankelijkheids functies van Windows Power shell Integrated Scripting Environment (ISE) die u mogelijk nuttig vindt.
ms.openlocfilehash: 18acf447965eaaa7f93bb4c443a304b37216a9ba
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663857"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Toegankelijkheid in Windows PowerShell ISE

Dit onderwerp bevat een beschrijving van de toegankelijkheids functies van Windows Power shell Integrated Scripting Environment (ISE) die u mogelijk nuttig vindt.

- [De grootte en locatie van de console en script deel vensters wijzigen](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [Sneltoetsen voor het bewerken van tekst](#keyboard-shortcuts-for-editing-text)
- [Sneltoetsen voor het uitvoeren van scripts](#keyboard-shortcuts-for-running-scripts)
- [Sneltoetsen voor het aanpassen van de weer gave](#keyboard-shortcuts-for-customizing-the-view)
- [Sneltoetsen voor fout opsporing in scripts](#keyboard-shortcuts-for-debugging-scripts)
- [Sneltoetsen voor Windows Power shell-tabbladen](#keyboard-shortcuts-for-windows-powershell-tabs)
- [Sneltoetsen voor het starten en afsluiten](#keyboard-shortcuts-for-starting-and-exiting)
- [Onderbrekings beheer met cmdlets](#breakpoint-management)

Microsoft streeft ernaar om zijn producten en diensten gebruiksvriendelijker te maken voor iedereen. De volgende onderwerpen bevatten informatie over de functies, producten en services die Windows PowerShell ISE toegankelijker maken voor mensen met een handicap.

Naast de toegankelijkheids functies en-hulpprogram ma's in micro soft Windows maken de volgende functies Windows PowerShell ISE meer toegankelijk voor mensen met een handicap:

- Sneltoetsen

- De syntaxis kleur tabel en de mogelijkheid om verschillende andere kleur instellingen te wijzigen met behulp van het script object [$psISE. options](object-model/The-ISEOptions-Object.md) .

- Teken grootte wijzigen

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>De grootte en locatie van de console en script deel vensters wijzigen

U kunt de volgende stappen gebruiken om de grootte en locatie van het console venster en het Script venster te wijzigen. Wanneer u de Windows PowerShell ISE opnieuw opent, blijven de grootte-en locatie wijzigingen die u hebt aangebracht bewaard.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Het formaat van het Script venster en het console venster wijzigen

1. Houd de muis aanwijzer stil op de gesplitste lijn tussen het Script venster en het console venster.

2. Wanneer de muis aanwijzer verandert in een twee puntige pijl, sleept u de rand om de grootte van het deel venster te wijzigen.

### <a name="to-move-the-script-pane-and-console-pane"></a>Het Script venster en het console venster verplaatsen

Voer een van de volgende handelingen uit:

- Als u het Script venster boven het console venster wilt verplaatsen, drukt u op <kbd>CTRL</kbd> + <kbd>1</kbd> of klikt u op de werk balk op het bovenste pictogram van het **Script venster weer geven** of klikt u in het menu **weer gave** op **Script venster bovenaan weer geven** .

- Als u het Script venster rechts van het console venster wilt verplaatsen, drukt u op <kbd>CTRL</kbd> + <kbd>2</kbd> of klikt u op de werk balk op het pictogram **Script venster rechts tonen** of klikt u in het menu **weer gave** op **Script venster rechts weer geven** .

- Om het deel venster script te maximaliseren, drukt u op <kbd>CTRL</kbd> + <kbd>3</kbd> of klikt u op de werk balk op het **deel venster script weer geven pictogram gemaximaliseerd** , of klikt u in het menu **weer gave** op **Script venster gemaximaliseerd weer geven** .

- Als u het console venster wilt maximaliseren en het deel venster script wilt verbergen, klikt u op het **deel venster script verbergen** in het menu **weer gave** en schakelt u de optie **script paneel weer geven** uit.

- Als u het Script venster wilt weer geven wanneer het console venster is gemaximaliseerd, klikt u aan de rechter kant van de rij met tabbladen op het **deel venster script weer geven** of in het menu **weer gave** op de menu optie **script deel venster weer** geven te selecteren.

## <a name="keyboard-shortcuts-for-editing-text"></a>Sneltoetsen voor het bewerken van tekst

U kunt de volgende sneltoetsen gebruiken bij het bewerken van tekst.

|           Actie            |       Sneltoetsen       |          Gebruiken in           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Kopieer**                    | <kbd>CTRL</kbd> + <kbd>C</kbd>   | Script venster, console venster |
| **Knippen**                     | <kbd>CTRL</kbd> + <kbd>X</kbd>   | Script venster, console venster |
| **Zoeken in script**          | <kbd>CTRL</kbd> + <kbd>F</kbd>   | Script venster               |
| **Volgende zoeken in script**     | <kbd>F3</kbd>                  | Script venster               |
| **Vorige zoeken in script** | <kbd>SHIFT</kbd> + <kbd>F3</kbd> | Script venster               |
| **Plakken**                   | <kbd>CTRL</kbd> + <kbd>V</kbd>   | Script venster, console venster |
| **Redo**                    | <kbd>CTRL</kbd> + <kbd>Y</kbd>   | Script venster, console venster |
| **Vervangen in script**       | <kbd>CTRL</kbd> + <kbd>H</kbd>   | Script venster               |
| **Opslaan**                    | <kbd>CTRL</kbd> + <kbd>S</kbd>   | Script venster               |
| **Alles selecteren**              | <kbd>CTRL</kbd> + <kbd>Een</kbd>   | Script venster, console venster |
| **Ongedaan maken**                    | <kbd>CTRL</kbd> + <kbd>Z</kbd>   | Script venster, console venster |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Sneltoetsen voor het uitvoeren van scripts

U kunt de volgende sneltoetsen gebruiken voor het uitvoeren van scripts in het Script-venster.

|            Actie            |                                                                                                     Sneltoets                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nieuw**                      | <kbd>CTRL</kbd> + <kbd>N</kbd>                                                                                                                                                                                               |
| **Openen**                     | <kbd>CTRL</kbd> + <kbd>O</kbd>                                                                                                                                                                                               |
| **Uitvoeringsrun**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **Selectie uitvoeren**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **Uitvoering stoppen**           | <kbd>CTRL</kbd> + <kbd>Onderbreken</kbd>. <kbd>CTRL</kbd> + <kbd>C</kbd> kan worden gebruikt wanneer de context ondubbelzinnig is (als er geen tekst is geselecteerd).                                                                               |
| **Tabblad** (naar volgend script)     | <kbd>CTRL</kbd> + <kbd>Tab</kbd> **Opmerking:** tab naar volgende script werkt alleen wanneer er één Power shell-tabblad is geopend of als u meer dan één Power shell-tabblad hebt geopend, maar de focus zich in het Script-venster bevindt.                |
| **Tab** (naar het vorige script) | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>Tab</kbd> **Opmerking:** tab naar vorig script werkt wanneer er slechts één Power shell-tabblad is geopend, of als u meer dan één Power shell-tabblad hebt geopend en de focus in het Script-venster. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Sneltoetsen voor het aanpassen van de weer gave

U kunt de volgende sneltoetsen gebruiken om de weer gave in Windows PowerShell ISE aan te passen. Ze zijn toegankelijk vanuit alle deel Vensters in de toepassing.

|           Actie           |         Sneltoets        |
| -------------------------- | -------------------------------- |
| **Naar het console venster gaan**     | <kbd>CTRL</kbd> + <kbd>D</kbd>     |
| **Naar het Script venster gaan**      | <kbd>CTRL</kbd> + <kbd>Ik heb</kbd>     |
| **Script venster weer geven**       | <kbd>CTRL</kbd> + <kbd>R</kbd>     |
| **Script venster verbergen**       | <kbd>CTRL</kbd> + <kbd>R</kbd>     |
| **Script paneel omhoog verplaatsen**    | <kbd>CTRL</kbd> + <kbd>1</kbd>     |
| **Script venster naar rechts verplaatsen** | <kbd>CTRL</kbd> + <kbd>2</kbd>     |
| **Script venster maximaliseren**   | <kbd>CTRL</kbd> + <kbd>3</kbd>     |
| **Inzoomen**                | <kbd>CTRL</kbd> + <kbd>Plus</kbd>  |
| **Uitzoomen**               | <kbd>CTRL</kbd> + <kbd>Min</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Sneltoetsen voor fout opsporing in scripts

U kunt de volgende sneltoetsen gebruiken bij het opsporen van fouten in scripts.

|           Actie           |               Sneltoets                |                Gebruiken in                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Uitvoeren/door gaan**           | <kbd>F5</kbd>                                  | Script-deel venster bij fout opsporing van een script |
| **Stap in**              | <kbd>F11</kbd>                                 | Script-deel venster bij fout opsporing van een script |
| **Stap over**              | <kbd>F10</kbd>                                 | Script-deel venster bij fout opsporing van een script |
| **Stap uit**               | <kbd>SHIFT</kbd> + <kbd>F11</kbd>                | Script-deel venster bij fout opsporing van een script |
| **Aanroep stack weer geven**     | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>D</kbd>  | Script-deel venster bij fout opsporing van een script |
| **Onderbrekings punten weer geven**       | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>L</kbd>  | Script-deel venster bij fout opsporing van een script |
| **Onderbrekings punt in-/uitschakelen**      | <kbd>F9</kbd>                                  | Script-deel venster bij fout opsporing van een script |
| **Alle onderbrekings punten verwijderen** | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>F9</kbd> | Script-deel venster bij fout opsporing van een script |
| **Fout opsporing stoppen**          | <kbd>SHIFT</kbd> + <kbd>F5</kbd>                 | Script-deel venster bij fout opsporing van een script |

> [!NOTE]
> U kunt ook de sneltoetsen gebruiken die zijn ontworpen voor de Windows Power shell-console wanneer u fouten opspoort in scripts in Windows PowerShell ISE. Als u deze sneltoetsen wilt gebruiken, moet u de snelkoppeling in het console venster typen en op <kbd>Enter</kbd>drukken.

|                 Actie                  |      Sneltoets       |                Gebruiken in                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **Doorgaan**                            | <kbd>C</kbd>                 | Console venster, bij fout opsporing van een script |
| **Stap in**                           | <kbd>S</kbd>                 | Console venster, bij fout opsporing van een script |
| **Stap over**                           | <kbd>Verticale</kbd>                 | Console venster, bij fout opsporing van een script |
| **Stap uit**                            | <kbd>O</kbd>                 | Console venster, bij fout opsporing van een script |
| **Laatste opdracht herhalen** (stap in/over) | <kbd>Voer</kbd>             | Console venster, bij fout opsporing van een script |
| **Aanroep stack weer geven**                  | <kbd>K</kbd>                 | Console venster, bij fout opsporing van een script |
| **Fout opsporing stoppen**                      | <kbd>Q</kbd>                 | Console venster, bij fout opsporing van een script |
| **Het script weer geven**                     | <kbd>L</kbd>                 | Console venster, bij fout opsporing van een script |
| **Opties voor fout opsporing in console weer geven**  | <kbd>H</kbd> of <kbd>?</kbd> | Console venster, bij fout opsporing van een script |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Sneltoetsen voor Windows Power shell-tabbladen

U kunt de volgende sneltoetsen gebruiken wanneer u Windows Power shell-tabbladen gebruikt.

|             Actie              |                                 Sneltoets                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **Tabblad Power shell sluiten**        | <kbd>CTRL</kbd> + <kbd>W</kbd>                                                       |
| **Nieuw Power shell-tabblad**          | <kbd>CTRL</kbd> + <kbd>T</kbd>                                                       |
| **Vorig Power shell-tabblad**     | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>Tab</kbd> (alleen wanneer er geen bestanden zijn geopend op een Power shell-tabblad) |
| **Volgende Windows Power shell-tabblad** | <kbd>CTRL</kbd> + <kbd>Tab</kbd> (alleen wanneer er geen bestanden zijn geopend op een Power shell-tabblad) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Sneltoetsen voor het starten en afsluiten

U kunt de volgende sneltoetsen gebruiken om de Windows Power shell-console ( **PowerShell.exe** ) te starten of Windows PowerShell ISE af te sluiten.

|                        Actie                         |               Sneltoets               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Afsluiten**                                              | <kbd>Alt</kbd> + <kbd>F4</kbd>                  |
| **PowerShell.exestarten** (Windows Power shell-console) | <kbd>CTRL</kbd> + <kbd>SHIFT</kbd> + <kbd>P</kbd> |

## <a name="breakpoint-management"></a>Onderbrekings beheer

Voor visueel gehandicapten is informatie over onderbrekings punten beschikbaar via de cmdlets voor het beheren van onderbrekings punten, zoals [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) en [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint). Zie voor meer informatie ' onderbrekings punten beheren ' in [de Windows PowerShell ISE fouten opsporen in scripts](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md).

## <a name="see-also"></a>Zie ook

[Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
