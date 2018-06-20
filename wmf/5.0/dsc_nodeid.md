---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 6c036c2d8f97e559d20dd3ac40133fa06f5dab08
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188282"
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
