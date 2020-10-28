---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-reeksen
description: Cmdlet-reeksen
ms.openlocfilehash: b4bcb6548f9d64a8cc5e3fc3a66c671a5566001d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668232"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="699eb-103">Cmdlet-reeksen</span><span class="sxs-lookup"><span data-stu-id="699eb-103">Cmdlet Sets</span></span>

<span data-ttu-id="699eb-104">Wanneer u uw cmdlets ontwerpt, kunt u gevallen tegen komen waarin u verschillende acties moet uitvoeren op hetzelfde gegevens gedeelte.</span><span class="sxs-lookup"><span data-stu-id="699eb-104">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="699eb-105">U moet bijvoorbeeld gegevens ophalen en instellen, of een proces starten en stoppen.</span><span class="sxs-lookup"><span data-stu-id="699eb-105">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="699eb-106">Hoewel u afzonderlijke cmdlets moet maken om elke actie uit te voeren, moet uw cmdlet-ontwerp een basis klasse bevatten waarvan de klassen voor de afzonderlijke cmdlets worden afgeleid.</span><span class="sxs-lookup"><span data-stu-id="699eb-106">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="699eb-107">Houd bij het implementeren van een basis klasse de volgende aandachtspunten in acht.</span><span class="sxs-lookup"><span data-stu-id="699eb-107">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="699eb-108">Declareer alle algemene para meters die worden gebruikt door alle afgeleide cmdlets in de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="699eb-108">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="699eb-109">Voeg cmdlet-specifieke para meters toe aan de juiste cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="699eb-109">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="699eb-110">Overschrijf de juiste invoer verwerkings methode in de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="699eb-110">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="699eb-111">Declareer het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) op alle cmdlet-klassen, maar Declareer het niet in de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="699eb-111">Declare the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="699eb-112">Implementeer een [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -of [System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) -klasse waarvan de naam en beschrijving overeenkomen met de set cmdlets.</span><span class="sxs-lookup"><span data-stu-id="699eb-112">Implement a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="699eb-113">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="699eb-113">Example</span></span>

<span data-ttu-id="699eb-114">In het volgende voor beeld ziet u de implementatie van een basis klasse die wordt gebruikt door Get-Proc en Stop-Proc cmdlet die is afgeleid van dezelfde basis klasse.</span><span class="sxs-lookup"><span data-stu-id="699eb-114">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProcessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
    [Parameter(
               Position = 0,
               Mandatory = true,
               ValueFromPipeline = true,
               ValueFromPipelineByPropertyName = true
    )]
    public string[] Name
    {
      get { return processNames; }
      set { processNames = value; }
    }
    private string[] processNames;

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard characters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a><span data-ttu-id="699eb-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="699eb-115">See Also</span></span>

[<span data-ttu-id="699eb-116">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="699eb-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
