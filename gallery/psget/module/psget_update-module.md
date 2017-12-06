---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Update-Module
ms.openlocfilehash: 66535cd5b1f44e108c2bc47fa343c77c86bb21dc
ms.sourcegitcommit: 58371abe9db4b9a0e4e1eb82d39a9f9e187355f9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2017
---
# <a name="update-module"></a>Update-Module

Downloadt en installeert de nieuwste versie van de opgegeven modules vanuit een online-galerie op de lokale computer.

## <a name="description"></a>Beschrijving

De cmdlet Update-Module installeert een nieuwere versie van een Windows PowerShell-module die is geïnstalleerd vanaf de on line galerie door het uitvoeren van Install-Module op de lokale computer.

De nieuwste versie van de opgegeven module in online galerie is standaard geïnstalleerd, tenzij u een vereiste versie opgeeft. U kunt een bestaande, geïnstalleerde module bijwerken door op te geven van de naam van de module. Update-Module zoekt $env: PSModulePath voor de module die u wilt bijwerken.

Update-Module uitgevoerd zonder de parameter Name updates alle modules weer die kunnen worden bijgewerkt op de lokale computer.

### <a name="notes"></a>Opmerkingen

- Deze cmdlet wordt uitgevoerd op Windows PowerShell 3.0 of latere versies van Windows PowerShell op Windows 7 of Windows 2008 R2 en latere versies van Windows.
- Als de module die u met de parameter Name opgeeft niet met behulp van Install-Module is geïnstalleerd, wordt er een fout optreedt. U kunt de Update-Module alleen uitvoeren op de modules die u hebt geïnstalleerd vanuit de on line galerie door het uitvoeren van de installatie-Module.
- Als de Update-Module probeert bij te werken van de binaire bestanden die gebruikt worden, foutmelding Update-Module een die identificeert de processen van het probleem en wordt de gebruiker om opnieuw te proberen Update-Module na het stoppen van de processen geïnformeerd.
- In PowerShell 5.0 of nieuwere versies, wanneer een module-Update-Module updates worden toegevoegd de meest recente (of opgegeven) versie van de module zodat de oudere en nieuwere versies nu side-by-side in dezelfde map zijn. Het normaal zou zijn handig om te zeggen dat en om een voorbeeld van de uitvoer van deze opdrachten weer te geven.


## <a name="cmdlet-syntax"></a>De syntaxis van cmdlet
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Verwijzing naar het online help van cmdlet

[Update-Module](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a>Voorbeeldopdrachten

```powershell
PS C:\windows\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\windows\system32> Update-Module -Name ContosoServer
PS C:\windows\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\ContosoServer\1.0
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```

### <a name="update-the-module-with-a-prerelease-version-requires--allowprerelease-flag"></a>Bijwerken van de module met een prerelease-versie, vlag - AllowPrerelease vereist
```powershell
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module

PS C:\windows\system32> Find-Module ContosoServer -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
3.0.0-alpha    ConstosoServer                      MSPSGallery          The PowerShell Contoso Server deployment tools...

PS C:\windows\system32> Update-Module -Name ContosoServer -AllowPrerelease
PS C:\windows\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
3.0.0-alpha ContosoServer MSPSGallery ContosoServer module

```


### <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a>De module TestDepWithNestedRequiredModules1 bijwerken met afhankelijkheden.
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module



```

