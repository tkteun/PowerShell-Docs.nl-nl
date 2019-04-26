---
title: Voorbeelden van de cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068434"
---
# <a name="cmdlet-samples"></a>Cmdlet-voorbeelden

Deze sectie beschrijft de voorbeeldcode die is opgegeven in de Windows PowerShell 2.0-SDK. U kunt code kopiëren van de onderwerpen in deze sectie of opent u de bronbestanden met de SDK is geïnstalleerd. De [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) biedt Leesmij-bestanden, bronbestanden en Visual Studio-project-bestanden voor elk voorbeeld. Met de SDK is geïnstalleerd, vindt u de voorbeelden in de `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` map.

## <a name="in-this-section"></a>In deze sectie

[Voorbeeld van GetProcessSample01](./getprocesssample01-sample.md) dit voorbeeld laat zien hoe u een cmdlet die worden opgehaald van de processen die op de lokale computer schrijft.

[Voorbeeld van GetProcessSample02](./getprocesssample02-sample.md) dit voorbeeld laat zien hoe u een cmdlet die worden opgehaald van de processen die op de lokale computer schrijft. Het biedt een naamparameter van die kan worden gebruikt om op te geven van de processen worden opgehaald.

[Voorbeeld van GetProcessSample03](./getprocesssample03-sample.md) dit voorbeeld laat zien hoe u een cmdlet die worden opgehaald van de processen die op de lokale computer schrijft. Het biedt een naamparameter van een object van de pijplijn of een waarde van een eigenschap van een object waarvan de de eigenschapsnaam hetzelfde als de parameternaam is kan accepteren.

[Voorbeeld van GetProcessSample04](./getprocesssample04-sample.md) dit voorbeeld laat zien hoe u een cmdlet die worden opgehaald van de processen die op de lokale computer schrijft. Er wordt een nonterminating fout gegenereerd als er een fout optreedt tijdens het ophalen van een proces.

[Voorbeeld van GetProcessSample05](./getprocesssample05-sample.md) in dit voorbeeld ziet u een volledige versie van de cmdlet Get-Proc.

[Voorbeeld van StopProcessSample01](./stopprocesssample01-sample.md) dit voorbeeld laat zien over het schrijven van een cmdlet die aanvragen van feedback van de gebruiker voordat wordt geprobeerd om een proces te stoppen en het implementeren van een `PassThru` parameter die aangeeft dat de gebruiker wil dat de cmdlet om terug te keren een -object.

[Voorbeeld van StopProcessSample02](./stopprocesssample02-sample.md) dit voorbeeld laat zien hoe u een cmdlet die verbose, debug- en waarschuwingsberichten schrijft tijdens het stoppen van processen op de lokale computer schrijft.

[Voorbeeld van StopProcessSample03](./stopprocesssample03-sample.md) dit voorbeeld laat zien hoe u schrijft een cmdlet die parameters aliassen en die hebben jokertekens gebruiken.

[Voorbeeld van StopProcessSample04](./stopprocesssample04-sample.md) dit voorbeeld laat zien hoe u een cmdlet die parametersets verklaart, geeft u de standaardparameter ingesteld, en u kunt een invoerobject schrijft.

[Voorbeeld van Events01](./events01-sample.md) dit voorbeeld laat zien over het maken van een cmdlet waarmee de gebruiker om u te registreren voor gebeurtenissen die worden gegenereerd door [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Gebruikers kunnen, bijvoorbeeld een actie om uit te voeren wanneer een bestand wordt gemaakt onder een bepaalde map registreren met deze cmdlet. In dit voorbeeld is afgeleid van de [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) basisklasse.

## <a name="see-also"></a>Zie ook

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
