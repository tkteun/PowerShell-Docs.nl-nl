---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Wat is er nieuw in Windows Power shell 5,0
ms.openlocfilehash: dba016546fe034684f6b7afe43ec2e7a1b793d96
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810580"
---
# <a name="whats-new-in-windows-powershell-50"></a>Wat is er nieuw in Windows Power shell 5,0

Windows Power shell 5,0 bevat belang rijke nieuwe functies die het gebruik ervan uitbreiden, de bruikbaarheid verbeteren en u in staat stellen om op Windows gebaseerde omgevingen eenvoudiger en uitgebreid te beheren.

Windows Power shell 5,0 is achterwaarts compatibel. Cmdlets, providers, modules, invoeg toepassingen, scripts, functies en profielen die zijn ontworpen voor Windows Power Shell 4,0, Windows Power Shell 3,0 en Windows Power Shell 2,0, werken doorgaans in Windows Power shell 5,0 zonder wijzigingen.

## <a name="installing-windows-powershell"></a>Windows PowerShell installeren

Windows Power shell 5,0 wordt standaard geïnstalleerd in Windows Server 2016 Technical Preview en Windows
10.

Als u Windows Power shell 5,0 wilt installeren op Windows Server 2012 R2, Windows 8,1 ENTER prise of Windows 8,1 Pro, downloadt en installeert u [Windows Management Framework 5,0](https://aka.ms/wmf5download). Lees de Download gegevens en zorg ervoor dat aan alle systeem vereisten wordt voldaan voordat u Windows Management Framework 5,0 installeert.

## <a name="in-this-topic"></a>In dit onderwerp

- [Windows Power Shell 4,0 DSC-updates in KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nieuwe functies in Windows Power shell 5,0](#new-features-in-windows-powershell-50)
- [Nieuwe functies in Windows Power Shell 4,0](#new-features-in-windows-powershell-40)
- [Nieuwe functies in Windows Power Shell 3,0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Windows Power Shell 4,0-updates in november 2014 update pakket (KB 3000850)

Veel updates en verbeteringen in Windows Power shell desired state Configuration (DSC) in Windows Power Shell 4,0 zijn beschikbaar in het [Update pakket van November 2014 voor Windows RT 8,1, Windows 8,1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850). U kunt bepalen of KB 3000850 op uw systeem is geïnstalleerd door `Get-Hotfix -Id KB3000850` in Windows Power shell uit te voeren.

- Updates voor bestaande cmdlets in de [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) -module
  - [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration) is sneller (vooral in ISE).
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) heeft een nieuwe para meter,-UseExisting, waarmee de laatst toegepaste configuratie opnieuw wordt toegepast.
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) -Force is opgelost.
  - [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration) toont meer nuttige informatie over de status van de engine.
  - [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) retourneert nu de computer naam samen met waar of onwaar.
  - [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration) ondersteunt nu UNC-paden.

- Nieuwe cmdlets in de [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) -module
  - [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration): voert een controle op de pull-server op aanvraag uit.
  - [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration): Hiermee wordt een configuratie gestopt die al wordt uitgevoerd.
  - [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument): Hiermee kunt u configuratie documenten in verschillende fasen verwijderen (in behandeling, eerder of actueel).

- Taal verbeteringen
  - DependsOn biedt nu ondersteuning voor samengestelde resources.
  - DependsOn ondersteunt nu nummers in namen van bron exemplaren.
  - Knooppunt expressies waarmee wordt geëvalueerd dat er geen fouten meer worden gegenereerd.
  - Er is een fout opgetreden die optreedt als een knooppunt expressie resulteert in empty.
  - Configuraties die configuraties aanroepen, werken nu in de Windows Power shell-console.

- Verbeteringen in de pull-modus
  - Pull-modus ondersteunt nu alle ZIP-bestanden.
  - **AllowModuleOverwrite** werkt nu goed.

- Verbeteringen in tolerantie
  - Met nieuwe **DebugMode** kunt u resource modules opnieuw laden.
  - Als er een configuratie fout optreedt, wordt het bestand Pending. MOF niet verwijderd.
  - De lokale Configuration Manager (LCM) is nu flexibeler wanneer de instellingen voor de configuratie van de mailinstis zijn beschadigd.

- Diagnostische verbeteringen
  - Er wordt een waarschuwing weer gegeven wanneer de LCM de timer instelt op andere instellingen dan u hebt opgegeven.
  - Fouten logboek bestanden bevatten nu de aanroep stack voor Windows Power shell-resources.

- Flexibiliteits verbeteringen
  - De LocalConfigurationManager-resource heeft een nieuwe eigenschap, **ActionAfterReboot**.
    - ContinueConfiguration (standaard waarde): hervat automatisch een configuratie nadat een doel knooppunt opnieuw is opgestart.
    - De stopconfiguration: een configuratie niet automatisch hervatten nadat een knoop punt opnieuw is opgestart.
  - Een consistentie-uitvoering kan nu vaker optreden dan een PULL-bewerking of vice versa.
  - Ondersteuning voor versie beheer: DSC kan nu een document herkennen dat is gegenereerd op een nieuwere client (opgenomen in [WMF 5,0](https://aka.ms/wmf5download)).

- Verbeteringen voor het voor komen van fouten
  - De module versie wordt nu afgedwongen voordat een configuratie wordt toegepast.
  - **DebugPreference** is nu correct ingesteld voor Get-, set-of test-TargetResource-aanroepen.

- Verbeteringen voor het verwerken van referenties
  - Er wordt nu een certificaat gebruikt als zowel **certificaat** -als **PSDscAllowPlainTextPassword** zijn opgegeven.
  - Referenties worden ontsleuteld, zelfs voor Get-TargetResource.
  - De referenties voor de configuratie van de gegevens worden versleuteld en ontsleuteld.
  - PSCredentials worden nu ontsleuteld wanneer ze zich in een Inge sloten object bevinden.

- Verbeteringen van ingebouwde bronnen
  - De pakket resource
    - Installeert niet langer het verkeerde pakket (op basis van lokale of webbronnen).
    - Biedt nu ondersteuning voor HTTPS.
  - Er wordt nu ondersteuning geboden voor HTTPS in de [pakket bron](/powershell/scripting/dsc/reference/resources/windows/packageresource).
  - De [Archief resource](/powershell/scripting/dsc/reference/resources/windows/archiveresource) ondersteunt nu referenties.

## <a name="new-features-in-windows-powershell-50"></a>Nieuwe functies in Windows Power shell 5,0

- [Nieuwe functies in Windows Power shell](#new-features-in-windows-powershell)
- [Nieuwe functies in Windows Power shell desired state Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nieuwe functies in Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nieuwe functies in Windows Power shell-webservices](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Belang rijke oplossingen voor fouten in Windows Power shell 5,0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nieuwe functies in Windows Power shell

- Vanaf Windows Power shell 5,0 kunt u ontwikkelen met behulp van klassen, door gebruik te maken van formele syntaxis en semantiek die vergelijkbaar zijn met andere object georiënteerde programmeer talen. **Klasse**, **Enum**en andere tref woorden zijn toegevoegd aan de Windows Power shell-taal ter ondersteuning van de nieuwe functie.
  Zie about_Classes voor meer informatie over het werken met klassen.

- Windows Power shell 5,0 introduceert een nieuwe, gestructureerde informatie stroom die u kunt gebruiken voor het verzenden van gestructureerde gegevens tussen een script en de aanroepers (of hosting omgeving). U kunt nu write-host gebruiken om uitvoer naar de informatie stroom te verzenden. Informatie stromen werkt ook voor Power shell. streams, taken, geplande taken en werk stromen. De volgende functies ondersteunen de informatie stroom.
  - Een nieuwe cmdlet write-Information waarmee u kunt opgeven hoe Windows Power shell gegevens streams voor een opdracht verwerkt. Write-host is een wrapper voor schrijf informatie. Write-Information is ook een ondersteunde werk stroom activiteit.
  - Met twee nieuwe algemene para meters, InformationVariable en Information Action, kunt u bepalen hoe gegevens stromen van een opdracht worden weer gegeven. Geldige waarden voor Information Action zijn SilentlyContinue, stop, continue, query, ignore of Suspend, waarbij SilentlyContinue de standaard instelling is. InformationVariable geeft een teken reeks als de naam van een variabele waarnaar u de Write-hostgegevens van een opdracht wilt opslaan.
  - Met een nieuwe voorkeurs variabele, InformationPreference, wordt uw standaard voorkeur voor gegevens stroom gegevens in een Windows Power shell-sessie opgegeven. De standaard waarde is SilentlyContinue.
  - Er zijn twee nieuwe algemene werk stroom parameters, PSInformation en Information Action, toegevoegd.
  - Wanneer u de indeling-tabel opdracht gebruikt, worden tabel kolommen nu automatisch opgemaakt door de eerste 300ms te evalueren van gegevens die via de stroom worden door gegeven.

- In samen werking met [micro soft Research](https://research.microsoft.com/)is een nieuwe cmdlet, ConvertFrom teken reeks, toegevoegd. Met de ConvertFrom-teken reeks kunt u gestructureerde objecten uit de inhoud van teken reeksen ophalen en parseren. Zie ConvertFrom-string (Engelstalig) voor meer informatie.
- Met een nieuwe cmdlet Convert-string wordt tekst automatisch opgemaakt op basis van een voor beeld van een para meter die u opgeeft.
- Een nieuwe module, micro soft. Power shell. Archive, bevat cmdlets waarmee u bestanden en mappen kunt comprimeren in archief (ook wel ZIP-bestanden genoemd), bestanden kunt extra heren uit bestaande ZIP-bestanden en ZIP-bestanden bijwerken met nieuwere versies van bestanden die zijn gecomprimeerd.
- Met een nieuwe module, Package Management, kunt u software pakketten op Internet detecteren en installeren.
  De package management-module (voorheen bekend als OneGet) is een manager of multiplexer van bestaande pakket beheerders (ook wel pakket providers genoemd) om Windows-pakket beheer samen te voegen met één Windows Power shell-interface.
- Met een nieuwe module, PowerShellGet, kunt u modules en DSC-resources zoeken, installeren, publiceren en bijwerken op de [PowerShell Gallery](https://www.powershellgallery.com/), of op een interne module opslagplaats die u kunt instellen door de cmdlet REGI ster-PSRepository uit te voeren.
- Er is een nieuw tref woord voor de taal, **verborgen**, toegevoegd om op te geven dat een lid (een eigenschap of methode) niet standaard wordt weer gegeven in de resultaten van de Get-leden (tenzij u de para meter-Force toevoegt).
  Eigenschappen of methoden die zijn gemarkeerd als verborgen, worden ook niet weer gegeven in IntelliSense-resultaten, tenzij u zich in een context bevindt waarin het lid zichtbaar moet zijn. Zo moet bij de automatische variabele $This verborgen leden worden weer gegeven in de methode klasse.
- Nieuwe items, verwijder items en Get-Child item zijn verbeterd ter ondersteuning van het maken en beheren van [symbolische koppelingen](https://en.wikipedia.org/wiki/Symbolic_link). De para meter **-item type** voor nieuw item accepteert een nieuwe waarde, **SymbolicLink**. U kunt nu symbolische koppelingen maken op één lijn door de cmdlet New-item uit te voeren.
- Get-Child item heeft ook een nieuwe depth-para meter, die u met de para meter-recursief gebruikt om de recursie te beperken. Get-Child item-recursief-diepte 2 retourneert bijvoorbeeld resultaten uit de huidige map, alle onderliggende mappen in de huidige map en alle mappen in de onderliggende mappen.
- Met kopie-item kunt u nu bestanden of mappen van de ene Windows Power shell-sessie naar een andere kopiëren, wat betekent dat u bestanden kunt kopiëren naar sessies die zijn verbonden met externe computers (inclusief computers waarop nano server wordt uitgevoerd en dus geen andere interface heeft). Als u bestanden wilt kopiëren, geeft u PSSession-Id's op als de waarde van de para meters New-FromSession en-ToSession, en add-Path en-Destination om respectievelijk het oorspronkelijke pad en de doel locatie op te geven. Kopieer-item-path c: \\ MyFile. txt-ToSession $s-bestemming d: \\ destinationFolder.
- Windows Power shell transcriptie is verbeterd voor alle hosting toepassingen (zoals Windows PowerShell ISE) naast de console-host (**Power shell. exe**). Transcriptie-opties (inclusief het inschakelen van een transcript voor het hele systeem) kunnen worden geconfigureerd door de instelling **Power shell transcriptie** Groepsbeleid in te scha kelen in Beheersjablonen/Windows-onderdelen/Windows Power shell.
- Met een nieuwe uitgebreide functie voor het traceren van scripts kunt u het gebruik van Windows Power shell-scripts op een systeem gedetailleerd bijhouden en analyseren. Nadat u gedetailleerde script tracering hebt ingeschakeld, worden alle script blokken door Windows Power shell geregistreerd in het gebeurtenis logboek van de Event Tracing for Windows (ETW), **micro soft-Windows-Power shell/operationeel**.
- Met ingang van Windows Power shell 5,0 worden nieuwe cmdlets voor cryptografische bericht syntaxis versleuteling en ontsleuteling van inhoud ondersteund door gebruik te maken van de indeling van de IETF-standaard voor het cryptografisch beveiligen van berichten zoals beschreven door [RFC5652](https://tools.ietf.org/html/rfc5652). De cmdlets Get-CmsMessage, Protect-CmsMessage en Unprotect-CmsMessage zijn toegevoegd aan de module [micro soft. Power shell. Security](/powershell/module/Microsoft.PowerShell.Security) .
- Nieuwe cmdlets in de module [micro soft. Power shell. Utility](/powershell/module/Microsoft.PowerShell.Utility) , Get-runs, debug-runs Pace, Get-RunspaceDebug, Enable-RunspaceDebug en Disable-RunspaceDebug, kunt u opties voor fout opsporing op een runs Pace instellen en de fout opsporing op een runs Pace starten en stoppen. Voor wille keurige runspaces (dat wil zeggen runspaces die niet de standaard runs Pace zijn voor een Windows Power shell-console of Windows PowerShell ISE-sessie), kunt u met Windows Power shell onderbrekings punten in een script instellen en onderbrekings punten toevoegen het script stoppen om uit te voeren, totdat u een fout opsporingsprogramma kunt toevoegen om fouten op te sporen in het runs Pace-script. Geneste probleemoplossings ondersteuning voor wille keurige runspaces is toegevoegd aan de Windows Power shell-script debugger voor runspaces.
- Er is een nieuwe indeling-hex-cmdlet toegevoegd aan de module [micro soft. Power shell. Utility](/powershell/module/Microsoft.PowerShell.Utility) .
  Met Format-hex kunt u tekst of binaire gegevens in hexadecimale indeling weer geven.
- Get-klem bord-en set-Klembord-cmdlets zijn toegevoegd aan de module [micro soft. Power shell. Utility](/powershell/module/Microsoft.PowerShell.Utility) ; Ze vereenvoudigen de overdracht van inhoud naar en van een Windows Power shell-sessie. De Klembord-cmdlets ondersteunen installatie kopieën, audio bestanden, bestands lijsten en tekst.
- Er is een nieuwe cmdlet, Clear-RecycleBin, toegevoegd aan de module [micro soft. Power shell. Management.](/powershell/module/Microsoft.PowerShell.Management) met deze cmdlet wordt de Prullenbak leeg gemaakt voor een vast station, dat externe stations bevat. Standaard wordt u gevraagd om een Clear-RecycleBin opdracht te bevestigen, omdat de eigenschap ConfirmImpact van de cmdlet is ingesteld op ConfirmImpact. High.
- Met een nieuwe cmdlet New-TemporaryFile kunt u een tijdelijk bestand maken als onderdeel van het uitvoeren van scripts. Het nieuwe tijdelijke bestand wordt standaard gemaakt in ```C:\Users\<user name>\AppData\Local\Temp``` .
- De cmdlets out-file, add-content en set-content hebben nu een nieuwe para meter-New-nieuwe regel, waarbij een nieuwe lijn na de uitvoer wordt wegge laten.
- De cmdlet New-GUID maakt gebruik van de .NET Framework GUID-klasse voor het genereren van een GUID, handig wanneer u scripts of DSC-resources schrijft.
- Omdat de gegevens van de bestands versie misleidend kunnen zijn, met name nadat een bestand is geïnstalleerd, zijn er nieuwe FileVersionRaw-en ProductVersionRaw-script eigenschappen beschikbaar voor file info-objecten. U kunt bijvoorbeeld de volgende opdracht uitvoeren om de waarden van deze eigenschappen voor Power shell. exe weer te geven, waarbij $pid de proces-ID bevat voor een actieve sessie van Windows Power shell:`Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force`
- Met de nieuwe cmdlets Enter-PSHostProcess en Exit-PSHostProcess kunt u fouten opsporen in Windows Power shell-scripts in processen gescheiden van het huidige proces dat wordt uitgevoerd in de Windows Power shell-console. Voer Enter-PSHostProcess uit om een specifieke proces-ID in te voeren of toe te voegen, en voer Get-runs Pace uit om de actieve runspaces binnen het proces te retour neren. Voer exit-PSHostProcess uit om het proces te ontkoppelen wanneer u klaar bent met het opsporen van fouten in het script in het proces.
- Er is een nieuwe wacht fout-cmdlet toegevoegd aan de module [micro soft. Power shell. Utility](/powershell/module/Microsoft.PowerShell.Utility) . U kunt wacht debugging uitvoeren om een script in het fout opsporingsprogramma te stoppen voordat u de volgende instructie in het script uitvoert.
- Het fout opsporingsprogramma van de Windows Power shell-werk stroom ondersteunt nu het volt ooien van opdrachten of tabbladen en u kunt fouten opsporen in geneste werk stromen U kunt nu op **CTRL + onderbreken** drukken om de fout opsporing in een actief script in te voeren, zowel voor lokale als externe sessies, en in een werk stroom script.
- Er is een cmdlet voor fout opsporing-taak toegevoegd aan de module [micro soft. Power shell. core](/powershell/module/Microsoft.PowerShell.Core) voor fout opsporing bij het uitvoeren van taak scripts voor Windows Power shell-werk stroom, achtergrond en taken die worden uitgevoerd in externe sessies.
- Er is een nieuwe status, AtBreakpoint, toegevoegd voor Windows Power shell-taken. De AtBreakpoint-status is van toepassing wanneer een taak een script uitvoert dat set-onderbrekings punten bevat en het script een onderbrekings punt heeft bereikt. Wanneer een taak wordt gestopt bij een onderbrekings punt voor fout opsporing, moet u fouten opsporen in de taak door de cmdlet debug-job uit te voeren.
- Windows Power shell 5,0 implementeert ondersteuning voor meerdere versies van één Windows Power shell-module in dezelfde map in $PSModulePath. Er is een eigenschap RequiredVersion toegevoegd aan de klasse ModuleSpecification om u te helpen de gewenste versie van een module op te halen. Deze eigenschap is wederzijds exclusief met de eigenschap ModuleVersion. RequiredVersion wordt nu ondersteund als onderdeel van de waarde van de para meter FullyQualifiedName van de cmdlets Get-module, import-module en Remove-module.
- U kunt nu de module versie validatie uitvoeren door de cmdlet test-ModuleManifest uit te voeren.
- Met de resultaten van de cmdlet Get-opdracht wordt nu een versie kolom weer gegeven. Er is een nieuwe versie-eigenschap toegevoegd aan de klasse CommandInfo. Get-opdracht toont opdrachten uit meerdere versies van dezelfde module. De eigenschap Version maakt ook deel uit van afgeleide klassen van CmdletInfo: CmdletInfo en ApplicationInfo.
- Get-Command heeft een nieuwe para meter,-ShowCommandInfo, die ShowCommand-informatie retourneert als PSObjects. Dit is met name handig voor wanneer de weer gave-opdracht wordt uitgevoerd in Windows PowerShell ISE met behulp van externe communicatie met Windows Power shell. De para meter-ShowCommandInfo vervangt de bestaande Get-SerializedCommand-functie in de module micro soft. Power shell. Utility, maar het script Get-SerializedCommand is nog steeds beschikbaar voor de ondersteuning van Down Level scripts.
- Met een nieuwe Get-ItemPropertyValue-cmdlet kunt u de waarde van een eigenschap ophalen zonder punt notatie te gebruiken. In oudere versies van Windows Power shell kunt u bijvoorbeeld de volgende opdracht uitvoeren om de waarde op te halen van de eigenschap Application base van de register sleutel PowerShellEngine: **(Get-item Property-pad HKLM: \\ software \\ micro soft \\ Power shell \\ 3 \\ PowerShellEngine-name Application base). Application base**. Vanuit Windows Power shell 5,0 kunt u **Get-ItemPropertyValue-Path HKLM: \\ software \\ micro soft \\ Power shell \\ 3 \\ PowerShellEngine-name Application base**uitvoeren.
- De Windows Power shell-console gebruikt nu syntaxis kleuren, net als in Windows PowerShell ISE.
- Een nieuwe netwerk switch-module bevat cmdlets waarmee u switch-, virtuele LAN (VLAN) en elementaire laag 2-netwerk switch poort configuratie kunt Toep assen op een Windows Server 2012 R2 logo-gecertificeerde netwerk switches.
- De para meter FullyQualifiedName is toegevoegd aan cmdlets voor import-module en Remove-module, ter ondersteuning van het opslaan van meerdere versies van één module.
- Save-Help, update-Help, import-PSSession, export-PSSession en Get-Command hebben een nieuwe para meter, FullyQualifiedModule, van het type ModuleSpecification. Voeg deze para meter toe om een module op te geven met de volledig gekwalificeerde naam.
- De waarde van **$PSVersionTable. PSVersion** is bijgewerkt naar 5,0.
- WMF 5,0 (Power shell 5,0) bevat de module **pest** . De ziekte is een framework voor het testen van eenheden voor Power shell. Het bevat enkele eenvoudig te gebruiken tref woorden waarmee u tests kunt maken voor uw scripts.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nieuwe functies in Windows Power shell desired state Configuration

- Met de taal verbeteringen van Windows Power shell kunt u Windows Power shell-resources voor desired state Configuration (DSC) definiëren met behulp van klassen. Import-Dscresource bieden is nu een echt dynamisch sleutel woord. Windows Power shell parseert de hoofd module van de opgegeven module. er wordt gezocht naar klassen die het kenmerk Dscresource bieden bevatten. U kunt nu klassen gebruiken om DSC-resources te definiëren, waarin geen MOF-bestand of een Dscresource bieden-submap in de module map is vereist. Een Windows Power shell-module bestand kan meerdere DSC-resource klassen bevatten.
- Er is een nieuwe para meter, ThrottleLimit, toegevoegd aan de volgende cmdlets in de PSDesiredStateConfiguration-module. Voeg de para meter ThrottleLimit toe om het aantal doel computers of-apparaten op te geven waarop u de opdracht op hetzelfde moment wilt uitvoeren.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get-DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- Met gecentraliseerde DSC-fout rapportage wordt uitgebreide fout informatie niet alleen geregistreerd in het gebeurtenis logboek, maar kan deze naar een centrale locatie worden verzonden voor latere analyse. U kunt deze centrale locatie gebruiken voor het opslaan van DSC-configuratie fouten die zijn opgetreden voor elke server in hun omgeving. Nadat de rapport server is gedefinieerd in de meta configuratie, worden alle fouten verzonden naar de rapport server en vervolgens opgeslagen in een Data Base. U kunt deze functionaliteit instellen, ongeacht of een doel knooppunt is geconfigureerd voor het ophalen van configuraties van een pull-server.
- Verbeteringen voor het Windows PowerShell ISE van het vereenvoudigen van DSC-resource-ontwerpen. U kunt nu het volgende doen.
  - Een lijst met alle DSC-resources in een **configuratie** -of **knooppunt** blok door **Ctrl + spatie** in te voeren op een lege regel in het blok.
  - Automatische voltooiing van bron eigenschappen van het **opsommings** type.
  - Automatische voltooiing van de eigenschap **DependsOn** van DSC-resources op basis van andere bron instanties in de configuratie.
  - Verbeterde tabposities voor de waarden van de bron eigenschap.
- Een gebruiker kan nu een bron uitvoeren onder een opgegeven set referenties door het kenmerk **PSDscRunAsCredential** toe te voegen aan een knooppunt blok. Bijvoorbeeld PSDscRunAsCredential = Get-Credential contoso \\ DscUser. Deze functie is handig voor het maken van configuraties die Windows Installer en uitvoer bare installatie Programma's uitvoeren, toegang krijgen tot de register component per gebruiker of andere taken uitvoeren buiten de huidige gebruikers context.
- ondersteuning voor 32-bits (x86) is toegevoegd voor het sleutel woord **Configuration** .
- Windows Power shell bevat nu ondersteuning voor aangepaste Help voor DSC-configuraties die zijn gedefinieerd door \[ CmdletBinding () aan de gegenereerde configuratie functie toe te voegen.
- Een nieuw **DscLocalConfigurationManager** -kenmerk geeft een configuratie blok aan als een meta configuratie, dat wordt gebruikt om de DSC lokale Configuration Manager te configureren. Dit kenmerk beperkt een configuratie tot alleen items die de DSC lokale Configuration Manager configureren. Tijdens de verwerking genereert deze configuratie een \* . meta. MOF-bestand dat vervolgens wordt verzonden naar de juiste doel knooppunten door de cmdlet Set-DscLocalConfigurationManager uit te voeren.
- Gedeeltelijke configuraties zijn nu toegestaan in Windows Power shell 5,0. U kunt configuratie documenten verzenden naar een knoop punt in fragmenten. Voor een knoop punt om meerdere fragmenten van een configuratie document te ontvangen, moet de lokale Configuration Manager van het knoop punt eerst worden ingesteld om de verwachte fragmenten op te geven
- Synchronisatie tussen computers is nieuw in DSC in Windows Power shell 5,0. Door gebruik te maken van de ingebouwde WaitFor- \* resources (**WaitForAll**, **WaitForAny**en **WaitForSome**), kunt u nu afhankelijkheden opgeven tussen computers tijdens de configuratie uitvoeringen, zonder externe indeling. Deze bronnen bieden synchronisatie van knoop punt naar knoop punt met behulp van CIM-verbindingen via het WS-man-protocol.
  Een configuratie kan wachten tot de specifieke resource status van een andere computer is gewijzigd.
- Net genoeg beheer (JEA), een nieuwe functie voor delegering van de beveiliging, maakt gebruik van DSC-en Windows Power shell-beperkte runspaces om ondernemingen te helpen beschermen tegen gegevens verlies of inbreuk op werk nemers, ongeacht of dit opzettelijk of onbedoeld is. Zie [net genoeg beheer](/powershell/scripting/learn/remoting/jea/overview)voor meer informatie over JEA, waaronder waar u de DSC-resource van xJEA kunt downloaden.
- De volgende nieuwe cmdlets zijn toegevoegd aan de PSDesiredStateConfiguration-module.
  - Een nieuwe cmdlet Get-DscConfigurationStatus krijgt informatie op hoog niveau over de configuratie status van een doel knooppunt. U kunt de status van de laatste of van alle configuraties verkrijgen.
  - Een nieuwe cmdlet Compare-DscConfiguration vergelijkt een opgegeven configuratie met de werkelijke status van een of meer doel knooppunten.
  - Met een nieuwe cmdlet Publish-DscConfiguration wordt een configuratie-MOF-bestand gekopieerd naar een doel knooppunt, maar wordt de configuratie niet toegepast. De configuratie wordt toegepast tijdens de volgende consistentie fase of wanneer u de cmdlet Update-DscConfiguration uitvoert.
  - Met een nieuwe cmdlet test-DscConfiguration kunt u controleren of een resulterende configuratie overeenkomt met de gewenste configuratie en waar als resultaat retourneert als de configuratie overeenkomt met de gewenste configuratie, of ONWAAR als de werkelijke configuratie niet overeenkomt met de gewenste configuratie.
  - Met een nieuwe cmdlet Update-DscConfiguration wordt een configuratie geforceerd verwerkt. Als de lokale Configuration Manager zich in de pull-modus bevindt, wordt de configuratie door de cmdlet opgehaald van de pull-server voordat deze wordt toegepast.

### <a name="new-features-in-windows-powershell-ise"></a>Nieuwe functies in Windows PowerShell ISE

- U kunt nu externe Windows Power shell-scripts en-bestanden bewerken in een lokale kopie van Windows PowerShell ISE, door Enter-PSSession uit te voeren om een externe sessie te starten op de computer die de bestanden opslaat die u wilt bewerken en vervolgens **PSEdit \< pad en bestands naam op \> de externe computer uit**te voeren. Deze functie vereenvoudigt het bewerken van Windows Power Shell-bestanden die zijn opgeslagen op de Server Core-installatie optie van Windows Server, waarbij Windows PowerShell ISE niet kan worden uitgevoerd.
- De cmdlet start-transcriptie wordt nu ondersteund in Windows PowerShell ISE.
- U kunt nu fouten opsporen in externe scripts in Windows PowerShell ISE.
- Een nieuwe menu opdracht, **verbreekt alle** (CTRL + B), breekt de fout opsporing voor zowel lokale als extern uitgevoerde scripts.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nieuwe functies in Windows Power shell Web Services (Management OData IIS extension)

- Vanaf Windows Power shell 5,0 kunt u een set Windows Power shell-cmdlets genereren op basis van de functionaliteit die wordt weer gegeven door een bepaald OData-eind punt, door de cmdlet Export-ODataEndpointProxy uit te voeren in de nieuwe module [micro soft. Power shell. OdataUtils](/powershell/module/microsoft.powershell.odatautils) .

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Belang rijke oplossingen voor fouten in Windows Power shell 5,0

- Windows Power shell 5,0 bevat een nieuwe COM-implementatie, die aanzienlijke prestatie verbeteringen biedt wanneer u met COM-objecten werkt. Zie [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ)voor een video demonstratie van het effect.
- Er zijn belang rijke prestatie verbeteringen aangebracht in de eerste tabpositie in een Windows Power shell-sessie, waardoor de voltooiings tijd van het tabblad wordt verkort met bijna 500 MS.

## <a name="new-features-in-windows-powershell-40"></a>Nieuwe functies in Windows Power Shell 4,0

Windows Power Shell 4,0 is achterwaarts compatibel. Cmdlets, providers, modules, invoeg toepassingen, scripts, functies en profielen die zijn ontworpen voor Windows Power Shell 3,0 en Windows Power Shell 2,0, werken in Windows Power Shell 4,0 zonder wijzigingen.

Windows Power Shell 4,0 wordt standaard geïnstalleerd op Windows 8,1 en Windows Server 2012 R2. Als u Windows Power Shell 4,0 wilt installeren op Windows 7 met SP1 of Windows Server 2008 R2, downloadt en installeert u [Windows Management Framework 4,0](https://www.microsoft.com/download/details.aspx?id=40855). Lees de Download gegevens en zorg ervoor dat aan alle systeem vereisten wordt voldaan voordat u Windows Management Framework 4,0 installeert.

- [Nieuwe functies in Windows Power shell](#new-features-in-windows-powershell-1)
- [Nieuwe functies in Windows Power shell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nieuwe functies in Windows Power shell-werk stroom](#new-features-in-windows-powershell-workflow)
- [Nieuwe functies in Windows Power shell-webservices](#new-features-in-windows-powershell-web-services)
- [Nieuwe functies in Windows Power shell Web Access](#new-features-in-windows-powershell-web-access)
- [Belang rijke oplossingen voor fouten in Windows Power Shell 4,0](#notable-bug-fixes-in-windows-powershell-40)

Windows Power Shell 4,0 bevat de volgende nieuwe functies.

### <a name="new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Nieuwe functies in Windows Power shell

- **Windows Power shell desired state Configuration** (DSC) is een nieuw beheer systeem in Windows power Shell 4,0 waarmee u configuratie gegevens kunt implementeren en beheren voor software services en de omgeving waarin deze services worden uitgevoerd. Zie [aan de slag met Windows Power shell desired state Configuration](/powershell/scripting/dsc/getting-started/wingettingstarted)(Engelstalig) voor meer informatie over DSC.
- **Met Save-Help** kunt u nu Help opslaan voor modules die op externe computers zijn geïnstalleerd. U kunt Save-Help gebruiken om de module Help te downloaden van een client met Internet verbinding (waarop niet alle modules zijn geïnstalleerd waarvoor u hulp nodig hebt), en vervolgens de opgeslagen Help kopiëren naar een externe gedeelde map of een externe computer die geen toegang tot internet heeft.
- De Windows Power Shell-fout opsporing is uitgebreid voor het toestaan van fout opsporing van Windows Power shell-werk stromen en voor scripts die worden uitgevoerd op externe computers. Windows Power shell-werk stromen kunnen nu worden opgespoord op script niveau vanuit de Windows Power shell-opdracht regel of Windows PowerShell ISE. Windows Power shell-scripts, met inbegrip van script werk stromen, kunnen nu worden opgespoord via externe sessies. Sessies voor externe fout opsporing worden bewaard via externe Windows Power shell-sessies die niet meer zijn verbonden en vervolgens opnieuw verbinding maken.
- Een **RunNow** -para meter voor **REGI ster-ScheduledJob** en **set-ScheduledJob** elimineert de nood zaak om een onmiddellijke start datum en-tijd voor taken in te stellen met behulp van de **trigger** parameter.
- Met **invoke-RestMethod** en **invoke-WebRequest** kunt u nu alle headers instellen met behulp van de para meter headers. Hoewel deze para meter altijd bestaat, was het een van de para meters voor de Web-cmdlets die hebben geleid tot uitzonde ringen of fouten.
- **Get-module** heeft een nieuwe para meter, **FullyQualifiedName**, van het type **ModuleSpecification \[ ]**. Met de para meter **FullyQualifiedName** van de Get-module kunt u nu een module opgeven met behulp van de naam, versie en optioneel de GUID van de module.
- De standaard instelling voor het uitvoerings beleid van Windows Server 2012 R2 is **RemoteSigned**. In Windows 8,1 is er geen wijziging in de standaard instelling.
- Vanaf Windows Power Shell 4,0 wordt de methode aanroep met behulp van dynamische methode namen ondersteund.
  U kunt een variabele gebruiken om een methode naam op te slaan en de methode vervolgens dynamisch aanroepen door de variabele aan te roepen.
- Asynchrone werk stroom taken worden niet meer verwijderd wanneer de time-outperiode die is opgegeven door de algemene para meter **PSElapsedTimeoutSec** workflow is verstreken.
- Er is een nieuwe para meter, **RepeatIndefinitely**, toegevoegd aan de cmdlets **New-JobTrigger** en **set-JobTrigger** . Dit elimineert de nood zaak van het opgeven van een **time span. MaxValue** -waarde voor de para meter **RepetitionDuration** om een geplande taak herhaaldelijk voor een onbepaalde periode uit te voeren.
- Er is een **PassThru** -para meter toegevoegd aan de cmdlets **Enable-JobTrigger** en **Disable-JobTrigger** . De para meter PassThru geeft alle objecten weer die zijn gemaakt of gewijzigd door de opdracht.
- De parameter namen voor het opgeven van een werk groep in de cmdlets **add-computer** en **Remove-computer** zijn nu consistent. Beide cmdlets gebruiken nu de para meter **werk groep**.
- Er is een nieuwe gemeen schappelijke para meter, **PipelineVariable**, toegevoegd. Met PipelineVariable kunt u de resultaten van een piped opdracht (of onderdeel van een piped opdracht) opslaan als een variabele die kan worden door gegeven via de rest van de pijp lijn.
- Verzamelings filters met behulp van de syntaxis van een methode worden nu ondersteund. Dit betekent dat u nu een verzameling objecten kunt filteren met behulp van vereenvoudigde syntaxis, vergelijkbaar met die voor WHERE () of where-object, opgemaakt als een methode aanroep. Hier volgt een voor beeld: (Get-process). where ({$ _. Naam-overeenkomende Power shell})
- De cmdlet **Get-process** heeft een nieuwe switch parameter, **IncludeUserName**.
- Een nieuwe cmdlet **Get-FileHash**, die een bestandshash retourneert in een van de verschillende indelingen voor een opgegeven bestand, is toegevoegd.
- In Windows Power Shell 4,0, als een module de sleutel **DefaultCommandPrefix** in het manifest gebruikt, of als de gebruiker een module importeert met de para meter **prefix** , worden de opdrachten in de module met het voor voegsel in de eigenschap **ExportedCommands** van de module weer gegeven. Wanneer u de opdrachten uitvoert met behulp van de module-gekwalificeerde syntaxis, module \\ naam opdracht, moeten de opdracht namen het voor voegsel bevatten.
- De waarde van **$PSVersionTable. PSVersion** is bijgewerkt naar 4,0.
- **Waar ()** operator gedrag is gewijzigd. `Collection.Where('property -match name')`het accepteren van een teken reeks expressie in de indeling `"Property -CompareOperator Value"` wordt niet meer ondersteund.
  De operator **WHERE ()** accepteert echter teken reeks expressies in de indeling van een script Block; Dit wordt nog steeds ondersteund.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nieuwe functies in Windows Power shell Integrated Scripting Environment (ISE)

- Windows PowerShell ISE ondersteunt zowel Windows Power shell-werk stroom fout opsporing als externe script fout opsporing.
- IntelliSense-ondersteuning is toegevoegd voor de gewenste status configuratie providers en configuraties van Windows Power shell.

### <a name="new-features-in-windows-powershell-workflow"></a>Nieuwe functies in Windows Power shell-werk stroom

- Er is ondersteuning toegevoegd voor een nieuwe algemene para meter **PipelineVariable** in de context van iteratieve pijp lijnen, zoals die worden gebruikt door System Center Orchestrator. dat wil zeggen, pijp lijnen met opdrachten die gewoon van links naar rechts worden uitgevoerd, in tegens telling tot verkeer met behulp van streamen.
- Het binden van de para meters is aanzienlijk verbeterd ten opzichte van het volt ooien van scenario's, zoals opdrachten die niet aanwezig zijn in de huidige runs Pace.
- Ondersteuning voor aangepaste container activiteiten is toegevoegd aan de Windows Power shell-werk stroom. Als een activiteit parameter van het type **activiteit**, **activiteit \[ ]** (of een algemene verzameling activiteiten is) en de gebruiker een script blok als argument heeft opgegeven, wordt het script blok door Windows Power shell-werk stroom geconverteerd naar XAML, net als bij een normale compilatie van Windows Power shell-script naar werk stroom.
- Na een crash maakt Windows Power shell-werk stroom automatisch opnieuw verbinding met beheerde knoop punten.
- U kunt de instructie **foreach-parallel** activitys nu beperken met behulp van de eigenschap **ThrottleLimit** .
- De algemene para meter **Error Action** heeft een nieuwe geldige waarde, **suspend**, die uitsluitend voor werk stromen is.
- Een werk stroom eindpunt wordt nu automatisch gesloten als er geen actieve sessies zijn, geen taken in uitvoering en geen taken in behandeling zijn. Deze functie bespaart resources op de computer die fungeert als de werk stroom server, wanneer aan de voor waarden voor automatisch sluiten is voldaan.

### <a name="new-features-in-windows-powershell-web-services"></a>Nieuwe functies in Windows Power shell-webservices

- Wanneer zich een fout voordoet in Windows Power shell Web Services (PSWS, ook wel Management OData IIS extension), terwijl een cmdlet wordt uitgevoerd, worden er meer gedetailleerde fout berichten naar de oproepende functie geretourneerd. Daarnaast volgen fout codes de [richt lijnen voor de fout code van Windows Azure rest API](/rest/api/storageservices/Common-REST-API-Error-Codes).
- Een eind punt kan nu de API-versie definiëren, maar ook het gebruik van een specifieke API-versie afdwingen. Wanneer de versie van de client en de server niet overeenkomt, worden fouten op de client en de server weer gegeven.
- Het beheer van het verzend schema is vereenvoudigd door automatisch waarden te genereren voor ontbrekende velden in het schema. Genereren vindt plaats als handig begin punt, zelfs als het verzend schema niet bestaat.
- Type verwerking in PSWS is verbeterd tot ondersteuning voor typen die gebruikmaken van een andere constructor dan de standaardconstructor, door te werken op dezelfde manier als de **PSTypeConverter** in Windows Power shell. Hiermee kunt u complexe typen gebruiken met PSWS.
- Met PSWS kan nu een gekoppeld exemplaar worden uitgebreid tijdens het uitvoeren van een query. Voor grotere binaire inhoud (zoals afbeeldingen, audio of video) zijn de kosten voor de overdracht aanzienlijk en is het beter om binaire gegevens zonder code ring over te dragen. PSWS maakt gebruik van benoemde resource stromen voor het overbrengen zonder code ring.
  De naam van de resource stroom is een eigenschap van een entiteit van het type **EDM. Stream** . Elke benoemde resource stroom heeft een afzonderlijke URI voor GET-of UPDATE-bewerkingen.
- OData-acties bieden nu een mechanisme voor het aanroepen van niet-ruwe methoden (maken, lezen, bijwerken en verwijderen) voor een resource. U kunt een actie aanroepen door een HTTP POST-aanvraag te verzenden naar de URI die voor de actie is gedefinieerd. De para meters voor de actie worden gedefinieerd in de hoofd tekst van de POST-aanvraag.
- Om consistent te zijn met de richt lijnen voor Windows Azure, moeten alle Url's worden vereenvoudigd. Een wijziging die is opgenomen in de **sleutel als segment** , staat het weer gegeven van afzonderlijke sleutels als segmenten. Houd er rekening mee dat verwijzingen die gebruikmaken van meerdere sleutel waarden, door komma's gescheiden waarden hebben in de notatie tussen haakjes, net als voorheen.
- Vóór deze release van PSWS is de enige manier om bewerkingen voor maken, bijwerken of verwijderen uit te voeren op een resource op het hoogste niveau. In deze release van PSWS kunnen gebruikers met een opgenomen resource dezelfde resultaten bereiken, terwijl ze dezelfde resource minder rechtstreeks bereiken, alsof deze bronnen zich bevinden.

### <a name="new-features-in-windows-powershell-web-access"></a>Nieuwe functies in Windows Power shell Web Access

- U kunt de verbinding verbreken en opnieuw verbinding maken met bestaande sessies in de web-console van Windows Power shell Web Access. Met de knop **Opslaan** in de webconsole kunt u de verbinding met een sessie verbreken zonder deze te verwijderen en opnieuw verbinding te maken met de sessie.
- Standaard parameters kunnen worden weer gegeven op de aanmeldings pagina. Als u standaard parameters wilt weer geven, configureert u waarden voor alle instellingen die worden weer gegeven in het gedeelte **optionele Verbindings instellingen** van de aanmeldings pagina in een bestand met de naam **Web. config**. U kunt het bestand **Web. config** gebruiken om alle optionele Verbindings instellingen te configureren, behalve voor een tweede of alternatieve set referenties.
- In Windows Server 2012 R2 kunt u autorisatie regels voor Windows Power shell-Internet toegang op afstand beheren. De cmdlets **add-PswaAuthorizationRule** en **test-PswaAuthorizationRule** bevatten nu een referentie parameter waarmee beheerders autorisatie regels kunnen beheren vanaf een externe computer of in een Windows Power shell-sessie voor Internet toegang.
- U kunt nu meerdere Windows Power shell-sessies voor webtoegang hebben in één browser sessie met behulp van een nieuw browser tabblad voor elke sessie. U hoeft niet langer een nieuwe browser sessie te openen om verbinding te maken met een nieuwe sessie in de Windows Power shell-console van het web.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Belang rijke oplossingen voor fouten in Windows Power Shell 4,0

- **Get-Counter** kan nu tellers retour neren die een apostrof bevatten in Franse versies van Windows.
- U kunt nu de **gettype** -methode op gedeserialiseerd objecten weer geven.
- **#Requires** -instructies stellen gebruikers nu in staat beheerders toegangs rechten te vereisen, indien nodig.
- De cmdlet **import-CSV** negeert nu lege regels.
- Er is een probleem opgelost waarbij Windows PowerShell ISE te veel geheugen gebruikt wanneer u een opdracht **invoke-WebRequest** uitvoert.
- In de **Get-module** worden nu module versies weer gegeven in een kolom **versie** .
- Verwijder-item-recursief verwijdert nu items uit submappen zoals verwacht.
- Er is een eigenschap **username** toegevoegd aan **Get-process** uitvoer objecten.
- De cmdlet **invoke-RestMethod** retourneert nu alle beschik bare resultaten.
- De **invoeg toepassing** wordt nu toegepast op hashtabellen, zelfs als de hashtabellen nog niet zijn geopend.
- **Select-object-Expand** niet meer mislukt of er wordt een uitzonde ring gegenereerd als de waarde van de eigenschap Null of leeg is.
- **Get-process** kan nu worden gebruikt in een pijp lijn met andere opdrachten die de eigenschap **ComputerName** van objecten ophalen.
- **ConvertTo-JSON** en **ConvertFrom-JSON** kan nu voor waarden binnen dubbele aanhalings tekens accepteren en de fout berichten kunnen nu worden gelokaliseerd.
- **Get-job** retourneert nu voltooide geplande taken, zelfs in nieuwe sessies.
- Problemen met het koppelen en ontkoppelen van Vhd's met behulp van de **bestandssysteem** provider in Windows power Shell 4,0 zijn opgelost. Windows Power shell kan nu nieuwe stations detecteren wanneer ze in dezelfde sessie zijn gekoppeld.
- U hoeft niet langer expliciet **ScheduledJob** of **werk stroom** modules te laden om met hun taak typen te werken.
- Er zijn prestatie verbeteringen aangebracht in het proces van het importeren van werk stromen waarmee geneste werk stromen worden gedefinieerd. Dit proces is nu sneller.

## <a name="new-features-in-windows-powershell-30"></a>Nieuwe functies in Windows Power Shell 3,0

Windows Power Shell 3,0 bevat de volgende nieuwe functies.

- [Windows Power shell-werk stroom](#windows-powershell-workflow)
- [Windows Power shell-Internet toegang](#windows-powershell-web-access)
- [Nieuwe Windows PowerShell ISE functies](#new-windows-powershell-ise-features)
- [Ondersteuning voor Microsoft .NET Framework 4,0](#support-for-microsoft-net-framework-4)
- [Ondersteuning voor Windows Preinstallation Environment](#support-for-windows-preinstallation-environment)
- [Verbroken sessies](#disconnected-sessions)
- [Connectiviteit van robuuste sessies](#robust-session-connectivity)
- [Bij te werken Help-systeem](#updatable-help-system)
- [Uitgebreide online-Help](#enhanced-online-help)
- [CIM-integratie](#cim-integration)
- [Sessie configuratie bestanden](#session-configuration-files)
- [Geplande taken en de integratie van taak planner](#scheduled-jobs-and-task-scheduler-integration)
- [Windows Power shell-taal verbeteringen](#windows-powershell-language-enhancements)
- [Nieuwe kern-cmdlets](#new-core-cmdlets)
- [Verbeteringen aan bestaande kern-cmdlets en-providers](#improvements-to-existing-core-cmdlets-and-providers)
- [Externe module importeren en detecteren](#remote-module-import-and-discovery)
- [Uitgebreide tabblad voltooiing](#enhanced-tab-completion)
- [Module automatisch laden](#module-auto-loading)
- [Verbeteringen in module-ervaring](#module-experience-improvements)
- [Vereenvoudigde opdracht detectie](#simplified-command-discovery)
- [Verbeterde ondersteuning voor logboek registratie, diagnostiek en groepsbeleid](#improved-logging-diagnostics-and-group-policy-support)
- [Verbeteringen in de opmaak en uitvoer](#formatting-and-output-improvements)
- [Verbeterde beleving van de console-host](#enhanced-console-host-experience)
- [Nieuwe cmdlet-en hosting-Api's](#new-cmdlet-and-hosting-apis)
- [Prestatie verbeteringen](#performance-improvements)
- [Ondersteuning voor runas en gedeelde host](#runas-and-shared-host-support)
- [Verbeteringen voor speciale teken verwerking](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows Power shell-werk stroom

De Windows Power shell-werk stroom biedt de kracht van Windows Workflow Foundation naar Windows Power shell.
U kunt werk stromen schrijven in XAML of in de Windows Power shell-taal en uitvoeren op dezelfde manier als u een cmdlet zou uitvoeren. De `Get-Command` cmdlet krijgt werk stroom opdrachten en de `Get-Help` cmdlet krijgt hulp voor werk stromen.

Werk stromen zijn reeksen van multicomputer Management-activiteiten die langdurig worden uitgevoerd, herhaal bare, frequente, kan worden opgestart, onderbreekbaar, suspendable en opnieuw kunnen worden gestart. Werk stromen kunnen worden hervat met een opzettelijke of accidentele onderbreking, zoals een netwerk storing, een Windows-computer of een stroom storing.

Werk stromen zijn ook draagbaar; ze kunnen worden geëxporteerd als of geïmporteerd uit XAML-bestanden. U kunt aangepaste sessie configuraties schrijven waarmee werk stromen of activiteiten in een werk stroom kunnen worden uitgevoerd door gedelegeerde of ondergeschikte gebruikers.

Hier volgen de voor delen van Windows Power shell-werk stroom

- Automatisering van geordende, langlopende taken.
- **Externe controle van langlopende taken**. De status en voortgang van activiteiten zijn op elk gewenst moment zichtbaar.
- **Beheer van alle computers.** Gelijktijdig taken uitvoeren als werk stromen op honderden beheerde knoop punten.
  De Windows Power shell-werk stroom bevat een ingebouwde bibliotheek met algemene beheer parameters, zoals **PSComputerName**, waarmee beheer scenario's voor meerdere computers mogelijk zijn.
- **Uitvoering van een enkele taak van complexe processen.** U kunt gerelateerde scripts combi neren die een volledig end-to-end-scenario implementeren in één werk stroom.
- **Persistentie.**: een werk stroom wordt opgeslagen (of Check-Point) op specifieke punten die zijn gedefinieerd door de auteur, zodat u de werk stroom kunt hervatten vanaf de laatste persistente taak (of controle punt), in plaats van de werk stroom vanaf het begin opnieuw te starten.
- **Kracht.** Automatisch herstel van fouten. Werk stromen blijven gepland en niet-gepland opnieuw worden gestart. U kunt de uitvoering van de werk stroom onderbreken en de werk stroom vervolgens hervatten vanaf het laatste persistentie punt.
  Werk stroom ontwerpers kunnen specifieke activiteiten aanwijzen die opnieuw moeten worden uitgevoerd in geval van een storing op een of meer beheerde knoop punten.
- **De mogelijkheid om de verbinding te verbreken, opnieuw te verbinden en uit te voeren in sessies zonder verbinding.** Gebruikers kunnen verbinding maken met de werk stroom server en de verbinding verbreken, maar de werk stroom wordt doorlopend uitgevoerd. U kunt zich afmelden bij de client computer of de client computer opnieuw opstarten en de uitvoering van de werk stroom op een andere computer controleren zonder de werk stroom te onderbreken.
- **Schema.** Werk stroom taken kunnen worden gepland zoals elke Windows Power shell-cmdlet of script.
- **Beperking van werk stromen en verbindingen.** Het uitvoeren van werk stromen en verbindingen met knoop punten kunnen worden beperkt, waardoor de scenario's voor schaal baarheid en hoge Beschik baarheid worden ingeschakeld.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access

Windows Power shell Web Access is een Windows Server 2012-functie waarmee gebruikers Windows Power shell-opdrachten en-scripts kunnen uitvoeren in een webconsole. Voor apparaten die gebruikmaken van de webconsole, zijn geen Windows Power shell, software voor extern beheer of installatie van invoeg toepassingen vereist. Alles wat vereist is, is een correct geconfigureerde Windows Power shell Web Access-Gateway en een browser voor client apparaten die Java script ondersteunt en cookies accepteert.

Zie [deploy Windows Power shell Web Access](/powershell/scripting/components/web-access/install-and-use-windows-powershell-web-access)(Engelstalig) voor meer informatie.

### <a name="new-windows-powershell-ise-features"></a>Nieuwe Windows PowerShell ISE functies

Voor Windows Power Shell 3,0 heeft Windows Power shell Integrated Scripting Environment (ISE) tal van nieuwe functies, waaronder IntelliSense, show-Opdrachtvenster, een gecombineerd console venster, fragmenten, accolades, vouw-samen vouwen secties, automatisch opslaan, lijst met recente items, uitgebreide kopie, blok kopie en volledige ondersteuning voor het schrijven van Windows Power shell-script werk stromen. Zie [about_Windows_PowerShell_ISE](/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise)voor meer informatie.

### <a name="support-for-microsoft-net-framework-4"></a>Ondersteuning voor Microsoft .NET Framework 4

Windows Power shell is gebouwd op basis van de common language runtime 4,0. Cmdlet-, script-en werk stroom auteurs kunnen de nieuwe Microsoft .NET Framework 4-klassen in Windows Power shell gebruiken, met functies die toepassings compatibiliteit en-implementatie, Managed Extensibility Framework, parallelle computing, netwerken, Windows Communication Foundation en Windows Workflow Foundation, bevatten.

### <a name="support-for-windows-preinstallation-environment"></a>Ondersteuning voor Windows Preinstallation Environment

Windows Power Shell 3,0 is een optioneel onderdeel van Windows Preinstallation Environment (Windows PE) 4,0 voor Windows 8. Windows PE is een mini maal besturings systeem waarmee een computer zonder besturings systeem wordt gestart en wordt voor bereid voor de installatie van Windows. Windows PE kan worden gebruikt voor het partitioneren en Format teren van harde schijven, het kopiëren van schijf installatie kopieën naar een computer en het initiëren van Windows Setup vanaf een netwerk share.
Windows Power Shell 3,0 kan worden gebruikt in Windows PE voor het beheren van implementatie-, diagnose-en herstel scenario's.

### <a name="disconnected-sessions"></a>Verbroken sessies

Met ingang van Windows Power Shell 3,0, permanente door de gebruiker beheerde sessies (' PSSessions ') die u maakt met behulp van de cmdlet New-PSSession, worden opgeslagen op de externe computer. Ze zijn niet langer afhankelijk van de sessie waarin ze zijn gemaakt.

U kunt nu de verbinding met een sessie verbreken zonder de opdrachten die worden uitgevoerd in de sessie te onderbreken. U kunt de sessie sluiten en de computer afsluiten. Later kunt u opnieuw verbinding maken met de sessie vanuit een andere sessie op hetzelfde of op een andere computer.

De para meter **ComputerName** van de `Get-PSSession` cmdlet haalt nu alle sessies van de gebruiker op die verbinding maken met de computer, zelfs als deze zijn gestart in een andere sessie op een andere computer. U kunt verbinding maken met de sessies, de resultaten van opdrachten ophalen, nieuwe opdrachten starten en vervolgens de verbinding met de sessie verbreken.

Er zijn nieuwe cmdlets toegevoegd ter ondersteuning van de functie voor verbroken sessies, waaronder `Disconnect-PSSession` , `Connect-PSSession` en `Receive-PSSession` , en er zijn nieuwe para meters toegevoegd aan cmdlets die PSSessions beheren, zoals de para meter **InDisconnectedSession** van de `Invoke-Command` cmdlet.

De functie voor het beëindigen van de verbinding wordt alleen ondersteund als de computers op de oorspronkelijke server (' client ') en het afsluiten van de verbinding Windows Power Shell 3,0 worden uitgevoerd.

### <a name="robust-session-connectivity"></a>Connectiviteit van robuuste sessies

Windows Power Shell 3,0 detecteert onverwachte verliezen van connectiviteit tussen de client en de server en probeert de verbinding opnieuw tot stand te brengen en de uitvoering automatisch te hervatten. Als de client/server-verbinding niet binnen de toegewezen tijd kan worden hersteld, wordt de gebruiker hiervan op de hoogte gebracht en wordt de sessie verbroken. Tijdens de poging om opnieuw verbinding te maken, biedt Windows Power shell voortdurende feedback over de gebruiker.

Als de niet-verbonden sessie met behulp van de InvokeCommand is gestart, maakt Windows Power shell een taak voor de niet-verbonden sessie, zodat het eenvoudiger wordt om opnieuw verbinding te maken en de uitvoering te hervatten.

Deze functies bieden een betrouwbaardere en onherstelbare mogelijkheden voor externe communicatie en bieden gebruikers de mogelijkheid om langlopende taken uit te voeren die robuuste sessies vereisen, zoals werk stromen.

### <a name="updatable-help-system"></a>Bij te werken Help-systeem

U kunt nu bijgewerkte Help-bestanden voor de cmdlets in uw modules downloaden. Met de `Update-Help` cmdlet worden de nieuwste Help-bestanden geïdentificeerd, worden deze gedownload van Internet, worden ze uitgepakt, gevalideerd en worden ze in de juiste taalspecifieke Directory voor de module geïnstalleerd.

Als u de bijgewerkte Help-bestanden wilt gebruiken, typt u `Get-Help` . U hoeft Windows of Windows Power shell niet opnieuw op te starten. Als u de Help voor modules in de map $pshome wilt bijwerken, start u Windows Power shell met de optie als administrator uitvoeren.

Ter ondersteuning van gebruikers die geen toegang hebben tot internet en gebruikers achter firewalls, downloadt de nieuwe `Save-Help` cmdlet Help-bestanden naar een bestandssysteem Directory, zoals een bestands share. Gebruikers kunnen de cmdlet vervolgens gebruiken `Update-Help` om bijgewerkte Help-bestanden van de bestands share op te halen.

U kunt de `Update-Help` cmdlet gebruiken om Help-bestanden voor alle of bepaalde modules in alle ondersteunde gebruikersinterface culturen bij te werken. U kunt zelfs een `Update-Help` opdracht in uw Windows Power shell-profiel plaatsen.
Windows Power shell downloadt standaard de Help-bestanden voor een module niet meer dan één keer per dag.

Windows 8-en Windows Server 2012-modules bevatten geen Help-bestanden. Als u de nieuwste Help-bestanden wilt downloaden, typt u `Update-Help` . Typ `Get-Help` (zonder para meters) of zie [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_Updatable_Help)voor meer informatie.

Wanneer de Help bestanden voor een cmdlet niet op de computer zijn geïnstalleerd, wordt in de `Get-Help` cmdlet nu automatisch gegenereerde Help weer gegeven. De automatisch gegenereerde Help omvat de opdracht syntaxis en instructies voor het gebruik van de `Update-Help` cmdlet om Help-bestanden te downloaden.

Elke auteur van een module kan de Help-informatie voor de module ondersteunen. U kunt Help-bestanden in de module toevoegen en Help-informatie gebruiken om ze bij te werken of de Help-bestanden te verwijderen en de bij te werken hulp gebruiken om ze te installeren. Zie [ondersteunende Help](/powershell/scripting/developer/module/supporting-updatable-help)voor meer informatie over ondersteunende Help.

### <a name="enhanced-online-help"></a>Uitgebreide online-Help

De online Help van Windows Power shell is een waardevolle resource voor alle gebruikers, maar is vooral belang rijk voor gebruikers die geen bijgewerkte Help-bestanden kunnen installeren.

Als u online-Help voor een Windows Power shell-cmdlet wilt weer geven, typt u:

```
Get-Help <cmdlet-name> -Online
```

In Windows Power shell wordt de online versie van het Help-onderwerp in de standaard browser van Internet geopend.

De functie **Get-Help-online** in Windows power Shell 3,0 is nu nog krachtiger omdat deze werkt, zelfs wanneer de Help bestanden voor de cmdlet niet op de computer zijn geïnstalleerd. De functie **Get-Help-online** haalt de URI op voor het online Help-onderwerp van de eigenschap HelpUri van cmdlets en geavanceerde functies.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
https://go.microsoft.com/fwlink/?LinkID=223923
```

Vanaf Windows Power Shell 3,0 kunnen auteurs van C#-cmdlets de eigenschap **HelpUri** vullen door een **HelpUri** -kenmerk te maken voor de cmdlet-klasse. Auteurs van geavanceerde functies kunnen een eigenschap **HelpUri** definiëren voor het kenmerk **CmdletBinding** . De waarde van de eigenschap **HelpUri** moet beginnen met http of https.

U kunt ook een **HelpUri** -waarde toevoegen aan de eerste gerelateerde koppeling van een Help-bestand op basis van een XML-cmdlet of de. Een koppelings instructie voor op opmerkingen gebaseerde Help in een functie.

Zie [ondersteuning voor online-Help](/powershell/scripting/developer/module/supporting-online-help) in de Microsoft docs voor meer informatie over de ondersteuning van online-Help.

### <a name="cim-integration"></a>CIM-integratie

Windows Power Shell 3,0 bevat ondersteuning voor de Common Information Model (CIM), die algemene definities bevat van beheer gegevens voor systemen, netwerken, toepassingen en services, waardoor de uitwisseling van beheer gegevens tussen heterogene systemen mogelijk wordt. Ondersteuning voor CIM in Windows Power Shell 3,0, met inbegrip van de mogelijkheid om Windows Power shell-cmdlets te schrijven op basis van nieuwe of bestaande CIM-klassen, opdrachten op basis van XML-bestanden voor cmdlet definition, ondersteuning voor CIM-.NET Framework. API-, CIM Management-cmdlets en WMI 2,0-providers.

### <a name="session-configuration-files"></a>Sessie configuratie bestanden

Vanaf Windows Power Shell 3,0 kunt u een aangepaste sessie configuratie ontwerpen met behulp van een bestand.
Met het nieuwe sessie configuratie bestand kunt u de omgeving van sessies bepalen die gebruikmaken van de sessie configuratie, inclusief welke modules, scripts en indelings bestanden worden geladen in sessies, welke cmdlets en taal elementen gebruikers kunnen gebruiken, welke modules en scripts ze kunnen uitvoeren en welke variabelen ze kunnen zien.

U kunt een sessie ontwerpen waarin gebruikers alleen de cmdlets van een bepaalde module kunnen uitvoeren, of een sessie waarin gebruikers volledige taal hebben, toegang hebben tot alle modules en toegang hebben tot scripts waarmee geavanceerde taken worden uitgevoerd.

In eerdere versies van Windows Power shell was beheer op dit niveau alleen beschikbaar voor gebruikers die een C#-programma of een complex opstart script kunnen schrijven. Nu kan elk lid van de groep Administrators op de computer een sessie configuratie aanpassen met behulp van een configuratie bestand.

Gebruik de cmdlet om een sessie configuratie bestand te maken `New-PSSessionConfigurationFile` . Gebruik de `Register-PSSessionConfiguration` of ' set-PSSessionConfiguration-cmdlets om het sessie configuratie bestand toe te passen op een sessie configuratie.

Zie [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files) en voor meer informatie `New-PSSessionConfigurationFile` .

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Geplande taken en de integratie van taak planner

U kunt nu Windows Power shell-achtergrond taken plannen en deze beheren in Windows Power shell en in taak planner.

Geplande Windows Power shell-taken zijn een handige hybride taak voor Windows Power shell-achtergrond taken en Task Scheduler-taken.

Net als Windows Power shell-achtergrond taken worden geplande taken asynchroon uitgevoerd op de achtergrond.
Exemplaren van geplande taken die zijn voltooid, kunnen worden beheerd met behulp van de taak-cmdlets, zoals `Start-Job` en `Get-Job` .

Net als taak planner-taken kunt u geplande taken uitvoeren op een eenmalige of terugkerende planning of als reactie op een actie of gebeurtenis. U kunt geplande taken weer geven en beheren in Task Scheduler, deze indien nodig inschakelen en uitschakelen, uitvoeren of gebruiken als sjablonen, en voor waarden instellen waaronder de taken worden gestart.

Daarnaast worden geplande taken geleverd met een aangepaste set cmdlets voor het beheer van deze functies. Met de cmdlets kunt u geplande taken maken, bewerken, beheren, uitschakelen en opnieuw inschakelen, geplande taak triggers maken en opties voor geplande taken instellen.

Zie [about_Scheduled_Jobs](/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1)voor meer informatie over geplande taken.

### <a name="windows-powershell-language-enhancements"></a>Windows Power shell-taal verbeteringen

Windows Power Shell 3,0 bevat veel functies die zijn ontworpen om de taal eenvoudiger, gemakkelijker te gebruiken en veelvoorkomende fouten te voor komen. De verbeteringen zijn onder andere eigenschaps inventarisatie, eigenschappen van aantal en lengte van scalaire objecten, nieuwe omleidings operatoren, de $Using bereik aanpassing, PSItem automatische variabele, flexibele script opmaak, kenmerken van variabelen, vereenvoudigde kenmerk argumenten, numerieke opdracht namen, de operator voor het stoppen van parseren, verbeterde matrix splatting, nieuwe bits-Opera Tors, geordende woorden lijsten, PSCustomObject Casting en

### <a name="new-core-cmdlets"></a>Nieuwe kern-cmdlets

Er zijn nieuwe cmdlets toegevoegd aan de Windows Power shell Core-installatie, inclusief cmdlets voor het beheren van geplande taken, verbroken sessies, CIM-integratie en het Help-systeem dat kan worden bijgewerkt.

|                           |                                 |
| ------------------------- | ------------------------------- |
| Add-JobTrigger            | New-JobTrigger                  |
| Connect-PSSession         | New-PSSessionConfigurationFile  |
| ConvertFrom-JSON          | New-PSTransportOption           |
| ConvertTo-Json            | New-New psworkflowexecutionoption   |
| Disable-JobTrigger        | New-PSWorkflowSession           |
| Disable-ScheduledJob      | New-ScheduledJobOption          |
| Verbinding verbreken-PSSession      | New-Wine vent                    |
| Enable-JobTrigger         | Receive-PSSession               |
| Enable-ScheduledJob       | REGI ster-CimIndicationEvent     |
| Get-CimAssociatedInstance | REGI ster-ScheduledJob           |
| Get-CimClass              | Remove-CimInstance              |
| Get-CimInstance           | Remove-CimSession               |
| Get-CimSession            | Remove-TypeData                 |
| Get-ControlPanelItem      | Naam wijzigen-computer                 |
| Get-IseSnippet            | Resume-job                      |
| Get-JobTrigger            | Opslaan-Help                       |
| Get-ScheduledJob          | Set-CimInstance                 |
| Get-ScheduledJobOption    | Set-JobTrigger                  |
| Get-TypeData              | Set-ScheduledJob                |
| Import-IseSnippet         | Set-ScheduledJobOption          |
| Invoke-AsWorkflow         | Weer geven-opdracht                    |
| Invoke-CimMethod          | Show-ControlPanelItem           |
| Invoke-RestMethod         | Onderbreken-taak                     |
| Invoke-WebRequest         | Test-PSSessionConfigurationFile |
| New-CimInstance           | Blok kering van bestand opheffen                    |
| New-CimSession            | Registratie ongedaan maken-ScheduledJob         |
| New-CimSessionOption      | Update-Help                     |
| New-IseSnippet            |                                 |

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Verbeteringen aan bestaande kern-cmdlets en-providers

Windows Power Shell 3,0 bevat nieuwe functies voor bestaande cmdlets, met inbegrip van de vereenvoudigde syntaxis, en nieuwe para meters voor de volgende cmdlets: computer-cmdlets, CSV-cmdlets, Get-Child item, Get-opdracht, Get-content, Get-History, Measure-object, Security cmdlets, select-object, Select-String, Split-pad, start-process, t-object, Test-Connection, add-member en WMI-cmdlets.

De Windows Power shell-providers zijn ook aanzienlijk verbeterd, inclusief ondersteuning voor certificaat providers voor het beheren van SSL-certificaten (Secure Socket Layer) voor webhosting, ondersteuning voor referentie, permanente netwerk stations en alternatieve gegevens stromen in bestandssysteem stations.

### <a name="remote-module-import-and-discovery"></a>Externe module importeren en detecteren

Windows Power Shell 3,0 breidt module detectie, import en impliciete mogelijkheden voor externe communicatie uit op externe computers. Met de module-cmdlets worden modules op externe computers opgehaald en worden de modules naar de externe of lokale computer geïmporteerd met behulp van externe communicatie van Windows Power shell. Met de nieuwe ondersteuning voor CIM-sessies kunt u CIM en WMI gebruiken voor het beheren van niet-Windows-computers door opdrachten te importeren naar de lokale computer die impliciet wordt uitgevoerd op de externe computer.

Zie de Help-onderwerpen voor de `Get-Module` cmdlets en voor meer informatie `Import-Module` .

### <a name="enhanced-tab-completion"></a>Uitgebreide tabblad voltooiing

Tabblad voltooiing in de Windows Power shell-console voltooit nu de namen van cmdlets, para meters, parameter waarden, opsommingen, .NET Frameworks-typen, COM-objecten, verborgen directory's en meer.
De functie voor het volt ooien van het tabblad is volledig herschreven op basis van een nieuwe parser en abstracte syntaxis structuur ter ondersteuning van meer scenario's, waaronder het in-Memory parseren van structuren en de vulling van het tabblad middenlijn.

### <a name="module-auto-loading"></a>Module automatisch laden

De `Get-Command` cmdlet haalt nu alle cmdlets en functies op uit alle modules die op de computer zijn geïnstalleerd, zelfs als de module niet in de huidige sessie is geïmporteerd.

Wanneer u de cmdlet krijgt die u nodig hebt, kunt u deze direct gebruiken zonder modules te importeren.
Windows Power shell-modules worden nu automatisch geïmporteerd wanneer u een cmdlet in de module gebruikt. U hoeft niet langer te zoeken naar de module en deze te importeren om de bijbehorende cmdlets te gebruiken.

Het automatisch importeren van modules wordt geactiveerd met behulp van de cmdlet in een opdracht die wordt uitgevoerd `Get-Command` voor een cmdlet zonder joker tekens of die wordt uitgevoerd `Get-Help` voor een cmdlet zonder joker tekens.

U kunt het automatisch importeren van modules in-en uitschakelen en configureren door gebruik te maken van de **$PSModuleAutoLoadingPreference** voorkeurs variabele.

Zie [about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules), [about_Preference_Variables](/powershell/module/microsoft.powershell.core/about/about_Preference_Variables)en de Help-onderwerpen voor de `Get-Command` cmdlets voor meer informatie `Import-Module` .

### <a name="module-experience-improvements"></a>Verbeteringen in module-ervaring

Windows Power Shell 3,0 biedt ondersteuning voor geavanceerde functies voor modules, waaronder de volgende nieuwe functies.

1. Module logboek registratie voor afzonderlijke modules (LogPipelineExecutionDetails) en de nieuwe instelling voor het inschakelen van module logboek registratie groepsbeleid
2. Uitgebreide module objecten die de waarden uit het module manifest beschikbaar maken
3. Nieuwe **ExportedCommands** -eigenschap van modules, inclusief geneste modules, waarmee opdrachten van alle typen worden gecombineerd
4. Verbeterde detectie van beschik bare (niet-geïmporteerde) modules, inclusief het toestaan van de para meters **Path** en **ListAvailable** in dezelfde opdracht
5. Nieuwe **DefaultCommandPrefix** -sleutel in module manifesten die geen naam conflicten voor komen zonder module code te wijzigen.
6. Verbeterde module vereisten, met inbegrip van volledig gekwalificeerde vereiste modules met versie en GUID en automatische invoer van vereiste modules
7. Stillere, gestroomlijnde werking van de `New-ModuleManifest` cmdlet.
8. Nieuwe **module** parameter voor #Requires
9. De `Import-Module` cmdlet is verbeterd met de para meters **MinimumVersion** en **RequiredVersion** .

### <a name="simplified-command-discovery"></a>Vereenvoudigde opdracht detectie

U hoeft niet langer alle modules te importeren om de opdrachten te ontdekken die beschikbaar zijn voor uw sessie. In Windows Power Shell 3,0 worden `Get-Command` alle opdrachten van alle geïnstalleerde modules opgehaald met de cmdlet. En als u een opdracht gebruikt, wordt de module die de opdracht exporteert automatisch geïmporteerd in uw sessie.

De nieuwe `Show-Command` cmdlet is speciaal ontworpen voor beginners. U kunt zoeken naar opdrachten in een venster. U kunt alle opdrachten weer geven of filteren op module, een module importeren door te klikken op een knop, tekst vakken en vervolg keuzelijsten gebruiken om een geldige opdracht te maken en de opdracht vervolgens te kopiëren of uit te voeren zonder het venster te verlaten.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Verbeterde ondersteuning voor logboek registratie, diagnostiek en groepsbeleid

Windows Power Shell 3,0 verbetert de ondersteuning voor logboek registratie en tracering voor opdrachten en modules, met ondersteuning voor gebeurtenis tracering in Windows (ETW)-logboeken, een Bewerk bare **LogPipelineExecutionDetails** -eigenschap van modules en de instelling logboek registratie inschakelen Groepsbeleid. U kunt nu parameter waarden uit logboek gegevens ophalen door de logboek eigenschappen weer te geven.

### <a name="formatting-and-output-improvements"></a>Verbeteringen in de opmaak en uitvoer

Dankzij de nieuwe opmaak-en uitvoer verbeteringen wordt de efficiëntie van alle Windows Power shell-gebruikers verbeterd. De verbeteringen omvatten uitvoer omleiding voor alle stromen, een uitgebreide cmdlet voor update typen waarmee typen dynamisch worden toegevoegd zonder indeling. ps1xml-bestanden, tekst omloop in uitvoer, standaard opmaak eigenschappen van aangepaste objecten, het type **PSCustomObject** , verbeterde opmaak voor WMI-objecten en heterogene objecten, en ondersteuning voor het detecteren van overbelasting van de methode.

### <a name="enhanced-console-host-experience"></a>Verbeterde beleving van de console-host

Het Windows Power shell-console-hostprogramma beschikt over nieuwe functies in Windows Power Shell 3,0, waaronder Apartment met één thread. Met de nieuwe optie uitvoeren met Power shell in Verkenner kunt u scripts uitvoeren in een onbeperkte sessie, alleen door met de rechter muisknop te klikken. Met de nieuwe logica voor het starten van de console-host wordt Windows Power shell sneller gestart en met nieuwe letter typen kunt u de bekende ervaring van het console venster personaliseren.

### <a name="new-cmdlet-and-hosting-apis"></a>Nieuwe cmdlet-en hosting-Api's

De nieuwe cmdlet-API en hosting-API omvatten open bare geavanceerde syntaxis structuur (AST) Api's en Api's voor het pagineren van pijp lijnen, geneste pijp lijnen, het tabblad voltooiing van runs Pace, Windows RT, het verouderde cmdlet-kenmerk en de verb-en zelfstandige eigenschappen van het object FunctionInfo.

### <a name="performance-improvements"></a>Verbeterde prestaties

Belang rijke prestatie verbeteringen in Windows Power shell zijn afkomstig van de nieuwe taal-parser, die is gebouwd op dynamische runtime Language (DLR) in .NET Framework 4. samen met compilatie van het runtime-script, verbeteringen van de prestaties van de engine en wijzigingen in het algoritme van de `Get-ChildItem` die de prestatie verbeteren, met name bij het zoeken naar netwerk shares.

### <a name="runas-and-shared-host-support"></a>Ondersteuning voor runas en gedeelde host

Windows Power Shell 3,0 bevat ondersteuning voor runas-en shared host-functies.

Met de functie *runas* , ontworpen voor Windows Power shell-werk stroom, kunnen gebruikers van een sessie configuratie sessies maken die worden uitgevoerd met de machtiging van een gedeeld gebruikers account. Hierdoor kunnen gebruikers met minder bevoegdheden bepaalde opdrachten en scripts uitvoeren met beheerders machtigingen en de nood zaak voor het toevoegen van minder Senior gebruikers aan de groep Administrators verminderen.

Met de functie **SharedHost** kunnen meerdere gebruikers op meerdere computers gelijktijdig verbinding maken met een werk stroom sessie en de voortgang van een werk stroom controleren. Gebruikers kunnen een werk stroom starten op de ene computer en vervolgens verbinding maken met de werk stroom sessie op een andere computer zonder de verbinding van de oorspronkelijke computer te verbreken. Gebruikers moeten dezelfde machtigingen hebben en dezelfde sessie configuratie gebruiken. Zie ' een Windows Power shell-werk stroom uitvoeren ' in aan de slag met Windows Power shell-werk stroom voor meer informatie.

### <a name="special-character-handling-improvements"></a>Verbeteringen voor speciale teken verwerking

Voor het verbeteren van de mogelijkheden van Windows Power Shell 3,0 het interpreteren en goed verwerken van speciale tekens, is de para meter **LiteralPath** , die speciale tekens in paden verwerkt, geldig op bijna alle cmdlets die de para meter **Path** hebben, inclusief de nieuwe `Update-Help` en `Save-Help` cmdlets. De parser bevat ook speciale logica voor het verbeteren van de verwerking van het apostroffen teken ( \` ) en vier Kante haken in bestands namen en paden.

## <a name="see-also"></a>Zie ook

- [about_Windows_PowerShell_5.0](/previous-versions/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
