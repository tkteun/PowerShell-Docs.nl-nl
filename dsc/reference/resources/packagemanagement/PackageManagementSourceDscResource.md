---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC PackageManagementSource Resource
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048175"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0 en Windows PowerShell 5.1

De **PackageManagementSource** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te registreren of de registratie van Package Management bronnen op een doelknooppunt. **Management-pakketbronnen geregistreerd op deze manier worden geregistreerd in de systeemcontext, kan worden gebruikt door het systeem-account of de DSC-engine.** Deze resource is vereist de **PackageManagement** -module, beschikbaar is via http://PowerShellGallery.com.

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
| ProviderName| Hiermee geeft u de naam van de OneGet-provider waarmee u goed werken met de pakketbron kunt.|
| SourceLocation| Hiermee geeft u de URI van de pakketbron.|
| Zorg ervoor dat| Bepaalt of de pakketbron om te worden ingeschreven of niet-geregistreerde.|
| InstallationPolicy| Gebruikt door providers, zoals de geïntegreerde Nuget-Provider. Hiermee bepaalt u of u het pakket met de bron vertrouwt. Een van: 'Niet-vertrouwd', vertrouwd' '.|
| SourceCredential| Biedt toegang tot het pakket op een externe bron.|

## <a name="example"></a>Voorbeeld

In dit voorbeeld wordt de http://nuget.org pakket gegevensbron via de **PackageManagementSource** DSC-resource.

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