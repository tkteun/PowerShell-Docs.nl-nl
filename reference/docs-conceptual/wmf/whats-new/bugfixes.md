---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Oplossingen voor bugs in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145206"
---
# <a name="bug-fixes-in-wmf-51"></a>Oplossingen voor bugs in WMF 5.1

## <a name="bug-fixes"></a>Opgeloste fouten

De volgende belang rijke fouten zijn opgelost in WMF 5,1:

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a>Automatische detectie van module honoreert PSModulePath volledig

Module-automatische detectie (modules automatisch laden zonder expliciete import-module bij het aanroepen van een opdracht) werd geïntroduceerd in WMF 3. Power shell is ingecheckt voor opdrachten `$PSHome\Modules` in voordat `$env:PSModulePath`u gaat gebruiken.

WMF 5,1 wijzigt dit gedrag `$env:PSModulePath` volledig. Dit maakt het mogelijk voor een door de gebruiker gemaakte module waarmee opdrachten worden gedefinieerd die worden verschaft `Get-ChildItem`door Power shell (bijvoorbeeld) om automatisch te worden geladen en de ingebouwde opdracht correct te vervangen.

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a>Bestands omleiding heeft geen vaste codes meer-Unicode-code ring

In alle eerdere versies van Power shell was het onmogelijk om de bestands codering te beheren die wordt gebruikt door de omleidings operator voor bestanden.

Vanaf de WMF 5,1 kunt u nu de bestands codering van de omleiding wijzigen door de instelling `$PSDefaultParameterValues`:

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a>Er is een regressie voor het openen van leden van System. reflectie. type info opgelost

Een regressie geïntroduceerd in WMF 5,0 om toegang te krijgen tot `System.Reflection.RuntimeType`leden van, `[int].ImplementedInterfaces`bijvoorbeeld. Deze fout is opgelost in WMF 5,1.

### <a name="fixed-some-issues-with-com-objects"></a>Er zijn problemen opgelost met COM-objecten

WMF 5,0 heeft een nieuwe COM-Binder geïntroduceerd voor het aanroepen van methoden voor COM-objecten en het openen van eigenschappen van COM-objecten. Deze nieuwe Binder verbetert de prestaties aanzienlijk, maar heeft ook een aantal bugs geïntroduceerd die zijn verholpen in WMF 5,1.

#### <a name="argument-conversions-were-not-always-performed-correctly"></a>Argument conversies zijn niet altijd correct uitgevoerd

In het volgende voor beeld:

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

De methode **SendKeys** verwacht een teken reeks, maar Power Shell heeft het teken niet omgezet naar een teken reeks, waardoor de conversie naar **IDispatch:: Invoke**wordt uitgesteld, waarbij **VariantChangeType** wordt gebruikt om de conversie uit te voeren. In dit voor beeld heeft dit ertoe geleid dat de sleutels ' 1 ', ' 7 ' en ' 3 ' worden verzonden in plaats van het verwachte **volume. Mute** -sleutel.

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a>Het inventariseren van COM-objecten wordt niet altijd correct verwerkt

Power shell inventariseert normaal gesp roken de meeste overzichts objecten, maar een regressie geïntroduceerd in WMF 5,0 heeft de inventarisatie van COM-objecten die IEnumerable implementeren, voor komen. Bijvoorbeeld:

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

In het bovenstaande voor beeld heeft WMF 5,0 de **Scripting. Dictionary** onjuist geschreven in de pijp lijn in plaats van de sleutel-waardeparen te inventariseren.

### <a name="ordered-was-not-allowed-inside-classes"></a>[gelast] is niet toegestaan binnen klassen

WMF 5,0 heeft klassen met validatie van type letterlijke waarden in klassen geïntroduceerd. `[ordered]`het lijkt op een letterlijke type, maar is geen echt .NET-type. WMF 5,0 heeft foutief een fout `[ordered]` gerapporteerd binnen een klasse:

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a>Help-informatie over onderwerpen met meerdere versies werkt niet

Als er meerdere versies van een module zijn geïnstalleerd, moet u vóór WMF 5,1 meerdere onderwerpen retour neren zonder een duidelijke manier om de werkelijke `help about_PSReadline` Help te bekijken, als u meer dan een Help-onderwerp, bijvoorbeeld about_PSReadline, gebruikt.

WMF 5,1 corrigeert dit door de Help voor de meest recente versie van het onderwerp te retour neren.

`Get-Help`biedt geen manier om de versie op te geven waarvoor u hulp nodig hebt. Om dit te omzeilen, gaat u naar de map modules en bekijkt u de Help rechtstreeks met een hulp programma zoals uw favoriete editor.

### <a name="powershellexe-reading-from-stdin-stopped-working"></a>het lezen van Power shell. exe van STDIN werkt niet meer

Klanten gebruiken `powershell -command -` systeem eigen apps om Power shell uit te voeren in het script via stdin. Dit is helaas verbroken door andere wijzigingen in de console-host.

Dit probleem is opgelost in versie 5,1 van de jubileum update van Windows 10.

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a>Power shell. exe maakt pieken in het CPU-gebruik bij het opstarten

Power shell gebruikt een WMI-query om te controleren of deze is gestart via groepsbeleid om te voor komen dat de aanmelding vertraging veroorzaakt. De WMI-query beëindigt het injecteren van tzres. MUI. dll in elk proces op het systeem, omdat de WMI **Win32_Process** -klasse de lokale tijdzone gegevens probeert op te halen. Dit resulteert in een grote CPU-piek in **WMIPRVSE** (de host van de WMI-provider). Correctie is het gebruik van Win32 API-aanroepen om dezelfde informatie te verkrijgen in plaats van WMI te gebruiken.
