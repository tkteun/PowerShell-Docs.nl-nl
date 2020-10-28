---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld GetProcessSample04
description: Voorbeeld GetProcessSample04
ms.openlocfilehash: 4b2b7f7ed5fd87711d0d7872caaf75d453de4832
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652730"
---
# <a name="getprocesssample04-sample"></a>Voorbeeld GetProcessSample04

In dit voor beeld ziet u hoe u een cmdlet implementeert waarmee de processen op de lokale computer worden opgehaald. Er wordt een niet-afsluit fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces. Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt meegeleverd met Windows Power shell 2,0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Het voor beeld maken met Visual Studio.

1. Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample04. De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Dubbel klik op het pictogram van het oplossings bestand (. SLN). Hiermee opent u het voorbeeld project in Visual Studio.

3. Selecteer in het menu **Build** de optie **Build Solution** .

    De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.

### <a name="how-to-run-the-sample"></a>Het voorbeeld uitvoeren

1. Maak de volgende module map:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Kopieer de voor beeld-assembly naar de module map.

3. Start Windows PowerShell.

4. Voer de volgende opdracht uit om de assembly in Windows Power shell te laden:

    `Import-module getprossessample04`

5. Voer de volgende opdracht uit om de cmdlet uit te voeren:

    `get-proc`

## <a name="requirements"></a>Vereisten

Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Demonstreert

In dit voor beeld ziet u het volgende.

- Het declareren van een cmdlet-klasse met het cmdlet-kenmerk.

- Declareer een cmdlet-para meter met het parameter kenmerk.

- De positie van de para meter opgeven.

- Opgeven dat de para meter invoer van de pijp lijn gebruikt. De invoer kan worden gemaakt op basis van een object of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.

- Het declareren van een validatie kenmerk voor de parameter invoer.

- Er wordt een niet-afsluit fout overgevuld en er wordt een fout bericht naar de fout stroom geschreven.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u een cmdlet maakt waarmee niet-afsluit fouten worden verwerkt en fout berichten naar de fout stroom worden geschreven.

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
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
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
