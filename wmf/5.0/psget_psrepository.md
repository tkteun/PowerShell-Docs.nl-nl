---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installeren
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a>Een PowerShell-opslagplaats registreren
U kunt PowerShellGet interne opslagplaatsen kunnen configureren. Dit wordt gedaan met behulp van de volgende toevoegingen:
- Register-PSRepository: Registreert een opslagplaats voor de huidige gebruiker.
- Registratie-PSRepository: Hiermee verwijdert u een geregistreerde opslagplaats voor de huidige gebruiker.
- Set-PSRepository: Waarden voor een geregistreerde-opslagplaats instellen.
- Get-PSRepository: Alle geregistreerde opslagplaatsen voor de huidige gebruiker niet ophalen.

Nadat een opslagplaats is geregistreerd, kunt u zoeken-Module en installatie-Module om hiermee te werken.

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```