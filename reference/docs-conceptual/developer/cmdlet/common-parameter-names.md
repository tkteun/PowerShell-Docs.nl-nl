---
ms.date: 09/13/2016
ms.topic: reference
title: Namen van veelvoorkomende parameters
description: Namen van veelvoorkomende parameters
ms.openlocfilehash: 506aab290abdb97a6e26c340ac4bd0051244f54b
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860876"
---
# <a name="common-parameter-names"></a>Namen van veelvoorkomende parameters

De para meters die in dit onderwerp worden beschreven, worden **algemene para meters** genoemd. Ze worden toegevoegd aan cmdlets door de Windows Power shell-runtime en kunnen niet worden gedeclareerd door de cmdlet.

> [!NOTE]
> Deze para meters worden ook toegevoegd aan provider-cmdlets en aan functies die met het kenmerk zijn gedecoreerd `CmdletBinding` .

## <a name="general-common-parameters"></a>Algemene algemene para meters

De volgende para meters worden toegevoegd aan alle cmdlets en kunnen worden geopend wanneer de cmdlet wordt uitgevoerd.
Deze para meters worden gedefinieerd door de klasse [System. Management. Automation. internal. Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) .

### <a name="confirm-alias-cf"></a>Bevestigen (alias: CF)

Gegevens type: SwitchParameter

Met deze para meter geeft u op of de cmdlet een prompt krijgt waarin wordt gevraagd of de gebruiker wilt door gaan.

### <a name="debug-alias-db"></a>Debug (alias: DB)

Gegevens type: SwitchParameter

Met deze para meter geeft u op of fout opsporingsgegevens op programmeer niveau kunnen worden weer gegeven op de opdracht regel. Deze berichten zijn bedoeld voor het oplossen van problemen met de werking van de cmdlet en worden gegenereerd door aanroepen naar de methode [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) . Fout opsporings berichten hoeven niet te worden gelokaliseerd.

### <a name="erroraction-alias-ea"></a>Error Action (alias: EA)

Gegevens type: opsomming

Deze para meter geeft aan welke actie moet worden uitgevoerd als er een fout optreedt. De mogelijke waarden voor deze para meter worden gedefinieerd door de inventarisatie [System. Management. Automation. Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="errorvariable-alias-ev"></a>ErrorVariable (alias: EV)

Gegevens type: teken reeks

Met deze para meter wordt de variabele opgegeven waarin objecten worden geplaatst wanneer er een fout optreedt. Als u wilt toevoegen aan deze variabele, gebruikt u +_varnaam_ in plaats van de variabele uit te scha kelen en in te stellen.

### <a name="outbuffer-alias-ob"></a>Outbuffer (alias: OB)

Gegevens type: Int32

Met deze para meter wordt het aantal objecten gedefinieerd dat moet worden opgeslagen in de uitvoer buffer voordat er objecten worden door gegeven aan de pijp lijn. Standaard worden objecten onmiddellijk door gegeven aan de pijp lijn.

### <a name="outvariable-alias-ov"></a>Outvariable (alias: OV)

Gegevens type: teken reeks

Met deze para meter geeft u de variabele op waarin alle uitvoer objecten worden geplaatst die door de cmdlet worden gegenereerd.
Als u wilt toevoegen aan deze variabele, gebruikt u +_varnaam_ in plaats van de variabele uit te scha kelen en in te stellen.

### <a name="pipelinevariable-alias-pv"></a>PipelineVariable (alias: hw)

Gegevens type: teken reeks

Met deze para meter wordt de waarde van het huidige pijplijn element opgeslagen als een variabele voor een benoemde opdracht tijdens het door lopen van de pijp lijn.

## <a name="verbose-alias-vb"></a>Uitgebreid (alias: VB)

Gegevens type: SwitchParameter

Met deze para meter wordt opgegeven of de cmdlet verklarende berichten schrijft die kunnen worden weer gegeven op de opdracht regel. Deze berichten zijn bedoeld om aanvullende hulp te bieden aan de gebruiker en worden gegenereerd door aanroepen naar de methode [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .

### <a name="warningaction-alias-wa"></a>WarningAction (alias: WA)

Gegevens type: opsomming

Deze para meter geeft aan welke actie moet worden uitgevoerd wanneer de cmdlet een waarschuwings bericht schrijft. De mogelijke waarden voor deze para meter worden gedefinieerd door de inventarisatie [System. Management. Automation. Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) .

### <a name="warningvariable-alias-wv"></a>WarningVariable (alias: WV)

Gegevens type: teken reeks

Met deze para meter geeft u de variabele op waarin waarschuwings berichten kunnen worden opgeslagen. Als u wilt toevoegen aan deze variabele, gebruikt u +_varnaam_ in plaats van de variabele uit te scha kelen en in te stellen.

## <a name="risk-mitigation-parameters"></a>Risk-Mitigation para meters

De volgende para meters worden toegevoegd aan cmdlets die bevestiging aanvragen voordat ze hun actie uitvoeren. Zie [bevestiging aanvragen](./requesting-confirmation-from-cmdlets.md)voor meer informatie over bevestigings aanvragen.
Deze para meters worden gedefinieerd door de klasse [System. Management. Automation. internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) .

### <a name="whatif-alias-wi"></a>WhatIf (alias: Wi)

Gegevens type: SwitchParameter

Met deze para meter geeft u op of de cmdlet een bericht schrijft dat de gevolgen van het uitvoeren van de cmdlet beschrijft zonder dat er acties daad werkelijk worden uitgevoerd.

## <a name="transaction-parameters"></a>Transactie parameters

De volgende para meter wordt toegevoegd aan cmdlets die trans acties ondersteunen. Deze para meters worden gedefinieerd door de klasse [System. Management. Automation. internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) . Trans actie-ondersteuning is geïntroduceerd in Power Shell 3,0 en stopgezet in Power shell 6,0.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (alias: usetx)

Gegevens type: SwitchParameter

Met deze para meter geeft u op of de cmdlet de huidige trans actie gaat gebruiken om de actie uit te voeren.

## <a name="see-also"></a>Zie ook

[System. Management. Automation. internal. Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System. Management. Automation. internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System. Management. Automation. internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
