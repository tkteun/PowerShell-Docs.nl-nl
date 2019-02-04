---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685632"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Side-By-Side-Module-ondersteuning voor versiebeheer voor DSC-Resources

Modules met DSC-resources kunnen worden geïnstalleerd side-by-side en DSC-configuraties kunt een specifieke versie van de resource die is geïnstalleerd op het systeem.

Zie voor meer informatie, [resources met meerdere versies gebruiken](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Bekende problemen

In deze release volgen de volgende bekende problemen van side-by-side-installatie:

-   Met behulp van twee verschillende versies van de DSC-resource binnen dezelfde configuratie wordt niet ondersteund.
