---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a>New-Guid
Vaak script (of misschien schrijven van een DSC-resource), hebt u de noodzaak van een unieke id. GUID's werken ook, en het is gemakkelijk om aan te roepen de .NET Framework-Guid-klasse voor het genereren van een, maar met een cmdlet maakt dit beter kunnen worden gevonden voor eindgebruikers die niet al bekend met de .NET Framework-klasse bent:

PS C:\\ &gt; nieuwe Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d