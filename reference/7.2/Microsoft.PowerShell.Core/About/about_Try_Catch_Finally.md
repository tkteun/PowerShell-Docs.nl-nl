---
description: Hierin wordt beschreven hoe u de `Try` -, `Catch` -en- `Finally` blokken gebruikt voor het afhandelen van afsluit fouten.
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705643"
---
# <a name="about-try-catch-finally"></a>Over try catch finally

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt beschreven hoe u de `Try` -, `Catch` -en- `Finally` blokken gebruikt voor het afhandelen van afsluit fouten.

## <a name="long-description"></a>LANGE BESCHRIJVING

Gebruik `Try` , `Catch` , en `Finally` blokkeert om te reageren op afsluit fouten in scripts of af te handelen. De `Trap` instructie kan ook worden gebruikt voor het afhandelen van afsluit fouten in scripts. Zie [about_Trap](about_Trap.md)voor meer informatie.

Een afsluit fout zorgt ervoor dat een instructie niet kan worden uitgevoerd. Als Power shell geen afsluit fout op een of andere manier verwerkt, stopt Power shell ook met het uitvoeren van de functie of het script met behulp van de huidige pijp lijn. In andere talen, zoals C \# , worden afsluit fouten aangeduid als uitzonde ringen.

Gebruik het `Try` blok om een sectie te definiëren van een script waarin Power shell op fouten moet worden gecontroleerd. Als er een fout optreedt in het `Try` blok, wordt de fout eerst opgeslagen in de `$Error` Automatische variabele. Power shell zoekt vervolgens naar een `Catch` blok om de fout af te handelen. Als de `Try` instructie geen overeenkomend blok heeft `Catch` , gaat Power shell door met zoeken naar een geschikt `Catch` blok of een `Trap` instructie in de bovenliggende bereiken. Wanneer een `Catch` blok is voltooid of als er geen geschikt `Catch` blok of een `Trap` instructie wordt gevonden, `Finally` wordt het blok uitgevoerd. Als de fout niet kan worden verwerkt, wordt de fout naar de fout stroom geschreven.

Een `Catch` blok kan opdrachten bevatten voor het volgen van de fout of voor het herstellen van de verwachte stroom van het script. Een `Catch` blok kan opgeven welke fout typen er worden onderschept. Een `Try` instructie kan meerdere `Catch` blokken bevatten voor verschillende soorten fouten.

Een `Finally` blok kan worden gebruikt om resources vrij te maken die niet langer nodig zijn voor uw script.

`Try`, en `Catch` `Finally` lijken op de `Try` , `Catch` en `Finally` tref woorden die worden gebruikt in de \# programmeer taal C.

### <a name="syntax"></a>SYNTAXIS

Een `Try` instructie bevat een `Try` blok, nul of meer `Catch` blokken en nul of één `Finally` blok. Een `Try` instructie moet ten minste één `Catch` blok of één `Finally` blok bevatten.

Hieronder ziet u de `Try` blok syntaxis:

```powershell
try {<statement list>}
```

Het `Try` tref woord wordt gevolgd door een lijst met overzichten tussen accolades. Als er een afsluit fout optreedt terwijl de instructies in de lijst met overzichten worden uitgevoerd, wordt het fout object door het script door gegeven van het `Try` blok naar een geschikt `Catch` blok.

Hieronder ziet u de `Catch` blok syntaxis:

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

Fout typen worden tussen haakjes weer gegeven. De buitenste haken geven aan dat het element optioneel is.

Het `Catch` sleutel woord wordt gevolgd door een optionele lijst met fout type specificaties en een instructie lijst. Als er een afsluit fout optreedt in het `Try` blok, zoekt Power shell naar een geschikt `Catch` blok. Als er een wordt gevonden, worden de instructies in het `Catch` blok uitgevoerd.

In het `Catch` blok kunnen een of meer fout typen worden opgegeven. Een fout type is een Microsoft .NET Framework-uitzonde ring of een uitzonde ring die is afgeleid van een .NET Framework uitzonde ring. Een `Catch` blok behandelt fouten van de opgegeven uitzonderings klasse .NET Framework of van een klasse die is afgeleid van de opgegeven klasse.

Als in een `Catch` blok een fout type wordt opgegeven, wordt het `Catch` type fout door dat blok afgehandeld. Als `Catch` voor een blok geen fout type wordt opgegeven, wordt in dat blok een `Catch` fout verwerkt die in het blok is aangetroffen `Try` . Een `Try` instructie kan meerdere `Catch` blokken bevatten voor de verschillende opgegeven fout typen.

Hieronder ziet u de `Finally` blok syntaxis:

```powershell
finally {<statement list>}
```

Het `Finally` sleutel woord wordt gevolgd door een lijst met overzichten die wordt uitgevoerd telkens wanneer het script wordt uitgevoerd, zelfs als de `Try` instructie zonder fouten is uitgevoerd of als er een fout is opgetreden in een `Catch` instructie.

