---
description: Hierin worden de para meters beschreven die met Windows Power shell workflow worden toegevoegd aan activiteiten.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: 93fdcdb9c5afe0b73e843baf2474ec7d3f96a6cf
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387801"
---
# <a name="about-activitycommonparameters"></a>Over ActivityCommonParameters

## <a name="short-description"></a>KORTE BESCHRIJVING

Hierin worden de para meters beschreven die met Windows Power shell workflow worden toegevoegd aan activiteiten.

## <a name="long-description"></a>LANGE BESCHRIJVING

De Windows Power shell-werk stroom voegt de algemene para meters voor de activiteit toe aan activiteiten die zijn afgeleid van de basis klasse PSActivity. Deze categorie bevat de InlineScript-activiteit en Windows Power shell-cmdlets die worden geïmplementeerd als activiteiten, zoals Get-Process en Get-Wine vent.

De algemene para meters voor de activiteit zijn niet geldig voor de Suspend-Workflow en Checkpoint-Workflow activiteiten en ze worden niet toegevoegd aan cmdlets of expressies die automatisch worden uitgevoerd in een InlineScript-script blok of vergelijk bare activiteit. De algemene para meters voor de activiteit zijn beschikbaar voor de activiteit InlineScript, maar niet voor opdrachten in het InlineScript-script blok.

Verschillende algemene para meters voor de activiteit zijn ook algemene werk stroom parameters of Windows Power shell common para meters. De algemene para meters voor andere activiteiten zijn uniek voor activiteiten.

Zie about_WorkflowCommonParameters voor meer informatie over de algemene werk stroom parameters. Zie about_CommonParameters voor meer informatie over de algemene para meters van Windows Power shell.

### <a name="list-of-activity-common-parameters"></a>LIJST MET ALGEMENE PARA METERS VOOR ACTIVITEIT

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a>PARAMETER BESCHRIJVINGEN

In deze sectie worden de algemene para meters voor de activiteit beschreven.

#### <a name="appendoutput-boolean"></a>AppendOutput \<Boolean\>

De waarde van de `$True` uitvoer van de activiteit wordt toegevoegd aan de waarde van de variabele.
De waarde van `$False` heeft geen effect. Als u een waarde aan een variabele toewijst, wordt de waarde van de variabele standaard vervangen.

Met de volgende opdrachten wordt bijvoorbeeld een proces object toegevoegd aan het Service object in de `$x` variabele.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

Deze para meter is bedoeld voor op XAML gebaseerde werk stromen. In script werk stromen kunt u ook de operator + = toewijzen gebruiken om uitvoer toe te voegen aan de waarde van een variabele, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a>Fout opsporing \<SwitchParameter\>

Geeft details op programmeer niveau weer over de bewerking die door de opdracht wordt uitgevoerd.
De para meter debug overschrijft de waarde van de variabele $DebugPreference voor de huidige opdracht. Deze para meter werkt alleen als de opdracht fout opsporingsgegevens genereert. Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.

#### <a name="displayname-string"></a>DisplayName \<String\>

Hiermee geeft u een beschrijvende naam op voor de activiteit. De waarde DisplayName wordt weer gegeven in de voortgangs balk terwijl de werk stroom wordt uitgevoerd en in de waarde van de eigenschap Progress van de werk stroom taak. Wanneer de para meter PSProgressMessage ook is opgenomen in de opdracht, wordt de inhoud van de voortgangs balk weer gegeven in \<DisplayName\> : \<PSProgressMessage\> Format.

#### <a name="erroraction-actionpreference"></a>Error Action \<ActionPreference\>

Hiermee wordt bepaald hoe de activiteit reageert op een niet-afsluit fout van de opdracht. Dit heeft geen invloed op beëindigings fouten. Deze para meter werkt alleen als de opdracht een niet-afsluit fout genereert, zoals die van de Write-Error-cmdlet. De para meter error Action overschrijft de waarde van de variabele $ErrorActionPreference voor de huidige opdracht. Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.

