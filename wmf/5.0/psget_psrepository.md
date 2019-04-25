---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058009"
---
# <a name="register-a-powershell-repository"></a>Een PowerShell-opslagplaats registreren
PowerShellGet tegen interne opslagplaatsen werken, kunt u configureren. Dit wordt gedaan met behulp van de volgende toevoegingen:
- Register-PSRepository: Registreert een opslagplaats voor de huidige gebruiker.
- De registratie ongedaan maken-PSRepository: Hiermee verwijdert u een geregistreerde opslagplaats voor de huidige gebruiker.
- Set-PSRepository: Waarden voor een geregistreerde opslagplaats instellen.
- Get-PSRepository: Alle geregistreerde opslagplaatsen voor de huidige gebruiker ophalen.

Nadat een opslagplaats is geregistreerd, kunt u Find-Module en Install-Module gebruiken om hiermee te werken.

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