Houd er rekening mee dat de pijp lijn wordt gestopt door op <kbd>CTRL</kbd> + <kbd>C</kbd> te drukken. Objecten die naar de pijp lijn worden verzonden, worden niet weer gegeven als uitvoer. Als u dus een instructie opneemt die moet worden weer gegeven, zoals ' finally Block is run ', wordt deze niet weer gegeven nadat u op <kbd>CTRL</kbd> + <kbd>C</kbd>hebt gedrukt, zelfs als het `Finally` blok is uitgevoerd.

### <a name="catching-errors"></a>OPVANGEN VAN FOUTEN

In het volgende voorbeeld script ziet u een `Try` blok met een `Catch` blok:

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

Het `Catch` tref woord moet direct volgen op het `Try` blok of een ander `Catch` blok.

Power shell herkent "NonsenseString" niet als cmdlet of ander item.
Als u dit script uitvoert, wordt het volgende resultaat geretourneerd:

```powershell
An error occurred.
```

Wanneer het script zich voordoet als ' NonsenseString ', treedt er een afsluit fout op. De `Catch` blok kering van de fout wordt door de lijst met instructies in het blok uit te voeren.

### <a name="using-multiple-catch-statements"></a>MEERDERE CATCH-INSTRUCTIES GEBRUIKEN

Een `Try` instructie kan een wille keurig aantal `Catch` blokken bevatten. Het volgende script heeft bijvoorbeeld een `Try` blok dat wordt gedownload `MyDoc.doc` en bevat twee `Catch` blokken:

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

Het eerste `Catch` blok behandelt fouten van het type **System .net. WebException** en **System. io. IOException** . In het tweede `Catch` blok is geen fout type opgegeven. Het tweede `Catch` blok verwerkt alle andere afsluit fouten die optreden.

Power shell komt overeen met fout typen op overname. Een `Catch` blok behandelt fouten van de opgegeven uitzonderings klasse .NET Framework of van een klasse die is afgeleid van de opgegeven klasse. Het volgende voor beeld bevat een `Catch` blok dat de fout ' opdracht niet gevonden ' onderschept:

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

Het opgegeven fout type **CommandNotFoundException**, neemt over van het type **System.SystemException** . In het volgende voor beeld wordt ook een niet-gevonden opdracht onderschept:

```powershell
catch [System.SystemException] {"Base Exception" }
```

Dit `Catch` blok verwerkt de fout ' opdracht niet gevonden ' en andere fouten die van het type **SystemException** overnemen.

Als u een fout klasse en een van de afgeleide klassen opgeeft, plaatst u het `Catch` blok voor de afgeleide klasse vóór het `Catch` blok voor de algemene klasse.

### <a name="using-traps-in-a-try-catch"></a>Traps gebruiken in een try-catch

Als er een afsluit fout optreedt in een `Try` blok met een `Trap` gedefinieerde binnen het `Try` blok, zelfs als er een overeenkomend `Catch` blok is, `Trap` neemt de instructie de controle.

Als een `Trap` bestaat in een hoger blok dan het `Try` , en er is geen overeenkomend `Catch` blok binnen het huidige bereik, `Trap` wordt de controle uitgevoerd, zelfs als een bovenliggend bereik een overeenkomend `Catch` blok heeft.

### <a name="accessing-exception-information"></a>UITZONDERINGS INFORMATIE OPENEN

Binnen een `Catch` blok kan de huidige fout worden geopend met `$_` , ook wel bekend als `$PSItem` . Het object is van het type **ErrorRecord**.

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

Als u dit script uitvoert, wordt het volgende resultaat geretourneerd:

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

Er zijn aanvullende eigenschappen die kunnen worden geopend, zoals **ScriptStackTrace**, **Exception** en **Error Details**.  Als we het script bijvoorbeeld wijzigen in het volgende:

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

Het resultaat is vergelijkbaar met:

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a>RESOURCES VRIJMAKEN DOOR TEN SLOTTE TE GEBRUIKEN

Als u resources wilt vrijmaken die door een script worden gebruikt, voegt u een `Finally` blok toe na de `Try` en- `Catch` blokken. De `Finally` blok-instructies worden uitgevoerd, ongeacht of er `Try` een afsluit fout is opgetreden in het blok. Power Shell voert het `Finally` blok uit voordat het script wordt beëindigd of voordat het huidige blok buiten het bereik valt.

Een `Finally` blok wordt zelfs uitgevoerd als u <kbd>CTRL</kbd> + <kbd>C</kbd> gebruikt om het script te stoppen. Een `Finally` blok wordt ook uitgevoerd als het sleutel woord exit het script in een `Catch` blok stopt.

### <a name="see-also"></a>ZIE OOK

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

