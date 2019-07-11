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
# <a name="defining-default-methods-for-objects"></a>Standaardmethoden voor objecten definiëren

Wanneer u .NET Framework-objecten uitbreidt, kunt u code methoden en -methoden van script toevoegen aan de objecten. Het XML-bestand dat wordt gebruikt voor het definiëren van deze methoden wordt in de volgende secties beschreven.

> [!NOTE]
> De voorbeelden in de volgende secties zijn uit het bestand Types.ps1xml typen in de installatiemap van Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Code-methoden

Een code-methode verwijst naar een statische methode van een .NET Framework-object.

In het volgende voorbeeld wordt de **ConvertLargeIntegerToInt64** methode wordt toegevoegd aan de [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type. De [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element wordt de uitgebreide methode gedefinieerd als een code-methode. De [naam](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Hiermee geeft u de naam van de uitgebreide methode. En de [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element Hiermee geeft u de statische methode. (U kunt ook toevoegen de [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element aan de leden van de [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)

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

## <a name="script-methods"></a>Script-methoden

Een scriptmethode definieert een methode waarvan de waarde de uitvoer van een script is. In het volgende voorbeeld wordt de **ConvertToDateTime** methode wordt toegevoegd aan de [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type. De [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element wordt de uitgebreide methode gedefinieerd als een scriptmethode. De [naam](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element Hiermee geeft u de naam van de uitgebreide methode. En de [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element Hiermee geeft u het script waarmee de waarde van de methode genereert. (U kunt ook toevoegen de [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element aan de leden van de [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)

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

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
