---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Oplossingen voor problemen in WMF 5.1
ms.openlocfilehash: 1e46d6d0419b3497450e6eaddbaa47456b004691
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222187"
---
# <a name="bug-fixes-in-wmf-51"></a>Oplossingen voor problemen in WMF 5.1#

## <a name="bug-fixes"></a>Oplossingen voor problemen ##

De volgende opmerkelijke fouten zijn verholpen in WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>Automatische detectie van module respecteert volledig `$env:PSModulePath` ###

Module auto-discovery (modules laden zonder een expliciete Import-Module bij het aanroepen van een opdracht automatisch) is geïntroduceerd in WMF 3.
Wanneer geïntroduceerd, PowerShell gecontroleerd voor opdrachten in `$PSHome\Modules` voordat u `$env:PSModulePath`.

Dit gedrag te houden van WMF 5.1 gewijzigd `$env:PSModulePath` volledig.
Hiermee kunt u een door de gebruiker opgestelde module die wordt gedefinieerd door PowerShell-opdrachten (bijvoorbeeld `Get-ChildItem`) automatisch geladen en de ingebouwde opdracht correct te overschrijven.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Omleiding van bestand geen langer harde-codes `-Encoding Unicode` ###

In alle eerdere versies van PowerShell is het onmogelijk om te bepalen de bestandscodering gebruikt door de omleidingsoperator van bestand bijvoorbeeld `Get-ChildItem > out.txt` omdat PowerShell toegevoegd `-Encoding Unicode`.

Beginnen met WMF 5.1, kunt u nu wijzigen de bestandscodering van omleiding door in te stellen `$PSDefaultParameterValues`:

```
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Een regressie bij het openen van de leden van vast `System.Reflection.TypeInfo` ###

Een regressie geïntroduceerd in WMF 5.0 heeft toegang tot leden van `System.Reflection.RuntimeType`, bijvoorbeeld `[int].ImplementedInterfaces`.
Deze fout is verholpen in WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Sommige problemen opgelost met COM-objecten ###

WMF 5.0 geïntroduceerd om een nieuw COM-binder voor aanroepen methoden op COM-objecten en toegang tot eigenschappen van de COM-objecten.
Deze nieuwe binder prestaties aanzienlijk verbeterd, maar ook een aantal fouten die zijn vastgesteld in WMF 5.1 geïntroduceerd.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argument conversies zijn niet altijd correct worden uitgevoerd ####

In het volgende voorbeeld:

```
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

De methode SendKeys verwacht een tekenreeks, maar PowerShell is niet geconverteerd de char naar een tekenreeks uitstellende geconverteerd naar een IDispatch::Invoke die VariantChangeType worden gebruikt voor de conversie, wat in dit voorbeeld leidde tot de sleutels '1', '7' en '3' in plaats daarvan verzenden van de verwachte Volume.Mute-sleutel.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Inventariseerbare COM-objecten die niet altijd correct wordt afgehandeld ####

Normaal gesproken inventariseren meeste inventariseerbare objecten PowerShell, maar een regressie geïntroduceerd in WMF 5.0 voorkomen dat de opsomming van COM-objecten die als IEnumerable is geïmplementeerd.  Bijvoorbeeld:

```
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

In het bovenstaande voorbeeld geschreven WMF 5.0 onjuist de Scripting.Dictionary aan de pijplijn in plaats van het inventariseren van de sleutel/waarde-paren.

Dit wijzigen adressen [uitgeven 1752224 op verbinding maken](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` is niet toegestaan in klassen ###

WMF 5.0 geïntroduceerd klassen met de validatie van het type letterlijke waarden in klassen gebruikt.
`[ordered]` ziet eruit als een letterlijke waarde van het type, maar is niet een waar .NET-type.
WMF 5.0 onjuist heeft een fout gerapporteerd op `[ordered]` binnen een klasse:

```
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Help-informatie op over onderwerpen met meerdere versies werkt niet ###

Voordat u WMF 5.1, als u meerdere versies van een module geïnstalleerd had en ze allemaal een help-onderwerp bijvoorbeeld gedeeld about_PSReadline, `help about_PSReadline` meerdere onderwerpen met geen duidelijke manier waarmee u de echte help zou retourneren.

WMF 5.1 corrigeert dit door te retourneren van de help voor de nieuwste versie van het onderwerp.

`Get-Help` biedt geen manier om op te geven welke versie u hulp wilt.
Om dit te voorkomen, navigeer naar de map modules en de hulp rechtstreeks met een hulpprogramma zoals uw favoriete editor weergeven.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>lezen van STDIN PowerShell.exe werkt niet

Klanten gebruiken `powershell -command -` van systeemeigen apps uit te voeren PowerShell doorgeeft in het script via STDIN helaas dit is verbroken vanwege een andere wijzigingen van de console-host.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe maakt piek in CPU-gebruik bij het opstarten

PowerShell maakt gebruik van een WMI-query om te controleren of het via Groepsbeleid om te voorkomen dat de vertraging veroorzaakt in de aanmelding is gestart.
De WMI-query belandt tzres.mui.dll injecteren in elk proces op het systeem omdat de Win32_Process WMI-klasse probeert op te halen van de lokale tijdzone-informatie.
Dit resulteert in een grote CPU piek in de wmiprvse (de WMI-provider host).
FIX is het gebruik van Win32-API-aanroepen dezelfde informatie in plaats van WMI ophalen.
