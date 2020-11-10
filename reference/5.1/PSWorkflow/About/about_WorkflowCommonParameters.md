---
description: In dit onderwerp worden de para meters beschreven die geldig zijn voor alle Windows Power shell-werk stroom opdrachten. Omdat de Windows Power shell-engine deze aan werk stromen toevoegt, kunt u deze para meters op elke werk stroom gebruiken. ze worden automatisch ingeschakeld voor de werk stromen die u ontwerpt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: c371666d4f58386848e7ef715b7c804dc1e8f28e
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387784"
---
# <a name="about-workflowcommonparameters"></a>Over WorkflowCommonParameters

## <a name="short-description"></a>KORTE BESCHRIJVING

In dit onderwerp worden de para meters beschreven die geldig zijn voor alle Windows Power shell-werk stroom opdrachten. Omdat de Windows Power shell-engine deze aan werk stromen toevoegt, kunt u deze para meters op elke werk stroom gebruiken. ze worden automatisch ingeschakeld voor de werk stromen die u ontwerpt.

## <a name="long-description"></a>LANGE BESCHRIJVING

Algemene para meters van de Windows Power shell-werk stroom zijn een set cmdlet-para meters die u kunt gebruiken met alle Windows Power shell-werk stromen en-activiteiten. Ze worden toegevoegd door de werk stroom-engine van Windows Power shell, niet door de auteur van de werk stroom, en ze zijn automatisch beschikbaar voor werk stromen en activiteiten. Werk stromen die drie niveaus diep zijn genest, bieden echter geen ondersteuning voor algemene para meters, waaronder algemene werk stroom parameters.

Alle werk stroom parameters zijn optioneel en hebben de naam (niet positioneel). Ze nemen geen invoer van de pijp lijn.

De meeste algemene werk stroom parameters hebben een PS-voor voegsel, zoals `PSComputerName` en `PSCredential` . Met de para meters voor de voor voegsels van PS worden de verbinding en de uitvoerings omgeving voor de doel computers geconfigureerd, ook wel ' externe knoop punten ' genoemd.

Veel van de algemene werk stroom parameters, zoals `PSAllowRedirection` en `AsJob` , hebben namen die vergelijkbaar zijn met de para meters die worden gebruikt in Windows Power shell voor externe toegang en achtergrond taken. Deze para meters werken op dezelfde manier als de para meters voor externe communicatie en taak, zodat u de kennis kunt gebruiken die u hebt ontwikkeld in externe communicatie en taken voor het beheren van werk stromen.

Werk stromen worden geïntroduceerd in Windows Power Shell 3,0.

### <a name="parameter-descriptions"></a>PARAMETER BESCHRIJVINGEN

In deze sectie worden de algemene werk stroom parameters beschreven.

#### <a name="-asjob-switchparameter"></a>-AsJob \<SwitchParameter\>

De werk stroom wordt uitgevoerd als een werk stroom taak. De werk stroom opdracht retourneert onmiddellijk een object dat een bovenliggende taak vertegenwoordigt. De bovenliggende taak bevat de onderliggende taken die worden uitgevoerd op elk van de doel computers. Gebruik de taak-cmdlets om de taak te beheren. Gebruik [Receive-job](xref:Microsoft.PowerShell.Core.Receive-Job)om de taak resultaten te verkrijgen.

#### <a name="-jobname-string"></a>-JobName \<String\>

Hiermee geeft u een beschrijvende naam voor de werk stroom taak op. Taken hebben standaard de naam taak \<n\> , waarbij \<n\> een rang nummer is.

Als u de para meter JobName in een werk stroom opdracht gebruikt, wordt de werk stroom uitgevoerd als een taak. de werk stroom opdracht retourneert een taak object, zelfs als u de `AsJob` para meter niet in de opdracht opneemt.

Zie [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)voor meer informatie over Windows Power shell-achtergrond taken.

#### <a name="-psallowredirection-switchparameter"></a>-PSAllowRedirection \<SwitchParameter\>

Hiermee kan de verbinding met de doel computers worden omgeleid.

