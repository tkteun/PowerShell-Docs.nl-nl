---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: DSC-PackageManagement Resource
ms.openlocfilehash: a984fbf5db561a696d89b60dde8b92096c6e4924
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagement-resource"></a>DSC-PackageManagement Resource

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De **PackageManagement** in Windows PowerShell Desired State Configuration (DSC)-bron biedt een mechanisme om te installeren of verwijderen van pakketten in een doelknooppunt Package Management. Deze resource vereist de **PackageManagement** module beschikbaar is via http://PowerShellGallery.com.

## <a name="syntax"></a>Syntaxis

```
PackageManagement [string] #ResourceName
{
    Name = [string]
    [ Source = [string] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ RequiredVersion = [string] ]
    [ MinimumVersion = [string] ]
    [ MaximumVersion = [string] ]
    [ SourceCredential = [PSCredential] ]
    [ ProviderName = [string] ]
    [ AdditionalParameters = [Microsoft.Management.Infrastructure.CimInstance[]] ]
}
```

## <a name="properties"></a>Eigenschappen
|  Eigenschap  |  Beschrijving   | 
|---|---| 
| Naam| Hiermee geeft u de naam van het pakket dat moet worden geïnstalleerd of verwijderd.| 
| Bron| Hiermee geeft u de naam van de pakketbron waar het pakket kan worden gevonden. Dit kan een URI of een bron die is geregistreerd bij registreren PackageSource of PackageManagementSource DSC-resource. De DSC-resource MSFT_PackageManagementSource kunt ook een pakketbron registreren.| 
| Zorg ervoor dat| Bepaalt of het pakket moet worden geïnstalleerd of verwijderd.| 
| RequiredVersion| Hiermee geeft u de exacte versie van het pakket dat u wilt installeren. Als u deze parameter niet opgeeft, wordt de nieuwste versie van het pakket dat ook voldoet aan alle maximale versie van het opgegeven met de parameter MaximumVersion geïnstalleerd in deze DSC-resource.| 
| MinimumVersion| Hiermee geeft u de minimaal toegestane versie van het pakket dat u wilt installeren. Als u deze parameter niet toevoegt, wordt deze DSC-resource intalls de hoogste versie van het pakket dat ook voldoet aan alle maximale versie van het opgegeven opgegeven door de parameter MaximumVersion.| 
| MaximumVersion| Hiermee geeft u de maximaal toegestane versie van het pakket dat u wilt installeren. Als u deze parameter niet opgeeft, installeert deze DSC-resource de hoogste nummer beschikbare versie van het pakket.| 
| SourceCredential | Hiermee geeft u een gebruikersaccount met rechten voor het installeren van een pakket voor een opgegeven pakket-provider of de bron.| 
| ProviderName| Hiermee geeft u een providernaam pakket waarnaar als bereik voor uw zoekopdracht pakket. U kunt providernamen pakket ophalen door de cmdlet Get-PackageProvider.| 
| AdditionalParameters| Provider specifieke parameters die worden doorgegeven als een hashtabel. U kunt bijvoorbeeld aanvullende parameters zoals doelpad doorgeven voor NuGet-provider.| 

## <a name="additional-parameters"></a>Extra Parameters
De volgende tabel geeft een lijst met opties voor de eigenschap AdditionalParameters.
|  Parameter  | Beschrijving   | 
|---|---|
| Doelpad| Gebruikt door providers zoals de ingebouwde Nuget-Provider. Hiermee geeft u een locatie waar u het pakket worden geïnstalleerd.|
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
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }    
    
    PackageManagementSource PSGallery 
    { 
        Ensure      = "Present" 
        Name        = "psgallery" 
        ProviderName= "PowerShellGet" 
        SourceUri   = "https://www.powershellgallery.com/api/v2/"   
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

