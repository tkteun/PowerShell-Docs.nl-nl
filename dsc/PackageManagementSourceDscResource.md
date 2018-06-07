---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagementSource Resource
ms.openlocfilehash: 5d049b05c387cafe27edb202d569852b10852dce
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753767"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC-PackageManagementSource Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 van Windows PowerShell

De **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te registreren of de registratie van gegevensbronnen in een doelknooppunt Package Management. **Pakket Management bronnen geregistreerd op deze manier zijn geregistreerd met de systeemcontext, kan worden gebruikt door het systeem-account of door de DSC-engine.** Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.

> [!IMPORTANT]
> De **PackageManagement** module moet ten minste versie 1.1.7.0 voor de volgende eigenschapsinformatie juist te zijn.

## <a name="syntax"></a>Syntaxis

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Hiermee geeft u de naam van de pakketbron om te worden ingeschreven of niet geregistreerd op uw systeem.|
| ProviderName| Hiermee geeft u de naam van de OneGet provider waarmee u interop met de pakketbron kunt.|
| SourceLocation| Hiermee geeft u de URI van de pakketbron.|
| Zorg ervoor dat| Hiermee wordt bepaald of de pakketbron worden geregistreerd of de registratie is verwijderd.|
| InstallationPolicy| Gebruikt door providers zoals de ingebouwde Nuget-Provider. Hiermee bepaalt u of u het pakket bron vertrouwt. Een van: 'Niet vertrouwd', 'Vertrouwd'.|
| SourceCredential| Biedt toegang tot het pakket op een externe bron.|

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt de http://nuget.org pakket bron met behulp van de **PackageManagementSource** DSC-resource.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```