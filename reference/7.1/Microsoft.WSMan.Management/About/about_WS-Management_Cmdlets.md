---
description: Biedt een overzicht van Web Services for Management (WS-Management) als achtergrond voor het gebruik van de WS-Management-cmdlets in Windows Power shell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/about/about_ws-management_cmdlets?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WS Management_Cmdlets
ms.openlocfilehash: c9d89d0559bf844927976c78bde6fca58ffa8855
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390504"
---
# <a name="about-ws-management-cmdlets"></a>Over WS-Management-cmdlets

## <a name="short-description"></a>KORTE BESCHRIJVING

Biedt een overzicht van Web Services for Management (WS-Management) als achtergrond voor het gebruik van de WS-Management-cmdlets in Windows Power shell.

## <a name="long-description"></a>LANGE BESCHRIJVING

In dit onderwerp vindt u een overzicht van Web Services for Management (WS-Management) als achtergrond voor het gebruik van de WS-Management-cmdlets in Windows Power shell. Dit onderwerp bevat ook koppelingen naar meer informatie over WS-Management. De micro soft-implementatie van WS-Management wordt ook wel Windows Remote Management (WinRM) genoemd.

## <a name="about-ws-management"></a>Over WS-Management

Windows Remote Management is de micro soft-implementatie van het WS-Management-protocol, een standaard op basis van een gebruikers vriendelijke, firewall vriendelijk protocol waarmee hardware en besturings systemen van verschillende leveranciers kunnen samen werken. De specificatie van het WS-Management-protocol biedt systemen een gemeen schappelijke manier om toegang te krijgen tot en Exchange-beheer gegevens in een IT-infra structuur (Information Technology). WS-Management en IPMI (Intelligent Platform Management Interface), samen met de gebeurtenis verzamelaar, zijn onderdelen van de Windows-functies voor het beheer van hardware.

Het WS-Management-protocol is gebaseerd op de volgende standaard web service-specificaties: HTTPS, SOAP via HTTP (WS-I profile), SOAP 1,2, WS-Addressing, WS-overdracht, WS-Enumeration en WS-eventing.

## <a name="ws-management-and-wmi"></a>WS-Management en WMI

WS-Management kunnen worden gebruikt om gegevens op te halen die worden weer gegeven door Windows Management Instrumentation (WMI). U kunt WMI-gegevens verkrijgen met scripts of toepassingen die gebruikmaken van de WS-Management Scripting-API of via het opdracht regel programma WinRM. WS-Management ondersteunt de meeste vertrouwde WMI-klassen en-bewerkingen, inclusief Inge sloten objecten. WS-Management kan gebruikmaken van WMI voor het verzamelen van gegevens over bronnen of voor het beheren van resources op een Windows-computer. Dit betekent dat u gegevens kunt verkrijgen over objecten zoals schijven, netwerk adapters, services of processen in uw onderneming via de bestaande set WMI-klassen. U hebt ook toegang tot de hardware-gegevens die beschikbaar zijn via de standaard WMI IPMI-provider.

## <a name="ws-management-windows-powershell-provider-wsman"></a>Windows Power shell-provider (WSMan) WS-Management

De WSMan-provider biedt een hiërarchische weer gave van de beschik bare WS-Management configuratie-instellingen. De provider stelt u in staat om de verschillende WS-Management configuratie opties te verkennen en in te stellen.

## <a name="ws-management-configuration"></a>WS-Management configuratie

Als WS-Management niet is geïnstalleerd en geconfigureerd, externe toegang tot Windows Power shell is niet beschikbaar, de WS-Management-cmdlets worden niet uitgevoerd, WS-Management scripts niet worden uitgevoerd en de WSMan-provider kan geen gegevens bewerkingen uitvoeren. Het WS-Management opdracht regel programma, WinRM en gebeurtenis door sturen is ook afhankelijk van de WS-Management configuratie.

## <a name="ws-management-cmdlets"></a>WS-Management-cmdlets

WS-Management functionaliteit wordt in Windows Power shell geïmplementeerd via een module die een set cmdlets en de WSMan-provider bevat. U kunt deze cmdlets gebruiken voor het volt ooien van de end-to-end taken die nodig zijn voor het beheren van WS-Management instellingen op lokale en externe computers.

De volgende WS-Management-cmdlets zijn beschikbaar.

## <a name="connection-cmdlets"></a>Verbindings-cmdlets

- Connect-WSMan: verbindt de lokale computer met de WS-Management (WinRM)-service op een externe computer.

- Verbinding verbreken-WSMan: de verbinding van de lokale computer met de WS-Management-service (WinRM) op een externe computer wordt verbroken.

## <a name="management-data-cmdlets"></a>Management-Data-cmdlets

