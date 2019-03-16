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
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054753"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="315b7-102">Parameters toevoegen die pijplijninvoer verwerken</span><span class="sxs-lookup"><span data-stu-id="315b7-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="315b7-103">Een bron van de invoer voor een cmdlet is een object in de pijplijn die afkomstig van een upstream-cmdlet is.</span><span class="sxs-lookup"><span data-stu-id="315b7-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="315b7-104">In deze sectie wordt beschreven hoe u een parameter toevoegen aan de cmdlet Get-Proc (beschreven in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md)) zodat de cmdlet pijplijnobjecten kan verwerken.</span><span class="sxs-lookup"><span data-stu-id="315b7-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="315b7-105">Maakt gebruik van deze cmdlet Get-Proc een `Name` parameter dat invoer van een pijplijn-object accepteert procesinformatie opgehaald uit de lokale computer op basis van de opgegeven namen en vervolgens geeft informatie weer over de processen op de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="315b7-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="315b7-106">Onderwerpen in deze sectie bevatten het volgende:</span><span class="sxs-lookup"><span data-stu-id="315b7-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="315b7-107">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="315b7-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="315b7-108">Invoer van de pijplijn definiëren</span><span class="sxs-lookup"><span data-stu-id="315b7-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="315b7-109">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="315b7-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="315b7-110">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="315b7-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="315b7-111">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="315b7-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="315b7-112">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="315b7-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="315b7-113">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="315b7-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="315b7-114">De Cmdlet-klasse definiëren</span><span class="sxs-lookup"><span data-stu-id="315b7-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="315b7-115">De eerste stap bij het maken van de cmdlet is altijd naamgeving van de cmdlet en de .NET-klasse die de cmdlet declareren.</span><span class="sxs-lookup"><span data-stu-id="315b7-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="315b7-116">Dit smdlet haalt procesinformatie, dus de hier gekozen naam van de term 'Ophalen'.</span><span class="sxs-lookup"><span data-stu-id="315b7-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="315b7-117">(Bijna elk soort cmdlet waarmee het ophalen van gegevens kan opdrachtregel invoer verwerken). Zie voor meer informatie over goedgekeurde werkwoorden [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="315b7-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="315b7-118">Hier volgt de definitie voor deze cmdlet Get-Proc.</span><span class="sxs-lookup"><span data-stu-id="315b7-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="315b7-119">Details van deze definitie zijn vermeld in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="315b7-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="315b7-120">Invoer van de pijplijn definiëren</span><span class="sxs-lookup"><span data-stu-id="315b7-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="315b7-121">In deze sectie wordt beschreven hoe u definieert u welke invoer van de pijplijn voor een cmdlet.</span><span class="sxs-lookup"><span data-stu-id="315b7-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="315b7-122">Deze cmdlet Get-Proc definieert een eigenschap die vertegenwoordigt de `Name` parameter zoals beschreven in [Parameters die invoer van de opdrachtregel proces toe te voegen](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="315b7-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="315b7-123">(Zie dit onderwerp voor algemene informatie over het declareren van parameters.)</span><span class="sxs-lookup"><span data-stu-id="315b7-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="315b7-124">Wanneer een cmdlet nodig heeft voor het verwerken van invoer van de pijplijn, moet deze zijn gebonden aan de invoerwaarden door de Windows PowerShell-runtime parameters hebben.</span><span class="sxs-lookup"><span data-stu-id="315b7-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="315b7-125">U doet dit door u moet toevoegen de `ValueFromPipeline` sleutelwoord of toe te voegen de `ValueFromPipelineByProperty` trefwoord dat u wilt de [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) declaratie van het kenmerk.</span><span class="sxs-lookup"><span data-stu-id="315b7-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="315b7-126">Geef de `ValueFromPipeline` sleutelwoord als de cmdlet toegang heeft tot het volledige invoerobject.</span><span class="sxs-lookup"><span data-stu-id="315b7-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="315b7-127">Geef de `ValueFromPipelineByProperty` als de cmdlet toegang heeft tot een eigenschap van het object alleen.</span><span class="sxs-lookup"><span data-stu-id="315b7-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="315b7-128">Hier is de parameterdeclaratie voor de `Name` parameter van deze cmdlet Get-Proc dat invoer van de pijplijn accepteert.</span><span class="sxs-lookup"><span data-stu-id="315b7-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

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

<span data-ttu-id="315b7-129">De vorige declaratie stelt de `ValueFromPipeline` trefwoord `true` zodat de Windows PowerShell-runtime wordt de parameter gebonden aan het binnenkomende object als het object is hetzelfde type als de parameter, of als u hetzelfde type kan worden afgedwongen.</span><span class="sxs-lookup"><span data-stu-id="315b7-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="315b7-130">De `ValueFromPipelineByPropertyName` sleutelwoord ook is ingesteld op `true` zodat de Windows PowerShell-runtime controleert het binnenkomende-object voor een `Name` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="315b7-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="315b7-131">Als het binnenkomende object heeft een dergelijke eigenschap, de runtime verbindt de `Name` parameter voor de `Name` eigenschap van het binnenkomende object.</span><span class="sxs-lookup"><span data-stu-id="315b7-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="315b7-132">De instelling van de `ValueFromPipeline` sleutelwoord kenmerk voor een parameter heeft voorrang op de instelling voor de `ValueFromPipelineByPropertyName` trefwoord.</span><span class="sxs-lookup"><span data-stu-id="315b7-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="315b7-133">Invoer verwerken methode te overschrijven</span><span class="sxs-lookup"><span data-stu-id="315b7-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="315b7-134">Als de cmdlet voor het afhandelen van de invoer van de pijplijn is, moet de juiste invoer verwerkingsmethoden overschrijven.</span><span class="sxs-lookup"><span data-stu-id="315b7-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="315b7-135">De van basic input-verwerkingsmethoden zijn geïntroduceerd in [het maken van uw eerste Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="315b7-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="315b7-136">Deze cmdlet Get-Proc overschrijft de [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) methode voor het afhandelen van de `Name` parameter is niets opgegeven door de gebruiker of een script.</span><span class="sxs-lookup"><span data-stu-id="315b7-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="315b7-137">Deze methode krijgt de processen voor elke gewenste procesnaam of alle processen als er geen naam is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="315b7-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="315b7-138">U ziet dat binnen [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), de aanroep van [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is de uitvoer mechanisme voor het verzenden van uitvoer objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="315b7-138">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="315b7-139">De tweede parameter van deze aanroep `enumerateCollection`, is ingesteld op `true` vertellen dat de Windows PowerShell-runtime voor het inventariseren van de matrix met proces-objecten en een proces op een tijdstip schrijven naar de opdrachtregel.</span><span class="sxs-lookup"><span data-stu-id="315b7-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="315b7-140">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="315b7-140">Code Sample</span></span>

<span data-ttu-id="315b7-141">Voor de volledige C# voorbeeldcode, Zie [GetProcessSample03 voorbeeld](./getprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="315b7-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="315b7-142">Objecttype definiëren en opmaak</span><span class="sxs-lookup"><span data-stu-id="315b7-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="315b7-143">Windows PowerShell wordt informatie doorgegeven tussen cmdlets met behulp van .net-objecten.</span><span class="sxs-lookup"><span data-stu-id="315b7-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="315b7-144">Als gevolg daarvan kan een cmdlet mogelijk nodig hebt voor het definiëren van een eigen type, of de cmdlet moet om uit te breiden van een bestaand type geleverd door een andere cmdlet.</span><span class="sxs-lookup"><span data-stu-id="315b7-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="315b7-145">Zie voor meer informatie over het definiëren van nieuwe typen of uitbreiden van bestaande typen [objecttypen uitbreiden en opmaak](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span><span class="sxs-lookup"><span data-stu-id="315b7-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="315b7-146">Het bouwen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="315b7-146">Building the Cmdlet</span></span>

<span data-ttu-id="315b7-147">Na de implementatie van een cmdlet moet deze met Windows PowerShell worden geregistreerd via een Windows PowerShell-module.</span><span class="sxs-lookup"><span data-stu-id="315b7-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="315b7-148">Zie voor meer informatie over het registreren van cmdlets [hoe u Cmdlets registreren, Providers en hosting van toepassingen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span><span class="sxs-lookup"><span data-stu-id="315b7-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="315b7-149">Testen van de Cmdlet</span><span class="sxs-lookup"><span data-stu-id="315b7-149">Testing the Cmdlet</span></span>

<span data-ttu-id="315b7-150">Wanneer de cmdlet is geregistreerd met Windows PowerShell, kunt u deze door te voeren op de opdrachtregel testen.</span><span class="sxs-lookup"><span data-stu-id="315b7-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="315b7-151">Bijvoorbeeld, test de code voor de voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="315b7-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="315b7-152">Zie voor meer informatie over het gebruik van cmdlets vanaf de opdrachtregel de [aan de slag met Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="315b7-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="315b7-153">Voer bij de Windows PowerShell-prompt de volgende opdrachten om op te halen van de procesnamen via de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="315b7-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="315b7-154">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="315b7-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="315b7-155">Voer de volgende regels om op te halen van de proces-objecten die u hebt een `Name` eigenschap van de processen met de naam 'IEXPLORE'.</span><span class="sxs-lookup"><span data-stu-id="315b7-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="315b7-156">In dit voorbeeld wordt de `Get-Process` cmdlet (geleverd door Windows PowerShell) als een upstream-opdracht om op te halen van de processen 'IEXPLORE'.</span><span class="sxs-lookup"><span data-stu-id="315b7-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="315b7-157">De volgende uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="315b7-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="315b7-158">Zie ook</span><span class="sxs-lookup"><span data-stu-id="315b7-158">See Also</span></span>

[<span data-ttu-id="315b7-159">Parameters die vanaf de opdrachtregel verwerken toe te voegen</span><span class="sxs-lookup"><span data-stu-id="315b7-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="315b7-160">Het maken van uw eerste Cmdlet</span><span class="sxs-lookup"><span data-stu-id="315b7-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="315b7-161">Objecttypen uitbreiden en opmaak</span><span class="sxs-lookup"><span data-stu-id="315b7-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="315b7-162">Over het registreren van Providers,-Cmdlets en -toepassingen hosten</span><span class="sxs-lookup"><span data-stu-id="315b7-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="315b7-163">Windows PowerShell-referentie</span><span class="sxs-lookup"><span data-stu-id="315b7-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="315b7-164">Cmdlet-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="315b7-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
