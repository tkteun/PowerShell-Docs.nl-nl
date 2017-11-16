---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Op basis van een klasse DSC-Resources

## <a name="defining-dsc-resources-with-classes"></a>DSC-resources met klassen definiëren

Op basis van feedback, hebben we aangebracht ontwerpen op basis van een klasse DSC bronnen eenvoudiger en gemakkelijker te begrijpen. De belangrijkste verschillen tussen een klasse gebaseerde DSC-resource en een cmdlet DSC-resourceprovider zijn:

* Een MOF-bestand voor het schema is niet vereist.
* Een **DSCResource** submap in de modulemap is niet vereist.
* Een PowerShell-module-bestand kan meerdere DSC-resource klassen bevatten.

Zie voor meer informatie [schrijven van een aangepaste DSC-resource met PowerShell klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).