Wanneer u de `PSConnectionURI` para meter gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Windows Power shell omgeleid, maar u kunt de `PSAllowRedirection` para meter gebruiken om de verbinding met de doel computer mogelijk te maken.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de `MaximumConnectionRedirectionCount` eigenschap van de `$PSSessionOption` Voorkeurs variabele in te stellen of de `MaximumConnectionRedirectionCount` eigenschap van de waarde van de `PSSessionOption parameter` . De standaard waarde is 5. Zie de beschrijving van de `PSSessionOption` para meter en [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor meer informatie.

#### <a name="-psapplicationname-string"></a>-PSApplicationName \<String\>

Hiermee geeft u het segment van de toepassings naam op van de verbindings-URI die wordt gebruikt om verbinding te maken met de doel computers. Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de `ConnectionURI` para meter niet in de opdracht gebruikt.

De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de lokale computer. Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.

De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden. De waarde van deze para meter moet overeenkomen met de waarde van de `URLPrefix` eigenschap van een listener op de externe computer.

#### <a name="-psauthentication-authenticationmechanism"></a>-PSAuthentication \<AuthenticationMechanism\>

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren wanneer er verbinding wordt gemaakt met de doel computers.

Geldige waarden zijn:

- **Standaard**
- **Basic**
- **CredSSP**
- **Samenvatting**
- **Kerberos**
- **Afspraken**
- **NegotiateWithImplicitCredential**

De standaard waarde is **standaard**.

Voor informatie over de waarden van deze para meter, zie de beschrijving van de `System.Management.Automation.Runspaces.AuthenticationMechanism` inventarisatie in de Power shell-SDK.

> [!WARNING]
> CredSSP-verificatie (Credential Security service provider), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

#### <a name="-psauthenticationlevel-authenticationlevel"></a>-PSAuthenticationLevel \<AuthenticationLevel\>

Hiermee geeft u het verificatie niveau voor de verbindingen met de doel computers.
De standaard waarde is **standaard**.

Geldige waarden zijn:

|Naam |Beschrijving |
|---------|---------|
|**Behoudt** | Het verificatie niveau is hetzelfde als de vorige opdracht. |
|**Standaard** | Windows-verificatie. |
|**Geen** | Geen COM-verificatie.   |
|**Verbinding maken** | COM-verificatie op verbinding niveau.|
|**Call** | COM-verificatie op aanroep niveau.   |
|**Pakket** | COM-verificatie op pakket niveau.|
|**PacketIntegrity** | COM-verificatie op pakket integriteit-niveau.  |
|**PacketPrivacy** | COM-verificatie op privacyniveau op pakket niveau. |

#### <a name="-pscertificatethumbprint-string"></a>-PSCertificateThumbprint \<String\>

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat wilt ophalen, gebruikt u de [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) of [Get-Child item] (.. /.. /Microsoft.PowerShell.Management/Get-Childitem.md)-cmdlets in het Windows Power shell-certificaat: station.

#### <a name="-pscomputername-string"></a>-PSComputerName \<String[]\>

Hiermee geeft u de lijst met computers die de doel knooppunten van de werk stroom zijn.
Opdrachten of activiteiten in een werk stroom worden uitgevoerd op de computers die zijn opgegeven met behulp van deze para meter. Standaard is dit de lokale computer.

Typ de NETBIOS-naam, het IP-adres of de FQDN-naam (Fully Qualified Domain Name) van een of meer computers in een door komma's gescheiden lijst. Typ de computer naam, ' localhost ' of een punt (.) om de lokale computer op te geven.

`PSComputerName`Open Windows Power shell met de optie als administrator uitvoeren om de lokale computer in de waarde van de para meter op te vragen.

Als deze para meter wordt wegge laten uit de opdracht, of de waarde is `$null` of een lege teken reeks is, is het werk stroom doel de lokale computer en wordt Windows Power shell Remoting niet gebruikt om de opdracht uit te voeren.

Als u een IP-adres wilt gebruiken in de waarde van de `ComputerName` para meter, moet de opdracht de `PSCredential` para meter bevatten. De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie *"een computer toevoegen aan de lijst met vertrouwde hosts"* in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.

#### <a name="-psconfigurationname-string"></a>-PSConfigurationName \<String\>

Hiermee geeft u de sessie configuraties op die worden gebruikt voor het configureren van sessies op de doel computers. Voer een sessie configuratie in op de doel computers (niet op de computer van de werk stroom server). De standaardwaarde is `Microsoft.PowerShell.Workflow`.

#### <a name="-psconnectionretrycount-uint"></a>-PSConnectionRetryCount \<UInt\>

Hiermee geeft u het maximum aantal pogingen op om verbinding te maken met elke doel computer als de eerste verbindings poging mislukt. Voer een getal tussen 1 en 4.294.967.295 (UInt. MaxValue) in. De standaard waarde, nul (0), vertegenwoordigt geen nieuwe pogingen.

#### <a name="-psconnectionretryintervalsec-uint"></a>-PSConnectionRetryIntervalSec \<UInt\>

Hiermee geeft u de vertraging tussen nieuwe pogingen in seconden op. De standaardwaarde is nul (0). Deze para meter is alleen geldig wanneer de waarde van PSConnectionRetryCount ten minste 1 is.

#### <a name="-psconnectionuri-systemuri"></a>-PSConnectionURI \<System.Uri\>

Hiermee geeft u een URI (Uniform Resource Identifier) op waarmee het verbindings eindpunt voor de werk stroom op de doel computer wordt gedefinieerd. De URI moet volledig gekwalificeerd zijn.

De indeling van deze teken reeks is als volgt:

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

De standaardwaarde is `http://localhost:5985/WSMAN`.

Als u geen opgeeft `PSConnectionURI` , kunt u de `PSUseSSL` `PSComputerName` `PSPort` para meters,, en gebruiken `PSApplicationName` om de waarden op te geven `PSConnectionURI` .

Geldige waarden voor het transport segment van de URI zijn **http** en **https**.
Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Windows Power shell wilt gebruiken, geeft u poort 5985 op voor HTTP of 5986 voor HTTPS.

#### <a name="-pscredential-pscredential"></a>-PSCredential \<PSCredential\>

Hiermee geeft u een gebruikers account op dat gemachtigd is om een werk stroom op de doel computer uit te voeren. Standaard is dit de huidige gebruiker. Deze para meter is alleen geldig als de para meter PSComputerName is opgenomen in de opdracht.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een variabele in die een `PSCredential` object bevat, bijvoorbeeld een waarde die door `Get-Credential` de cmdlet wordt geretourneerd. Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.

#### <a name="-pselapsedtimeoutsec-uint32"></a>-PSElapsedTimeoutSec \<UInt32\>

Hiermee wordt bepaald hoe lang de werk stroom en alle gerelateerde resources in het systeem worden onderhouden. Wanneer de time-out is verlopen, wordt de werk stroom verwijderd, zelfs als deze nog wordt verwerkt. Voer een waarde in tussen 10 en 4.294.967.295. De standaard waarde, 0 (nul), betekent dat er geen verstreken time-out is.

#### <a name="-psparametercollection-hashtable"></a>-PSParameterCollection \<Hashtable[]\>

Geeft verschillende algemene parameter waarden van werk stromen voor verschillende doel computers.

Voer een door komma's gescheiden lijst van hash-tabellen in met één hash-tabel voor elke doel computer. In elke hash-tabel is de eerste sleutel `PSComputerName` en de bijbehorende waarde is de naam van de doel computer. Joker tekens zijn toegestaan in de naam van de computer. Voor de resterende sleutels in de hash-tabel is de sleutel de parameter naam en de waarde de waarde van de para meter.

Bijvoorbeeld:

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

In het bovenstaande voor beeld hebben alle verbindingen een standaard-PSElapsedTimeoutSec van 20 seconden, met uitzonde ring van Server01, waarbij de standaard waarde wordt overschreven door een eigen time-out van 10 seconden op te geven.

#### <a name="-pspersist-boolean"></a>-PSPersist \<Boolean\>

Voegt controle punten toe aan de werk stroom, naast de controle punten die in de werk stroom zijn opgegeven.

Met deze para meter kunnen de controle punten in een werk stroom, zoals die zijn opgegeven met behulp van de `PSPersist` algemene activiteit para meter, de `Checkpoint-Workflow` activiteit of de variabele, niet worden onderdrukt `$PSPersistPreference` .

Een ' controle punt ' of ' persistentie punt ' is een moment opname van de werk stroom status en gegevens die zijn vastgelegd terwijl de werk stroom wordt uitgevoerd en wordt opgeslagen in een opslag voor persistentie op de schijf of in een SQL database. De Windows Power shell-werk stroom gebruikt de opgeslagen gegevens om een onderbroken of onderbroken werk stroom te hervatten vanaf het laatste persistentie punt, in plaats van de werk stroom opnieuw te starten.

Geldige waarden:

- ( *Standaard* ) Als u deze para meter weglaat, wordt aan het begin en einde van de werk stroom een controle punt toegevoegd, naast de controle punten die in de werk stroom zijn opgegeven.

- `$True`. Voegt een controle punt toe aan het begin en het einde van de werk stroom en een controle punt na elke activiteit, naast de controle punten die in de werk stroom zijn opgegeven.

- `$False`. Er zijn geen controle punten toegevoegd. Controle punten worden alleen genomen wanneer deze zijn opgegeven in de werk stroom.

#### <a name="-psport-int32"></a>-PSPort \<Int32\>

Hiermee geeft u de netwerk poort op de doel computers. De standaard poorten zijn 5985 (de WinRM-poort voor HTTP) en 5986 (de WinRM-poort voor HTTPS).

Gebruik de para meter PSPort alleen als dat nodig is. De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers. Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.

#### <a name="-psprivatemetadata-hashtable"></a>-PSPrivateMetadata \<Hashtable\>

Voorziet in aangepaste informatie over werk stroom taken. Voer een hash-tabel in. De sleutels en waarden worden aangepast voor elke werk stroom. Zie het Help-onderwerp voor de werk stroom voor meer informatie over de persoonlijke meta gegevens van een werk stroom.

Deze para meter wordt niet verwerkt door de werk stroom-engine van Windows Power shell.
In plaats daarvan geeft de engine de hash-tabel rechtstreeks door aan de werk stroom.

#### <a name="-psrunningtimeoutsec-uint32"></a>-PSRunningTimeoutSec \<UInt32\>

Hiermee geeft u de uitvoerings tijd van de werk stroom in seconden op, met uitzonde ring van elke keer dat de werk stroom wordt onderbroken. Als de uitvoering van de werk stroom niet is voltooid wanneer de tijd is verstreken, stopt de Windows Power shell workflow engine de uitvoering van de werk stroom.

#### <a name="-pssessionoption-pssessionoption"></a>-PSSessionOption \<PSSessionOption\>

Hiermee stelt u geavanceerde opties in voor de sessies op de doel computers. Voer een `PSSessionOption` object in, zoals een, dat u maakt met behulp van de- `New-PSSessionOption` cmdlet.

De standaard waarden voor de sessie opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders gebruikt de sessie de waarden die zijn opgegeven in de sessie configuratie.

Voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden, raadpleegt u het Help-onderwerp voor de `New-PSSessionOption` cmdlet (. /.. /Microsoft.PowerShell.Core/New-PSSessionOption.md). Zie about_Preference_Variables voor meer informatie over de `$PSSessionOption` voorkeurs [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)variabele.

#### <a name="-psusessl-switchparameter"></a>-PSUseSSL \<SwitchParameter\>

Maakt gebruik van het Secure Sockets Layer (SSL)-protocol om verbinding te maken met de doel computer. Standaard wordt SSL niet gebruikt.

WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden. UseSSL is een extra bescherming waarmee de gegevens worden verzonden via een HTTPS in plaats van HTTP. Als u deze para meter gebruikt maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

## <a name="see-also"></a>ZIE OOK

- [about_ActivityCommonParameters](about_ActivityCommonParameters.md)
- [about_Workflows](about_Workflows.md)
- [Invoke-AsWorkflow](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [New-New psworkflowexecutionoption](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [New-PSWorkflowSession](xref:PSWorkflow.New-PSWorkflowSession)
