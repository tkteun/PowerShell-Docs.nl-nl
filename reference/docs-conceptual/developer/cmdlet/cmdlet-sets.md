---
title: Cmdlet-sets | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9595c9ca09148de05c69d60a2ede5688c3db61b0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774810"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="2ea64-102">Cmdlet-reeksen</span><span class="sxs-lookup"><span data-stu-id="2ea64-102">Cmdlet Sets</span></span>

<span data-ttu-id="2ea64-103">Wanneer u uw cmdlets ontwerpt, kunt u gevallen tegen komen waarin u verschillende acties moet uitvoeren op hetzelfde gegevens gedeelte.</span><span class="sxs-lookup"><span data-stu-id="2ea64-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="2ea64-104">U moet bijvoorbeeld gegevens ophalen en instellen, of een proces starten en stoppen.</span><span class="sxs-lookup"><span data-stu-id="2ea64-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="2ea64-105">Hoewel u afzonderlijke cmdlets moet maken om elke actie uit te voeren, moet uw cmdlet-ontwerp een basis klasse bevatten waarvan de klassen voor de afzonderlijke cmdlets worden afgeleid.</span><span class="sxs-lookup"><span data-stu-id="2ea64-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="2ea64-106">Houd bij het implementeren van een basis klasse de volgende aandachtspunten in acht.</span><span class="sxs-lookup"><span data-stu-id="2ea64-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="2ea64-107">Declareer alle algemene para meters die worden gebruikt door alle afgeleide cmdlets in de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="2ea64-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="2ea64-108">Voeg cmdlet-specifieke para meters toe aan de juiste cmdlet-klasse.</span><span class="sxs-lookup"><span data-stu-id="2ea64-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="2ea64-109">Overschrijf de juiste invoer verwerkings methode in de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="2ea64-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="2ea64-110">Declareer het kenmerk [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) op alle cmdlet-klassen, maar Declareer het niet in de basis klasse.</span><span class="sxs-lookup"><span data-stu-id="2ea64-110">Declare the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="2ea64-111">Implementeer een [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -of [System. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) -klasse waarvan de naam en beschrijving overeenkomen met de set cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2ea64-111">Implement a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="2ea64-112">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="2ea64-112">Example</span></span>

<span data-ttu-id="2ea64-113">In het volgende voor beeld ziet u de implementatie van een basis klasse die wordt gebruikt door de cmdlet Get-proc en stop-proc die is afgeleid van dezelfde basis klasse.</span><span class="sxs-lookup"><span data-stu-id="2ea64-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2ea64-114">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2ea64-114">See Also</span></span>

[<span data-ttu-id="2ea64-115">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="2ea64-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
