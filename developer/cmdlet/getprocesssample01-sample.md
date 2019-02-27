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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849495"
---
# <a name="getprocesssample01-sample"></a><span data-ttu-id="c570e-102">Voorbeeld GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="c570e-102">GetProcessSample01 Sample</span></span>

<span data-ttu-id="c570e-103">Dit voorbeeld laat zien hoe u voor het implementeren van een cmdlet die worden opgehaald van de processen die op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c570e-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="c570e-104">Deze cmdlet is een vereenvoudigde versie van de `Get-Process` cmdlet die wordt geleverd door Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c570e-104">This cmdlet is a simplified version of the `Get-Process` cmdlet that is provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="c570e-105">Over het bouwen van het voorbeeld met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c570e-105">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="c570e-106">Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="c570e-106">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample01 folder.</span></span> <span data-ttu-id="c570e-107">De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span><span class="sxs-lookup"><span data-stu-id="c570e-107">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.</span></span>

2. <span data-ttu-id="c570e-108">Dubbelklik op het pictogram voor het oplossingsbestand (.sln).</span><span class="sxs-lookup"><span data-stu-id="c570e-108">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="c570e-109">Hiermee opent u het voorbeeldproject in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c570e-109">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="c570e-110">In de **bouwen** in het menu **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="c570e-110">In the **Build** menu, select **Build Solution**.</span></span>

  <span data-ttu-id="c570e-111">De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.</span><span class="sxs-lookup"><span data-stu-id="c570e-111">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="c570e-112">Hoe u het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="c570e-112">How to run the sample</span></span>

1. <span data-ttu-id="c570e-113">Open een opdrachtpromptvenster.</span><span class="sxs-lookup"><span data-stu-id="c570e-113">Open a Command Prompt window.</span></span>

2. <span data-ttu-id="c570e-114">Navigeer naar de map met het voorbeeld DLL-bestand.</span><span class="sxs-lookup"><span data-stu-id="c570e-114">Navigate to the directory containing the sample .dll file.</span></span>

3. <span data-ttu-id="c570e-115">Installutil 'GetProcessSample01.dll' worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c570e-115">Run installutil "GetProcessSample01.dll".</span></span>

4. <span data-ttu-id="c570e-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c570e-116">Start Windows PowerShell.</span></span>

5. <span data-ttu-id="c570e-117">Voer de volgende opdracht om toe te voegen de module in de shell.</span><span class="sxs-lookup"><span data-stu-id="c570e-117">Run the following command to add the snap-in to the shell.</span></span>

   `Add-PSSnapin GetProcPSSnapIn01`

6. <span data-ttu-id="c570e-118">Voer de volgende opdracht om uit te voeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c570e-118">Enter the following command to run the cmdlet.</span></span> `get-proc`

   `get-proc`

   <span data-ttu-id="c570e-119">Dit is een voorbeeld van de uitvoer die het resultaat is van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="c570e-119">This is a sample output that results from following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="c570e-120">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c570e-120">Requirements</span></span>

<span data-ttu-id="c570e-121">In dit voorbeeld vereist Windows PowerShell 1.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="c570e-121">This sample requires Windows PowerShell 1.0 or later.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="c570e-122">Hier ziet u</span><span class="sxs-lookup"><span data-stu-id="c570e-122">Demonstrates</span></span>

<span data-ttu-id="c570e-123">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="c570e-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="c570e-124">Het maken van een eenvoudig voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c570e-124">Creating a basic sample cmdlet.</span></span>

- <span data-ttu-id="c570e-125">Het definiëren van een cmdlet-klasse met behulp van de Cmdlet-kenmerk.</span><span class="sxs-lookup"><span data-stu-id="c570e-125">Defining a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="c570e-126">Het maken van een module die geschikt is voor zowel Windows PowerShell 1.0 en Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c570e-126">Creating a snap-in that works with both Windows PowerShell 1.0 and Windows PowerShell 2.0.</span></span> <span data-ttu-id="c570e-127">Opeenvolgende voorbeelden gebruiken modules in plaats van modules, zodat ze Windows PowerShell 2.0 is vereist.</span><span class="sxs-lookup"><span data-stu-id="c570e-127">Subsequent samples use modules instead of snap-ins so they require Windows PowerShell 2.0.</span></span>

## <a name="example"></a><span data-ttu-id="c570e-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="c570e-128">Example</span></span>

<span data-ttu-id="c570e-129">Dit voorbeeld laat zien hoe u een eenvoudige cmdlet en de module maakt.</span><span class="sxs-lookup"><span data-stu-id="c570e-129">This sample shows how to create a simple cmdlet and its snap-in.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c570e-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c570e-130">See Also</span></span>

[<span data-ttu-id="c570e-131">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c570e-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)