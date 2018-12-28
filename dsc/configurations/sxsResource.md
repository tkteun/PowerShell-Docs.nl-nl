---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Importeren van een specifieke versie van een geïnstalleerde-resource
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403892"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Importeren van een specifieke versie van een geïnstalleerde-resource

> Van toepassing op: Windows PowerShell 5.0

In PowerShell 5.0, kunnen verschillende versies van DSC-resources worden geïnstalleerd op een computer naast elkaar. Een resource-module kunt u verschillende versies van een resource opslaan in versie met de naam van mappen.

## <a name="installing-separate-resource-versions-side-by-side"></a>Afzonderlijke resource versies naast elkaar installeren

U kunt de **MinimumVersion**, **MaximumVersion**, en **RequiredVersion** parameters van de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet om op te geven welke versie van een module te installeren. Aanroepen van **Install-Module** zonder op te geven een versie installeert de meest recente versie.

Bijvoorbeeld, er zijn meerdere versies van de **xFailOverCluster** -module, die elk bevat een **xCluster** resource. Aanroepen van **Install-Module** zonder de versie op te geven aantal installeert de meest recente versie van de module.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Geef voor het installeren van een specifieke versie van een module, een **RequiredVersion** van 1.1.0.0. Hiermee installeert u de opgegeven versie naast de geïnstalleerde versie.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

U ziet nu zowel versie van de module weergegeven wanneer u `Get-DSCResource`.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Een resourceversie opgeven in een configuratie

Als u afzonderlijke resource-versies die zijn geïnstalleerd op een computer hebt, moet u de versie van die resource opgeven wanneer u deze in een configuratie gebruikt. U dit doen door op te geven de **ModuleVersion** parameter van de **sleutelwoorden Import-dscresource bieden** trefwoord. Als u niet om op te geven van de versie van een resource-module van een resource die u meer dan één versie geïnstalleerd hebt, wordt er een fout gegenereerd in de configuratie.

De volgende configuratie laat zien hoe om op te geven van de versie van de resource om aan te roepen:

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

>Opmerking: De parameter ModuleVersion van sleutelwoorden Import-dscresource bieden is niet beschikbaar in PowerShell 4.0. In PowerShell 4.0, kunt u de versie van een module door een module-specificatie-object doorgeven aan de parameter ModuleName van sleutelwoorden Import-dscresource bieden. Een module-specificatie-object is een hashtabel met sleutels ModuleName en requiredversion aan. Bijvoorbeeld:

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

- [DSC-configuraties](configurations.md)
- [DSC-Resources](../resources/resources.md)
