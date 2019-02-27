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
ms.openlocfilehash: dcab755f565cd176c85ef6b9c719bceae10301b4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845778"
---
# <a name="extending-properties-for-objects"></a>Eigenschappen voor objecten uitbreiden

Wanneer u .NET Framework-objecten uitbreidt, kunt u toevoegen alias eigenschappen, code-eigenschappen, houd er rekening mee eigenschappen, scripteigenschappen en eigenschappen aan de objecten. Het XML-bestand dat wordt gebruikt voor het definiëren van deze eigenschappen wordt in de volgende secties beschreven.

> [!NOTE]
> De voorbeelden in de volgende secties zijn uit het bestand standaard Types.ps1xml typen in de installatiemap van Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Alias Properties

De eigenschap van een alias definieert een nieuwe naam voor een bestaande eigenschap.

In het volgende voorbeeld wordt de `Count` eigenschap wordt toegevoegd aan de [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) type. De [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) element de uitgebreide eigenschap wordt gedefinieerd als een eigenschap van een alias. De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de nieuwe naam. En de [ReferencedMemberName](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) element Hiermee geeft u de bestaande eigenschap waarnaar wordt verwezen door de alias. (U kunt ook toevoegen de [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

In het volgende voorbeeld wordt de `Node` eigenschap wordt toegevoegd aan de [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type. De [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element de uitgebreide eigenschap wordt gedefinieerd als een code-eigenschap. De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide eigenschap. En de [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) element de statische methode waarnaar wordt verwezen door de uitgebreide eigenschap wordt gedefinieerd. (U kunt ook toevoegen de [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="note-properties"></a>Houd er rekening mee eigenschappen

Een opmerking eigenschap definieert een eigenschap die een statische waarde heeft.

In het volgende voorbeeld wordt de `Status` eigenschap (waarvan de waarde is altijd "Geslaagd") wordt toegevoegd aan de [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) type. De [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element de uitgebreide eigenschap wordt gedefinieerd als een eigenschap Opmerking; de [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide eigenschap; en de [waarde](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element Hiermee geeft u de statische waarde van de uitgebreide eigenschap. (De [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) element kan ook worden toegevoegd aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="script-properties"></a>Scripteigenschappen van

De eigenschap van een script definieert een eigenschap waarvan de waarde de uitvoer van een script is.

In het volgende voorbeeld wordt de `VersionInfo` eigenschap wordt toegevoegd aan de [System.IO.Fileinfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) type. De [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element de uitgebreide eigenschap wordt gedefinieerd als een scripteigenschap. De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide eigenschap. En de [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) element Hiermee geeft u het script waarmee de waarde van de eigenschap wordt gegenereerd. (U kunt ook toevoegen de [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

## <a name="property-sets"></a>Eigenschap instellen

Een groep van uitgebreide eigenschappen die kan worden verwezen door de naam van de set Hiermee definieert u een eigenschap worden ingesteld. Bijvoorbeeld, de `Property` parameter van de [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet kunt opgeven een bepaalde eigenschap is ingesteld om te worden weergegeven. Wanneer een eigenschap worden ingesteld is opgegeven, worden alleen de eigenschappen die deel uitmaken van de set weergegeven.
Een groep van uitgebreide eigenschappen die kan worden verwezen door de naam van de set Hiermee definieert u een eigenschap worden ingesteld. Bijvoorbeeld, de `Property` parameter van de [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) cmdlet kunt opgeven een bepaalde eigenschap is ingesteld om te worden weergegeven. Wanneer een eigenschap worden ingesteld is opgegeven, worden alleen de eigenschappen die deel uitmaken van de set weergegeven.

Er is geen beperking voor het aantal groepen die kunnen worden gedefinieerd voor een object. De eigenschap die wordt gebruikt voor het definiëren van de standaard weergave-eigenschappen van een object moeten echter worden opgegeven in de set van PSStandardMembers lid. De set-namen van de standaard-eigenschappen zijn in het bestand van de typen Types.ps1xml DefaultDisplayProperty, DefaultDisplayPropertySet en DefaultKeyPropertySet. Een extra eigenschappensets die u aan de ledenset PSStandardMembers toevoegt worden genegeerd.

In het volgende voorbeeld wordt de eigenschap DefaultDisplayPropertySet ingesteld wordt toegevoegd aan de set PSStandardMembers lid van de [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) type. De [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element wordt gedefinieerd voor de groep met eigenschappen. De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de eigenschap is ingesteld. En de [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) element Hiermee geeft u de eigenschappen van de set. (U kunt ook toevoegen de [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) element aan de leden van de [Type](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) element.)

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
