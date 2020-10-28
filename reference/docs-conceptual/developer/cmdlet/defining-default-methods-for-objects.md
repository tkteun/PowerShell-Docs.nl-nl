---
ms.date: 09/13/2016
ms.topic: reference
title: Standaardmethoden voor objecten definiëren
description: Standaardmethoden voor objecten definiëren
ms.openlocfilehash: b3b61b552d0f5ef4a018c6f1dd495ac0c770cddc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653099"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="ae69d-103">Standaardmethoden voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="ae69d-103">Defining Default Methods for Objects</span></span>

<span data-ttu-id="ae69d-104">Wanneer u .NET Framework objecten uitbreidt, kunt u code methoden en script methoden toevoegen aan de-objecten.</span><span class="sxs-lookup"><span data-stu-id="ae69d-104">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="ae69d-105">De XML die wordt gebruikt voor het definiëren van deze methoden, wordt beschreven in de volgende secties.</span><span class="sxs-lookup"><span data-stu-id="ae69d-105">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="ae69d-106">De voor beelden in de volgende secties zijn afkomstig uit het `Types.ps1xml` type bestand in de installatiemap van Windows Power shell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="ae69d-106">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="ae69d-107">Zie [over Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="ae69d-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="ae69d-108">Code methoden</span><span class="sxs-lookup"><span data-stu-id="ae69d-108">Code methods</span></span>

<span data-ttu-id="ae69d-109">Een code methode verwijst naar een statische methode van een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="ae69d-109">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="ae69d-110">In het volgende voor beeld wordt de methode **toString** toegevoegd aan het [ knooppunt typeSystem.Xml.Xml](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="ae69d-110">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="ae69d-111">Het [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -element definieert de uitgebreide methode als een code methode.</span><span class="sxs-lookup"><span data-stu-id="ae69d-111">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="ae69d-112">Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) geeft de naam van de uitgebreide methode aan.</span><span class="sxs-lookup"><span data-stu-id="ae69d-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="ae69d-113">En het element [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) geeft de statische methode aan.</span><span class="sxs-lookup"><span data-stu-id="ae69d-113">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="ae69d-114">U kunt ook het element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) toevoegen aan de leden van het element [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="ae69d-114">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="ae69d-115">Script methoden</span><span class="sxs-lookup"><span data-stu-id="ae69d-115">Script methods</span></span>

<span data-ttu-id="ae69d-116">Een script methode definieert een methode waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="ae69d-116">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="ae69d-117">In het volgende voor beeld wordt de methode **ConvertToDateTime** toegevoegd aan het type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="ae69d-117">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="ae69d-118">Het [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) -element definieert de uitgebreide methode als een script methode.</span><span class="sxs-lookup"><span data-stu-id="ae69d-118">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="ae69d-119">Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) geeft de naam van de uitgebreide methode aan.</span><span class="sxs-lookup"><span data-stu-id="ae69d-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="ae69d-120">En het [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) -element geeft het script op waarmee de methode waarde wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="ae69d-120">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="ae69d-121">U kunt ook het element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) toevoegen aan de leden van het element [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .</span><span class="sxs-lookup"><span data-stu-id="ae69d-121">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="ae69d-122">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ae69d-122">See also</span></span>

[<span data-ttu-id="ae69d-123">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="ae69d-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
