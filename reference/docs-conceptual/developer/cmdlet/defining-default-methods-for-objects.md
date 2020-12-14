---
ms.date: 09/13/2016
ms.topic: reference
title: Standaardmethoden voor objecten definiëren
description: Standaardmethoden voor objecten definiëren
ms.openlocfilehash: c65ca91a7038f32d8c3ef62cfe7881e5ad4dba5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355524"
---
# <a name="defining-default-methods-for-objects"></a>Standaardmethoden voor objecten definiëren

Wanneer u .NET Framework objecten uitbreidt, kunt u code methoden en script methoden toevoegen aan de-objecten.
De XML die wordt gebruikt voor het definiëren van deze methoden, wordt beschreven in de volgende secties.

> [!NOTE]
> De voor beelden in de volgende secties zijn afkomstig uit het `Types.ps1xml` type bestand in de installatiemap van Windows Power shell ( `$PSHOME` ). Zie [over Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)voor meer informatie.

## <a name="code-methods"></a>Code methoden

Een code methode verwijst naar een statische methode van een .NET Framework-object.

In het volgende voor beeld wordt de methode **toString** toegevoegd aan het [ knooppunt typeSystem.Xml.Xml](/dotnet/api/System.Xml.XmlNode) . Het [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -element definieert de uitgebreide methode als een code methode. Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) geeft de naam van de uitgebreide methode aan. En het element [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference#System_Management_Automation_PSCodeMethod_CodeReference) geeft de statische methode aan. U kunt ook het element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) toevoegen aan de leden van het element [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="script-methods"></a>Script methoden

Een script methode definieert een methode waarvan de waarde de uitvoer van een script is. In het volgende voor beeld wordt de methode **ConvertToDateTime** toegevoegd aan het type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . Het [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) -element definieert de uitgebreide methode als een script methode. Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name#System_Management_Automation_PSMemberInfo_Name) geeft de naam van de uitgebreide methode aan. En het [script](/dotnet/api/system.management.automation.psscriptmethod.script#System_Management_Automation_PSScriptMethod_Script) -element geeft het script op waarmee de methode waarde wordt gegenereerd. U kunt ook het element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod) toevoegen aan de leden van het element [PSMemberSets](/dotnet/api/system.management.automation.psmemberset) .

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

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
