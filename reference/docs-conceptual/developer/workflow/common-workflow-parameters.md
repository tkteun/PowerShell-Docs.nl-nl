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
ms.openlocfilehash: b2e8f272a82ee03de306fd8eac45e109142f6284
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356656"
---
# <a name="common-workflow-parameters"></a>Veelvoorkomende werkstroomparameters

Een werk stroom activiteit die is gegenereerd op basis van een Windows Power shell-cmdlet definieert een aantal para meters die gemeen schappelijk zijn voor alle activiteiten. Een subset van deze para meters kan tijdens de ontwerp tijd worden opgegeven, zodat werk stroom ontwerpers activiteiten kunnen aanpassen. Een andere subset van deze para meters kan door de gebruiker worden opgegeven bij het aanroepen van de activiteit.

De algemene werk stroom parameters zijn als volgt gegroepeerd in verschillende categorieën.

## <a name="connectivity-parameters"></a>Connectiviteits parameters

|Naam|Type|Beschrijving|Kan tijdens de uitvoerings tijd worden opgegeven door de eind gebruiker?|Kan worden opgegeven door werk stroom auteur tijdens de ontwerp tijd?|Kan worden opgegeven door werk stroom auteur bij instantiëring?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Een lijst met computer namen waarvoor taken moeten worden gestart.|Ja|Ja|Ja|
|PSCredential|[System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|De verificatie referentie die moet worden gebruikt om u aan te melden bij de computers die zijn opgegeven met de para meter PSComputerName. Deze para meter is alleen geldig als PSComputerName is opgegeven.|Ja|Ja|Ja|
|PSPort|UInt32|De poort die moet worden gebruikt om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSUseSSL|Booleaanse waarde|Gebruik Secure Sockets Layer Protocol (SSL) om een beveiligde verbinding met de externe computer tot stand te brengen om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSConfigurationName|Tekenreeks|De sessie configuratie die wordt gebruikt om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSApplicationName|Tekenreeks|Het gedeelte toepassings naam van de verbindings-URI voor het uitvoeren van de werk stroom. Gebruik deze para meter alleen als u de para meter ConnectionURI niet gebruikt.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Het maximum aantal gelijktijdige verbindingen dat tot stand kan worden gebracht om de werk stroom uit te voeren.|Ja|TBD|Ja|
|PSConnectionURI|String[]|Een matrix met volledig gekwalificeerde Uri's waarmee de eind punten voor de interactieve sessies worden opgegeven waarmee de werk stroom wordt uitgevoerd.|Ja|Ja|Ja|
|PSAllowRedirection|Booleaanse waarde|Hiermee geeft u op of omleiding van deze verbinding naar een alternatieve URI mag worden uitgevoerd om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSSessionOption|[System. Management. Automation. Remoting. Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Geavanceerde opties voor de sessie die wordt gebruikt om de werk stroom uit te voeren.|Ja|Ja|Ja|
|PSAuthentication|[System. Management. Automation. Runspaces. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Een waarde van de opsomming [System. Management. Automation. Runspaces. Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) die het authenticatie mechanisme specificeert dat wordt gebruikt om de referenties van de gebruiker te verifiëren.|Ja|Ja|Ja|
|PSCertificateThumbprint|Tekenreeks|Het digitale open bare-sleutel certificaat (x509) van een gebruikers account dat is gemachtigd om de werk stroom uit te voeren.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Gedrags parameters