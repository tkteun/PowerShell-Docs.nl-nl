---
title: Events01-voor beeld | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7b0f759ca6f3c078649a462eac1713e8214a237
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774454"
---
# <a name="events01-sample"></a><span data-ttu-id="21196-102">Voorbeeld Events01</span><span class="sxs-lookup"><span data-stu-id="21196-102">Events01 Sample</span></span>

<span data-ttu-id="21196-103">In dit voor beeld ziet u hoe u een cmdlet maakt waarmee de gebruiker zich kan registreren voor gebeurtenissen die worden gegenereerd door [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="21196-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="21196-104">Met deze cmdlet kunnen gebruikers een actie registreren die moet worden uitgevoerd wanneer een bestand wordt gemaakt in een specifieke map.</span><span class="sxs-lookup"><span data-stu-id="21196-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="21196-105">Dit voor beeld is afgeleid van de basis klasse [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .</span><span class="sxs-lookup"><span data-stu-id="21196-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="21196-106">Het voor beeld maken met behulp van Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="21196-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="21196-107">Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map Events01.</span><span class="sxs-lookup"><span data-stu-id="21196-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="21196-108">De standaardlocatie is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="21196-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="21196-109">Dubbel klik op het pictogram van het oplossings bestand (. SLN).</span><span class="sxs-lookup"><span data-stu-id="21196-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="21196-110">Hiermee opent u het voorbeeld project in micro soft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="21196-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="21196-111">Selecteer in het menu **Build** de optie **Build Solution**.</span><span class="sxs-lookup"><span data-stu-id="21196-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="21196-112">De bibliotheek voor het voor beeld wordt opgebouwd in de standaard- `\bin` of- `\bin\debug` mappen.</span><span class="sxs-lookup"><span data-stu-id="21196-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="21196-113">Het voorbeeld uitvoeren</span><span class="sxs-lookup"><span data-stu-id="21196-113">How to run the sample</span></span>

1. <span data-ttu-id="21196-114">Maak de volgende module map:</span><span class="sxs-lookup"><span data-stu-id="21196-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="21196-115">Kopieer het bibliotheek bestand voor het voor beeld naar de map module.</span><span class="sxs-lookup"><span data-stu-id="21196-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="21196-116">Start Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21196-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="21196-117">Voer de volgende opdracht uit om de cmdlet in Windows Power shell te laden:</span><span class="sxs-lookup"><span data-stu-id="21196-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="21196-118">Gebruik de cmdlet REGI ster-FileSystemEvent om een actie te registreren waarmee een bericht wordt geschreven wanneer een bestand wordt gemaakt in de map TEMP.</span><span class="sxs-lookup"><span data-stu-id="21196-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="21196-119">Maak een bestand in de map TEMP en houd er rekening mee dat de actie wordt uitgevoerd (het bericht wordt weer gegeven).</span><span class="sxs-lookup"><span data-stu-id="21196-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="21196-120">Dit is een voor beeld van een uitvoer die het resultaat is van de volgende stappen.</span><span class="sxs-lookup"><span data-stu-id="21196-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="21196-121">Vereisten</span><span class="sxs-lookup"><span data-stu-id="21196-121">Requirements</span></span>

<span data-ttu-id="21196-122">Voor dit voor beeld is Windows Power Shell 2,0 vereist.</span><span class="sxs-lookup"><span data-stu-id="21196-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="21196-123">Demonstreert</span><span class="sxs-lookup"><span data-stu-id="21196-123">Demonstrates</span></span>

<span data-ttu-id="21196-124">In dit voor beeld ziet u het volgende.</span><span class="sxs-lookup"><span data-stu-id="21196-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="21196-125">Een cmdlet schrijven voor gebeurtenis registratie</span><span class="sxs-lookup"><span data-stu-id="21196-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="21196-126">De cmdlet is afgeleid van de klasse [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , die ondersteuning biedt voor de algemene para meters van de `Register-*Event` cmdlets.</span><span class="sxs-lookup"><span data-stu-id="21196-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="21196-127">Cmdlets die zijn afgeleid van [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) hoeven alleen de specifieke para meters te definiëren en de `GetSourceObject` en `GetSourceObjectEventName` abstracte methoden te negeren.</span><span class="sxs-lookup"><span data-stu-id="21196-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="21196-128">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="21196-128">Example</span></span>

<span data-ttu-id="21196-129">In dit voor beeld ziet u hoe u zich registreert voor gebeurtenissen die worden gegenereerd door [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="21196-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="21196-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="21196-130">See Also</span></span>

[<span data-ttu-id="21196-131">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="21196-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
