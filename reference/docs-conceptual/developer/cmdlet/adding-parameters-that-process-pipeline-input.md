---
ms.date: 09/13/2016
ms.topic: reference
title: Parameters toevoegen die pijplijninvoer verwerken
description: Parameters toevoegen die pijplijninvoer verwerken
ms.openlocfilehash: b150d5be93207d9c010a6d2d4de901b4526f1d79
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668351"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Parameters toevoegen die pijplijninvoer verwerken

Eén invoer bron voor een cmdlet is een object in de pijp lijn dat afkomstig is uit een upstream-cmdlet. In deze sectie wordt beschreven hoe u een para meter kunt toevoegen aan de Get-Proc cmdlet (beschreven in [het maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md)) zodat de cmdlet pijplijn objecten kan verwerken.

Met deze Get-Proc cmdlet wordt een `Name` para meter gebruikt die invoer van een pijplijn object accepteert, worden proces gegevens van de lokale computer opgehaald op basis van de opgegeven namen, en wordt vervolgens informatie weer gegeven over de processen op de opdracht regel.

## <a name="defining-the-cmdlet-class"></a>De cmdlet-klasse definiëren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Met deze cmdlet worden proces gegevens opgehaald, zodat de naam van de term ' Get ' is. (Bijna elk soort cmdlet waarmee informatie kan worden opgehaald, kan opdracht regel invoer verwerken.) Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over goedgekeurde cmdlet-termen.

Hier volgt de definitie voor deze Get-Proc-cmdlet. Details van deze definitie vindt u in [het maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Invoer van de pijp lijn definiëren

In deze sectie wordt beschreven hoe u de invoer van de pijp lijn voor een cmdlet definieert. Deze Get-Proc-cmdlet definieert een eigenschap die de `Name` para meter vertegenwoordigt, zoals wordt beschreven in [para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md).
(Zie het onderwerp voor algemene informatie over het declareren van para meters.)

Wanneer een cmdlet echter de invoer van de pijp lijn moet verwerken, moeten de para meters zijn gekoppeld aan invoer waarden door de Windows Power shell-runtime. U kunt dit doen door het `ValueFromPipeline` tref woord toe te voegen of het `ValueFromPipelineByProperty` tref woord toe te voegen aan de kenmerk declaratie [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) . Geef het `ValueFromPipeline` tref woord op als de cmdlet het volledige invoer object opent. Geef op `ValueFromPipelineByProperty` of de cmdlet alleen een eigenschap van het object heeft geopend.

Dit is de parameter declaratie voor de `Name` para meter van deze Get-Proc-cmdlet die de invoer van de pijp lijn accepteert.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="35-44":::

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

Met de vorige declaratie wordt het `ValueFromPipeline` sleutel woord ingesteld op `true` zodat de Windows Power shell-runtime de para meter verbindt met het inkomende object als het object hetzelfde type heeft als de para meter, of als het kan worden gedwongen naar hetzelfde type. Het `ValueFromPipelineByPropertyName` sleutel woord wordt ook ingesteld op `true` zodat de Windows Power shell-runtime het inkomende object voor een `Name` eigenschap controleert. Als het inkomende object een dergelijke eigenschap heeft, wordt de para meter door de runtime gebonden `Name` aan de `Name` eigenschap van het binnenkomende object.

> [!NOTE]
> De instelling van het `ValueFromPipeline` sleutel woord attribute voor een para meter krijgt voor rang op de instelling voor het `ValueFromPipelineByPropertyName` tref woord.

## <a name="overriding-an-input-processing-method"></a>Een invoer verwerkings methode overschrijven

Als uw cmdlet de invoer van de pijp lijn moet afhandelen, moet de juiste invoer methoden worden overschreven. De basis methoden voor invoer verwerking zijn geïntroduceerd bij het [maken van uw eerste cmdlet](./creating-a-cmdlet-without-parameters.md).

Deze Get-Proc-cmdlet overschrijft de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) om de `Name` parameter invoer van de gebruiker of een script af te handelen. Met deze methode worden de processen voor elke aangevraagde proces naam of alle processen opgehaald als er geen naam is opgegeven. U ziet dat in [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)de aanroep van [WriteObject (System. object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) het uitvoer mechanisme is voor het verzenden van uitvoer objecten naar de pijp lijn. De tweede para meter van deze aanroep, `enumerateCollection` , wordt ingesteld op `true` om de Windows Power shell-runtime te laten opsommen van de matrix van proces objecten en een proces per keer naar de opdracht regel te schrijven.

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
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a>Code voorbeeld

Zie GetProcessSample03-voor [beeld](./getprocesssample03-sample.md)voor de volledige C#-voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Windows Power shell geeft informatie door over cmdlets met behulp van .net-objecten. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Na de implementatie van een cmdlet moet deze met Windows Power shell zijn geregistreerd via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. Test bijvoorbeeld de code voor de voor beeld-cmdlet. Zie aan de slag [met Windows Power shell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)voor meer informatie over het gebruik van cmdlets vanaf de opdracht regel.

- Voer de volgende opdrachten bij de Windows Power shell-prompt in om de proces namen via de pijp lijn op te halen.

  ```powershell
  PS> type ProcessNames | get-proc
  ```

  De volgende uitvoer wordt weer gegeven.

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      809      21  40856    4448    147    9.50  2288  iexplore
      737      21  26036   16348    144   22.03  3860  iexplore
       39       2   1024     388     30    0.08  3396  notepad
     3927      62  71836   26984    467  195.19  1848  OUTLOOK
  ```

- Voer de volgende regels in om de proces objecten op te halen die een `Name` eigenschap van de processen met de naam "iexplore" hebben. In dit voor beeld wordt de `Get-Process` cmdlet (meegeleverd door Windows Power shell) gebruikt als een upstream-opdracht voor het ophalen van de "iexplore"-processen.

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  De volgende uitvoer wordt weer gegeven.

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a>Zie ook

[Para meters toevoegen die opdracht regel invoer verwerken](./adding-parameters-that-process-command-line-input.md)

[Uw eerste cmdlet maken](./creating-a-cmdlet-without-parameters.md)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Naslaginformatie over Windows PowerShell](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)
