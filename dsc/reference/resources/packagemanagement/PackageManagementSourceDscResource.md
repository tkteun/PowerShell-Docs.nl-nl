---
ms.date: 09/20/2019
keywords: DSC, Power shell, configuratie, installatie
title: DSC PackageManagementSource-resource
ms.openlocfilehash: 20b7851e44751d4bd0add718d2f7294d5215ab70
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324575"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC PackageManagementSource-resource

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5. x

De **PackageManagementSource** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het registreren of ongedaan maken van de registratie van pakket beheer bronnen op een doel knooppunt.
**Pakket beheer bronnen die op deze manier zijn geregistreerd, worden geregistreerd in de systeem context, die bruikbaar is voor het systeem account of de DSC-engine.** Deze bron vereist de module **Package Management** , die beschikbaar is via de [PowerShell Gallery](https://PowerShellGallery.com).

> [!IMPORTANT]
> De **Package Management** -module moet ten minste versie 1.1.7.0 zijn voor de volgende eigenschaps gegevens die u wilt corrigeren.

## <a name="syntax"></a>Syntaxis

```Syntax
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [ InstallationPolicy = [string]{ Trusted | Untrusted } ]
    [ SourceCredential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>properties

|Eigenschap |Description |
|---|---|
|Name |Hiermee geeft u de naam van de pakket bron moet worden geregistreerd of niet geregistreerd op uw systeem. |
|ProviderName |Hiermee geeft u de naam van de OneGet-provider op waarmee u interop met de pakket bron kunt doen. |
|SourceLocation |Hiermee geeft u de URI van de pakket bron. |
|InstallationPolicy |Wordt gebruikt door providers zoals de ingebouwde Nuget-provider. Hiermee wordt bepaald of u de bron van het pakket vertrouwt. Een van de volgende opties: **Niet-vertrouwd** of **vertrouwd**. |
|SourceCredential |Biedt toegang tot het pakket op een externe bron. |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Description |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`bijvoorbeeld als de id van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is. |
|Zo |Hiermee wordt bepaald of de bron van het pakket moet worden geregistreerd of verwijderd. De standaard waarde is **aanwezig**. |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In dit voor beeld `https://nuget.org` wordt de pakket bron geregistreerd met behulp van de DSC-resource **PackageManagementSource** .

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "https://api.nuget.org/api/v3/"
        InstallationPolicy ="Trusted"
    }
}
```