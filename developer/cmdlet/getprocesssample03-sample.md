---
title: Voorbeeld van GetProcessSample03 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068042"
---
# <a name="getprocesssample03-sample"></a>Voorbeeld GetProcessSample03

Dit voorbeeld laat zien hoe u voor het implementeren van een cmdlet die worden opgehaald van de processen die op de lokale computer. Het biedt een `Name` parameter een object van de pijplijn of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de parameternaam is kan accepteren. Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet geleverd door Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Over het bouwen van het voorbeeld met behulp van Visual Studio.

1. Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample03. De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.

2. Dubbelklik op het pictogram voor het oplossingsbestand (.sln). Hiermee opent u het voorbeeldproject in Visual Studio.

3. In de **bouwen** in het menu **Build Solution**.

    De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.

### <a name="how-to-run-the-sample"></a>Hoe u het voorbeeld uitvoeren

1. Maak de volgende modulemap:

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. Kopieer de voorbeeld-assembly naar de modulemap.

3. Start Windows PowerShell.

4. Voer de volgende opdracht om het laden van de assembly in Windows PowerShell:

    `Import-module getprossessample03`

5. Voer de volgende opdracht om uit te voeren van de cmdlet:

    `get-proc`

## <a name="requirements"></a>Vereisten

In dit voorbeeld is Windows PowerShell 2.0 vereist.

## <a name="demonstrates"></a>Ziet u

In dit voorbeeld ziet u het volgende.

- Het declareren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.

- Cmdlet-parameter met behulp van de Parameter-kenmerk declareren.

- De positie van de parameter aangeeft.

- Op te geven dat de parameter wordt de invoer van de pijplijn. De invoer kan worden uitgevoerd van een object of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de naam van de parameter is.

- Een kenmerk validatie voor de parameter invoer declareren.

## <a name="example"></a>Voorbeeld

In dit voorbeeld toont een implementatie van de cmdlet Get-Proc met een `Name` parameter dat invoer van de pijplijn accepteert.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
    /// </summary>
    [Parameter(
               Position = 0,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