Geldige waarden:

- Doen. Hiermee wordt het fout bericht weer gegeven en wordt de opdracht verder uitgevoerd. ' Door gaan ' is de standaard waarde.

- Negeren. Onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.
  In tegens telling tot SilentlyContinue, voegt negeren het fout bericht niet toe aan de automatische variabele $Error. De waarde ignore is geïntroduceerd in Windows Power Shell 3,0.

- Inquire. Hiermee wordt het fout bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering. Deze waarde wordt zelden gebruikt.

- Tot. Onderbreekt automatisch een werk stroom taak zodat deze verder kan worden onderzocht. Na onderzoek kan de werk stroom worden hervat.

- SilentlyContinue. Onderdrukt het fout bericht en gaat door met het uitvoeren van de opdracht.

- Stoppen. Geeft het fout bericht weer en stopt met het uitvoeren van de opdracht.

#### <a name="input-object"></a>Ingevoerd \<Object[]\>

Hiermee wordt een verzameling objecten verzonden naar een activiteit. Dit is een alternatief voor pijpleiding objecten per keer naar de activiteit.

#### <a name="mergeerrortooutput-boolean"></a>MergeErrorToOutput \<Boolean\>

Een waarde voor `$True` het toevoegen van fouten aan de uitvoer stroom. Een waarde van `$False` is niet van invloed op. Gebruik deze para meter met de parallelle `ForEach -Parallel` sleutel en tref woorden voor het verzamelen van fouten en uitvoer van meerdere parallelle opdrachten in één verzameling.

#### <a name="psactionretrycount-int32"></a>PSActionRetryCount \<Int32\>

Herhaalde pogingen om de activiteit uit te voeren als de eerste poging mislukt. De standaard waarde, 0, probeert niet.

#### <a name="psactionretryintervalsec-int32"></a>PSActionRetryIntervalSec \<Int32\>

Bepaalt het interval tussen nieuwe pogingen in seconden. De standaard waarde, 0, probeert de actie onmiddellijk opnieuw uit te proberen. Deze para meter is alleen geldig als de para meter PSActionRetryCount ook in de opdracht wordt gebruikt.

#### <a name="psactionrunningtimeoutsec-int32"></a>PSActionRunningTimeoutSec \<Int32\>

Hiermee wordt bepaald hoe lang de activiteit op elke doel computer kan worden uitgevoerd. Als de activiteit niet wordt voltooid voordat de time-out is verlopen, genereert de Windows Power shell-werk stroom een afsluit fout en stopt de verwerking van de werk stroom op de betrokken doel computer.

#### <a name="psallowredirection-boolean"></a>PSAllowRedirection \<Boolean\>

Met de waarde $True kan de verbinding met de doel computers worden omgeleid.
Een waarde van $False heeft geen effect. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Wanneer u de para meter PSConnectionURI gebruikt, kan de externe bestemming een instructie retour neren die wordt omgeleid naar een andere URI. Standaard worden verbindingen niet door Windows Power shell omgeleid, maar u kunt de para meter PSAllowRedirection gebruiken met de waarde $True om omleiding van de verbinding met de doel computer toe te staan.

U kunt ook het aantal keren beperken dat de verbinding wordt omgeleid door de eigenschap MaximumConnectionRedirectionCount van de `$PSSessionOption` Voorkeurs variabele in te stellen of de eigenschap MaximumConnectionRedirectionCount van de waarde van de SSessionOption para meter van cmdlets waarmee een sessie wordt gemaakt. De standaard waarde is 5.

#### <a name="psapplicationname-string"></a>PSApplicationName \<String\>

Hiermee geeft u het segment van de toepassings naam op van de verbindings-URI die wordt gebruikt om verbinding te maken met de doel computers. Gebruik deze para meter om de naam van de toepassing op te geven wanneer u de para meter ConnectionURI niet gebruikt in de opdracht. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

