---
title: Parameters die opdrachtregel verwerken toe te voegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], parameters
- Get-Proc cmdlet [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], command line input
- command line input [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], creating
ms.assetid: da0b32f8-7b51-440e-a061-3177b5759e0e
caps.latest.revision: 9
ms.openlocfilehash: c9ad84c5bcb6826fcf51db9a1f1a578a65a1f275
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854954"
---
# <a name="adding-parameters-that-process-command-line-input"></a>Parameters toevoegen die opdrachtregelinvoer verwerken

Een bron van de invoer voor een cmdlet is vanaf de opdrachtregel. In dit onderwerp wordt beschreven hoe u om toe te voegen een parameter voor de **Get-Proc** cmdlet (die wordt beschreven [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)) zodat de cmdlet kan de invoer van de lokale computer op basis van expliciete verwerken objecten die is doorgegeven aan de cmdlet. De **Get-Proc** cmdlet beschreven hier haalt processen op basis van hun namen en vervolgens geeft informatie weer over de processen achter de opdrachtprompt.

## <a name="defining-the-cmdlet-class"></a>De Cmdlet-klasse definiëren

De eerste stap bij het maken van de cmdlet is cmdlet naamgeving en de declaratie van het .NET Framework-klasse die de cmdlet. Dit smdlet haalt procesinformatie, dus de hier gekozen naam van de term 'Ophalen'. (Bijna elk soort cmdlet waarmee het ophalen van gegevens kan opdrachtregel invoer verwerken). Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

Hier is de klassendeclaratie voor de **Get-Proc** cmdlet. Meer informatie over deze definitie vindt u in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand: Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="declaring-parameters"></a>Parameters declareren

Cmdlet-parameter kan de gebruiker voor invoer naar de cmdlet. In het volgende voorbeeld **Get-Proc** en `Get-Member` zijn de namen van de pipeline-cmdlets en `MemberType` is een parameter voor de `Get-Member` cmdlet. De parameter is het argument 'eigenschap'.

**PS > get-proc; `get-member` membertype - eigenschap**

Voor het declareren van parameters voor een cmdlet, moet u eerst de eigenschappen die staan voor de parameters definiëren. In de **Get-Proc** cmdlet, de enige parameter is `Name`, die in dit geval vertegenwoordigt de naam van de .NET Framework-proces dat moet worden opgehaald. Daarom definieert de cmdlet-klasse een eigenschap van het typetekenreeks om te accepteren van een matrix van namen.

Hier is de parameterdeclaratie voor de `Name` parameter van de **Get-Proc** cmdlet.

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

