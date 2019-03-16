---
title: Namen van algemene parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059657"
---
# <a name="common-parameter-names"></a>Namen van veelvoorkomende parameters

De parameters die worden beschreven in dit onderwerp worden aangeduid als *algemene parameters*. Ze zijn toegevoegd aan de cmdlets door de Windows PowerShell-runtime en kunnen niet worden gedefinieerd door de cmdlet.

> [!NOTE]
> Deze parameters zijn ook toegevoegd aan de provider-cmdlets en -functies die zijn voorzien van de `CmdletBinding` kenmerk.

## <a name="general-common-parameters"></a>Algemene algemene Parameters

De volgende parameters worden toegevoegd aan alle cmdlets en kunnen worden geopend wanneer de cmdlet wordt uitgevoerd. Deze parameters worden gedefinieerd door de [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) klasse.

### <a name="debug-alias-db"></a>Fouten opsporen in (alias: db)

Gegevenstype: SwitchParameter

Deze parameter bepaalt of programmeur op serverniveau foutopsporing die berichten kunnen worden weergegeven op de opdrachtregel. Deze berichten zijn bedoeld voor het oplossen van de werking van de cmdlet en worden gegenereerd door aanroepen naar de [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) methode. Foutopsporingsberichten hoeft te worden gelokaliseerd.

### <a name="erroraction-alias-ea"></a>ErrorAction (alias: ea)

Gegevenstype: Inventarisatie

Deze parameter bepaalt welke actie moet plaatsvinden wanneer er een fout optreedt. De mogelijke waarden voor deze parameter worden gedefinieerd door de [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) opsomming.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: VW)

Gegevenstype: Tekenreeks

Deze parameter bepaalt de variabele waarin objecten plaatsen wanneer een fout optreedt. Als u wilt toevoegen aan deze variabele, gebruik +*varnaam* in plaats van uit te schakelen en de variabele instellen.

### <a name="outvariable-alias-ov"></a>OutVariable (alias: ov)

Gegevenstype: Tekenreeks

Deze parameter bepaalt de variabele in voor alle objecten die worden gegenereerd door de cmdlet uitvoeren. Als u wilt toevoegen aan deze variabele, gebruik +*varnaam* in plaats van uit te schakelen en de variabele instellen.

### <a name="outbuffer-alias-ob"></a>OutBuffer (alias: o)

Gegevenstype: Int32

Deze parameter bepaalt het aantal objecten op te slaan in de uitvoerbuffer voordat de objecten worden doorgegeven in de pijplijn. Objecten worden standaard onmiddellijk doorgegeven in de pijplijn.

### <a name="verbose-alias-vb"></a>Uitgebreide (alias: vb)

Gegevenstype: SwitchParameter

Deze parameter bepaalt of de cmdlet schrijft verklarende berichten die kunnen worden weergegeven op de opdrachtregel. Deze berichten zijn bedoeld voor aanvullende hulp voor de gebruiker en worden gegenereerd door aanroepen naar de [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) methode.

### <a name="warningaction-alias-wa"></a>WarningAction (alias: wa)

Gegevenstype: Inventarisatie

Deze parameter bepaalt welke actie moet plaatsvinden wanneer de cmdlet een waarschuwingsbericht wordt weergegeven schrijft. De mogelijke waarden voor deze parameter worden gedefinieerd door de [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) opsomming.

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: wv)

Gegevenstype: Tekenreeks

Deze parameter bepaalt de variabele waarin waarschuwingsberichten kunnen worden opgeslagen. Als u wilt toevoegen aan deze variabele, gebruik +*varnaam* in plaats van uit te schakelen en de variabele instellen.

## <a name="risk-mitigation-parameters"></a>Risicobeperking Parameters

De volgende parameters worden toegevoegd aan de cmdlets die vraagt om bevestiging voordat ze hun actie uitvoeren. Zie voor meer informatie over aanvragen voor bevestiging [aanvragen bevestiging](./requesting-confirmation-from-cmdlets.md). Deze parameters worden gedefinieerd door de [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) klasse.

### <a name="confirm-alias-cf"></a>Controleer of (alias: cf)

Gegevenstype: SwitchParameter

Deze parameter bepaalt of de cmdlet een bericht waarin u wordt gevraagd weergegeven of de gebruiker of is dat ze willen om door te gaan.

### <a name="whatif-alias-wi"></a>WhatIf (alias: wi)

Gegevenstype: SwitchParameter

Deze parameter bepaalt of een bericht waarin wordt beschreven van de gevolgen van de cmdlet uitvoert zonder daadwerkelijk uitvoeren van een actie door de cmdlet wordt geschreven.

## <a name="transaction-parameters"></a>Transactieparameters

De volgende parameter wordt toegevoegd aan de cmdlets die ondersteuning bieden voor transacties. Deze parameters worden gedefinieerd door de [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) klasse.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Gegevenstype: SwitchParameter

Deze parameter geeft aan of de cmdlet de huidige transactie wordt gebruikt de actie uit te voeren.

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
