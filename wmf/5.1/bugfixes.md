---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Oplossingen voor problemen in WMF 5.1
ms.openlocfilehash: f53fc40b79a3906ac2025b0eff342c0705b82655
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085045"
---
# <a name="bug-fixes-in-wmf-51"></a>Oplossingen voor problemen in WMF 5.1

## <a name="bug-fixes"></a>Opgeloste fouten

De volgende belangrijke fouten zijn verholpen in WMF 5.1:

### <a name="module-auto-discovery-fully-honors-envpsmodulepath"></a>Module-auto-discovery volledig zich houdt aan `$env:PSModulePath`

Module-auto-discovery (modules laden zonder een expliciete Import-Module bij het aanroepen van een opdracht automatisch) werd geïntroduceerd in WMF 3.
Wanneer geïntroduceerd, PowerShell gecontroleerd op opdrachten in `$PSHome\Modules` voordat u `$env:PSModulePath`.

WMF 5.1 verandert dit gedrag in acht neemt `$env:PSModulePath` volledig.
Hiermee kunt u een door de gebruiker opgestelde module waarmee wordt gedefinieerd door de PowerShell-opdrachten (bijvoorbeeld `Get-ChildItem`) automatisch geladen en de ingebouwde opdracht correct te overschrijven.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Omleiding van het bestand niet langer vastgelegd `-Encoding Unicode`

In alle eerdere versies van PowerShell, is het niet mogelijk om te bepalen de bestandscodering die bijvoorbeeld worden gebruikt door de omleidingsoperator bestand `Get-ChildItem > out.txt` omdat PowerShell toegevoegd `-Encoding Unicode`.

Beginnen met WMF 5.1, kunt u nu wijzigen de bestandscodering van omleiding door in te stellen `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Er is een regressie bij het openen van leden van opgelost `System.Reflection.TypeInfo`

Een regressie die is geïntroduceerd in WMF 5.0 verbroken toegang tot leden van `System.Reflection.RuntimeType`, bijvoorbeeld `[int].ImplementedInterfaces`.
Deze fout is verholpen in WMF 5.1.


### <a name="fixed-some-issues-with-com-objects"></a>Sommige problemen opgelost met COM-objecten

WMF 5.0 geïntroduceerd voor een nieuwe COM binder voor aanroepen methoden van COM-objecten en toegang tot eigenschappen van COM-objecten.
Deze nieuwe binder prestaties aanzienlijk verbeterd, maar ook enkele problemen die zijn verholpen in WMF 5.1 geïntroduceerd.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argument conversies zijn niet altijd correct uitgevoerd

In het volgende voorbeeld:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

De methode SendKeys verwacht een tekenreeks, maar PowerShell heeft niet de tekens naar een tekenreeks converteren, het uitstellen van de conversie naar IDispatch::Invoke die VariantChangeType voor de conversie, die in dit voorbeeld heeft geresulteerd in het verzenden van de sleutels '1', '7' en '3' in plaats daarvan gebruikt van de verwachte Volume.Mute-sleutel.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Inventariseerbare COM-objecten niet altijd correct worden verwerkt

PowerShell normaal gesproken de meeste invoeroverzicht objecten worden opgesomd, maar een regressie die is geïntroduceerd in WMF 5.0 niet meer aanmelden bij de inventarisatie van COM-objecten die als IEnumerable is geïmplementeerd.  Bijvoorbeeld:

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

In het bovenstaande voorbeeld geschreven WMF 5.0 ten onrechte de Scripting.Dictionary aan de pijplijn in plaats van het inventariseren van de sleutel/waarde-paren.

Dit ook wijzigen van adressen [uitgeven 1752224 op verbinding maken](https://connect.microsoft.com/PowerShell/feedback/details/1752224)

### <a name="ordered-was-not-allowed-inside-classes"></a>`[ordered]` is niet toegestaan in klassen

WMF 5.0 geïntroduceerd klassen met validatie van het type letterlijke waarden in de klassen.
`[ordered]` ziet eruit als een letterlijke type, maar is geen waar .NET-type.
WMF 5.0 heeft een fout niet juist gerapporteerd op `[ordered]` binnen een klasse:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```


### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Help-informatie op over onderwerpen met meerdere versies werkt niet

Voordat u WMF 5.1, als er meerdere versies van een module geïnstalleerd en ze allemaal een help-onderwerp, bijvoorbeeld gedeeld about_PSReadline, `help about_PSReadline` retourneerde meerdere onderwerpen met geen duidelijke manier om de echte Help-informatie weer te geven.

WMF 5.1 corrigeert dit door te retourneren van de help voor de meest recente versie van het onderwerp.

`Get-Help` biedt geen een manier om op te geven welke versie u hulp wilt.
Om dit te omzeilen, Ga naar de map modules en de Help rechtstreeks met een hulpprogramma zoals uw favoriete editor.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>lezen van STDIN PowerShell.exe niet meer werkt

Klanten gebruiken `powershell -command -` van native apps uit te voeren PowerShell deze door te geven in het script via STDIN helaas Hiermee is verbroken vanwege andere wijzigingen aan de consolehost.

https://windowsserver.uservoice.com/forums/301869-powershell/suggestions/15854689-powershell-exe-command-is-broken-on-windows-10

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe maakt piek in CPU-gebruik bij het opstarten

PowerShell maakt gebruik van een WMI-query om te controleren of deze werd gestart via Groepsbeleid om te voorkomen dat vertraging veroorzaken bij aanmelden.
De WMI-query eindigt tzres.mui.dll injecteren in elk proces op het systeem, omdat de Win32_Process WMI-klasse probeert op te halen van informatie over de lokale tijdzone.
Dit resulteert in een grote piek van de CPU in wmiprvse (de WMI-provider host).
Oplossing is het gebruik van Win32 API-aanroepen naar dezelfde gegevens in plaats van WMI ophalen.
