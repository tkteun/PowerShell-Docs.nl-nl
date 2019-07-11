---
title: Parameter toe te voegen aan een Cmdlet ingesteld | Microsoft Docs
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
ms.openlocfilehash: d330b9be1da9fbb36be324e68fd6cf2d874fc06b
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733806"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a>Parametersets toevoegen aan een cmdlet

## <a name="things-to-know-about-parameter-sets"></a>Om te weten over parametersets

Windows PowerShell definieert een parameter is ingesteld als een groep van de parameters die samen te werken. Door het groeperen van de parameters van een cmdlet, kunt u één cmdlet die de functionaliteit ervan op basis van welke groep van de parameters worden opgegeven die de gebruiker kunt wijzigen.

Een voorbeeld van een cmdlet die twee parametersets gebruikt voor het definiëren van verschillende functies is de `Get-EventLog` cmdlet die wordt geleverd door Windows PowerShell. Deze cmdlet worden verschillende gegevens geretourneerd wanneer de gebruiker Hiermee geeft u de `List` of `LogName` parameter. Als de `LogName` parameter is opgegeven, wordt de cmdlet retourneert informatie over de gebeurtenissen in een opgegeven gebeurtenislogboek. Als de `List` parameter is opgegeven, wordt de cmdlet retourneert informatie over het logboek bestanden zelf (niet de gebeurtenisgegevens ze bevatten). In dit geval de `List` en `LogName` parameters identificeren twee afzonderlijke parametersets.

Twee belangrijke dingen om te weten over parametersets is dat de Windows PowerShell-runtime wordt slechts één parameter is ingesteld voor een bepaalde invoer gebruikt, en elke parameter is ingesteld, moet ten minste één parameter hebben die uniek is voor deze parameter is ingesteld.

Als u wilt laten zien dat laatste moment, met deze cmdlet Stop-Proc maakt gebruik van drie parametersets: `ProcessName`, `ProcessId`, en `InputObject`. Elk van deze parametersets heeft een parameter die zich niet in de andere parametersets. De parametersets andere parameters kunnen delen, maar de cmdlet maakt gebruik van de unieke parameters `ProcessName`, `ProcessId`, en `InputObject` om te bepalen welke set parameters die voor de Windows PowerShell-runtime wordt gebruikt.

## <a name="declaring-the-cmdlet-class"></a>De Cmdlet-klasse declareren

De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren. Voor deze cmdlet wordt de levenscyclus van een term 'Stop' omdat de cmdlet systeemprocessen stopt gebruikt. De naam van het zelfstandig naamwoord 'Proc' wordt gebruikt omdat de cmdlet op processen werkt. Houd er rekening mee dat de naam van de cmdlet werkwoord en een zelfstandig naamwoord naam van de cmdlet-klasse worden weergegeven in de onderstaande verklaring.

> [!NOTE]
> Zie voor meer informatie over de namen van de term goedgekeurde cmdlet [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

De volgende code wordt de klassedefinitie van deze cmdlet Stop-Proc.

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a>De Parameters van de Cmdlet declareren

Deze cmdlet definieert drie parameters nodig als invoer voor de cmdlet (deze parameters ook definiëren de parametersets), evenals een `Force` parameter die wordt beheerd betekenis van de cmdlet en een `PassThru` parameter waarmee wordt bepaald of de cmdlet verzendt een uitvoerobject via de pijplijn. Deze cmdlet geeft standaard, niet een object via de pijplijn. Zie voor meer informatie over deze laatste twee parameters [maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md).

### <a name="declaring-the-name-parameter"></a>De Parameter Name declareren

Deze invoerparameter kan de gebruiker om op te geven van de namen van de processen worden gestopt. Houd er rekening mee dat de `ParameterSetName` kenmerken van het door u opgegeven trefwoord de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk geeft u de `ProcessName` parameter ingesteld voor deze parameter.

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

Houd er ook rekening mee dat u dat de alias "Procesnaam" voor deze parameter is opgegeven.

### <a name="declaring-the-id-parameter"></a>De Parameter Id declareren

Deze invoerparameter kan de gebruiker om op te geven van de id's van de processen worden gestopt. Houd er rekening mee dat de `ParameterSetName` kenmerken van het door u opgegeven trefwoord de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk geeft u de `ProcessId` parameterset.

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

Houd er ook rekening mee dat u dat de alias "Proces-id" aan deze parameter wordt gegeven.

### <a name="declaring-the-inputobject-parameter"></a>De InputObject Parameter declareren

Deze invoerparameter kan de gebruiker om op te geven van een invoer-object dat informatie bevat over de processen worden gestopt. Houd er rekening mee dat de `ParameterSetName` kenmerken van het door u opgegeven trefwoord de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) kenmerk geeft u de `InputObject` parameter ingesteld voor deze parameter.

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

Houd er ook rekening mee dat u dat deze parameter geen alias heeft.

### <a name="declaring-parameters-in-multiple-parameter-sets"></a>Parameters in meerdere parametersets declareren

Hoewel er een unieke parameter voor elke parameter is ingesteld moet, kunnen tot meer dan één parameterset parameters behoren. In dergelijke gevallen geeft u de gedeelde parameter een [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) de kenmerkdeclaratie van het voor elke waartoe de parameter set hoort. Als een parameter in alle parametersets, alleen moet de parameterkenmerk eenmaal declareren en hoeft niet om op te geven dat de naam van de parameterset.

## <a name="overriding-an-input-processing-method"></a>Invoer verwerken methode te overschrijven

Elke cmdlet moet verwerken van methode invoer overschrijven, dit is meestal de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode. In deze cmdlet de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode zodat een willekeurig aantal processen kan worden verwerkt door de cmdlet wordt overschreven. Het bevat een instructie Select die aanroepen van een andere methode op basis van welke parameterset de gebruiker is opgegeven.

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

De Help-methoden aangeroepen door de Select-instructie niet hier worden beschreven, maar ziet u de implementatie in het volledige codevoorbeeld in de volgende sectie.

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [StopProcessSample04 voorbeeld](./stopprocesssample04-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .NET-objecten. Als gevolg daarvan kan een cmdlet mogelijk voor het definiëren van een eigen type of de cmdlet moet mogelijk om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](/previous-versions//ms714665(v=vs.85)).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet, moet u deze registreren met Windows PowerShell via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze door te voeren op de opdrachtregel testen. Hier volgen enkele tests uit die laten zien hoe de `ProcessId` en `InputObject` parameters kunnen worden gebruikt voor het testen van hun parametersets om een proces te stoppen.

- Met Windows PowerShell is gestart, voert u de cmdlet Stop-Proc met de `ProcessId` parameter ingesteld om een proces op basis van de id te stoppen. In dit geval wordt de cmdlet gebruikt de `ProcessId` parameter ingesteld op het proces beëindigen.

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- Met Windows PowerShell is gestart, voert u de cmdlet Stop-Proc met de `InputObject` parameter ingesteld op het beëindigen van processen voor het Kladblok-object opgehaald door de `Get-Process` opdracht.

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a>Zie ook

[Het maken van een Cmdlet die Hiermee wijzigt u het systeem](./creating-a-cmdlet-that-modifies-the-system.md)

[Over het maken van een Windows PowerShell-Cmdlet](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Objecttypen uitbreiden en opmaak](/previous-versions//ms714665(v=vs.85))

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)
