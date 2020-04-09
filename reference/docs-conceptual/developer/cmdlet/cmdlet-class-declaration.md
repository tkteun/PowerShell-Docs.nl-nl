---
title: Cmdlet-klassen declaratie | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], declaring
- declaring cmdlets [PowerShell SDK]
ms.assetid: 1fcc4c5e-0c75-496c-a712-5f844e310576
caps.latest.revision: 14
ms.openlocfilehash: 0de49d979c31b0e8d111323a2e1899d97868ec3f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978709"
---
# <a name="cmdlet-class-declaration"></a>Declaratie van cmdlet-klassen

Een Microsoft .NET Framework-klasse wordt gedeclareerd als een cmdlet door het **cmdlet** -kenmerk op te geven als meta gegevens voor de klasse. (Het **cmdlet** -kenmerk is het enige vereiste kenmerk voor alle cmdlets).
Wanneer u het **cmdlet** -kenmerk opgeeft, moet u de combi natie van verb en samen stelling opgeven waarmee de cmdlet aan de gebruiker wordt geïdentificeerd. En u moet de Windows Power shell-functionaliteit beschrijven die door de cmdlet wordt ondersteund. Zie voor meer informatie over de declaratie syntaxis die wordt gebruikt om het **cmdlet** -kenmerk op te geven de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).

> [!NOTE]
> Het **cmdlet** -kenmerk wordt gedefinieerd door de klasse [System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) . De eigenschappen van deze klasse komen overeen met de declaratie parameters die worden gebruikt bij het declareren van het kenmerk.

## <a name="nouns"></a>Woorden

Het zelfstandige naam woord van de cmdlet specificeert de resources waarop de cmdlet optreedt. Het zelfstandig naam woord onderscheidt uw cmdlets van andere cmdlets.

Zelfstandige naam woorden in de namen van de cmdlets moeten specifiek zijn en in het geval van algemene zelfstandig naam woorden, zoals *Server*, is het raadzaam om een kort voor voegsel toe te voegen waarmee uw resource van andere vergelijk bare bronnen wordt onderscheiden. Bijvoorbeeld een naam van een cmdlet die een zelfstandig nummer met een voor voegsel bevat `Get-SQLServer`. Met de combi natie van een specifiek zelfstandig naam woord met een meer algemene term kan de gebruiker snel de cmdlet vinden op basis van de actie en vervolgens de cmdlet identificeren aan de hand van de bijbehorende resource, terwijl het voor komen van onnodige naam duplicatie van de cmdlet.

Zie [vereiste ontwikkel richtlijnen](./required-development-guidelines.md)voor een lijst met speciale tekens die niet kunnen worden gebruikt in cmdlet-namen.

## <a name="verbs"></a>Termen

Wanneer u een term opgeeft, moet u voor de ontwikkelings richtlijnen een van de vooraf gedefinieerde woorden gebruiken die worden meegeleverd met Windows Power shell. Als u een van deze vooraf gedefinieerde termen gebruikt, zorgt u ervoor dat de cmdlets die u schrijft en de cmdlets die door micro soft en door anderen zijn geschreven, consistent zijn. De opdracht ' Get ' wordt bijvoorbeeld gebruikt voor cmdlets waarmee gegevens worden opgehaald.

Zie [cmdlet verb names](./approved-verbs-for-windows-powershell-commands.md)(Engelstalig) voor meer informatie over richt lijnen voor termen. Zie [vereiste ontwikkel richtlijnen](./required-development-guidelines.md)voor een lijst met speciale tekens die niet kunnen worden gebruikt in cmdlet-namen.

## <a name="supporting-windows-powershell-functionality"></a>Ondersteuning van Windows Power shell-functionaliteit

Met het kenmerk **cmdlet** kunt u ook opgeven dat uw cmdlet een van de algemene functionaliteit ondersteunt die wordt geboden door Windows Power shell. Dit omvat ondersteuning voor algemene functionaliteit, zoals het bevestigen van de gebruikers feedback (ondersteuning voor de functie ShouldProcess) en ondersteuning voor trans acties. (Ondersteuning voor trans acties is geïntroduceerd in Windows Power Shell 2,0).

Zie voor meer informatie over de declaratie syntaxis die wordt gebruikt om het **cmdlet** -kenmerk op te geven de [cmdlet-kenmerk declaratie](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>Definitie van cmdlet-klasse

De volgende code is de definitie voor een GetProc-cmdlet-klasse. U ziet dat Pascal-behuizing wordt gebruikt en dat de naam van de klasse het werk woord en het zelfstandige woord van de cmdlet bevat.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs" range="33-34":::

## <a name="pascal-casing"></a>Pascal-behuizing

Wanneer u een naam wilt voor cmdlets, gebruikt u het hoofdletter gebruik. De cmdlets `Get-Item` en `Get-ItemProperty` tonen bijvoorbeeld de juiste manier om hoofdletter gebruik te gebruiken wanneer u de naamgeving van cmdlets gebruikt.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute-declaratie](./cmdlet-attribute-declaration.md)

[Namen van cmdlet-termen](./approved-verbs-for-windows-powershell-commands.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
