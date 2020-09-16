---
title: Naslag informatie voor Windows Power shell | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- Windows PowerShell SDK
ms.openlocfilehash: 1c1a3a4de2df2043fe12cad6a69b7bc36ab9d3d7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786676"
---
# <a name="windows-powershell-reference"></a>Naslaginformatie over Windows PowerShell

Windows Power shell is een omgeving met Microsoft .NET Framework dat is ontworpen voor beheer automatisering. Windows Power shell biedt een nieuwe benadering voor het bouwen van opdrachten, het samen stellen van oplossingen en het maken van op Graphical User Interface gebaseerde beheer hulpprogramma's.

Met Windows Power shell kan een systeem beheerder het beheer van systeem bronnen automatiseren door de uitvoering van opdrachten rechtstreeks of via scripts uit te voeren.

## <a name="developer-audience"></a>Doel groep van ontwikkel aars

De Windows Power shell Software Development Kit (SDK) is geschreven voor opdracht ontwikkelaars die referentie gegevens nodig hebben over de Api's van Windows Power shell. Opdracht ontwikkelaars gebruiken Windows Power shell voor het maken van opdrachten en providers die de taken uitbreiden die kunnen worden uitgevoerd door Windows Power shell.

## <a name="windows-powershell-resources"></a>Windows Power shell-resources

Naast de Windows Power shell SDK bevatten de volgende bronnen meer informatie.

[Aan de slag met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell) Biedt een inleiding tot Windows Power shell: de taal, de cmdlets, de providers en het gebruik van-objecten.

[Een Windows Power shell-module schrijven](./module/writing-a-windows-powershell-module.md) Bevat informatie en voor beelden voor beheerders, script ontwikkelaars en cmdlet-ontwikkel aars die hun Windows Power shell-oplossingen moeten inpakken en distribueren met behulp van Windows Power shell-modules.

[Een Windows Power shell-cmdlet schrijven](./cmdlet/writing-a-windows-powershell-cmdlet.md) Bevat informatie en code voorbeelden voor programma managers die cmdlets ontwerpen en voor ontwikkel aars die cmdlet-code implementeren.

[Windows Power shell-team blog](https://blogs.msdn.microsoft.com/PowerShell/) De beste resource voor het leren van en samen werken met andere Windows Power shell-gebruikers. Lees de blog van het Windows Power shell-team en Word lid van het Windows Power shell-gebruikers Forum (micro soft. public. Windows. Power shell).
Gebruik Windows Live Search om andere Windows Power shell-blogs en-bronnen te vinden. Wanneer u uw expertise ontwikkelt, kunt u uw ideeën dan vrij bijdragen.

[Browser van de Power shell-module](/powershell/module/) Bevat de meest recente versies van de Help-onderwerpen voor de opdracht regel.

## <a name="class-libraries"></a>Class-bibliotheken

[System. Management. Automation](/dotnet/api/System.Management.Automation) deze naam ruimte is de hoofd naam ruimte voor Windows Power shell. Het bevat de klassen, opsommingen en interfaces die zijn vereist voor het implementeren van aangepaste cmdlets. Met name de klasse [System. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) is de basis klasse waarvan alle cmdlet-klassen moeten worden afgeleid. Zie voor meer informatie over cmdlets.

[System. Management. Automation. provider](/dotnet/api/System.Management.Automation.Provider) deze naam ruimte bevat de klassen, opsommingen en interfaces die zijn vereist voor het implementeren van een Windows Power shell-provider. Met name de klasse [System. Management. Automation. provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) is de basis klasse waaruit alle Windows Power shell-provider klassen moeten worden afgeleid.

[Micro soft. Power shell. opdrachten](/dotnet/api/Microsoft.PowerShell.Commands) deze naam ruimte bevat de klassen voor de cmdlets en providers die worden geïmplementeerd door Windows Power shell. Het is ook raadzaam dat *u een naam*maakt. De naam ruimte van opdrachten voor de cmdlets die u implementeert.

[System. Management. Automation. host](/dotnet/api/System.Management.Automation.Host) deze naam ruimte bevat de klassen, opsommingen en interfaces die de cmdlet gebruikt voor het definiëren van de interactie tussen de gebruiker en Windows Power shell.

[System. Management. Automation. Internal](/dotnet/api/System.Management.Automation.Internal) deze naam ruimte bevat de basis klassen die door andere naam ruimte klassen worden gebruikt. De klasse [System. Management. Automation. internal. Cmdletmetadataattribute](/dotnet/api/System.Management.Automation.Internal.CmdletMetadataAttribute) is bijvoorbeeld de basis klasse voor de klasse [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .

[System. Management. Automation. Runspaces](/dotnet/api/System.Management.Automation.Runspaces) deze naam ruimte bevat de klassen, opsommingen en interfaces die worden gebruikt voor het maken van een Windows Power shell-runs Pace. In deze context is de Windows Power shell-runs Pace de context waarin een of meer Windows Power shell-pijp lijnen cmdlets aanroepen. Dat wil zeggen dat cmdlets werken in de context van een Windows Power shell-runs Pace. Zie [Windows Power shell runspaces](hosting/creating-runspaces.md)voor meer informatie AboutWindows Power shell runspaces.
