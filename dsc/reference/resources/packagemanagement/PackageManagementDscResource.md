---
ms.date: 06/20/2018
keywords: DSC, powershell, configuratie en installatie
title: DSC-Package Management-Resource
ms.openlocfilehash: 18cbbfe0715c82dcfdf4a5fb6ee36ee814e43d3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686864"
---
# <a name="dsc-packagemanagement-resource"></a>DSC-Package Management-Resource

Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

De **PackageManagement** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te installeren of verwijderen van Package Management-pakketten op een doelknooppunt. Deze resource is vereist de **PackageManagement** -module, beschikbaar is via [ http://PowerShellGallery.com ](http://PowerShellGallery.com).

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

| Eigenschap | Beschrijving |
| --- | --- |
| Naam| Hiermee geeft u de naam van het pakket dat moet worden geïnstalleerd of verwijderd.|
| AdditionalParameters| Specifieke hashtabel van de provider van de parameters die worden doorgegeven aan `Get-Package -AdditionalArguments`. Bijvoorbeeld, kunt u aanvullende parameters, zoals het doelpad doorgeven voor NuGet-provider.|
| Zorg ervoor dat| Bepaalt of het pakket moet worden geïnstalleerd of verwijderd.|
| MaximumVersion|Hiermee geeft u de maximaal toegestane versie van het pakket dat u wilt zoeken. Als u deze parameter niet toevoegt, zoekt de resource is de hoogste versie van het pakket.|
| MinimumVersion|Hiermee geeft u de minimaal toegestane versie van het pakket dat u wilt zoeken. Als u deze parameter niet toevoegt, de bron zoekt naar de hoogste versie van het pakket dat ook voldoet aan alle maximale opgegeven versie van het opgegeven door de _MaximumVersion_ parameter.|
| ProviderName| Hiermee geeft u de naam van een pakket provider waarnaar u wilt uw zoekopdracht pakket beperken. Krijgt u provider-pakketnamen door het uitvoeren van de `Get-PackageProvider` cmdlet.|
| RequiredVersion| Hiermee geeft u de exacte versie van het pakket dat u wilt installeren. Als u deze parameter niet opgeeft, deze DSC-resource wordt geïnstalleerd voor de nieuwste beschikbare versie van het pakket dat ook voldoet aan een maximale versie van het opgegeven door de _MaximumVersion_ parameter.|
| Bron| Hiermee geeft u de naam van de pakketbron waar het pakket kan worden gevonden. Dit kan een URI of een bron die is geregistreerd bij `Register-PackageSource` of PackageManagementSource DSC-resource.|
| SourceCredential | Hiermee geeft u een gebruikersaccount met rechten voor het installeren van een pakket voor een opgegeven pakket-provider of de bron.|

## <a name="additional-parameters"></a>Extra Parameters

De volgende tabel bevat opties voor de eigenschap AdditionalParameters.

| Parameter | Beschrijving |
| --- | --- |
| DestinationPath| Gebruikt door providers, zoals de geïntegreerde Nuget-Provider. Hiermee geeft u een locatie waar u het pakket dat moet worden geïnstalleerd.|
| InstallationPolicy| Gebruikt door providers, zoals de geïntegreerde Nuget-Provider. Hiermee bepaalt u of u het pakket met de bron vertrouwt. Een van: `Untrusted`, `Trusted`.|

## <a name="example"></a>Voorbeeld

In dit voorbeeld installeert de **JQuery** NuGet-pakket en **GistProvider** PowerShell module met behulp van de **PackageManagement** DSC-resource. In dit voorbeeld eerst zorgt ervoor dat de bronnen vereist pakket beschikbaar zijn en vervolgens definieert de verwachte status van de **JQuery** en **GistProvider** pakketten (NuGet en PowerShell, respectievelijk).

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