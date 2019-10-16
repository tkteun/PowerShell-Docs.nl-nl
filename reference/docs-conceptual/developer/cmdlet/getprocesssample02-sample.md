---
title: GetProcessSample02-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355620"
---
# <a name="getprocesssample02-sample"></a>Voorbeeld GetProcessSample02

In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Het bevat een `Name`-para meter die kan worden gebruikt om de processen op te geven die moeten worden opgehaald. Deze cmdlet is een vereenvoudigde versie van de `Get-Process`-cmdlet van Windows Power Shell 2,0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Het voor beeld maken met Visual Studio.

1. Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample02. De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Dubbel klik op het pictogram van het oplossings bestand (. SLN). Hiermee opent u het voorbeeld project in Visual Studio.

3. Selecteer in het menu **Build** de optie **Build Solution**.

    De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.

### <a name="how-to-run-the-sample"></a>Het voor beeld uitvoeren

1. Maak de volgende module map:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Kopieer de voor beeld-assembly naar de module map.

3. Start Windows PowerShell.

4. Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:

    `import-module getprossessample02`

5. Voer de volgende opdracht uit om de cmdlet uit te voeren:

    `get-proc`

## <a name="requirements"></a>Vereisten

Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Laat zien

In dit voor beeld ziet u het volgende.

- Het declareren van een cmdlet-klasse met het cmdlet-kenmerk.

- Declareer een cmdlet-para meter met het parameter kenmerk.

- De positie van de para meter opgeven.

- Het declareren van een validatie kenmerk voor de parameter invoer.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u een implementatie van de cmdlet Get-proc die een `Name`-para meter bevat.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

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
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
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
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
