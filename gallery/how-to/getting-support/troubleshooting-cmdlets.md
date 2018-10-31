---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Cmdlets voor het oplossen van problemen
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002459"
---
# <a name="troubleshooting-cmdlets"></a>Cmdlets voor het oplossen van problemen

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a>Over het oplossen van ' Waarschuwing: kan het pakket 'uw pakket name' niet downloaden "probleem

Dit apparaat gerapporteerd die `Install-Module` of `Update-Module` soms op sommige computers mislukt.
Op basis van ons onderzoek, is het iets te maken met de netwerkverbinding.
Onlangs bijgewerkt we NuGet-provider zodat deze op betrouwbare wijze pakketten kan downloaden.
U kunt de meest recente versie van NuGet-provider installeren en vervolgens installeren of bijwerken van uw module in onderstaande instructies volgen.
We gaan 'Azure'-module gebruiken als het onderstaande voorbeeld.

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
