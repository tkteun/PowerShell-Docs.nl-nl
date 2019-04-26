---
title: Voorbeeld van GetProcessSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068025"
---
# <a name="getprocesssample04-sample"></a>Voorbeeld GetProcessSample04

Dit voorbeeld laat zien hoe u voor het implementeren van een cmdlet die worden opgehaald van de processen die op de lokale computer. Er wordt een nonterminating fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces. Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet geleverd door Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Over het bouwen van het voorbeeld met behulp van Visual Studio.

1. Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample04. De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Dubbelklik op het pictogram voor het oplossingsbestand (.sln). Hiermee opent u het voorbeeldproject in Visual Studio.

3. In de **bouwen** in het menu **Build Solution**.

    De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.

### <a name="how-to-run-the-sample"></a>Hoe u het voorbeeld uitvoeren

1. Maak de volgende modulemap:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Kopieer de voorbeeld-assembly naar de modulemap.

3. Start Windows PowerShell.

4. Voer de volgende opdracht om het laden van de assembly in Windows PowerShell:

    `Import-module getprossessample04`

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

- Een nonterminating fout overlapping van en schrijven van een foutbericht naar de foutstroom.

## <a name="example"></a>Voorbeeld

Dit voorbeeld laat zien hoe u een cmdlet die afsluitfouten worden verwerkt en foutberichten schrijft naar de foutstroom maakt.

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
