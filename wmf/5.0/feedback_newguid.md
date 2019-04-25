---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085319"
---
# <a name="new-guid"></a>New-Guid
Vaak script (of misschien schrijven van een DSC-resource), hebt u de noodzaak van een unieke id. GUID's werken, en is het eenvoudig om aan te roepen van het .NET Framework Guid-klasse voor het genereren van een, maar met een cmdlet kunt u dit sneller wordt ontdekt voor eindgebruikers die nog niet bekend bent met de .NET Framework-klasse:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