De standaard waarde is de waarde van de `$PSSessionApplicationName` Voorkeurs variabele op de doel computer. Als deze voorkeurs variabele niet is gedefinieerd, is de standaard waarde WSMAN. Deze waarde is geschikt voor de meeste toepassingen. Zie [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie.

De WinRM-service gebruikt de naam van de toepassing om een listener te selecteren om de verbindings aanvraag te onderhouden. De waarde van deze para meter moet overeenkomen met de waarde van de eigenschap URLPrefix van een listener op de externe computer.

#### <a name="psauthentication-authenticationmechanism"></a>PSAuthentication \<AuthenticationMechanism\>

Hiermee geeft u het mechanisme op dat wordt gebruikt om de referenties van de gebruiker te verifiëren wanneer er verbinding wordt gemaakt met de doel computers. Geldige waarden zijn default, Basic, CredSSP, Digest, Kerberos, Negotiate en NegotiateWithImplicitCredential. De standaard waarde is standaard. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Voor informatie over de waarden van deze para meter, zie de beschrijving van de inventarisatie **System. Management. Automation. Runspaces. AuthenticationMechanism** in de Power shell-SDK.

> [!WARNING]
> CredSSP-verificatie (Credential Security service provider), waarbij de referenties van de gebruiker worden door gegeven aan een externe computer die moet worden geverifieerd, is ontworpen voor opdrachten waarvoor verificatie is vereist voor meer dan één bron, zoals het openen van een externe netwerk share. Dit mechanisme verhoogt het beveiligings risico van de externe bewerking. Als er is geknoeid met de externe computer, kunnen de referenties die aan worden door gegeven, worden gebruikt om de netwerk sessie te beheren.

#### <a name="pscertificatethumbprint-string"></a>PSCertificateThumbprint \<String\>

Hiermee geeft u het digitale open bare-sleutel certificaat (x509) op van een gebruikers account dat is gemachtigd om deze actie uit te voeren. Voer de vinger afdruk van het certificaat in. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts. ze werken niet met domein accounts.

Als u een certificaat wilt ophalen, gebruikt u de cmdlets [Get-item](xref:Microsoft.PowerShell.Management.Get-Item) of [Get-Child item](xref:Microsoft.PowerShell.Management.Get-ChildItem) in het Windows Power shell-certificaat: station.

#### <a name="pscomputername-string"></a>PSComputerName \<String[]\>

Hiermee geeft u de doel computers op waarop de activiteit wordt uitgevoerd. Standaard is dit de lokale computer. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Typ de NETBIOS-naam, het IP-adres of de FQDN-naam (Fully Qualified Domain Name) van een of meer computers in een door komma's gescheiden lijst. Typ de computer naam, ' localhost ' of een punt (.) om de lokale computer op te geven.

Als u de lokale computer in de waarde van de para meter PSComputerName wilt toevoegen, opent u Windows Power shell met de optie als administrator uitvoeren.

Als deze para meter wordt wegge laten uit de opdracht, of als de waarde $null of een lege teken reeks is, is het werk stroom doel de lokale computer en wordt Windows Power shell Remoting niet gebruikt om de opdracht uit te voeren.

Als u een IP-adres wilt gebruiken in de waarde van de para meter ComputerName, moet de opdracht de para meter PSCredential bevatten. De computer moet ook worden geconfigureerd voor HTTPS-Trans Port of het IP-adres van de externe computer moet worden opgenomen in de WinRM TrustedHosts-lijst op de lokale computer. Zie "een computer toevoegen aan de lijst met vertrouwde hosts" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)voor instructies voor het toevoegen van een computer naam aan de lijst TrustedHosts.

#### <a name="psconfigurationname-string"></a>PSConfigurationName \<String\>

Hiermee geeft u de sessie configuraties op die worden gebruikt voor het maken van sessies op de doel computers. Voer de naam in van een sessie configuratie op de doel computers (niet op de computer waarop de werk stroom wordt uitgevoerd). De standaard instelling is micro soft. Power shell. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

