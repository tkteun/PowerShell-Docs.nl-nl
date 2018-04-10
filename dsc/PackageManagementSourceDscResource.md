---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagementSource Resource
ms.openlocfilehash: 8c0cb5a3b0a019ddb5ed995406f499298103b07c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC-PackageManagementSource Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te registreren of de registratie van gegevensbronnen in een doelknooppunt Package Management. **Pakket Management bronnen geregistreerd op deze manier zijn geregistreerd met de systeemcontext, kan worden gebruikt door het systeem-account of door de DSC-engine.** Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.

## <a name="syntax"></a>Syntaxis

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Hiermee geeft u de naam van de pakketbron om te worden ingeschreven of niet geregistreerd op uw systeem.|
| Zorg ervoor dat| Hiermee wordt bepaald of de pakketbron worden geregistreerd of de registratie is verwijderd.|
| InstallationPolicy| Hiermee bepaalt u of u de pakketbron vertrouwt. Een van: 'Niet vertrouwd', 'Vertrouwd'.|
| ProviderName| Hiermee geeft u de naam van de OneGet provider waarmee u interop met de pakketbron kunt.|
| SourceUri| Hiermee geeft u de URI van de pakketbron.|
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
        SourceUri   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```