---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Wat is er nieuw in Windows PowerShell 5.0
ms.openlocfilehash: 7a2ef581f2cd867b35533597d4942fd5bfc94570
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225808"
---
# <a name="whats-new-in-windows-powershell-50"></a>Wat is er nieuw in Windows PowerShell 5.0
Windows PowerShell 5.0 bevat belangrijke nieuwe functies die het gebruik ervan uitbreiden, de bruikbaarheid wordt verbeterd, en kunnen u zelf regelen en beheren van Windows gebaseerde omgevingen gemakkelijker en uitgebreider.

Windows PowerShell 5.0 is achterwaarts compatibel. -Cmdlets, providers, -modules, -modules, scripts, functies en -profielen die zijn ontworpen voor Windows PowerShell 4.0, Windows PowerShell 3.0 en Windows PowerShell 2.0 in het algemeen werken in Windows PowerShell 5.0 zonder wijzigingen.

# <a name="installing-windows-powershell"></a>Windows PowerShell installeren
Windows PowerShell 5.0 wordt standaard geïnstalleerd op Windows Server 2016 Technical Preview en Windows 10.

Voor het installeren van Windows PowerShell 5.0 op Windows Server 2012 R2, Windows 8.1 Enterprise of Windows 8.1 Pro, download en installeer [Windows Management Framework 5.0](http://aka.ms/wmf5download). Moet u de details van de download lezen en voldoen aan alle systeemvereisten, voordat u Windows Management Framework 5.0 installeren.

## <a name="in-this-topic"></a>In dit onderwerp

- [Windows PowerShell 4.0 DSC-updates in KB 3000850](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Nieuwe functies in Windows PowerShell 5.0](#new-features-in-windows-powershell-50)
- [Nieuwe functies in Windows PowerShell 4.0](#new-features-in-windows-powershell-40)
- [Nieuwe functies in Windows PowerShell 3.0](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>Updatepakket van Windows PowerShell 4.0-updates in November 2014 (KB 3000850)
Veel updates en verbeteringen aan Windows PowerShell Desired State Configuration (DSC) in Windows PowerShell 4.0 zijn beschikbaar in de [updatepakket van November 2014 voor Windows RT 8.1, Windows 8.1 en Windows Server 2012 R2](https://support.microsoft.com/kb/3000850/) (KB 3000850 ). U kunt bepalen of KB 3000850 is geïnstalleerd op uw systeem door het uitvoeren van `Get-Hotfix -Id KB3000850` in Windows PowerShell.

- Updates voor bestaande cmdlets in de [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) module

    -   [Sleutelwoorden Get-dscresource bieden](http://technet.microsoft.com/library/dn521625.aspx) is veel sneller (met name in ISE).

    -   [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) heeft een nieuwe parameter, - UseExisting, die de laatste toegepaste configuratie opnieuw toegepast.

    -   [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) -Force is opgelost.

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) meer nuttige informatie over de status van de engine wordt weergegeven.

    -   [Test-DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) nu retourneert de naam van de computer, samen met waar of ONWAAR.

    -   [Nieuwe DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) biedt nu ondersteuning voor UNC-paden.

- Er zijn nieuwe cmdlets in de [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) module

    -   [Update-DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx): voert een on-demand pull-server uit.

    -   [Stop-DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx): stopt een configuratie die al wordt uitgevoerd.

    -   [Remove-DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx): kunt u het verwijderen van configuratiedocumenten in verschillende stadia (in behandeling, vorige of huidige).

- Verbeteringen voor taal

    -   DependsOn biedt nu ondersteuning voor samengestelde resources.

    -   DependsOn biedt nu ondersteuning voor getallen in de namen van voorbeeldresources-exemplaar.

    -   Knooppuntexpressies die niet meer worden geëvalueerd tot leeg throw fouten.

    -   Een fout die optreedt als een knooppunt-expressie wordt geëvalueerd als leeg zijn is, opgelost.

    -   Configuraties aanroepen van configuraties nu werkt in de Windows PowerShell-console.

- Verbeteringen voor pull-modus

    -   Pull-modus biedt nu ondersteuning voor alle ZIP-bestanden.

    -   **AllowModuleOverwrite** nu correct werkt.

- Verbeteringen voor tolerantie

    -   Nieuwe **fouten opsporen-modus** kunt u opnieuw laden van resource-modules.

    -   Als een configuratiefout optreedt, wordt het bestand pending.mof niet verwijderd.

    -   De lokale Configuration Manager (LCM) is nu beter bestand is tegen wanneer metaconfiguration instellingen zijn beschadigd.

- Verbeteringen voor diagnosefuncties

    -   Een waarschuwing wordt weergegeven wanneer de LCM wordt de timer ingesteld op andere instellingen dan u hebt opgegeven.

    -   Fout-logboekbestanden bevat nu de aanroepstack voor Windows PowerShell-resources.

- Verbeteringen voor flexibiliteit

    -   De resource LocalConfigurationManager heeft een nieuwe eigenschap **ActionAfterReboot**.

        -   ContinueConfiguration (standaardwaarde): een configuratie voor automatisch hervat nadat een doelknooppunt opnieuw wordt opgestart.

        -   De StopConfiguration: Niet automatisch een configuratie hervatten nadat een knooppunt opnieuw wordt opgestart.

    -   Een consistentiecontrole uitvoeren kan nu treden vaker op dan een PULL-bewerking of vice versa.

    -   Ondersteuning voor versiebeheer: DSC nu een document dat is gegenereerd op een nieuwere client kunt herkennen (meegeleverd bij [WMF 5.0](http://aka.ms/wmf5download)).

- Fout preventie verbeteringen

    -   Moduleversie wordt nu afgedwongen voordat een configuratie is toegepast.

    -   **DebugPreference** nu correct is ingesteld voor Get-, Set- of Test-TargetResource aanroepen.

- Referentie voor het verwerken van verbeteringen

    -   Een certificaat wordt nu gebruikt als zowel **certificaat** en **PSDscAllowPlainTextPassword** zijn opgegeven.

    -   Referenties worden ontsleuteld, zelfs voor Get-TargetResource.

    -   Metaconfiguration referenties worden versleuteld en ontsleuteld.

    -   PSCredentials zijn nu ontsleuteld wanneer ze zich in een ingesloten object.

- Verbeteringen van de ingebouwde resource

    -   De pakket-bron

        -   Niet meer installeert het verkeerde pakket (via lokaal of web-bronnen).

        -   Biedt nu ondersteuning voor HTTPS.

    -   Er is nu ondersteuning voor HTTPS in de [resource inpakt](http://technet.microsoft.com/library/dn282132.aspx).

    -   [Archiveren van resource](http://technet.microsoft.com/library/dn249917.aspx) biedt nu ondersteuning voor referenties.

## <a name="new-features-in-windows-powershell-50"></a>Nieuwe functies in Windows PowerShell 5.0

- [Nieuwe functies in Windows PowerShell](#new-features-in-windows-powershell)
- [Nieuwe functies in Windows PowerShell Desired State Configuration](#new-features-in-windows-powershell-desired-state-configuration)
- [Nieuwe functies in Windows PowerShell ISE](#new-features-in-windows-powershell-ise)
- [Nieuwe functies in Windows PowerShell-webservices](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Oplossingen voor problemen die aandacht vereisen in Windows PowerShell 5.0](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Nieuwe functies in Windows PowerShell

- Vanaf Windows PowerShell 5.0, kunt u ontwikkelen met behulp van klassen, met behulp van de syntaxis van de formele en semantiek die vergelijkbaar met andere objectgeoriënteerde programmeertalen zijn. **Klasse**, **Enum**, en andere trefwoorden zijn toegevoegd aan de Windows PowerShell-taal voor de ondersteuning van de nieuwe functie. Zie voor meer informatie over het werken met klassen about_Classes.

- Windows PowerShell 5.0 introduceert een nieuwe, gestructureerde gegevensstroom die u gebruiken kunt voor het verzenden van gestructureerde gegevens tussen een script en de aanroepers (of hostingomgeving). U kunt nu Write-Host gebruiken om te verzenden van uitvoer naar de gegevensstroom. Informatiestromen werkt ook voor PowerShell.Streams, taken, geplande taken en werkstromen. De volgende functies ondersteuning voor de gegevensstroom.

    -   Een nieuwe cmdlet met Write-informatie waarmee u kunt opgeven hoe de stroom van gegevens voor een opdracht worden verwerkt in Windows PowerShell. Write-Host is een wrapper voor Write-informatie. Write-informatie is ook een ondersteunde workflow-activiteit.

    -   Twee nieuwe algemene parameters, InformationVariable en InformationAction, kunnen u bepalen hoe gegevensstromen van een opdracht worden weergegeven. Geldige waarden voor InformationAction zijn SilentlyContinue, stoppen, doorgaan, opvragen, negeren of onderbreking met SilentlyContinue wordt de standaardwaarde. InformationVariable geeft een tekenreeks als de naam van een variabele die u wilt dat de gegevens Write-Host van een opdracht die is opgeslagen.

    -   Een nieuwe voorkeursvariabele, InformationPreference, Hiermee geeft u de standaardvoorkeur voor de stroom van gegevens in een Windows PowerShell-sessie. De standaardwaarde is SilentlyContinue.

    -   Twee nieuwe werkstroom algemene parameters, PSInformation en InformationAction, zijn toegevoegd.

    -   Wanneer u de opdracht Format-Table, worden tabelkolommen nu automatisch opgemaakt door het evalueren van de eerste 300ms van gegevens die wordt doorgegeven via de stroom.

- In samenwerking met [Microsoft Research](http://research.microsoft.com/), een nieuwe cmdlet, ConvertFrom-tekenreeks is toegevoegd. ConvertFrom-tekenreeks kunt u gestructureerde objecten uit de inhoud van tekenreeksen uitpakken en parseren. Zie voor meer informatie, ConvertFrom-tekenreeks.

- Een nieuwe cmdlet voor het omzetten van tekenreeks maakt automatisch tekst op basis van een voorbeeld dat u in een - voorbeeld-parameter opgeeft.

- Een nieuwe Microsoft.PowerShell.Archive,-module bevat cmdlets waarmee u bestanden comprimeren en mappen naar (ook bekend als ZIP)-archiefbestanden uitpakken van bestanden uit bestaande ZIP-bestanden en ZIP-bestanden met een nieuwere versie van de bestanden die in deze update.

- Een nieuwe module PackageManagement, kunt u detecteren en installeren van software-updatepakketten op het Internet. De module PackageManagement (voorheen oneget genaamd) is een manager of multiplexer van bestaande Pakketbeheer (ook wel pakket providers) om te leiden tot een uniformer beheer van Windows-pakket met een enkel Windows PowerShell-interface.

- Een nieuwe module PowerShellGet, kunt u vinden, installeren, publiceren en bijwerken van de modules en DSC-resources op de [PowerShell Gallery](http://www.powershellgallery.com/), of op een interne module-opslagplaats die u door de cmdlet Register-PSRepository kunt instellen.

- Een nieuwe taal-trefwoord **verborgen**, is toegevoegd om op te geven dat een lid (dit is een eigenschap of een methode) niet wordt weergegeven in de resultaten van de Get-Member standaard (tenzij u de parameter - Force). Eigenschappen en methoden die verborgen zijn gemarkeerd ook, worden niet weergegeven in de resultaten van IntelliSense, tenzij u zich in een context waar het lid weergegeven worden moet; bijvoorbeeld, de automatische variabelen $dit verborgen leden in de klassenmethode moet worden weergegeven.

- Nieuw Item, Item verwijderen en Get-ChildItem zijn uitgebreid ter ondersteuning van het maken en beheren van [symbolische koppelingen](http://en.wikipedia.org/wiki/Symbolic_link). De **- ItemType** parameter voor New-object accepteert een nieuwe waarde **SymbolicLink**. U kunt nu symbolische koppelingen maken in een enkele regel door de cmdlet New-Item.

- Get-ChildItem heeft ook een nieuwe - diepte parameter, die u met de - Recurse-parameter gebruiken om te beperken de recursie. Bijvoorbeeld: Get-ChildItem-Recurse - diepte 2 resultaten retourneert uit de huidige map, alle onderliggende mappen in de huidige map en alle mappen in de onderliggende mappen.

- Copy-Item nu kunt u bestanden of mappen vanuit een Windows PowerShell-sessie naar de andere kopieert, wat betekent dat u bestanden kunt kopiëren naar sessies die zijn verbonden met externe computers (met inbegrip van computers waarop [Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx), en Daarom hebben geen andere interface). Bestanden wilt kopiëren, PSSession-id's opgeven als de waarde van de parameters voor de nieuwe - FromSession en -ToSession en add - Path en - bestemming om op te geven van pad voor de oorsprong en bestemming, respectievelijk. Bijvoorbeeld, Copy-Item-pad c:\\myFile.txt - ToSession $s-doel d:\\doelmap.

- Windows PowerShell transcriptie, is verbeterd om toe te passen op alle hosting-toepassingen (zoals Windows PowerShell ISE) naast de consolehost (**powershell.exe**). Transcriptiemogelijkheden (, waaronder het inschakelen van een systeembreed transcript) kunnen worden geconfigureerd door in te schakelen de **PowerShell transcriptie inschakelen** instelling voor Groepsbeleid in Administrative Templates/Windows-onderdelen/Windows gevonden PowerShell.

- Een nieuwe functie voor het traceren van gedetailleerde script kunt u gedetailleerde bijhouden en analyseren van Windows PowerShell scripts gebruiken op een systeem inschakelen. Nadat u gedetailleerde script tracering ingeschakeld, Windows PowerShell alle scriptblokken registreert in het gebeurtenislogboek van Event Tracing voor Windows (ETW) **Microsoft-Windows-PowerShell/Operational**.

- Vanaf Windows PowerShell 5.0, nieuwe cmdlets voor Cryptographic Message-syntaxis ondersteunt versleuteling en ontsleuteling van inhoud met behulp van de IETF-standaard indeling voor het beveiligen van berichten cryptografisch zoals beschreven door [RFC5652](http://tools.ietf.org/html/rfc5652). De cmdlets Get-CmsMessage en beveiligen-CmsMessage Unprotect-CmsMessage zijn toegevoegd aan de [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) module.

- Er zijn nieuwe cmdlets in de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) -module, Get-Runspace, foutopsporing Runspace, Get-RunspaceDebug, Enable-RunspaceDebug en Disable-RunspaceDebug, kunnen u foutopsporingsopties instellen op een runspace en starten en stoppen foutopsporing op een runspace. Voor het opsporen van fouten in willekeurige runspaces "dat wil zeggen, runspaces die niet de standaard-runspace voor een Windows PowerShell-console of Windows PowerShell ISE-sessie ' 'Windows PowerShell kunt u onderbrekingspunten instellen in een script, en hebt toegevoegd onderbrekingspunten stoppen van het script uit wordt uitgevoerd totdat u kunt een foutopsporingsprogramma fouten opsporen in het script runspace koppelen. Ondersteuning voor geneste foutopsporing voor willekeurige runspaces is toegevoegd aan de Windows PowerShell-Scriptdebugger voor runspaces genoemd.

- Een nieuwe indeling Hex-cmdlet is toegevoegd aan de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module. Indeling: hexadecimaal kunt u tekst of binaire gegevens weergeven in hexadecimale notatie.

- Get-Klembord en Set-Klembord-cmdlets zijn toegevoegd aan de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module; ze vereenvoudigen de overdracht van inhoud naar en van een Windows PowerShell-sessie. De Klembord-cmdlets bieden ondersteuning voor afbeeldingen, audio-bestanden, bestandslijsten en tekst.

- Een nieuwe cmdlet Clear-RecycleBin is toegevoegd aan de [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) module; deze lege cartridges die cmdlet blijven het recyclen van de opslaglocatie voor een vaste schijf, waaronder externe stations. Standaard wordt u gevraagd om te bevestigen van een opdracht wissen RecycleBin, omdat de ConfirmImpact-eigenschap van de cmdlet is ingesteld op ConfirmImpact.High.

- Een nieuwe cmdlet New-TemporaryFile, kunt u een tijdelijk bestand als onderdeel van het uitvoeren van scripts maken. Standaard wordt het nieuwe tijdelijke bestand gemaakt ```C:\Users\<user name>\AppData\Local\Temp```.

- De Out-File, Add-inhoud en de cmdlets Set-inhoud hebt nu een nieuwe parameter - NoNewline, die een nieuwe regel na de uitvoer wordt weggelaten.

- De cmdlet New-Guid maakt gebruik van de .NET Framework-Guid-klasse voor het genereren van een GUID is handig bij het schrijven van scripts of DSC-resources.

- Omdat informatie over de bestandsversie misleidend, is met name wanneer een bestand is gevuld, zijn nieuwe FileVersionRaw en ProductVersionRaw scripteigenschappen beschikbaar voor FileInfo-objecten. Bijvoorbeeld, kunt u uitvoeren de volgende opdracht om de waarden van deze eigenschappen voor de powershell.exe, weer te geven waar $pid de proces-ID voor een actieve sessie van Windows PowerShell bevat:  ```Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force```

- Er zijn nieuwe cmdlets Enter PSHostProcess en afsluiten PSHostProcess kunt u fouten opsporen in Windows PowerShell-scripts in processen los van het huidige proces dat wordt uitgevoerd in de Windows PowerShell-console. Uitvoeren van de Enter-PSHostProcess invoeren of koppelen aan een specifiek proces-ID en voer Get-Runspace om terug te keren van de actieve runspaces in het proces. Afsluiten-PSHostProcess loskoppelen van het proces voor wanneer u bent klaar opsporen van fouten in het script in het proces worden uitgevoerd.

- Een nieuwe cmdlet voor Wait-foutopsporing is toegevoegd aan de [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) module. U kunt wachten-foutopsporing als u wilt een script in het foutopsporingsprogramma stoppen voordat u de volgende instructie uitvoert in het script uitvoeren.

- Het foutopsporingsprogramma van Windows PowerShell-werkstroom biedt nu ondersteuning voor opdracht of het tabblad voltooiing, en u kunt fouten opsporen in de geneste werkstroomfuncties. U kunt nu ook op **Ctrl + Break** het foutopsporingsprogramma invoeren in een script uit te voeren, zowel lokale als externe sessies en een werkstroomscript.

- Een Debug-Job-cmdlet is toegevoegd aan de [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) module fouten opsporen in actieve taak scripts voor Windows PowerShell-werkstroom, achtergrond en taken die in externe sessies worden uitgevoerd.

- Een nieuwe status, AtBreakpoint, is toegevoegd voor Windows PowerShell-taken. De status van de AtBreakpoint is van toepassing wanneer een taak wordt uitgevoerd een script dat set onderbrekingspunten bevat en het script een onderbrekingspunt is bereikt. Wanneer een taak is gestopt op een onderbrekingspunt foutopsporing, moet u de taak fouten opsporen door de cmdlet Debug-taak wordt uitgevoerd.

- Windows PowerShell 5.0 implementeert ondersteuning voor meerdere versies van een enkel Windows PowerShell-module in dezelfde map in $PSModulePath. Een eigenschap RequiredVersion is toegevoegd aan de klasse ModuleSpecification om u te helpen krijgt u de gewenste versie van een module. Deze eigenschap is sluiten elkaar wederzijds uit met de eigenschap ModuleVersion. RequiredVersion wordt nu ondersteund als onderdeel van de waarde van de parameter FullyQualifiedName van de Get-Module, Import-Module en Remove-Module-cmdlets.

- U kunt nu module versie validatie uitvoeren door de cmdlet Test-ModuleManifest.

- Resultaten van de cmdlet Get-opdracht weer nu een kolom versie. een nieuwe versie-eigenschap is toegevoegd aan de klasse CommandInfo. GET-opdracht laat zien opdrachten van meerdere versies van dezelfde module. De eigenschap Version maakt ook deel uit van afgeleide klassen van CmdletInfo: CmdletInfo en ApplicationInfo.

- GET-opdracht heeft een nieuwe parameter, - ShowCommandInfo, die informatie als PSObjects ShowCommand retourneert. Dit is vooral nuttig functionaliteit voor wanneer opdracht weergeven met behulp van Windows PowerShell voor externe toegang in Windows PowerShell ISE wordt uitgevoerd. De parameter - ShowCommandInfo vervangt de bestaande functie Get-SerializedCommand in de module Microsoft.PowerShell.Utility, maar het script Get-SerializedCommand is nog steeds beschikbaar voor de ondersteuning voor downlevel-scripts.

- Een nieuwe Get-ItemPropertyValue-cmdlet kunt u de waarde van een eigenschap niet verkrijgen zonder een puntnotering. In oudere versies van Windows PowerShell kunt u bijvoorbeeld de volgende opdracht uit om de waarde van de eigenschap toepassingsbasis van de registersleutel PowerShellEngine uitvoeren: **(Get-ItemProperty-pad HKLM:\\SOFTWARE\\ Microsoft\\PowerShell\\3\\PowerShellEngine-ApplicationBase naam). ApplicationBase**. Vanaf Windows PowerShell 5.0, kunt u uitvoeren **Get-ItemPropertyValue-pad HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine-naam ApplicationBase** .

- De Windows PowerShell-console gebruikt nu syntaxiskleuren, net zoals in de Windows PowerShell ISE.

- Een nieuwe systeemtaak-module bevat cmdlets waarmee u kunt de switch, virtuele LAN (VLAN) en basic Layer 2-switch-poort netwerkconfiguratie toepassen op Windows Server 2012 R2-logo gecertificeerde netwerkswitches.

- De parameter FullyQualifiedName is toegevoegd voor Import-Module en Remove-Module-cmdlets voor de ondersteuning van meerdere versies van een module voor enkele opslaan.

- Help opslaan, Update-Help, Import-PSSession, Export-PSSession en Get-opdracht hebt een nieuwe parameter FullyQualifiedModule van het type ModuleSpecification. Deze parameter om op te geven van een module met de volledig gekwalificeerde naam toevoegen.

- De waarde van **$PSVersionTable.PSVersion** is bijgewerkt naar 5.0.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Nieuwe functies in Windows PowerShell Desired State Configuration

- Verbeteringen van de Windows PowerShell-taal kunnen u Windows PowerShell Desired State Configuration (DSC) resources definiëren met behulp van klassen. Sleutelwoorden import-dscresource bieden is nu een waar dynamische sleutelwoord; Windows PowerShell parseert de opgegeven module'™ s basismodule, zoeken naar klassen die het kenmerk sleutelwoorden dscresource bieden bevatten. U kunt nu klassen gebruiken voor het definiëren van DSC-resources, die geen een MOF-bestand of een submap sleutelwoorden dscresource bieden in de modulemap vereist is. Een Windows PowerShell-module-bestand kan meerdere DSC-resource-klassen bevatten.

- Een nieuwe parameter, ThrottleLimit, is toegevoegd aan de volgende cmdlets in de module PSDesiredStateConfiguration. De parameter ThrottleLimit om op te geven van het aantal doelcomputers of apparaten waarop u de opdracht te laten werken op hetzelfde moment wilt toevoegen.

    -   Get-DscConfiguration

    -   Get-DscConfigurationStatus

    -   Get-DscLocalConfigurationManager

    -   Restore-DscConfiguration

    -   Test-DscConfiguration

    -   Vergelijk-DscConfiguration

    -   Publiceren-DscConfiguration

    -   Set-DscLocalConfigurationManager

    -   Start-DscConfiguration

    -   Update-DscConfiguration

- Met het centrale DSC foutrapportage, is uitgebreide foutinformatie niet alleen geregistreerd in de event log, maar deze kan worden verzonden naar een centrale locatie voor latere analyse. U kunt deze centrale locatie voor het opslaan van DSC-configuratiefouten die zijn opgetreden voor elke server in hun omgeving. Nadat de rapportserver is gedefinieerd in het meta-configuratie, worden alle fouten verzonden naar de rapportserver en vervolgens opgeslagen in een database. U kunt deze functionaliteit, ongeacht of er een doelknooppunt is geconfigureerd voor het ophalen van configuraties van een pull-server instellen.

- Verbeteringen in Windows PowerShell ISE vereenvoudigen ontwerpen van DSC-resource. U kunt nu het volgende doen.

    -   Lijst met alle DSC-resources binnen een **configuratie** of **knooppunt** blokkeren door in te voeren **Ctrl + spatie** op een lege regel in het blok.

    -   Automatisch aanvullen van resource-eigenschappen van de **opsomming** type.

    -   Automatische aanvulling op de **DependsOn** eigenschap van DSC-resources, op basis van andere resource-exemplaren in de configuratie.

    -   Verbeterde tab-aanvulling van de waarden van de resource-eigenschappen.

- Een gebruiker kan een resource onder een opgegeven set referenties nu uitvoeren door toe te voegen de **PSDscRunAsCredential** kenmerk aan een knooppunt-blok. Bijvoorbeeld, PSDscRunAsCredential = Get-Credential Contoso\\DscUser. Deze functie is handig voor het maken van configuraties die worden uitgevoerd van Windows Installer en uitvoerbare installatieprogramma's, toegang tot de registercomponent per gebruiker of andere taken buiten de huidige gebruikerscontext uitvoeren.

- Er is een 32-bits (x86-indeling) ondersteuning toegevoegd voor de **configuratie** trefwoord.

- Windows PowerShell biedt nu ondersteuning voor aangepaste Help-informatie voor DSC-configuraties, gedefinieerd door toe te voegen \[CmdletBinding()] voor de functie gegenereerde configuratie.

- Een nieuwe **DscLocalConfigurationManager** kenmerk wordt aangegeven dat een configuratie-blok een meta-configuratie, dat wordt gebruikt voor het configureren van de DSC Local Configuration Manager. Dit kenmerk wordt een configuratie met alleen de items die de DSC Local Configuration Manager configureren beperkt. Tijdens de verwerking van deze configuratie genereert een \*. meta.mof-bestand dat wordt verzonden naar de juiste doelknooppunten door de cmdlet Set-DscLocalConfigurationManager.

- Gedeeltelijke configuraties zijn nu toegestaan in Windows PowerShell 5.0. Van configuratiedocumenten kunt u naar een knooppunt in fragmenten leveren. Voor een knooppunt voor het ontvangen van meerdere fragmenten van een configuratiedocument, het knooppunt '™ s Local Configuration Manager moet eerst worden ingesteld om op te geven van het verwachte aantal fragmenten

- Synchronisatie van cross-computer is er nieuw in DSC in Windows PowerShell 5.0. Met behulp van de ingebouwde WaitFor\* resources (**WaitForAll**, **WaitForAny**, en **WaitForSome**), kunt u nu afhankelijkheden op computers opgeven tijdens de configuratie wordt uitgevoerd, zonder externe indelingen. Deze bronnen vindt u knooppunt-naar-knooppunt synchronisatie met behulp van CIM-verbindingen via het protocol WS-Man. Een configuratie kunt wachten op een andere computer'™ s de status van de specifieke resource te wijzigen.

- Alleen Enough Administration (JEA), een nieuwe functie van de delegatie-beveiliging, maakt gebruik van DSC en Windows PowerShell beperkte runspaces veilig om ondernemingen te helpen gegevens verloren gaan of inbreuk op door werknemers, of opzettelijke en niet. Zie voor meer informatie over JEA, met inbegrip van waar u de xJEA DSC-resource, kunt downloaden [Just Enough Administration, stap voor stap](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx).

- De volgende nieuwe-cmdlets zijn toegevoegd aan de module PSDesiredStateConfiguration.

    -   Een nieuwe cmdlet voor Get-DscConfigurationStatus haalt informatie op hoog niveau over de configuratiestatus van een doelknooppunt. U vindt de status van de laatste of van alle configuraties.

    -   Een nieuwe cmdlet voor vergelijken-DscConfiguration vergelijkt een opgegeven configuratie met de huidige status van een of meer doelknooppunten.

    -   Een nieuwe cmdlet van publiceren-DscConfiguration een MOF-configuratiebestand worden gekopieerd naar een doelknooppunt, maar de configuratie is niet van toepassing. De configuratie wordt toegepast tijdens de volgende consistentie, of wanneer u de cmdlet Update-DscConfiguration uitvoeren.

    -   Een nieuwe cmdlet Test-DscConfiguration kunt u verifiëren dat een resulterende configuratie komt overeen met de gewenste configuratie, retourneert True als de configuratie komt overeen met de gewenste configuratie, of ONWAAR als de werkelijke niet overeenkomt met de gewenste de configuratie.

    -   Een nieuwe Update-DscConfiguration cmdlet wordt een configuratie moeten worden verwerkt. Als de Local Configuration Manager in de pull-modus, krijgt de cmdlet de configuratie van de pull-server voordat u deze toepast.

### <a name="new-features-in-windows-powershell-ise"></a>Nieuwe functies in Windows PowerShell ISE

- U kunt nu externe Windows PowerShell-scripts en bestanden in een lokale kopie van Windows PowerShell ISE kunt bewerken door het uitvoeren van de Enter-PSSession naar een externe sessie starten op de computer die '™ s opslaan van de bestanden die u wilt bewerken, en vervolgens voert **PSEdit <path and file name on the remote computer>**. Deze functie vergemakkelijkt bewerken Windows PowerShell-bestanden die zijn opgeslagen op de Server Core-installatieoptie van Windows Server, waar Windows PowerShell ISE kan niet worden uitgevoerd.

- De cmdlet Start-Transcript wordt nu ondersteund in Windows PowerShell ISE.

- U kunt nu fouten opsporen in externe scripts in Windows PowerShell ISE.

- Een nieuwe opdracht, **alle opsplitsen** (Ctrl + B), wordt in het foutopsporingsprogramma voor zowel lokale als extern uitvoeren van scripts.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Nieuwe functies in Windows PowerShell Web Services (Management OData IIS-extensie)

- Vanaf Windows PowerShell 5.0, kunt u een set op basis van de functionaliteit die door een opgegeven OData-eindpunt, door de cmdlet Export-ODataEndpointProxy, gevonden in de nieuwe Windows PowerShell-cmdlets genereren [ Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) module.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Oplossingen voor problemen die aandacht vereisen in Windows PowerShell 5.0

- Windows PowerShell 5.0 bevat een nieuw COM-implementatie, biedt belangrijke prestatieverbeteringen wanneer u met COM-objecten werkt. Zie voor een videodemonstratie van het effect [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ).

- Aanzienlijke prestatieverbeteringen zijn aangebracht aan de eerste tab-Aanvulling in een Windows PowerShell-sessie, tabblad voltooiingstijd verkorten door bijna 500 ms.

## <a name="new-features-in-windows-powershell-40"></a>Nieuwe functies in Windows PowerShell 4.0
Windows PowerShell 4.0 is achterwaarts compatibel. -Cmdlets, providers, -modules, -modules, scripts, functies en -profielen die zijn ontworpen voor Windows PowerShell 3.0 en Windows PowerShell 2.0 werken in Windows PowerShell 4.0 zonder wijzigingen.

Windows PowerShell 4.0 wordt standaard geïnstalleerd op Windows 8.1 en Windows Server 2012 R2. Voor het installeren van Windows PowerShell 4.0 op Windows 7 met SP1 of Windows Server 2008 R2, download en installeer [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855). Moet u de details van de download lezen en voldoen aan alle systeemvereisten, voordat u Windows Management Framework 4.0 installeren.

- [Nieuwe functies in Windows PowerShell](#new-features-in-windows-powershell-1)
- [Nieuwe functies in Windows PowerShell Integrated Scripting Environment (ISE)](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Nieuwe functies in Windows PowerShell-werkstroom](#new-features-in-windows-powershell-workflow)
- [Nieuwe functies in Windows PowerShell-webservices](#new-features-in-windows-powershell-web-services)
- [Nieuwe functies in Windows PowerShell-webtoegang](#new-features-in-windows-powershell-web-access)
- [Oplossingen voor problemen die aandacht vereisen in Windows PowerShell 4.0](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0 bevat de volgende nieuwe functies.

### <a name="new-features-in-windows-powershell"></a>Nieuwe functies in Windows PowerShell

- **Windows PowerShell Desired State Configuration** (DSC) is een nieuw managementsysteem in Windows PowerShell 4.0 waarmee de implementatie en het beheer van configuratiegegevens voor softwareservices en de omgeving waarin de services worden uitgevoerd. Zie voor meer informatie over DSC [aan de slag met Windows PowerShell Desired State Configuration](https://technet.microsoft.com/library/c134aa32-b085-4656-9a89-955d8ff768d0).

- **Help opslaan** nu zorgt voor flinke besparingen help voor modules die op externe computers zijn geïnstalleerd. U kunt Help opslaan naar Help-module downloaden van een internetverbinding client (waarvoor niet alle van de modules waarvoor u hulp wilt worden altijd geïnstalleerd) en kopieer vervolgens de opgeslagen Help voor een externe gedeelde map of een externe computer waarop geen Internet de toegang.

- De Windows PowerShell-foutopsporing is verbeterd zodat foutopsporing van Windows PowerShell-werkstromen, evenals de scripts die worden uitgevoerd op externe computers. Windows PowerShell-werkstromen kunnen nu worden opgespoord op het scriptniveau van het uit de Windows PowerShell-opdrachtregel of de Windows PowerShell ISE. Windows PowerShell-scripts, met inbegrip van scriptwerkstromen, kunnen nu via externe sessies worden opgespoord. Externe foutopsporing sessies blijven behouden via externe Windows PowerShell-sessies die worden losgekoppeld en later opnieuw verbinding gemaakt.

- Een **RunNow** parameter voor **Register-ScheduledJob** en **Set-ScheduledJob** elimineert de noodzaak om in te stellen van een onmiddellijke startdatum en tijd voor taken met behulp van de **Trigger** parameter.

- **Invoke-RestMethod** en **Invoke-WebRequest** nu kunt u alle headers instellen met behulp van de Headers-parameter. Hoewel deze parameter altijd al bestond, is een van de verschillende parameters voor de web-cmdlets dat heeft geresulteerd in fouten of uitzonderingen.

- **Get-Module** heeft een nieuwe parameter **FullyQualifiedName**, van het type **ModuleSpecification\[]**. De **FullyQualifiedName** parameter van Get-Module nu kunt u opgeven van een module met behulp van de module-naam, versie en (optioneel) de GUID.

- De standaardinstelling voor het beleid van kan worden uitgevoerd op Windows Server 2012 R2 is **RemoteSigned**. Op Windows 8.1 is er geen wijziging in standaard instellen.

- Vanaf Windows PowerShell 4.0, wordt aanroepen van de methode met behulp van dynamische methodenamen ondersteund. U kunt een variabele gebruiken voor het opslaan van de naam van een methode, en vervolgens dynamisch de methode worden aangeroepen door het aanroepen van de variabele.

- Asynchrone werkstroomtaken niet meer worden verwijderd wanneer de time-outperiode die is opgegeven door de **PSElapsedTimeoutSec** algemene werkstroomparameter is verstreken.

- Een nieuwe parameter **RepeatIndefinitely**, is toegevoegd aan de **New-JobTrigger** en **Set-JobTrigger** cmdlets. Dit elimineert de noodzaak van het opgeven van een **TimeSpan.MaxValue** waarde voor de **RepetitionDuration** parameter voor een geplande taak meerdere keren voor onbepaalde tijd uitgevoerd.

- Een **Passthru** parameter is toegevoegd aan de **inschakelen-JobTrigger** en **Disable-JobTrigger** cmdlets. De parameter Passthru wordt eventuele objecten die zijn gemaakt of gewijzigd door de opdracht weergegeven.

- De namen van parameters voor het opgeven van een werkgroep in de **Computer toevoegen** en **Remove-Computer** cmdlets nu consistent zijn. Beide cmdlets de parameter nu gebruiken **werkgroepnaam**.

- Een nieuwe algemene parameter **PipelineVariable**, is toegevoegd. PipelineVariable kunt u de resultaten van een opdracht doorgesluisd (of een deel van een piped opdracht) opslaan als een variabele die kan worden doorgegeven via de rest van de pijplijn.

- Verzameling filteren met behulp van een syntaxis van de methode wordt nu ondersteund. Dit betekent dat u nu een verzameling van objecten met behulp van de vereenvoudigde syntaxis, vergelijkbaar met dat van Where() of Where-Object, opgemaakt als een methodeaanroep kunt filteren. Hier volgt een voorbeeld: (Get-Process) .waarbij ({$_. Geef de naam - overeenkomen met 'powershell'})

- De **Get-Process** cmdlet heeft een nieuwe switchparameter **IncludeUserName**.

- Een nieuwe cmdlet **Get-FileHash**, die de hash van een bestand in een van de verschillende notaties voor een opgegeven bestand retourneert, is toegevoegd.

- In Windows PowerShell 4.0, als een module gebruikt de **DefaultCommandPrefix** sleutel in het manifest, of als de gebruiker de invoer een module met de **voorvoegsel** parameter, de **ExportedCommands**eigenschap van de module bevat de opdrachten in de module met het voorvoegsel. Wanneer u de opdrachten uitvoert met behulp van de syntaxis modulegekwalificeerde, ModuleName\\CommandName, door de opdrachtnamen van de moeten de toevoeging van het voorvoegsel.

- De waarde van **$PSVersionTable.PSVersion** is bijgewerkt naar 4.0.

- **WHERE()** operator gedrag is gewijzigd. `Collection.Where('property -match name')` accepteert een tekenreeksexpressie in de indeling `"Property -CompareOperator Value"` wordt niet meer ondersteund. Echter, de **Where()** operator accepteert expressies voor verbindingsreeksen in de indeling van een scriptblock; dit wordt nog steeds ondersteund.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Nieuwe functies in Windows PowerShell Integrated Scripting Environment (ISE)

- Windows PowerShell ISE ondersteunt zowel Windows PowerShell-werkstroom foutopsporing als externe script opsporen van fouten.

- IntelliSense-ondersteuning toegevoegd voor Windows PowerShell Desired State Configuration-providers en configuraties.

### <a name="new-features-in-windows-powershell-workflow"></a>Nieuwe functies in Windows PowerShell-werkstroom

- Er is ondersteuning toegevoegd voor een nieuwe **PipelineVariable** algemene parameter in de context van iteratieve pijplijnen, zoals die worden gebruikt door System Center Orchestrator; dat wil zeggen, pijplijnen die gewoon links-naar-rechts, plaats worden opdrachten uitgevoerd afgewisseld met behulp van streaming.

- ParameterBinding is aanzienlijk uitgebreid om te werken buiten tabblad voltooiing scenario's, zoals met opdrachten die niet zijn opgenomen in de huidige runspace.

- Ondersteuning voor aangepaste container activiteiten is toegevoegd aan Windows PowerShell-werkstroom. Als een activiteitsparameter van de typen is **activiteit**, **activiteit\[]**' 'is een algemene verzameling van de activiteiten ' of door de gebruiker een scriptblok is opgegeven als argument, klikt u vervolgens Windows PowerShell-werkstroom converteert het scriptblok naar XAML, net als bij normale Windows PowerShell-script-naar-workflow compilatie.

- Na het vastlopen van een Windows PowerShell-werkstroom automatisch opnieuw verbinding maakt met beheerde knooppunten.

- U kunt nu beperken **Foreach-Parallel** activiteit instructies met behulp van de **ThrottleLimit** eigenschap.

- De **ErrorAction** algemene parameter heeft een nieuwe geldige waarde **onderbreken**, dat wil zeggen uitsluitend bedoeld voor werkstromen.

- Een werkstroom-eindpunt nu automatisch gesloten als er geen actieve sessies, geen taken in uitvoering en er geen taken in behandeling. Deze functie bespaart bronnen op de computer die als de werkstroomserver fungeert wanneer de automatische afsluiting voorwaarden is voldaan.

### <a name="new-features-in-windows-powershell-web-services"></a>Nieuwe functies in Windows PowerShell-webservices

- Wanneer er een fout optreedt in Windows PowerShell Web Services (PSWS, ook wel Management OData IIS-extensie), terwijl wordt een cmdlet uitgevoerd, meer gedetailleerde fout berichten worden geretourneerd voor de oproepende functie. Bovendien foutcodes Volg [richtlijnen voor de code van de Windows Azure REST API fout](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx).

- Een eindpunt kunt nu de API-versie te definiëren, evenals afdwingen dat een specifieke API-versie. Wanneer versie verschillen tussen client en server optreden, worden fouten weergegeven voor zowel de client en de server.

- Beheer van het schema van de verzending is vereenvoudigd door het automatisch genereren van waarden voor de ontbrekende velden in het schema. Generatie gebeurt, als een handig startpunt, zelfs als het schema verzending niet bestaat.

- Type verwerken in PSWS is verbeterd ter ondersteuning van typen die het gebruik van een andere constructor dan de standaardconstructor door zich op dezelfde manier naar de **PSTypeConverter** in Windows PowerShell. Hiermee kunt u complexe typen met PSWS gebruiken.

- PSWS kunnen nu het uitbreiden van een verbonden exemplaar tijdens het uitvoeren van een query. Voor grotere binaire inhoud (zoals afbeeldingen, audio of video), de kosten voor gegevensoverdracht is van belang en is het beter om over te dragen van binaire gegevens zonder te coderen. Benoemde resource streams PSWS gebruikt voor het overdragen zonder te coderen. De benoemde bronstream is een eigenschap van een entiteit van de **Edm.Stream** type. Elke stroom met de naam resource heeft een afzonderlijke URI voor GET- of UPDATE-bewerkingen.

- OData-acties hebben nu een mechanisme voor het aanroepen van niet-CRUD (maken, lezen, bijwerken en verwijderen) methoden op een resource. U kunt een actie activeren door een HTTP POST-aanvraag te verzenden naar de URI die is gedefinieerd voor de actie. De parameters voor de actie worden gedefinieerd in de hoofdtekst van de POST-aanvraag.

- Om te worden consistent zijn met Windows Azure-richtlijnen, moeten alle URL's worden vereenvoudigd. Een wijziging die is opgenomen in **sleutel als Segment** kan één sleutels wordt weergegeven als segmenten. Houd er rekening mee dat verwijzingen die gebruikmaken van meerdere sleutelwaarden die zijn vereist voor door komma's gescheiden waarden in de haakjes, net als voorheen.

- Vóór deze release van PSWS, het alleen bewerkingen is manier om uit te voeren maken, bijwerken of verwijderen om aan te roepen, Post, Put of verwijderen van een resource op het hoogste niveau. Nieuw in deze release van PSWS toestaan opgenomen resourcebewerkingen dat gebruikers de dezelfde resultaten controleren terwijl het bereiken van de dezelfde resource minder rechtstreeks nadert alsof deze resources zijn opgenomen.

### <a name="new-features-in-windows-powershell-web-access"></a>Nieuwe functies in Windows PowerShell-webtoegang

- U kunt verbreken en opnieuw verbinding maken met bestaande sessies in de Windows PowerShell-webtoegang op basis van de web console. Een **opslaan** knop in de webconsole kunt u een sessie verbreken zonder deze te verwijderen en opnieuw verbinding maken met de sessie een andere tijd.

- Standaard-parameters kunnen worden weergegeven op de pagina aanmelden. Als u wilt weergeven standaardparameters, configureren van waarden voor alle instellingen weergegeven in de **optionele verbindingsinstellingen** gebied van de aanmeldingspagina in een bestand met de naam **web.config**. U kunt de **web.config** bestand om alle optionele verbindingsinstellingen, met uitzondering van een tweede of een alternatieve set referenties te configureren.

- U kunt autorisatieregels op afstand voor Windows PowerShell-webtoegang beheren in Windows Server 2012 R2. De **Add-PswaAuthorizationRule** en **Test-PswaAuthorizationRule** cmdlets hebben nu een parameter Credential waarmee beheerders voor het beheren van autorisatieregels vanaf een externe computer of in een Windows PowerShell Web Access-sessie.

- U kunt nu meerdere sessies van Windows PowerShell-webtoegang in een enkele browsersessie hebben met behulp van een nieuw browsertabblad voor elke sessie. U moet niet meer openen van een nieuwe browsersessie verbinding maken met een nieuwe sessie in de Windows PowerShell web gebaseerde beheerconsole.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Oplossingen voor problemen die aandacht vereisen in Windows PowerShell 4.0

- **Get-Counter** nu items met een aanhalingsteken in de Franse edities van Windows kunt terugkeren.

- U kunt nu zien de **GetType** methode voor gedeserialiseerde objecten.

- **#Requires** instructies kunnen gebruikers vereisen Administrator-rechten voor toegang, nu indien nodig.

- De **importeren Csv** cmdlet nu lege regels worden genegeerd.

- Een probleem waarbij Windows PowerShell ISE te veel geheugen gebruikt als u werkt met een **Invoke-WebRequest** opdracht is opgelost.

- **Get-Module** toont nu moduleversies in een **versie** kolom.

- Remove-Item - Recurse nu items verwijderen uit submappen zoals verwacht.

- Een **gebruikersnaam** eigenschap is toegevoegd aan **Get-Process** uitvoer van objecten.

- De **Invoke-RestMethod** cmdlet retourneert nu alle beschikbare resultaten.

- **Add Member** nu wordt van kracht op hashtabellen, zelfs als de hashtabellen nog niet is geopend.

- **Select-Object - Vouw** langer mislukt of wordt een uitzondering gegenereerd als de waarde van de eigenschap null of leeg zijn is.

- **Get-Process** kan nu worden gebruikt in een pijplijn met andere opdrachten die aan de **ComputerName** eigenschap van de objecten.

- **ConvertTo Json** en **ConvertFrom-Json** nu termen tussen dubbele aanhalingstekens kunt accepteren en de foutberichten zijn nu lokaliseerbare.

- **Get-Job** nu retourneert een voltooid taken, zelfs in nieuwe sessies geplande.

- Problemen met koppelen en ontkoppelen van VHD's met behulp van de **bestandssysteem** -provider in Windows PowerShell 4.0 zijn hersteld. Windows PowerShell is nu in staat om te detecteren van nieuwe stations wanneer ze zijn gekoppeld in dezelfde sessie.

- U moet niet meer expliciet laden **ScheduledJob** of **werkstroom** modules om te werken met hun taaktypen.

- Verbeteringen zijn aangebracht aan het proces van het importeren van werkstromen die geneste werkstromen; definiëren Dit proces is nu sneller.

## <a name="new-features-in-windows-powershell-30"></a>Nieuwe functies in Windows PowerShell 3.0
Windows PowerShell 3.0 bevat de volgende nieuwe functies.

- [Windows PowerShell-werkstroom](#windows-powershell-workflow)
- [Windows PowerShell-internettoegang](#windows-powershell-web-access)
- [Nieuwe functies van Windows PowerShell ISE](#new-windows-powershell-ise-features)
- [Ondersteuning voor Microsoft .NET Framework 4.0](#support-for-microsoft-net-framework-4)
- [Ondersteuning voor Windows Preinstallation Environment](#support-for-windows-preinstallation-environment)
- [Niet-verbonden sessies](#disconnected-sessions)
- [Robuuste sessie verbinding](#robust-session-connectivity)
- [Bij te werken Help-systeem](#updatable-help-system)
- [Verbeterde Online-Help](#enhanced-online-help)
- [CIM-integratie](#cim-integration)
- [Sessie-configuratiebestanden](#session-configuration-files)
- [Geplande taken en taak Scheduler-integratie](#scheduled-jobs-and-task-scheduler-integration)
- [Verbeteringen in Windows PowerShell-taal](#windows-powershell-language-enhancements)
- [Nieuwe Core-Cmdlets](#new-core-cmdlets)
- [Verbeteringen voor bestaande essentiële Cmdlets en Providers](#improvements-to-existing-core-cmdlets-and-providers)
- [Externe module-import en detectie](#remote-module-import-and-discovery)
- [Verbeterde Tab-aanvulling](#enhanced-tab-completion)
- [Module automatisch geladen](#module-auto-loading)
- [Verbeteringen van de module-ervaring](#module-experience-improvements)
- [Vereenvoudigde opdracht detectie](#simplified-command-discovery)
- [Verbeterde logboekregistratie van diagnostische gegevens en ondersteuning voor groepen van beleid](#improved-logging-diagnostics-and-group-policy-support)
- [Opmaak- en uitvoer verbeteringen](#formatting-and-output-improvements)
- [Verbeterde Console Host-ervaring](#enhanced-console-host-experience)
- [Nieuwe Cmdlet en het hosten van API 's](#new-cmdlet-and-hosting-apis)
- [Verbeterde prestaties](#performance-improvements)
- [Uitvoeren als- en ondersteuning voor gedeelde hostgroep](#runas-and-shared-host-support)
- [Verwerking van verbeteringen in speciaal teken](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell-werkstroom
Windows PowerShell-werkstroom zorgt de kracht van Windows Workflow Foundation in Windows PowerShell. U kunt schrijven van werkstromen in XAML of in de Windows PowerShell-taal en voert ze net zoals u zou een cmdlet uitvoert. De [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet haalt workflw opdrachten en de [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet help voor werkstromen opgehaald.

Werkstromen zijn reeksen multicomputer management-activiteiten met de status van langlopende, herhaalbaar, regelmatig, worden opgestart, onderbreekbaar, suspendable en opnieuw starten. Werkstromen kunnen worden hervat vanaf een opzettelijke wordt onderbroken, zoals netwerkstoringen, een Windows opnieuw starten of een stroomstoring.

Werkstromen zijn ook draagbare; ze kunnen worden geëxporteerd als of geïmporteerd uit de XAML-bestanden. U kunt aangepaste sessieconfiguraties waarmee werkstromen of activiteiten in een werkstroom wordt uitgevoerd door de gedelegeerde of onderliggende gebruikers schrijven.

De volgende zijn de voordelen van Windows PowerShell-werkstroom

- Gesequentieerd, langlopende taken te automatiseren.

- **Externe controle van langlopende taken**. Status en voortgang van activiteiten zijn zichtbaar op elk gewenst moment.

- **Multicomputer management.** Taken als werkstromen tegelijkertijd uitgevoerd op honderden beheerde knooppunten. Windows PowerShell-werkstroom bevat een ingebouwde bibliotheek met algemene Beheerparameters, zoals **PSComputerName**, welke scenario's voor beheer van meerdere computers inschakelen.

- **Enkele taak uitvoeren van complexe processen.** U kunt gerelateerde scripts die een volledige end-to-end-scenario in een enkele werkstroom implementeren combineren.

- **Persistentie.** : een werkstroom wordt opgeslagen (of controle-waarnaar wordt verwezen) op specifieke tijdstippen gedefinieerd door de auteur, zodat u de werkstroom van de laatst vastgelegde taak (of controlepunt) hervatten kunt in plaats van de werkstroom vanaf het begin opnieuw te starten.

- **Robuustheid.** Geautomatiseerd foutherstel. Werkstromen blijven actief na geplande en ongeplande opnieuw wordt opgestart. U kunt werkstroom onderbreekt en hervat u vervolgens de werkstroom vanaf het laatste punt voor persistentie. Werkstroomauteurs kunnen wijzen specifieke activiteiten moet opnieuw worden uitgevoerd bij een storing op een of meer beheerde knooppunten.

- **Mogelijkheid om te verbreken, opnieuw verbinding maken en uitvoeren in niet-verbonden sessies.** Gebruikers kunnen verbinding maken en verbreken van de werkstroomserver, maar de werkstroom wordt continu uitgevoerd. U kunt Meld u af bij de clientcomputer of de clientcomputer opnieuw opstarten en controleren van de werkstroom kan worden uitgevoerd vanaf een andere computer zonder dat de werkstroom wordt onderbroken.

- **Bij het plannen.** Werkstroomtaken kunnen worden gepland, zoals een Windows PowerShell-cmdlet of script.

- **Werkstroom en bandbreedtebeperking van verbinding.** Uitvoering en verbindingen met knooppunten kunnen worden beperkt, waardoor scenario's voor schaalbaarheid en hoge beschikbaarheid.

### <a name="windows-powershell-web-access"></a>Windows PowerShell Web Access
Windows PowerShell-webtoegang is een Windows Server 2012-functie waarmee gebruikers kunnen Windows PowerShell-opdrachten en scripts uitvoeren in een webgebaseerde console. Apparaten die gebruikmaken van de webconsole vereisen geen Windows PowerShell, extern beheer van software of invoegtoepassing browser-installaties. Dat is vereist, is een gateway goed geconfigureerde Windows PowerShell-webtoegang en een browser op het clientapparaat die JavaScript ondersteunt en cookies accepteert.

Zie voor meer informatie, [Windows PowerShell-webtoegang implementeren](http://go.microsoft.com/fwlink/p/?LinkID=221050).

### <a name="new-windows-powershell-ise-features"></a>Nieuwe functies van Windows PowerShell ISE
Voor Windows PowerShell 3.0 en Windows PowerShell Integrated Scripting Environment (ISE) heeft een groot aantal nieuwe functies, zoals IntelliSense opdracht weergeven-venster, een geïntegreerde consolevenster codefragmenten, haakje-koppeling, vouw samenvouwen secties, automatisch moeten worden opgeslagen, onlangs geopende items lijst met, uitgebreide kopiëren, blokkeren kopiëren en volledige ondersteuning voor het schrijven van Windows PowerShell-script-werkstromen. Zie voor meer informatie, [about_Windows_PowerShell_ISE [3]](https://technet.microsoft.com/library/dfa54d47-60c6-4fff-8197-c747e8d411bb).

### <a name="support-for-microsoft-net-framework-4"></a>Ondersteuning voor Microsoft .NET Framework 4
Windows PowerShell is gebouwd op basis van de Common Language Runtime 4.0. Cmdlet, scripts en werkstroomauteurs kunnen de nieuwe Microsoft .NET Framework 4 klassen gebruiken in Windows PowerShell met kenmerken, zoals compatibiliteit van toepassingen en -implementatie, uitbreidingsframework beheerd, parallelle computers, netwerken, Windows Communication Foundation en Windows Workflow Foundation.

### <a name="support-for-windows-preinstallation-environment"></a>Ondersteuning voor Windows Preinstallation Environment
Windows PowerShell 3.0 is een optioneel onderdeel van de Windows Preinstallation Environment (Windows PE) 4.0 voor Windows 8. Windows PE is een minimaal besturingssysteem die een computer waarop geen besturingssysteem en wordt het voorbereid voor de installatie van Windows wordt gestart. Windows PE kan worden gebruikt voor de partitie en harde schijven formatteren, schijfkopieën kopiëren naar een computer en Windows Setup starten vanaf een netwerkshare. Windows PowerShell 3.0 kan worden gebruikt op Windows PE voor het beheren van implementatie, diagnostische gegevens en scenario's voor herstel.

### <a name="disconnected-sessions"></a>Niet-verbonden sessies
Vanaf Windows PowerShell 3.0, worden permanente gebruikers beheerde sessies ('PSSessions') die u maakt met behulp van de cmdlet New-PSSession opgeslagen op de externe computer. Ze zijn niet meer afhankelijk van de sessie waarin ze zijn gemaakt.

U kunt nu een sessie verbreken zonder te onderbreken van de opdrachten die worden uitgevoerd in de sessie. U kunt de sessie sluiten en de computer afsluiten. Later kunt u verbinding kunt maken met de sessie van een andere sessie op hetzelfde of een andere computer.

De **ComputerName** parameter van de [Get-PSSession](https://technet.microsoft.com/library/b2b10531-d0df-4746-b877-e75c09955cb6) cmdlet nu krijgt u alle sessies van de gebruiker die verbinding met de computer maken, zelfs als ze zijn gestart in een andere sessie op een andere computer. U kunt verbinding maken met de sessies, de resultaten van opdrachten, nieuwe opdrachten start en vervolgens de sessie verbreken.

Nieuwe cmdlets toegevoegd ter ondersteuning van de functie niet verbonden sessies met inbegrip van [Disconnect-PSSession](https://technet.microsoft.com/library/f8f95111-612f-4cba-9098-77904b0473d8), [Connect-PSSession](https://technet.microsoft.com/library/b803dd29-f208-4079-80d4-db04d778f060), en Receive-PSSession en nieuwe parameters is toegevoegd aan cmdlets die PSSessions, zoals beheren de **InDisconnectedSession** parameter van de [Invoke-Command](https://technet.microsoft.com/library/906b4b41-7da8-4330-9363-e7164e5e6970) cmdlet.

De functie sessies verbroken wordt alleen ondersteund als de computers op zowel de oorsprong ('client') en het beëindigen van de kanten van de verbinding ('server') wordt uitgevoerd Windows PowerShell 3.0.

### <a name="robust-session-connectivity"></a>Robuuste sessie verbinding
Windows PowerShell 3.0 onverwachte verlies van verbinding tussen de client en server detecteert en probeert opnieuw verbinding en kan worden uitgevoerd automatisch hervat. Als de client / server-verbinding kan niet worden hersteld binnen de toegewezen tijd, de gebruiker op de hoogte is gesteld en de sessie wordt verbroken. Tijdens een poging verbinding te maken, biedt Windows PowerShell continue feedback aan de gebruiker.

Als de niet-verbonden sessie is gestart met behulp van de InvokeCommand, maakt Windows PowerShell u een taak voor de niet-verbonden sessie zodat u gemakkelijk opnieuw verbinding maken met en hervat kan worden uitgevoerd.

Deze functies bieden een meer betrouwbare en herstelbaar voor externe toegang en toestaan dat gebruikers langlopende taken waarvoor robuuste sessies, zoals werkstromen uit te voeren.

### <a name="updatable-help-system"></a>Bij te werken Help-systeem
U kunt nu bijgewerkte help-bestanden voor de cmdlets in uw modules downloaden. De [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet identificeert de meest recente help-bestanden, downloadt u deze vanaf het Internet, ze uitgepakt, valideert ze en installeert u deze in de juiste taalspecifieke-map voor de module.

Voor het gebruik van de bijgewerkte help-bestanden, typt u gewoon `Get-Help`. U hoeft niet opnieuw opstarten van Windows of Windows PowerShell. Om bij te werken help voor modules in de map $pshome, start u Windows PowerShell met de optie 'Als administrator uitvoeren'.

Ter ondersteuning van gebruikers die geen toegang tot Internet en gebruikers achter een firewall, de nieuwe [Help opslaan](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlet help-bestanden downloadt naar een bestand system-map, zoals een bestandsshare. Gebruikers kunnen vervolgens gebruiken de [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet om op te halen van bijgewerkte help-bestanden van de bestandsshare.

U kunt de [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet om bij te werken help-bestanden voor alle of bepaalde modules in alle ondersteunde UI culturen. U kunt zelfs plaatst een [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) opdracht in uw Windows PowerShell-profiel. Standaard downloadt Windows PowerShell help-bestanden voor een module niet meer dan één keer per dag.

Windows 8 en Windows Server 2012-modules bevatten geen help-bestanden. Voor het downloaden van de meest recente help-bestanden, typt u `Update-Help`. Typ voor meer informatie `Get-Help` (zonder parameters) of Zie [about_Updatable_Help](https://technet.microsoft.com/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

Wanneer de help-bestanden voor een cmdlet zijn niet geïnstalleerd op de computer, de [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) cmdlet worden nu automatisch gegenereerde help weergegeven. De help voor het automatisch gegenereerde, bevat de opdrachtsyntaxis en instructies voor het gebruik van de [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) cmdlet helpbestanden te downloaden.

Een module-auteur kan ondersteunen bij te werken Help voor de module. U kunt de help-bestanden opnemen in de module en bij te werken Help gebruiken deze bijwerkt of laat de help-bestanden en gebruik bij te werken Help ze te installeren. Zie voor meer informatie over ondersteunende bij te werken Help [ondersteunende bij te werken Help](http://go.microsoft.com/FWLink/?LinkID=242129) in MSDN.

### <a name="enhanced-online-help"></a>Verbeterde Online-Help
De online help van Windows PowerShell is een waardevolle bron voor alle gebruikers, maar het is vooral belangrijk voor gebruikers die zich niet of kunnen de bijgewerkte help-bestanden niet installeren.

Als online-help voor een Windows PowerShell-cmdlet, typt u:

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell opent de online versie van het help-onderwerp in uw standaardinternetbrowser.

De **Get-Help-Online** functie in Windows PowerShell 3.0 is nu nog krachtiger omdat het werkt, zelfs als help-bestanden voor de cmdlet zijn niet geïnstalleerd op de computer. De **Get-Help-Online** functie haalt de URI voor de online help-onderwerp van de eigenschap HelpUri van cmdlets en geavanceerde functies.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

Vanaf Windows PowerShell 3.0, auteurs van C# cmdlets kunt vullen de **HelpUri** eigenschap met het maken van een **HelpUri** kenmerk voor de cmdlet-klasse. Auteurs van geavanceerde functies kunnen definiëren een **HelpUri** eigenschap op de **CmdletBinding** kenmerk. De waarde van de **HelpUri** eigenschap moet beginnen met 'http' of 'https'.

U kunt ook een **HelpUri** waarde in de eerste gerelateerde koppeling van een XML-indeling cmdlet help-bestand of de. De richtlijn van de koppeling van de help op basis van een opmerking in een functie.

Zie voor meer informatie over ondersteunende online help [ondersteunende Online Help](http://go.microsoft.com/fwlink/?LinkId=242132) in MSDN.

### <a name="cim-integration"></a>CIM-integratie
Windows PowerShell 3.0 bevat ondersteuning voor de CIM Common Information Model (), waarmee u algemene definities van beheergegevens voor systemen, netwerken, toepassingen en services, zodat ze het uitwisselen van beheergegevens tussen heterogene-systemen. Ondersteuning voor CIM in Windows PowerShell 3.0, inclusief de mogelijkheid om te maken van Windows PowerShell-cmdlets op basis van nieuwe of bestaande CIM-klassen, opdrachten op basis van de definitie van de cmdlet XML-bestanden, ondersteuning voor CIM .NET Framework. API, CIM-cmdlets voor beheer en 2.0 WMI-providers.

### <a name="session-configuration-files"></a>Sessie-configuratiebestanden
Vanaf Windows PowerShell 3.0, kunt u een aangepaste sessieconfiguratie ontwerpen met behulp van een bestand. Het configuratiebestand van de nieuwe sessie kunt u de omgeving van sessies die gebruikmaken van de sessieconfiguratie, inclusief welke modules, scripts, bepalen en format-bestanden worden geladen in sessies, welke gebruikers van de elementen cmdlets en -taal gebruiken kunnen, welke modules en scripts die ze kunnen uitvoeren en welke variabelen die ze kunnen zien.

U kunt een sessie waarin gebruikers kunnen alleen de cmdlets uitgevoerd vanaf een bepaalde module of een sessie waarin gebruikers hebben volledige taal, toegang tot alle modules en toegang tot de scripts die geavanceerde taken uitvoeren ontwerpen.

In eerdere versies van Windows PowerShell, controle op dit niveau is alleen beschikbaar voor degenen die kan worden geschreven een C# programma of script complexe opstarten. Elk lid van de groep Administrators op de computer kan nu een sessieconfiguratie aanpassen met behulp van een configuratiebestand.

Voor het maken van een sessie-configuratiebestand gebruikt de [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866) cmdlet. Als u wilt het configuratiebestand van de sessie op een sessieconfiguratie toepassen, gebruikt u de [Register-PSSessionConfiguration](https://technet.microsoft.com/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) of [Set-PSSessionConfiguration](https://technet.microsoft.com/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) cmdlets.

Zie voor meer informatie, [about_Session_Configuration_Files](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.0) en [New-PSSessionConfigurationFile](https://technet.microsoft.com/library/5f3e3633-6e90-479c-aea9-ba45a1954866).

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>Geplande taken en taak Scheduler-integratie
U kunt nu Windows PowerShell-achtergrondtaken plannen en deze beheren in Windows PowerShell en in Task Scheduler.

Windows PowerShell geplande taken zijn een handige hybride van Windows PowerShell-achtergrondtaken en Task Scheduler-taken.

Net als Windows PowerShell-achtergrondtaken, geplande taken asynchroon op de achtergrond uitgevoerd. Exemplaren van geplande taken hebt voltooid, kunnen worden beheerd met behulp van de taak-cmdlets, zoals [Start-Job](https://technet.microsoft.com/library/2bc04935-0deb-4ec0-b856-d7290cca6442) en [Get-Job](https://technet.microsoft.com/library/1352c534-7193-46ca-9ab1-0c5219a661ad).

Zoals Task Scheduler-taken, kunt u geplande taken uitvoeren volgens een schema eenmalig of terugkerende of in reactie op een actie of een gebeurtenis. U kunt bekijken en beheren van geplande taken in Task Scheduler, inschakelen en uitschakelen van deze indien nodig, ze uit te voeren of ze als sjablonen gebruiken en stel de voorwaarden waaronder de taken worden gestart.

Bovendien Geplande taken worden geleverd met een aangepaste set cmdlets voor het beheren van deze. De cmdlets kunt u maken, bewerken, beheren, uitschakelen, en geplande taken opnieuw in te schakelen, geplande taak triggers maken en opties voor de geplande taak instellen.

Zie voor meer informatie over geplande taken [about_Scheduled_Jobs](https://technet.microsoft.com/library/3b546629-703c-4939-b44f-52dd567bce92).

### <a name="windows-powershell-language-enhancements"></a>Verbeteringen in Windows PowerShell-taal
Windows PowerShell 3.0 bevat veel functies die zijn ontworpen voor het maken van de taal eenvoudiger en eenvoudiger te gebruiken en om veelvoorkomende fouten te voorkomen. De verbeteringen omvatten eigenschap opsomming, aantal en de lengte-eigenschappen op scalaire objecten, nieuwe omleiding operators, de bereikaanpassingsfunctie $Using, PSItem automatische variabelen, flexibele script opmaak, de kenmerken van de variabelen, vereenvoudigde kenmerk argumenten, numerieke opdrachtnamen, de operator Stop parseren, verbeterde matrix splatting, nieuwe bits-operators, geordende woordenboeken, PSCustomObject casten en verbeterde op basis van een opmerking Help-informatie.

### <a name="new-core-cmdlets"></a>Nieuwe Core-Cmdlets
Er zijn nieuwe cmdlets zijn toegevoegd aan de Windows PowerShell Core-installatie, inclusief cmdlets voor het beheren van geplande taken, niet-verbonden sessies, CIM-integratie en het bij te werken Help-systeem.

|||
|-|-|
|Toevoegen-JobTrigger|Nieuwe-JobTrigger|
|Connect-PSSession|Nieuwe PSSessionConfigurationFile|
|ConvertFrom-Json|New-PSTransportOption|
|ConvertTo Json|Nieuwe PSWorkflowExecutionOption|
|Disable-JobTrigger|New-PSWorkflowSession|
|Disable-ScheduledJob|Nieuwe ScheduledJobOption|
|Verbinding verbreken-PSSession|Nieuwe-WinEvent|
|Enable-JobTrigger|Ontvangen-PSSession|
|Enable-ScheduledJob|Register-CimIndicationEvent|
|Get-CimAssociatedInstance|Register-ScheduledJob|
|Get-CimClass|Remove-CimInstance|
|Get-CimInstance|Remove-CimSession|
|Get-CimSession|Remove-TypeData|
|Get-ControlPanelItem|Rename-Computer|
|Get-IseSnippet|Resume-Job|
|Get-JobTrigger|Help opslaan|
|Get-ScheduledJob|Set-CimInstance|
|Get-ScheduledJobOption|Set-JobTrigger|
|Get-TypeData|Set-ScheduledJob|
|Import-IseSnippet|Set-ScheduledJobOption|
|Aanroepen AsWorkflow|Opdracht weergeven|
|Invoke-CimMethod|Show-ControlPanelItem|
|Aanroepen RestMethod|Suspend-Job|
|Invoke-WebRequest|Test-PSSessionConfigurationFile|
|Nieuwe-CimInstance|De blokkering opheffen-bestand|
|Nieuwe-CimSession|Unregister-ScheduledJob|
|Nieuwe CimSessionOption|Help bijwerken|
|Nieuwe IseSnippet||

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>Verbeteringen voor bestaande essentiële Cmdlets en Providers
Windows PowerShell 3.0 bevat nieuwe functies voor bestaande cmdlets, met inbegrip van de syntaxis van de vereenvoudigde en nieuwe parameters voor de volgende cmdlets: Computer-cmdlets, CSV-cmdlets Get-ChildItem, Get-Command, Get-inhoud, Get-geschiedenis Meetobject-beveiliging cmdlets, Select-Object, selecteer-tekenreeks, Split-Path, Start-proces, t-Object, Test-Connection, lid zijn van het toevoegen en WMI-cmdlets.

De Windows PowerShell-providers zijn ook aanzienlijk verbeterd, waaronder Certificate Providerondersteuning voor het beheren van Secure Socket Layer (SSL)-certificaten voor het hosten van web, ondersteuning voor de referentie, permanente netwerkstations en alternatieve gegevensstreams in door het bestandssysteem.

### <a name="remote-module-import-and-discovery"></a>Externe module-import en detectie
Windows PowerShell 3.0 is een uitbreiding module detectie, importeren en mogelijkheden voor impliciete externe communicatie op externe computers. De Module-cmdlets modules ophalen op externe computers en importeer de modules in de lokale of externe computer met behulp van Windows PowerShell voor externe toegang. Ondersteuning van nieuwe CIM-sessie kunt u gebruikmaken van CIM- en WMI-niet-Windows-computers beheren door het importeren van opdrachten op de lokale computer die impliciet wordt uitgevoerd op de externe computer.

Voor meer informatie, Zie de help-onderwerpen voor de [Get-Module](https://technet.microsoft.com/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) en [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="enhanced-tab-completion"></a>Verbeterde Tab-aanvulling
Tab-Aanvulling in de Windows PowerShell-console nu is voltooid de namen van cmdlets, parameters, parameterwaarden, opsommingen, .NET Frameworks typen, COM-objecten, verborgen mappen, en meer. De functie voor tabblad voltooiing is volledig herschreven op basis van een nieuwe parser en de abstracte syntaxisstructuur voor de ondersteuning van meer scenario's, met inbegrip van parseren structuren in het geheugen en schouderstreek tab-Aanvulling.

### <a name="module-auto-loading"></a>Module automatisch geladen
De [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet nu krijgt u alle cmdlets en -functies van alle modules weer die zijn geïnstalleerd op de computer, zelfs als de module is niet geïmporteerd in de huidige sessie.

Wanneer u de cmdlet die u nodig hebt, kunt u dit onmiddellijk zonder het importeren van alle modules. Windows PowerShell-modules worden nu automatisch geïmporteerd wanneer u een cmdlet in de module. U moet niet meer te zoeken naar de module en voor het gebruik van de cmdlets te importeren.

Het importeren van modules automatisch wordt geactiveerd door met de cmdlet uitgevoerd in een opdracht **Get-Command** voor een cmdlet zonder jokertekens of met [Get-Help](https://technet.microsoft.com/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) voor een cmdlet zonder jokertekens.

U kunt inschakelen, uitschakelen en configureren van automatische importeren van modules met behulp van de **$PSModuleAutoLoadingPreference** voorkeursvariabele.

Zie voor meer informatie, [about_Modules](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_modules?view=powershell-5.0), [about_Preference_Variables [v4]](https://technet.microsoft.com/library/31344314-be29-4286-b039-afa5460cbe8b), en de help-onderwerpen voor de [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) en [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlets.

### <a name="module-experience-improvements"></a>Verbeteringen van de module-ervaring
Windows PowerShell 3.0 biedt ondersteuning voor geavanceerde functies voor modules, waaronder de volgende nieuwe functies.

1. Module-logboekregistratie voor afzonderlijke modules (LogPipelineExecutionDetails) en de nieuwe instelling voor Groepsbeleid 'Inschakelen op Module logboekregistratie'

2. Module-objecten die beschikbaar maken van de waarden van de module-manifest uitgebreid

3. Nieuwe **ExportedCommands** eigenschap van modules, waaronder geneste modules, waarin opdrachten van alle typen worden gecombineerd

4. Verbeterde detectie van beschikbare (niet geïmporteerd)-modules, met inbegrip van zodat de **pad** en **ListAvailable** parameters in dezelfde opdracht

5. Nieuwe **DefaultCommandPrefix** sleutel in de modulemanifesten die voorkomt naamconflicten zonder code van de module te wijzigen.

6. Module-vereisten, met inbegrip van de vereiste modules met versie en GUID en het automatisch importeren van de vereiste modules volledig gekwalificeerde verbeterd

7. Rustigere, gestroomlijnde bewerking van de [New-ModuleManifest](https://technet.microsoft.com/library/512adced-f42f-4e88-ba7c-834fc9e5d047) cmdlet.

8. Nieuwe **Module** parameter voor #Requires

9. Verbeterde [Import-Module](https://technet.microsoft.com/library/af616c24-e122-4098-930e-1e3ea2080ade) cmdlet met zowel **MinimumVersion** en **RequiredVersion** parameters.

### <a name="simplified-command-discovery"></a>Vereenvoudigde opdracht detectie
U moet niet meer voor het importeren van alle modules voor het detecteren van de opdrachten die beschikbaar zijn op uw sessie. In Windows PowerShell 3.0, de [Get-Command](https://technet.microsoft.com/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) cmdlet haalt alle opdrachten van alle geïnstalleerde modules. En als u een opdracht, de module die Hiermee exporteert u de opdracht automatisch geïmporteerd in uw sessie is.

De nieuwe [opdracht weergeven](https://technet.microsoft.com/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) cmdlet speciaal is ontworpen voor beginners. U kunt zoeken naar de opdrachten in een venster. U kunt alle opdrachten weergeven of filteren op de module, een module importeren door te klikken op een knop, tekstvakken en vervolgkeuzelijsten gebruiken om te maken van een geldige opdracht, en kopieer vervolgens of de opdracht uitvoeren zonder ze ooit buiten het venster.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>Verbeterde logboekregistratie van diagnostische gegevens en ondersteuning voor groepen van beleid
Windows PowerShell 3.0 verbetert de logboekregistratie en tracering van ondersteuning voor opdrachten en -modules met ondersteuning voor Event Tracing in Windows (ETW) zich aanmeldt, een bewerkbaar **LogPipelineExecutionDetails** eigenschap van modules, en de "inschakelen op Module Logboekregistratie' groep beleidsinstelling. U kunt nu parameterwaarden van logboekgegevens krijgen door de logboekeigenschappen van het weer te geven.

### <a name="formatting-and-output-improvements"></a>Opmaak- en uitvoer verbeteringen
Nieuwe opmaak- en uitvoer verbeteringen verbeteren de efficiëntie van alle gebruikers van Windows PowerShell. De verbeteringen omvatten uitvoer omleiden voor alle stromen, een verbeterde Update-Type-cmdlet die wordt toegevoegd typen dynamisch zonder Format.ps1xml bestanden, tekstterugloop in de uitvoer van de eigenschappen voor de opmaak van de aangepaste objecten, standaard de **PSCustomObject** type, verbeterde opmaak voor WMI-objecten en heterogene objecten en ondersteuning voor het detecteren van methode overloads.

### <a name="enhanced-console-host-experience"></a>Verbeterde Console Host-ervaring
De Windows PowerShell-console hostprogramma bevat nieuwe functies in Windows PowerShell 3.0, met inbegrip van één threaded apartment standaard. De nieuwe optie 'Uitvoeren met PowerShell' in Verkenner kunt u scripts uitvoeren in een onbeperkte sessie met de rechtermuisknop op. Nieuwe console host starten logische Start Windows PowerShell sneller en nieuwe lettertypen kunnen u de vertrouwde console-venster ervaring aanpassen.

Zie voor meer informatie, [about_Run_With_PowerShell](https://technet.microsoft.com/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb).

### <a name="new-cmdlet-and-hosting-apis"></a>Nieuwe Cmdlet en het hosten van API 's
De nieuwe Cmdlet-API en host API bevatten openbare geavanceerde syntaxisstructuur (AST) API's en API's voor het wisselbestand van de pijplijn, geneste pijplijnen runspace pools tab-aanvulling, Windows RT, de verouderde cmdlet-kenmerk en werkwoord en een zelfstandig naamwoord eigenschappen van het object FunctionInfo.

### <a name="performance-improvements"></a>Verbeterde prestaties
Aanzienlijke prestatieverbeteringen in Windows PowerShell afkomstig zijn van de nieuwe taal-parser die is gebouwd op dynamische Runtime taal (DLR) in .NET Framework 4., samen met de runtime-script compilatie, verbeteringen van de engine betrouwbaarheid en wijzigingen in de algoritme van de [Get-ChildItem](https://technet.microsoft.com/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) verbeteren de prestaties, met name bij het netwerk te zoeken naar deelt.

### <a name="runas-and-shared-host-support"></a>Uitvoeren als- en ondersteuning voor gedeelde hostgroep
Windows PowerShell 3.0 biedt ondersteuning voor RunAs- en Host gedeelde functies.

De *RunAs* functie, die is ontworpen voor Windows PowerShell Workflow, kan gebruikers van een sessieconfiguratie-sessies die worden uitgevoerd met de machtiging van een gedeelde gebruikersaccount maken. Dit kan minder bevoegde gebruikers bepaalde opdrachten en scripts uitvoeren met beheerdersrechten en vermindert de noodzaak voor het minder senior gebruikers toevoegen aan de groep Administrators.

De **SharedHost** functie kan meerdere gebruikers op meerdere computers verbinding maken met een Werkstroomsessie gelijktijdig en de voortgang van een werkstroom. Gebruikers kunnen geen werkstroom starten op één computer en klikt u vervolgens verbinding maken met de Werkstroomsessie op een andere computer zonder de sessie verbreken met de oorspronkelijke computer. Gebruikers moeten dezelfde machtigingen hebben en gebruikmaken van dezelfde sessieconfiguratie. Zie voor meer informatie 'Uitvoeren van een Windows PowerShell Workflow' in het aan de slag met Windows PowerShell-werkstroom.

### <a name="special-character-handling-improvements"></a>Verwerking van verbeteringen in speciaal teken
Voor het verbeteren van de mogelijkheden van Windows PowerShell 3.0 het interpreteren en correct verwerkt speciale tekens, de **LiteralPath** speciale tekens in paden verwerkt, parameter is geldig voor bijna alle cmdlets die u hebt een  **Pad** parameter, met inbegrip van de nieuwe [Update-Help](https://technet.microsoft.com/library/93e1d870-ace6-432b-8778-8920291d7545) en [Help opslaan](https://technet.microsoft.com/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) cmdlets. De parser bevat ook speciale logica voor het verbeteren van de verwerking van het teken backtick (\`) en tussen vierkante haken in namen en paden.

## <a name="see-also"></a>Zie ook
- [about_Windows_PowerShell_5.0](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)