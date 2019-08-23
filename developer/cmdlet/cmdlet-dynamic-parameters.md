---
title: Cmdlet dynamische para meters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 19d31f6b619dff23e7e35bb53d2397f4f41eb728
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986243"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="0d355-102">Cmdlet dynamische para meters</span><span class="sxs-lookup"><span data-stu-id="0d355-102">Cmdlet dynamic parameters</span></span>

<span data-ttu-id="0d355-103">Met cmdlets kunt u para meters definiëren die beschikbaar zijn voor de gebruiker onder speciale omstandigheden, zoals wanneer het argument van een andere para meter een specifieke waarde is.</span><span class="sxs-lookup"><span data-stu-id="0d355-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="0d355-104">Deze para meters worden toegevoegd tijdens runtime en worden aangeduid als dynamische para meters, omdat ze alleen worden toegevoegd wanneer dit nodig is.</span><span class="sxs-lookup"><span data-stu-id="0d355-104">These parameters are added at runtime and are referred to as dynamic parameters because they're only added when needed.</span></span> <span data-ttu-id="0d355-105">U kunt bijvoorbeeld een cmdlet ontwerpen waarmee meerdere para meters worden toegevoegd wanneer een specifieke switch parameter wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0d355-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="0d355-106">Providers en Power shell-functies kunnen ook dynamische para meters definiëren.</span><span class="sxs-lookup"><span data-stu-id="0d355-106">Providers and PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-powershell-cmdlets"></a><span data-ttu-id="0d355-107">Dynamische para meters in Power shell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="0d355-107">Dynamic parameters in PowerShell cmdlets</span></span>

<span data-ttu-id="0d355-108">Power shell gebruikt dynamische para meters in verschillende provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="0d355-108">PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="0d355-109">De `Get-Item` `Get-ChildItem` cmdlets en voegen bijvoorbeeld tijdens runtime een **CodeSigningCert** -para meter toe wanneer de para meter **Path** het pad naar de **certificaat** provider specificeert.</span><span class="sxs-lookup"><span data-stu-id="0d355-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a **CodeSigningCert** parameter at runtime when the **Path** parameter specifies the **Certificate** provider path.</span></span> <span data-ttu-id="0d355-110">Als met de para meter **Path** een pad voor een andere provider wordt opgegeven, is de para meter **CodeSigningCert** niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="0d355-110">If the **Path** parameter specifies a path for a different provider, the **CodeSigningCert** parameter isn't available.</span></span>

<span data-ttu-id="0d355-111">In de volgende voor beelden ziet u hoe de para meter **CodeSigningCert** wordt `Get-Item` toegevoegd tijdens runtime wanneer wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="0d355-111">The following examples show how the **CodeSigningCert** parameter is added at runtime when `Get-Item` is run.</span></span>

<span data-ttu-id="0d355-112">In dit voor beeld heeft de Power shell-runtime de para meter toegevoegd en is de cmdlet geslaagd.</span><span class="sxs-lookup"><span data-stu-id="0d355-112">In this example, the PowerShell runtime has added the parameter and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -CodeSigningCert
```

```Output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="0d355-113">In dit voor beeld wordt een bestandssysteem station opgegeven en wordt er een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="0d355-113">In this example, a **FileSystem** drive is specified and an error is returned.</span></span> <span data-ttu-id="0d355-114">Het fout bericht geeft aan dat de para meter **CodeSigningCert** niet kan worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="0d355-114">The error message indicates that the **CodeSigningCert** parameter can't be found.</span></span>

```powershell
Get-Item -Path C:\ -CodeSigningCert
```

```Output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="0d355-115">Ondersteuning voor dynamische para meters</span><span class="sxs-lookup"><span data-stu-id="0d355-115">Support for dynamic parameters</span></span>

<span data-ttu-id="0d355-116">Voor het ondersteunen van dynamische para meters moeten de volgende elementen worden opgenomen in de cmdlet-code.</span><span class="sxs-lookup"><span data-stu-id="0d355-116">To support dynamic parameters, the following elements must be included in the cmdlet code.</span></span>

### <a name="interface"></a><span data-ttu-id="0d355-117">Interface</span><span class="sxs-lookup"><span data-stu-id="0d355-117">Interface</span></span>

<span data-ttu-id="0d355-118">[System. Management. Automation. IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="0d355-118">[System.Management.Automation.IDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters).</span></span>
<span data-ttu-id="0d355-119">Deze interface biedt de methode waarmee de dynamische para meters worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="0d355-119">This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="0d355-120">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0d355-120">For example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

### <a name="method"></a><span data-ttu-id="0d355-121">Methode</span><span class="sxs-lookup"><span data-stu-id="0d355-121">Method</span></span>

<span data-ttu-id="0d355-122">[System. Management. Automation. IDynamicParameters. GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span><span class="sxs-lookup"><span data-stu-id="0d355-122">[System.Management.Automation.IDynamicParameters.GetDynamicParameters](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters).</span></span>
<span data-ttu-id="0d355-123">Deze methode haalt het object op dat de dynamische parameter definities bevat.</span><span class="sxs-lookup"><span data-stu-id="0d355-123">This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="0d355-124">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0d355-124">For example:</span></span>

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

### <a name="class"></a><span data-ttu-id="0d355-125">Klasse</span><span class="sxs-lookup"><span data-stu-id="0d355-125">Class</span></span>

<span data-ttu-id="0d355-126">Een klasse die de dynamische para meters definieert die moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="0d355-126">A class that defines the dynamic parameters to be added.</span></span> <span data-ttu-id="0d355-127">Deze klasse moet een **parameter** kenmerk voor elke para meter en eventuele optionele **alias** -en **validatie** kenmerken bevatten die nodig zijn voor de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d355-127">This class must include a **Parameter** attribute for each parameter and any optional **Alias** and **Validation** attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="0d355-128">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="0d355-128">For example:</span></span>

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

<span data-ttu-id="0d355-129">Zie [dynamische para meters declareren](./how-to-declare-dynamic-parameters.md)voor een volledig voor beeld van een cmdlet die dynamische para meters ondersteunt.</span><span class="sxs-lookup"><span data-stu-id="0d355-129">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d355-130">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0d355-130">See also</span></span>

[<span data-ttu-id="0d355-131">System. Management. Automation. IDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="0d355-131">System.Management.Automation.IDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="0d355-132">System. Management. Automation. IDynamicParameters. GetDynamicParameters</span><span class="sxs-lookup"><span data-stu-id="0d355-132">System.Management.Automation.IDynamicParameters.GetDynamicParameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="0d355-133">Dynamische para meters declareren</span><span class="sxs-lookup"><span data-stu-id="0d355-133">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="0d355-134">Een Windows Power shell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="0d355-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
