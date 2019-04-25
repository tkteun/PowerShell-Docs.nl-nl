---
title: Cmdlet klassendeclaratie | Microsoft Docs
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
ms.openlocfilehash: 3168275423dc65fcb2e41dedd9bea275ede58397
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068637"
---
# <a name="cmdlet-class-declaration"></a>Declaratie van cmdlet-klassen

Een Microsoft .NET Framework-klasse is gedeclareerd als een cmdlet door op te geven de **Cmdlet** kenmerk, zoals metagegevens voor de klasse. (De **Cmdlet** kenmerk is de enige vereiste kenmerk voor alle cmdlets). Wanneer u opgeeft de **Cmdlet** kenmerk, moet u het werkwoord-en-zelfstandig naamwoord paar die de cmdlet voor de gebruiker identificeert. Daarnaast moet u de Windows PowerShell-functionaliteit die ondersteuning biedt voor de cmdlet beschrijft. Voor meer informatie over de syntaxis van de declaratie die wordt gebruikt om op te geven de **Cmdlet** kenmerk, Zie [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).

> [!NOTE]
> De **Cmdlet** kenmerk wordt gedefinieerd door de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) klasse. De eigenschappen van deze klasse komen overeen met de declaratie-parameters die worden gebruikt wanneer u het kenmerk declareren.

## <a name="nouns"></a>Zelfstandige naamwoorden

Het zelfstandig naamwoord van de cmdlet Hiermee geeft u de resources waarop de cmdlet fungeert. Het zelfstandig naamwoord wordt onderscheid gemaakt tussen de cmdlets van andere cmdlets.

Zelfstandige naamwoorden in namen van de cmdlets moet specifiek, en in het geval van algemene zelfstandige naamwoorden, zoals *server*, het is raadzaam om toe te voegen een korte voorvoegsel dat wordt onderscheid gemaakt uw resource vanuit andere vergelijkbare resources tussen. Bijvoorbeeld, een cmdletnaam met een zelfstandig naamwoord met het voorvoegsel is `Get-SQLServer`. De combinatie van een specifieke zelfstandig naamwoord met een algemene term kan de gebruiker de cmdlet snel vinden door de bijbehorende actie en klikt u vervolgens de cmdlet identificeren door de resource zonder duplicatie van onnodige cmdlet-naam.

Zie voor een lijst van speciale tekens die niet in de namen van de cmdlets worden gebruikt, [vereist ontwikkeling richtlijnen](./required-development-guidelines.md).

## <a name="verbs"></a>Termen

Wanneer u een term opgeeft, wordt de richtlijnen voor ontwikkeling moeten u een van de vooraf gedefinieerde bewerkingen die worden geleverd door Windows PowerShell te gebruiken. Met behulp van een van deze vooraf gedefinieerde bewerkingen, wordt u zorgen voor consistentie tussen de cmdlets die u schrijft en de cmdlets die zijn ontwikkeld door Microsoft en door anderen. Bijvoorbeeld, wordt de term 'Ophalen' gebruikt voor cmdlets waarmee gegevens worden opgehaald.

Zie voor meer informatie over richtlijnen voor termen [namen van de term cmdlets](./approved-verbs-for-windows-powershell-commands.md). Zie voor een lijst van speciale tekens die niet in de namen van de cmdlets worden gebruikt, [vereist ontwikkeling richtlijnen](./required-development-guidelines.md).

## <a name="supporting-windows-powershell-functionality"></a>Ondersteuning van Windows PowerShell-functionaliteit

De **Cmdlet** kenmerk ook kunt u opgeven dat de cmdlet biedt ondersteuning voor enkele van de algemene functionaliteit die wordt geleverd door Windows PowerShell. Dit omvat ondersteuning voor algemene functionaliteit zoals (aangeduid als ondersteuning voor de functie shouldprocess wordt overgeslagen) de bevestiging van de gebruiker feedback en ondersteuning voor transacties. (Ondersteuning voor transacties is geïntroduceerd in Windows PowerShell 2.0).

Voor meer informatie over de syntaxis van de declaratie die wordt gebruikt om op te geven de **Cmdlet** kenmerk, Zie [Cmdlet kenmerkdeclaratie](./cmdlet-attribute-declaration.md).

## <a name="cmdlet-class-definition"></a>De definitie van de cmdlet-klasse

De volgende code wordt de definitie voor een cmdlet GetProc klasse. U ziet dat Pascal hoofdlettergebruik wordt gebruikt en dat de naam van de klasse het werkwoord en een zelfstandig naamwoord van de cmdlet bevat.

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L33-L34 "GetProcessSample01.cs")]

## <a name="pascal-casing"></a>Pascal hoofdlettergebruik

Wanneer u cmdlets naam, gebruikt u Pascal hoofdlettergebruik. Bijvoorbeeld, de `Get-Item` en `Get-ItemProperty` cmdlets weer de juiste manier hoofdletters gebruikt bij het benoemen van cmdlets.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute)

[CmdletAttribute declaratie](./cmdlet-attribute-declaration.md)

[Namen van de cmdlet-bewerking](./approved-verbs-for-windows-powershell-commands.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
