---
title: Toevoegen van aliassen, jokertekens, en voor het tot Cmdlet-Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: db664e589f625855b5a33a02c522d6b238ad2810
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075253"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a>Aliassen, jokertekenuitbreiding en Help toevoegen aan cmdlet-parameters

In deze sectie wordt beschreven hoe u aliassen, jokertekens, toevoegen en Help berichten naar de parameters van de cmdlet Stop-Proc (beschreven in [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md)).

Deze cmdlet Stop-Proc probeert te beëindigen van processen die worden opgehaald met de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)).

Onderwerpen in deze sectie bevatten het volgende:

- [De Cmdlet definiëren](#Defining-the-Cmdlet)

- [Parameters voor aanpassing van het systeem definiëren](#Defining-Parameters-for-System-Modification)

- [Een Parameteralias definiëren](#Defining-a-Parameter-Alias)

- [Help voor Parameters maken](#Creating-Help-for-Parameters)

- [Invoer verwerken methode te overschrijven](#Overriding-an-Input-Processing-Method)

- [Ondersteunende jokertekens](#Supporting-Wildcard-Expansion)

- [Voorbeeld van code](#Defining-a-Parameter-Alias)

- [Objecttype definiëren en opmaak](#Define-Object-Types-and-Formatting)

- [Het bouwen van de Cmdlet](#Building-the-Cmdlet)

- [Testen van de Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a>De Cmdlet definiëren

De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren. Omdat u een cmdlet als u wilt wijzigen van het systeem schrijft, moet deze dienovereenkomstig worden genoemd. Omdat deze cmdlet systeemprocessen stopt, wordt de term 'Stop', die is gedefinieerd door de [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) klasse, met het zelfstandig naamwoord 'Proc' om aan te geven van proces. Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

De volgende code wordt de klassedefinitie van deze cmdlet Stop-Proc.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a>Parameters voor aanpassing van het systeem definiëren

De cmdlet moet parameters definiëren die ondersteuningssysteem wijzigingen en feedback van gebruikers. De cmdlet moet definiëren een `Name` parameter of een vergelijkbare zodat de cmdlet kunnen wijzigen van het systeem door een soort id. Bovendien de cmdlet moet definiëren de `Force` en `PassThru` parameters. Zie voor meer informatie over deze parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="defining-a-parameter-alias"></a>Een Parameteralias definiëren

Een parameteralias is een alternatieve naam of een goed gedefinieerde 1- of 2 letter korte naam voor een cmdlet-parameter. In beide gevallen is het doel van het gebruik van aliassen voor het vereenvoudigen van de vermelding van de gebruiker vanaf de opdrachtregel. Windows PowerShell ondersteunt aliassen via de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk, die gebruikmaakt van de syntaxis van de declaratie [Alias()].

De volgende code toont hoe een alias is toegevoegd aan de `Name` parameter.

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

Naast het gebruik van de [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) kenmerk, de Windows PowerShell-runtime voert gedeeltelijke namen matchen, zelfs als er geen aliassen zijn opgegeven. Bijvoorbeeld, als de cmdlet heeft een `FileName` parameter en dat is de enige parameter die met begint `F`, de gebruiker kan invoeren `Filename`, `Filenam`, `File`, `Fi`, of `F` en nog steeds herkent de vermelding als de `FileName` parameter.

## <a name="creating-help-for-parameters"></a>Help voor Parameters maken

Windows PowerShell kunt u Help-informatie voor cmdlet-parameters maken. Doe dit voor elke parameter die wordt gebruikt voor feedback op systeem wijzigen en de gebruiker. Voor elke parameter voor de ondersteuning van Help-informatie, kunt u instellen de `HelpMessage` kenmerken van het sleutelwoord in de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaratie van het kenmerk. Dit trefwoord definieert de tekst die moet worden weergegeven voor de gebruiker voor hulp bij het gebruik van de parameter. U kunt ook instellen de `HelpMessageBaseName` sleutelwoord voor het identificeren van de naam op van een resource moet worden gebruikt voor het bericht. Als u dit sleutelwoord instelt, moet u ook instellen de `HelpMessageResourceId` trefwoord om op te geven van de resource-id.

De volgende code uit deze cmdlet Stop-Proc definieert de `HelpMessage` kenmerk trefwoord voor de `Name` parameter.

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

## <a name="overriding-an-input-processing-method"></a>Invoer verwerken methode te overschrijven

De cmdlet moet verwerken van methode invoer overschrijven, dit is meestal [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord). Bij het wijzigen van het systeem, de cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) en [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methoden waarmee de gebruiker om feedback te geven voordat er een wijziging is aangebracht. Zie voor meer informatie over deze methoden, [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).

## <a name="supporting-wildcard-expansion"></a>Ondersteunende jokertekens

Als u wilt toestaan dat de selectie van meerdere objecten, uw cmdlet kunt gebruiken de [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) en [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) klassen voor jokertekens worden uitbreiding voor de parameter invoeren. Er zijn voorbeelden van jokertekenpatronen lsa * \*.txt en [a-c]\*. Gebruik de back-aanhalingsteken (') als een escape-teken als het patroon bevat een teken letterlijk moet worden gebruikt.

Wildcard-uitbreidingen van bestands- en padnamen zijn voorbeelden van veelvoorkomende scenario's waarin de cmdlet ondersteuning voor het pad invoer toestaan kunt wanneer de selectie van meerdere objecten vereist is. Gebruikelijk is in het bestandssysteem, waarbij een gebruiker wil zien van alle bestanden die zich bevinden in de huidige map.

U hoeft slechts zelden een aangepaste jokertekens patroon overeenkomende implementatie. In dit geval moet de cmdlet ondersteuning voor de volledige POSIX-1003.2, 3,13 specificatie voor jokertekens of de volgende vereenvoudigde subset:

- **Vraagteken (?).** Komt overeen met een willekeurig teken op de opgegeven locatie.

- **Sterretje (\*).** Komt overeen met nul of meer tekens vanaf de opgegeven locatie.

- **Open haakje sluiten ([]).** Introduceert een haakje-expressie voor het patroon die tekens of een bereik met tekens kan bevatten. Als een bereik is vereist, wordt een koppelteken (-) gebruikt om aan te geven van het bereik.

- **Sluiten haak sluiten (]).** Een patroon haakje-expressie wordt beëindigd.

- **Back-aanhalingsteken (') als escape-teken.** Geeft aan dat het volgende teken letterlijk moet worden genomen. Let erop dat bij het opgeven van de back-aanhalingsteken vanaf de opdrachtregel (in plaats van via een programma opgeven), het back-offerte escape-teken moet worden twee keer opgegeven.

> [!NOTE]
> Zie voor meer informatie over de jokertekenpatronen [ondersteunt jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).

De volgende code laat zien hoe u jokertekens opties instellen en definiëren van het jokerteken-patroon gebruikt voor het oplossen van de `Name` parameter voor deze cmdlet.

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

De volgende code toont hoe u kunt testen of de procesnaam overeenkomt met het patroon gedefinieerde jokertekens. U ziet dat in dit geval als de procesnaam komt niet overeen met het patroon, de cmdlet blijft op de naam van de volgende procedure.

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [StopProcessSample03 voorbeeld](./stopprocesssample03-sample.md).

## <a name="define-object-types-and-formatting"></a>Definieer objecttypen en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten. Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet, moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel. We gaan de voorbeeld-cmdlet Stop-Proc testen. Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Start Windows PowerShell en Stop-procedure gebruiken om te stoppen van een proces met behulp van de procesnaam-alias voor de `Name` parameter.

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Controleer de volgende vermelding op de opdrachtregel. Omdat de parameter Name verplicht is, wordt u gevraagd voor het. Invoeren '!? " Hiermee geeft u de help-tekst die is gekoppeld aan de parameter.

    ```powershell
    PS> stop-proc
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- Maak nu de volgende vermelding te beëindigen alle processen die overeenkomen met het patroon jokerteken ' * Opmerking\*'. U wordt gevraagd voordat elk proces dat overeenkomt met het patroon wordt gestopt.

    ```powershell
    PS> stop-proc -Name *note*
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zie ook

[Maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md)

[Over het maken van een Windows PowerShell-Cmdlet](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Objecttypen uitbreiden en opmaak](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Ondersteuning van jokertekens in de Cmdlet-Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
