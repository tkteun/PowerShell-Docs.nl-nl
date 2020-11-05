---
ms.date: 09/13/2016
ms.topic: reference
title: Parameters toevoegen die opdrachtregelinvoer verwerken
description: Parameters toevoegen die opdrachtregelinvoer verwerken
ms.openlocfilehash: f20469d366330aa787fbc16e4f0a76e67fc7c6db
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354606"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Parameters toevoegen die opdrachtregelinvoer verwerken

De eerste invoer bron voor een cmdlet is de opdracht regel. In dit onderwerp wordt beschreven hoe u een para meter kunt toevoegen aan de `Get-Proc` cmdlet (die wordt beschreven in [uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)), zodat de cmdlet invoer van de lokale computer kan verwerken op basis van expliciete objecten die aan de cmdlet worden door gegeven. `Get-Proc`Met de cmdlet die hier wordt beschreven, worden processen opgehaald op basis van hun namen en wordt vervolgens informatie weer gegeven over de processen bij een opdracht prompt.

## <a name="defining-the-cmdlet-class"></a>De cmdlet-klasse definiëren

De eerste stap bij het maken van de cmdlet is de naam van de cmdlet en de declaratie van de .NET Framework klasse die de cmdlet implementeert. Met deze cmdlet worden proces gegevens opgehaald, zodat de naam van de term ' Get ' is. (Bijna elk soort cmdlet waarmee informatie kan worden opgehaald, kan opdracht regel invoer verwerken.) Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

