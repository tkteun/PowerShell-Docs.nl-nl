---
title: Hoe bij te werken Help Works | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794379"
---
# <a name="how-updatable-help-works"></a>De werking van Help die kan worden bijgewerkt

In dit onderwerp wordt uitgelegd hoe bij te werken Help processen de HelpInfo XML-bestand en de CAB-bestanden voor elke module en installeert de help voor gebruikers bijgewerkt.

## <a name="the-update-help-process"></a>Het proces voor Update-Help

De volgende lijst beschrijft de acties van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet wanneer een gebruiker een opdracht voor het bijwerken van de help-bestanden voor een module in een bepaalde gebruikersinterfacecultuur uitvoert.

1. `Update-Help` Met deze eigenschap wordt het externe HelpInfo XML-bestand van de locatie die is opgegeven door de waarde van de **HelpInfoURI** sleutel in de module-manifest en valideert u het bestand op basis van het schema. (Als u het schema, Zie [HelpInfo XML-Schema](./helpinfo-xml-schema.md).) Vervolgens `Update-Help` zoekt naar een lokale HelpInfo XML-bestand voor de module in de modulemap op de computer van de gebruiker.

2. `Update-Help` vergelijkt het versienummer van de help-bestanden voor de opgegeven cultuur van de gebruikersinterface in de lokale en externe HelpInfo XML-bestanden voor de module. Als het versienummer van het externe bestand is groter dan het versienummer van het lokale bestand, of als er geen lokale HelpInfo XML-bestand voor de module `Update-Help` bereidt het downloaden van nieuwe help-bestanden.

3. `Update-Help` het CAB-bestand voor de module selecteert in de locatie die is opgegeven door de **HelpContentUri** -element in het externe HelpInfo XML-bestand. Deze modulenaam van de, module GUID en gebruikersinterfacecultuur gebruikt om te identificeren van het CAB-bestand.

4. `Update-Help` het CAB-bestand wordt gedownload, Hiermee wordt het, valideert de inhoudsbestanden van Help-informatie en de help-inhoud bestanden opgeslagen in de taalspecifieke submap van de modulemap op de computer van de gebruiker.

5. `Update-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door de externe HelpInfo XML-bestand te kopiëren. Wordt het lokale HelpInfo XML-bestand hebt bewerkt, waarbij er elementen alleen voor de CAB-bestand dat deze is geïnstalleerd. Vervolgens slaat het lokale HelpInfo XML-bestand in de modulemap en is de update.

## <a name="the-save-help-process"></a>Het proces Help opslaan

De volgende lijst beschrijft de acties van de [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets wanneer een gebruiker wordt uitgevoerd voor opdrachten voor het bijwerken van de help-bestanden in een bestandsshare en deze bestanden vervolgens gebruiken om bij te werken van de help-bestanden op de de computer van de gebruiker.

De `Save-Help` cmdlet worden de volgende acties uitgevoerd in reactie op een opdracht voor het opslaan van de help-bestanden voor een module in een bestandsshare die is opgegeven door de **doelpad** parameter.

1. `Save-Help` Met deze eigenschap wordt het externe HelpInfo XML-bestand van de locatie die is opgegeven door de waarde van de **HelpInfoURI** sleutel in de module-manifest en valideert u het bestand op basis van het schema. (Als u het schema, Zie [HelpInfo XML-Schema](./helpinfo-xml-schema.md).) Vervolgens `Save-Help` zoekt naar een lokale HelpInfo XML-bestand in de map die is opgegeven door de **doelpad** parameter in de `Save-Help` opdracht.

2. `Save-Help` vergelijkt het versienummer van de help-bestanden voor de opgegeven cultuur van de gebruikersinterface in de lokale en externe HelpInfo XML-bestanden voor de module. Als het versienummer van het externe bestand is groter dan het versienummer van het lokale bestand, of als er geen lokale HelpInfo XML-bestand voor de module in de **doelpad** directory `Save-Help` bereidt het downloaden van nieuwe help-bestanden.

3. `Save-Help` het CAB-bestand voor de module selecteert in de locatie die is opgegeven door de **HelpContentUri** -element in het externe HelpInfo XML-bestand. Deze modulenaam van de, module GUID en gebruikersinterfacecultuur gebruikt om te identificeren van het CAB-bestand.

4. `Save-Help` het CAB-bestand wordt gedownload en opgeslagen in de **doelpad** directory. (Er wordt geen eventuele submappen taalspecifieke gemaakt.)

5. `Save-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door de externe HelpInfo XML-bestand te kopiëren. Wordt het lokale HelpInfo XML-bestand hebt bewerkt, waarbij er elementen alleen voor het CAB-bestand die zijn opgeslagen. Vervolgens wordt het lokale HelpInfo XML-bestand in de **doelpad** directory en de update is afgelopen.

   De `Update-Help` cmdlet worden de volgende acties uitgevoerd in reactie op een opdracht voor het bijwerken van de help-bestanden op de computer van een gebruiker uit de bestanden in een bestandsshare die is opgegeven door de **bronpad** parameter.

1. `Update-Help` Met deze eigenschap wordt het externe HelpInfo XML-bestand van de **bronpad** directory. Vervolgens wordt gezocht naar een lokale HelpInfo XML-bestand in de modulemap op de computer van de gebruiker.

2. `Update-Help` vergelijkt het versienummer van de help-bestanden voor de opgegeven cultuur van de gebruikersinterface in de lokale en externe HelpInfo XML-bestanden voor de module. Als het versienummer van het externe bestand is groter dan het versienummer van het lokale bestand, of als er geen lokale HelpInfo XML-bestand, `Update-Help` wordt voorbereid voor het installeren van nieuwe help-bestanden.

3. `Update-Help` Hiermee selecteert u het CAB-bestand voor de module op basis van **bronpad** directory. Deze modulenaam van de, module GUID en gebruikersinterfacecultuur gebruikt om te identificeren van het CAB-bestand.

4. `Update-Help` Hiermee wordt het CAB-bestand, valideert de inhoudsbestanden van Help-informatie en de help-inhoud bestanden opgeslagen in de taalspecifieke submap van de modulemap op de computer van de gebruiker.

5. `Update-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door de externe HelpInfo XML-bestand te kopiëren. Wordt het lokale HelpInfo XML-bestand hebt bewerkt, waarbij er elementen alleen voor de CAB-bestand dat deze is geïnstalleerd. Vervolgens slaat het lokale HelpInfo XML-bestand in de modulemap en is de update.