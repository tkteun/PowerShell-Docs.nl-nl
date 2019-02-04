---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 5ac9566979e1b761249f5cc7c62ed44047a2b9f6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685233"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="25dcd-102">Een PowerShell-opslagplaats registreren</span><span class="sxs-lookup"><span data-stu-id="25dcd-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="25dcd-103">PowerShellGet tegen interne opslagplaatsen werken, kunt u configureren.</span><span class="sxs-lookup"><span data-stu-id="25dcd-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="25dcd-104">Dit wordt gedaan met behulp van de volgende toevoegingen:</span><span class="sxs-lookup"><span data-stu-id="25dcd-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="25dcd-105">Register-PSRepository: Registreert een opslagplaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="25dcd-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="25dcd-106">De registratie ongedaan maken-PSRepository: Hiermee verwijdert u een geregistreerde opslagplaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="25dcd-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="25dcd-107">Set-PSRepository: Waarden voor een geregistreerde opslagplaats instellen.</span><span class="sxs-lookup"><span data-stu-id="25dcd-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="25dcd-108">Get-PSRepository: Alle geregistreerde opslagplaatsen voor de huidige gebruiker ophalen.</span><span class="sxs-lookup"><span data-stu-id="25dcd-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="25dcd-109">Nadat een opslagplaats is geregistreerd, kunt u Find-Module en Install-Module gebruiken om hiermee te werken.</span><span class="sxs-lookup"><span data-stu-id="25dcd-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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
