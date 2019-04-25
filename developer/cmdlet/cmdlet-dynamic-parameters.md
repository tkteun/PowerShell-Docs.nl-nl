---
title: Cmdlet dynamische Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068535"
---
# <a name="cmdlet-dynamic-parameters"></a><span data-ttu-id="b63fb-102">Dynamische cmdlet-parameters</span><span class="sxs-lookup"><span data-stu-id="b63fb-102">Cmdlet Dynamic Parameters</span></span>

<span data-ttu-id="b63fb-103">Cmdlets kunt parameters definiëren die beschikbaar voor de gebruiker in speciale omstandigheden zijn, zoals wanneer het argument van een andere parameter is voor een specifieke waarde.</span><span class="sxs-lookup"><span data-stu-id="b63fb-103">Cmdlets can define parameters that are available to the user under special conditions, such as when the argument of another parameter is a specific value.</span></span> <span data-ttu-id="b63fb-104">Deze parameters worden toegevoegd tijdens runtime en worden aangeduid als *dynamische parameters* omdat ze worden toegevoegd wanneer ze wel nodig zijn.</span><span class="sxs-lookup"><span data-stu-id="b63fb-104">These parameters are added at runtime and are referred to as *dynamic parameters* because they are added only when they are needed.</span></span> <span data-ttu-id="b63fb-105">U kunt bijvoorbeeld een cmdlet die door verschillende parameters worden toegevoegd als een specifieke switch-parameter is opgegeven ontwerpen.</span><span class="sxs-lookup"><span data-stu-id="b63fb-105">For example, you can design a cmdlet that adds several parameters only when a specific switch parameter is specified.</span></span>

> [!NOTE]
> <span data-ttu-id="b63fb-106">Providers en -functies van Windows PowerShell kunnen u ook dynamische parameters definiëren.</span><span class="sxs-lookup"><span data-stu-id="b63fb-106">Providers and Windows PowerShell functions can also define dynamic parameters.</span></span>

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a><span data-ttu-id="b63fb-107">Dynamische Parameters in Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b63fb-107">Dynamic Parameters in Windows PowerShell Cmdlets</span></span>

<span data-ttu-id="b63fb-108">Windows PowerShell maakt gebruik van dynamische parameters in een aantal van de provider-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b63fb-108">Windows PowerShell uses dynamic parameters in several of its provider cmdlets.</span></span> <span data-ttu-id="b63fb-109">Bijvoorbeeld, de `Get-Item` en `Get-ChildItem` cmdlets toevoegen een `CodeSigningCert` parameter tijdens runtime wanneer de `Path` parameter van de cmdlet geeft u het pad naar de provider van het certificaat.</span><span class="sxs-lookup"><span data-stu-id="b63fb-109">For example, the `Get-Item` and `Get-ChildItem` cmdlets add a `CodeSigningCert` parameter at runtime when the `Path` parameter of the cmdlet specifies the Certificate provider path.</span></span> <span data-ttu-id="b63fb-110">Als de `Path` parameter van de cmdlet geeft u het pad voor een andere provider de `CodeSigningCert` parameter is niet beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="b63fb-110">If the `Path` parameter of the cmdlet specifies a path for a different provider, the `CodeSigningCert` parameter is not available.</span></span>

<span data-ttu-id="b63fb-111">De volgende voorbeelden ziet u hoe de `CodeSigningCert` parameter tijdens runtime wordt toegevoegd wanneer de `Get-Item` cmdlet wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b63fb-111">The following examples show how the `CodeSigningCert` parameter is added at runtime when the `Get-Item` cmdlet is run.</span></span>

<span data-ttu-id="b63fb-112">In het eerste voorbeeld, de Windows PowerShell-runtime is toegevoegd met de parameter en de cmdlet is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b63fb-112">In the first example, the Windows PowerShell runtime has added the parameter, and the cmdlet is successful.</span></span>

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

<span data-ttu-id="b63fb-113">Een bestandssysteem-station is opgegeven in het tweede voorbeeld, en wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b63fb-113">In the second example, a FileSystem drive is specified, and an error is returned.</span></span> <span data-ttu-id="b63fb-114">Het foutbericht geeft aan dat de `CodeSigningCert` parameter kan niet worden gevonden.</span><span class="sxs-lookup"><span data-stu-id="b63fb-114">The error message indicates that the `CodeSigningCert` parameter cannot be found.</span></span>

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a><span data-ttu-id="b63fb-115">Ondersteuning voor dynamische Parameters</span><span class="sxs-lookup"><span data-stu-id="b63fb-115">Support for Dynamic Parameters</span></span>

<span data-ttu-id="b63fb-116">Ter ondersteuning van dynamische parameters, moet de cmdlet-code de volgende elementen bevatten.</span><span class="sxs-lookup"><span data-stu-id="b63fb-116">To support dynamic parameters, the cmdlet code must include the following elements.</span></span>

<span data-ttu-id="b63fb-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) deze interface biedt de methode waarmee de dynamische parameters worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="b63fb-117">[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) This interface provides the method that retrieves the dynamic parameters.</span></span>

<span data-ttu-id="b63fb-118">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b63fb-118">Example:</span></span>

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

<span data-ttu-id="b63fb-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) deze methode haalt het object dat de definities van de dynamische parameter bevat.</span><span class="sxs-lookup"><span data-stu-id="b63fb-119">[System.Management.Automation.Idynamicparameters.Getdynamicparameters\*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) This method retrieves the object that contains the dynamic parameter definitions.</span></span>

<span data-ttu-id="b63fb-120">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b63fb-120">Example:</span></span>

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

<span data-ttu-id="b63fb-121">Dynamische Parameter-klasse deze klasse definieert de parameters moeten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="b63fb-121">Dynamic Parameter class This class defines the parameters to be added.</span></span> <span data-ttu-id="b63fb-122">Deze klasse moet een parameterkenmerk voor elke parameter en een optionele Alias en validatie aan de kenmerken die nodig zijn door de cmdlet bevatten.</span><span class="sxs-lookup"><span data-stu-id="b63fb-122">This class must include a Parameter attribute for each parameter and any optional Alias and Validation attributes that are needed by the cmdlet.</span></span>

<span data-ttu-id="b63fb-123">Voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="b63fb-123">Example:</span></span>

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

<span data-ttu-id="b63fb-124">Zie voor een compleet voorbeeld van een cmdlet die ondersteuning biedt voor dynamische parameters, [hoe u dynamische Parameters declareren](./how-to-declare-dynamic-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b63fb-124">For a complete example of a cmdlet that supports dynamic parameters, see [How to Declare Dynamic Parameters](./how-to-declare-dynamic-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b63fb-125">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b63fb-125">See Also</span></span>

[<span data-ttu-id="b63fb-126">System.Management.Automation.Idynamicparameters</span><span class="sxs-lookup"><span data-stu-id="b63fb-126">System.Management.Automation.Idynamicparameters</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters)

[<span data-ttu-id="b63fb-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span><span class="sxs-lookup"><span data-stu-id="b63fb-127">System.Management.Automation.Idynamicparameters.Getdynamicparameters\*</span></span>](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[<span data-ttu-id="b63fb-128">Hoe u dynamische Parameters declareren</span><span class="sxs-lookup"><span data-stu-id="b63fb-128">How to Declare Dynamic Parameters</span></span>](./how-to-declare-dynamic-parameters.md)

[<span data-ttu-id="b63fb-129">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b63fb-129">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
