---
description: Hierin wordt beschreven hoe functies die het `CmdletBinding` kenmerk opgeven, de methoden en eigenschappen kunnen gebruiken die beschikbaar zijn voor gecompileerde cmdlets.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 13a9d7258f1a52d5fcbb2d8c55b91c8d6454452d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706237"
---
# <a name="about-functions-advanced-methods"></a>Over functies geavanceerde methoden

## <a name="short-description"></a>Korte beschrijving

Hierin wordt beschreven hoe functies die het `CmdletBinding` kenmerk opgeven, de methoden en eigenschappen kunnen gebruiken die beschikbaar zijn voor gecompileerde cmdlets.

## <a name="long-description"></a>Lange beschrijving

Functies waarmee het `CmdletBinding` kenmerk wordt opgegeven, hebben toegang tot een aantal methoden en eigenschappen via de `$PSCmdlet` variabele. Deze methoden omvatten de volgende methoden:

- Methoden voor het uitvoeren van invoer waarbij cmdlets worden gebruikt om hun werk uit te voeren.
- De `ShouldProcess` `ShouldContinue` methoden en die worden gebruikt om gebruikers feedback te krijgen voordat een actie wordt uitgevoerd.
- De `ThrowTerminatingError` methode voor het genereren van fout records.
- Verschillende `Write` methoden die verschillende soorten uitvoer retour neren.

Alle methoden en eigenschappen van de klasse **PSCmdlet** zijn beschikbaar voor geavanceerde functies. Zie [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)voor meer informatie.

Zie about_Functions_CmdletBindingAttribute voor meer informatie over het `CmdletBinding` kenmerk [](about_Functions_CmdletBindingAttribute.md).
Zie [System. Management. Automation. cmdlet. CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute)voor de **CmdletBindingAttribute** -klasse.

### <a name="input-processing-methods"></a>Invoer verwerkings methoden

De methoden die in deze sectie worden beschreven, worden de invoer verwerkings methoden genoemd. Voor-functies worden deze drie methoden vertegenwoordigd door de `Begin` , `Process` en, en `End` de blokken van de functie. U hoeft geen van deze blokken in uw functies te gebruiken.

> [!NOTE]
> Deze blokken zijn ook beschikbaar voor functies die niet gebruikmaken van het- `CmdletBinding` kenmerk.

#### <a name="begin"></a>Beginnen

Dit blok wordt gebruikt om de functie optioneel een eenmalige voor verwerking te bieden.
De Power shell-runtime gebruikt de code in dit blok keer voor elk exemplaar van de functie in de pijp lijn.

#### <a name="process"></a>Proces

Dit blok wordt gebruikt om de verwerking van records per record te bieden voor de functie. U kunt een `Process` blok gebruiken zonder de andere blokken te definiëren. Het aantal `Process` blok uitvoeringen is afhankelijk van hoe u de functie gebruikt en wat invoer van de functie ontvangt.

De automatische variabele `$_` of `$PSItem` bevat het huidige object in de pijp lijn voor gebruik in het `Process` blok. De `$input` Automatische variabele bevat een enumerator die alleen beschikbaar is voor functies en script blokken.
Zie [about_Automatic_Variables](about_Automatic_Variables.md)voor meer informatie.

- Als u de functie aan het begin of buiten een pijp lijn aanroept, wordt het `Process` blok eenmaal uitgevoerd.
- Binnen een pijp lijn wordt het `Process` blok eenmaal uitgevoerd voor elk invoer object dat de functie bereikt.
- Als de pijplijn invoer die de functie bereikt, leeg is, wordt het `Process` blok **niet** uitgevoerd.
  - De `Begin` blokken en worden `End` nog steeds uitgevoerd.

> [!IMPORTANT]
> Als een functie parameter is ingesteld om pijplijn invoer te accepteren en er geen `Process` blok is gedefinieerd, mislukt record-voor-record verwerking. In dit geval wordt de functie slechts één keer uitgevoerd, ongeacht de invoer.

#### <a name="end"></a>Beëindigen

Dit blok wordt gebruikt om een eenmalige naverwerking te bieden voor de functie.

In het volgende voor beeld ziet u het overzicht van een functie die een `Begin` blok bevat voor eenmalige voor verwerking, een `Process` blok voor het verwerken van meerdere records en een `End` blok keren voor eenmalige verwerking.

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> Voor het gebruik van een `Begin` of- `End` blok is vereist dat u alle drie de blokken definieert. Wanneer u alle drie de blokken gebruikt, moet alle Power shell-code zich in een van de blokken bevinden.

### <a name="confirmation-methods"></a>Bevestigings methoden

#### <a name="shouldprocess"></a>ShouldProcess

Deze methode wordt aangeroepen om bevestiging van de gebruiker aan te vragen voordat de functie een actie uitvoert waardoor het systeem wordt gewijzigd. De functie kan worden voortgezet op basis van de Booleaanse waarde die door de methode wordt geretourneerd. Deze methode kan alleen worden aangeroepen vanuit het `Process{}` blok van de functie. Het `CmdletBinding` kenmerk moet ook declareren dat de functie ondersteunt `ShouldProcess` (zoals weer gegeven in het vorige voor beeld).

