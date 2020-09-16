---
title: GetProcessSample01-voor beeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 84956fbafdd58623ca4f332efc940fb93b421c6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784245"
---
# <a name="getprocesssample01-sample"></a>Voorbeeld GetProcessSample01

In dit voor beeld ziet u hoe u een cmdlet implementeert waarmee de processen op de lokale computer worden opgehaald. Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt meegeleverd met Windows Power shell 2,0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Het voor beeld maken met behulp van Visual Studio.

1. Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample01. De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Dubbel klik op het pictogram van het oplossings bestand (. SLN). Hiermee opent u het voorbeeld project in micro soft Visual Studio.

3. Selecteer in het menu **Build** de optie **Build Solution**.

  De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.

### <a name="how-to-run-the-sample"></a>Het voorbeeld uitvoeren

1. Open een opdrachtpromptvenster.

2. Navigeer naar de map met het bestand Sample. dll.

3. Voer InstallUtil ' GetProcessSample01.dll ' uit.

4. Start Windows PowerShell.

5. Voer de volgende opdracht uit om de module toe te voegen aan de shell.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Voer de volgende opdracht in om de cmdlet uit te voeren. `get-proc`

   `get-proc`

   Dit is een voorbeeld uitvoer die het gevolg is van de volgende stappen.

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

Voor dit voor beeld is Windows Power shell 1,0 of hoger vereist.

## <a name="demonstrates"></a>Demonstreert

In dit voor beeld ziet u het volgende.

- Een eenvoudige voor beeld-cmdlet maken.

- Een cmdlet-klasse definiëren met behulp van het cmdlet-kenmerk.

- Er wordt een module gemaakt die werkt met Windows Power shell 1,0 en Windows Power Shell 2,0. In de volgende voor beelden worden modules gebruikt in plaats van modules, zodat ze Windows Power Shell 2,0 nodig hebben.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u een eenvoudige cmdlet en de bijbehorende module maakt.

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

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
