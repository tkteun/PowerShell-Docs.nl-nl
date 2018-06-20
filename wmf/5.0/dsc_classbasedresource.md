---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221847"
---
# <a name="class-based-dsc-resources"></a>DSC-resources op basis van een klasse

## <a name="defining-dsc-resources-with-classes"></a>DSC-resources met klassen definiëren

Op basis van feedback, hebben we aangebracht ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.
De belangrijkste verschillen tussen een klasse gebaseerde DSC-resource en een cmdlet DSC-resourceprovider zijn:

* Een MOF-bestand voor het schema is niet vereist.
* Een **DSCResource** submap in de modulemap is niet vereist.
* Een PowerShell-module-bestand kan meerdere DSC-resource klassen bevatten.

Zie voor meer informatie [schrijven van een aangepaste DSC-resource met PowerShell klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).