Om te informeren over de Windows PowerShell-runtime die deze eigenschap is de `Name` parameter, een [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk wordt toegevoegd aan de eigenschapsdefinitie van de. De eenvoudige syntaxis voor het declareren van dit kenmerk is `[Parameter()]`.

> [!NOTE]
> Een parameter moet expliciet gemarkeerd als openbaar. De parameters die niet zijn gemarkeerd als openbare standaard naar interne en niet worden gevonden door de Windows PowerShell-runtime.

Deze cmdlet wordt een matrix van tekenreeksen voor de `Name` parameter. Indien mogelijk moet de cmdlet ook een parameter definiëren als een matrix, omdat Hiermee wordt de cmdlet om te accepteren van meer dan één item.

#### <a name="things-to-remember-about-parameter-definitions"></a>Om te onthouden over parameterdefinities

- Vooraf gedefinieerde Windows PowerShell parameter kolomnamen en gegevenstypen moeten opnieuw worden gebruikt zo veel mogelijk om ervoor te zorgen dat uw cmdlet compatibel met Windows PowerShell-cmdlets is. Bijvoorbeeld, als alle cmdlets gebruiken de vooraf gedefinieerde `Id` unieke parameternaam in voor een resource, de gebruiker wordt eenvoudig te begrijpen van de betekenis van de parameter, ongeacht welke cmdlet die ze gebruiken. Parameternamen worden in feite, als volgt dezelfde regels als die worden gebruikt voor de namen van variabelen in de common language runtime (CLR). Zie voor meer informatie over de naamgeving van parameter [namen van de Cmdlet-parameters](https://msdn.microsoft.com/en-us/c4500737-0a05-4d01-911b-394424c65bfb).

- Windows PowerShell behoudt een aantal namen van parameters om een consistente gebruikerservaring te bieden. Gebruik niet de namen van deze parameters: `WhatIf`, `Confirm`, `Verbose`, `Debug`, `Warn`, `ErrorAction`, `ErrorVariable`, `OutVariable`, en `OutBuffer`. Bovendien de volgende aliassen voor de namen van deze parameters zijn gereserveerd: `vb`, `db`, `ea`, `ev`, `ov`, en `ob`.

- `Name` is een eenvoudige en algemene parameternamen, aanbevolen voor gebruik in uw cmdlets. Is het beter om te kiezen van een parameternaam als volgt dan de naam van een complexe die uniek is voor een bepaalde cmdlet en moeilijk te onthouden.

- Parameters zijn niet hoofdlettergevoelig in Windows PowerShell, hoewel standaard de shell hoofdlettergebruik behoudt. Hoofdlettergevoeligheid van de argumenten is afhankelijk van de werking van de cmdlet. Argumenten worden doorgegeven aan een parameter zoals opgegeven op de opdrachtregel.

- Zie voor meer voorbeelden van andere parameterdeclaraties [Cmdlet-Parameters](./cmdlet-parameters.md).

## <a name="declaring-parameters-as-positional-or-named"></a>Parameters declareren als positionele of benoemde

Een cmdlet moet elke parameter worden ingesteld als een parameter positionele of met de naam. Beide soorten parameters accepteren één argumenten, meerdere argumenten gescheiden door komma's en instellingen voor Booleaanse. Een Boole-parameter, ook wel een *overschakelen*, alleen Booleaanse instellingen worden verwerkt. De switch wordt gebruikt om de aanwezigheid van de parameter. De aanbevolen standaardwaarde is `false`.

Het voorbeeld **Get-Proc** cmdlet definieert de `Name` parameter als een positionele parameter met de positie 0. Dit betekent dat het eerste argument dat de gebruiker op de opdrachtregel invoert automatisch voor deze parameter is geplaatst. Als u wilt voor het definiëren van een benoemde parameter, voor de gebruiker moet opgeven de parameternaam vanaf de opdrachtregel, laat u de `Position` sleutelwoord buiten de kenmerkdeclaratie.

> [!NOTE]
> Als parameters moeten de naam, wordt u aangeraden dat u de meest gebruikte parameters positionele zodat gebruikers niet hebben de naam van de parameter.

## <a name="declaring-parameters-as-mandatory-or-optional"></a>Parameters declareren als verplicht of optioneel

Een cmdlet, moet elke parameter ingesteld als een optionele of een verplichte parameter. In het voorbeeld **Get-Proc** cmdlet, de `Name` parameter wordt gedefinieerd als optioneel, omdat de `Mandatory` sleutelwoord is niet ingesteld in de kenmerkdeclaratie.

## <a name="supporting-parameter-validation"></a>Validatie van de Parameter ondersteunen

Het voorbeeld **Get-Proc** cmdlet wordt toegevoegd een kenmerk Invoervalidatie [System.Management.Automation.Validatenotnulloremptyattribute](/dotnet/api/System.Management.Automation.ValidateNotNullOrEmptyAttribute), naar de `Name` parameter validatie inschakelen die de de invoer is geen van beide `null` of leeg zijn. Dit kenmerk is een van verschillende validatie kenmerken die worden geleverd door Windows PowerShell. Zie voor meer voorbeelden van andere kenmerken validatie [Parameter invoer valideren](./validating-parameter-input.md).

```
[Parameter(Position = 0)]
[ValidateNotNullOrEmpty]
public string[] Name
```

## <a name="overriding-an-input-processing-method"></a>Invoer verwerken methode te overschrijven

Als de cmdlet voor het afhandelen van de invoer van de opdrachtregel, moet deze de juiste invoer verwerkingsmethoden overschrijven. De van basic input-verwerkingsmethoden zijn geïntroduceerd in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

De **Get-Proc** cmdlet vervangt de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het afhandelen van de `Name` parameter is niets opgegeven door de gebruiker of een script. Deze methode haalt de processen voor elke gewenste procesnaam of alle processen als er geen naam is opgegeven. U ziet dat in [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), de aanroep van [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/system.management.automation.cmdlet.writeobject?view=powershellsdk-1.1.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is de uitvoer mechanisme voor het verzenden van uitvoer objecten aan de pijplijn. De tweede parameter van deze aanroep `enumerateCollection`, is ingesteld op `true` om te informeren over de Windows PowerShell-runtime voor het inventariseren van de uitvoermatrix met proces-objecten en een proces op een tijdstip schrijven naar de opdrachtregel.

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

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [GetProcessSample02 voorbeeld](./getprocesssample02-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET Framework-objecten. Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of een cmdlet uit te breiden van een bestaand type geleverd door een andere cmdlet moet mogelijk. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Nadat u een cmdlet kunt implementeren, moet u het registreren met Windows PowerShell met behulp van een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Als de cmdlet is geregistreerd met Windows PowerShell, kunt u deze testen door te voeren op de opdrachtregel. Hier volgen twee manieren om te testen hoe de code voor de voorbeeld-cmdlet. Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Gebruik bij de Windows PowerShell-prompt de volgende opdracht om het proces van Internet Explorer, met de naam "IEXPLORE."

    ```powershell
    PS> get-proc -name iexplore
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----   ------ --   -----------
        354      11  10036   18992    85   0.67   3284   iexplore
    ```

- Gebruik de volgende opdracht als de Internet Explorer, Outlook en Kladblok processen met de naam 'IEXPLORE', 'OUTLOOK' en 'KLADBLOK,'. Als er meerdere processen, die allemaal worden weergegeven.

    ```powershell
    PS> get-proc -name iexplore, outlook, notepad
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)   Id   ProcessName
    -------  ------  -----   -----  -----  ------   --    -----------
        732      21  24696    5000    138   2.25  2288   iexplore
        715      19  20556   14116    136   1.78  3860   iexplore
       3917      62  74096   58112    468 191.56  1848   OUTLOOK
         39       2   1024    3280     30   0.09  1444   notepad
         39       2   1024     356     30   0.08  3396   notepad
    ```

## <a name="see-also"></a>Zie ook

[Parameters die proces Pipeline ingevoerd toe te voegen](./adding-parameters-that-process-pipeline-input.md)

[Het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referentie](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)
