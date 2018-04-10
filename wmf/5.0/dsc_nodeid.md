---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a>Scheiding van knooppunt- en configuratie-id's

## <a name="overview"></a>Overzicht

Om te kunnen bieden een flexibele en meer gestroomlijnde ervaring bij het gebruik van DSC in Pull-modus, hebben we een aantal functies in deze release toegevoegd. Deze functies zijn bedoeld om u de flexibiliteit eenvoudig instellen en configuraties implementeren op meerdere knooppunten terwijl u nog steeds bijhouden van de status en rapportage-informatie voor elk knooppunt afzonderlijk toestaan.
Deze functies zijn als volgt:

* De configuratienaam van een die de configuratie voor een computer identificeert. Deze naam kan worden gedeeld door meerdere doelknooppunten
* Een agent-ID die een unieke identificatie van één knooppunt
* Een registratiestap die alleen de eerste keer een doelknooppunt plaatsvindt verbinding maakt met een pull-server

**Opmerking:** deze functies en functionaliteit zijn toegevoegd en de bestaande pull-functies en -concepten niet vervangen. U kunt deze nieuwe functies of de oudere met de nieuwe pull-server de back-upfunctie in deze release.

Zie voor meer informatie [een pull-client met behulp van configuratienamen instellen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)