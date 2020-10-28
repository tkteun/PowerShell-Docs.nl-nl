---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-voorbeelden
description: Cmdlet-voorbeelden
ms.openlocfilehash: 6ee149f611e5af5c45a62363e19e66bf200c0c0a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668249"
---
# <a name="cmdlet-samples"></a>Cmdlet-voorbeelden

In deze sectie wordt de voorbeeld code beschreven die is opgenomen in de Windows Power Shell 2,0 SDK. U kunt code kopiëren uit de onderwerpen in deze sectie of de bron bestanden openen die met de SDK zijn geïnstalleerd. De [Windows Power shell 2,0 Software Development Kit (SDK)](https://www.microsoft.com/download/details.aspx?id=2560) bevat Leesmij-bestanden, bron bestanden en Visual Studio-project bestanden voor elk voor beeld. Als de SDK is geïnstalleerd, kunt u de voor beelden in de `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` map vinden.

## <a name="in-this-section"></a>In deze sectie

[GetProcessSample01](./getprocesssample01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald.

[GetProcessSample02](./getprocesssample02-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Het biedt een naam parameter die kan worden gebruikt om de processen op te geven die moeten worden opgehaald.

[GetProcessSample03](./getprocesssample03-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Het biedt een naam parameter die een object van de pijp lijn kan accepteren of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.

[GetProcessSample04](./getprocesssample04-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Er wordt een niet-afsluit fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces.

[GetProcessSample05](./getprocesssample05-sample.md) -voor beeld In dit voor beeld ziet u een volledige versie van de cmdlet Get-Proc.

[StopProcessSample01](./stopprocesssample01-sample.md) -voor beeld Dit voor beeld laat zien hoe u een cmdlet schrijft die feedback van de gebruiker vraagt voordat deze probeert een proces te stoppen, en hoe u een `PassThru` para meter implementeert die aangeeft dat de gebruiker de cmdlet een object wil laten retour neren.

[StopProcessSample02](./stopprocesssample02-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee fout opsporing, uitgebreide en waarschuwings berichten worden geschreven terwijl processen op de lokale computer worden gestopt.

[StopProcessSample03](./stopprocesssample03-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarvan de para meters aliassen hebben en die joker tekens ondersteunen.

[StopProcessSample04](./stopprocesssample04-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft die parameter sets declareert, de standaard parameterset opgeeft en een invoer object accepteert.

[Events01](./events01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet maakt waarmee de gebruiker zich kan registreren voor gebeurtenissen die worden gegenereerd door [System. io. Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Met deze cmdlet kunnen gebruikers bijvoorbeeld een actie registreren die moet worden uitgevoerd wanneer een bestand wordt gemaakt in een specifieke map. Dit voor beeld is afgeleid van de basis klasse [micro soft. Power shell. commands. Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="see-also"></a>Zie ook

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