Hier is de klassen declaratie voor de `Get-Proc` cmdlet. Meer informatie over deze definitie vindt u in [het maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Para meters declareren

Met een cmdlet-para meter kan de gebruiker invoer opgeven voor de cmdlet. In het volgende voor beeld `Get-Proc` `Get-Member` zijn de namen van pijplijn-cmdlets en `MemberType` is een para meter voor de `Get-Member` cmdlet. De para meter heeft het argument ' Property '.

**PS> Get-proc; `get-member` -member type-eigenschap**

Als u para meters voor een cmdlet wilt declareren, moet u eerst de eigenschappen definiëren die de para meters vertegenwoordigen. In de `Get-Proc` cmdlet is de enige para meter `Name` , die in dit geval de naam vertegenwoordigt van het .NET Framework proces object dat moet worden opgehaald. Daarom definieert de klasse cmdlet een eigenschap van het type teken reeks om een matrix met namen te accepteren.

Hier ziet u de parameter declaratie voor de `Name` para meter van de `Get-Proc` cmdlet.

```csharp
/// <summary>
/// Specify the cmdlet Name parameter.
/// </summary>
  [Parameter(Position = 0)]
  [ValidateNotNullOrEmpty]
  public string[] Name
  {
    get { return processNames; }
    set { processNames = value; }
  }
  private string[] processNames;

  #endregion Parameters
```

```vb
<Parameter(Position:=0), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

Als u de Windows Power shell-runtime wilt laten weten dat deze eigenschap de `Name` para meter is, wordt het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) toegevoegd aan de eigenschaps definitie. De basis syntaxis voor het declareren van dit kenmerk is `[Parameter()]` .

> [!NOTE]
> Een para meter moet expliciet als openbaar worden gemarkeerd. Para meters die niet zijn gemarkeerd als open bare standaard waarde voor intern en niet worden gevonden door de Windows Power shell-runtime.

Deze cmdlet gebruikt een matrix met teken reeksen voor de `Name` para meter. Als dat mogelijk is, moet uw cmdlet ook een para meter definiëren als een matrix, omdat hierdoor meer dan één item kan worden geaccepteerd met de cmdlet.

#### <a name="things-to-remember-about-parameter-definitions"></a>Wat u moet weten over parameter definities

- Vooraf gedefinieerde namen van Windows Power shell-para meters en gegevens typen moeten zo veel mogelijk worden hergebruikt om ervoor te zorgen dat uw cmdlet compatibel is met Windows Power shell-cmdlets. Als alle cmdlets bijvoorbeeld de naam van de vooraf gedefinieerde `Id` para meter gebruiken om een resource te identificeren, is de gebruiker eenvoudig inzicht in de betekenis van de para meter, ongeacht welke cmdlet ze gebruiken. In principe volgen de namen van para meters dezelfde regels als die worden gebruikt voor variabelenamen in de Common Language Runtime (CLR). Zie [cmdlet para meter names](/previous-versions/ms714468(v=vs.85))(Engelstalig) voor meer informatie over de naamgeving van para meters.

- Windows Power Shell heeft enkele parameter namen gereserveerd om een consistente gebruikers ervaring te bieden. Gebruik deze parameter namen niet: `WhatIf` ,, `Confirm` `Verbose` ,, `Debug` , `Warn` `ErrorAction` , `ErrorVariable` , `OutVariable` en `OutBuffer` . Daarnaast zijn de volgende aliassen voor deze parameter namen gereserveerd: `vb` ,, `db` , `ea` , `ev` `ov` en `ob` .

- `Name` is een eenvoudige en algemene parameter naam, aanbevolen voor gebruik in de-cmdlets. Het is beter om een parameter naam te kiezen, zoals deze, een complexe naam die uniek is voor een specifieke cmdlet en moeilijk te onthouden is.

- Para meters zijn hoofdletter gevoelig in Windows Power shell, hoewel de shell standaard niet wordt bewaard. Hoofdletter gevoeligheid van de argumenten is afhankelijk van de werking van de cmdlet. Argumenten worden door gegeven aan een para meter zoals opgegeven op de opdracht regel.

- Zie [cmdlet-para meters](./cmdlet-parameters.md)voor voor beelden van andere parameter declaraties.

## <a name="declaring-parameters-as-positional-or-named"></a>Para meters declareren als positioneel of benoemd

Voor een cmdlet moet elke para meter worden ingesteld als een positie of para meter met de naam. Beide soorten para meters accepteren enkele argumenten, meerdere argumenten gescheiden door komma's en Booleaanse instellingen. Een Booleaanse para meter, ook wel een *Switch* genoemd, verwerkt alleen Boole-instellingen. De switch wordt gebruikt om de aanwezigheid van de para meter te bepalen. De aanbevolen standaard waarde is `false` .

De voor beeld- `Get-Proc` cmdlet definieert de `Name` para meter als een positionele para meter met positie
0. Dit betekent dat het eerste argument dat de gebruiker invoert op de opdracht regel automatisch wordt ingevoegd voor deze para meter. Als u een benoemde para meter wilt definiëren waarvoor de gebruiker de parameter naam moet opgeven vanaf de opdracht regel, blijft u het `Position` sleutel woord uit de kenmerk declaratie.

> [!NOTE]
> Tenzij para meters moeten worden benoemd, wordt u aangeraden de meest gebruikte para meters positioneel te maken zodat gebruikers de parameter naam niet hoeven in te voeren.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Para meters declareren als verplicht of optioneel

Een cmdlet moet elke para meter instellen als een optionele of een verplichte para meter. In de voor beeld `Get-Proc` -cmdlet `Name` wordt de para meter gedefinieerd als optioneel omdat het `Mandatory` sleutel woord niet is ingesteld in de kenmerk declaratie.

## <a name="supporting-parameter-validation"></a>Ondersteuning voor parameter validatie

De voor beeld `Get-Proc` -cmdlet voegt een invoer validatie kenmerk, [System. Management. Automation. Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), toe aan de `Name` para meter om validatie mogelijk te maken dat de invoer niet `null` of leeg is. Dit kenmerk is een van de beschik bare validatie kenmerken van Windows Power shell. Zie [para meter invoer valideren](./validating-parameter-input.md)voor voor beelden van andere validatie kenmerken.

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Een invoer verwerkings methode overschrijven

Als uw cmdlet opdracht regel invoer verwerkt, moet deze de juiste invoer methoden onderdrukken. De basis methoden voor invoer verwerking zijn geïntroduceerd bij het [maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).

De `Get-Proc` cmdlet overschrijft de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) om de `Name` parameter invoer van de gebruiker of een script af te handelen. Met deze methode worden de processen voor elke aangevraagde proces naam en alle voor processen opgehaald als er geen naam is opgegeven. U ziet dat in [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de aanroep van [System. Management. Automation. cmdlet. WriteObject% 28System. object% 2CSystem. Boolean %29](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) het uitvoer mechanisme is voor het verzenden van uitvoer objecten naar de pijp lijn. De tweede para meter van deze aanroep, `enumerateCollection` , wordt ingesteld op `true` om de Windows Power shell-runtime op de hoogte te stellen van de uitvoer matrix van proces objecten en het één proces per keer naar de opdracht regel te schrijven.

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
    // Write the processes to the pipeline making them available
    // to the next cmdlet. The second argument of this call tells
    // PowerShell to enumerate the array, and send one process at a
    // time to the pipeline.
    WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    }
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        Dim processes As Process()
        processes = Process.GetProcesses()
    End If

    '/ If process names are specified, write the processes to the
    '/ pipeline to display them or make them available to the next cmdlet.

    For Each name As String In processNames
        '/ The second parameter of this call tells PowerShell to enumerate the
        '/ array, and send one process at a time to the pipeline.
        WriteObject(Process.GetProcessesByName(name), True)
    Next

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Code voorbeeld

Zie GetProcessSample02-voor [beeld](./getprocesssample02-sample.md)voor de volledige C#-voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Windows Power shell geeft informatie tussen cmdlets door .NET Framework-objecten te gebruiken. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet een cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren met behulp van een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. Hier volgen twee manieren om de code voor de voor beeld-cmdlet te testen. Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.

- Gebruik de volgende opdracht bij de Windows Power shell-prompt om het Internet Explorer-proces met de naam ' IEXPLORE ' weer te geven.

  ```powershell
  get-proc -name iexplore
  ```

  De volgende uitvoer wordt weer gegeven.

  ```Output
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----   ------ --   -----------
      354      11  10036   18992    85   0.67   3284   iexplore
  ```

- Gebruik de volgende opdracht om de Internet Explorer-, Outlook-en Notepad-processen met de naam ' IEXPLORE, ' OUTLOOK ' en ' NOTEPAD ' te vermelden. Als er meerdere processen zijn, worden deze weer gegeven.

  ```powershell
  get-proc -name iexplore, outlook, notepad
  ```

  De volgende uitvoer wordt weer gegeven.

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
  -------  ------  -----   -----  -----  ------   --   -----------
      732      21  24696    5000    138   2.25  2288   iexplore
      715      19  20556   14116    136   1.78  3860   iexplore
     3917      62  74096   58112    468 191.56  1848   OUTLOOK
       39       2   1024    3280     30   0.09  1444   notepad
       39       2   1024     356     30   0.08  3396   notepad
  ```

## <a name="see-also"></a>Zie ook

[Parameters toevoegen die pijplijninvoer verwerken](./adding-parameters-that-process-pipeline-input.md)

[Uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)

[Object typen en-opmaak uitbreiden](/previous-versions/ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions/ms714644(v=vs.85))

[Naslaginformatie over Windows PowerShell](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)
