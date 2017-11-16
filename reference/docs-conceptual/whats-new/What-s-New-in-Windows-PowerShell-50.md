---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Wat is er nieuw in Windows PowerShell 5.0
ms.openlocfilehash: 3a412b35c593c99fb8ea8307b12ccc05871863f4
ms.sourcegitcommit: e2360ac94fe4deb0ed0f5c8c8d9b293551ec8030
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/05/2017
---
# <a name="whats-new-in-windows-powershell-50"></a>Wat is er nieuw in Windows PowerShell 5.0
Windows PowerShell 5.0 bevat belangrijke nieuwe functies die het gebruik ervan uitbreiden, de bruikbaarheid verbeteren en kunnen u bepalen en beheren van Windows-omgevingen gemakkelijker en uitvoerig.

Windows PowerShell 5.0 is achterwaarts compatibel. Cmdlets, providers, modules, -modules, scripts, functies en -profielen die zijn ontworpen voor Windows PowerShell 4.0, Windows PowerShell 3.0 en Windows PowerShell 2.0 in het algemeen kunt u werken in Windows PowerShell 5.0 zonder wijzigingen.

# <a name="installing-windows-powershell"></a>Windows PowerShell installeren
Windows PowerShell 5.0 wordt standaard geïnstalleerd op Windows Server 2016 Technical Preview en Windows 10. 

