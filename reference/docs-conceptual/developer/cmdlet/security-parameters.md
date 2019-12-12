---
title: Beveiligings parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359349"
---
# <a name="security-parameters"></a>Beveiligingsparameters

De volgende tabel bevat de aanbevolen namen en functionaliteit voor para meters die worden gebruikt voor het leveren van beveiligings gegevens voor een bewerking, zoals para meters voor het opgeven van informatie over certificaat sleutels en bevoegdheden.

|Parameter|Functionaliteit|
|---|---|
|**MIGREREN**<br>Gegevenstype: tekenreeks|Implementeer deze para meter om het toegangs beheer niveau voor een catalogus of een Uniform Resource Identifier (URI) op te geven.|
|**CERT**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam van een bestand kan opgeven dat een van de volgende bevat:<br>-Een base64-of Distinguished Encoding Rules (DER) gecodeerd x. 509-certificaat<br>-Een PKCS-bestand (Public Key Cryptography Standards) #12 dat ten minste één certificaat en sleutel bevat|
|**CertIssuerName**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam van de verlener van een certificaat kan opgeven of dat de gebruiker een subtekenreeks kan opgeven.|
|**CertRequestFile**<br>Gegevenstype: tekenreeks|Implementeer deze para meter om de naam op te geven van een bestand dat een base64-of DER-gecodeerd PKCS #10 certificaat aanvraag bevat.|
|**CertSerialNumber**<br>Gegevenstype: tekenreeks|Implementeer deze para meter om het serie nummer op te geven dat is uitgegeven door de certificerings instantie.|
|**CertStoreLocation**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de locatie van het certificaat archief kan opgeven. De locatie is doorgaans een bestandspad.|
|**CertSubjectName**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de verlener van een certificaat kan opgeven of dat de gebruiker een subtekenreeks kan opgeven.|
|**CertUsage**<br>Gegevenstype: tekenreeks|Implementeer deze para meter om het sleutel gebruik of de Enhanced Key Usage op te geven. De sleutel kan worden weer gegeven als een bitmasker, een bit, een object-id (OID) of een teken reeks.|
|**Referentie**<br>Gegevens type: [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementeer deze para meter zodat de cmdlet de gebruiker automatisch vraagt naar een gebruikers naam of wacht woord. Er wordt een prompt voor beide weer gegeven als een volledige referentie niet rechtstreeks is opgegeven.|
|**CSPName**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam van de Certificate Service Provider (CSP) kan opgeven.|
|**CSPType**<br>Gegevenstype: geheel getal|Implementeer deze para meter zodat de gebruiker het type CSP kan opgeven.|
|**Groep**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een verzameling principals kan opgeven voor toegang. Zie de beschrijving van de **Principal** para meter voor meer informatie.|
|**Algoritme**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de algoritme voor sleutel generatie kan opgeven die moet worden gebruikt voor de beveiliging.|
|**Paar**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de naam van de sleutel container kan opgeven.|
|**Sleutel lengte**<br>Gegevenstype: geheel getal|Implementeer deze para meter zodat de gebruiker de lengte van de sleutel in bits kan opgeven.|
|**Bewerking**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een actie kan opgeven die op een beveiligd object kan worden uitgevoerd.|
|**Principaal**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een unieke Identificeer bare entiteit kan opgeven voor toegang.|
|**Bevoegdheden**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker het recht kan opgeven dat een cmdlet een bewerking voor een bepaalde entiteit moet uitvoeren.|
|**Bevoegdheden**<br>Gegevens type: matrix van bevoegdheden|Implementeer deze para meter zodat de gebruiker de rechten kan opgeven die een cmdlet nodig heeft om de bewerking voor een bepaalde vermelding uit te voeren.|
|**Role**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een set bewerkingen kan opgeven die door een entiteit kan worden uitgevoerd.|
|**SaveCred**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat referenties die eerder zijn opgeslagen door de gebruiker worden gebruikt wanneer de para meter wordt opgegeven.|
|**Bereik**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker de groep beveiligde objecten kan opgeven voor de cmdlet.|
|**GEVAL**<br>Gegevenstype: tekenreeks|Implementeer deze para meter zodat de gebruiker een unieke id kan opgeven die een principal vertegenwoordigt.|
|**Veilige**<br>Gegevens type: SwitchParameter|Implementeer deze para meter zodat de vertrouwens niveaus worden ondersteund wanneer de para meter wordt opgegeven.|
|**TrustLevel**<br>Gegevens type: tref woord|Implementeer deze para meter zodat de gebruiker het vertrouwens niveau kan opgeven dat wordt ondersteund. Mogelijke waarden zijn bijvoorbeeld Internet, intranet en FullTrust.|

## <a name="see-also"></a>Zie ook

[Cmdlet-para meters](./cmdlet-parameters.md)

[Een Windows Power shell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)

[Windows Power shell SDK](../windows-powershell-reference.md)
