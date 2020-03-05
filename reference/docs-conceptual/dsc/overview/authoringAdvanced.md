---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Informatie over de rol van DSC in een CI/CD-pijp lijn
ms.openlocfilehash: 79740225c030974546035b67e0f873fa00aa690a
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279346"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>Informatie over de rol van DSC in een CI/CD-pijp lijn

In dit artikel worden de soorten benaderingen beschreven die beschikbaar zijn voor het combi neren van configuraties en resources.
Het doel van elk scenario is hetzelfde, om de complexiteit te reduceren wanneer meerdere configuraties de voor keur hebben om de eind status van de server implementatie te bereiken. Een voor beeld hiervan is dat meerdere teams bijdragen aan het resultaat van een server implementatie, zoals een toepassings eigenaar die de toepassings status bijhoudt en een centraal team wijzigingen in de beveiligings basislijnen aanbrengt. De nuances van elke benadering, met inbegrip van de voor delen en risico's, worden hier beschreven.

![Pijplijn](media/authoringAdvanced/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Typen technieken voor gezamenlijk ontwerpen

Er zijn twee oplossingen ingebouwd in lokale Configuration Manager om dit concept in te scha kelen:

|        Concept         |                    Gedetailleerde gegevens                     |
| ---------------------- | ----------------------------------------------------------- |
| Gedeeltelijke configuraties | [Documentatie](../pull-server/partialConfigs.md)           |
| Samengestelde resources    | [Documentatie](../resources/authoringResourceComposite.md) |

## <a name="understanding-the-impact-of-each-approach"></a>Het effect van elke benadering

Een van deze oplossingen kan worden gebruikt om het resultaat van een server implementatie te beheren. Er is echter een aanzienlijk verschil in de impact van het gebruik van elke benadering.

## <a name="partial-configurations"></a>Gedeeltelijke configuraties

Bij het gebruik van gedeeltelijke configuraties is lokale Configuration Manager geconfigureerd om meerdere configuraties onafhankelijk te beheren. Configuraties worden onafhankelijk gecompileerd en vervolgens toegewezen aan het knoop punt. Hiervoor moet LCM vooraf worden geconfigureerd met de naam van elke configuratie.

![PartialConfiguration](media/authoringAdvanced/PartialConfiguration.jpg)

Gedeeltelijke configuraties bieden twee of meer teams die de configuratie van een server volledig kunnen beheren, vaak zonder het voor deel van communicatie of samen werking.

Klanten hebben feedback gegeven die dit kan leiden tot bron conflicten, onbedoelde onderdrukkingen en uiteindelijk verlies van echte configuratie beheer van de Asset.

Daarnaast hebben klanten feedback gegeven die bij het gebruik van dit model de configuratie wijzigingen van teams beheert waarschijnlijk niet volledig worden getest via een release pijplijn, waardoor onverwachte resultaten ontstaan bij de productie.

**Het is essentieel dat één pijp lijn wordt gebruikt om alle wijzigingen te evalueren die aan servers worden vrijgegeven.**

In de onderstaande afbeelding heeft Team B hun gedeeltelijke configuratie vrijgegeven aan team A. team A voert vervolgens hun tests uit op een server waarop beide configuraties zijn toegepast. In dit model is slechts één instantie gemachtigd om wijzigingen aan te brengen in de productie.

![PartialSinglePipeline](media/authoringAdvanced/PartialSinglePipeline.jpg)

Als er wijzigingen zijn vereist van Team B, moeten ze een pull-aanvraag indienen bij de bron beheer omgeving van team A. Team A bekijkt vervolgens de wijzigingen met behulp van test automatisering en release to Production wanneer er betrouw baarheid is dat de wijzigingen geen fouten veroorzaken in de toepassingen of services die door de server worden gehost.

## <a name="composite-resources"></a>Samengestelde resources

Een samengestelde resource is een DSC-configuratie die is verpakt als een resource. Er zijn geen speciale vereisten voor het configureren van LCM om samengestelde resources te accepteren. De resources worden gebruikt binnen een nieuwe configuratie en een enkele compilatie resulteert in één MOF-bestand.

![CompositeResource](media/authoringAdvanced/CompositeResource.jpg)

Er zijn twee veelvoorkomende scenario's voor samengestelde resources. De eerste is om complexiteit en abstracte unieke concepten te reduceren. De tweede is om toe te staan dat basis lijnen worden verpakt zodat een toepassings team veilig kan worden geïmplementeerd via hun release pijplijn tot productie nadat alle tests zijn geslaagd.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = "Present"
    Path = "c:\inetpub\file1.zip"
    Source = "http://uri/file1.zip"
  }
  Service A
  {
    Ensure = "Present"
    Name = "ServiceA"
    Status = "Running"
  }
  SecurityBaseline Settings
  {
    Ensure = "Present"
    Datacenter = "NorthAmerica"
  }
}
```

Samengestelde resources bevorderen zowel samen stelling als samen werking met behulp van een pijp lijn tijdens het bouwen van een operationele loop tijd.

Mogelijk maakt u al gebruik van samengestelde resources zonder deze te realiseren. Een voor beeld is **serviceset**.
Deze resource beheert de status van meerdere Windows-Services zonder deze afzonderlijk te hoeven aanbieden. De eigenschap name accepteert een matrix met teken reeksen om de naam van elke service op te geven. Wanneer de configuratie is gecompileerd, bevat de MOF een unieke service sectie voor elk van de namen die worden door gegeven aan serviceset.

Organisaties kunnen "agents" of "middleware" hebben die op elke server moeten worden geïnstalleerd. Een samengestelde resource is het beste antwoord op het beheren van de afhankelijkheden, het instellen en configureren van dergelijke hulpprogram ma's en hulpprogram ma's.

De persoon of het team dat verantwoordelijk is voor oplossingen die meerdere servers beslaan, is een configuratie met hun vereisten. Vervolgens wordt de configuratie gebundeld als een samengestelde resource met behulp van de instructies in de documentatie voor de samengestelde resource. Ten slotte moet de nieuwe samengestelde resource worden gepubliceerd op een locatie zoals een bestands share of NuGet feed waar toepassings teams deze kunnen gebruiken in hun configuraties.

Telkens wanneer het team een nieuwe versie loslaat, wordt het versie nummer in het module manifest voor de samengestelde resource verhoogd. De toepassings teams bevatten de samengestelde resource in de configuratie die ze ontwerpen voor het beheren van toepassings afhankelijkheden. Wanneer de operations/Security-teams een nieuwe versie van hun resource vrijgeven, melden ze de toepassings teams van een nieuwe wijziging.

De toepassings teams kunnen een vrijgave voor productie activeren waarbij alleen de basis lijnen worden gewijzigd.
Dit biedt echter een kans om de impact op toepassingen te evalueren voordat het risico op een service storing optreedt.

> [!NOTE]
> Feedback over het gebruik van samengestelde resources bevat criticism die wijzigingen aanbrengen vereist het compileren en uitgeven van een nieuwe MOF. Dit is standaard. Elke nieuwe configuratie release moet een statische verwijzing naar een specifieke versie van elke resource bevatten en moet worden gevalideerd door tests voordat productie server knooppunten worden bereikt. Het proces van het testen en vrijgeven van wijzigingen van broncode beheer maakt een veilige omgeving voor het vrijgeven van wijzigingen in kleine, maar veelvuldige batches.

Meer informatie over het gebruik van release pijplijnen voor het beheren van de basis infrastructuur vindt u in het Witboek: [het pipeline-model voor de release](../further-reading/whitepapers.md).
