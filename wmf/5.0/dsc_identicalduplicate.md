---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187529"
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Identieke dubbele Resources in een configuratie toestaan

DSC niet toestaan of conflicterende resourcedefinities binnen een configuratie verwerkt. In plaats van het conflict op te lossen, gewoon is mislukt. Als het hergebruik van de configuratie wordt meer door samengestelde bronnen worden gebruikt, wordt vaker enzovoort conflicten optreden. Wanneer u conflicterende resourcedefinities identiek zijn, moet DSC smart en dit toestaan. Met deze release ondersteuning wordt voor meerdere resource-exemplaren die identiek zijn gedefinieerd:

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

In eerdere versies is het resultaat een compilatie is mislukt vanwege een conflict tussen de WindowsFeature FE_IIS en WindowsFeature Worker_IIS exemplaren probeert om te controleren of de rol 'Webserver' is geïnstalleerd. U ziet dat *alle* van de eigenschappen die worden geconfigureerd in deze twee configuraties identiek zijn. Aangezien *alle* van de eigenschappen in deze twee bronnen identiek zijn, resulteert dit in een geslaagde compilatie nu.

Als een van de eigenschappen van verschillen tussen de twee bronnen, worden deze niet gezien identiek en compilatie mislukt:

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

Deze configuratie vergelijkbaar mislukken omdat de WindowsFeature FE_IIS en WindowsFeature Worker_IIS resources niet langer identiek zijn en daarom in strijd.
