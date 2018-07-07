---
ms.date: 06/12/2017
contributor: manikb
keywords: Galerie, powershell, cmdlet, psget
title: Cmdlets voor het oplossen van problemen
ms.openlocfilehash: c0a1fbcafd8c4443dc9d628c54c4c525d9701861
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892471"
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