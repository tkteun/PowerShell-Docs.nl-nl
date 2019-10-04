---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Een specifieke versie van een geïnstalleerde resource importeren
ms.openlocfilehash: 5ed81e11aa67eb6590d958647f48a33b1b5f1c0e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941969"
---
# <a name="import-a-specific-version-of-an-installed-resource"></a>Een specifieke versie van een geïnstalleerde resource importeren

> Van toepassing op: Windows Power shell 5,0

In Power shell 5,0 kunnen afzonderlijke versies van DSC-resources worden geïnstalleerd op een computer naast elkaar. Een resource module kan afzonderlijke versies van een bron opslaan in versie mappen met de naam.

## <a name="installing-separate-resource-versions-side-by-side"></a>Afzonderlijke resource versies naast elkaar installeren

U kunt de para meters **MinimumVersion**, **MaximumVersion**en **RequiredVersion** van de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) gebruiken om op te geven welke versie van een module moet worden geïnstalleerd. Als u **install-module** aanroept zonder een versie op te geven, wordt de meest recente versie geïnstalleerd.

Er zijn bijvoorbeeld meerdere versies van de **xFailOverCluster** -module, die elk een **xCluster** -resource bevatten. Als u **install-module** aanroept zonder het versie nummer op te geven, wordt de meest recente versie van de module geïnstalleerd.

```powershell
PS> Install-Module xFailOverCluster
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, ...
```

Als u een specifieke versie van een module wilt installeren, geeft u een **RequiredVersion** van 1.1.0.0 op. Hiermee wordt de opgegeven versie naast de geïnstalleerde versie geïnstalleerd.

```powershell
PS> Install-Module xFailOverCluster -RequiredVersion 1.1
```

Nu ziet u beide versies van de module die wordt weer gegeven wanneer u `Get-DSCResource` gebruikt.

```powershell
PS> Get-DscResource xCluster
```

```output
ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      xCluster                  xFailOverCluster               1.1        {DomainAdministratorCredential, Name, ...
PowerShell      xCluster                  xFailOverCluster               1.2.0.0    {DomainAdministratorCredential, Name, ...
```

## <a name="specifying-a-resource-version-in-a-configuration"></a>Een bron versie opgeven in een configuratie

Als er afzonderlijke resource versies op een computer zijn geïnstalleerd, moet u de versie van die bron opgeven wanneer u deze in een configuratie gebruikt. U doet dit door de para meter **ModuleVersion** van het sleutel woord **import-dscresource bieden** op te geven. Als u de versie van een resource module niet opgeeft van een resource waarvan u meer dan één versie hebt geïnstalleerd, genereert de configuratie een fout.

In de volgende configuratie ziet u hoe u de versie van de te kiezen resource opgeeft:

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

>Opmerking: De ModuleVersion-para meter van import-Dscresource bieden is niet beschikbaar in Power Shell 4,0. In Power Shell 4,0 kunt u een module versie opgeven door een module specificatie object door te geven aan de para meter module van import-Dscresource bieden. Een module-specificatie object is een hash-tabel die module-en RequiredVersion-sleutels bevat. Bijvoorbeeld:

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

Dit werkt ook in Power shell 5,0, maar u wordt aangeraden de para meter **ModuleVersion** te gebruiken.

## <a name="see-also"></a>Zie ook

- [DSC-configuraties](configurations.md)
- [DSC-resources](../resources/resources.md)
