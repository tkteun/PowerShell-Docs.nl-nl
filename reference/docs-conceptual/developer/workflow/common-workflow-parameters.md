---
title: Algemene werk stroom parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: c436ad017be72d97c26552c85d9fd212892ec731
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557513"
---
# <a name="common-workflow-parameters"></a>Veelvoorkomende werkstroomparameters

Een werk stroom activiteit die is gegenereerd op basis van een Windows Power shell-cmdlet definieert een aantal para meters die gemeen schappelijk zijn voor alle activiteiten. Een subset van deze para meters kan tijdens de ontwerp tijd worden opgegeven, zodat werk stroom ontwerpers activiteiten kunnen aanpassen. Een andere subset van deze para meters kan door de gebruiker worden opgegeven bij het aanroepen van de activiteit.

De algemene werk stroom parameters zijn als volgt gegroepeerd in verschillende categorieën.

## <a name="connectivity-parameters"></a>Connectiviteits parameters

|Name|Type|Beschrijving|Kan tijdens de uitvoerings tijd worden opgegeven door de eind gebruiker?|Kan worden opgegeven door werk stroom auteur tijdens de ontwerp tijd?|Kan worden opgegeven door werk stroom auteur bij instantiëring?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|Teken reeks []|Een lijst met computer namen waarvoor taken moeten worden gestart.|Ja|Ja|Ja|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|De verificatie referentie die moet worden gebruikt om u aan te melden bij de computers die zijn opgegeven met de para meter PSComputerName. Deze para meter is alleen geldig als PSComputerName is opgegeven.|Ja|Ja|Ja|
|PSPort|UInt32|De poort die moet worden gebruikt om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSUseSSL|Booleaans|Gebruik Secure Sockets Layer Protocol (SSL) om een beveiligde verbinding met de externe computer tot stand te brengen om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSConfigurationName|Tekenreeks|De sessie configuratie die wordt gebruikt om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSApplicationName|Tekenreeks|Het gedeelte toepassings naam van de verbindings-URI voor het uitvoeren van de werk stroom. Gebruik deze para meter alleen als u de para meter ConnectionURI niet gebruikt.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Het maximum aantal gelijktijdige verbindingen dat tot stand kan worden gebracht om de werk stroom uit te voeren.|Ja|NOG TE BEPALEN|Ja|
|PSConnectionURI|Teken reeks []|Een matrix met volledig gekwalificeerde Uri's waarmee de eind punten voor de interactieve sessies worden opgegeven waarmee de werk stroom wordt uitgevoerd.|Ja|Ja|Ja|
|PSAllowRedirection|Booleaans|Hiermee geeft u op of omleiding van deze verbinding naar een alternatieve URI mag worden uitgevoerd om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSSessionOption|[System. Management. Automation. Remoting. Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Geavanceerde opties voor de sessie die wordt gebruikt om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSAuthentication|[System. Management. Automation. Runspaces. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Een waarde van de opsomming [System. Management. Automation. Runspaces. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) die het authenticatie mechanisme specificeert dat wordt gebruikt om de referenties van de gebruiker te verifiëren.|Ja|Ja|Ja|
|PSCertificateThumbprint|Tekenreeks|Het digitale open bare-sleutel certificaat (x509) van een gebruikers account dat is gemachtigd om de werk stroom uit te voeren.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Gedrags parameters
