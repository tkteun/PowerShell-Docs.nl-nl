---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Verbeteringen van pakketbeheer in WMF 5.1
ms.openlocfilehash: cb19c2d71391b5729ce9d73fc6b033270f8db307
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325117"
---
# <a name="improvements-to-package-management-in-wmf-51"></a>Verbeteringen van pakketbeheer in WMF 5.1

De volgende correcties zijn aangebracht in de WMF 5,1:

## <a name="version-alias"></a>Versie alias

**Scenario**: Als u versie 1,0 en 2,0 van een pakket hebt, P1, op uw systeem is geïnstalleerd en u versie 1,0 wilt verwijderen, moet u `Uninstall-Package -Name P1 -Version 1.0` de installatie van versie 1,0 ongedaan maken na het uitvoeren van de cmdlet. Het resultaat is echter dat versie 2,0 wordt verwijderd.

Dit komt doordat de `-Version` para meter een alias van de `-MinimumVersion` para meter is. Wanneer Package Management zoekt naar een gekwalificeerd pakket met de minimale versie van 1,0, wordt de meest recente versie geretourneerd. Dit gedrag wordt in normale gevallen verwacht, omdat het zoeken naar de meest recente versie doorgaans het gewenste resultaat is. Het mag echter niet worden toegepast op de `Uninstall-Package` aanvraag.

**Oplossing**: alias `-Version` volledig verwijderd uit Package Management (ook OneGet) en PowerShellGet.

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>Meerdere prompts voor het Boots trappen van de NuGet-provider

**Scenario**: Wanneer u of `Find-Module` `Install-Module` een andere Package Management-cmdlets voor de eerste keer uitvoert op uw computer, probeert Package Management de NuGet-provider te Boots trapn. Dit komt omdat de PowerShellGet-provider ook de NuGet-provider gebruikt voor het downloaden van Power shell-modules.
Package Management vraagt de gebruiker vervolgens om toestemming om de NuGet-provider te installeren. Nadat de gebruiker Ja voor de Boots trapping heeft geselecteerd, wordt de meest recente versie van de NuGet-provider geïnstalleerd.

In sommige gevallen, wanneer u een oude versie van de NuGet-provider op uw computer hebt geïnstalleerd, wordt de oudere versie van NuGet soms eerst geladen in de Power shell-sessie (dat is de race voorwaarde in Package Management). PowerShellGet vereist echter dat de nieuwere versie van de NuGet-provider werkt. PowerShellGet vraagt package management om de NuGet-provider opnieuw aan te bootslen.
Dit resulteert in meerdere prompts voor het Boots trappen van de NuGet-provider.

**Oplossing**: In WMF 5.1 laadt Package Management de nieuwste versie van de NuGet-provider om te voor komen dat er meerdere prompts worden gevraagd om de NuGet-provider te Boots trappen.

U kunt dit probleem ook omzeilen door de oude versie van de NuGet-provider (NuGet-Anycpu. exe) hand matig te verwijderen als deze bestaat uit $env:P rogramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>Ondersteuning voor Package Management op computers met alleen intranet toegang

**Scenario**: Voor het Enter prise-scenario werken mensen onder een omgeving waarin er geen Internet toegang is, maar alleen intranet. Package Management biedt geen ondersteuning voor dit probleem in WMF 5,0.

**Scenario**: In WMF 5,0 heeft Package Management geen ondersteuning voor computers die toegang hebben tot een intranet (maar niet via internet).

**Oplossing**: In WMF 5,1 kunt u deze stappen volgen om intranet computers toe te staan package management te gebruiken:

1. Down load de NuGet-provider met behulp van een andere computer met `Install-PackageProvider -Name NuGet`een Internet verbinding.

2. Zoek de NuGet-provider onder `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` ofwel `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`of.

3. Kopieer de binaire bestanden naar een map of netwerk share locatie waartoe de intranet computer toegang heeft en installeer vervolgens de NuGet-provider `Install-PackageProvider -Name NuGet -Source <Path to folder>`met.


## <a name="event-logging-improvements"></a>Verbeteringen in gebeurtenis logboek registratie

Wanneer u pakketten installeert, wijzigt u de status van de computer. In WMF 5,1 registreert package management nu gebeurtenissen in het Windows-gebeurtenis logboek `Install-Package`voor `Uninstall-Package`, en `Save-Package` -activiteiten. Het gebeurtenis logboek is hetzelfde als voor Power shell, dat wil zeggen `Microsoft-Windows-PowerShell, Operational`.

## <a name="support-for-basic-authentication"></a>Ondersteuning voor basis verificatie

In WMF 5,1 biedt package management ondersteuning voor het zoeken en installeren van pakketten van een opslag plaats waarvoor basis verificatie is vereist. U kunt uw referenties voor de `Find-Package` cmdlets en `Install-Package` opgeven. Bijvoorbeeld:

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a>Ondersteuning voor het gebruik van Package Management achter een proxy

In WMF 5,1 maakt package management nu nieuwe proxy parameters `-ProxyCredential` en. `-Proxy` Met deze para meters kunt u de proxy-URL en referenties voor Package Management-cmdlets opgeven. Standaard worden systeem proxy instellingen gebruikt. Bijvoorbeeld:

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
