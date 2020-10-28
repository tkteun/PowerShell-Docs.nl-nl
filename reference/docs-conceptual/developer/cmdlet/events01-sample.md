---
ms.date: 09/13/2016
ms.topic: reference
title: Voorbeeld Events01
description: Voorbeeld Events01
ms.openlocfilehash: 1d9ef1f71fe38ca788cc50c02367701986ed87b2
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652963"
---
# <a name="events01-sample"></a><span data-ttu-id="73b2d-103">Voorbeeld Events01</span><span class="sxs-lookup"><span data-stu-id="73b2d-103">Events01 Sample</span></span>

<span data-ttu-id="73b2d-104">In dit voor beeld ziet u hoe u een cmdlet maakt waarmee de gebruiker zich kan registreren voor gebeurtenissen die worden gegenereerd door [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="73b2d-104">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="73b2d-105">Met deze cmdlet kunnen gebruikers een actie registreren die moet worden uitgevoerd wanneer een bestand wordt gemaakt in een specifieke map.</span><span class="sxs-lookup"><span data-stu-id="73b2d-105">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="73b2d-106">Dit voor beeld is afgeleid van de basis klasse [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .</span><span class="sxs-lookup"><span data-stu-id="73b2d-106">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="73b2d-107">Het voor beeld maken met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73b2d-107">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="73b2d-108">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map Events01.</span><span class="sxs-lookup"><span data-stu-id="73b2d-108">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="73b2d-109">De standaardlocatie is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="73b2d-109">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="73b2d-110">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="73b2d-110">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="73b2d-111">Hiermee opent u het voorbeeld project in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73b2d-111">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="73b2d-112">Selecteer in het menu **Build** de optie **Build Solution** .</span><span class="sxs-lookup"><span data-stu-id="73b2d-112">In the **Build** menu, select **Build Solution** .</span></span>
   <span data-ttu-id="73b2d-113">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard- `\bin` of- `\bin\debug` mappen.</span><span class="sxs-lookup"><span data-stu-id="73b2d-113">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="73b2d-114">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="73b2d-114">How to run the sample</span></span>

1. <span data-ttu-id="73b2d-115">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="73b2d-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="73b2d-116">Kopieer het bibliotheek bestand voor het voor beeld naar de map module.</span><span class="sxs-lookup"><span data-stu-id="73b2d-116">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="73b2d-117">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="73b2d-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="73b2d-118">Voer de volgende opdracht uit om de cmdlet in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="73b2d-118">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="73b2d-119">Gebruik de cmdlet Register-FileSystemEvent om een actie te registreren waarmee een bericht wordt geschreven wanneer een bestand wordt gemaakt in de map TEMP.</span><span class="sxs-lookup"><span data-stu-id="73b2d-119">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="73b2d-120">Maak een bestand in de map TEMP en houd er rekening mee dat de actie wordt uitgevoerd (het bericht wordt weer gegeven).</span><span class="sxs-lookup"><span data-stu-id="73b2d-120">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="73b2d-121">Dit is een voor beeld van een uitvoer die het resultaat is van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="73b2d-121">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="73b2d-122">Vereisten</span><span class="sxs-lookup"><span data-stu-id="73b2d-122">Requirements</span></span>

<span data-ttu-id="73b2d-123">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="73b2d-123">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="73b2d-124">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="73b2d-124">Demonstrates</span></span>

<span data-ttu-id="73b2d-125">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="73b2d-125">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="73b2d-126">Een cmdlet schrijven voor gebeurtenis registratie</span><span class="sxs-lookup"><span data-stu-id="73b2d-126">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="73b2d-127">De cmdlet is afgeleid van de klasse [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , die ondersteuning biedt voor de algemene para meters van de `Register-*Event` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="73b2d-127">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="73b2d-128">Cmdlets die zijn afgeleid van [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) hoeven alleen de specifieke para meters te definiëren en de `GetSourceObject` en `GetSourceObjectEventName` abstracte methoden te negeren.</span><span class="sxs-lookup"><span data-stu-id="73b2d-128">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="73b2d-129">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="73b2d-129">Example</span></span>

<span data-ttu-id="73b2d-130">In dit voor beeld ziet u hoe u zich registreert voor gebeurtenissen die worden gegenereerd door [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="73b2d-130">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="73b2d-131">Zie ook</span><span class="sxs-lookup"><span data-stu-id="73b2d-131">See Also</span></span>

[<span data-ttu-id="73b2d-132">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="73b2d-132">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
