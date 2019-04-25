---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 28f4f8ae2bbddc8fb5ef9d95d3061a91fcc8ffe2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058723"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="73ebb-102">Toestaan van identieke dubbele Resources in een configuratie</span><span class="sxs-lookup"><span data-stu-id="73ebb-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="73ebb-103">DSC niet toestaan of conflicterende resourcedefinities binnen een configuratie worden verwerkt.</span><span class="sxs-lookup"><span data-stu-id="73ebb-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="73ebb-104">In plaats van het conflict op te lossen, gewoon is mislukt.</span><span class="sxs-lookup"><span data-stu-id="73ebb-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="73ebb-105">Als het hergebruik van de configuratie wordt meer samengestelde resources gebruikt, wordt vaker enzovoort conflicten optreden.</span><span class="sxs-lookup"><span data-stu-id="73ebb-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="73ebb-106">Wanneer er conflicterende resourcedefinities identiek zijn, moet de DSC Wees slim en dit toestaan.</span><span class="sxs-lookup"><span data-stu-id="73ebb-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="73ebb-107">Met deze versie wordt ondersteund met meerdere exemplaren van resources met identieke definities:</span><span class="sxs-lookup"><span data-stu-id="73ebb-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="73ebb-108">In eerdere versies is het resultaat een compilatie is mislukt vanwege een conflict tussen de WindowsFeature FE_IIS en WindowsFeature Worker_IIS exemplaren probeert om te controleren of de rol 'Webserver' is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="73ebb-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="73ebb-109">U ziet dat *alle* zijn identiek in deze twee configuraties van de eigenschappen die worden geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="73ebb-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="73ebb-110">Aangezien *alle* van de eigenschappen in deze twee resources identiek zijn, resulteert dit in een geslaagde compilatie nu.</span><span class="sxs-lookup"><span data-stu-id="73ebb-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="73ebb-111">Als een van de eigenschappen van de verschillen tussen de twee resources, ze komen niet in aanmerking identiek zijn en compilatie mislukt:</span><span class="sxs-lookup"><span data-stu-id="73ebb-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="73ebb-112">Deze configuratie is vergelijkbaar mislukken omdat de FE_IIS WindowsFeature en de resources WindowsFeature Worker_IIS daarom in strijd niet langer identiek zijn zijn.</span><span class="sxs-lookup"><span data-stu-id="73ebb-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>