#### <a name="psconnectionretrycount-uint"></a>PSConnectionRetryCount \<UInt\>

Hiermee geeft u het maximum aantal pogingen op om verbinding te maken met elke doel computer als de eerste verbindings poging mislukt. Voer een getal tussen 1 en 4.294.967.295 (UInt. MaxValue) in. De standaard waarde, nul (0), vertegenwoordigt geen nieuwe pogingen.
Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

#### <a name="psconnectionretryintervalsec-uint"></a>PSConnectionRetryIntervalSec \<UInt\>

Hiermee geeft u de vertraging tussen nieuwe pogingen in seconden op. De standaardwaarde is nul (0). Deze para meter is alleen geldig wanneer de waarde van PSConnectionRetryCount ten minste 1 is. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

#### <a name="psconnectionuri-systemuri"></a>PSConnectionURI \<System.Uri\>

Hiermee geeft u een URI (Uniform Resource Identifier) op waarmee het verbindings eindpunt voor de activiteit op de doel computer wordt gedefinieerd. De URI moet volledig gekwalificeerd zijn. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

De indeling van deze teken reeks is als volgt:

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

De standaardwaarde is `http://localhost:5985/WSMAN`.

Als u geen PSConnectionURI opgeeft, kunt u de para meters PSUseSSL, PSComputerName, PSPort en PSApplicationName gebruiken om de PSConnectionURI waarden op te geven.

Geldige waarden voor het transport segment van de URI zijn HTTP en HTTPS. Als u een verbindings-URI met een transport segment opgeeft, maar geen poort opgeeft, wordt de sessie gemaakt met standaard poorten: 80 voor HTTP en 443 voor HTTPS. Als u de standaard poorten voor externe communicatie van Windows Power shell wilt gebruiken, geeft u poort 5985 op voor HTTP of 5986 voor HTTPS.

#### <a name="pscredential-pscredential"></a>PSCredential \<PSCredential\>

Hiermee geeft u een gebruikers account op dat gemachtigd is om de activiteit op de doel computer uit te voeren. Standaard is dit de huidige gebruiker. Deze para meter is alleen geldig als de para meter PSComputerName is opgenomen in de opdracht. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Typ een gebruikers naam, zoals "gebruiker01" of "Domain01\User01", of voer een variabele in die een PSCredential-object bevat, zoals een item dat door de Get-Credential-cmdlet wordt geretourneerd. Als u alleen een gebruikers naam opgeeft, wordt u gevraagd een wacht woord op te geven.

#### <a name="psdebug-psdatacollectiondebugrecord"></a>PSDebug \<PSDataCollection[DebugRecord]\>

Hiermee worden fout opsporingsgegevens van de activiteit toegevoegd aan de opgegeven verzameling record voor fout opsporing, in plaats van het schrijven van fout berichten naar de console of naar de waarde van de eigenschap debug van de werk stroom taak. U kunt fout opsporingsgegevens van meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor fout opsporing.

Als u deze algemene activiteit wilt gebruiken, gebruikt u de cmdlet New-Object om een PSDataCollection-object met een type DebugRecord te maken en het object in een variabele op te slaan. Gebruik vervolgens de variabele als de waarde van de para meter PSDebug van een of meer activiteiten, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a>PSDisableSerialization \<Boolean\>

Stuurt de activiteit om live-objecten (niet geserialiseerd) naar de werk stroom te retour neren.
De resulterende objecten hebben methoden, evenals eigenschappen, maar ze kunnen niet worden opgeslagen wanneer een controle punt wordt gemaakt.

#### <a name="psdisableserializationpreference-boolean"></a>PSDisableSerializationPreference \<Boolean\>

