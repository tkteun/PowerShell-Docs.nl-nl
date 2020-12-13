---
ms.date: 09/13/2016
ms.topic: reference
title: Declaratie van het kenmerk Cmdlet
description: Declaratie van het kenmerk Cmdlet
ms.openlocfilehash: 6bdfe39a4ab9ef4d4cc98daa592f69f7fab95e84
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653553"
---
# <a name="cmdlet-attribute-declaration"></a>Declaratie van het kenmerk Cmdlet

Het cmdlet-kenmerk identificeert een Microsoft .NET Framework-klasse als cmdlet en geeft het woord en de zelfstandige op die worden gebruikt voor het aanroepen van de cmdlet.

## <a name="syntax"></a>Syntaxis

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a>Parameters

`VerbName` ([System. String](/dotnet/api/System.String)) vereist. Hiermee geeft u de cmdlet-term. Met deze opdracht geeft u de actie op die door de cmdlet wordt uitgevoerd. Zie voor meer informatie over goedgekeurde cmdlet- [termen](./approved-verbs-for-windows-powershell-commands.md) en de [vereiste ontwikkel richtlijnen](./required-development-guidelines.md).

`NounName` ([System. String](/dotnet/api/System.String)) vereist. Hiermee geeft u het zelfstandig naam woord voor cmdlet. Dit zelfstandig naam woord geeft de resource op waarvoor de cmdlet wordt uitgevoerd. Zie voor meer informatie over cmdlet-naam woorden [cmdlet-declaratie](./cmdlet-class-declaration.md) en [sterk aanbevolen ontwikkel richtlijnen](./strongly-encouraged-development-guidelines.md).

`SupportsShouldProcess` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. `True` geeft aan dat de cmdlet aanroepen ondersteunt voor de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) , die de cmdlet biedt om de gebruiker te vragen voordat een actie wordt uitgevoerd die het systeem wijzigt. `False`, de standaard waarde, geeft aan dat de cmdlet geen ondersteuning biedt voor aanroepen naar de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . Zie [bevestiging aanvragen](./requesting-confirmation-from-cmdlets.md)voor meer informatie over bevestigings aanvragen.

`ConfirmImpact` ([System. Management. Automation. Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) een optionele benoemde para meter. Hiermee geeft u op wanneer de actie van de cmdlet moet worden bevestigd door een aanroep van de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) . [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt alleen aangeroepen wanneer de ConfirmImpact-waarde van de cmdlet (standaard, gemiddeld) gelijk is aan of groter is dan de waarde van de `$ConfirmPreference` variabele. Deze para meter moet alleen worden opgegeven als de `SupportsShouldProcess` para meter is opgegeven.

`DefaultParameterSetName` ([System. String](/dotnet/api/System.String)) een optionele benoemde para meter. Hiermee geeft u de standaard parameterset op die de Windows Power shell-runtime probeert te gebruiken wanneer niet kan worden bepaald welke para meter moet worden gebruikt. U ziet dat deze situatie kan worden geëlimineerd door de unieke para meter van elke para meter in te stellen op een verplichte para meter.

Er is één geval waarin Windows Power shell de standaard parameterset niet kan gebruiken, zelfs als er een standaard naam voor de parameterset is opgegeven. De Windows Power shell-runtime kan geen onderscheid maken tussen parameter sets op basis van uitsluitend het object type. Als u bijvoorbeeld één parameterset hebt die een teken reeks als het bestandspad gebruikt en een andere set die rechtstreeks een **file info** -object gebruikt, kan Windows Power shell niet bepalen welke para meter is ingesteld op basis van de waarden die zijn door gegeven aan de cmdlet, en wordt ook de standaard parameterset gebruikt. In dit geval, zelfs als u een standaard naam voor de parameterset opgeeft, wordt door Windows Power shell een dubbel zinnige para meter set-fout bericht gegenereerd.

`SupportsTransactions` ([System. Boolean](/dotnet/api/System.Boolean)) een optionele benoemde para meter. `True` geeft aan dat de cmdlet kan worden gebruikt binnen een trans actie. Wanneer `True` is opgegeven, voegt de Windows Power shell-runtime de `UseTransaction` para meter toe aan de parameter lijst van de cmdlet. `False`, de standaard waarde, geeft aan dat de cmdlet niet kan worden gebruikt binnen een trans actie.

## <a name="remarks"></a>Opmerkingen

- Samen worden de term en het zelfstandige id gebruikt voor het identificeren van de geregistreerde cmdlet en het aanroepen van de cmdlet in een script.

- Wanneer de cmdlet wordt aangeroepen vanuit de Windows Power shell-console, lijkt de opdracht op de volgende opdracht:

**Verbnaam-naam zelfstandige**

- Alle cmdlets die resources buiten Windows Power shell wijzigen, moeten het `SupportsShouldProcess` sleutel woord bevatten wanneer het cmdlet-kenmerk wordt gedeclareerd, waardoor de cmdlet de methode [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) kan aanroepen voordat de cmdlet de actie uitvoert. Als de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) wordt geretourneerd `false` , mag de actie niet worden uitgevoerd. Zie [verzoeken om bevestiging](./requesting-confirmation-from-cmdlets.md)voor meer informatie over de bevestigings aanvragen die zijn gegenereerd door de aanroep [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) .

De `Confirm` `WhatIf` para meters en cmdlets zijn alleen beschikbaar voor cmdlets die ondersteuning bieden voor [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -aanroepen.

## <a name="example"></a>Voorbeeld

De volgende klassedefinitie maakt gebruik van het cmdlet-kenmerk om de .NET Framework klasse te identificeren voor een **Get-proc-** cmdlet waarmee informatie wordt opgehaald over de processen die worden uitgevoerd op de lokale computer.

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

Zie [GetProc-zelf studie](./getproc-tutorial.md)voor meer informatie over de cmdlet **Get-proc** .

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
