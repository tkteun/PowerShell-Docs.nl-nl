---
description: Introduceert geavanceerde functies waarmee u cmdlets kunt maken met behulp van scripts.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: 53cba129778161d8c44186eb999387e51bb71e50
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252614"
---
# <a name="about-functions-advanced"></a>Over functies Geavanceerd

## <a name="short-description"></a>KORTE BESCHRIJVING
Introduceert geavanceerde functies waarmee u cmdlets kunt maken met behulp van scripts.

## <a name="long-description"></a>LANGE BESCHRIJVING

Een cmdlet is één opdracht die deel uitmaakt van de pijplijn semantiek van Power shell. Dit omvat binaire cmdlets, geavanceerde script functies, CDXML en werk stromen.

Met geavanceerde functies kunt u cmdlets maken die zijn geschreven als een Power shell-functie. Geavanceerde functies maken het gemakkelijker om cmdlets te maken zonder dat ze een binaire cmdlet hoeven te schrijven en te compileren. Binaire cmdlets zijn .NET-klassen die zijn geschreven in een .NET-taal, zoals C#.

Geavanceerde functies gebruiken het `CmdletBinding` kenmerk om ze te identificeren als functies die fungeren als-cmdlets. Het `CmdletBinding` kenmerk is vergelijkbaar met het cmdlet-kenmerk dat wordt gebruikt in gecompileerde cmdlet-klassen om de klasse als een cmdlet te identificeren. Zie [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)voor meer informatie over dit kenmerk.

In het volgende voor beeld ziet u een functie die een naam accepteert en vervolgens een begroeting afdrukt met de opgegeven naam. U ziet ook dat deze functie een naam definieert die een paar woorden (verzenden) en een zelfstandig naam woord (Greeting) bevat, zoals het combi neren van woorden en zelfstandigen van een gecompileerde cmdlet. Functies zijn echter niet vereist voor het maken van een naam van een woorden groep.

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

De para meters van de functie worden gedeclareerd met behulp van het parameter kenmerk.
Dit kenmerk kan alleen worden gebruikt, of het kan worden gecombineerd met het alias kenmerk of met verschillende kenmerken voor de validatie van de para meters. Zie [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)voor meer informatie over het declareren van para meters (inclusief dynamische para meters die tijdens runtime worden toegevoegd).

Het werkelijke werk van de functie Previous wordt uitgevoerd in het proces blok, wat gelijk is aan de methode ProcessingRecord die wordt gebruikt door gecompileerde cmdlets voor het verwerken van de gegevens die worden door gegeven aan de cmdlet. Dit blok, samen met de begin-en eind blokken, wordt beschreven in het onderwerp [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) .

Geavanceerde functies verschillen op de volgende manieren van gecompileerde cmdlets:

- Met een geavanceerde functie parameter binding wordt geen uitzonde ring gegenereerd wanneer een matrix met teken reeksen is gebonden aan een Boole-para meter.
- Het kenmerk validate en het kenmerk ValidatePattern kunnen geen benoemde para meters door geven.
- Geavanceerde functies kunnen niet worden gebruikt in trans acties.

## <a name="see-also"></a>ZIE OOK

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
