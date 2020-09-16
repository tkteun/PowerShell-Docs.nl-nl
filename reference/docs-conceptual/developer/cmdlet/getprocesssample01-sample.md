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
# <a name="getprocesssample01-sample"></a><span data-ttu-id="40d02-102">Voorbeeld GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="40d02-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="40d02-103">In dit voor beeld ziet u hoe u een cmdlet implementeert waarmee de processen op de lokale computer worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="40d02-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="40d02-104">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt meegeleverd met Windows Power shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="40d02-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="40d02-105">Het voor beeld maken met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40d02-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="40d02-106">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="40d02-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="40d02-107">De standaard locatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="40d02-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="40d02-108">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="40d02-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="40d02-109">Hiermee opent u het voorbeeld project in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40d02-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="40d02-110">Selecteer in het menu **Build** de optie **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="40d02-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="40d02-111">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard mappen \Bin of \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="40d02-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="40d02-112">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="40d02-112">How to run the sample</span></span>

1. <span data-ttu-id="40d02-113">Open een opdrachtpromptvenster.</span><span class="sxs-lookup"><span data-stu-id="40d02-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="40d02-114">Navigeer naar de map met het bestand Sample. dll.</span><span class="sxs-lookup"><span data-stu-id="40d02-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="40d02-115">Voer InstallUtil ' GetProcessSample01.dll ' uit.</span><span class="sxs-lookup"><span data-stu-id="40d02-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="40d02-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40d02-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="40d02-117">Voer de volgende opdracht uit om de module toe te voegen aan de shell.</span><span class="sxs-lookup"><span data-stu-id="40d02-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="40d02-118">Voer de volgende opdracht in om de cmdlet uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="40d02-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="40d02-119">Dit is een voorbeeld uitvoer die het gevolg is van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="40d02-119">This is a sample output that results from following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="40d02-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="40d02-120">Requirements</span></span>

<span data-ttu-id="40d02-121">Voor dit voor beeld is Windows Power shell 1,0 of hoger vereist.</span><span class="sxs-lookup"><span data-stu-id="40d02-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="40d02-122">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="40d02-122">Demonstrates</span></span>

<span data-ttu-id="40d02-123">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="40d02-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="40d02-124">Een eenvoudige voor beeld-cmdlet maken.</span><span class="sxs-lookup"><span data-stu-id="40d02-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="40d02-125">Een cmdlet-klasse definiëren met behulp van het cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="40d02-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="40d02-126">Er wordt een module gemaakt die werkt met Windows Power shell 1,0 en Windows Power Shell 2,0.</span><span class="sxs-lookup"><span data-stu-id="40d02-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="40d02-127">In de volgende voor beelden worden modules gebruikt in plaats van modules, zodat ze Windows Power Shell 2,0 nodig hebben.</span><span class="sxs-lookup"><span data-stu-id="40d02-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="40d02-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="40d02-128">Example</span></span>

<span data-ttu-id="40d02-129">In dit voor beeld ziet u hoe u een eenvoudige cmdlet en de bijbehorende module maakt.</span><span class="sxs-lookup"><span data-stu-id="40d02-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="40d02-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="40d02-130">See Also</span></span>

[<span data-ttu-id="40d02-131">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="40d02-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