Hiermee wordt het equivalent van de para meter PSDisableSerialization toegepast op de hele werk stroom, niet alleen de activiteit. Het toevoegen van deze para meter wordt over het algemeen niet aanbevolen, omdat een werk stroom die de objecten niet serialiseren, niet kan worden hervat of niet kan worden bewaard.

Geldige waarden:

- Prijs Als u dit weglaat, en u de para meter PSDisableSerialization ook niet hebt toegevoegd aan een activiteit, worden de objecten geserialiseerd.

- `$True`. Stuurt alle activiteiten in een werk stroom om objecten met ' live ' (geen serieel) te retour neren. De resulterende objecten hebben methoden, evenals eigenschappen, maar ze kunnen niet worden opgeslagen wanneer een controle punt wordt gemaakt.
- `$False`. Werk stroom objecten worden geserialiseerd.

#### <a name="pserror-psdatacollectionerrorrecord"></a>PSError \<PSDataCollection[ErrorRecord]\>

Voegt fout berichten van de activiteit toe aan de opgegeven verzameling van fouten records, in plaats van de fout berichten naar de console of naar de waarde van de eigenschap Error van de werk stroom taak te schrijven. U kunt fout berichten van meerdere activiteiten toevoegen aan hetzelfde verzamelings object van de fout record.

Als u deze algemene activiteit wilt gebruiken, gebruikt u de `New-Object` cmdlet om een PSDataCollection-object te maken met het type ErrorRecord en slaat u het object op in een variabele. Gebruik vervolgens de variabele als de waarde van de para meter PSError van een of meer activiteiten, zoals wordt weer gegeven in het volgende voor beeld.

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a>PSPersist \<Boolean\>

Neemt een controle punt na de activiteit. Dit controle punt is een aanvulling op de controle punten die in de werk stroom zijn opgegeven. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Een ' controle punt ' of ' persistentie punt ' is een moment opname van de werk stroom status en gegevens die zijn vastgelegd terwijl de werk stroom wordt uitgevoerd en wordt opgeslagen in een opslag voor persistentie op schijf. De Windows Power shell-werk stroom gebruikt de opgeslagen gegevens om een onderbroken of onderbroken werk stroom te hervatten vanaf het laatste persistentie punt, in plaats van de werk stroom opnieuw te starten.

Geldige waarden:

- Prijs Als u deze para meter weglaat, worden er geen controle punten toegevoegd. Controle punten worden gemaakt op basis van de instellingen voor de werk stroom.

- `$True`. Neemt een controle punt nadat de activiteit is voltooid.
  Dit controle punt is een aanvulling op de controle punten die in de werk stroom zijn opgegeven.

- `$False`. Er zijn geen controle punten toegevoegd. Controle punten worden alleen genomen wanneer deze zijn opgegeven in de werk stroom.

#### <a name="psport-int32"></a>PSPort \<Int32\>

Hiermee geeft u de netwerk poort op de doel computers. De standaard poorten zijn 5985 (de WinRM-poort voor HTTP) en 5986 (de WinRM-poort voor HTTPS). Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

Gebruik de para meter PSPort alleen als dat nodig is. De poort die in de opdracht is ingesteld, is van toepassing op alle computers of sessies waarop de opdracht wordt uitgevoerd. Een alternatieve poort instelling kan verhinderen dat de opdracht wordt uitgevoerd op alle computers. Voordat u een andere poort gebruikt, moet u de WinRM-listener op de externe computer configureren om op die poort te Luis teren.

#### <a name="psprogress-psdatacollectionprogressrecord"></a>PSProgress \<PSDataCollection[ProgressRecord]\>

Hiermee worden voortgangs berichten van de activiteit toegevoegd aan de opgegeven verzameling van voortgangs records, in plaats van de voortgangs berichten naar de console of naar de waarde van de eigenschap Progress van de werk stroom taak te schrijven. U kunt voortgangs berichten uit meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor voortgangs records.

#### <a name="psprogressmessage-string"></a>PSProgressMessage \<String\>

