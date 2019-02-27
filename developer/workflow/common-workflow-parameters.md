---
title: Algemene Werkstroomparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5891467-8e13-484d-b7af-32e6bffab35d
caps.latest.revision: 4
ms.openlocfilehash: 2aca4483e500432ef9f52804e85678d2268aa4cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846905"
---
# <a name="common-workflow-parameters"></a>Veelvoorkomende werkstroomparameters

Een workflow-activiteit die is gegenereerd op basis van een Windows PowerShell-cmdlet definieert een aantal parameters dat algemene voor alle activiteiten. Een subset van deze parameters kan worden opgegeven tijdens het ontwerpen zodat werkstroomauteurs activiteiten kunnen aanpassen. Een andere subset van deze parameters kan worden opgegeven door de gebruiker bij het aanroepen van de activiteit.

De algemene werkstroomparameters zijn ondergebracht in verschillende categorieën als volgt.

## <a name="connectivity-parameters"></a>Parameters voor connectiviteit

|Naam|Type|Description|Kan worden opgegeven door de eindgebruiker tijdens de uitvoering?|Kan worden opgegeven door de auteur van de werkstroom tijdens het ontwerpen?|Kan worden opgegeven door de auteur van de werkstroom op instantiëring?|
|----------|----------|-----------------|-----------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------|
|PSComputerName|String[]|Een lijst met computernamen waarvoor u taken starten.|Ja|Ja|Ja|
|PSCredential|[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|De verificatiereferentie op die moet gebruiken om aan te melden op de computers die zijn opgegeven door de parameter PSComputerName. Deze parameter is alleen geldig als PSComputerName is opgegeven.|Ja|Ja|Ja|
|PSPort|UInt32|De poort moet worden gebruikt om uit te voeren van de werkstroom.|Ja|Ja|Ja|
|PSUseSSL|Booleaanse waarde|Secure Sockets Layer (SSL)-protocol gebruiken om te maken van een beveiligde verbinding met de externe computer voor het uitvoeren van de werkstroom.|Ja|Ja|Ja|
|PSConfigurationName|Tekenreeks|De sessieconfiguratie gebruikt voor het uitvoeren van de werkstroom.|Ja|Ja|Ja|
|PSApplicationName|Tekenreeks|Het gedeelte van de naam van toepassing van de URI-verbinding voor het uitvoeren van de werkstroom. Gebruik deze parameter alleen als u de parameter ConnectionURI niet gebruikt.|Ja|Ja|Ja|
|PSThrottleLimit|UInt32|Het maximale aantal gelijktijdige verbindingen dat kan worden bepaald voor het uitvoeren van de werkstroom.|Ja|TBD|Ja|
|PSConnectionURI|String[]|Een matrix met de volledig gekwalificeerde URI's die het opgeven van de eindpunten voor de interactieve sessies gebruikt voor het uitvoeren van de werkstroom.|Ja|Ja|Ja|
|PSAllowRedirection|Booleaanse waarde|Geeft aan of de omleiding van deze verbinding met een andere URI om uit te voeren van de werkstroom toe te staan.|Ja|Ja|Ja|
|PSSessionOption|[System.Management.Automation.Remoting.Pssessionoption](/dotnet/api/System.Management.Automation.Remoting.PSSessionOption)|Geavanceerde opties voor de sessie die is gebruikt voor het uitvoeren van de werkstroom.|Ja|Ja|Ja|
|PSAuthentication|[System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism)|Een waarde van de [System.Management.Automation.Runspaces.Authenticationmechanism](/dotnet/api/System.Management.Automation.Runspaces.AuthenticationMechanism) opsomming die Hiermee geeft u het verificatiemechanisme gebruikt voor het verifiëren van de referenties van de gebruiker.|Ja|Ja|Ja|
|PSCertificateThumbprint|Tekenreeks|De digitale openbare-sleutelcertificaat (X509) van een gebruikersaccount dat gemachtigd is om de werkstroom uitvoert.|Ja|Ja|Ja|

### <a name="behavior-parameters"></a>Parameters voor de werking