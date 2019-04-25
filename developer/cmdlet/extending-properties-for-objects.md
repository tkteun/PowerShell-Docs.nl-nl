---
title: Uitbreiding van eigenschappen voor objecten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 496e363b041194563d46c09eee67a12055bb54b0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068144"
---
# <a name="extending-properties-for-objects"></a><span data-ttu-id="b0ceb-102">Eigenschappen voor objecten uitbreiden</span><span class="sxs-lookup"><span data-stu-id="b0ceb-102">Extending Properties for Objects</span></span>

<span data-ttu-id="b0ceb-103">Wanneer u .NET Framework-objecten uitbreidt, kunt u toevoegen alias eigenschappen, code-eigenschappen, houd er rekening mee eigenschappen, scripteigenschappen en eigenschappen aan de objecten.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-103">When you extend .NET Framework objects, you can add alias properties, code properties, note properties, script properties, and property sets to the objects.</span></span> <span data-ttu-id="b0ceb-104">Het XML-bestand dat wordt gebruikt voor het definiëren van deze eigenschappen wordt in de volgende secties beschreven.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-104">The XML that is used to define these properties is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="b0ceb-105">De voorbeelden in de volgende secties zijn uit het bestand standaard Types.ps1xml typen in de installatiemap van Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="b0ceb-105">The examples in the following sections are from the default Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="alias-properties"></a><span data-ttu-id="b0ceb-106">Alias Properties</span><span class="sxs-lookup"><span data-stu-id="b0ceb-106">Alias Properties</span></span>

<span data-ttu-id="b0ceb-107">De eigenschap van een alias definieert een nieuwe naam voor een bestaande eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-107">An alias property defines a new name for an existing property.</span></span>

