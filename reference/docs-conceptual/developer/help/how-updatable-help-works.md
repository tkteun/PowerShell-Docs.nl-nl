---
title: De werking van Help die kan worden bijgewerkt
ms.date: 09/13/2016
ms.openlocfilehash: 4849ce81e31171c6822a9078a77ebb45729185a3
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893285"
---
# <a name="how-updatable-help-works"></a>De werking van Help die kan worden bijgewerkt

In dit onderwerp wordt uitgelegd hoe u met behulp van bijwerk bare Help het HelpInfo XML-bestand en de CAB-bestanden voor elke module kunt verwerken, en wordt bijgewerkte Help voor gebruikers geïnstalleerd.

## <a name="the-update-help-process"></a>De update-Help proces

De volgende lijst bevat de acties van de cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) wanneer een gebruiker een opdracht uitvoert om de Help-bestanden voor een module in een bepaalde UI-cultuur bij te werken.

1. `Update-Help` Hiermee wordt het XML-bestand van de externe HelpInfo opgehaald van de locatie die is opgegeven door de waarde van de sleutel **HelpInfoURI** in het module manifest en wordt het bestand gevalideerd op basis van het schema. (Zie [HelpInfo XML-schema](./helpinfo-xml-schema.md)voor het weer geven van het schema.) Zoekt vervolgens naar `Update-Help` een lokaal HelpInfo XML-bestand voor de module in de module directory op de computer van de gebruiker.

1. `Update-Help` vergelijkt het versie nummer van de Help bestanden voor de opgegeven UI-cultuur in de externe en lokale HelpInfo XML-bestanden voor de module. Als het versie nummer van het externe bestand groter is dan het versie nummer van het lokale bestand, of als er geen lokaal HelpInfo XML-bestand voor de module is, wordt voor `Update-Help` bereid om nieuwe Help-bestanden te downloaden.

1. `Update-Help` Hiermee wordt het CAB-bestand voor de module geselecteerd vanaf de locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand voor externe HelpInfo. De module naam, module-GUID en UI-cultuur worden gebruikt voor het identificeren van het CAB-bestand.

1. `Update-Help` Hiermee downloadt u het CAB-bestand, pakt u het uit, valideert u de bestanden van de Help-inhoud en slaat u de Help-inhouds bestanden op in de taalspecifieke submap van de module directory op de computer van de gebruiker.

1. `Update-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door het externe HelpInfo XML-bestand te kopiëren. Het lokale HelpInfo XML-bestand wordt zodanig bewerkt dat het alleen elementen bevat voor het CAB-bestand dat het heeft geïnstalleerd.
   Vervolgens wordt het lokale HelpInfo XML-bestand in de module directory opgeslagen en wordt de update beëindigd.

## <a name="the-save-help-process"></a>Het Help-proces voor opslaan

In de volgende lijst worden de acties beschreven van de cmdlets [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) wanneer een gebruiker opdrachten uitvoert om de Help-bestanden in een bestands share bij te werken en vervolgens deze bestanden gebruiken om de Help-bestanden op de computer van de gebruiker bij te werken.

Met de `Save-Help` cmdlet worden de volgende acties uitgevoerd als reactie op een opdracht om de Help-bestanden op te slaan voor een module in een bestands share die is opgegeven door de para meter **doelpad** .

1. `Save-Help` Hiermee wordt het XML-bestand van de externe HelpInfo opgehaald van de locatie die is opgegeven door de waarde van de sleutel **HelpInfoURI** in het module manifest en wordt het bestand gevalideerd op basis van het schema. (Zie [HelpInfo XML-schema](./helpinfo-xml-schema.md)voor het weer geven van het schema.) Zoekt vervolgens naar `Save-Help` een lokaal HelpInfo XML-bestand in de map die is opgegeven door de para meter **doelpad** in de `Save-Help` opdracht.

1. `Save-Help` vergelijkt het versie nummer van de Help bestanden voor de opgegeven UI-cultuur in de externe en lokale HelpInfo XML-bestanden voor de module. Als het versie nummer van het externe bestand groter is dan het versie nummer van het lokale bestand, of als er geen lokaal HelpInfo XML-bestand is voor de module in de **doelpad** -map, wordt voor `Save-Help` bereid om nieuwe Help-bestanden te downloaden.

1. `Save-Help` Hiermee wordt het CAB-bestand voor de module geselecteerd vanaf de locatie die is opgegeven door het element **HelpContentUri** in het XML-bestand voor externe HelpInfo. De module naam, module-GUID en UI-cultuur worden gebruikt voor het identificeren van het CAB-bestand.

1. `Save-Help` het CAB-bestand wordt gedownload en opgeslagen in de **doelpad** -map. (Er worden geen taalspecifieke submappen gemaakt.)

1. `Save-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door het externe HelpInfo XML-bestand te kopiëren. Het lokale HelpInfo XML-bestand wordt zodanig bewerkt dat het alleen elementen bevat voor het CAB-bestand dat het heeft opgeslagen.
   Vervolgens wordt het lokale HelpInfo XML-bestand opgeslagen in de **doelpad** -map en wordt de update beëindigd.

   Met de `Update-Help` cmdlet worden de volgende acties uitgevoerd als reactie op een opdracht voor het bijwerken van de Help-bestanden op de computer van een gebruiker van de bestanden in een bestands share die is opgegeven door de para meter **SourcePath** .

1. `Update-Help` Hiermee wordt het XML-bestand van de externe HelpInfo opgehaald uit de map **SourcePath** . Vervolgens zoekt het naar een lokaal HelpInfo XML-bestand in de module directory op de computer van de gebruiker.

1. `Update-Help` vergelijkt het versie nummer van de Help bestanden voor de opgegeven UI-cultuur in de externe en lokale HelpInfo XML-bestanden voor de module. Als het versie nummer van het externe bestand groter is dan het versie nummer van het lokale bestand, of als er geen lokaal HelpInfo XML-bestand is, wordt `Update-Help` voor bereid om nieuwe Help-bestanden te installeren.

1. `Update-Help` Hiermee selecteert u het CAB-bestand voor de module uit de map **SourcePath** . De module naam, module-GUID en UI-cultuur worden gebruikt voor het identificeren van het CAB-bestand.

1. `Update-Help` Hiermee wordt het CAB-bestand uitgepakt, worden de Help-inhouds bestanden gevalideerd en worden de Help-inhouds bestanden opgeslagen in de taalspecifieke submap van de module directory op de computer van de gebruiker.

1. `Update-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door het externe HelpInfo XML-bestand te kopiëren. Het lokale HelpInfo XML-bestand wordt zodanig bewerkt dat het alleen elementen bevat voor het CAB-bestand dat het heeft geïnstalleerd.
   Vervolgens wordt het lokale HelpInfo XML-bestand in de module directory opgeslagen en wordt de update beëindigd.
