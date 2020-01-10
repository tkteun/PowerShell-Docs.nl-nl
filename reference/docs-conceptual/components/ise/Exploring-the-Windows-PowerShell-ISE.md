---
ms.date: 01/02/2020
keywords: Power shell, cmdlet
title: Kennismaking met Windows PowerShell ISE
ms.openlocfilehash: 03728a8c83962894b27738609a5b1bec841fdb13
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737097"
---
# <a name="exploring-the-windows-powershell-ise"></a>Kennismaking met Windows PowerShell ISE

U kunt de Windows Power shell® Integrated Scripting Environment (ISE) gebruiken om opdrachten en scripts te maken, uit te voeren en fouten op te sporen. De Windows PowerShell ISE bestaat uit de menu balk, Windows Power shell-tabbladen, de werk balk, script tabbladen, een script paneel, een console venster, een status balk, een schuif regelaar voor tekst formaat en context gevoelige Help.

> [!NOTE]
> Vanaf Windows PowerShell ISE 3,0 worden de opdracht-en uitvoer deel Vensters gecombineerd in één console venster.

## <a name="menu-bar"></a>Menubalk

De menu balk bevat de **menu's bestand**, **bewerken**, **weer gave**, **extra**, **fout opsporing**, **invoeg toepassingen**en **Help** . Met de knoppen in de menu's kunt u taken uitvoeren die betrekking hebben op het schrijven en uitvoeren van scripts en het uitvoeren van opdrachten in de Windows PowerShell ISE. Daarnaast kan een [invoeg programma](object-model/The-ISEAddOnTool-Object.md) worden geplaatst op de menu balk door scripts uit te voeren die gebruikmaken van de [ISE object model hiërarchie](object-model/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> In Windows PowerShell ISE 2,0 zijn de menu's **tools** en **invoeg toepassingen** niet aanwezig.

## <a name="windows-powershell-tabs"></a>Windows Power shell-tabbladen

Een Windows Power shell-tabblad is de omgeving waarin een Windows Power shell-script wordt uitgevoerd. U kunt nieuwe Windows Power shell-tabbladen in de Windows PowerShell ISE openen om afzonderlijke omgevingen op uw lokale computer of op externe computers te maken. U kunt Maxi maal acht Power shell-tabbladen tegelijkertijd openen.

## <a name="toolbar"></a>Werkbalk

De volgende knoppen bevinden zich op de werk balk.

|             Knop             |                                                                                     Functie                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Nieuw**                        | Hiermee opent u een nieuw script.                                                                                                                                                              |
| **Lopend**                       | Hiermee opent u een bestaand script of bestand.                                                                                                                                                |
| **Opslaan**                       | Hiermee slaat u een script of bestand op.                                                                                                                                                          |
| **Verminderen**                        | Hiermee knipt u de geselecteerde tekst en kopieert u deze naar het klem bord.                                                                                                                           |
| **Copy**                       | Hiermee wordt de geselecteerde tekst naar het klem bord gekopieerd.                                                                                                                                       |
| **Plakken**                      | Hiermee wordt de inhoud van het klem bord op de cursor locatie geplakt.                                                                                                                     |
| **Uitvoer venster wissen**          | Hiermee wordt alle inhoud in het deel venster Uitvoer gewist.                                                                                                                                           |
| **Opdracht**                       | Hiermee wordt de zojuist uitgevoerde actie omgedraaid.                                                                                                                                     |
| **Redo**                       | Voert de actie uit die zojuist ongedaan is gemaakt.                                                                                                                                        |
| **Script uitvoeren**                 | Voert een script uit.                                                                                                                                                                   |
| **Selectie uitvoeren**              | Hiermee voert u een geselecteerd deel van een script uit.                                                                                                                                             |
| **Uitvoering stoppen**             | Hiermee stopt u een script dat wordt uitgevoerd.                                                                                                                                                  |
| **Nieuwe externe Power shell-tabblad**  | Hiermee maakt u een nieuw Power shell-tabblad dat een sessie op een externe computer tot stand brengt. Er wordt een dialoog venster weer gegeven waarin wordt gevraagd om de gegevens op te geven die nodig zijn om de externe verbinding tot stand te brengen. |
| **Power shell. exe starten**       | Hiermee opent u een Power shell-console.                                                                                                                                                      |
| **Script paneel bovenaan weer geven**       | Hiermee verplaatst u het Script venster naar de bovenkant in de weer gave.                                                                                                                                 |
| **Script venster rechts weer geven**     | Het deel venster script naar rechts in de weer gave verplaatsen.                                                                                                                               |
| **Gemaximaliseerd Script venster weer geven** | Maximaliseert het Script-venster.                                                                                                                                                       |

## <a name="script-tab"></a>Script tabblad

Hier wordt de naam weer gegeven van het script dat u wilt bewerken. U kunt klikken op een script tabblad om het script te selecteren dat u wilt bewerken.

Wanneer u het tabblad script aanwijst, wordt het volledig gekwalificeerde pad naar het script bestand weer gegeven in de knop info.

## <a name="script-pane"></a>Script venster

Hiermee kunt u scripts maken en uitvoeren. U kunt bestaande scripts openen, bewerken en uitvoeren in het Script-venster.

## <a name="output-pane"></a>Deel venster uitvoer

Hier worden de resultaten weer gegeven van de opdrachten en scripts die u hebt uitgevoerd. U kunt ook de inhoud kopiëren en wissen in het deel venster uitvoer.

## <a name="command-pane"></a>Opdracht venster

Hiermee kunt u opdrachten schrijven. U kunt een opdracht met één regel of een opdracht voor meerdere regels uitvoeren in het opdracht venster. Druk op <kbd>SHIFT</kbd>+<kbd>Enter</kbd> om elke regel van een opdracht voor meerdere regels op te geven en druk op <kbd>Enter</kbd> na de laatste regel om de opdracht voor meerdere regels uit te voeren. In de prompt boven in het opdracht venster wordt het pad naar de huidige werkmap weer gegeven.

## <a name="status-bar"></a>Status balk

Met kunt u zien of de opdrachten en scripts die u uitvoert, zijn voltooid. De status balk bevindt zich aan de onderkant van de weer gave. Geselecteerde delen van fout berichten worden weer gegeven op de status balk.

## <a name="text-size-slider"></a>Schuif regelaar voor tekst grootte

Hiermee wordt de grootte van de tekst op het scherm verg root of verkleind.

## <a name="help"></a>Help

Help voor Windows PowerShell ISE is beschikbaar op internet in de TechNet-bibliotheek. U kunt de Help openen door te klikken op **Windows PowerShell ISE Help** in het menu **Help** of door op de <kbd>F1</kbd> -toets te drukken, behalve wanneer de cursor zich op een naam van de cmdlet bevindt in het deel venster script of in het console venster.
In het **Help** -menu kunt u ook de `Update-Help`-cmdlet uitvoeren en het opdracht venster weer geven waarmee u opdrachten aanbiedt door alle para meters voor een cmdlet weer te geven en u in staat te stellen de para meters in een gemakkelijk te gebruiken formulier in te vullen.

## <a name="see-also"></a>Zie ook

- [Introductie van de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
