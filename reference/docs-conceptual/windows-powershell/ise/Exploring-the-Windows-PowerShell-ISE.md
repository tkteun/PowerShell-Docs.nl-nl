---
ms.date: 01/02/2020
title: Kennismaking met Windows PowerShell ISE
description: Dit artikel bevat een overzicht van de functies van de Windows PowerShell ISE
ms.topic: conceptual
ms.custom: ISE-F1-page
ms.openlocfilehash: e9f236ba443fd8ca99cb57acfc8a3b3549192c61
ms.sourcegitcommit: 1e1535cb22d16de06f80beafe77a37a7c77de6d3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/27/2021
ms.locfileid: "108025649"
---
# <a name="exploring-the-windows-powershell-ise"></a>Kennismaking met Windows PowerShell ISE

U kunt de Windows PowerShell IsE (Integrated Scripting Environment) gebruiken om opdrachten en scripts te maken, uit te voeren en fouten op te sporen. De Windows PowerShell ISE bestaat uit de menubalk, Windows PowerShell-tabbladen, de werkbalk, scripttabbladen, een scriptvenster, een consolevenster, een statusbalk, een schuifregelaar voor tekstgrootte en contextgevoelige Help.

## <a name="menu-bar"></a>Menubalk

De menubalk bevat de  **menu's Bestand,** **Bewerken,** **Weergeven, Extra,** **Fouten opsporen,** **Invoegtoepassingen** en **Help.** Met de knoppen in de menu's kunt u taken uitvoeren die betrekking hebben op het schrijven en uitvoeren van scripts en het uitvoeren van opdrachten in Windows PowerShell ISE. Daarnaast kan een [hulpprogramma voor invoeggebruik](object-model/The-ISEAddOnTool-Object.md) op de menubalk worden geplaatst door scripts uit te voeren die gebruikmaken van de [ISE-objectmodelhiërarchie](object-model/The-ISE-Object-Model-Hierarchy.md).

## <a name="windows-powershell-tabs"></a>Windows PowerShell tabbladen

Een Windows PowerShell tabblad is de omgeving waarin een Windows PowerShell script wordt uitgevoerd. U kunt nieuwe tabbladen Windows PowerShell openen in de Windows PowerShell ISE om afzonderlijke omgevingen te maken op uw lokale computer of op externe computers. Mogelijk hebt u maximaal acht PowerShell-tabbladen tegelijk geopend.

