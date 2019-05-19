---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Oplossingen voor problemen in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856208"
---
# <a name="bug-fixes-in-wmf-51"></a>Oplossingen voor problemen in WMF 5.1

## <a name="bug-fixes"></a>Opgeloste fouten

De volgende belangrijke fouten zijn verholpen in WMF 5.1:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>Module-auto-discovery respecteert volledig PSModulePath

Module-auto-discovery (modules laden zonder een expliciete Import-Module bij het aanroepen van een opdracht automatisch) werd geïntroduceerd in WMF 3. Wanneer geïntroduceerd, PowerShell gecontroleerd op opdrachten in `$PSHome\Modules` voordat u `$env:PSModulePath`.

WMF 5.1 verandert dit gedrag in acht neemt `$env:PSModulePath` volledig. Hiermee kunt u een door de gebruiker opgestelde module waarmee wordt gedefinieerd door de PowerShell-opdrachten (bijvoorbeeld `Get-ChildItem`) automatisch geladen en de ingebouwde opdracht correct te overschrijven.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Omleiding van het bestand niet langer vastgelegd-Unicode-codering

In alle eerdere versies van PowerShell is het niet mogelijk om te bepalen de bestandscodering die worden gebruikt door het bestand omleidingsoperator.

Beginnen met WMF 5.1, kunt u nu wijzigen de bestandscodering van omleiding door in te stellen `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Er is een regressie bij het openen van leden van System.Reflection.TypeInfo opgelost

Een regressie die is geïntroduceerd in WMF 5.0 verbroken toegang tot leden van `System.Reflection.RuntimeType`, bijvoorbeeld `[int].ImplementedInterfaces`. Deze fout is verholpen in WMF 5.1.

### <a name="fixed-some-issues-with-com-objects"></a>Sommige problemen opgelost met COM-objecten

WMF 5.0 geïntroduceerd voor een nieuwe COM binder voor aanroepen methoden van COM-objecten en toegang tot eigenschappen van COM-objecten. Deze nieuwe binder prestaties aanzienlijk verbeterd, maar ook enkele problemen die zijn verholpen in WMF 5.1 geïntroduceerd.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argument conversies zijn niet altijd correct uitgevoerd

In het volgende voorbeeld:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

De **SendKeys** methode verwacht een tekenreeks, maar PowerShell heeft niet de tekens naar een tekenreeks converteren, het uitstellen van de conversie naar **IDispatch::Invoke**, welke toepassingen **VariantChangeType**voor de conversie uitvoeren. In dit voorbeeld dit leidde tot het verzenden van de sleutels '1', '7' en '3' in plaats van de verwachte **Volume.Mute** sleutel.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Inventariseerbare COM-objecten niet altijd correct worden verwerkt

PowerShell normaal gesproken de meeste invoeroverzicht objecten worden opgesomd, maar een regressie die is geïntroduceerd in WMF 5.0 niet meer aanmelden bij de inventarisatie van COM-objecten die als IEnumerable is geïmplementeerd. Bijvoorbeeld:

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

In het bovenstaande voorbeeld WMF 5.0 onjuist geschreven de **Scripting.Dictionary** aan de pijplijn in plaats van het inventariseren van de sleutel/waarde-paren.

### <a name="ordered-was-not-allowed-inside-classes"></a>[geordende] is niet toegestaan in klassen

WMF 5.0 geïntroduceerd klassen met validatie van het type letterlijke waarden in de klassen. `[ordered]` ziet eruit als een letterlijke type, maar is geen waar .NET-type. WMF 5.0 heeft een fout niet juist gerapporteerd op `[ordered]` binnen een klasse:

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

`Get-Help` biedt geen een manier om op te geven welke versie u hulp wilt. Om dit te omzeilen, Ga naar de map modules en de Help rechtstreeks met een hulpprogramma zoals uw favoriete editor.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>lezen van STDIN PowerShell.exe niet meer werkt

Klanten gebruiken `powershell -command -` van native apps uit te voeren PowerShell doorgegeven in het script via STDIN Helaas is verbroken door andere wijzigingen in de consolehost.

Dit probleem wordt opgelost voor versie 5.1 in Windows 10 Jubileumupdate.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>PowerShell.exe maakt piek in CPU-gebruik bij het opstarten

PowerShell maakt gebruik van een WMI-query om te controleren of deze werd gestart via Groepsbeleid om te voorkomen dat vertraging veroorzaken bij aanmelden. De WMI-query eindigt tzres.mui.dll injecteren in elk proces op het systeem sinds de WMI **Win32_Process** klasse probeert op te halen van informatie over de lokale tijdzone. Dit resulteert in een grote piek CPU in **wmiprvse** (de WMI-provider host). Oplossing is het gebruik van Win32 API-aanroepen naar dezelfde gegevens in plaats van WMI ophalen.