Hiermee geeft u een beschrijvende beschrijving van de activiteit. De waarde PSProgressMessage wordt weer gegeven in de voortgangs balk terwijl de werk stroom wordt uitgevoerd. Wanneer de DisplayName ook is opgenomen in de opdracht, wordt de inhoud van de voortgangs balk weer gegeven in \<DisplayName\> : \<PSProgressMessage\> Format.

Deze para meter is met name handig voor het identificeren van activiteiten in een ForEach-parallel-script blok. Zonder dit bericht worden activiteiten in alle parallelle vertakkingen aangeduid met dezelfde naam.

#### <a name="psremotingbehavior-remotingbehavior"></a>PSRemotingBehavior \<RemotingBehavior\>

Hiermee geeft u op hoe externe toegang wordt beheerd wanneer de activiteit wordt uitgevoerd op de doel computers.
Power shell is de standaard instelling.

Geldige waarden zijn:

- Geen: de activiteit wordt niet uitgevoerd op externe computers.

- Power shell: externe toegang van Windows Power shell wordt gebruikt om de activiteit uit te voeren op doel computers.

- Aangepast: de activiteit ondersteunt een eigen type externe communicatie. Deze waarde is geldig wanneer de cmdlet die wordt geïmplementeerd als activiteit, de waarde van het kenmerk RemotingCapability instelt op SupportedByCommand en de opdracht de para meter ComputerName bevat.

#### <a name="psrequiredmodules-string"></a>PSRequiredModules \<String[]\>

Hiermee worden de opgegeven modules geïmporteerd voordat de opdracht wordt uitgevoerd. Voer de module namen in. De modules moeten worden geïnstalleerd op de doel computer.

Modules die zijn geïnstalleerd in een pad dat is opgegeven in de omgevings variabele PSModulePath, worden automatisch geïmporteerd bij het eerste gebruik van een opdracht in de module.
Gebruik deze para meter om modules te importeren die zich niet in een PSModulePath-locatie bevinden.

Omdat elke activiteit in een werk stroom wordt uitgevoerd in een eigen sessie, wordt met een Import-Module-opdracht een module alleen geïmporteerd in de sessie waarin deze wordt uitgevoerd. De module wordt niet geïmporteerd in sessies waarin andere activiteiten worden uitgevoerd.

#### <a name="pssessionoption-pssessionoption"></a>PSSessionOption \<PSSessionOption\>

Hiermee stelt u geavanceerde opties in voor de sessies op de doel computers. Voer een PSSessionOption-object in, zoals een, dat u maakt met behulp van de cmdlet New-PSSessionOption. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

De standaard waarden voor de sessie opties worden bepaald door de waarde van de `$PSSessionOption` Voorkeurs variabele, als deze is ingesteld. Anders gebruikt de sessie de waarden die zijn opgegeven in de sessie configuratie.

Zie het Help-onderwerp voor de New-PSSessionOption [-cmdlet New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)voor een beschrijving van de sessie opties, met inbegrip van de standaard waarden.

Zie [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)voor meer informatie over de $PSSessionOption voorkeurs variabele.

#### <a name="psusessl-boolean"></a>PSUseSSL \<Boolean\>

Een waarde van $True maakt gebruik van het Secure Sockets Layer (SSL)-protocol om verbinding te maken met de doel computer. Standaard wordt SSL niet gebruikt. Een waarde van $False heeft geen effect. Deze algemene activiteit para meter is ook een algemene werk stroom parameter.

WS-Management versleutelt alle Windows Power shell-inhoud die via het netwerk wordt verzonden. UseSSL is een extra bescherming waarmee de gegevens worden verzonden via een HTTPS in plaats van HTTP. Als u deze para meter gebruikt maar SSL is niet beschikbaar op de poort die wordt gebruikt voor de opdracht, mislukt de opdracht.

#### <a name="psverbose-psdatacollectionverboserecord"></a>PSVerbose \<PSDataCollection[VerboseRecord]\>

