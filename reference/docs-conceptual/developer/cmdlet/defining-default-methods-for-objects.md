---
title: Standaard methoden voor objecten definiëren | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356404"
---
# <a name="defining-default-methods-for-objects"></a>Standaardmethoden voor objecten definiëren

Wanneer u .NET Framework objecten uitbreidt, kunt u code methoden en script methoden toevoegen aan de-objecten.
De XML die wordt gebruikt voor het definiëren van deze methoden, wordt beschreven in de volgende secties.

> [!NOTE]
> De voor beelden in de volgende secties zijn afkomstig uit het bestand `Types.ps1xml` in de installatiemap van Windows Power shell (`$PSHOME`). Zie [about types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)voor meer informatie.

## <a name="code-methods"></a>Code methoden

Een code methode verwijst naar een statische methode van een .NET Framework-object.

In het volgende voor beeld wordt de methode **toString** toegevoegd aan het type [System. XML. XMLNode](/dotnet/api/System.Xml.XmlNode) . Het [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -element definieert de uitgebreide methode als een code methode. Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) geeft de naam van de uitgebreide methode aan. En het element [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) geeft de statische methode aan. U kunt ook het element [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) toevoegen aan de leden van het element [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

Een script methode definieert een methode waarvan de waarde de uitvoer van een script is. In het volgende voor beeld wordt de methode **ConvertToDateTime** toegevoegd aan het type [System. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) . Het [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) -element definieert de uitgebreide methode als een script methode. Het element [name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) geeft de naam van de uitgebreide methode aan. En het [script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) -element geeft het script op waarmee de methode waarde wordt gegenereerd. U kunt ook het element [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) toevoegen aan de leden van het element [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) .

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

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
