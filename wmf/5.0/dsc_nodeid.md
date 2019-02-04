---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685758"
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
