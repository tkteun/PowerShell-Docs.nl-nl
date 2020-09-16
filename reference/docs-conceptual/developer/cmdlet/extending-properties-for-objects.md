---
title: Eigenschappen uitbreiden voor objecten | Microsoft Docs
ms.date: 08/21/2019
ms.openlocfilehash: acd20c7e2b6ef84a9c932538eb8e167d68c8a660
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784296"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="0aad5-102">Eigenschappen voor objecten uitbreiden</span><span class="sxs-lookup"><span data-stu-id="0aad5-102">Extending Properties for Objects</span></span>

<span data-ttu-id="0aad5-103">Wanneer u .NET Framework objecten uitbreidt, kunt u alias eigenschappen, code-eigenschappen, notitie-eigenschappen, script eigenschappen en eigenschappen sets aan de objecten toevoegen.</span><span class="sxs-lookup"><span data-stu-id="0aad5-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="0aad5-104">De XML die deze eigenschappen definieert, wordt in de volgende secties beschreven.</span><span class="sxs-lookup"><span data-stu-id="0aad5-104">The XML that defines these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="0aad5-105">De voor beelden in de volgende secties zijn afkomstig uit het `Types.ps1xml` bestand standaard typen in de Power shell-installatie directory ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="0aad5-105">The examples in the following sections are from the default `Types.ps1xml` types file in the PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="0aad5-106">Zie [over Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="0aad5-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="0aad5-107">Alias eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0aad5-107">Alias properties</span></span>

