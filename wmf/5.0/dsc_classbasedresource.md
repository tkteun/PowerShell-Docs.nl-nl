---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 4def20aa95f66ab23c9eee575150bc3db02541d8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="class-based-dsc-resources"></a>DSC-resources op basis van een klasse

## <a name="defining-dsc-resources-with-classes"></a>DSC-resources met klassen definiëren

Op basis van feedback, hebben we aangebracht ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen.
De belangrijkste verschillen tussen een klasse gebaseerde DSC-resource en een cmdlet DSC-resourceprovider zijn:

* Een MOF-bestand voor het schema is niet vereist.
* Een **DSCResource** submap in de modulemap is niet vereist.
* Een PowerShell-module-bestand kan meerdere DSC-resource klassen bevatten.

Zie voor meer informatie [schrijven van een aangepaste DSC-resource met PowerShell klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).