---
title: Parameter sets toevoegen aan een cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355634"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Parametersets toevoegen aan een cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Wat u moet weten over parameter sets

Windows Power shell definieert een para meter die is ingesteld als een groep para meters die samen werken. Als u de para meters van een cmdlet groepeert, kunt u een enkele cmdlet maken die de functionaliteit ervan kan wijzigen op basis van de groep para meters die de gebruiker opgeeft.

Een voor beeld van een cmdlet die gebruikmaakt van twee parameters sets voor het definiëren van verschillende functies is de `Get-EventLog`-cmdlet die wordt meegeleverd met Windows Power shell. Met deze cmdlet wordt een andere informatie geretourneerd als de gebruiker de para meter `List` of `LogName` opgeeft. Als de para meter `LogName` is opgegeven, retourneert de cmdlet informatie over de gebeurtenissen in een bepaald gebeurtenis logboek. Als de para meter `List` is opgegeven, retourneert de cmdlet informatie over de logboek bestanden zelf (niet de gebeurtenis gegevens die ze bevatten). In dit geval identificeren de para meters `List` en `LogName` twee afzonderlijke parameter sets.

Twee belang rijke zaken die u moet onthouden over parameter sets is dat de Windows Power shell-runtime slechts één para meterset voor een bepaalde invoer gebruikt en dat elke parameterset ten minste één para meter moet hebben die uniek is voor de ingestelde para meter.

Ter illustratie van dat laatste punt gebruikt deze stop-proc-cmdlet drie parameter sets: `ProcessName`, `ProcessId` en `InputObject`. Elk van deze parameter sets heeft één para meter die zich niet in de andere parameter sets bevindt. De parameter sets kunnen andere para meters delen, maar de cmdlet gebruikt de unieke para meters `ProcessName`, `ProcessId` en `InputObject` om te bepalen welke set para meters moet worden gebruikt door de Windows Power shell-runtime.

## <a name="declaring-the-cmdlet-class"></a>De cmdlet-klasse declareren

De eerste stap bij het maken van de cmdlet is altijd de naam van de cmdlet en het declareren van de .NET-klasse die de cmdlet implementeert. Voor deze cmdlet wordt de levens cyclus term ' Stop ' gebruikt omdat de cmdlet systeem processen stopt. De naam van het zelfstandige zelfstandig proces wordt gebruikt omdat de cmdlet werkt voor processen. Houd er rekening mee dat het cmdlet-werk woord en de naam van het zelfstandigen worden weer gegeven in de naam van de cmdlet-klasse.

> [!NOTE]
> Zie voor meer informatie over de namen van goedgekeurde cmdlet- [verbs](./approved-verbs-for-windows-powershell-commands.md).

De volgende code is de klassedefinitie voor deze stop-proc-cmdlet.

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a>De para meters van de cmdlet declareren

Met deze cmdlet worden drie para meters gedefinieerd die nodig zijn als invoer voor de cmdlet (deze para meters definiëren ook de parameter sets), evenals een `Force` para meter waarmee wordt beheerd wat de cmdlet doet en een para meter `PassThru` die bepaalt of de cmdlet een uitvoer object verzendt via de pijp lijn. Met deze cmdlet wordt standaard geen object door gegeven via de pijp lijn. Zie [een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)voor meer informatie over deze laatste twee para meters.

### <a name="declaring-the-name-parameter"></a>De para meter name declareren

Met deze invoer parameter kan de gebruiker de namen opgeven van de processen die moeten worden gestopt. Houd er rekening mee dat het sleutel woord `ParameterSetName` van het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de para meter `ProcessName` bevat die voor deze para meter is ingesteld.

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

Houd er rekening mee dat de alias ' procesnaam ' wordt gegeven aan deze para meter.

### <a name="declaring-the-id-parameter"></a>Declareren van de id-para meter