- Get-WSManInstance: geeft beheer gegevens weer voor een resource-exemplaar dat is opgegeven door een resource-URI.

- Invoke-WSManAction: roept een actie aan voor het doel object dat is opgegeven door de resource-URI en de selecters.

- New-WSManInstance: maakt een nieuw beheer resource-exemplaar.

- Remove-WSManInstance: verwijdert een beheer resource-exemplaar.

- Set-WSManInstance: Hiermee wijzigt u de beheer gegevens die zijn gerelateerd aan een resource.

## <a name="setup-and-configuration-cmdlets"></a>Cmdlets voor Setup en configuratie

- Set-WSManQuickConfig: Hiermee configureert u de lokale computer voor extern beheer.
  U kunt de cmdlet Set-WSManQuickConfig gebruiken om WS-Management te configureren om externe verbindingen met de WS-Management-service (WinRM) toe te staan. Met de cmdlet Set-WSManQuickConfig worden de volgende bewerkingen uitgevoerd:
  - Hiermee wordt bepaald of de WS-Management-service (WinRM) wordt uitgevoerd. Als de WinRM-service niet wordt uitgevoerd, start de Set-WSManQuickConfig-cmdlet de service.
  - Hiermee stelt u het opstart type van de WS-Management (WinRM)-service in op automatisch.
  - Er wordt een listener gemaakt die aanvragen van elk IP-adres accepteert. Het standaard transport protocol is HTTP.
  - Hiermee schakelt u een firewall-uitzonde ring voor WS-Management verkeer.

  Opmerking: als u deze cmdlet wilt uitvoeren in Windows Vista, Windows Server 2008 en latere versies van Windows, moet u Windows Power shell starten met de optie als administrator uitvoeren.

- Test-WSMan: controleert of WS-Management is geïnstalleerd en geconfigureerd. De Test-WSMan-cmdlet test of de WS-Management-service (WinRM) wordt uitgevoerd en is geconfigureerd op een lokale of externe computer.

- Disable-WSManCredSSP: Hiermee schakelt u CredSSP-verificatie op een client computer uit.

- Enable-WSManCredSSP: Hiermee schakelt u CredSSP-verificatie in op een client computer.

- Get-WSManCredSSP: haalt de CredSSP-gerelateerde configuratie voor een client computer op.

## <a name="ws-management-specific-cmdlets"></a>WS-Management-specifieke cmdlets

- New-WSManSessionOption: maakt een WSManSessionOption-object dat als invoer wordt gebruikt voor een of meer para meters van een WS-Management-cmdlet.

## <a name="additional-ws-management-information"></a>Aanvullende informatie over WS-Management

Zie de volgende onderwerpen in de Windows-documentatie voor meer informatie over WS-Management.

[Windows Remote Management](/windows/win32/winrm/portal)

[Over Windows Remote Management](/windows/win32/winrm/about-windows-remote-management)

[Installatie en configuratie voor Windows Remote Management](/windows/win32/winrm/installation-and-configuration-for-windows-remote-management)

[Architectuur van Windows Remote Management](/windows/win32/winrm/windows-remote-management-architecture)

[WS-Management-protocol](/windows/win32/winrm/ws-management-protocol)

[Windows Remote Management en WMI](/windows/win32/winrm/windows-remote-management-and-wmi)

[Bron-Uri's](/windows/win32/winrm/resource-uris)

[Extern hardwarematig beheer](/windows/win32/winrm/remote-hardware-management)

[Gebeurtenissen](/windows/win32/winrm/events)

## <a name="see-also"></a>ZIE OOK

[Connect-WSMan](xref:Microsoft.WSMan.Management.Connect-WSMan)

[Disable-WSManCredSSP](xref:Microsoft.WSMan.Management.Disable-WSManCredSSP)

[Verbinding verbreken-WSMan](xref:Microsoft.WSMan.Management.Disconnect-WSMan)

[Enable-WSManCredSSP](xref:Microsoft.WSMan.Management.Enable-WSManCredSSP)

[Get-WSManCredSSP](xref:Microsoft.WSMan.Management.Get-WSManCredSSP)

[Get-WSManInstance](xref:Microsoft.WSMan.Management.Get-WSManInstance)

[Invoke-WSManAction](xref:Microsoft.WSMan.Management.Invoke-WSManAction)

[New-WSManInstance](xref:Microsoft.WSMan.Management.New-WSManInstance)

[Remove-WSManInstance](xref:Microsoft.WSMan.Management.Remove-WSManInstance)

[Set-WSManInstance](xref:Microsoft.WSMan.Management.Set-WSManInstance)

[Set-WSManQuickConfig](xref:Microsoft.WSMan.Management.Set-WSManQuickConfig)

[Testen-WSMan](xref:Microsoft.WSMan.Management.Test-WSMan)
