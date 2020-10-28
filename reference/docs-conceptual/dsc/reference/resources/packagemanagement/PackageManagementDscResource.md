---
ms.date: 07/15/2020
ms.topic: reference
title: DSC Package Management-resource
description: DSC Package Management-resource
ms.openlocfilehash: b6676860acea094e04479e38f29ee7c72430851b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667365"
---
# <a name="dsc-packagemanagement-resource"></a>DSC Package Management-resource

Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0, Windows Power shell 5,1

De **Package Management** -resource in Windows Power shell desired state Configuration (DSC) biedt een mechanisme voor het installeren of verwijderen van pakket beheer pakketten op een doel knooppunt. Deze bron vereist de module **Package Management** , die beschikbaar is via [https://PowerShellGallery.com](https://PowerShellGallery.com) .

> [!IMPORTANT]
> De **Package Management** -module moet ten minste versie 1.1.7.0 zijn voor de volgende eigenschaps gegevens die u wilt corrigeren.

## <a name="syntax"></a>Syntax

```Syntax
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ AdditionalParameters = [HashTable] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string]{ Absent | Present } ]
    [ MaximumVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ ProviderName = [string] ]
    [ PsDscRunAsCredential = [PSCredential] ]
    [ RequiredVersion = [string] ]
    [ Source = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|Naam |Hiermee geeft u de naam op van het pakket dat moet worden geïnstalleerd of verwijderd. |
|AdditionalParameters |Providerspecifieke hashtabel van para meters die worden door gegeven aan `Get-Package -AdditionalArguments` . U kunt bijvoorbeeld voor NuGet-provider aanvullende para meters door geven zoals doelpad. |
|MaximumVersion |Hiermee geeft u de Maxi maal toegestane versie van het pakket dat u wilt zoeken. Als u deze para meter niet toevoegt, vindt de resource de hoogste beschik bare versie van het pakket. |
|MinimumVersion |Hiermee geeft u de mini maal toegestane versie van het pakket dat u wilt zoeken. Als u deze para meter niet toevoegt, zoekt de resource de hoogste beschik bare versie van het pakket die ook voldoet aan de maximum opgegeven versie die is opgegeven door de para meter **MaximumVersion** . |
|ProviderName |Hiermee geeft u de naam van een pakket provider op waarmee u de pakket zoekopdracht wilt bereiken. U kunt pakket provider namen ophalen door de cmdlet uit te voeren `Get-PackageProvider` . |
|RequiredVersion |Hiermee geeft u de exacte versie van het pakket op dat u wilt installeren. Als u deze para meter niet opgeeft, installeert deze DSC-resource de nieuwste beschik bare versie van het pakket die ook voldoet aan de maximum versie die is opgegeven door de para meter **MaximumVersion** . |
|Bron |Hiermee geeft u de naam van de pakket bron op waarin het pakket kan worden gevonden. Dit kan een URI zijn of een bron die is geregistreerd bij `Register-PackageSource` of PACKAGEMANAGEMENTSOURCE DSC-resource. |
|SourceCredential |Hiermee geeft u een gebruikers account op dat rechten heeft om een pakket te installeren voor een opgegeven pakket provider of bron. |

## <a name="additional-parameters"></a>Aanvullende para meters

De volgende tabel bevat de opties voor de eigenschap AdditionalParameters.

|Parameter |Beschrijving |
|---|---|
|DestinationPath |Wordt gebruikt door providers zoals de ingebouwde Nuget-provider. Hiermee geeft u een bestands locatie op waar het pakket moet worden geïnstalleerd. |
|InstallationPolicy |Wordt gebruikt door providers zoals de ingebouwde Nuget-provider. Hiermee wordt bepaald of u de bron van het pakket vertrouwt. Een van: **niet-vertrouwd** of **vertrouwd** . |

## <a name="common-properties"></a>Algemene eigenschappen

|Eigenschap |Beschrijving |
|---|---|
|DependsOn |Geeft aan dat de configuratie van een andere bron moet worden uitgevoerd voordat deze resource wordt geconfigureerd. De syntaxis voor het gebruik van deze eigenschap is bijvoorbeeld als de ID van het resource-script blok dat u als eerste wilt uitvoeren, de naam ResourceName is en het type van de bron resource is `DependsOn = "[ResourceType]ResourceName"` . |
|Zo |Hiermee wordt bepaald of het pakket moet worden geïnstalleerd of verwijderd. De standaard waarde is **aanwezig** . |
|PsDscRunAsCredential |Hiermee stelt u de referentie in voor het uitvoeren van de gehele resource als. |

> [!NOTE]
> De algemene eigenschap **PsDscRunAsCredential** is toegevoegd aan WMF 5,0 om het uitvoeren van een DSC-resource in de context van andere referenties toe te staan. Zie [referenties gebruiken met DSC-resources](../../../configurations/runasuser.md)voor meer informatie.

## <a name="example"></a>Voorbeeld

In dit voor beeld wordt het **jQuery** NuGet-pakket en de **GistProvider** Power shell-module geïnstalleerd met behulp van de **Package Management** DSC-resource. In dit voor beeld wordt eerst gegarandeerd dat de vereiste pakket bronnen beschikbaar zijn en definieert vervolgens de verwachte status van de **jQuery** -en **GistProvider** -pakketten (respectievelijk NuGet en Power shell).

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
        SourceLocation   = "https://www.powershellgallery.com/api/v2"
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