<span data-ttu-id="b0ceb-108">In het volgende voorbeeld wordt de `Count` eigenschap wordt toegevoegd aan de [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) type.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-108">In the following example, the `Count` property is added to the [System.Array?Displayproperty=Fullname](/dotnet/api/System.Array) type.</span></span> <span data-ttu-id="b0ceb-109">De [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element de uitgebreide eigenschap wordt gedefinieerd als een eigenschap van een alias.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-109">The [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element defines the extended property as an alias property.</span></span> <span data-ttu-id="b0ceb-110">De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de nieuwe naam.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the new name.</span></span> <span data-ttu-id="b0ceb-111">En de [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element Hiermee geeft u de bestaande eigenschap waarnaar wordt verwezen door de alias.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-111">And, the [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element specifies the existing property that is referenced by the alias.</span></span> <span data-ttu-id="b0ceb-112">(U kunt ook toevoegen de [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="b0ceb-112">(You can also add the [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="code-properties"></a><span data-ttu-id="b0ceb-113">Code-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b0ceb-113">Code Properties</span></span>

<span data-ttu-id="b0ceb-114">Een code-eigenschap verwijst naar een statische eigenschap van een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-114">A code property references a static property of a .NET Framework object.</span></span>

<span data-ttu-id="b0ceb-115">In het volgende voorbeeld wordt de `Node` eigenschap wordt toegevoegd aan de [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-115">In the following example, the `Node` property is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="b0ceb-116">De [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element de uitgebreide eigenschap wordt gedefinieerd als een code-eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-116">The [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element defines the extended property as a code property.</span></span> <span data-ttu-id="b0ceb-117">De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="b0ceb-118">En de [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element de statische methode waarnaar wordt verwezen door de uitgebreide eigenschap wordt gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-118">And, the [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element defines the static method that is referenced by the extended property.</span></span> <span data-ttu-id="b0ceb-119">(U kunt ook toevoegen de [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="b0ceb-119">(You can also add the [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="note-properties"></a><span data-ttu-id="b0ceb-120">Houd er rekening mee eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b0ceb-120">Note Properties</span></span>

<span data-ttu-id="b0ceb-121">Een opmerking eigenschap definieert een eigenschap die een statische waarde heeft.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-121">A note property defines a property that has a static value.</span></span>

<span data-ttu-id="b0ceb-122">In het volgende voorbeeld wordt de `Status` eigenschap (waarvan de waarde is altijd "Geslaagd") wordt toegevoegd aan de [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-122">In the following example, the `Status` property (whose value is always "Success") is added to the [System.IO.Directoryinfo?Displayproperty=Fullname](/dotnet/api/System.IO.DirectoryInfo) type.</span></span> <span data-ttu-id="b0ceb-123">De [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element de uitgebreide eigenschap wordt gedefinieerd als een eigenschap Opmerking; de [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide eigenschap; en de [waarde](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element Hiermee geeft u de statische waarde van de uitgebreide eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-123">The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element defines the extended property as a note property; the [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property; and the [Value](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the static value of the extended property.</span></span> <span data-ttu-id="b0ceb-124">(De [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element kan ook worden toegevoegd aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="b0ceb-124">(The [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element can also be added to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-properties"></a><span data-ttu-id="b0ceb-125">Scripteigenschappen van</span><span class="sxs-lookup"><span data-stu-id="b0ceb-125">Script Properties</span></span>

<span data-ttu-id="b0ceb-126">De eigenschap van een script definieert een eigenschap waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-126">A script property defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="b0ceb-127">In het volgende voorbeeld wordt de `VersionInfo` eigenschap wordt toegevoegd aan de [System.IO.FileInfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) type.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-127">In the following example, the `VersionInfo` property is added to the [System.IO.FileInfo?Displayproperty=Fullname](/dotnet/api/System.IO.FileInfo) type.</span></span> <span data-ttu-id="b0ceb-128">De [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element de uitgebreide eigenschap wordt gedefinieerd als een scripteigenschap.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-128">The [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element defines the extended property as a script property.</span></span> <span data-ttu-id="b0ceb-129">De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide eigenschap.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-129">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended property.</span></span> <span data-ttu-id="b0ceb-130">En de [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element Hiermee geeft u het script waarmee de waarde van de eigenschap wordt gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-130">And, the [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element specifies the script that generates the property value.</span></span> <span data-ttu-id="b0ceb-131">(U kunt ook toevoegen de [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="b0ceb-131">(You can also add the [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="property-sets"></a><span data-ttu-id="b0ceb-132">Eigenschap instellen</span><span class="sxs-lookup"><span data-stu-id="b0ceb-132">Property Sets</span></span>

<span data-ttu-id="b0ceb-133">Een groep van uitgebreide eigenschappen die kan worden verwezen door de naam van de set Hiermee definieert u een eigenschap worden ingesteld.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-133">A property set defines a group of extended properties that can be referenced by the name of the set.</span></span> <span data-ttu-id="b0ceb-134">Bijvoorbeeld, de `Property` parameter van de [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet kunt opgeven een bepaalde eigenschap is ingesteld om te worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-134">For example, the `Property` parameter of the [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet can specify a specific property set to be displayed.</span></span> <span data-ttu-id="b0ceb-135">Wanneer een eigenschap worden ingesteld is opgegeven, worden alleen de eigenschappen die deel uitmaken van de set weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-135">When a property set is specified, only those properties that belong to the set are displayed.</span></span>

<span data-ttu-id="b0ceb-136">Er is geen beperking voor het aantal groepen die kunnen worden gedefinieerd voor een object.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-136">There is no restriction on the number of property sets that can be defined for an object.</span></span> <span data-ttu-id="b0ceb-137">De eigenschap die wordt gebruikt voor het definiëren van de standaard weergave-eigenschappen van een object moeten echter worden opgegeven in de set van PSStandardMembers lid.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-137">However, the property sets used to define the default display properties of an object must be specified within the PSStandardMembers member set.</span></span> <span data-ttu-id="b0ceb-138">De set-namen van de standaard-eigenschappen zijn in het bestand van de typen Types.ps1xml DefaultDisplayProperty, DefaultDisplayPropertySet en DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-138">In the Types.ps1xml types file, the default property set names include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="b0ceb-139">Een extra eigenschappensets die u aan de ledenset PSStandardMembers toevoegt worden genegeerd.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-139">Any additional property sets that you add to the PSStandardMembers member set are ignored.</span></span>

<span data-ttu-id="b0ceb-140">In het volgende voorbeeld wordt de eigenschap DefaultDisplayPropertySet ingesteld wordt toegevoegd aan de set PSStandardMembers lid van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-140">In the following example, the DefaultDisplayPropertySet property set is added to the PSStandardMembers member set of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type.</span></span> <span data-ttu-id="b0ceb-141">De [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element wordt gedefinieerd voor de groep met eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-141">The [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element defines the group of properties.</span></span> <span data-ttu-id="b0ceb-142">De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de eigenschap is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-142">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the property set.</span></span> <span data-ttu-id="b0ceb-143">En de [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element Hiermee geeft u de eigenschappen van de set.</span><span class="sxs-lookup"><span data-stu-id="b0ceb-143">And, the [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element specifies the properties of the set.</span></span> <span data-ttu-id="b0ceb-144">(U kunt ook toevoegen de [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element aan de leden van de [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span><span class="sxs-lookup"><span data-stu-id="b0ceb-144">(You can also add the [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element to the members of the [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b0ceb-145">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0ceb-145">See Also</span></span>

[<span data-ttu-id="b0ceb-146">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b0ceb-146">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
