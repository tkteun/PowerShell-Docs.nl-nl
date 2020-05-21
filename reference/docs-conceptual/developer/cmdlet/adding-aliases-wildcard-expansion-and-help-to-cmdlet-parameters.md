---
title: Aliassen, uitbrei ding van joker tekens en Help voor cmdlet-para meters toevoegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: 7c4098c6c670f22253fe7d463b33e45208d00790
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559995"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Aliassen, jokertekenuitbreiding en Help toevoegen aan cmdlet-parameters

In deze sectie wordt beschreven hoe u aliassen, uitbrei ding van joker tekens en Help-berichten toevoegt aan de para meters van de cmdlet stop-proc (beschreven in [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)).

Deze Stop-proc-cmdlet probeert processen te stoppen die worden opgehaald met de cmdlet Get-proc (beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)).

## <a name="defining-the-cmdlet"></a>De cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Omdat u een cmdlet schrijft om het systeem te wijzigen, moet dit dienovereenkomstig een naam hebben. Omdat met deze cmdlet systeem processen worden gestopt, wordt de term ' Stop ' gebruikt, die door de [System. Management. Automation. Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) -klasse is gedefinieerd, met het zelfstandig naam woord ' proc ' om het proces aan te geven. Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

De volgende code is de klassedefinitie voor deze stop-proc-cmdlet.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Para meters definiëren voor systeem wijziging

Uw cmdlet moet para meters definiëren die systeem wijzigingen en gebruikers feedback ondersteunen. Met de cmdlet wordt een `Name` para meter of gelijkwaardige waarde gedefinieerd, zodat de cmdlet het systeem kan wijzigen met een bepaalde sorteer-id. Daarnaast moet de cmdlet de `Force` `PassThru` para meters en opgeven. Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over deze para meters.

## <a name="defining-a-parameter-alias"></a>Een parameter alias definiëren

Een parameter alias kan een alternatieve naam of een goed gedefinieerde korte naam van één of twee letters zijn voor een cmdlet-para meter. In beide gevallen is het doel van het gebruik van aliassen om de gebruikers vermelding te vereenvoudigen vanaf de opdracht regel. Windows Power shell ondersteunt parameter aliassen via het kenmerk [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) , dat gebruikmaakt van de declaratie syntaxis [alias ()].

De volgende code laat zien hoe een alias wordt toegevoegd aan de `Name` para meter.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

Naast het gebruik van het kenmerk [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) voert de Windows Power shell-runtime gedeeltelijke naam aanpassing uit, zelfs als er geen aliassen zijn opgegeven. Als uw cmdlet bijvoorbeeld een para meter heeft `FileName` en de enige para meter is die begint met `F` , kan de gebruiker `Filename` `Filenam` `File` `Fi` `F` de vermelding als de para meter opgeven,,, of en nog steeds herkennen `FileName` .

## <a name="creating-help-for-parameters"></a>Help voor para meters maken