Met deze invoer parameter kan de gebruiker de id's opgeven van de processen die moeten worden gestopt. Houd er rekening mee dat het sleutel woord `ParameterSetName` van het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de para meter set `ProcessId` bevat.

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

Houd er rekening mee dat de alias ' ProcessId ' wordt opgegeven voor deze para meter.

### <a name="declaring-the-inputobject-parameter"></a>Declareren van de para meter input object

Met deze invoer parameter kan de gebruiker een invoer object opgeven dat informatie bevat over de processen die moeten worden gestopt. Houd er rekening mee dat het sleutel woord `ParameterSetName` van het kenmerk [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de para meter `InputObject` bevat die voor deze para meter is ingesteld.

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

Houd er rekening mee dat deze para meter geen alias heeft.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Para meters declareren in meerdere parameter sets

Hoewel er een unieke para meter moet zijn voor elke parameterset, kunnen para meters deel uitmaken van meer dan één parameterset. In dergelijke gevallen geeft u de gedeelde para meter een [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk declaratie voor elke set waarvan de para meter deel uitmaakt. Als een para meter zich in alle parameter sets bevindt, hoeft u alleen maar één keer het parameter kenmerk te declareren en hoeft u de naam van de parameter set niet op te geven.

## <a name="overriding-an-input-processing-method"></a>Een invoer verwerkings methode overschrijven

Elke cmdlet moet een invoer verwerkings methode overschrijven, meestal is dit de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . In deze cmdlet wordt de methode [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) genegeerd, zodat de cmdlet elk wille keurig aantal processen kan verwerken. Het bevat een SELECT-instructie die een andere methode aanroept op basis van de para meter die de gebruiker heeft opgegeven.

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

De Help-methoden die worden aangeroepen door de SELECT-instructie worden hier niet beschreven, maar u kunt de implementatie ervan bekijken in het voor beeld van de volledige code in de volgende sectie.

## <a name="code-sample"></a>Code voorbeeld

Zie StopProcessSample04- C# voor [beeld](./stopprocesssample04-sample.md)voor de volledige voorbeeld code.

## <a name="defining-object-types-and-formatting"></a>Object typen en-opmaak definiëren

Windows Power shell geeft informatie door over cmdlets met behulp van .NET-objecten. Daarom moet een cmdlet een eigen type kunnen definiëren, of moet de cmdlet een bestaand type uitbreiden dat door een andere cmdlet wordt verschaft. Zie [object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))voor meer informatie over het definiëren van nieuwe typen of het uitbreiden van bestaande typen.

## <a name="building-the-cmdlet"></a>De cmdlet bouwen

Nadat u een cmdlet hebt geïmplementeerd, moet u deze met Windows Power shell registreren via een Windows Power shell-module. Zie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))voor meer informatie over het registreren van cmdlets.

## <a name="testing-the-cmdlet"></a>De cmdlet testen

Als uw cmdlet is geregistreerd bij Windows Power shell, kunt u deze testen door deze uit te voeren op de opdracht regel. Hier volgen enkele tests die laten zien hoe de para meters `ProcessId` en `InputObject` kunnen worden gebruikt om de parameter sets te testen om een proces te stoppen.

- Als Windows Power shell is gestart, voert u de cmdlet stop-proc uit met de para meter `ProcessId` om een proces te stoppen op basis van de id. In dit geval gebruikt de cmdlet de para meter `ProcessId` die is ingesteld om het proces te stoppen.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Als Windows Power shell is gestart, voert u de cmdlet stop-proc uit met de para meter `InputObject` ingesteld op het stoppen van processen voor het Notepad-object dat is opgehaald met de opdracht `Get-Process`.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zie ook

[Een cmdlet maken die het systeem wijzigt](./creating-a-cmdlet-that-modifies-the-system.md)

[Een Windows Power shell-cmdlet maken](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Object typen en-opmaak uitbreiden](/previous-versions//ms714665(v=vs.85))

[Cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85))

[Windows Power shell SDK](../windows-powershell-reference.md)
