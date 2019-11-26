---
title: Voor beelden van cmdlets | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356537"
---
# <a name="cmdlet-samples"></a>Cmdlet-voorbeelden

In deze sectie wordt de voorbeeld code beschreven die is opgenomen in de Windows Power Shell 2,0 SDK. U kunt code kopiëren uit de onderwerpen in deze sectie of de bron bestanden openen die met de SDK zijn geïnstalleerd. De [Windows Power shell 2,0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) bevat Leesmij-bestanden, bron bestanden en Visual Studio-project bestanden voor elk voor beeld. Als de SDK is geïnstalleerd, kunt u de voor beelden vinden onder de map `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

## <a name="in-this-section"></a>In deze sectie

[GetProcessSample01](./getprocesssample01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald.

[GetProcessSample02](./getprocesssample02-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Het biedt een naam parameter die kan worden gebruikt om de processen op te geven die moeten worden opgehaald.

[GetProcessSample03](./getprocesssample03-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Het biedt een naam parameter die een object van de pijp lijn kan accepteren of een waarde van een eigenschap van een object waarvan de naam van de eigenschap gelijk is aan de naam van de para meter.

[GetProcessSample04](./getprocesssample04-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee de processen op de lokale computer worden opgehaald. Er wordt een niet-afsluit fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces.

[GetProcessSample05](./getprocesssample05-sample.md) -voor beeld In dit voor beeld wordt een volledige versie van de cmdlet Get-proc weer gegeven.

[StopProcessSample01](./stopprocesssample01-sample.md) -voor beeld Dit voor beeld laat zien hoe u een cmdlet schrijft die feedback van de gebruiker vraagt voordat deze probeert een proces te stoppen, en hoe u een para meter `PassThru` implementeert die aangeeft dat de gebruiker de cmdlet een object wil laten retour neren.

[StopProcessSample02](./stopprocesssample02-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarmee fout opsporing, uitgebreide en waarschuwings berichten worden geschreven terwijl processen op de lokale computer worden gestopt.

[StopProcessSample03](./stopprocesssample03-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft waarvan de para meters aliassen hebben en die joker tekens ondersteunen.

[StopProcessSample04](./stopprocesssample04-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet schrijft die parameter sets declareert, de standaard parameterset opgeeft en een invoer object accepteert.

[Events01](./events01-sample.md) -voor beeld In dit voor beeld ziet u hoe u een cmdlet maakt waarmee de gebruiker zich kan registreren voor gebeurtenissen die worden gegenereerd door [System. io. Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Met deze cmdlet kunnen gebruikers bijvoorbeeld een actie registreren die moet worden uitgevoerd wanneer een bestand wordt gemaakt in een specifieke map. Dit voor beeld is afgeleid van de basis klasse [micro soft. Power shell. commands. Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="see-also"></a>Zie ook

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)