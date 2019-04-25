---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058196"
---
# <a name="separation-of-node-and-configuration-ids"></a>Scheiding van knooppunt- en configuratie-id's

## <a name="overview"></a>Overzicht

Om te kunnen bieden een meer flexibele en een gestroomlijnde ervaring bij het gebruik van DSC in de Pull-modus, hebben we een aantal functies in deze release toegevoegd. Deze functies zijn bedoeld om u hebt de flexibiliteit om gemakkelijk instellen en implementeren van configuraties over meerdere knooppunten tijdens het bijhouden van de status en rapportagegegevens afzonderlijk voor elk knooppunt.
Deze functies zijn als volgt:

* De configuratienaam van een waarin de configuratie voor een computer. Deze naam kan worden gedeeld door meerdere doelknooppunten
* Een agent-ID die één knooppunt wordt aangeduid
* Een registratiestap die alleen een doelknooppunt de eerste keer plaatsvindt verbinding maakt met een pull-server

**Opmerking:** Deze functies en functionaliteiten zijn toegevoegd en de bestaande pull-functies en concepten niet vervangen. U kunt deze nieuwe functies of de oudere zijn met de nieuwe pull-server worden verzonden in deze release.

Zie voor meer informatie, [instellen van een pull-client met behulp van configuratienamen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
