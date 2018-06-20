---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Kennismaking met Windows PowerShell ISE
ms.assetid: e0d2c6e8-5126-40e7-a1e1-d1cff29fe94a
ms.openlocfilehash: 059651f159fb2636a93167709134788e90d062b8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952270"
---
# <a name="exploring-the-windows-powershell-ise"></a>Kennismaking met Windows PowerShell ISE

U kunt de Windows PowerShell® Integrated Scripting Environment (ISE) maakt en foutopsporing van opdrachten en scripts uitvoeren. De Windows PowerShell ISE bestaat uit de menubalk, Windows PowerShell-tabbladen, de werkbalk, script tabbladen, een scriptvenster, een consolevenster, een statusbalk, een schuifregelaar tekst grootte en contextgevoelige Help.

> [!NOTE]
> Windows PowerShell ISE 3.0 vanaf de opdracht en de uitvoer deelvensters zijn gecombineerd in één Console deelvenster.

## <a name="menu-bar"></a>Menubalk

De menubalk bevat de **bestand**, **bewerken**, **weergave**, **extra**, **Debug**,  **Invoegtoepassingen**, en **Help** menu's. De knoppen op de menu's kunnen u taken met betrekking tot scripts schrijven en wordt uitgevoerd en actieve opdrachten in de Windows PowerShell ISE uitvoeren. Bovendien een [invoegtoepassing hulpprogramma](../../core-powershell/ise/The-ISEAddOnTool-Object.md) kan worden geplaatst op de menubalk door het uitvoeren van scripts die gebruikmaken van de [de ISE-Model objecthiërarchie](../../core-powershell/ise/The-ISE-Object-Model-Hierarchy.md).

> [!NOTE]
> In Windows PowerShell ISE 2.0 de **extra** en **invoegtoepassingen** menu's zijn niet aanwezig.

## <a name="windows-powershell-tabs"></a>Tabbladen van Windows PowerShell

Een Windows PowerShell-tabblad is de omgeving waarin een Windows PowerShell-script wordt uitgevoerd. U kunt nieuwe Windows PowerShell-tabbladen openen in de Windows PowerShell ISE afzonderlijke omgevingen maken op de lokale computer of op externe computers. Mogelijk hebt u maximaal acht PowerShell tabbladen tegelijkertijd openen.

## <a name="toolbar"></a>Werkbalk

De volgende knoppen bevinden zich op de werkbalk.

|Knop|Functie|
|----------|------------|
|**Nieuw**|Hiermee opent u een nieuw script.|
|**Open**|Hiermee opent u een bestaand script of het bestand.|
|**Opslaan**|Hiermee slaat u een script of het bestand.|
|**Knippen**|De geselecteerde tekst knippen en naar het Klembord gekopieerd.|
|**Kopiëren**|De geselecteerde tekst naar het Klembord gekopieerd.|
|**Paste**|De inhoud van het Klembord op de cursorlocatie plakken|
|**Deelvenster Uitvoer wissen**|Hiermee wist u alle inhoud in het deelvenster Uitvoer.|
|**Undo**|Keert de actie die zojuist is uitgevoerd.|
|**Redo**|Voert de actie die u zojuist hebt ongedaan is gemaakt.|
|**Script uitvoeren**|Een script wordt uitgevoerd.|
|**Selectie uitvoeren**|Een geselecteerde deel van een script kan worden uitgevoerd.|
|**Uitvoering stoppen**|Hiermee stopt een script dat wordt uitgevoerd.|
|**Nieuwe externe PowerShell-tabblad**|Maakt een nieuw PowerShell-tabblad waarmee een sessie op een externe computer. Een dialoogvenster wordt weergegeven en u wordt gevraagd om de gegevens die zijn vereist voor het maken van de externe verbinding invoeren.|
|**Start PowerShell.exe**|Hiermee opent u een PowerShell-Console.|
|**Script deelvenster bovenkant weergeven**|Verplaatst het scriptvenster boven in de weergave.|
|**Scriptvenster rechts weergeven**|Verplaatst het scriptvenster naar rechts in de weergave.|
|**Gemaximaliseerd scriptvenster weergeven**|Hiermee maximaliseert u het Script-veld.|

## <a name="script-tab"></a>Tabblad script

Hiermee wordt de naam van het script dat u wilt bewerken. U kunt klikken op de tab script voor het script dat u wilt bewerken.

Wanneer u het tabblad script aanwijst, is het volledig gekwalificeerde pad naar het scriptbestand wordt weergegeven in knopinfo.

## <a name="script-pane"></a>Scriptvenster

Hiermee kunt u maken en uitvoeren van scripts. U kunt openen, bewerken en bestaande scripts uitvoeren in het scriptvenster.

## <a name="output-pane"></a>Deelvenster Uitvoer

Geeft de resultaten van de opdrachten en scripts die u hebt uitgevoerd. U kunt ook kopiëren en wissen van de inhoud in het deelvenster Uitvoer.

## <a name="command-pane"></a>Deelvenster van de opdracht

Hiermee kunt u opdrachten schrijven. U kunt een opdracht een regel of een opdracht met meerdere regels uitvoeren in het opdrachtvenster. Druk op SHIFT + ENTER drukken om elke regel van een opdracht met meerdere regels en druk op ENTER na de laatste regel de meerregelige opdracht uit te voeren. De prompt weergegeven boven op het opdrachtvenster ziet u het pad naar de huidige werkmap.

## <a name="status-bar"></a>Statusbalk

Hiermee kunt u zien of de opdrachten en scripts die u uitvoert voltooid zijn. De statusbalk is zeer onder aan de weergave. Geselecteerde gedeelten van foutberichten worden weergegeven op de statusbalk.

## <a name="text-size-slider"></a>Schuifregelaar tekst grootte

Verhoogt of verlaagt u hiermee de grootte van de tekst op het scherm.

## <a name="help"></a>Help

Help voor Windows PowerShell ISE is beschikbaar in de TechNet-bibliotheek op het Web. U kunt de Help openen door te klikken op **Help voor Windows PowerShell ISE** op de **Help** menu of door de F1-toets overal blijft, behalve wanneer de cursor op de naam van een cmdlet in het scriptvenster of het consolevenster. Van de **Help** menu u kunt ook de Update-Help-cmdlet uitvoeren en weergeven van het opdrachtvenster die u helpt bij het samenstellen van opdrachten door alle parameters voor een cmdlet weergegeven en kunt u in de parameters in te vullen een formulier eenvoudig te gebruiken.

## <a name="see-also"></a>Zie ook

- [Introducing the Windows PowerShell ISE](../../core-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md)