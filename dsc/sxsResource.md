---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: Resources met meerdere versies gebruiken
ms.openlocfilehash: 6400d6506106657ba28fa1f9c83d9f8ee1c93ba3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34187007"
---
# <a name="using-resources-with-multiple-versions"></a>Resources met meerdere versies gebruiken

> Van toepassing op: Windows PowerShell 5.0

In PowerShell 5.0 DSC-resources mogelijk meerdere versies en versies kunnen worden geïnstalleerd op een computer naast elkaar. Dit wordt geïmplementeerd door meerdere versies van een resource-module die zijn opgenomen in dezelfde modulemap.

## <a name="installing-multiple-resource-versions-side-by-side"></a>Installeren van meerdere resources versies side-by-side

U kunt de **MinimumVersion**, **MaximumVersion**, en **RequiredVersion** parameters van de [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet om op te geven welke versie van een module te installeren. Het aanroepen van **Install-Module** zonder op te geven met een versie installeert de meest recente versie.

Bijvoorbeeld: Er zijn meerdere versies van de **xFailOverCluster** -module, die een **xCluster** bron. Het resultaat van aanroepen **Install-Module** zonder op te geven van de versie nummer ziet er als volgt:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Als u nu **Install-Module** opnieuw, maar Geef een **RequiredVersion** van 1.1.0.0, resulteert dit in de volgende:

```powershell
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Install-Module xFailOverCluster -RequiredVersion 1.1
C:\Program Files\WindowsPowerShell\Modules\xFailOverCluster> Get-DscResource xCluster

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Een resourceversie opgeven in een configuratie

Als u meerdere resources die zijn geïnstalleerd op een computer hebt, moet u de versie van de bron opgeven wanneer u deze in een configuratie gebruikt. U doet dit door geven de **ModuleVersion** parameter van de **importeren DscResource** sleutelwoord. Als u niet de versie van een resource-module van een resource die u meer dan één versie geïnstalleerd hebt, wordt er een fout gegenereerd in de configuratie.

De volgende configuratie ziet u hoe de versie van de bron aan te roepen:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName xFailOverCluster -ModuleVersion 1.1

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

>Opmerking: De parameter ModuleVersion van importeren DscResource is niet beschikbaar in PowerShell 4.0. In PowerShell 4.0, kunt u een moduleversie door een module specificatie-object doorgegeven aan de parameter ModuleName van importeren DscResource opgeven. Een module-specificatie van het object is een hashtabel met ModuleName en RequiredVersion sleutels. Bijvoorbeeld:

```powershell
configuration VersionTest
{
    Import-DscResource -ModuleName (@{ModuleName='xFailOverCluster'; RequiredVersion='1.1'} )

    Node 'localhost'
    {
       xCluster ClusterTest
       {
            Name                          = 'TestCluster'
            StaticIPAddress               = '10.0.0.3'
            DomainAdministratorCredential = Get-Credential
        }
     }
}
```

Dit werkt ook in PowerShell 5.0, maar het is raadzaam dat u de **ModuleVersion** parameter.

## <a name="see-also"></a>Zie ook
* [DSC-configuraties](configurations.md)
* [DSC-Resources](resources.md)