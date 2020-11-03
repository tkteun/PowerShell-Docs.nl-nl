---
description: Hierin worden de beperkingen van Windows Power Shell 4,0 op Windows RT 8,1 beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252538"
---
# <a name="about-windows-rt"></a>Over Windows RT

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden de beperkingen van Windows Power Shell 4,0 op Windows RT 8,1 beschreven.

## <a name="long-description"></a>LANGE BESCHRIJVING

Het Windows RT 8,1-besturings systeem is geïnstalleerd op computers en apparaten (zoals micro soft-Opper vlak 2, waarop het het besturings systeem is dat wordt geleverd bij de computer) die gebruikmaakt van Advanced RISC machine-processors (ARM).

Windows Power Shell 4,0 is opgenomen in Windows RT 8,1. Alle cmdlets, providers en modules en de meeste scripts die zijn ontworpen voor Windows Power Shell 2,0 en latere versies, worden zonder wijzigingen uitgevoerd op Windows RT 8,1.

Omdat Windows RT 8,1 niet alle Windows-onderdelen bevat, werken sommige Windows Power shell-onderdelen anders of werken ze niet op Windows RT-apparaten. In de volgende lijst worden de verschillen beschreven.

- Windows PowerShell ISE is niet opgenomen in en kan niet worden uitgevoerd op Windows RT 8,1.
  Windows PowerShell ISE vereist Windows Presentation Foundation, dat niet is opgenomen in Windows RT 8,1.

- Externe communicatie van Windows Power shell en de WinRM-service zijn standaard uitgeschakeld.
  Als u externe toegang wilt inschakelen, voert u de Enable-PSRemoting-cmdlet uit. Voer ook de Set-Service-cmdlet uit om het opstart type van de WinRM-service in te stellen op automatisch of automatisch (vertraagd starten).

  Externe toegang is uitgeschakeld, u kunt Windows Power shell Remoting gebruiken om opdrachten uit te voeren op andere computers, maar andere computers kunnen geen opdrachten uitvoeren op het Windows RT-apparaat. Ook wel impliciete externe communicatie, dat wil zeggen externe toegang die is ingebouwd in een cmdlet of script, en niet expliciet is aangevraagd met toegevoegde para meters
  - werkt niet in Windows Power shell die wordt uitgevoerd op Windows RT 8,1.

- Computers die lid zijn van een domein en Kerberos-verificatie worden niet ondersteund in Windows RT 8,1. U kunt Windows Power shell niet gebruiken om deze functies toe te voegen of te beheren.

- Microsoft .NET Framework-klassen die niet worden ondersteund op Windows RT 8,1 worden ook niet ondersteund door Windows Power shell op Windows RT 8,1.

- Trans acties zijn niet ingeschakeld op Windows RT 8,1. Trans actie-cmdlets, zoals start-trans actie en transactie parameters, zoals UseTransaction, werken niet goed.

- Alle Windows Power shell-sessies op Windows RT 8,1-apparaten gebruiken de ConstrainedLanguage taal modus. ConstrainedLanguage taal modus is een aanvulling op de code-integriteit van de gebruikers modus (UMCI). Alle Windows-cmdlets en Windows Power shell-taal elementen zijn toegestaan, maar typen worden beperkt om ervoor te zorgen dat gebruikers Windows Power shell niet kunnen gebruiken om de UMCI-beveiligingen te omzeilen of te schenden.

Zie [about_Language_Modes](about_Language_Modes.md)voor meer informatie over de taal modus ConstrainedLanguage.

## <a name="see-also"></a>ZIE OOK

[about_Language_Modes](about_Language_Modes.md)

[about_Remote](about_Remote.md)

[about_Windows_PowerShell_ISE](about_Windows_PowerShell_ISE.md)
