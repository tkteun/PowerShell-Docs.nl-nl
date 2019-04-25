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
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a>Toestaan van identieke dubbele Resources in een configuratie

DSC niet toestaan of conflicterende resourcedefinities binnen een configuratie worden verwerkt. In plaats van het conflict op te lossen, gewoon is mislukt. Als het hergebruik van de configuratie wordt meer samengestelde resources gebruikt, wordt vaker enzovoort conflicten optreden. Wanneer er conflicterende resourcedefinities identiek zijn, moet de DSC Wees slim en dit toestaan. Met deze versie wordt ondersteund met meerdere exemplaren van resources met identieke definities:

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

In eerdere versies is het resultaat een compilatie is mislukt vanwege een conflict tussen de WindowsFeature FE_IIS en WindowsFeature Worker_IIS exemplaren probeert om te controleren of de rol 'Webserver' is geïnstalleerd. U ziet dat *alle* zijn identiek in deze twee configuraties van de eigenschappen die worden geconfigureerd. Aangezien *alle* van de eigenschappen in deze twee resources identiek zijn, resulteert dit in een geslaagde compilatie nu.

Als een van de eigenschappen van de verschillen tussen de twee resources, ze komen niet in aanmerking identiek zijn en compilatie mislukt:

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

Deze configuratie is vergelijkbaar mislukken omdat de FE_IIS WindowsFeature en de resources WindowsFeature Worker_IIS daarom in strijd niet langer identiek zijn zijn.
