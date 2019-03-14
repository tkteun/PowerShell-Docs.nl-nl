---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
contributor: jianyunt, quoctruong
title: Verbeteringen in Pakketbeheer in WMF 5.1
ms.openlocfilehash: 30ef59ed9dc0d56636d85cc6e53523a9a73963a4
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794277"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Verbeteringen in Pakketbeheer in WMF 5.1

## <a name="improvements-in-packagemanagement"></a>Verbeteringen in Pakketbeheer

Hier volgen de verbeteringen aangebracht in de WMF 5.1:

### <a name="version-alias"></a>Versie Alias

**Scenario**: Als u versie 1.0 of 2.0 van een pakket, P1, dat is geïnstalleerd op uw systeem hebt en u wilt verwijderen van versie 1.0, moet u uitvoeren `Uninstall-Package -Name P1 -Version 1.0` en versie 1.0 om te worden verwijderd na het uitvoeren van de cmdlet verwacht. Maar het resultaat is dat versie 2.0 wordt verwijderd.

Dit gebeurt omdat de `-Version` parameter is een alias van de `-MinimumVersion` parameter. PackageManagement zoekt een gekwalificeerde pakket met de minimale versie van 1.0, retourneert de meest recente versie. Dit is verwacht gedrag in de normale gevallen omdat zoeken naar dat de meest recente versie is gewoonlijk het gewenste resultaat. Maar deze moet niet van toepassing op de `Uninstall-Package` geval.

**Oplossing**: verwijderd `-Version` alias volledig in PackageManagement (ook wel) OneGet) en PowerShellGet.

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Meerdere aanwijzingen voor het opstarten van het NuGet-provider

**Scenario**: Bij het uitvoeren van `Find-Module` of `Install-Module` of andere PackageManagement-cmdlets voor de eerste keer PackageManagement op de computer probeert te starten van de NuGet-provider. Dit gebeurt omdat de PowerShellGet-provider ook het NuGet-provider wordt gebruikt voor het downloaden van de PowerShell-modules. PackageManagement vraagt vervolgens de gebruiker om toestemming voor het installeren van de NuGet-provider. Nadat de gebruiker 'Ja' voor het uitvoeren van de bootstrap selecteert, wordt de meest recente versie van de NuGet-provider worden geïnstalleerd.

Echter, in sommige gevallen, wanneer u een oude versie van NuGet-provider is geïnstalleerd op uw computer hebt soms de oudere versie van NuGet opgehaald geladen eerst in de PowerShell-sessie (dat wil zeggen de racevoorwaarde in PackageManagement). PowerShellGet vereist echter de nieuwere versie van het NuGet-provider om te werken, zodat PowerShellGet PackageManagement opnieuw opstarten van het NuGet-provider wordt gevraagd. Dit resulteert in meerdere stappen voor het opstarten van het NuGet-provider.

**Oplossing**: PackageManagement geladen in WMF5.1, de meest recente versie van de NuGet-provider om te voorkomen dat meerdere aanwijzingen voor het opstarten van het NuGet-provider.

U kunt ook omzeilen dit probleem door de oude versie van het NuGet-provider (NuGet-Anycpu.exe) handmatig te verwijderen als bestaat uit $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Ondersteuning voor PackageManagement op computers met alleen toegang tot Intranet

**Scenario**: Voor het enterprise-scenario, mensen werken in een omgeving waarbij er geen toegang tot Internet, maar Intranet alleen. PackageManagement heeft geen ondersteuning voor deze aanvraag in WMF 5.0.

**Scenario**: In WMF 5.0 PackageManagement bieden geen ondersteuning voor computers die alleen Intranet (maar niet met Internet) hebben toegang.

**Oplossing**: In WMF 5.1, kunt u deze stappen om toe te staan intranetcomputers PackageManagement gebruiken:

1. Download het NuGet-provider met behulp van een andere computer met een internetverbinding met behulp van `Install-PackageProvider -Name NuGet`.

2. Zoek het NuGet-provider onder `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.

3. De binaire bestanden kopiëren naar een map of sharelocatie die de Intranet-computer kan toegang krijgen tot, en installeer het NuGet-provider met `Install-PackageProvider -Name NuGet -Source <Path to folder>`.


### <a name="event-logging-improvements"></a>Verbeteringen in de gebeurtenis vastleggen

Wanneer u pakketten installeert, wijzigt u de status van de computer. In WMF 5.1, PackageManagement nu legt gebeurtenissen vast in het Windows-gebeurtenislogboek voor `Install-Package`, `Uninstall-Package`, en `Save-Package` activiteiten. Het gebeurtenislogboek is dezelfde als die voor PowerShell, dat wil zeggen, `Microsoft-Windows-PowerShell, Operational`.

### <a name="support-for-basic-authentication"></a>Ondersteuning voor basisverificatie

PackageManagement ondersteunt in WMF 5.1, zoeken en installeren van pakketten vanuit een opslagplaats die hiervoor is basisauthenticatie vereist. U kunt uw referenties opgeven de `Find-Package` en `Install-Package` cmdlets. Bijvoorbeeld:

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Ondersteuning voor het gebruik van PackageManagement achter een proxy

In WMF 5.1, PackageManagement duurt nu nog maar de proxyparameters voor de nieuwe `-ProxyCredential` en `-Proxy`. Met behulp van deze parameters, kunt u de proxy-URL en referenties voor PackageManagement-cmdlets. Standaard worden systeem proxy-instellingen gebruikt. Bijvoorbeeld:

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
