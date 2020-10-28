---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld GetProcessSample01
description: Voorbeeld GetProcessSample01
ms.openlocfilehash: 159c277d17a8551d2b5c52377a230babacafc9ab
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652769"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="28637-103">Voorbeeld GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="28637-103">GetProcessSample01 Sample</span></span>

<span data-ttu-id="28637-104">In dit voor beeld ziet u hoe u een cmdlet implementeert waarmee de processen op de lokale computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="28637-104">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="28637-105">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt meegeleverd met Windows Power shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="28637-105">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="28637-106">Het voor beeld maken met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28637-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="28637-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="28637-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="28637-108">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="28637-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="28637-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="28637-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="28637-110">Hiermee opent u het voorbeeld project in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28637-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="28637-111">Selecteer in het menu **Build** de optie **Build Solution** .</span><span class="sxs-lookup"><span data-stu-id="28637-111">In the **Build** menu, select **Build Solution** .</span></span>

  <span data-ttu-id="28637-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="28637-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="28637-113">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="28637-113">How to run the sample</span></span>

1. <span data-ttu-id="28637-114">Open een opdrachtpromptvenster.</span><span class="sxs-lookup"><span data-stu-id="28637-114">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="28637-115">Navigeer naar de map met het bestand Sample. dll.</span><span class="sxs-lookup"><span data-stu-id="28637-115">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="28637-116">Voer InstallUtil ' GetProcessSample01.dll ' uit.</span><span class="sxs-lookup"><span data-stu-id="28637-116">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="28637-117">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28637-117">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="28637-118">Voer de volgende opdracht uit om de module toe te voegen aan de shell.</span><span class="sxs-lookup"><span data-stu-id="28637-118">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="28637-119">Voer de volgende opdracht in om de cmdlet uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="28637-119">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="28637-120">Dit is een voorbeeld uitvoer die het gevolg is van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="28637-120">This is a sample output that results from following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="28637-121">Vereisten</span><span class="sxs-lookup"><span data-stu-id="28637-121">Requirements</span></span>

<span data-ttu-id="28637-122">Voor dit voor beeld is Windows Power shell 1,0 of hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="28637-122">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="28637-123">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="28637-123">Demonstrates</span></span>

<span data-ttu-id="28637-124">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="28637-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="28637-125">Een eenvoudige voor beeld-cmdlet maken.</span><span class="sxs-lookup"><span data-stu-id="28637-125">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="28637-126">Een cmdlet-klasse definiëren met behulp van het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="28637-126">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="28637-127">Er wordt een module gemaakt die werkt met Windows Power shell 1,0 en Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="28637-127">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="28637-128">In de volgende voor beelden worden modules gebruikt in plaats van modules, zodat ze Windows Power Shell 2,0 nodig hebben.</span><span class="sxs-lookup"><span data-stu-id="28637-128">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="28637-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="28637-129">Example</span></span>

<span data-ttu-id="28637-130">In dit voor beeld ziet u hoe u een eenvoudige cmdlet en de bijbehorende module maakt.</span><span class="sxs-lookup"><span data-stu-id="28637-130">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="28637-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="28637-131">See Also</span></span>

[<span data-ttu-id="28637-132">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="28637-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