Windows PowerShell 5.0 installeren op Windows Server 2012 R2, Windows 8.1 Enterprise of Windows 8.1 Pro, downloaden en installeren [Windows Management Framework 5.0](http://aka.ms/wmf5download). Zorg ervoor dat de details van de download te lezen en voldoen aan alle systeemvereisten voordat u Windows Management Framework 5.0 installeert.

## <a name="in-this-topic"></a>In dit onderwerp

- [Windows PowerShell 4.0 DSC-updates in KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nieuwe functies in Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nieuwe functies in Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nieuwe functies in Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Updatepakket voor Windows PowerShell 4.0-updates in November 2014 (KB 3000850)
Veel updates en verbeteringen voor Windows PowerShell Desired State Configuration (DSC) in Windows PowerShell 4.0 zijn beschikbaar in de [updatepakket van November 2014 voor Windows RT 8.1, Windows 8.1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). U kunt bepalen of KB 3000850 is geïnstalleerd op uw systeem door het uitvoeren van `Get-Hotfix -Id KB3000850` in Windows PowerShell.

- Updates voor bestaande cmdlets in de [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) module

    -   [Get-DscResource](http://technet.microsoft.com/library/dn521625.aspx) sneller (met name in ISE).

    -   [Start DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) heeft een nieuwe parameter, - UseExisting, die de laatst toegepaste configuratie wordt opnieuw toegepast.

    -   [Start DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) -Force is opgelost.

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) nuttiger geeft informatie weer over de status van de engine.

    -   [Test DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) nu de naam van de computer samen met waar of onwaar retourneert.

    -   [Nieuwe DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) ondersteunt nu het UNC-paden.

- Nieuwe cmdlets in de [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) module

    -   [Update DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx): een controle op aanvraag pull-server uitgevoerd.

    -   [Stop DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx): Hiermee stopt u een configuratie die al wordt uitgevoerd.

    -   [Verwijder DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx): kunt u het verwijderen van configuratiedocumenten in verschillende stadia (in behandeling, vorige of huidige).

- Taal-verbeteringen

    -   DependsOn biedt nu ondersteuning voor samengestelde bronnen.

    -   DependsOn ondersteunt nu de cijfers in namen van de resource-exemplaar.

    -   Knooppuntexpressies die niet langer worden geëvalueerd tot leeg Veroorzaak fouten.

    -   Een fout die optreedt als een knooppunt-expressie in een leeg resulteert is opgelost.

    -   Aanroepen van configuraties nu configuraties werken in de Windows PowerShell-console.

- Verbeteringen voor pull-modus

    -   Pull-modus ondersteunt nu alle ZIP-bestanden.

    -   **AllowModuleOverwrite** nu correct werkt.

- Verbeterde tolerantie

    -   Nieuwe **fouten opsporen-modus** kunt u het laden van de resource-modules.

    -   Als een configuratiefout optreedt, wordt het bestand pending.mof niet verwijderd.

    -   De lokale Configuration Manager (LCM) is nu toleranter wanneer metaconfiguratie instellingen zijn beschadigd.

- Diagnostische verbeteringen

    -   Een waarschuwing wordt weergegeven wanneer de LCM wordt de timer ingesteld op andere instellingen dan u hebt opgegeven.

    -   Logboekbestanden van de fout bevat nu de aanroepstack voor Windows PowerShell-bronnen.

- Flexibiliteit verbeteringen

    -   De resource LocalConfigurationManager heeft een nieuwe eigenschap **ActionAfterReboot**.

        -   ContinueConfiguration (standaardwaarde): een configuratie automatisch hervat nadat een doelknooppunt opnieuw is opgestart.

        -   StopConfiguration: Niet automatisch een configuratie opnieuw nadat een knooppunt opnieuw wordt opgestart.

    -   Een consistentiecontrole uitvoeren kan nu vaker dan een PULL-bewerking of vice versa.

    -   Ondersteuning voor versiebeheer: DSC herkent nu een document dat is gegenereerd op een nieuwere client (opgenomen in [WMF 5.0](http://aka.ms/wmf5download)).

- Fout preventie verbeteringen

    -   Moduleversie wordt nu afgedwongen voordat een configuratie is toegepast.

    -   **DebugPreference** nu juist is ingesteld voor Get, instellen of Test TargetResource aanroepen.

- Referentie verbeteringen verwerken

    -   Een certificaat wordt nu gebruikt als beide **certificaat** en **PSDscAllowPlainTextPassword** zijn opgegeven.

    -   Referenties worden ontsleuteld, zelfs voor Get-TargetResource.

    -   Metaconfiguratie referenties zijn versleuteld en ontsleuteld.

    -   PSCredentials zijn nu ontsleuteld wanneer ze zich in een ingesloten object.

- Verbeteringen van de ingebouwde resource

    -   De pakket-resource

        -   Het verkeerde pakket niet meer is geïnstalleerd (vanaf de lokale of webbronnen).

        -   Biedt nu ondersteuning voor HTTPS.

    -   Er is nu ondersteuning voor HTTPS in de [resource van het pakket](http://technet.microsoft.com/library/dn282132.aspx).

    -   [Archiveren van resource](http://technet.microsoft.com/library/dn249917.aspx) biedt nu ondersteuning voor referenties.

## <a name="new-features-in-windows-powershell-50"></a>Nieuwe functies in Windows PowerShell 5.0

- [Nieuwe functies in Windows PowerShell](#new-features-in-windows-powershell)
- [Nieuwe functies in Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nieuwe functies in Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nieuwe functies in Windows PowerShell-webservices](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Opmerkelijke oplossingen voor problemen in Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nieuwe functies in Windows PowerShell

- U start in Windows PowerShell 5.0, kunt u ontwikkelen met behulp van klassen, met behulp van formele syntaxis en de semantiek die vergelijkbaar met andere objectgeoriënteerde programmeertalen zijn. **Klasse**, **Enum**, en andere sleutelwoorden zijn toegevoegd aan de Windows PowerShell-taal voor de ondersteuning van de nieuwe functie. Zie voor meer informatie over het werken met klassen about_Classes.

- Windows PowerShell 5.0 introduceert een nieuwe, gestructureerde gegevensstroom die u gebruiken kunt voor het verzenden van gestructureerde gegevens tussen een script en de aanroepfuncties (of hostingomgeving). U kunt nu Write-Host gebruiken voor het verzenden van uitvoer naar de gegevensstroom. Informatiestromen werkt ook voor PowerShell.Streams, taken, geplande taken en werkstromen. De volgende functies ondersteunen de gegevensstroom.

    -   Een nieuwe cmdlet met schrijven informatie waarmee u kunt opgeven hoe de stroom van gegevens voor een opdracht worden verwerkt in Windows PowerShell. Write-Host is een wrapper voor Write-informatie. Write-informatie is ook een ondersteunde workflow-activiteit.

    -   Twee nieuwe algemene parameters, InformationVariable en InformationAction, kunnen u bepalen hoe gegevensstromen van een opdracht worden weergegeven. Geldige waarden voor InformationAction zijn SilentlyContinue, stoppen, doorgaan, opvragen, negeren of onderbreken met SilentlyContinue wordt de standaardwaarde. InformationVariable geeft een tekenreeks als de naam van een variabele waarnaar de gegevens Write-Host van een opdracht die is opgeslagen.

    -   Een nieuwe voorkeursvariabele InformationPreference, bevat uw standaardvoorkeur voor de stroom van gegevens in een Windows PowerShell-sessie. De standaardwaarde is SilentlyContinue.

    -   Twee nieuwe werkstroom algemene parameters, PSInformation en InformationAction, er zijn toegevoegd.

    -   Wanneer u de opdracht Format-Table, worden tabelkolommen nu automatisch ingedeeld door de eerste 300ms van gegevens die door de stroom te evalueren.

- In samenwerking met [Microsoft Research](http://research.microsoft.com/), een nieuwe cmdlet ConverterenVan-tekenreeks is toegevoegd. ConverterenVan-tekenreeks kunt u uitpakken en parseren van gestructureerde objecten uit de inhoud van tekenreeksen. Zie voor meer informatie ConverterenVan-tekenreeks.

- Een nieuwe cmdlet voor het omzetten van tekenreeks automatisch op basis van een voorbeeld die u in het voorbeeld van de parameter opgeeft - tekst opgemaakt.

- Microsoft.PowerShell.Archive, een nieuwe module bevat cmdlets waarmee u Comprimeer bestanden en mappen in (ook wel bekend als ZIP)-archiefbestanden uitpakken van bestaande ZIP-bestanden en ZIP-bestanden met nieuwere versies van bestanden die gecomprimeerd binnen deze bijwerken.

- Een nieuwe module PackageManagement, kunt u detecteren en software-updatepakketten installeren op het Internet. De module PackageManagement (voorheen bekend als OneGet) is een manager of multiplexer van bestaande pakket managers (ook wel pakket providers) consistent beheer van Windows-pakket met een enkel Windows PowerShell-interface.

- Een nieuwe module PowerShellGet, kunt u vinden, installeren, publiceren en bijwerken van modules en DSC-resources op de [PowerShell Gallery](http://www.powershellgallery.com/), of op een interne module-opslagplaats die u instellen kunt door de cmdlet Register-PSRepository.

- Een nieuw taal trefwoord **Hidden**, is toegevoegd om op te geven dat een lid (een eigenschap of een methode) niet wordt weergegeven in de resultaten van de Get-lid standaard (tenzij u de parameter - Force). Eigenschappen en methoden die verborgen zijn gemarkeerd worden ook niet weergegeven in de resultaten van de IntelliSense, tenzij u in een context waarin het lid weergegeven worden moet; bijvoorbeeld, de automatische variabelen $dit verborgen leden in de klassenmethode moet worden weergegeven.

- Nieuw Item, Item verwijderen en Get-ChildItem zijn uitgebreid ter ondersteuning van maken en beheren van [symbolische koppelingen](http://en.wikipedia.org/wiki/Symbolic_link). De **- ItemType** voor nieuw Item-parameter accepteert een nieuwe waarde **SymbolicLink**. U kunt nu symbolische koppelingen maken op een enkele regel door de cmdlet New-Item.

- Get-ChildItem heeft ook een nieuwe - diepte parameter, die u met de - Recurse-parameter gebruiken om te beperken van de recursie. Bijvoorbeeld: Get-ChildItem-Recurse - diepte 2 resultaten retourneert uit de huidige map alle van de onderliggende mappen in de huidige map en alle mappen in de onderliggende mappen.

- Copy-Item nu kunt u bestanden of mappen vanuit een Windows PowerShell-sessie naar de andere kopiëren, wat betekent dat u kunt bestanden kopiëren naar sessies die zijn verbonden met externe computers (met inbegrip van computers met [Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), en Daarom hebben geen andere interface). Om bestanden te kopiëren, PSSession-id's opgeven als de waarde van de nieuwe parameters voor FromSession - en - ToSession en voeg - pad en - doel oorsprongpad op te geven en de bestemming, respectievelijk. Bijvoorbeeld: Copy-Item-pad c:\\mijnbestand.txt - ToSession $s-bestemming d:\\doelmap.

- Windows PowerShell schrijffouten is verbeterd om toe te passen op alle hosting toepassingen (zoals Windows PowerShell ISE) naast de console-host (**powershell.exe**). Schrijffouten-opties (waaronder het inschakelen van de tekst van een hele systeem) kunnen worden geconfigureerd door het inschakelen van de **PowerShell schrijffouten inschakelen** groepsbeleidsinstelling in beheerdersrechten sjablonen/Windows-onderdelen/Windows gevonden PowerShell.

- Een nieuwe gedetailleerde script traceringsfunctie stelt u gedetailleerde bijhouden en analyseren van Windows PowerShell scripts gebruiken op een systeem. Nadat u gedetailleerde script tracering ingeschakeld, Windows PowerShell alle scriptblokken registreert in het gebeurtenislogboek Event Tracing voor Windows (ETW) **Microsoft-Windows-PowerShell/operationeel**.

- U start in Windows PowerShell 5.0, nieuwe Cryptographic Message Syntax cmdlets ondersteuning voor versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het beveiligen van berichten cryptografisch zoals beschreven door [RFC5652](http://tools.ietf.org/html/rfc5652). De cmdlets Get-CmsMessage beveiligen CmsMessage en Unprotect CmsMessage zijn toegevoegd aan de [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) module.

- Nieuwe cmdlets in de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module, Get-Runspace foutopsporing Runspace, Get-RunspaceDebug, Enable RunspaceDebug en Disable-RunspaceDebug, kunnen u foutopsporingsopties instellen op een runspace en starten en stoppen foutopsporing op een runspace. Voor het opsporen van willekeurige runspaces ' dat wil zeggen runspaces die niet de standaard runspace voor een Windows PowerShell-console of Windows PowerShell ISE sessie ' 'Windows PowerShell kunt u onderbrekingspunten instellen in een script, en hebt toegevoegd onderbrekingspunten stopt het script uit actief totdat u een foutopsporingsprogramma fouten opsporen in het script runspace kan koppelen. Ondersteuning voor geneste foutopsporing voor willekeurige runspaces is toegevoegd aan de Windows PowerShell-Scriptdebugger voor runspaces.

- Een nieuwe indeling Hex-cmdlet is toegevoegd aan de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module. Indeling Hex kunt u tekst of binaire gegevens weergeven in hexadecimale notatie.

- Klembord GET en Set-Klembord-cmdlets zijn toegevoegd aan de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module; ze vereenvoudigen de overdracht van inhoud naar en van een Windows PowerShell-sessie. De Klembord-cmdlets ondersteunen afbeeldingen, audio-bestanden, bestandslijsten en tekst.

- Een nieuwe cmdlet Clear-RecycleBin is toegevoegd aan de [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) module; deze lege cartridges die cmdlet blijven de Recycle Bin voor een vast station, waaronder externe stations. Standaard wordt u gevraagd om te bevestigen dat een opdracht wissen RecycleBin omdat de eigenschap ConfirmImpact van de cmdlet is ingesteld op ConfirmImpact.High.

- Een nieuwe cmdlet New-TemporaryFile, maakt u een tijdelijk bestand als onderdeel van het uitvoeren van scripts. Standaard wordt het nieuwe tijdelijke bestand gemaakt ```C:\Users\<user name>\AppData\Local\Temp```.

- De Out-File, Add-inhoud en Set-inhoud cmdlets hebt nu een nieuwe NoNewline - parameter die een nieuwe regel na de uitvoer wordt weggelaten.

- De cmdlet New-Guid maakt gebruik van de .NET Framework-Guid-klasse voor het genereren van een GUID zijn, is nuttig wanneer u bij het schrijven van scripts of DSC-resources.

- Omdat informatie over de bestandsversie misleidend, is met name als er een bestand is hersteld, zijn eigenschappen van nieuwe FileVersionRaw en ProductVersionRaw script beschikbaar voor FileInfo objecten. Bijvoorbeeld, kunt u uitvoeren de volgende opdracht om de waarden van deze eigenschappen voor powershell.exe, weer te geven waar $pid de proces-ID bevat voor een actieve sessie van Windows PowerShell:```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```

- Nieuwe cmdlets Enter PSHostProcess en afsluiten PSHostProcess kunt u Windows PowerShell-scripts in processen die gescheiden van het huidige proces dat wordt uitgevoerd in de Windows PowerShell-console voor foutopsporing. Uitvoeren van de Enter-PSHostProcess invoeren of koppelen aan een specifiek proces-ID en voer Get-Runspace om te retourneren van de actieve runspaces binnen het proces. Exit-PSHostProcess ontkoppelen van het proces, wanneer u hebt het script in het proces voor foutopsporing worden uitgevoerd.

- Een nieuwe cmdlet in de wacht-foutopsporing is toegevoegd aan de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module. Wacht-foutopsporing om te stoppen van een script in het foutopsporingsprogramma voordat u de volgende instructie in het script uitvoert, kunt u uitvoeren.

- Het foutopsporingsprogramma van Windows PowerShell Workflow biedt nu ondersteuning voor voltooiing opdracht of tabblad en u kunt fouten opsporen geneste werkstroom functies. U kunt nu ook op **Ctrl + Break** het foutopsporingsprogramma invoeren in een script wordt uitgevoerd, in zowel lokale als externe sessies en in een werkstroomscript.

- Een cmdlet Debug-Job is toegevoegd aan de [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) module fouten opsporen in actieve taak scripts voor Windows PowerShell Workflow, achtergrond en taken in externe sessies worden uitgevoerd.

- Een nieuwe status AtBreakpoint, is toegevoegd voor Windows PowerShell-taken. De status van de AtBreakpoint van toepassing als een taak is met een script dat set onderbrekingspunten bevat en het script een onderbrekingspunt heeft bereikt. Wanneer een taak is gestopt op een onderbrekingspunt foutopsporing, moet u de taak door de cmdlet Debug-Job fouten opsporen.

- Windows PowerShell 5.0 implementeert ondersteuning voor meerdere versies van een enkel Windows PowerShell-module in dezelfde map in $PSModulePath. Een eigenschap RequiredVersion is toegevoegd aan de klasse ModuleSpecification om u te helpen krijgt u de gewenste versie van een module. Deze eigenschap is wederzijds uitsluitend met de eigenschap ModuleVersion. RequiredVersion wordt nu ondersteund als onderdeel van de waarde van de parameter FullyQualifiedName van Get-Module Import-Module en Remove-Module-cmdlets.

- U kunt nu module versie validatie uitvoeren door de cmdlet Test-ModuleManifest.

- Resultaten van de cmdlet Get-Command nu weergeven een kolom versie; een nieuwe versie-eigenschap is toegevoegd aan de klasse CommandInfo. GET-opdracht bevat opdrachten van meerdere versies van dezelfde module. De eigenschap Version maakt ook deel uit van afgeleide klassen van CmdletInfo: CmdletInfo en ApplicationInfo.

- GET-opdracht heeft een nieuwe parameter, - ShowCommandInfo, waarmee PSObjects ShowCommand-gegevens geretourneerd. Dit is vooral nuttig functionaliteit voor wanneer opdracht weergeven met behulp van Windows PowerShell op afstand wordt uitgevoerd in Windows PowerShell ISE. De parameter - ShowCommandInfo vervangt de bestaande Get-SerializedCommand-functie in de module Microsoft.PowerShell.Utility, maar het script Get-SerializedCommand is nog steeds beschikbaar voor de ondersteuning voor downlevel-scripts.

- Een nieuwe Get-ItemPropertyValue-cmdlet kunt u profiteren van de waarde van een eigenschap zonder puntnotatie te gebruiken. In oudere versies van Windows PowerShell kunt u bijvoorbeeld de volgende opdracht om de waarde van de eigenschap toepassingsbasis van de registersleutel PowerShellEngine uitvoeren: **(Get-ItemProperty-pad HKLM:\\SOFTWARE\\ Microsoft\\PowerShell\\3\\PowerShellEngine-naam van de ApplicationBase). ApplicationBase**. U start in Windows PowerShell 5.0, u kunt uitvoeren **Get-ItemPropertyValue-pad HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine-naam ApplicationBase** .

- De Windows PowerShell-console gebruikt nu de syntaxis van de kleuren, net zoals in de Windows PowerShell ISE.

- Een nieuwe NetworkSwitch-module bevat cmdlets waarmee u kunt de switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie van toepassing op Windows Server 2012 R2-logo gecertificeerde netwerkswitches.

- De parameter FullyQualifiedName in Import-Module en Remove-Module-cmdlets toegevoegd ter ondersteuning van meerdere versies van de module voor een enkele opslaan.

- Help opslaan, Update-Help, Import-PSSession, Export-PSSession en Get-Command hebben een nieuwe parameter, FullyQualifiedModule van het type ModuleSpecification. Deze parameter om op te geven van een module met de volledig gekwalificeerde naam toevoegen.

- De waarde van **$PSVersionTable.PSVersion** is bijgewerkt naar 5.0.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nieuwe functies in Windows PowerShell Desired State Configuration

- Verbeteringen van de taal van Windows PowerShell kunnen u Windows PowerShell Desired State Configuration (DSC) resources met behulp van klassen definiëren. Importeren DscResource is nu een waar dynamische sleutelwoord; Windows PowerShell parseert de opgegeven module'™ s root-module, zoeken naar klassen die het kenmerk DscResource bevatten. U kunt nu klassen gebruiken voor het definiëren van DSC-resources die geen een MOF-bestand of een submap DSCResource in de modulemap vereist is. Een bestand van Windows PowerShell-module kan meerdere DSC-resource klassen bevatten.

- Een nieuwe parameter, ThrottleLimit, is toegevoegd aan de volgende cmdlets in de module PSDesiredStateConfiguration. De parameter ThrottleLimit Geef het aantal doelcomputers of apparaten waarop u de opdracht te laten werken op hetzelfde moment wilt toevoegen.

    -   Get-DscConfiguration

    -   Get-DscConfigurationStatus

    -   Get-DscLocalConfigurationManager

    -   Restore DscConfiguration

    -   Test DscConfiguration

    -   Vergelijken DscConfiguration

    -   Publiceren DscConfiguration

    -   Set-DscLocalConfigurationManager

    -   Start DscConfiguration

    -   Update DscConfiguration

- Met het centrale DSC foutrapportage, is uitgebreide informatie over fouten niet alleen geregistreerd in de event log, maar het kan worden verzonden naar een centrale locatie voor latere analyse. U kunt deze centrale locatie voor het opslaan van de DSC configuratiefouten die zijn opgetreden voor elke server in hun omgeving. Nadat de rapportserver is gedefinieerd in het meta-configuratie, worden alle fouten verzonden naar de rapportserver en vervolgens worden opgeslagen in een database. U kunt deze functionaliteit ongeacht of er een doelknooppunt is geconfigureerd voor het ophalen van de configuraties van een pull-server instellen.

- Verbeteringen in Windows PowerShell ISE vereenvoudigen ontwerpen van DSC-resource. U kunt nu het volgende doen.

    -   Lijst van alle DSC-resources binnen een **configuratie** of **knooppunt** blok door te voeren **Ctrl + spatiebalk** op een lege regel in het blok.

    -   Automatisch aanvullen van resource-eigenschappen van de **opsomming** type.

    -   Automatisch aanvullen in de **DependsOn** eigenschap van DSC-resources op basis van andere exemplaren resource in de configuratie.

    -   Verbeterde tab-aanvulling van de waarden van de resource-eigenschap.

- Een gebruiker kan nu uitvoeren van een bron op onder een opgegeven set referenties door toe te voegen de **PSDscRunAsCredential** kenmerk aan een knooppunt-blok. Bijvoorbeeld: PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Deze functionaliteit is handig voor het maken van de configuraties die bij het uitvoeren van Windows Installer en uitvoerbare installatieprogramma's, toegang tot de registercomponent per gebruiker of andere taken buiten de huidige gebruikerscontext.

- Er is ondersteuning voor 32-bits (x86 86) toegevoegd voor de **configuratie** sleutelwoord.

- Windows PowerShell biedt nu ondersteuning voor aangepaste help voor DSC-configuraties, gedefinieerd door toe te voegen \[CmdletBinding()] voor de functie gegenereerde configuratie.

- Een nieuwe **DscLocalConfigurationManager** kenmerk wordt aangegeven dat een configuratie-blok een meta-configuratie, die wordt gebruikt voor het configureren van de DSC Local Configuration Manager. Dit kenmerk wordt beperkt van een configuratie met alleen de items die DSC Local Configuration Manager configureren. Tijdens de verwerking deze configuratie genereert een \*. meta.mof-bestand dat wordt verzonden naar de juiste doelknooppunten door de cmdlet Set-DscLocalConfigurationManager.

- Gedeeltelijke configuraties zijn nu toegestaan in Windows PowerShell 5.0. U kunt configuratiedocumenten leveren aan een knooppunt in fragmenten. Voor een knooppunt voor het ontvangen van meerdere fragmenten van een configuratie-document, het knooppunt '™ s Local Configuration Manager moet eerst worden ingesteld om op te geven van de verwachte fragmenten

- Synchronisatie van cross-computer is nieuw in DSC in Windows PowerShell 5.0. Met behulp van de ingebouwde WaitFor\* resources (**WaitForAll**, **WaitForAny**, en **WaitForSome**), kunt u nu afhankelijkheden opgeven op computers tijdens de configuratie wordt uitgevoerd, zonder externe integraties. Deze resources bieden knooppunt naar synchronisatie met behulp van CIM-verbindingen via het protocol WS-Man. Een configuratie kan wachten op een andere computer'™ s bronstatus te wijzigen.

- Net genoeg Administration (JEA), een nieuwe overdracht beveiligingsfunctie, maakt gebruik van DSC en Windows PowerShell beperkte runspaces ondernemingen kunnen helpen beveiligen van inbreuk door werknemers, of verlies van gegevens of opzettelijk of met opzet. Zie voor meer informatie over JEA, met inbegrip van waar u de resource xJEA DSC kunt downloaden [net genoeg beheer van de stap voor stap](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).

- De volgende nieuwe cmdlets zijn toegevoegd aan de module PSDesiredStateConfiguration.

    -   Een nieuwe Get-DscConfigurationStatus-cmdlet haalt informatie op hoog niveau over de configuratiestatus van de uit een doelknooppunt. Kunt u de status van de laatste of alle configuraties.

    -   Een nieuwe vergelijken DscConfiguration cmdlet vergelijkt een opgegeven configuratie met de huidige status van een of meer doelknooppunten.

    -   Een nieuwe publiceren DscConfiguration cmdlet een MOF-bestand voor configuratie gekopieerd naar een target-knooppunt, maar de configuratie is niet van toepassing. De configuratie is toegepast tijdens de volgende fase van de consistentie, of wanneer u de cmdlet Update DscConfiguration uitvoeren.

    -   Een nieuwe Test DscConfiguration cmdlet kunt u controleren of een resulterende configuratie overeenkomt met de gewenste configuratie, retourneert waar als de configuratie komt overeen met de gewenste configuratie of ONWAAR als de configuratie van de werkelijke niet overeenkomt met de gewenste de configuratie.

    -   Een nieuwe Update DscConfiguration cmdlet zorgt ervoor dat een configuratie moeten worden verwerkt. Als de lokale Configuration Manager in de pull-modus is, krijgt de cmdlet de configuratie van de pull-server voordat dit wordt toegepast.

### <a name="new-features-in-windows-powershell-ise"></a>Nieuwe functies in Windows PowerShell ISE

- U kunt nu externe Windows PowerShell-scripts en bestanden in een lokale kopie van Windows PowerShell ISE bewerken door te voeren Enter-PSSession naar een externe sessie starten op de computer die '™ s opslaan van de bestanden die u wilt bewerken en vervolgens voert **PSEdit <path and file name on the remote computer>**. Deze functie kan vergemakkelijken bewerken Windows PowerShell-bestanden die zijn opgeslagen op de Server Core-installatieoptie van Windows Server, waarbij Windows PowerShell ISE kan niet worden uitgevoerd.

- De cmdlet Start-de tekst wordt nu ondersteund in Windows PowerShell ISE.

- U kunt nu externe scripts in Windows PowerShell ISE voor foutopsporing.

- Een nieuwe opdracht, **alle opsplitsen** (Ctrl + B), wordt in het foutopsporingsprogramma voor zowel lokale als extern uitvoeren van scripts.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nieuwe functies in Windows PowerShell Web Services (Management OData IIS-extensie)

- U start in Windows PowerShell 5.0, kunt u een set Windows PowerShell-cmdlets die zijn gebaseerd op de functionaliteit die door een bepaalde OData-eindpunt beschikbaar gesteld door de cmdlet Export-ODataEndpointProxy, gevonden in de nieuwe genereren [ Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) module.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Opmerkelijke oplossingen voor problemen in Windows PowerShell 5.0

- Windows PowerShell 5.0 bevat een nieuw COM-implementatie die aanzienlijke prestatieverbeteringen biedt wanneer u met COM-objecten werkt. Zie voor een videodemonstratie van het effect [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ).

- Aanzienlijke prestatieverbeteringen hebt aangebracht om de eerste tab-Aanvulling in een Windows PowerShell-sessie tabblad voltooiingstijd verkorten door bijna 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nieuwe functies in Windows PowerShell 4.0
Windows PowerShell 4.0 is achterwaarts compatibel. Cmdlets, providers, modules, -modules, scripts, functies en -profielen die zijn ontworpen voor Windows PowerShell 3.0 en Windows PowerShell 2.0 werken in Windows PowerShell 4.0 zonder wijzigingen.

Windows PowerShell 4.0 wordt standaard geïnstalleerd op Windows 8.1 en Windows Server 2012 R2. Voor het installeren van Windows PowerShell 4.0 in Windows 7 met SP1 of Windows Server 2008 R2, downloaden en installeren [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Zorg ervoor dat de details van de download te lezen en voldoen aan alle systeemvereisten voordat u Windows Management Framework 4.0 installeren.

- [Nieuwe functies in Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nieuwe functies in Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nieuwe functies in Windows PowerShell Workflow](#new-features-in-windows-powershell-workflow)
- [Nieuwe functies in Windows PowerShell-webservices](#new-features-in-windows-powershell-web-services)
- [Nieuwe functies in Windows PowerShell-webtoegang](#new-features-in-windows-powershell-web-access)
- [Opmerkelijke oplossingen voor problemen in Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 omvat de volgende nieuwe functies.

### <a name="new-features-in-windows-powershell"></a>Nieuwe functies in Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) is een nieuw managementsysteem in Windows PowerShell 4.0 waarmee de implementatie en beheer van configuratiegegevens voor softwareservices en de omgeving waarin deze services worden uitgevoerd. Zie voor meer informatie over DSC [aan de slag met Windows PowerShell Desired State Configuration](https://technet.microsoft.com/en-us/library/c134aa32-b085-4656-9a89-955d8ff768d0).

- **Help opslaan** nu kunt u de help voor modules die zijn geïnstalleerd op externe computers opslaan. U kunt Help opslaan module Help downloaden vanuit een internetverbinding client (waarvoor niet alle modules waarvoor u hulp wilt worden altijd geïnstalleerd) en kopieer de opgeslagen Help voor een externe gedeelde map of een externe computer waarop geen Internet toegang.

- De Windows PowerShell-foutopsporing is verbeterd zodat u foutopsporing van Windows PowerShell-werkstromen als scripts die worden uitgevoerd op externe computers. Windows PowerShell-werkstromen kunnen nu fouten worden opgespoord op het scriptniveau van het uit de Windows PowerShell-opdrachtregel- of Windows PowerShell ISE. Windows PowerShell-scripts, met inbegrip van scriptwerkstromen, kunnen nu fouten worden opgespoord via externe sessies. Externe foutopsporing sessies blijven behouden via Windows PowerShell-sessies die worden losgekoppeld en later opnieuw verbinding gemaakt.

- Een **RunNow** parameter voor **Register-ScheduledJob** en **Set-ScheduledJob** hoeven in te stellen van een onmiddellijke startdatum en tijd voor taken met behulp van de **Trigger** parameter.

- **Invoke-RestMethod** en **Invoke-WebRequest** nu kunt u alle koppen instellen met behulp van de parameter Headers. Hoewel deze parameter altijd bestonden is, is een van de verschillende parameters voor de web-cmdlets dat heeft geresulteerd in fouten of uitzonderingen.

- **Get-Module** heeft een nieuwe parameter **FullyQualifiedName**, van het type **ModuleSpecification\[]**. De **FullyQualifiedName** parameter van Get-Module nu kunt u opgeven van een module met behulp van de module-naam, versie en eventueel de GUID.

- De standaardinstelling voor het beleid van kan worden uitgevoerd op Windows Server 2012 R2 is **RemoteSigned**. Op Windows 8.1 is er geen wijziging in te stellen.

- U start in Windows PowerShell 4.0, wordt methodeaanroep met behulp van dynamische methodenamen ondersteund. U kunt het gebruik van een variabele voor het opslaan van de naam van een methode en vervolgens dynamisch de methode worden aangeroepen door het aanroepen van de variabele.

- Asynchrone werkstroomtaken worden niet meer verwijderd wanneer de time-outperiode die is opgegeven door de **PSElapsedTimeoutSec** algemene werkstroomparameter is verstreken.

- Een nieuwe parameter **RepeatIndefinitely**, is toegevoegd aan de **New-JobTrigger** en **Set-JobTrigger** cmdlets. Hierdoor is de noodzaak voor het opgeven van een **TimeSpan.MaxValue** waarde voor de **RepetitionDuration** -parameter voor een geplande taak meerdere keren voor onbepaalde tijd uitgevoerd.

- Een **Passthru** parameter is toegevoegd aan de **Enable-JobTrigger** en **Disable-JobTrigger** cmdlets. De parameter Passthru gebruikt geeft objecten weer die zijn gemaakt of gewijzigd door de opdracht.

- De namen van parameters voor het opgeven van een werkgroep in de **Add-Computer** en **Remove-Computer** cmdlets nu consistent zijn. Beide cmdlets nu gebruiken de parameter **werkgroepnaam**.

- Een nieuwe algemene parameter **PipelineVariable**, is toegevoegd. PipelineVariable kunt u de resultaten van een opdracht doorgesluisd (of een deel van een opdracht piped) opslaan als een variabele die kan worden doorgegeven via de rest van de pijplijn.

- Verzameling filteren met behulp van een syntaxis van de methode wordt nu ondersteund. Dit betekent dat u kunt nu een verzameling van objecten filteren met behulp van vereenvoudigde syntaxis, vergelijkbaar met dat van Where() of Where-Object, worden opgemaakt als een methodeaanroep. Hieronder volgt een voorbeeld: (Get-Process) .waarbij ({$_. Name - overeenkomen met 'powershell'})

- De **Get-Process** cmdlet heeft een nieuwe parameter van de switch **IncludeUserName**.

- Een nieuwe cmdlet **Get-FileHash**, die als resultaat geeft de hash van een bestand in een van de verschillende indelingen voor een bepaald bestand, is toegevoegd.

- In Windows PowerShell 4.0, als een module wordt gebruikt de **DefaultCommandPrefix** sleutel in het manifest, of als de gebruiker invoer een module met de **voorvoegsel** parameter, de **ExportedCommands**eigenschap van de module worden de opdrachten in de module met het voorvoegsel. Wanneer u de opdrachten uitvoert met behulp van de syntaxis modulegekwalificeerde, modulenaam\\CommandName, het voorvoegsel voor de opdrachtnamen van de moeten bevatten.

- De waarde van **$PSVersionTable.PSVersion** is bijgewerkt naar 4.0.

- **WHERE()** operator gedrag is gewijzigd. `Collection.Where('property -match name')`het accepteren van een tekenreeksexpressie in de indeling `"Property -CompareOperator Value"` wordt niet langer ondersteund. Echter, de **Where()** operator accepteert tekenreeksexpressies in de indeling van een scriptblock; dit wordt nog steeds ondersteund.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nieuwe functies in Windows PowerShell Integrated Scripting Environment (ISE)

- Windows PowerShell ISE ondersteunt Windows PowerShell-werkstroom foutopsporing en foutopsporing van extern script.

- IntelliSense-ondersteuning is toegevoegd voor Windows PowerShell Desired State Configuration-providers en configuraties.

### <a name="new-features-in-windows-powershell-workflow"></a>Nieuwe functies in Windows PowerShell Workflow

- Er is ondersteuning toegevoegd voor een nieuwe **PipelineVariable** algemene parameter in de context van herhalende pijplijnen, zoals die wordt gebruikt door System Center Orchestrator; dat wil zeggen, pijplijnen die opdrachten gewoon links naar rechts, niet uitvoeren afgewisseld uitgevoerd met behulp van streaming.

- ParameterBinding is aanzienlijk uitgebreid samenwerkt buiten tabblad voltooiing scenario's, zoals opdrachten die niet zijn opgenomen in de huidige runspace.

- Ondersteuning voor aangepaste container activiteiten is toegevoegd aan Windows PowerShell-werkstroom. Als een parameter van de activiteit van de typen **activiteit**, **activiteit\[]**' 'of is een algemene verzameling activiteiten "en de gebruiker een scriptblok is opgegeven als argument, vervolgens Windows PowerShell-werkstroom omgezet in het scriptblok XAML, net als bij normale Windows PowerShell-scriptwerkstroom compilatie.

- Na het vastlopen van een Windows PowerShell-werkstroom automatisch opnieuw verbinding maakt met beheerde knooppunten.

- U kunt nu beperken **Foreach-Parallel** activiteit instructies met behulp van de **ThrottleLimit** eigenschap.

- De **ErrorAction** algemene parameter heeft een nieuwe geldige waarde **onderbreken**, die uitsluitend voor werkstromen.

- Een werkstroom eindpunt nu automatisch gesloten als er geen actieve sessies, geen taken wordt uitgevoerd en er geen in behandeling zijnde taken. Deze functie bespaart bronnen op de computer die als de workflow-server fungeert wanneer de automatische sluiting voorwaarden is voldaan.

### <a name="new-features-in-windows-powershell-web-services"></a>Nieuwe functies in Windows PowerShell-webservices

- Wanneer een fout optreedt in de Windows PowerShell Web Services (PSWS, ook wel Management OData IIS-extensie), terwijl wordt een cmdlet uitgevoerd, gedetailleerde fout berichten zijn geretourneerd naar de aanroeper. Bovendien foutcodes Volg [REST API van Windows Azure fout code richtlijnen](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).

- Een eindpunt kunt nu de API-versie te definiëren, evenals afdwingen van het gebruik van een specifieke versie van de API. Wanneer versie verschillen tussen client en server optreden, worden fouten weergegeven voor zowel de client als de server.

- Beheer van het schema van de verzending is vereenvoudigd door het automatisch genereren van waarden voor eventuele ontbrekende velden in het schema. Generatie optreedt, als een nuttig startpunt, zelfs als het schema van de verzending niet bestaat.

- Type verwerken bij PSWS is verbeterd ter ondersteuning van typen die het gebruik van een andere constructor dan de standaardconstructor door gedragen als de **PSTypeConverter** in Windows PowerShell. Hiermee kunt u complexe typen met PSWS gebruiken.

- PSWS kunt nu een bijbehorende exemplaar uitbreiden tijdens het uitvoeren van een query. De kosten voor de overdracht is belangrijk voor groter binaire inhoud (zoals afbeeldingen, audio of video), en is het beter om over te dragen van binaire gegevens zonder codering. Benoemde bron streams PSWS gebruikt voor het overdragen van zonder codering. De stroom benoemde bron is een eigenschap van een entiteit van de **Edm.Stream** type. Elke benoemde bronstream heeft een afzonderlijke URI voor GET of UPDATE-bewerkingen.

- OData-acties hebben nu een mechanisme voor het aanroepen van niet-CRUD (maken, lezen, bijwerken en verwijderen) methoden van een resource. U kunt een actie aanroepen door een HTTP POST-aanvraag verzenden naar de URI die is gedefinieerd voor de actie. De parameters voor de actie zijn gedefinieerd in de hoofdtekst van de POST-aanvraag.

- Als u consistent zijn met Windows Azure-richtlijnen, moeten alle URL's worden vereenvoudigd. Een wijziging die is opgenomen in **sleutel als Segment** kunt u één sleutels worden weergegeven als segmenten. Vergeet niet dat verwijzingen die gebruikmaken van meerdere sleutelwaarden door komma's gescheiden waarden in de notatie tussen haakjes als voorheen vereist.

- Voordat u deze release van PSWS, het alleen manier om uit te voeren Create, Update of Delete is bewerkingen aan te roepen Post, Put of verwijderen van een resource op het hoogste niveau. Nieuw in deze release van PSWS bewerkingen van resources die zijn opgenomen, kunnen gebruikers dezelfde resultaten bereiken bij het bereiken van dezelfde resource minder rechtstreeks bijna alsof deze resources zijn opgenomen.

### <a name="new-features-in-windows-powershell-web-access"></a>Nieuwe functies in Windows PowerShell-webtoegang

- U kunt verbreken en opnieuw verbinding maken met bestaande sessies in de Windows PowerShell-webtoegang webgebaseerde console. Een **opslaan** knop in de webconsole kunt u een sessie verbreken zonder het te verwijderen en opnieuw verbinding maken met de sessie een andere tijd.

- Standaard-parameters kunnen worden weergegeven op de aanmeldingspagina. Als u wilt weergeven standaardparameters, waarden configureren voor alle instellingen weergegeven in de **optionele verbindingsinstellingen** gebied van de aanmeldingspagina in een bestand met de naam **web.config**. U kunt de **web.config** bestand om alle optionele verbindingsinstellingen, met uitzondering van een tweede of een alternatieve set referenties te configureren.

- U kunt extern autorisatieregels voor Windows PowerShell Web Access in Windows Server 2012 R2 beheren. De **Add-PswaAuthorizationRule** en **Test-PswaAuthorizationRule** cmdlets omvatten nu een parameter Credential waarmee beheerders voor het beheren van autorisatieregels vanaf een externe computer of in een Windows PowerShell Web Access-sessie.

- U kunt nu meerdere sessies van Windows PowerShell-webtoegang in één browsersessie hebben met behulp van een nieuw browsertabblad voor elke sessie. U moet niet langer een nieuwe browsersessie verbinding maken met een nieuwe sessie in de Windows PowerShell web gebaseerde beheerconsole openen.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Opmerkelijke oplossingen voor problemen in Windows PowerShell 4.0

- **Get-Counter** items met een aanhalingsteken in Franse edities van Windows kunnen nu worden geretourneerd.

- U ziet nu de **GetType** methode in gedeserialiseerde objecten.

- **#Requires** instructies kunnen nu gebruikers vereisen Administrator-rechten voor toegang, indien nodig.

- De **importeren Csv** cmdlet nu lege regels worden genegeerd.

- Een probleem waarbij Windows PowerShell ISE te veel geheugen gebruikt wanneer u een **Invoke-WebRequest** opdracht is opgelost.

- **Get-Module** worden nu weergegeven moduleversies in een **versie** kolom.

- Software-Item - Recurse nu verwijdert items van submappen zoals verwacht.

- Een **gebruikersnaam** eigenschap is toegevoegd aan **Get-Process** uitvoer van objecten.

- De **Invoke-RestMethod** cmdlet nu alle beschikbare resultaten retourneert.

- **Voeg lid** nu wordt van kracht op hashtabellen, zelfs als de hash-tabellen nog niet is geopend.

- **Select-Object - Vouw** niet meer is mislukt of wordt een uitzondering gegenereerd als de waarde van de eigenschap null of leeg is.

- **Get-Process** kan nu worden gebruikt in een pijplijn met andere opdrachten die krijgt de **ComputerName** eigenschap uit de objecten.

- **ConvertTo-Json** en **ConverterenVan Json** kan nu termen tussen dubbele aanhalingstekens accepteren en de foutberichten zijn nu lokaliseerbare.

- **Get-Job** nu retourneert een voltooid taken, zelfs in nieuwe sessies geplande.

- Problemen met koppelen en ontkoppelen van VHD's met behulp van de **bestandssysteem** -provider in Windows PowerShell 4.0 zijn opgelost. Windows PowerShell is nu in staat voor het detecteren van nieuwe schijven wanneer ze zijn gekoppeld in dezelfde sessie.

- Niet langer moet u expliciet laden **ScheduledJob** of **werkstroom** modules met hun taaktypen werkt.

- Verbeterde prestaties zijn aangebracht aan het proces van het importeren van werkstromen die geneste werkstromen; definiëren Dit proces is nu sneller.

## <a name="new-features-in-windows-powershell-30"></a>Nieuwe functies in Windows PowerShell 3.0
Windows PowerShell 3.0 bevat de volgende nieuwe functies.

- [Windows PowerShell-werkstroom](#windows-powershell-workflow)
- [Windows PowerShell-internettoegang](#windows-powershell-web-access)
- [Nieuwe functies van Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Ondersteuning voor Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Ondersteuning voor Windows-omgeving voor voorinstallatie](#support-for-windows-preinstallation-environment)
- [Niet-verbonden sessies](#disconnected-sessions)
- [Robuuste sessie verbinding](#robust-session-connectivity)
- [Bijwerkbare Help-systeem](#updatable-help-system)
- [Verbeterde Online-Help](#enhanced-online-help)
- [CIM-integratie](#cim-integration)
- [Sessie-configuratiebestanden](#session-configuration-files)
- [Geplande taken en taak Scheduler-integratie](#scheduled-jobs-and-task-scheduler-integration)
- [Verbeteringen in Windows PowerShell-taal](#windows-powershell-language-enhancements)
- [Nieuwe Core-Cmdlets](#new-core-cmdlets)
- [Verbeteringen in bestaande essentiële Cmdlets en -Providers](#improvements-to-existing-core-cmdlets-and-providers)
- [Externe module-import en detectie](#remote-module-import-and-discovery)
- [Verbeterde Tab-aanvulling](#enhanced-tab-completion)
- [Module automatisch-laden](#module-auto-loading)
- [Module ervaring verbeteringen](#module-experience-improvements)
- [Vereenvoudigde opdracht detectie](#simplified-command-discovery)
- [Verbeterde logboekregistratie van diagnostische gegevens en ondersteuning voor beleid](#improved-logging-diagnostics-and-group-policy-support)
- [Opmaak en uitvoer verbeteringen](#formatting-and-output-improvements)
- [Verbeterde Console Host-ervaring](#enhanced-console-host-experience)
- [Nieuwe Cmdlet en het hosten van API 's](#new-cmdlet-and-hosting-apis)
- [Verbeterde prestaties](#performance-improvements)
- [RunAs en ondersteuning voor gedeelde hostgroep](#runas-and-shared-host-support)
- [Verbeteringen in behandeling speciaal teken](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell-werkstroom
Windows PowerShell Workflow biedt de kracht van Windows Workflow Foundation voor Windows PowerShell. U kunt schrijven van werkstromen in XAML of in de taal van de Windows PowerShell en voer ze net zoals u zou een cmdlet uitvoert. De [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet workflw opdrachten opgehaald en de [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet krijgt help voor werkstromen.

Werkstromen zijn reeksen multicomputer management-activiteiten die langlopende, herhaalbaar, regelmatig, parallel lopend, onderbreekbaar, suspendable en opnieuw starten. Werkstromen kunnen worden hervat vanaf een opzettelijk of per ongeluk onderbreking, bijvoorbeeld een netwerkstoring of een Windows opnieuw wordt opgestart een stroomstoring.

Werkstromen zijn ook draagbare; ze kunnen worden geëxporteerd als of geïmporteerd uit de XAML-bestanden. U kunt aangepaste sessieconfiguraties waarmee werkstroom of activiteiten in een werkstroom wordt uitgevoerd door de gedelegeerde of onderliggende gebruikers schrijven.

Hier volgen de voordelen van Windows PowerShell Workflow

- Gesequentieerd, langlopende taken te automatiseren.

- **Externe controle van langlopende taken**. De status en voortgang van activiteiten die zijn zichtbaar op elk gewenst moment.

- **Multicomputer management.** Taken als werkstromen tegelijkertijd uitvoeren op honderden beheerde knooppunten. Windows PowerShell Workflow bevat een ingebouwde bibliotheek met algemene Beheerparameters, zoals **PSComputerName**, die scenario's voor beheer van meerdere computers inschakelen.

- **De uitvoering van de taak één van complexe processen.** U kunt gerelateerde scripts die een volledige end-to-end-scenario in een enkele werkstroom implementeren combineren.

- **Persistentie.** : een werkstroom wordt opgeslagen (of controle-waarnaar wordt verwezen) op bepaalde tijdstippen die zijn gedefinieerd door de auteur, zodat u de werkstroom vanaf de laatst vastgelegde taak (of controlepunt) hervatten kunt in plaats van de werkstroom vanaf het begin opnieuw te starten.

- **Robuustheid.** Geautomatiseerd foutherstel. Werkstromen blijven na geplande en ongeplande opnieuw wordt opgestart. U kunt de werkstroom onderbreekt en hervat vervolgens de werkstroom vanaf het laatste punt in de persistentie. Werkstroomauteurs kunnen aanwijzen specifieke activiteiten moet opnieuw worden uitgevoerd in geval van storing op een of meer beheerde knooppunten.

- **Mogelijkheid om te verbreken, opnieuw verbinding maken en uitvoeren in verbroken sessies.** Gebruikers kunnen verbinding maken en Verbreek de verbinding tussen de werkstroomserver, maar de werkstroom continu wordt uitgevoerd. U kunt Meld u af bij de clientcomputer of de client opnieuw opstarten en controleren van de uitvoering van de werkstroom van een andere computer zonder de werkstroom te onderbreken.

- **Planning.** Werkstroomtaken kunnen worden gepland zoals een Windows PowerShell-cmdlet of script.

- **Werkstroom en bandbreedtebeperking van verbinding.** Uitvoering van de werkstroom en verbinding maken met knooppunten kunnen worden beperkt, waardoor u scenario's voor schaalbaarheid en hoge beschikbaarheid.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access
Windows PowerShell-webtoegang is een Windows Server 2012-functie waarmee gebruikers op een webconsole Windows PowerShell-opdrachten en scripts uitvoeren. Apparaten die gebruikmaken van de webconsole vereisen geen Windows PowerShell, extern beheer van software of browser invoegtoepassing installaties. Alle vereiste is een goed geconfigureerde Windows PowerShell Web Access-gateway en een browser op het clientapparaat die JavaScript ondersteunt en cookies accepteert.

Zie voor meer informatie [Windows PowerShell-webtoegang implementeren](http://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nieuwe functies van Windows PowerShell ISE
Voor Windows PowerShell 3.0 en Windows PowerShell Integrated Scripting Environment (ISE) heeft veel nieuwe functies, waaronder IntelliSense weergeven opdrachtvenster, een uniforme consolevenster codefragmenten, haakje-koppeling, vouw samenvouwen secties, automatisch moeten worden opgeslagen, onlangs geopende items lijst, uitgebreide kopiëren, blok kopiëren en volledige ondersteuning voor het schrijven van werkstromen voor Windows PowerShell-script. Zie voor meer informatie [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/en-us/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Ondersteuning voor Microsoft .NET Framework 4
Windows PowerShell is gebouwd op basis van de Common Language Runtime 4.0. Cmdlet, script en werkstroomauteurs kunnen gebruiken de nieuwe Microsoft .NET Framework 4-klassen in Windows PowerShell met kenmerken, zoals compatibiliteit van toepassingen en implementatie, uitbreidbaarheid Framework beheerd, parallelle berekeningen, netwerken, Windows Communication Foundation en Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Ondersteuning voor Windows-omgeving voor voorinstallatie
Windows PowerShell 3.0 is een optioneel onderdeel van Windows Preinstallation Environment (Windows PE) 4.0 voor Windows 8. Windows PE is een minimaal besturingssysteem die een computer waarop geen besturingssysteem en voorbereid voor Windows-installatie wordt gestart. Windows PE kan worden gebruikt voor de partitie en harde schijven formatteren, schijfkopieën kopiëren naar een computer en Windows Setup starten vanaf een netwerkshare. Windows PowerShell 3.0 kan worden gebruikt op Windows PE-implementatie, diagnostische gegevens en herstelscenario's beheren.

### <a name="disconnected-sessions"></a>Niet-verbonden sessies
Vanaf Windows PowerShell 3.0 kan worden permanente gebruiker beheerde sessies ('PSSessions') die u maakt met de cmdlet New-PSSession opgeslagen op de externe computer. Ze zijn niet langer afhankelijk van de sessie waarin ze zijn gemaakt.

U kunt nu een sessie verbreken zonder de opdrachten die worden uitgevoerd in de sessie verstoren. U kunt de sessie sluiten en de computer afsluiten. Later kunt u verbinding kunt maken met de sessie van een andere sessie op dezelfde of een andere computer.

De **ComputerName** parameter van de [Get-PSSession](https://technet.microsoft.com/en-us/library/b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet nu haalt alle sessies van de gebruiker die verbinding met de computer maken, zelfs als deze zijn gestart in een andere sessie op een andere computer. U kunt verbinding maken met de sessies, krijgen de resultaten van opdrachten, nieuwe opdrachten starten en vervolgens de sessie verbreken.

Nieuwe cmdlets toegevoegd ter ondersteuning van de functie verbroken sessies, inclusief [Disconnect-PSSession](https://technet.microsoft.com/en-us/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/en-us/library/b803dd29-f208-4079-80d4-db04d778f060), en Receive-PSSession en nieuwe parameters zijn toegevoegd aan -cmdlets die PSSessions, zoals beheren de **InDisconnectedSession** parameter van de [Invoke-Command](https://technet.microsoft.com/en-us/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.

De functie sessies verbroken wordt alleen ondersteund als de computers van beide van oorsprong ('client') en wordt beëindigd ('server') uiteinden van de verbinding actief zijn Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Robuuste sessie verbinding
Windows PowerShell 3.0 onverwachte verliezen van de verbinding tussen de client en server detecteert en probeert verbinding te herstellen en uitvoering automatisch hervat. Als de client / server-verbinding kan niet worden hersteld binnen de toegewezen tijd, wordt de gebruiker wordt geïnformeerd en wordt de sessie wordt verbroken. Tijdens de poging verbinding te maken, biedt Windows PowerShell continue feedback voor de gebruiker.

Als de verbroken sessie is gestart met behulp van de InvokeCommand, maakt de Windows PowerShell een taak voor de verbroken sessie gemakkelijker verbinding en hervat kan worden uitgevoerd.

Deze functies bieden een betrouwbaardere en herstelbare remoting-ervaring en toestaan dat gebruikers langlopende taken uitvoeren die robuust sessies, zoals werkstromen vereisen.

### <a name="updatable-help-system"></a>Bijwerkbare Help-systeem
U kunt nu downloaden van bijgewerkte help-bestanden voor de cmdlets in uw modules. De [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet identificeert de nieuwste help-bestanden, downloadt u deze vanaf het Internet, ze zijn uitgepakt, evalueert deze en installeert u ze in de juiste map specifieke taal zijn gebonden voor de module.

De bijgewerkte help-bestanden wilt gebruiken, typt u gewoon `Get-Help`. U hoeft niet opnieuw opstarten van Windows of Windows PowerShell. U werkt de help voor modules in de map $pshome, start u Windows PowerShell met de optie 'Als administrator uitvoeren'.

Ter ondersteuning van gebruikers die geen toegang tot Internet en gebruikers achter een firewall, de nieuwe [Help opslaan](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet help-bestanden downloadt naar een systeemmap, zoals een bestandsshare. Gebruikers kunnen vervolgens gebruiken de [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet voor het ophalen van bijgewerkte help-bestanden van de bestandsshare.

U kunt de [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet bij te werken help-bestanden voor alle of bepaalde modules in alle ondersteunde UI culturen. U kunt zelfs toe leiden dat een [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) opdracht in uw Windows PowerShell-profiel. Standaard downloadt Windows PowerShell help-bestanden voor een module niet meer dan één keer per dag.

Windows 8 en Windows Server 2012-modules bevatten geen help-bestanden. Voor het downloaden van de meest recente help-bestanden, typt u `Update-Help`. Typ voor meer informatie `Get-Help` (zonder parameters) of Raadpleeg [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Wanneer de help-bestanden voor een cmdlet zijn niet geïnstalleerd op de computer, de [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet worden nu automatisch gegenereerde help weergegeven. De help automatisch wordt gegenereerd, bevat de opdrachtsyntaxis en instructies voor het gebruik van de [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet helpbestanden te downloaden.

Een module-auteur kan ondersteunen bij te werken Help voor de module. U kunt bijvoorbeeld help-bestanden in de module en bij te werken Help bijwerken of laat de help-bestanden en bij te werken Help gebruiken ze te installeren. Zie voor meer informatie over ondersteunende bij te werken Help [ondersteunende bij te werken Help](http://go.microsoft.com/FWLink/?LinkID=242129) in MSDN.

### <a name="enhanced-online-help"></a>Verbeterde Online-Help
Online-help van Windows PowerShell is een waardevolle resource voor alle gebruikers, maar het is vooral belangrijk voor gebruikers die zich niet of kunnen de bijgewerkte help-bestanden niet installeren.

Als u online-help voor een Windows PowerShell-cmdlet, typt u:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell wordt de online versie van het help-onderwerp in de standaardbrowser geopend.

De **Get-Help-Online** functie in Windows PowerShell 3.0 is nu nog krachtiger omdat dit werkt zelfs wanneer help-bestanden voor de cmdlet niet zijn geïnstalleerd op de computer. De **Get-Help-Online** functie krijgt de URI voor de online help-onderwerp van de eigenschap HelpUri van cmdlets en geavanceerde functies.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

Vanaf Windows PowerShell 3.0 kan de auteurs van C#-cmdlets kunnen vullen de **HelpUri** eigenschap door het maken van een **HelpUri** kenmerk voor de cmdlet-klasse. Auteurs van geavanceerde functies kunnen definiëren een **HelpUri** -eigenschap op de **CmdletBinding** kenmerk. De waarde van de **HelpUri** eigenschap moet beginnen met 'http' of 'https'.

U kunt ook een **HelpUri** waarde in de eerste gerelateerde koppeling van een XML-indeling cmdlet help-bestand of de. De richtlijn van de koppeling van help op basis van een opmerking in een functie.

Zie voor meer informatie over ondersteunende online help [ondersteunende Online Help](http://go.microsoft.com/fwlink/?LinkId=242132) in MSDN.

### <a name="cim-integration"></a>CIM-integratie
Windows PowerShell 3.0 bevat ondersteuning voor de Common Information Model (CIM), waarmee gemeenschappelijke definities van beheergegevens voor systemen, netwerken, toepassingen en services, zodat ze het uitwisselen van beheergegevens tussen heterogene systemen. Ondersteuning voor CIM in Windows PowerShell 3.0, inclusief de mogelijkheid voor het ontwerpen van Windows PowerShell-cmdlets op basis van nieuwe of bestaande CIM klassen, opdrachten op basis van de definitie van de cmdlet XML-bestanden, ondersteuning voor CIM .NET Framework. API, CIM-cmdlets voor beheer en 2.0 WMI-providers.

### <a name="session-configuration-files"></a>Sessie-configuratiebestanden
U kunt vanaf Windows PowerShell 3.0 is een aangepaste sessieconfiguratie ontwerpen met behulp van een bestand. Het configuratiebestand van de nieuwe sessie kunt u de omgeving van sessies die gebruikmaken van de sessieconfiguratie, inclusief welke modules, scripts, bepalen en format-bestanden zijn geladen in sessies, welke elementen cmdlets en -taal gebruikers gebruiken kunnen, welke modules en scripts te kunnen worden uitgevoerd en welke variabelen die ze kunnen zien.

U kunt een sessie waarin gebruikers kunnen alleen de cmdlets uitvoeren van een bepaalde module of een sessie die gebruikers hebben volledig taal, toegang tot alle modules en toegang tot de scripts die geavanceerde taken uitvoeren ontwerpen.

In eerdere versies van Windows PowerShell zijn besturingselement op dit niveau is alleen beschikbaar voor gebruikers die een C#-programma of een script complexe opstarten kan schrijven. Elk lid van de groep Administrators op de computer kan nu een sessieconfiguratie aanpassen met behulp van een configuratiebestand.

Voor het maken van een configuratiebestand sessie gebruikt de [nieuw PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. Als het configuratiebestand van de sessie voor een sessieconfiguratie geldt, gebruiken de [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) of [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.

Zie voor meer informatie [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8) en [nieuw PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Geplande taken en taak Scheduler-integratie
U kunt nu Windows PowerShell-achtergrondtaken plannen en ze beheren in Windows PowerShell en in Taakplanner.

Windows PowerShell geplande taken zijn een handig hybride van Windows PowerShell-achtergrondtaken en Taakplanner-taken.

Net als Windows PowerShell-achtergrondtaken, geplande taken asynchroon op de achtergrond uitgevoerd. Exemplaren van geplande taken die zijn voltooid, kunnen worden beheerd met behulp van de taak-cmdlets, zoals [starttaak](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442) en [Get-Job](https://technet.microsoft.com/en-us/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

U kunt geplande taken zoals Taakplanner-taken uitvoeren volgens een schema eenmalig of terugkerende of als reactie op een actie of een gebeurtenis. U kunt bekijken en beheren van geplande taken in Taakplanner, inschakelen en uitschakelen, indien nodig, ze uitvoeren of deze als sjabloon gebruiken en stel de voorwaarden waaronder de taak wordt gestart.

Bovendien Geplande taken worden geleverd met een aangepaste set cmdlets voor het beheer ervan. De cmdlets kunt u maken, bewerken, beheren, uitschakelen, en geplande taken opnieuw in te schakelen, triggers geplande taak maken en stelt u opties voor geplande taak.

Zie voor meer informatie over de geplande taken [about_Scheduled_Jobs](https://technet.microsoft.com/en-us/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Verbeteringen in Windows PowerShell-taal
Windows PowerShell 3.0 bevat veel functies die zijn ontworpen voor de taal eenvoudigere, eenvoudiger te gebruiken en om veelvoorkomende fouten te voorkomen. De verbeteringen omvatten eigenschap opsomming, aantal en de lengte-eigenschappen op scalaire objecten, nieuwe omleiding operators, de bereikaanpassingsfunctie $Using, PSItem automatische variabelen, flexibele script opmaak, de kenmerken van variabelen, vereenvoudigde kenmerk argumenten, numerieke opdrachtnamen, de operator stoppen parseren, verbeterde matrix splatting, nieuwe bits-operators, geordende woordenboeken, PSCustomObject casten en verbeterde Opmerking gebaseerde Help-informatie.

### <a name="new-core-cmdlets"></a>Nieuwe Core-Cmdlets
Er zijn nieuwe cmdlets toegevoegd aan de Windows PowerShell Core-installatie, inclusief cmdlets voor het beheren van geplande taken, niet-verbonden sessies, CIM-integratie en het bij te werken Help-systeem.

|||
|-|-|
|-JobTrigger|Nieuwe-JobTrigger|
|Connect-PSSession|Nieuwe PSSessionConfigurationFile|
|ConverterenVan Json|New-PSTransportOption|
|ConvertTo-Json|Nieuwe PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|Nieuwe ScheduledJobOption|
|Verbinding verbreken-PSSession|Nieuwe WinEvent|
|Enable-JobTrigger|Ontvangen-PSSession|
|Enable-ScheduledJob|Register CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Verwijder CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Verwijder TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Help opslaan|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Importeren IseSnippet|Set-ScheduledJobOption|
|Aanroepen AsWorkflow|Opdracht weergeven|
|Aanroepen CimMethod|Weergeven ControlPanelItem|
|Aanroepen RestMethod|Suspend-Job|
|Aanroepen WebRequest|Test PSSessionConfigurationFile|
|Nieuwe CimInstance|De blokkering opheffen bestand|
|Nieuwe-CimSession|Unregister-ScheduledJob|
|Nieuwe CimSessionOption|Help bijwerken|
|Nieuwe IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Verbeteringen in bestaande essentiële Cmdlets en -Providers
Windows PowerShell 3.0 bevat nieuwe functies voor bestaande cmdlets zoals vereenvoudigde syntaxis en nieuwe parameters voor de volgende cmdlets: Computer cmdlets, CSV-cmdlets Get-ChildItem Get-Command-, Get-inhoud, Get-geschiedenis Meetobject-beveiliging cmdlets, Select-Object, selecteer-tekenreeks, Split-Path, Start-proces t-Object, Test-Connection lid zijn van het toevoegen en WMI-cmdlets.

De Windows PowerShell-providers zijn ook sterk verbeterd, inclusief certificaat Providerondersteuning voor het beheren van certificaten voor webhosting Secure Socket Layer (SSL), ondersteuning voor de referentie en permanente netwerkstations alternatieve gegevensstreams in bestandssysteem stations.

### <a name="remote-module-import-and-discovery"></a>Externe module-import en detectie
Windows PowerShell 3.0 breidt module detectie, importeren en impliciete remoting mogelijkheden op externe computers. De Module-cmdlets modules ophalen op externe computers en importeer de modules in de lokale of externe computer met behulp van Windows PowerShell op afstand. Nieuwe ondersteuning voor CIM-sessie kunt u gebruikmaken van CIM- en WMI voor het beheren van niet-Windows-computers door het importeren van opdrachten op de lokale computer die impliciet wordt uitgevoerd op de externe computer.

Zie voor meer informatie het help-onderwerpen voor de [Get-Module](https://technet.microsoft.com/en-us/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) en [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="enhanced-tab-completion"></a>Verbeterde Tab-aanvulling
Tab-Aanvulling in de Windows PowerShell-console nu voltooit de namen van cmdlets, parameters parameterwaarden, opsommingen, .NET Frameworks typen, COM-objecten, verborgen mappen en meer. Het tabblad voltooiing onderdeel wordt volledig herschreven op basis van een nieuwe parser en de abstracte syntaxisstructuur voor de ondersteuning van meer scenario's, waaronder parseren structuren in het geheugen en schouderstreek tab-Aanvulling.

### <a name="module-auto-loading"></a>Module automatisch-laden
De [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet nu haalt alle cmdlets en -functies uit alle modules weer die zijn geïnstalleerd op de computer, zelfs als de module niet is geïmporteerd in de huidige sessie.

Wanneer u de cmdlet die u nodig hebt, kunt u dit onmiddellijk zonder te importeren geen modules. Windows PowerShell-modules worden nu automatisch geïmporteerd wanneer u een cmdlet in de module. U hoeft niet meer te zoeken naar de module en voor het gebruik van de cmdlets te importeren.

Met de cmdlet uitgevoerd in een opdracht automatisch importeren van modules wordt geactiveerd **Get-Command** voor een cmdlet zonder jokertekens of met [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) voor een cmdlet zonder jokertekens.

U kunt inschakelen, uitschakelen en configureren van automatische importeren van modules met behulp van de **$PSModuleAutoLoadingPreference** voorkeursvariabele.

Zie voor meer informatie [about_Modules [v4]](https://technet.microsoft.com/en-us/library/94f57429-a539-4aee-bb0d-205cd7e801f9), [about_Preference_Variables [v4]](https://technet.microsoft.com/en-us/library/31344314-be29-4286-b039-afa5460cbe8b), en de help-onderwerpen voor de [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) en [Import-Module ](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="module-experience-improvements"></a>Module ervaring verbeteringen
Windows PowerShell 3.0 biedt geavanceerde functies die worden ondersteund voor modules, waaronder de volgende nieuwe functies.

1. Module-logboekregistratie voor afzonderlijke modules (LogPipelineExecutionDetails) en de nieuwe instelling voor Groepsbeleid 'Inschakelen op Module-logboekregistratie'

2. Module-objecten die de waarden van de module-manifest uitgebreid

3. Nieuwe **ExportedCommands** eigenschap van modules, waaronder genest modules, die opdrachten van alle typen combineert

4. Verbeterde detectie van beschikbare (niet-geïmporteerde) modules, waaronder zodat de **pad** en **ListAvailable** parameters in dezelfde opdracht

5. Nieuwe **DefaultCommandPrefix** sleutel in de modulemanifesten die voorkomt naamconflicten zonder module code te wijzigen.

6. Verbeterd, module vereisten, met inbegrip van volledig gekwalificeerde vereiste modules met versie en de GUID en de vereiste modules automatisch importeren

7. Rustigere, gestroomlijnde bewerking van de [nieuw ModuleManifest](https://technet.microsoft.com/en-us/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.

8. Nieuwe **Module** parameter voor #Requires

9. Verbeterde [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet met beide **MinimumVersion** en **RequiredVersion** parameters.

### <a name="simplified-command-discovery"></a>Vereenvoudigde opdracht detectie
U hoeft niet meer voor het importeren van alle modules voor het detecteren van de opdrachten die beschikbaar zijn voor uw sessie. In Windows PowerShell 3.0 de [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet alle opdrachten van alle geïnstalleerde modules opgehaald. En als u een opdracht, de module die exporteert u de opdracht wordt automatisch geïmporteerd in uw sessie.

De nieuwe [opdracht weergeven](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet is speciaal ontworpen voor beginnende gebruikers. U kunt zoeken naar de opdrachten in een venster. U kunt alle opdrachten weergeven of filteren door de module, een module importeren door te klikken op een knop, tekstvakken en vervolgkeuzelijsten maken van een geldige opdracht en kopieer vervolgens of de opdracht uitgevoerd zonder het venster gebruiken.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Verbeterde logboekregistratie van diagnostische gegevens en ondersteuning voor beleid
Windows PowerShell 3.0 verbetert de logboekregistratie en tracering van ondersteuning voor opdrachten en modules met ondersteuning voor gebeurtenistracering in Windows (ETW) zich aanmeldt, een bewerkbare **LogPipelineExecutionDetails** eigenschap van modules en de "inschakelen op Module Logboekregistratie' groep beleidsinstelling. U kunt nu de parameterwaarden vanuit logboekdetails krijgen door de logboekeigenschappen weer te geven.

### <a name="formatting-and-output-improvements"></a>Opmaak en uitvoer verbeteringen
Nieuwe opmaak en uitvoer verbeteringen verbeteren de efficiëntie van alle gebruikers van Windows PowerShell. De verbeteringen omvatten uitvoeromleiding voor alle gegevensstromen, een verbeterde Type Update cmdlet die wordt toegevoegd typen dynamisch zonder Format.ps1xml bestanden, automatische terugloop in de uitvoer standaard opmaakeigenschappen van aangepaste objecten de **PSCustomObject** tekst, verbeterde opmaak voor WMI-objecten en heterogene objecten en ondersteuning voor het detecteren van methode overloads.

### <a name="enhanced-console-host-experience"></a>Verbeterde Console Host-ervaring
Het programma voor Windows PowerShell-console host heeft nieuwe functies in Windows PowerShell 3.0 single threaded apartment inclusief standaard. De nieuwe optie 'Uitvoeren met PowerShell' in Verkenner kunt u scripts uitvoeren in een onbeperkte-sessie met de rechtermuisknop op. Nieuwe console host starten logica Start Windows PowerShell sneller en nieuwe lettertypen kunnen u de vertrouwde console-venster afstemmen.

Zie voor meer informatie [about_Run_With_PowerShell](https://technet.microsoft.com/en-us/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Nieuwe Cmdlet en het hosten van API 's
De nieuwe Cmdlet API en die als host fungeert API bevatten openbare geavanceerde syntaxisstructuur (AST) API's en API's voor pijplijn paginering, geneste pijplijnen runspace pools tab-aanvulling, Windows RT, de verouderde cmdlet-kenmerk en term en zelfstandig naamwoord eigenschappen van het object FunctionInfo.

### <a name="performance-improvements"></a>Verbeterde prestaties
Aanzienlijke prestatieverbeteringen in Windows PowerShell afkomstig zijn van de nieuwe taal parser dat is gemaakt op dynamische Runtime taal (DLR) in .NET Framework 4., samen met de runtime script compilatie, verbeteringen van de engine-betrouwbaarheid en wijzigingen in de algoritme van de [Get-ChildItem](https://technet.microsoft.com/en-us/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) verbeteren de prestaties, vooral wanneer zoeken netwerk deelt.

### <a name="runas-and-shared-host-support"></a>RunAs en ondersteuning voor gedeelde hostgroep
Windows PowerShell 3.0 bevat ondersteuning voor RunAs- en gedeeld Host-functies.

De *RunAs* functie, die zijn bestemd voor Windows PowerShell Workflow, kan gebruikers van een sessieconfiguratie sessies die worden uitgevoerd met de machtiging van een gedeelde gebruikersaccount maken. Hierdoor hoeven minder bevoegde gebruikers bepaalde opdrachten en scripts uitvoeren met beheerdersrechten en vermindert de noodzaak om minder senior gebruikers toevoegen aan de groep Administrators.

De **SharedHost** functie kan meerdere gebruikers op meerdere computers verbinding maken met een Werkstroomsessie gelijktijdig en de voortgang van een werkstroom. Gebruikers kunnen geen werkstroom starten op één computer en maak verbinding met de Werkstroomsessie op een andere computer zonder de sessie verbreken met de oorspronkelijke computer. Gebruikers moeten dezelfde machtigingen hebben en dezelfde sessieconfiguratie gebruikt. Zie voor meer informatie 'Uitgevoerd een Windows PowerShell Workflow' aan de slag met Windows PowerShell Workflow.

### <a name="special-character-handling-improvements"></a>Verbeteringen in behandeling speciaal teken
Voor het verbeteren van de mogelijkheid van Windows PowerShell 3.0 interpreteren en correct verwerkt speciale tekens, de **LiteralPath** speciale tekens in paden verwerkt, parameter is geldig voor bijna alle cmdlets die u hebt een  **Pad** parameter, met inbegrip van de nieuwe [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) en [Help opslaan](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlets. De parser bevat ook speciale logica ter verbetering van de verwerking van het teken backtick (\`) en vierkante haken in paden en bestandsnamen.

## <a name="see-also"></a>Zie ook
- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)