Zie [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess)voor meer informatie over deze methode.

Zie [bevestiging aanvragen](/powershell/scripting/developer/cmdlet/requesting-confirmation)voor meer informatie over het aanvragen van een bevestiging.

#### <a name="shouldcontinue"></a>ShouldContinue

Deze methode wordt aangeroepen om een tweede bevestigings bericht aan te vragen. Deze moet worden aangeroepen wanneer de `ShouldProcess` methode wordt geretourneerd `$true` . Zie [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)voor meer informatie over deze methode.

### <a name="error-methods"></a>Fout methoden

Functies kunnen twee verschillende methoden aanroepen wanneer er fouten optreden. Wanneer er een niet-afsluit fout optreedt, moet de functie de methode aanroepen `WriteError` , die wordt beschreven in de `Write` sectie methoden. Als er een afsluit fout optreedt en de functie kan niet worden voortgezet, moet de `ThrowTerminatingError` methode worden aangeroepen. U kunt ook de- `Throw` instructie voor het beëindigen van fouten en de cmdlet [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) gebruiken voor niet-afsluit fouten.

Zie [System. Management. Automation. cmdlet. ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)voor meer informatie.

### <a name="write-methods"></a>Schrijf methoden

Een functie kan de volgende methoden aanroepen om verschillende typen uitvoer te retour neren.
U ziet dat niet alle uitvoer naar de volgende opdracht in de pijp lijn wordt verplaatst. U kunt ook de verschillende `Write` cmdlets gebruiken, zoals `Write-Error` .

#### <a name="writecommanddetail"></a>WriteCommandDetail

`WriteCommandDetails`Zie [System. Management. Automation. cmdlet. WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)voor meer informatie over de-methode.

#### <a name="writedebug"></a>WriteDebug

Als u informatie wilt opgeven die kan worden gebruikt om problemen met een functie op te lossen, moet u de functie aanroepen met de `WriteDebug` methode. De `WriteDebug` methode geeft fout opsporingsberichten weer voor de gebruiker. Zie [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug)voor meer informatie.

#### <a name="writeerror"></a>WriteError

Functies moeten deze methode aanroepen wanneer er niet-afsluit fouten optreden en de functie is ontworpen om de verwerking van records voort te zetten. Zie [System. Management. Automation. cmdlet. WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)voor meer informatie.

> [!NOTE]
> Als er een afsluit fout optreedt, moet de functie de methode [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) aanroepen.

#### <a name="writeobject"></a>WriteObject

Met de- `WriteObject` methode kan de functie een object verzenden naar de volgende opdracht in de pijp lijn. In de meeste gevallen `WriteObject` is de methode die moet worden gebruikt wanneer de functie gegevens retourneert. Zie [System. Management. Automation. PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)voor meer informatie.

#### <a name="writeprogress"></a>WriteProgress

Voor functies met acties die veel tijd in beslag nemen, kan met deze methode de methode worden aangeroepen, `WriteProgress` zodat de voortgangs gegevens worden weer gegeven. U kunt bijvoorbeeld het percentage voltooid weer geven.
Zie [System. Management. Automation. PSCmdlet. WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress)voor meer informatie.

#### <a name="writeverbose"></a>WriteVerbose

Als u gedetailleerde informatie over de werking van de functie wilt opgeven, moet u de functie aanroepen `WriteVerbose` om uitgebreide berichten weer te geven aan de gebruiker. Standaard worden uitgebreide berichten niet weer gegeven. Zie [System. Management. Automation. PSCmdlet. WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose)voor meer informatie.

#### <a name="writewarning"></a>WriteWarning

Als u informatie wilt geven over voor waarden die onverwachte resultaten kunnen veroorzaken, moet u de functie aanroepen met de methode WriteWarning om waarschuwings berichten voor de gebruiker weer te geven. Standaard worden waarschuwings berichten weer gegeven. Zie [System. Management. Automation. PSCmdlet. WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning)voor meer informatie.

> [!NOTE]
> U kunt ook waarschuwings berichten weer geven door de `$WarningPreference` variabele te configureren of door `Verbose` de `Debug` opdracht regel opties te gebruiken. Zie about_Preference_Variables voor meer informatie over de `$WarningPreference` variabele [](about_Preference_Variables.md).

### <a name="other-methods-and-properties"></a>Andere methoden en eigenschappen

`$PSCmdlet`Zie [System. Management. Automation. PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)voor meer informatie over de andere methoden en eigenschappen die kunnen worden gebruikt via de variabele.

Met de eigenschap [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) kunt u bijvoorbeeld de ingestelde para meter weer geven die wordt gebruikt. Met parameter sets kunt u een functie maken waarmee verschillende taken worden uitgevoerd op basis van de para meters die worden opgegeven wanneer de functie wordt uitgevoerd.

## <a name="see-also"></a>Zie ook

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Preference_Variables](about_Preference_Variables.md)

