---
title: Over het maken van een PowerShell-module Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055934"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Een Windows PowerShell-module maken

Een Windows PowerShell-module biedt een mechanisme voor het registreren van sets met cmdlets en een andere Windows PowerShell-provider met de shell, dus het uitbreiden van de functionaliteit van de shell. Een Windows PowerShell-module kan de cmdlets en providers in een enkele assembly, het kunt registreren of een specifieke lijst met cmdlets en providers.

Module-assembly's moeten worden geïnstalleerd in een beveiligde map, net zoals met andere besturingssystemen. Anders kunnen kwaadwillende gebruikers een assembly vervangen door onveilige code.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell-module klassen

Alle Windows PowerShell-module-klassen die zijn afgeleid van de [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) of [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klassen.

## <a name="examples"></a>Voorbeelden

[Schrijven van een PowerShell-module Windows](./writing-a-windows-powershell-snap-in.md): Dit voorbeeld toont het maken van een module die wordt gebruikt voor het registreren van de cmdlets en providers in een assembly.

[Schrijven van aangepaste Windows PowerShell module](./writing-a-custom-windows-powershell-snap-in.md): Dit voorbeeld laat zien hoe u een aangepaste module die wordt gebruikt voor het registreren van een specifieke set cmdlets en providers die kunnen of bestaat mogelijk niet in een enkele assembly maakt.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Cmdlets registreren](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
