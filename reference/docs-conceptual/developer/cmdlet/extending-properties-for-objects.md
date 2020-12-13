---
ms.date: 08/21/2019
ms.topic: reference
title: Eigenschappen voor objecten uitbreiden
description: Eigenschappen voor objecten uitbreiden
ms.openlocfilehash: 37803d9fd87319204565c2abde62f269744481b9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652885"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="358f9-103">Eigenschappen voor objecten uitbreiden</span><span class="sxs-lookup"><span data-stu-id="358f9-103">Extending Properties for Objects</span></span>

<span data-ttu-id="358f9-104">Wanneer u .NET Framework objecten uitbreidt, kunt u alias eigenschappen, code-eigenschappen, notitie-eigenschappen, script eigenschappen en eigenschappen sets aan de objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="358f9-104">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="358f9-105">De XML die deze eigenschappen definieert, wordt in de volgende secties beschreven.</span><span class="sxs-lookup"><span data-stu-id="358f9-105">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="358f9-106">De voor beelden in de volgende secties zijn afkomstig uit het `Types.ps1xml` bestand standaard typen in de Power shell-installatie directory ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="358f9-106">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="358f9-107">Zie [over Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="358f9-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="358f9-108">Alias eigenschappen</span><span class="sxs-lookup"><span data-stu-id="358f9-108">Alias properties</span></span>

<span data-ttu-id="358f9-109">Een alias eigenschap definieert een nieuwe naam voor een bestaande eigenschap.</span><span class="sxs-lookup"><span data-stu-id="358f9-109">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="358f9-110">In het volgende voor beeld wordt de eigenschap **Count** toegevoegd aan het type [System. array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="358f9-110">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="358f9-111">Het [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -element definieert de eigenschap Extended als een alias eigenschap.</span><span class="sxs-lookup"><span data-stu-id="358f9-111">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="358f9-112">Het [naam](/dotnet/api/system.management.automation.psmemberinfo.name) element geeft de nieuwe naam op.</span><span class="sxs-lookup"><span data-stu-id="358f9-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="358f9-113">En het element [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) geeft de bestaande eigenschap op waarnaar wordt verwezen door de alias.</span><span class="sxs-lookup"><span data-stu-id="358f9-113">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="358f9-114">U kunt het element ook toevoegen `AliasProperty` aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="358f9-114">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a><span data-ttu-id="358f9-115">Code-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="358f9-115">Code properties</span></span>

<span data-ttu-id="358f9-116">Een code-eigenschap verwijst naar een statische eigenschap van een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="358f9-116">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="358f9-117">In het volgende voor beeld wordt de eigenschap **mode** toegevoegd aan het type [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="358f9-117">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="358f9-118">Het [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -element definieert de eigenschap Extended als een code-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="358f9-118">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="358f9-119">Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="358f9-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="358f9-120">En, het [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -element, definieert de statische methode waarnaar wordt verwezen door de uitgebreide eigenschap.</span><span class="sxs-lookup"><span data-stu-id="358f9-120">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="358f9-121">U kunt het element ook toevoegen `CodeProperty` aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="358f9-121">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a><span data-ttu-id="358f9-122">Eigenschappen van notitie</span><span class="sxs-lookup"><span data-stu-id="358f9-122">Note properties</span></span>

<span data-ttu-id="358f9-123">Een eigenschap Note definieert een eigenschap die een statische waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="358f9-123">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="358f9-124">In het volgende voor beeld wordt de eigenschap **status** , waarvan de waarde altijd is **geslaagd**, toegevoegd aan het type [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="358f9-124">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="358f9-125">Het [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -element definieert de eigenschap Extended als een notitie-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="358f9-125">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="358f9-126">Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="358f9-126">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="358f9-127">Met het element [Value](/dotnet/api/system.management.automation.psnoteproperty.value) wordt de statische waarde van de uitgebreide eigenschap opgegeven.</span><span class="sxs-lookup"><span data-stu-id="358f9-127">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="358f9-128">Het `NoteProperty` element kan ook worden toegevoegd aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="358f9-128">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a><span data-ttu-id="358f9-129">Script eigenschappen</span><span class="sxs-lookup"><span data-stu-id="358f9-129">Script properties</span></span>

<span data-ttu-id="358f9-130">Een script eigenschap definieert een eigenschap waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="358f9-130">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="358f9-131">In het volgende voor beeld wordt de eigenschap **VersionInfo** toegevoegd aan het type [System. io. file info](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="358f9-131">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="358f9-132">Het [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -element definieert de eigenschap Extended als script eigenschap.</span><span class="sxs-lookup"><span data-stu-id="358f9-132">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="358f9-133">Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="358f9-133">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="358f9-134">En het element [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) geeft het script op waarmee de waarde van de eigenschap wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="358f9-134">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="358f9-135">U kunt het element ook toevoegen `ScriptProperty` aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="358f9-135">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a><span data-ttu-id="358f9-136">Eigenschappen sets</span><span class="sxs-lookup"><span data-stu-id="358f9-136">Property sets</span></span>

<span data-ttu-id="358f9-137">Een verzameling eigenschappen definieert een groep uitgebreide eigenschappen waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="358f9-137">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="358f9-138">De eigenschap para meter [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) 
  kan bijvoorbeeld een specifieke eigenschappenset opgeven die moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="358f9-138">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="358f9-139">Wanneer een eigenschappenset is opgegeven, worden alleen de eigenschappen die deel uitmaken van de set weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="358f9-139">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="358f9-140">Er is geen beperking voor het aantal eigenschappen sets dat kan worden gedefinieerd voor een object.</span><span class="sxs-lookup"><span data-stu-id="358f9-140">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="358f9-141">De eigenschappen sets die worden gebruikt om de standaard eigenschappen voor de weer gave van een object te definiëren, moeten echter worden opgegeven in de ledenset **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="358f9-141">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="358f9-142">In het `Types.ps1xml` type bestand zijn de standaard namen van eigenschappen sets **DefaultDisplayProperty**, **DefaultDisplayPropertySet** en **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="358f9-142">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="358f9-143">Eventuele extra eigenschappen sets die u aan de ledenset **PSStandardMembers** toevoegt, worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="358f9-143">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="358f9-144">In het volgende voor beeld wordt de eigenschap **DefaultDisplayPropertySet** toegevoegd aan de ledenset **PSStandardMembers** van het type [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="358f9-144">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="358f9-145">Het [eigenschappenset](/dotnet/api/system.management.automation.pspropertyset) -element definieert de groep eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="358f9-145">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="358f9-146">Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) specificeert de naam van de eigenschappenset.</span><span class="sxs-lookup"><span data-stu-id="358f9-146">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="358f9-147">En de eigenschappen van de set worden opgegeven met het element [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) .</span><span class="sxs-lookup"><span data-stu-id="358f9-147">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="358f9-148">U kunt het element ook toevoegen `PropertySet` aan de leden van het element [type](/dotnet/api/system.management.automation.pstypename) .</span><span class="sxs-lookup"><span data-stu-id="358f9-148">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="358f9-149">Zie ook</span><span class="sxs-lookup"><span data-stu-id="358f9-149">See also</span></span>

[<span data-ttu-id="358f9-150">Over Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="358f9-150">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="358f9-151">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="358f9-151">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="358f9-152">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="358f9-152">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
