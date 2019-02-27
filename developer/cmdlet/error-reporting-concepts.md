---
title: Concepten voor foutrapportage | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846163"
---
# <a name="error-reporting-concepts"></a>Concepten voor foutrapportage

Windows PowerShell biedt twee methoden voor die fouten rapporteren: een mechanisme voor *wordt beëindigd fouten* en een ander mechanisme voor *niet-afsluitfouten*. Het is goed belangrijk voor uw cmdlet fouten rapporteren zodat de hosttoepassing die uw cmdlets wordt uitgevoerd op de juiste manier kan reageren.

De cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) methode wanneer er een fout optreedt die niet bestaat of kunt u voorkomen dat de cmdlet om door te gaan voor het verwerken van de invoer-objecten. De cmdlet moet aanroepen de [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) methode voor het rapporteren van niet-afsluitfouten wanneer de cmdlet kunt doorgaan met het verwerken van de invoer-objecten. Beide methoden bieden een foutrecord die de host-toepassing gebruiken kunt om de oorzaak van de fout onderzoeken.

Gebruik de volgende richtlijnen om te bepalen of een fout wordt een afsluitende of niet-afsluitfout.

- Een fout is een afsluitfout als deze wordt voorkomen uw cmdlet dat voortgezet voor het verwerken van het huidige object of verwerken, is verdere invoer objecten, ongeacht hun inhoud.

- Een fout is een afsluitfout als u de cmdlet niet wilt doorgaan met het verwerken van het huidige object of eventuele verdere invoer objecten, ongeacht hun inhoud.

- Een fout is een afsluitfout als dit zich voordoet in een cmdlet die niet wordt geaccepteerd of een object geretourneerd of als het vindt plaats in een cmdlet die accepteert of slechts één object geretourneerd.

- Een fout is een niet-afsluitfout als u de cmdlet wilt doorgaan met het verwerken van het huidige object en alle verdere invoer objecten.

- Een fout is een niet-afsluitfout als deze is gekoppeld aan een specifieke invoer object of een subset van de invoer-objecten.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Windows PowerShell-foutrecords](./windows-powershell-error-records.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
