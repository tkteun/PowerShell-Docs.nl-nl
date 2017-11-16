---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a>Nieuwe Guid
Vaak script (of misschien schrijven van een DSC-resource), hebt u de noodzaak van een unieke id. GUID's werken ook, en het is gemakkelijk om aan te roepen de .NET Framework-Guid-klasse voor het genereren van een, maar met een cmdlet maakt dit beter kunnen worden gevonden voor eindgebruikers die niet al bekend met de .NET Framework-klasse bent:

PS C:\\ &gt; nieuwe Guid

GUID

----

e19d6ea5-3cc2-4DB9-8095-0cdaed5a703d

