---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a>New-Guid
Vaak script (of misschien schrijven van een DSC-resource), hebt u de noodzaak van een unieke id. GUID's werken ook, en het is gemakkelijk om aan te roepen de .NET Framework-Guid-klasse voor het genereren van een, maar met een cmdlet maakt dit beter kunnen worden gevonden voor eindgebruikers die niet al bekend met de .NET Framework-klasse bent:

PS C:\\ &gt; nieuwe Guid

GUID

----

e19d6ea5-3cc2-4DB9-8095-0cdaed5a703d