Hiermee worden uitgebreide berichten van de activiteit toegevoegd aan de opgegeven verzameling uitgebreide records, in plaats van de uitgebreide berichten naar de console of naar de waarde van de eigenschap uitgebreid van de werk stroom taak te schrijven. U kunt uitgebreide berichten van meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor uitgebreide records.

#### <a name="pswarning-psdatacollectionwarningrecord"></a>PSWarning \<PSDataCollection[WarningRecord]\>

Hiermee worden waarschuwings berichten van de activiteit toegevoegd aan de opgegeven verzameling waarschuwings records, in plaats van de waarschuwings berichten naar de console of naar de waarde van de eigenschap Warning van de werk stroom taak te schrijven. U kunt waarschuwings berichten van meerdere activiteiten toevoegen aan hetzelfde verzamelings object voor waarschuwings records.

#### <a name="result"></a>Resultaat

Deze para meter is alleen geldig in XAML-werk stromen.

#### <a name="usedefaultinput-boolean"></a>UseDefaultInput \<Boolean\>

Hiermee wordt alle invoer van de werk stroom geaccepteerd als invoer voor de activiteit op waarde.

De Get-Process-activiteit in de volgende voorbeeld werk stroom maakt bijvoorbeeld gebruik van de algemene para meter UseDefaultInput voor het ophalen van invoer die wordt door gegeven aan de werk stroom. Wanneer u de werk stroom met invoer uitvoert, wordt die invoer gebruikt door de activiteit.

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a>Uitgebreide \<SwitchParameter\>

Geeft gedetailleerde informatie weer over de bewerking die door de opdracht wordt uitgevoerd.
Deze informatie komt overeen met de informatie in een tracering of in een transactie logboek.
De para meter uitgebreid overschrijft de waarde van de variabele $VerbosePreference voor de huidige opdracht. Deze para meter werkt alleen als de opdracht een uitgebreid bericht genereert. Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.

#### <a name="warningaction-actionpreference"></a>WarningAction \<ActionPreference\>

Hiermee wordt bepaald hoe de activiteit reageert op een waarschuwing. ' Door gaan ' is de standaard waarde. De para meter WarningAction overschrijft de waarde van de variabele $WarningPreference voor de huidige opdracht. Deze para meter werkt alleen als er een waarschuwings bericht wordt gegenereerd door de opdracht. Deze para meter is ook een gemeen schappelijke Windows Power shell-para meter.

Geldige waarden:

- SilentlyContinue. Onderdrukt het waarschuwings bericht en gaat door met het uitvoeren van de opdracht.

- Doen. Geeft het waarschuwings bericht weer en voert de opdracht verder uit.
  ' Door gaan ' is de standaard waarde.

- Inquire. Hiermee wordt het waarschuwings bericht weer gegeven en wordt u gevraagd om bevestiging voordat u doorgaat met de uitvoering. Deze waarde wordt zelden gebruikt.

- Stoppen. Geeft het waarschuwings bericht weer en stopt met het uitvoeren van de opdracht.

> [!NOTE]
> De para meter WarningAction overschrijft de waarde van de $WarningAction voorkeurs variabele niet wanneer de para meter wordt gebruikt in een opdracht voor het uitvoeren van een script of functie.

### <a name="examples"></a>VOORBEELDEN

De algemene para meters voor de activiteit zijn erg nuttig. U kunt bijvoorbeeld de para meter PSComputerName gebruiken om bepaalde activiteiten uit te voeren op slechts een subset van de doel computers.

U kunt ook de para meters PSConnectionRetryCount en PSConnectionRetryIntervalSec gebruiken om de waarden voor nieuwe pogingen voor bepaalde activiteiten aan te passen.

In het volgende voor beeld ziet u hoe u de algemene para meters voor de activiteit PSComputerName gebruikt om een Get-EventLog-activiteit alleen uit te voeren op computers die een bepaald domein.

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a>ZIE OOK

[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)
