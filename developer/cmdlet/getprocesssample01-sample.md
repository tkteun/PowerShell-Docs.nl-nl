---
title: Voorbeeld van GetProcessSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068059"
---
# <a name="getprocesssample01-sample"></a>Voorbeeld GetProcessSample01

Dit voorbeeld laat zien hoe u voor het implementeren van een cmdlet die worden opgehaald van de processen die op de lokale computer. Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt geleverd door Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Over het bouwen van het voorbeeld met behulp van Visual Studio.

1. Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample01. De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Dubbelklik op het pictogram voor het oplossingsbestand (.sln). Hiermee opent u het voorbeeldproject in Microsoft Visual Studio.

3. In de **bouwen** in het menu **Build Solution**.

  De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.

### <a name="how-to-run-the-sample"></a>Hoe u het voorbeeld uitvoeren

1. Open een opdrachtpromptvenster.

2. Navigeer naar de map met het voorbeeld DLL-bestand.

3. Installutil 'GetProcessSample01.dll' worden uitgevoerd.

4. Start Windows PowerShell.

5. Voer de volgende opdracht om toe te voegen de module in de shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Voer de volgende opdracht om uit te voeren van de cmdlet. `get-proc`

   `get-proc`

   Dit is een voorbeeld van de uitvoer die het resultaat is van de volgende stappen.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Vereisten

In dit voorbeeld vereist Windows PowerShell 1.0 of hoger.

## <a name="demonstrates"></a>Ziet u

In dit voorbeeld ziet u het volgende.

- Het maken van een eenvoudig voorbeeld-cmdlet.

- Het definiëren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.

- Het maken van een module die geschikt is voor zowel Windows PowerShell 1.0 en Windows PowerShell 2.0. Opeenvolgende voorbeelden gebruiken modules in plaats van modules, zodat ze Windows PowerShell 2.0 is vereist.

## <a name="example"></a>Voorbeeld

Dit voorbeeld laat zien hoe u een eenvoudige cmdlet en de module maakt.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)