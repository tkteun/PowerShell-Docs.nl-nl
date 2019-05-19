---
title: Parameters die Pijpleidinginvoer verwerken toe te voegen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: def0ac2ff98575beb29c3c2a7d91a5a5c53e648e
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854984"
---
# <a name="adding-parameters-that-process-pipeline-input"></a>Parameters toevoegen die pijplijninvoer verwerken

Een bron van de invoer voor een cmdlet is een object in de pijplijn die afkomstig van een upstream-cmdlet is. In deze sectie wordt beschreven hoe u een parameter toevoegen aan de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)) zodat de cmdlet pijplijnobjecten kan verwerken.

Maakt gebruik van deze cmdlet Get-Proc een `Name` parameter dat invoer van een pijplijn-object accepteert procesinformatie opgehaald uit de lokale computer op basis van de opgegeven namen en vervolgens geeft informatie weer over de processen op de opdrachtregel.

## <a name="defining-the-cmdlet-class"></a>De Cmdlet-klasse definiëren

De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren. Dit smdlet haalt procesinformatie, dus de hier gekozen naam van de term 'Ophalen'. (Bijna elk soort cmdlet waarmee het ophalen van gegevens kan opdrachtregel invoer verwerken). Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).

Hier volgt de definitie voor deze cmdlet Get-Proc. Details van deze definitie zijn vermeld in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a>Invoer van de pijplijn definiëren

In deze sectie wordt beschreven hoe u definieert u welke invoer van de pijplijn voor een cmdlet. Deze cmdlet Get-Proc definieert een eigenschap die vertegenwoordigt de `Name` parameter zoals beschreven in [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md). (Zie dit onderwerp voor algemene informatie over het declareren van parameters.)

Wanneer een cmdlet nodig heeft voor het verwerken van invoer van de pijplijn, moet deze zijn gebonden aan de invoerwaarden door de Windows PowerShell-runtime parameters hebben. U doet dit door u moet toevoegen de `ValueFromPipeline` sleutelwoord of toe te voegen de `ValueFromPipelineByProperty` trefwoord dat u wilt de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaratie van het kenmerk. Geef de `ValueFromPipeline` sleutelwoord als de cmdlet toegang heeft tot het volledige invoerobject. Geef de `ValueFromPipelineByProperty` als de cmdlet toegang heeft tot een eigenschap van het object alleen.

Hier is de parameterdeclaratie voor de `Name` parameter van deze cmdlet Get-Proc dat invoer van de pijplijn accepteert.

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

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

De vorige declaratie stelt de `ValueFromPipeline` trefwoord `true` zodat de Windows PowerShell-runtime wordt de parameter gebonden aan het binnenkomende object als het object is hetzelfde type als de parameter, of als u hetzelfde type kan worden afgedwongen. De `ValueFromPipelineByPropertyName` sleutelwoord ook is ingesteld op `true` zodat de Windows PowerShell-runtime controleert het binnenkomende-object voor een `Name` eigenschap. Als het binnenkomende object heeft een dergelijke eigenschap, de runtime verbindt de `Name` parameter voor de `Name` eigenschap van het binnenkomende object.

> [!NOTE]
> De instelling van de `ValueFromPipeline` sleutelwoord kenmerk voor een parameter heeft voorrang op de instelling voor de `ValueFromPipelineByPropertyName` trefwoord.

## <a name="overriding-an-input-processing-method"></a>Invoer verwerken methode te overschrijven

Als de cmdlet voor het afhandelen van de invoer van de pijplijn is, moet de juiste invoer verwerkingsmethoden overschrijven. De van basic input-verwerkingsmethoden zijn geïntroduceerd in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).

Deze cmdlet Get-Proc overschrijft de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het afhandelen van de `Name` parameter is niets opgegeven door de gebruiker of een script. Deze methode krijgt de processen voor elke gewenste procesnaam of alle processen als er geen naam is opgegeven. U ziet dat binnen [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), de aanroep van [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is de uitvoer mechanisme voor het verzenden van uitvoer objecten aan de pijplijn. De tweede parameter van deze aanroep `enumerateCollection`, is ingesteld op `true` vertellen dat de Windows PowerShell-runtime voor het inventariseren van de matrix met proces-objecten en een proces op een tijdstip schrijven naar de opdrachtregel.

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

## <a name="code-sample"></a>Voorbeeld van code

Voor de volledige C# voorbeeldcode, Zie [GetProcessSample03 voorbeeld](./getprocesssample03-sample.md).

## <a name="defining-object-types-and-formatting"></a>Objecttype definiëren en opmaak

Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten. Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet. Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-cmdlet"></a>Het bouwen van de Cmdlet

Na de implementatie van een cmdlet moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module. Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen van de Cmdlet

Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze door te voeren op de opdrachtregel testen. Bijvoorbeeld, test de code voor de voorbeeld-cmdlet. Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).

- Voer bij de Windows PowerShell-prompt de volgende opdrachten om op te halen van de procesnamen via de pijplijn.

    ```powershell
    PS> type ProcessNames | get-proc
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- Voer de volgende regels om op te halen van de proces-objecten die u hebt een `Name` eigenschap van de processen met de naam 'IEXPLORE'. In dit voorbeeld wordt de `Get-Process` cmdlet (geleverd door Windows PowerShell) als een upstream-opdracht om op te halen van de processen 'IEXPLORE'.

    ```powershell
    PS> get-process iexplore | get-proc
    ```

De volgende uitvoer wordt weergegeven.

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a>Zie ook

[Parameters die vanaf de opdrachtregel verwerken toe te voegen](./adding-parameters-that-process-command-line-input.md)

[Het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)

[Objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Over het registreren van Providers,-Cmdlets en -toepassingen hosten](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell-referentie](../windows-powershell-reference.md)

[Cmdlet-voorbeelden](./cmdlet-samples.md)