<span data-ttu-id="0aad5-108">Een alias eigenschap definieert een nieuwe naam voor een bestaande eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0aad5-108">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="0aad5-109">In het volgende voor beeld wordt de eigenschap **Count** toegevoegd aan het type [System. array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-109">In the following example, the **Count** property is added to the [System.Array](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="0aad5-110">Het [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -element definieert de eigenschap Extended als een alias eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0aad5-110">The [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) element defines the extended property as an alias property.</span></span> <span data-ttu-id="0aad5-111">Het [naam](/dotnet/api/system.management.automation.psmemberinfo.name) element geeft de nieuwe naam op.</span><span class="sxs-lookup"><span data-stu-id="0aad5-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the new name.</span></span> <span data-ttu-id="0aad5-112">En het element [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) geeft de bestaande eigenschap op waarnaar wordt verwezen door de alias.</span><span class="sxs-lookup"><span data-stu-id="0aad5-112">And, the [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="0aad5-113">U kunt het element ook toevoegen `AliasProperty` aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-113">You can also add the `AliasProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="0aad5-114">Code-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0aad5-114">Code properties</span></span>

<span data-ttu-id="0aad5-115">Een code-eigenschap verwijst naar een statische eigenschap van een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="0aad5-115">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="0aad5-116">In het volgende voor beeld wordt de eigenschap **mode** toegevoegd aan het type [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-116">In the following example, the **Mode** property is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="0aad5-117">Het [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -element definieert de eigenschap Extended als een code-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0aad5-117">The [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) element defines the extended property as a code property.</span></span> <span data-ttu-id="0aad5-118">Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="0aad5-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="0aad5-119">En, het [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -element, definieert de statische methode waarnaar wordt verwezen door de uitgebreide eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0aad5-119">And, the [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="0aad5-120">U kunt het element ook toevoegen `CodeProperty` aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-120">You can also add the `CodeProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="0aad5-121">Eigenschappen van notitie</span><span class="sxs-lookup"><span data-stu-id="0aad5-121">Note properties</span></span>

<span data-ttu-id="0aad5-122">Een eigenschap Note definieert een eigenschap die een statische waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="0aad5-122">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="0aad5-123">In het volgende voor beeld wordt de eigenschap **status** , waarvan de waarde altijd is **geslaagd**, toegevoegd aan het type [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-123">In the following example, the **Status** property, whose value is always **Success**, is added to the [System.IO.DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="0aad5-124">Het [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -element definieert de eigenschap Extended als een notitie-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0aad5-124">The [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) element defines the extended property as a note property.</span></span> <span data-ttu-id="0aad5-125">Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="0aad5-125">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="0aad5-126">Met het element [Value](/dotnet/api/system.management.automation.psnoteproperty.value) wordt de statische waarde van de uitgebreide eigenschap opgegeven.</span><span class="sxs-lookup"><span data-stu-id="0aad5-126">The [Value](/dotnet/api/system.management.automation.psnoteproperty.value) element specifies the static value of the extended property.</span></span> <span data-ttu-id="0aad5-127">Het `NoteProperty` element kan ook worden toegevoegd aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-127">The `NoteProperty` element can also be added to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="0aad5-128">Script eigenschappen</span><span class="sxs-lookup"><span data-stu-id="0aad5-128">Script properties</span></span>

<span data-ttu-id="0aad5-129">Een script eigenschap definieert een eigenschap waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="0aad5-129">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="0aad5-130">In het volgende voor beeld wordt de eigenschap **VersionInfo** toegevoegd aan het type [System. io. file info](/dotnet/api/System.IO.FileInfo) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-130">In the following example, the **VersionInfo** property is added to the [System.IO.FileInfo](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="0aad5-131">Het [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -element definieert de eigenschap Extended als script eigenschap.</span><span class="sxs-lookup"><span data-stu-id="0aad5-131">The [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) element defines the extended property as a script property.</span></span> <span data-ttu-id="0aad5-132">Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op.</span><span class="sxs-lookup"><span data-stu-id="0aad5-132">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the extended property.</span></span> <span data-ttu-id="0aad5-133">En het element [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) geeft het script op waarmee de waarde van de eigenschap wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="0aad5-133">And, the [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) element specifies the script that generates the property value.</span></span> <span data-ttu-id="0aad5-134">U kunt het element ook toevoegen `ScriptProperty` aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-134">You can also add the `ScriptProperty` element to the members of the [MemberSets](/dotnet/api/system.management.automation.psmemberset) element.</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="0aad5-135">Eigenschappen sets</span><span class="sxs-lookup"><span data-stu-id="0aad5-135">Property sets</span></span>

<span data-ttu-id="0aad5-136">Een verzameling eigenschappen definieert een groep uitgebreide eigenschappen waarnaar kan worden verwezen door de naam van de set.</span><span class="sxs-lookup"><span data-stu-id="0aad5-136">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span>
<span data-ttu-id="0aad5-137">De eigenschap para meter [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) 
 **Property** kan bijvoorbeeld een specifieke eigenschappenset opgeven die moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0aad5-137">For example, the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** parameter can specify a specific property set to be displayed.</span></span> <span data-ttu-id="0aad5-138">Wanneer een eigenschappenset is opgegeven, worden alleen de eigenschappen die deel uitmaken van de set weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="0aad5-138">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="0aad5-139">Er is geen beperking voor het aantal eigenschappen sets dat kan worden gedefinieerd voor een object.</span><span class="sxs-lookup"><span data-stu-id="0aad5-139">There's no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="0aad5-140">De eigenschappen sets die worden gebruikt om de standaard eigenschappen voor de weer gave van een object te definiëren, moeten echter worden opgegeven in de ledenset **PSStandardMembers** .</span><span class="sxs-lookup"><span data-stu-id="0aad5-140">However, the property sets used to define the default display properties of an object must be specified within the **PSStandardMembers** member set.</span></span> <span data-ttu-id="0aad5-141">In het `Types.ps1xml` type bestand zijn de standaard namen van eigenschappen sets **DefaultDisplayProperty**, **DefaultDisplayPropertySet**en **DefaultKeyPropertySet**.</span><span class="sxs-lookup"><span data-stu-id="0aad5-141">In the `Types.ps1xml` types file, the default property set names include **DefaultDisplayProperty**, **DefaultDisplayPropertySet**, and **DefaultKeyPropertySet**.</span></span> <span data-ttu-id="0aad5-142">Eventuele extra eigenschappen sets die u aan de ledenset **PSStandardMembers** toevoegt, worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="0aad5-142">Any additional property sets that you add to the **PSStandardMembers** member set are ignored.</span></span>

<span data-ttu-id="0aad5-143">In het volgende voor beeld wordt de eigenschap **DefaultDisplayPropertySet** toegevoegd aan de ledenset **PSStandardMembers** van het type [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-143">In the following example, the **DefaultDisplayPropertySet** property set is added to the **PSStandardMembers** member set of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="0aad5-144">Het [eigenschappenset](/dotnet/api/system.management.automation.pspropertyset) -element definieert de groep eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="0aad5-144">The [PropertySet](/dotnet/api/system.management.automation.pspropertyset) element defines the group of properties.</span></span> <span data-ttu-id="0aad5-145">Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) specificeert de naam van de eigenschappenset.</span><span class="sxs-lookup"><span data-stu-id="0aad5-145">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name) element specifies the name of the property set.</span></span> <span data-ttu-id="0aad5-146">En de eigenschappen van de set worden opgegeven met het element [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-146">And, the [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) element specifies the properties of the set.</span></span> <span data-ttu-id="0aad5-147">U kunt het element ook toevoegen `PropertySet` aan de leden van het element [type](/dotnet/api/system.management.automation.pstypename) .</span><span class="sxs-lookup"><span data-stu-id="0aad5-147">You can also add the `PropertySet` element to the members of the [Type](/dotnet/api/system.management.automation.pstypename) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0aad5-148">Zie ook</span><span class="sxs-lookup"><span data-stu-id="0aad5-148">See also</span></span>

[<span data-ttu-id="0aad5-149">Over Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="0aad5-149">About Types.ps1xml</span></span>](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[<span data-ttu-id="0aad5-150">System. Management. Automation</span><span class="sxs-lookup"><span data-stu-id="0aad5-150">System.Management.Automation</span></span>](/dotnet/api/System.Management.Automation)

[<span data-ttu-id="0aad5-151">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="0aad5-151">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
