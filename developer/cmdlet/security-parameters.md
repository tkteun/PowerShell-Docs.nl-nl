---
title: Beveiligingsparameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849026"
---
# <a name="security-parameters"></a>Beveiligingsparameters

De volgende tabel bevat de aanbevolen namen en de functionaliteit voor parameters die worden gebruikt om te voorzien van informatie over de beveiliging voor een bewerking, zoals parameters die sleutel en bevoegdheden certificaatgegevens opgeeft.

ACL-gegevenstype: Tekenreeks

Deze parameter om op te geven van het toegangsniveau van de controle van de beveiliging voor een catalogus of voor een Uniform Resource Identifier (URI) implementeren.

CertBestand gegevenstype: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan de naam van een bestand met een van de volgende opgeven:

- Een met Base64 of regels DER (Distinguished Encoding) gecodeerd x.509-certificaat

- Een Public Key Cryptography Standards (PKCS) #12-bestand met ten minste één certificaat en de sleutel

CertIssuerName gegevenstype: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan de naam van de verlener van een certificaat opgeven of zodat de gebruiker kan een subtekenreeks opgeven.

CertRequestFile Data type: Tekenreeks

Deze parameter om op te geven van de naam van een bestand met een met Base64- of DER-gecodeerd PKCS #10 certificaataanvraag implementeren.

CertSerialNumber gegevenstype: Tekenreeks

Deze parameter om op te geven van het serienummer dat is uitgegeven door de certificeringsinstantie (CA) implementeren.

CertStoreLocation gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de locatie van het certificaatarchief opgeven. De locatie is doorgaans een bestandspad.

CertSubjectName gegevenstype: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan de verlener van een certificaat opgeven of zodat de gebruiker kan een subtekenreeks opgeven.

CertUsage gegevenstype: Tekenreeks

Deze parameter om op te geven van het gebruik van de sleutel of het uitgebreide sleutelgebruik implementeren. De sleutel kan worden weergegeven als een en ander maskeren, wat een object-id (OID), of een tekenreeks.

Referentie-gegevenstype: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)

Implementeer deze parameter zodat de cmdlet wordt automatisch de gebruiker gevraagd om een gebruikersnaam of wachtwoord. Een prompt voor zowel wordt weergegeven als een volledige referentie niet rechtstreeks worden verstrekt.

CSP-naam-gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de naam van de certificaat-provider (CSP) opgeven.

CSPType gegevenstype: Geheel getal

Implementeer deze parameter zodat de gebruiker kan het type van de CSP opgeven.

Gegevens van het type groep: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan een verzameling van beveiligings-principals voor toegang tot opgeven. Zie voor meer informatie, de beschrijving van de `Principal` parameter.

KeyAlgorithm gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan het genereren van sleutels-algoritme moet worden gebruikt voor beveiliging opgeven.

Naam van sleutelcontainer gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de naam van de sleutelcontainer opgeven.

Sleutellengte gegevenstype: Geheel getal

Implementeer deze parameter zodat de gebruiker de lengte van de sleutel in bits kunt opgeven.

Bewerking gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een actie die kan worden uitgevoerd op een beveiligde object opgeven.

Principal-gegevenstype: Tekenreeks

Deze parameter implementeren zodat de gebruiker kan een unieke identificeerbare entiteit voor toegang tot opgeven.

Bevoegdheden voor gegevenstype: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan het recht voor dat een cmdlet uit te voeren een bewerking voor een bepaalde entiteit moet opgeven.

Bevoegdheden gegevenstype: Matrix van bevoegdheden

Implementeer deze parameter zodat de gebruiker kan de rechten die een cmdlet uit te voeren van de bewerking voor een bepaalde vermelding moet opgeven.

Gegevenstype van de rol: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan een reeks bewerkingen die kunnen worden uitgevoerd door een entiteit opgeven.

SaveCred gegevenstype: SwitchParameter

Implementeer deze parameter zodat de referenties die zijn opgeslagen door de gebruiker worden gebruikt wanneer de parameter is opgegeven.

Het bereik van gegevens van het type: Tekenreeks

Implementeer deze parameter zodat de gebruiker kan de groep met beveiligde objecten voor de cmdlet opgeven.

SID Data type: Tekenreeks

Implementeer deze parameter zodat de gebruiker een unieke id die staat voor een principal kan opgeven.

Vertrouwde gegevenstype: SwitchParameter

Implementeer deze parameter zodat vertrouwensniveaus worden ondersteund wanneer de parameter is opgegeven.

TrustLevel gegevenstype: Trefwoord

Implementeer deze parameter zodat het vertrouwensniveau dat wordt ondersteund door de gebruiker kan opgeven. Mogelijke waarden zijn bijvoorbeeld internet en intranet fulltrust.

## <a name="see-also"></a>Zie ook

[Cmdlet-Parameters](./cmdlet-parameters.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
