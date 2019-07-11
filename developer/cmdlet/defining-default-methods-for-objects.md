---
title: Standaardmethoden definiëren voor objecten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733975"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="bbf81-102">Standaardmethoden voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="bbf81-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="bbf81-103">Wanneer u .NET Framework-objecten uitbreidt, kunt u code methoden en -methoden van script toevoegen aan de objecten.</span><span class="sxs-lookup"><span data-stu-id="bbf81-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="bbf81-104">Het XML-bestand dat wordt gebruikt voor het definiëren van deze methoden wordt in de volgende secties beschreven.</span><span class="sxs-lookup"><span data-stu-id="bbf81-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="bbf81-105">De voorbeelden in de volgende secties zijn uit het bestand Types.ps1xml typen in de installatiemap van Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="bbf81-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="bbf81-106">Code-methoden</span><span class="sxs-lookup"><span data-stu-id="bbf81-106">Code Methods</span></span>

<span data-ttu-id="bbf81-107">Een code-methode verwijst naar een statische methode van een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="bbf81-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="bbf81-108">In het volgende voorbeeld wordt de **ConvertLargeIntegerToInt64** methode wordt toegevoegd aan de [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type.</span><span class="sxs-lookup"><span data-stu-id="bbf81-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="bbf81-109">De [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element wordt de uitgebreide methode gedefinieerd als een code-methode.</span><span class="sxs-lookup"><span data-stu-id="bbf81-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="bbf81-110">De [naam](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Hiermee geeft u de naam van de uitgebreide methode.</span><span class="sxs-lookup"><span data-stu-id="bbf81-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="bbf81-111">En de [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element Hiermee geeft u de statische methode.</span><span class="sxs-lookup"><span data-stu-id="bbf81-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="bbf81-112">(U kunt ook toevoegen de [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element aan de leden van de [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span><span class="sxs-lookup"><span data-stu-id="bbf81-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="bbf81-113">Script-methoden</span><span class="sxs-lookup"><span data-stu-id="bbf81-113">Script Methods</span></span>

<span data-ttu-id="bbf81-114">Een scriptmethode definieert een methode waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="bbf81-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="bbf81-115">In het volgende voorbeeld wordt de **ConvertToDateTime** methode wordt toegevoegd aan de [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type.</span><span class="sxs-lookup"><span data-stu-id="bbf81-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="bbf81-116">De [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element wordt de uitgebreide methode gedefinieerd als een scriptmethode.</span><span class="sxs-lookup"><span data-stu-id="bbf81-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="bbf81-117">De [naam](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Hiermee geeft u de naam van de uitgebreide methode.</span><span class="sxs-lookup"><span data-stu-id="bbf81-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="bbf81-118">En de [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element Hiermee geeft u het script waarmee de waarde van de methode genereert.</span><span class="sxs-lookup"><span data-stu-id="bbf81-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="bbf81-119">(U kunt ook toevoegen de [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element aan de leden van de [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span><span class="sxs-lookup"><span data-stu-id="bbf81-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bbf81-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bbf81-120">See Also</span></span>

[<span data-ttu-id="bbf81-121">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="bbf81-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
