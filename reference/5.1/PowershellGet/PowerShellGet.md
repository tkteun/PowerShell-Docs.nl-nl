---
Download Help Link: https://go.microsoft.com/fwlink/?LinkId=393271
Help Version: 5.2.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 130582b1b9f18a8f6ada7c009c6d25a7dab75e46
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890709"
---
# PowerShellGet-module

## Description

PowerShellGet is een module met opdrachten voor het detecteren, installeren, bijwerken en publiceren van Power shell-artefacten, zoals modules, DSC-resources, functie mogelijkheden en scripts.

> [!IMPORTANT]
> Vanaf april 2020 biedt de PowerShell Gallery niet langer ondersteuning voor Transport Layer Security (TLS) versie 1,0 en 1,1. Als u geen TLS 1,2 of hoger gebruikt, wordt er een fout bericht weer gegeven wanneer u probeert toegang te krijgen tot de PowerShell Gallery. Gebruik de volgende opdracht om ervoor te zorgen dat u TLS 1,2 gebruikt:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Zie de [aankondiging](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in het Power shell-blog voor meer informatie.

## PowerShellGet-cmdlets

### [Zoeken-opdracht](Find-Command.md)
Hiermee vindt u Power shell-opdrachten in modules.

### [Zoeken-Dscresource bieden](Find-DscResource.md)
Hiermee vindt u een DSC-resource.

### [Find-Module](Find-Module.md)
Hiermee worden modules in een opslag plaats gevonden die overeenkomen met opgegeven criteria.

### [Zoeken-RoleCapability](Find-RoleCapability.md)
Hiermee vindt u functie mogelijkheden in modules.

### [Zoeken-script](Find-Script.md)
Zoekt naar een script.

### [Get-InstalledModule](Get-InstalledModule.md)
Hiermee wordt een lijst met modules opgehaald op de computer die is geïnstalleerd door PowerShellGet.

### [Get-InstalledScript](Get-InstalledScript.md)
Hiermee wordt een geïnstalleerd script opgehaald.

### [Get-PSRepository](Get-PSRepository.md)
Hiermee worden Power shell-opslag plaatsen opgehaald.

### [Installatie-module](Install-Module.md)
Hiermee downloadt u een of meer modules uit een opslag plaats en installeert u deze op de lokale computer.

### [Install-script](Install-Script.md)
Hiermee wordt een script geïnstalleerd.

### [New-ScriptFileInfo](New-ScriptFileInfo.md)
Hiermee maakt u een script bestand met meta gegevens.

### [Publish-Module](Publish-Module.md)
Hiermee publiceert u een opgegeven module van de lokale computer naar een online galerie.

### [Publish-Script](Publish-Script.md)
Publiceert een script.

### [REGI ster-PSRepository](Register-PSRepository.md)
Registreert een Power shell-opslag plaats.

### [Save-Module](Save-Module.md)
Slaat een module en de bijbehorende afhankelijkheden op de lokale computer op, maar installeert de module niet.

### [Save-Script](Save-Script.md)
Slaat een script op.

### [Set-PSRepository](Set-PSRepository.md)
Hiermee stelt u waarden in voor een geregistreerde opslag plaats.

### [Test-ScriptFileInfo](Test-ScriptFileInfo.md)
Hiermee wordt een opmerkingen blok voor een script gevalideerd.

### [Uninstall-module](Uninstall-Module.md)
Hiermee verwijdert u een module.

### [Uninstall-script](Uninstall-Script.md)
Hiermee verwijdert u een script.

### [Registratie ongedaan maken-PSRepository](Unregister-PSRepository.md)
Hiermee wordt de registratie van een opslag plaats ongedaan gemaakt.

### [Update-Module](Update-Module.md)
Downloadt en installeert de nieuwste versie van de opgegeven modules van een online galerie naar de lokale computer.

### [Update-ModuleManifest](Update-ModuleManifest.md)
Hiermee wordt een manifest bestand van de module bijgewerkt.

### [Update-script](Update-Script.md)
Hiermee wordt een script bijgewerkt.

### [Update-ScriptFileInfo](Update-ScriptFileInfo.md)
Hiermee wordt informatie over een script bijgewerkt.
