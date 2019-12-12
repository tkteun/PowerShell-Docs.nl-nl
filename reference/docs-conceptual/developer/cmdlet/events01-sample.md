---
title: Events01-voor beeld | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359360"
---
# <a name="events01-sample"></a>Voorbeeld Events01

In dit voor beeld ziet u hoe u een cmdlet maakt waarmee de gebruiker zich kan registreren voor gebeurtenissen die worden gegenereerd door [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).
Met deze cmdlet kunnen gebruikers een actie registreren die moet worden uitgevoerd wanneer een bestand wordt gemaakt in een specifieke map.
Dit voor beeld is afgeleid van de basis klasse [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Het voor beeld maken met behulp van Visual Studio.

1. Terwijl de Windows Power Shell 2,0 SDK is geïnstalleerd, gaat u naar de map Events01.
   De standaard locatie is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Dubbel klik op het pictogram van het oplossings bestand (. SLN).
   Hiermee opent u het voorbeeld project in micro soft Visual Studio.

3. Selecteer in het menu **Build** de optie **Build Solution**.
   De bibliotheek voor het voor beeld wordt opgebouwd in de standaard `\bin` of `\bin\debug` mappen.

### <a name="how-to-run-the-sample"></a>Het voorbeeld uitvoeren

1. Maak de volgende module map:

    `[user]/documents/windowspowershell/modules/events01`

2. Kopieer het bibliotheek bestand voor het voor beeld naar de map module.

3. Start Windows PowerShell.

4. Voer de volgende opdracht uit om de cmdlet in Windows Power shell te laden:

    ```powershell
    import-module events01
    ```

5. Gebruik de cmdlet REGI ster-FileSystemEvent om een actie te registreren waarmee een bericht wordt geschreven wanneer een bestand wordt gemaakt in de map TEMP.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Maak een bestand in de map TEMP en houd er rekening mee dat de actie wordt uitgevoerd (het bericht wordt weer gegeven).

Dit is een voor beeld van een uitvoer die het resultaat is van de volgende stappen.

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

Voor dit voor beeld is Windows Power Shell 2,0 vereist.

## <a name="demonstrates"></a>Hier ziet u

In dit voor beeld ziet u het volgende.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Een cmdlet schrijven voor gebeurtenis registratie

De cmdlet is afgeleid van de klasse [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , die ondersteuning biedt voor algemene para meters voor de `Register-*Event`-cmdlets.
Cmdlets die zijn afgeleid van [micro soft. Power shell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) hoeven alleen de specifieke para meters te definiëren en de `GetSourceObject` en `GetSourceObjectEventName` abstracte methoden te overschrijven.

## <a name="example"></a>Voorbeeld

In dit voor beeld ziet u hoe u zich registreert voor gebeurtenissen die worden gegenereerd door [System. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).

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

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](writing-a-windows-powershell-cmdlet.md)