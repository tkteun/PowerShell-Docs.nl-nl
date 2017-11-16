---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, setup
contributor: jianyunt, quoctruong
title: Verbeteringen in beheer van het pakket in WMF 5.1
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Verbeteringen in beheer van het pakket in WMF 5.1#

## <a name="improvements-in-packagemanagement"></a>Verbeteringen in PackageManagement ##
Hier volgen de fixes die zijn aangebracht in de WMF 5.1: 

### <a name="version-alias"></a>Versie Alias

**Scenario**: als u versie 1.0 en 2.0 van een pakket, P1, dat is geïnstalleerd op uw systeem hebt en u wilt verwijderen, versie 1.0, moet u uitvoeren `Uninstall-Package -Name P1 -Version 1.0` en versie 1.0 worden verwijderd na het uitvoeren van de cmdlet verwacht. Maar het resultaat is dat versie 2.0 wordt verwijderd.  
    
Dit komt doordat de `-Version` parameter is een alias van de `-MinimumVersion` parameter. Wanneer PackageManagement een gekwalificeerde pakket met de minimale versie 1.0 zoekt, wordt de meest recente versie. Dit is verwacht gedrag in normale gevallen omdat zoeken naar dat de meest recente versie is meestal het gewenste resultaat oplevert. Maar deze moet niet van toepassing op de `Uninstall-Package` geval.
    
**Oplossing**: verwijderd `-Version` alias volledig in PackageManagement (ook OneGet) en PowerShellGet. 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Meerdere wordt u gevraagd om het uitvoeren van de bootstrap de NuGet-provider

**Scenario**: bij het uitvoeren van `Find-Module` of `Install-Module` of andere cmdlets PackageManagement op uw computer voor de eerste keer, PackageManagement probeert te bootstrap van de NuGet-provider. Dit gebeurt omdat de provider PowerShellGet ook de NuGet-provider gebruikt voor het downloaden van de PowerShell-modules. PackageManagement wordt vervolgens de gebruiker toestemming voor het installeren van de NuGet-provider. Nadat de gebruiker 'Ja' voor het uitvoeren van de bootstrap selecteert, kunt u de nieuwste versie van de NuGet-provider wordt geïnstalleerd. 
    
Echter, in sommige gevallen wanneer u een oude versie van het NuGet-provider is geïnstalleerd op uw computer hebt soms de oudere versie van het NuGet opgehaald geladen eerst naar de PowerShell-sessie (dat wil zeggen de voorwaarde race in PackageManagement). PowerShellGet vereist echter de latere versie van de NuGet-provider om te werken, zodat PowerShellGet PackageManagement naar bootstrap de NuGet-provider opnieuw wordt gevraagd. Dit resulteert in meerdere wordt u gevraagd om het uitvoeren van de bootstrap de NuGet-provider.

**Oplossing**: In WMF5.1, PackageManagement laadt de meest recente versie van de NuGet-provider om te voorkomen dat meerdere wordt u gevraagd om het uitvoeren van de bootstrap de NuGet-provider.

U kunt ook omzeilen dit probleem door de oude versie van de NuGet-provider (NuGet-Anycpu.exe) handmatig te verwijderen als bestaat uit $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Ondersteuning voor PackageManagement op computers met alleen toegang tot Intranet

**Scenario**: voor het bedrijfsscenario mensen werken in een omgeving waarin er geen toegang tot Internet maar Intranet alleen. PackageManagement heeft geen ondersteuning voor deze aanvraag in WMF 5.0.

**Scenario**: In WMF 5.0, PackageManagement computers waarvoor alleen Intranet (maar niet Internet) niet ondersteunt toegang.

**Oplossing**: WMF-5.1, u kunt deze stappen zodat intranetcomputers PackageManagement gebruiken:

1. Download de NuGet-provider met behulp van een andere computer met een internetverbinding via `Install-PackageProvider -Name NuGet`.

2. De provider NuGet onder vinden `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. De binaire bestanden kopiëren naar een map of sharelocatie die de computer van het Intranet toegang en installeer het NuGet-provider met `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Gebeurtenis logboekregistratie verbeteringen

Wanneer u pakketten installeren, wijzigt u de status van de computer. In WMF 5.1 PackageManagement nu legt gebeurtenissen vast in het Windows-gebeurtenislogboek voor `Install-Package`, `Uninstall-Package`, en `Save-Package` activiteiten. Het gebeurtenislogboek is hetzelfde als voor PowerShell, dat wil zeggen, `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Ondersteuning voor basisverificatie

In WMF 5.1 ondersteunt PackageManagement zoeken en installeren van pakketten uit een opslagplaats die hiervoor is basisauthenticatie vereist. U kunt opgeven dat uw referenties voor de `Find-Package` en `Install-Package` cmdlets. Bijvoorbeeld:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Ondersteuning voor het gebruik van PackageManagement zich achter een proxy

In de WMF 5.1, duurt PackageManagement nu nieuwe proxyparameters `-ProxyCredential` en `-Proxy`. Gebruik van deze parameters kunt u de proxy-URL en referenties naar PackageManagement-cmdlets. Proxy-systeeminstellingen worden standaard gebruikt. Bijvoorbeeld:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

