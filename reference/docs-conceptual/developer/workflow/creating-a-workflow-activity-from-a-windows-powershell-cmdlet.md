---
title: Een werk stroom activiteit maken op basis van een Windows Power shell-cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: f45b5e985fa38ca4ff41707f1842ddb8b930e2b1
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557496"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a>Een werkstroomactiviteit maken uit een Windows PowerShell-cmdlet

Een Windows Power shell-module of-cmdlet kan worden verpakt als een werk stroom activiteit met behulp van de methoden van de klasse [micro soft. Power shell. activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) . Gebruik de methoden [micro soft. Power shell. activities. Activitygenerator. Generatefrommoduleinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft. Power shell. activities. Activitygenerator. Generatefromcommandinfo *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)en micro soft. Power shell. activities [. Activitygenerator. Generatefromname *](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) van de klasse [micro soft. Power shell. activities. Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) om C#-code te genereren die een activiteit vertegenwoordigt. Vervolgens kunt u de resulterende C#-code compileren in een assembly die als activiteit kan worden toegevoegd aan een project.

U kunt vervolgens de resulterende C#-code compileren in een assembly die als activiteit kan worden toegevoegd aan een project met behulp van een opdracht regel met het volgende formulier.

**CSC/nologo/out: Assemblyname/target: bibliotheek/Reference: System. activities. activity/Reference: micro soft. Power shell. activities codefile.cs**

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u C#-code voor een activiteit kunt genereren vanuit een Windows Power shell-module.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a>Voorbeeld

In het volgende voor beeld ziet u hoe u C#-code voor een activiteit genereert vanuit een Windows Power shell-cmdlet.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```
