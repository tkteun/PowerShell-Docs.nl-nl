---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685751"
---
# <a name="class-based-dsc-resources"></a>DSC-resources op basis van een klasse

## <a name="defining-dsc-resources-with-classes"></a>DSC-resources met klassen definiëren

Op basis van feedback, hebben we ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.
De belangrijkste verschillen tussen een klasse op basis van DSC-resource en een cmdlet DSC-resourceprovider zijn:

* Een MOF-bestand voor het schema is niet vereist.
* Een **sleutelwoorden dscresource bieden** submap in de modulemap is niet vereist.
* Een PowerShell-module-bestand kan meerdere DSC-resource-klassen bevatten.

Zie voor meer informatie, [schrijven van een aangepaste DSC-resource met de PowerShell-klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).