Met Windows Power shell kunt u Help maken voor cmdlet-para meters. Doe dit voor alle para meters die worden gebruikt voor systeem wijzigingen en gebruikers feedback. Voor elke para meter om hulp te ondersteunen, kunt u het `HelpMessage` sleutel woord kenmerk instellen in de kenmerk declaratie [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Dit sleutel woord definieert de tekst die voor de gebruiker moet worden weer gegeven voor hulp bij het gebruik van de para meter. U kunt ook het `HelpMessageBaseName` tref woord instellen om de basis naam te identificeren van een resource die moet worden gebruikt voor het bericht. Als u dit tref woord hebt ingesteld, moet u ook het `HelpMessageResourceId` tref woord instellen om de resource-id op te geven.

Met de volgende code uit deze stop-proc-cmdlet wordt het `HelpMessage` sleutel woord attribute voor de `Name` para meter gedefinieerd.

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a>Een invoer verwerkings methode overschrijven

De cmdlet moet een invoer verwerkings methode overschrijven. Dit is meestal [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Bij het wijzigen van het systeem moet de cmdlet de methoden [System. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) gebruiken om de gebruiker feedback te geven voordat een wijziging wordt aangebracht. Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over deze methoden.

## <a name="supporting-wildcard-expansion"></a>Ondersteuning voor het uitbreiden van joker tekens

Als u wilt toestaan dat meerdere objecten worden geselecteerd, kan uw cmdlet de klassen [System. Management. Automation. Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) en [System. Management. Automation. Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) gebruiken om ondersteuning voor joker tekens te bieden voor de invoer van para meters. Voor beelden van Joker teken patronen zijn LSA *, \* . txt en [a-c] \* . Gebruik het back-quote teken (') als escape-teken wanneer het patroon een teken bevat dat letterlijk moet worden gebruikt.

Een Joker teken uitbreiding van bestands-en padnamen zijn voor beelden van veelvoorkomende scenario's waarbij de cmdlet mogelijk ondersteuning biedt voor invoer van paden wanneer de selectie van meerdere objecten is vereist. Een veelvoorkomend geval is in het bestands systeem, waarbij een gebruiker alle bestanden in de huidige map wil weer geven.

U moet een aangepaste implementatie van Joker teken patronen die slechts zelden overeenkomen, hebben. In dit geval moet uw cmdlet de volledige POSIX 1003,2, 3,13 specificatie voor de uitbrei ding van het Joker teken of de volgende vereenvoudigde subset ondersteunen:

- **Vraag teken (?).** Komt overeen met een teken op de opgegeven locatie.

- **Asterisk ( \* ).** Komt overeen met nul of meer tekens, te beginnen bij de opgegeven locatie.

- **Haakje openen ([).** Introduceert een patroon rechte haak expressie die tekens of een reeks tekens kan bevatten. Als een bereik vereist is, wordt een koppel teken (-) gebruikt om het bereik aan te geven.

- **Haakje sluiten (]).** Hiermee wordt een expressie voor een patroon haak afgesloten.

- **Escape teken voor back-quote (').** Geeft aan dat het volgende teken letterlijk moet worden genomen. Houd er rekening mee dat wanneer u het nummer van de back-quote opgeeft vanaf de opdracht regel (in plaats van het programma op te geven), het escape-teken voor de back-quote twee keer moet worden opgegeven.

> [!NOTE]
> Zie [ondersteuning voor joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)voor meer informatie over Joker teken patronen.

De volgende code laat zien hoe u opties voor joker tekens instelt en het Joker teken definieert dat wordt gebruikt voor het omzetten van de `Name` para meter voor deze cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

De volgende code laat zien hoe u kunt testen of de proces naam overeenkomt met het gedefinieerde Joker teken patroon. In dit geval, als de proces naam niet overeenkomt met het patroon, blijft de cmdlet de volgende proces naam ophalen.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Code voorbeeld

Zie StopProcessSample03-voor [beeld](./stopprocesssample03-sample.md)voor de volledige C#-voorbeeld code.

## <a name="define-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Windows Power shell geeft informatie door over cmdlets met behulp van .net-objecten. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. We gaan de voor beeld van de cmdlet stop-proc testen. Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.

- Start Windows Power shell en gebruik stop-proc om een proces te stoppen met de alias van de procesnaam voor de `Name` para meter.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Maak de volgende vermelding op de opdracht regel. Omdat de para meter name verplicht is, wordt u gevraagd. Invoeren van "!?" Hiermee wordt de Help-tekst voor de para meter geopend.

    ```powershell
    PS> stop-proc
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Maak nu de volgende vermelding om alle processen te stoppen die overeenkomen met het Joker teken ' * Note \* '. U wordt gevraagd om elk proces dat overeenkomt met het patroon te stoppen.

    ```powershell
    PS> stop-proc -Name *note*
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

    De volgende uitvoer wordt weer gegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zie ook

[Een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)

[Een Windows Power shell-cmdlet maken](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Ondersteuning voor joker tekens in cmdlet-para meters](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
