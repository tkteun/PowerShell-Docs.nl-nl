---
title: Voorbeeld van Events01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: c9963819f1842d1245735dabc487babaa566c160
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068127"
---
# <a name="events01-sample"></a><span data-ttu-id="8a3b1-102">Voorbeeld Events01</span><span class="sxs-lookup"><span data-stu-id="8a3b1-102">Events01 Sample</span></span>

<span data-ttu-id="8a3b1-103">Dit voorbeeld laat zien over het maken van een cmdlet waarmee de gebruiker om u te registreren voor gebeurtenissen die worden gegenereerd door [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="8a3b1-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="8a3b1-104">Met deze cmdlet, kunnen gebruikers zich registreren een actie om uit te voeren wanneer een bestand wordt gemaakt onder een specifieke map.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="8a3b1-105">In dit voorbeeld is afgeleid van de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) basisklasse.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-105">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="8a3b1-106">Over het bouwen van het voorbeeld met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="8a3b1-107">Met de Windows PowerShell 2.0 SDK is geïnstalleerd, gaat u naar de map Events01.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span> <span data-ttu-id="8a3b1-108">De standaardlocatie is C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01.</span></span>

2. <span data-ttu-id="8a3b1-109">Dubbelklik op het pictogram voor het oplossingsbestand (.sln).</span><span class="sxs-lookup"><span data-stu-id="8a3b1-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="8a3b1-110">Hiermee opent u het voorbeeldproject in Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="8a3b1-111">In de **bouwen** in het menu **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="8a3b1-112">De bibliotheek voor het voorbeeld worden in de standaard \bin of \bin\debug mappen samengesteld.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="8a3b1-113">Hoe u het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="8a3b1-113">How to run the sample</span></span>

1. <span data-ttu-id="8a3b1-114">Maak de volgende modulemap:</span><span class="sxs-lookup"><span data-stu-id="8a3b1-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="8a3b1-115">Kopieer het DLL-bestand voor het voorbeeld naar de modulemap.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="8a3b1-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="8a3b1-117">Voer de volgende opdracht om het laden van de cmdlet in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8a3b1-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="8a3b1-118">Gebruik de cmdlet Register-FileSystemEvent voor het registreren van een actie die een bericht wordt geschreven wanneer een bestand wordt gemaakt in de map TEMP.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="8a3b1-119">Maak een bestand in de map TEMP en houd er rekening mee dat de actie wordt uitgevoerd (het bericht wordt weergegeven).</span><span class="sxs-lookup"><span data-stu-id="8a3b1-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="8a3b1-120">Dit is een voorbeeld van de uitvoer die het resultaat is door deze stappen te volgen.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="8a3b1-121">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8a3b1-121">Requirements</span></span>

<span data-ttu-id="8a3b1-122">In dit voorbeeld is Windows PowerShell 2.0 vereist.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8a3b1-123">Ziet u</span><span class="sxs-lookup"><span data-stu-id="8a3b1-123">Demonstrates</span></span>

<span data-ttu-id="8a3b1-124">In dit voorbeeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-124">This sample demonstrates the following.</span></span>

- <span data-ttu-id="8a3b1-125">Over het schrijven van een cmdlet voor gebeurtenisregistratie.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-125">How to write a cmdlet for event registration.</span></span> <span data-ttu-id="8a3b1-126">De cmdlet is afgeleid van de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) klasse, die ondersteuning voor algemene parameters met de Register biedt-\*-cmdlets gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the Register-\*Event cmdlets.</span></span> <span data-ttu-id="8a3b1-127">Cmdlets die zijn afgeleid van [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) moet alleen de specifieke parameters definiëren en overschrijven de `GetSourceObject` en `GetSourceObjectEventName` abstracte methoden.</span><span class="sxs-lookup"><span data-stu-id="8a3b1-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="8a3b1-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="8a3b1-128">Example</span></span>

<span data-ttu-id="8a3b1-129">In dit voorbeeld laat zien hoe u zich registreren voor gebeurtenissen die worden gegenereerd door [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="8a3b1-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](https://msdn.microsoft.com/en-us/library/system.io.filesystemwatcher\(v=vs.110\).aspx).</span></span>

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="8a3b1-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8a3b1-130">See Also</span></span>

[<span data-ttu-id="8a3b1-131">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8a3b1-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)