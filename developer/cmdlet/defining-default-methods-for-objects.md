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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068212"
---
# <a name="defining-default-methods-for-objects"></a>Standaardmethoden voor objecten definiëren

Wanneer u .NET Framework-objecten uitbreidt, kunt u code methoden en -methoden van script toevoegen aan de objecten. Het XML-bestand dat wordt gebruikt voor het definiëren van deze methoden wordt in de volgende secties beschreven.

> [!NOTE]
> De voorbeelden in de volgende secties zijn uit het bestand Types.ps1xml typen in de installatiemap van Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Code-methoden

Een code-methode verwijst naar een statische methode van een .NET Framework-object.

In het volgende voorbeeld wordt de **ConvertLargeIntegerToInt64** methode wordt toegevoegd aan de [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type. De [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element wordt de uitgebreide methode gedefinieerd als een code-methode. De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide methode. En de [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element Hiermee geeft u de statische methode. (U kunt ook toevoegen de [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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

Een scriptmethode definieert een methode waarvan de waarde de uitvoer van een script is. In het volgende voorbeeld wordt de **ConvertToDateTime** methode wordt toegevoegd aan de [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type. De [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element wordt de uitgebreide methode gedefinieerd als een scriptmethode. De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide methode. En de [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element Hiermee geeft u het script waarmee de waarde van de methode genereert. (U kunt ook toevoegen de [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)

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