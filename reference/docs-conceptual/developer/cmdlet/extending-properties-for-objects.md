---
title: Eigenschappen uitbreiden voor objecten | Microsoft Docs
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355536"
---
# <a name="extending-properties-for-objects"></a>Eigenschappen voor objecten uitbreiden

Wanneer u .NET Framework objecten uitbreidt, kunt u alias eigenschappen, code-eigenschappen, notitie-eigenschappen, script eigenschappen en eigenschappen sets aan de objecten toevoegen. De XML die deze eigenschappen definieert, wordt in de volgende secties beschreven.

> [!NOTE]
> De voor beelden in de volgende secties zijn afkomstig uit het standaard `Types.ps1xml` typen bestand in de Power shell-installatiemap (`$PSHOME`). Zie [about types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)voor meer informatie.

## <a name="alias-properties"></a>Alias eigenschappen

Een alias eigenschap definieert een nieuwe naam voor een bestaande eigenschap.

In het volgende voor beeld wordt de eigenschap **Count** toegevoegd aan het type [System. array](/dotnet/api/System.Array) . Het [AliasProperty](/dotnet/api/system.management.automation.psaliasproperty) -element definieert de eigenschap Extended als een alias eigenschap. Het [naam](/dotnet/api/system.management.automation.psmemberinfo.name) element geeft de nieuwe naam op. En het element [ReferencedMemberName](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) geeft de bestaande eigenschap op waarnaar wordt verwezen door de alias. U kunt ook het `AliasProperty`-element toevoegen aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="code-properties"></a>Code-eigenschappen

Een code-eigenschap verwijst naar een statische eigenschap van een .NET Framework-object.

In het volgende voor beeld wordt de eigenschap **mode** toegevoegd aan het type [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . Het [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -element definieert de eigenschap Extended als een code-eigenschap. Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op. En, het [GetCodeReference](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) -element, definieert de statische methode waarnaar wordt verwezen door de uitgebreide eigenschap. U kunt ook het `CodeProperty`-element toevoegen aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="note-properties"></a>Eigenschappen van notitie

Een eigenschap Note definieert een eigenschap die een statische waarde heeft.

In het volgende voor beeld wordt de eigenschap **status** , waarvan de waarde altijd is **geslaagd**, toegevoegd aan het type [System. io. DirectoryInfo](/dotnet/api/System.IO.DirectoryInfo) . Het [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -element definieert de eigenschap Extended als een notitie-eigenschap. Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op. Met het element [Value](/dotnet/api/system.management.automation.psnoteproperty.value) wordt de statische waarde van de uitgebreide eigenschap opgegeven. Het `NoteProperty`-element kan ook worden toegevoegd aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="script-properties"></a>Script eigenschappen

Een script eigenschap definieert een eigenschap waarvan de waarde de uitvoer van een script is.

In het volgende voor beeld wordt de eigenschap **VersionInfo** toegevoegd aan het type [System. io. file info](/dotnet/api/System.IO.FileInfo) . Het [ScriptProperty](/dotnet/api/system.management.automation.psscriptproperty) -element definieert de eigenschap Extended als script eigenschap. Met het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) geeft u de naam van de uitgebreide eigenschap op. En het element [GetScriptBlock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) geeft het script op waarmee de waarde van de eigenschap wordt gegenereerd. U kunt ook het `ScriptProperty`-element toevoegen aan de leden van het element [MemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="property-sets"></a>Eigenschappen sets

Een verzameling eigenschappen definieert een groep uitgebreide eigenschappen waarnaar kan worden verwezen door de naam van de set.
De [notatie-tabel](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**eigenschaps** parameter kan bijvoorbeeld een specifieke eigenschappenset opgeven die moet worden weer gegeven. Wanneer een eigenschappenset is opgegeven, worden alleen de eigenschappen die deel uitmaken van de set weer gegeven.

Er is geen beperking voor het aantal eigenschappen sets dat kan worden gedefinieerd voor een object. De eigenschappen sets die worden gebruikt om de standaard eigenschappen voor de weer gave van een object te definiëren, moeten echter worden opgegeven in de ledenset **PSStandardMembers** . In het bestand `Types.ps1xml` typen zijn de standaard namen van eigenschappen sets **DefaultDisplayProperty**, **DefaultDisplayPropertySet**en **DefaultKeyPropertySet**. Eventuele extra eigenschappen sets die u aan de ledenset **PSStandardMembers** toevoegt, worden genegeerd.

In het volgende voor beeld wordt de eigenschap **DefaultDisplayPropertySet** toegevoegd aan de ledenset **PSStandardMembers** van het type [System. ServiceProcess. servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) . Het [eigenschappenset](/dotnet/api/system.management.automation.pspropertyset) -element definieert de groep eigenschappen. Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name) specificeert de naam van de eigenschappenset. En de eigenschappen van de set worden opgegeven met het element [ReferencedProperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) . U kunt ook het `PropertySet`-element toevoegen aan de leden van het [type](/dotnet/api/system.management.automation.pstypename) element.

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

## <a name="see-also"></a>Zie ook

[Over typen. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