Zie How to Create a PowerShell Tab in Windows PowerShell ISE (Een [PowerShell-tabblad maken in Windows PowerShell ISE).](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

## <a name="toolbar"></a>Werkbalk

De volgende knoppen bevinden zich op de werkbalk.

|             Knop             |                                                                                     Functie                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nieuw**                        | Hiermee opent u een nieuw script.                                                                                                                                                              |
| **Openen**                       | Hiermee opent u een bestaand script of bestand.                                                                                                                                                |
| **Opslaan**                       | Hiermee slaat u een script of bestand.                                                                                                                                                          |
| **Knippen**                        | De geselecteerde tekst wordt wegkapt en gekopieerd naar het klembord.                                                                                                                           |
| **Kopiëren**                       | Kopieert de geselecteerde tekst naar het klembord.                                                                                                                                       |
| **Plakken**                      | Hiermee plakt u de inhoud van het klembord op de cursorlocatie.                                                                                                                     |
| **Consoledeelvenster leegmaken**          | Alle inhoud in het consolevenster wordt gew clears.                                                                                                                                           |
| **Ongedaan maken**                       | De actie die zojuist is uitgevoerd, wordt omgekeerd.                                                                                                                                     |
| **Redo**                       | Voert de actie uit die zojuist ongedaan is gemaakt.                                                                                                                                        |
| **Script uitvoeren**                 | Voert een script uit.                                                                                                                                                                   |
| **Selectie uitvoeren**              | Voert een geselecteerd gedeelte van een script uit.                                                                                                                                             |
| **Bewerking stoppen**             | Stopt een script dat wordt uitgevoerd.                                                                                                                                                  |
| **Nieuw tabblad Remote PowerShell**  | Hiermee maakt u een nieuw PowerShell-tabblad dat een sessie op een externe computer tot leven brengt. Er wordt een dialoogvenster weergegeven waarin u wordt gevraagd details op te geven die nodig zijn om de externe verbinding tot stand te brengen. |
| **Start PowerShell.exe**       | Hiermee opent u een PowerShell-console.                                                                                                                                                      |
| **Scriptvenster bovenaan weergeven**       | Hiermee wordt het deelvenster Script naar boven in de weergave verplaatst.                                                                                                                                 |
| **Scriptvenster rechts weergeven**     | Hiermee wordt het deelvenster Script naar rechts in de weergave verplaatst.                                                                                                                               |
| **Scriptvenster gemaximaliseerd weergeven** | Maximaliseert het scriptvenster.                                                                                                                                                       |
| **Opdrachtvenster tonen** | Geeft het deelvenster Opdrachten voor geïnstalleerde modules weer als een afzonderlijk venster. |
| **Opdracht-invoegprogramma tonen** | Geeft het deelvenster Opdrachten voor geïnstalleerde modules weer als een zijbalk-invoegsel. |


## <a name="script-tab"></a>Tabblad Script

Geeft de naam weer van het script dat u wilt bewerken. U kunt op een scripttabblad klikken om het script te selecteren dat u wilt bewerken.

Wanneer u naar het scripttabblad gaat, wordt het volledig gekwalificeerde pad naar het scriptbestand weergegeven in de knopinfo.

## <a name="script-pane"></a>Scriptdeelvenster

Hiermee kunt u scripts maken en uitvoeren. U kunt bestaande scripts openen, bewerken en uitvoeren in het deelvenster Script. Zie Scripts schrijven en uitvoeren in de Windows PowerShell ISE voor [meer Windows PowerShell ISE.](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md)

## <a name="console-pane"></a>Consoledeelvenster

Geeft de resultaten weer van de opdrachten en scripts die u hebt uitgevoerd. U kunt opdrachten uitvoeren in het deelvenster Console. U kunt de inhoud ook kopiëren en verwijderen in het deelvenster Console.

Raadpleeg voor meer informatie de volgende artikelen:

- [Het consoledeelvenster in de Windows PowerShell ISE](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)
- [How to Debug Scripts in Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md) (Fouten opsporen in scripts met Windows PowerShell ISE)
- [Tab-aanvulling gebruiken in het scriptvenster en consolevenster](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md)

## <a name="status-bar"></a>Statusbalk

Hiermee kunt u zien of de opdrachten en scripts die u hebt uitgevoerd, zijn voltooid. De statusbalk staat helemaal onderaan de weergave. Geselecteerde gedeelten van foutberichten worden weergegeven op de statusbalk.

## <a name="text-size-slider"></a>Text-Size schuifregelaar

Verhoogt of verkleint de grootte van de tekst op het scherm.

## <a name="help"></a>Help

Help voor Windows PowerShell ISE is beschikbaar op docs.microsoft.com. U kunt de Help openen door te klikken **op Windows PowerShell ISE Help** in het menu **Help** of door ergens op de toets <kbd>F1</kbd> te drukken, behalve wanneer de cursor zich op de naam van een cmdlet in het scriptvenster of het consolevenster.
In het **menu Help** kunt u ook de cmdlet uitvoeren en het opdrachtvenster weergeven dat u helpt bij het maken van opdrachten door alle parameters voor een cmdlet weer te geven en de parameters in te vullen in een eenvoudig te gebruiken `Update-Help` formulier.

## <a name="see-also"></a>Zie ook

- [Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Profielen gebruiken in Windows PowerShell ISE](How-to-Use-Profiles-in-Windows-PowerShell-ISE.md)
- [Toegankelijkheid in Windows PowerShell ISE](Accessibility-in-Windows-PowerShell-ISE.md)
- [Sneltoetsen voor de Windows PowerShell ISE](Keyboard-Shortcuts-for-the-Windows-PowerShell-ISE.md)
