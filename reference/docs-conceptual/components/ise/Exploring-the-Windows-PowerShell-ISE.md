---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Kennismaking met Windows PowerShell ISE
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 059651f159fb2636a93167709134788e90d062b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404458"
---
# <a name="exploring-the-windows-powershell-ise"></a>Kennismaking met Windows PowerShell ISE

U kunt de Windows PowerShell® Integrated Scripting Environment (ISE) gebruiken om te maken, uitvoeren en fouten opsporen in opdrachten en scripts. De Windows PowerShell ISE bestaat uit de in de menubalk, Windows PowerShell-tabbladen, de werkbalk, script tabbladen, een scriptvenster, een consolevenster, een statusbalk, een schuifregelaar tekst-grootte en contextgevoelige Help.

> [!NOTE]
> Beginnen met Windows PowerShell ISE 3.0, de opdracht en de uitvoer deelvensters zijn gecombineerd in één Console-venster.

## <a name="menu-bar"></a>In de menubalk

De menubalk bevat de **bestand**, **bewerken**, **weergave**, **extra**, **Debug**,  **Invoegtoepassingen**, en **Help** menu's. De knoppen op de menu's kunnen u taken met betrekking tot scripts schrijven en actieve en actieve opdrachten in de Windows PowerShell ISE uit te voeren. Bovendien een [invoegtoepassing hulpprogramma](../../core-powershell/ise/The-ISEAddOnTool-Object.md) mag worden geplaatst op de menubalk, door het uitvoeren van scripts die gebruikmaken van de [de objectmodelhiërarchie van ISE](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> In Windows PowerShell ISE 2.0, de **extra** en **invoegtoepassingen** menu's zijn niet aanwezig.

## <a name="windows-powershell-tabs"></a>Windows PowerShell tabbladen

Een Windows PowerShell-tabblad is de omgeving waarin een Windows PowerShell-script wordt uitgevoerd. U kunt nieuwe Windows PowerShell-tabbladen openen in de Windows PowerShell ISE op afzonderlijke omgevingen maken op uw lokale computer of op externe computers. Er kunnen maximaal acht PowerShell tabbladen tegelijkertijd openen.

## <a name="toolbar"></a>Werkbalk

De volgende knoppen bevinden zich op de werkbalk.

|Knop|Functie|
|----------|------------|
|**Nieuw**|Hiermee opent u een nieuw script.|
|**Open**|Hiermee opent u een bestaand script of een bestand.|
|**Opslaan**|Hiermee slaat u een script of een bestand.|
|**Knippen**|De geselecteerde tekst knippen en vervolgens gekopieerd naar het Klembord.|
|**Kopiëren**|De geselecteerde tekst naar het Klembord gekopieerd.|
|**Plakken**|De inhoud van het Klembord op de cursorlocatie geplakt.|
|**Deelvenster Uitvoer wissen**|Hiermee schakelt u alle inhoud in het deelvenster Uitvoer.|
|**Ongedaan maken**|De bewerking die zojuist is uitgevoerd, ongedaan maken.|
|**Redo**|Voert de actie die alleen ongedaan is gemaakt.|
|**Script uitvoeren**|Een script wordt uitgevoerd.|
|**Selectie uitvoeren**|Een geselecteerde gedeelte van een script wordt uitgevoerd.|
|**Uitvoering stoppen**|Hiermee stopt u een script dat wordt uitgevoerd.|
|**Nieuwe externe PowerShell-tabblad**|Hiermee maakt u een nieuwe PowerShell-tabblad waarmee een sessie op een externe computer. Een dialoogvenster wordt weergegeven en vraagt u om in te voeren van gegevens die zijn vereist om de externe verbinding te maken.|
|**Start PowerShell.exe**|Hiermee opent een PowerShell-Console.|
|**Script deelvenster-bovenaan weergeven**|Het scriptvenster verplaatst naar de bovenkant in de weergave.|
|**Scriptvenster rechts weergeven**|Het scriptvenster verplaatst naar rechts in de weergave.|
|**Gemaximaliseerd scriptvenster weergeven**|Het scriptvenster maximaliseert.|

## <a name="script-tab"></a>Tabblad script

Geeft de naam van het script dat u wilt bewerken. U kunt klikken op een tabblad script om te selecteren van het script dat u wilt bewerken.

Wanneer u naar het tabblad script verwijzen, wordt het volledig gekwalificeerde pad naar het scriptbestand in een tooltip weergegeven.

## <a name="script-pane"></a>Scriptvenster

Hiermee kunt u scripts maken en uitvoeren. U kunt openen, bewerken en bestaande scripts uitvoeren in het scriptvenster.

## <a name="output-pane"></a>Deelvenster Uitvoer

Geeft de resultaten van de opdrachten en scripts die u hebt uitgevoerd. U kunt ook kopiëren en schakelt u de inhoud in het deelvenster Uitvoer.

## <a name="command-pane"></a>Deelvenster van de opdracht

Kunt u het schrijven van opdrachten. U kunt een opdracht een regel of een met meerdere regels in het deelvenster opdracht uitvoeren. Druk op SHIFT + ENTER drukken om elke regel van een met meerdere regels opdracht en druk op ENTER na de laatste regel voor het uitvoeren van de opdracht met meerdere regels. De prompt weergegeven boven op het opdrachtvenster ziet u het pad naar de huidige werkmap.

## <a name="status-bar"></a>Statusbalk

Hiermee kunt u zien of de opdrachten en scripts die u uitvoert voltooid zijn. De statusbalk is zeer onder aan de weergave. Geselecteerde gedeelten van foutberichten worden weergegeven op de statusbalk.

## <a name="text-size-slider"></a>Tekengrootte: schuifregelaar

Vergroot of verkleint u de grootte van de tekst op het scherm.

## <a name="help"></a>Help

Help voor Windows PowerShell ISE is beschikbaar in de TechNet-bibliotheek op het Web. U kunt de Help openen door te klikken op **Help van Windows PowerShell ISE** op de **Help** menu of druk op F1 drukt overal, behalve wanneer de cursor op de cmdletnaam van een in het scriptvenster of in het consolevenster. Uit de **Help** menu kunt u ook uitvoeren de cmdlet Update-Help, en het opdrachtvenster die u helpt bij het maken van opdrachten door alle parameters voor een cmdlet weergegeven en u in de parameters in te vullen in te schakelen weer een formulier kunt u eenvoudig te gebruiken.

## <a name="see-also"></a>Zie ook

- [Maak kennis met de Windows PowerShell ISE](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)