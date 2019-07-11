---
title: Windows PowerShell-referentie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows PowerShell SDK
ms.assetid: cbba4879-bcac-484a-9906-4bbe2cd1eb33
caps.latest.revision: 11
ms.openlocfilehash: 48b2b2b9ab2a39cf185ed54bcfa99d46562e13b6
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733750"
---
# <a name="windows-powershell-reference"></a>Naslaginformatie over Windows PowerShell

Windows PowerShell is een Microsoft .NET Framework-verbonden omgeving die is ontworpen voor het automatiseren van administratieve. Windows PowerShell biedt een nieuwe benadering voor het bouwen van opdrachten, oplossingen samenstellen en het maken van grafische hulpprogramma's voor beheer op basis van een interface.

Windows PowerShell kan een systeembeheerder voor het automatiseren van het beheer van systeembronnen door het uitvoeren van opdrachten rechtstreeks of via scripts.

## <a name="developer-audience"></a>Doelgroep: ontwikkelaars

De Windows PowerShell Software Development Kit (SDK) is geschreven voor ontwikkelaars van de opdracht die behoefte hebben aan referentie-informatie over de API die is geleverd door Windows PowerShell. Opdracht ontwikkelaars gebruiken Windows PowerShell-opdrachten en -providers die een uitbreiding vormen van de taken die kunnen worden uitgevoerd door de Windows PowerShell maken.

## <a name="windows-powershell-resources"></a>Windows PowerShell-Resources

Naast de SDK van Windows PowerShell bevatten de volgende bronnen meer informatie.

[Aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) bevat een inleiding tot PowerShell van Windows: de taal, de cmdlets, de providers en het gebruik van objecten.

[Een Windows PowerShell-Module schrijven](./module/writing-a-windows-powershell-module.md) bevat informatie en voorbeelden voor beheerders, script-ontwikkelaars en cmdlet-ontwikkelaars die willen Inpakken en distribueren van de Windows PowerShell-oplossingen met behulp van Windows PowerShell-modules.

[Schrijven van een Windows PowerShell-Cmdlet](./cmdlet/writing-a-windows-powershell-cmdlet.md) biedt informatie en codevoorbeelden voor programmamanagers die cmdlets ontwerpen en ontwikkelaars die de cmdlet-code.

[Windows PowerShell-teamblog](https://blogs.msdn.microsoft.com/PowerShell/) de beste resource voor het leren van en samenwerken met andere gebruikers van Windows PowerShell. Lees het teamblog van Windows PowerShell en wordt u lid van de Windows PowerShell-gebruikersforum (microsoft.public.windows.powershell). Gebruik Windows Live Search om te zoeken naar andere Windows PowerShell-blogs en resources. Klik, als u uw expertise ontwikkelen, uw ideeën bijdragen.

[PowerShell modulebrowser](/powershell/module/) biedt de nieuwste versies van de opdrachtregel Help-onderwerpen.

## <a name="class-libraries"></a>Klassenbibliotheken

[System.Management.Automation](/dotnet/api/System.Management.Automation) deze naamruimte is de naamruimte root voor Windows PowerShell. Het bevat de klassen, opsommingen en interfaces die nodig zijn voor het implementeren van aangepaste cmdlets. In het bijzonder de [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klasse is de basisklasse van die alle cmdlet klassen moeten worden afgeleid. Zie voor meer informatie over cmdlets.

[System.Management.Automation.Provider](/dotnet/api/System.Management.Automation.Provider) deze naamruimte bevat de klassen, opsommingen en interfaces die nodig zijn voor het implementeren van een Windows PowerShell-provider. In het bijzonder de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse is de basisklasse van die alle Windows PowerShell providerklassen moeten worden afgeleid.

[Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) deze naamruimte bevat de klassen voor de cmdlets en providers die zijn geïmplementeerd door de Windows PowerShell. Op deze manier is het aanbevolen dat u maakt een *uwnaam*. De naamruimte van de opdrachten voor die cmdlets die u implementeert.

[System.Management.Automation.Host](/dotnet/api/System.Management.Automation.Host) deze naamruimte bevat de klassen, opsommingen en interfaces die gebruikmaakt van de cmdlet voor het definiëren van de interactie tussen de gebruiker en de Windows PowerShell.

[System.Management.Automation.Internal](/dotnet/api/System.Management.Automation.Internal) deze naamruimte bevat de basisklassen die worden gebruikt door andere naamruimteklassen. Bijvoorbeeld, de [System.Management.Automation.Internal.Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) klasse is de basisklasse van de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasse.

[System.Management.Automation.Runspaces](/dotnet/api/System.Management.Automation.Runspaces) deze naamruimte bevat de klassen, opsommingen en interfaces die worden gebruikt voor het maken van een Windows PowerShell-runspace. In deze context is de Windows PowerShell-runspace de context waarin een of meer pijplijnen van Windows PowerShell cmdlets aanroepen. Dat wil zeggen, werken cmdlets binnen de context van een Windows PowerShell-runspace. Zie voor meer informatie aboutWindows PowerShell runspaces, [Windows PowerShell Runspaces](https://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9).
