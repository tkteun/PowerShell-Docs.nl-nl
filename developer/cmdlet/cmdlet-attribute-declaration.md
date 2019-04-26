---
title: Kenmerk van de cmdlet-declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068620"
---
# <a name="cmdlet-attribute-declaration"></a>Declaratie van het kenmerk Cmdlet

Het kenmerk Cmdlet identificeert een Microsoft .NET Framework-klasse als een cmdlet en Hiermee geeft u het werkwoord en een zelfstandig naamwoord gebruikt voor het aanroepen van de cmdlet.

## <a name="syntax"></a>Syntaxis

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

`VerbName` ([System.String](/dotnet/api/System.String)) vereist. Hiermee geeft u de cmdlet-bewerking. Deze term Hiermee geeft u de actie op die door de cmdlet. Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md) en [vereist ontwikkeling richtlijnen](./required-development-guidelines.md).

`NounName` ([System.String](/dotnet/api/System.String)) vereist. Hiermee geeft u de cmdlet-zelfstandig naamwoord. Deze zelfstandig naamwoord Hiermee geeft u de resource die de cmdlet reageert. Zie voor meer informatie over de cmdlet-woorden [Cmdlet declaratie](./cmdlet-class-declaration.md) en [ten zeerste aangeraden ontwikkeling richtlijnen](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. `True` Geeft aan dat de cmdlet biedt ondersteuning voor aanroepen naar de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode, die de cmdlet een manier biedt om de gebruiker vragen voordat een actie die wijzigingen van het systeem wordt uitgevoerd. `False`, de standaardwaarde geeft aan dat de cmdlet geen ondersteuning voor aanroepen naar de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode. Zie voor meer informatie over aanvragen voor bevestiging [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).

`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) met de naam van parameter optioneel. Hiermee geeft u op wanneer de actie van de cmdlet moet worden bevestigd door een aanroep naar de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode. [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) alleen worden aangeroepen wanneer de ConfirmImpact-waarde van de cmdlet (standaard is dit normaal) gelijk aan of groter is dan de waarde van is de `$ConfirmPreference` variabele. Deze parameter moet worden opgegeven alleen wanneer de `SupportsShouldProcess` parameter is opgegeven.

`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) met de naam van parameter optioneel. Hiermee geeft u dat de standaardparameter ingesteld dat de Windows PowerShell-runtime probeert te gebruiken als deze niet kan bepalen welke parameter ingesteld voor het gebruik. U ziet dat deze situatie te worden geëlimineerd door de unieke parameter van elke parameter is een verplichte parameter ingesteld.

Er is een situatie waarin de standaardparameter instellen, zelfs als een standaardnaam voor de parameter-set is opgegeven niet gebruiken in Windows PowerShell. De Windows PowerShell-runtime kan onderscheid maken tussen parametersets die uitsluitend zijn gebaseerd op objecttype. Bijvoorbeeld, als u hebt één parameterset die wordt gebruikt een tekenreeks als het bestandspad en een andere set die duurt een **FileInfo** object direct Windows PowerShell kan niet worden vastgesteld welke parameter ingesteld voor gebruik op basis van de waarden worden doorgegeven aan de cmdlet, noch gebruikt de parameterset standaard. In dit geval, zelfs als u de naam van een standaardparameter instellen opgeeft, genereert Windows PowerShell een niet-eenduidige parameter set foutbericht weergegeven.

`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) met de naam van parameter optioneel. `True` Geeft aan dat de cmdlet kan worden gebruikt binnen een transactie. Wanneer `True` is opgegeven, wordt de Windows PowerShell-runtime voegt de `UseTransaction` parameter aan de lijst met parameters van de cmdlet. `False`, de standaardwaarde geeft aan dat de cmdlet kan niet worden gebruikt binnen een transactie.

## <a name="remarks"></a>Opmerkingen

- Samen worden het werkwoord en een zelfstandig naamwoord gebruikt voor het identificeren van uw geregistreerde cmdlet en aanroepen van de cmdlet uit binnen een script.

- Wanneer de cmdlet wordt opgeroepen via de Windows PowerShell-console, lijkt de opdracht op de volgende opdracht uit:

**VerbName NounName**

- Alle cmdlets die bronnen buiten Windows PowerShell wijzigen moet bevatten de `SupportsShouldProcess` sleutelwoord wanneer de Cmdlet-kenmerk is gedeclareerd, waardoor de cmdlet om aan te roepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) methode voordat de cmdlet wordt de bijbehorende actie uitgevoerd. Als de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen retourneert `false`, de actie niet moet worden genomen. Voor meer informatie over de bevestiging van aanvragen die worden gegenereerd door de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen, Zie [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md).

De `Confirm` en `WhatIf` cmdlet-parameters zijn alleen beschikbaar voor cmdlets die ondersteuning bieden voor [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) aanroepen.

## <a name="example"></a>Voorbeeld

De volgende klassendefinitie gebruikt de Cmdlet-kenmerk voor het identificeren van de .NET Framework-klasse voor een **Get-Proc** -cmdlet haalt informatie op over de processen die op de lokale computer worden uitgevoerd.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Voor meer informatie over de **Get-Proc** cmdlet, Zie [GetProc zelfstudie](./getproc-tutorial.md).

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
