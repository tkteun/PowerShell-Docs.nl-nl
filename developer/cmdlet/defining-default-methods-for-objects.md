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
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="9e6a7-102">Standaardmethoden voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="9e6a7-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="9e6a7-103">Wanneer u .NET Framework-objecten uitbreidt, kunt u code methoden en -methoden van script toevoegen aan de objecten.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="9e6a7-104">Het XML-bestand dat wordt gebruikt voor het definiëren van deze methoden wordt in de volgende secties beschreven.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="9e6a7-105">De voorbeelden in de volgende secties zijn uit het bestand Types.ps1xml typen in de installatiemap van Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="9e6a7-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="9e6a7-106">Code-methoden</span><span class="sxs-lookup"><span data-stu-id="9e6a7-106">Code Methods</span></span>

<span data-ttu-id="9e6a7-107">Een code-methode verwijst naar een statische methode van een .NET Framework-object.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="9e6a7-108">In het volgende voorbeeld wordt de **ConvertLargeIntegerToInt64** methode wordt toegevoegd aan de [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) type.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="9e6a7-109">De [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element wordt de uitgebreide methode gedefinieerd als een code-methode.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="9e6a7-110">De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide methode.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="9e6a7-111">En de [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element Hiermee geeft u de statische methode.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="9e6a7-112">(U kunt ook toevoegen de [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="9e6a7-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="9e6a7-113">Script-methoden</span><span class="sxs-lookup"><span data-stu-id="9e6a7-113">Script Methods</span></span>

<span data-ttu-id="9e6a7-114">Een scriptmethode definieert een methode waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="9e6a7-115">In het volgende voorbeeld wordt de **ConvertToDateTime** methode wordt toegevoegd aan de [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) type.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="9e6a7-116">De [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element wordt de uitgebreide methode gedefinieerd als een scriptmethode.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="9e6a7-117">De [naam](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element Hiermee geeft u de naam van de uitgebreide methode.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="9e6a7-118">En de [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element Hiermee geeft u het script waarmee de waarde van de methode genereert.</span><span class="sxs-lookup"><span data-stu-id="9e6a7-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="9e6a7-119">(U kunt ook toevoegen de [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element aan de leden van de [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="9e6a7-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9e6a7-120">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9e6a7-120">See Also</span></span>

[<span data-ttu-id="9e6a7-121">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e6a7-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)