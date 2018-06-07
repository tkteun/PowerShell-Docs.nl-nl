---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagement Resource
ms.openlocfilehash: 3d52934b130d59acee4d7f8a92da2c743c1eb305
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753784"
---
# <a name="dsc-packagemanagement-resource"></a>DSC-PackageManagement Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0, 5.1 van Windows PowerShell

De **PackageManagement** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te installeren of verwijderen van pakketten in een doelknooppunt Package Management. Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.

> [!IMPORTANT]
> De **PackageManagement** module moet ten minste versie 1.1.7.0 voor de volgende eigenschapsinformatie juist te zijn.

## <a name="syntax"></a>Syntaxis

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [AdditionalParameters = [HashTable]]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [MaximumVersion = [string]]
    [MinimumVersion = [string]]
    [ProviderName = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [RequiredVersion = [string]]
    [Source = [string]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Eigenschappen

|  Eigenschap  |  Beschrijving   |
|---|---|
| Naam| Hiermee geeft u de naam van het pakket dat moet worden geïnstalleerd of verwijderd.|
| AdditionalParameters| Specifieke hashtabel van de provider van de parameters die worden doorgegeven aan `Get-Package -AdditionalArguments`. U kunt bijvoorbeeld aanvullende parameters zoals doelpad doorgeven voor NuGet-provider.|
| Zorg ervoor dat| Bepaalt of het pakket moet worden geïnstalleerd of verwijderd.|
| MaximumVersion|Hiermee geeft u de maximaal toegestane versie van het pakket dat u wilt zoeken. Als u deze parameter niet toevoegt, wordt de hoogste versie van het pakket gevonden in de resource.|
| MinimumVersion|Hiermee geeft u de minimaal toegestane versie van het pakket dat u wilt zoeken. Als u deze parameter niet toevoegt, de bron zoekt de hoogste versie van het pakket dat ook voldoet aan alle opgegeven maximumversie opgegeven door de _MaximumVersion_ parameter.|
| ProviderName| Hiermee geeft u een providernaam pakket waarnaar als bereik voor uw zoekopdracht pakket. U kunt providernamen pakket ophalen door het uitvoeren van de `Get-PackageProvider` cmdlet.|
| RequiredVersion| Hiermee geeft u de exacte versie van het pakket dat u wilt installeren. Als u deze parameter niet opgeeft, deze DSC-resource worden geïnstalleerd voor de nieuwste versie van het pakket dat ook voldoet aan alle maximale versie van het opgegeven door de _MaximumVersion_ parameter.|
| Bron| Hiermee geeft u de naam van de pakketbron waar het pakket kan worden gevonden. Dit kan een URI of een bron die is geregistreerd bij `Register-PackageSource` of PackageManagementSource DSC-resource.|
| SourceCredential | Hiermee geeft u een gebruikersaccount met rechten voor het installeren van een pakket voor een opgegeven pakket-provider of de bron.|

## <a name="additional-parameters"></a>Extra Parameters

De volgende tabel geeft een lijst met opties voor de eigenschap AdditionalParameters.
|  Parameter  | Beschrijving   |
|---|---|
| DestinationPath| Gebruikt door providers zoals de ingebouwde Nuget-Provider. Hiermee geeft u een locatie waar u het pakket worden geïnstalleerd.|
| InstallationPolicy| Gebruikt door providers zoals de ingebouwde Nuget-Provider. Hiermee bepaalt u of u het pakket bron vertrouwt. Een van: 'Niet vertrouwd', 'Vertrouwd'.|

## <a name="example"></a>Voorbeeld

Dit voorbeeld installeert de **JQuery** NuGet-pakket en **GistProvider** PowerShell module met behulp van de **PackageManagement** DSC-resource. In dit voorbeeld eerst zorgt ervoor dat de vereiste pakket bronnen beschikbaar zijn en vervolgens definieert de verwachte status van de **JQuery** en **GistProvider** pakketten (NuGet en PowerShell, respectievelijk).

```powershell
Configuration PackageTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagementSource PSGallery
    {
        Ensure      = "Present"
        Name        = "psgallery"
        ProviderName= "PowerShellGet"
        SourceLocation   = "https://www.powershellgallery.com/api/v2/"
        InstallationPolicy ="Trusted"
    }

    PackageManagement NugetPackage
    {
        Ensure               = "Present"
        Name                 = "JQuery"
        AdditionalParameters = "$env:HomeDrive\nuget"
        RequiredVersion      = "2.0.1"
        DependsOn            = "[PackageManagementSource]SourceRepository"
    }

    PackageManagement PSModule
    {
        Ensure               = "Present"
        Name                 = "gistprovider"
        Source               = "PSGallery"
        DependsOn            = "[PackageManagementSource]PSGallery"
    }
}
```