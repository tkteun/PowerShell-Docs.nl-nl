---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Rolmogelijkheden JEA
ms.openlocfilehash: bd0a995adc60e50049ff99d6b23e7c2aeb745a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685492"
---
# <a name="jea-role-capabilities"></a>Rolmogelijkheden JEA

> Van toepassing op: Windows PowerShell 5.0

Bij het maken van een JEA-eindpunt, moet u definiëren een of meer "rolmogelijkheden" die worden beschreven *wat* iemand in een JEA-sessie kunt doen.
De mogelijkheid van een rol is een PowerShell-gegevensbestand met de extensie .psrc met een lijst met alle cmdlets, functies, -providers en externe programma's die beschikbaar zijn voor het koppelen van gebruikers moeten worden gemaakt.

In dit onderwerp wordt beschreven hoe u een PowerShell-rol mogelijkheid-bestand voor uw gebruikers JEA maken.

## <a name="determine-which-commands-to-allow"></a>Bepalen welke opdrachten om toe te staan

De eerste stap bij het maken van een bestand van rol mogelijkheid is om te overwegen wat de gebruikers die de rol is toegewezen toegang nodig tot.
Even kunnen duren voordat dit proces voor het verzamelen vereisten, maar het is een belangrijk proces.
Gebruikers toegang geven tot te weinig cmdlets en -functies kunt voorkomen dat ze aan hun werk gedaan te krijgen.
Toegang tot te veel cmdlets en -functies kan leiden tot meer dan u bedoeld met hun impliciete beheerdersbevoegdheden verzwakken van uw beveiliging virtualisatieproducten doen gebruikers.

Hoe u gaat over dit proces is afhankelijk van uw organisatie en doelstellingen, maar de volgende tips kunnen helpen Zorg ervoor dat u op de juiste weg bent.

1. **Identificeer** de gebruikers opdrachten wordt gebruikt om hun werk te doen. Hierbij kan het controleren van IT-personeel, automatiseringsscripts controleren of Transcripten van PowerShell-sessie of de logboeken analyseren.
2. **Update** gebruik van opdrachtregelprogramma's voor PowerShell-equivalent, waar mogelijk, voor de beste controle- en JEA aanpassing ervaring. Externe programma's kunnen niet worden beperkt als granulair als systeemeigen PowerShell-cmdlets en functies in JEA.
3. **Beperken** het bereik van de cmdlets als nodig is om alleen bepaalde parameters of parameterwaarden toestaan. Dit is vooral belangrijk als gebruikers moeten alleen deel uitmaken van een systeem te beheren.
4. **Maak** aangepaste functies om complexe opdrachten of opdrachten die moeilijk te beperken in JEA te vervangen. Een eenvoudige functie die loopt van een complexe opdracht of toepassing van extra validatielogica kan bieden extra controle voor het gemak van beheerders en eindgebruikers.
5. **Test** binnen het bereik de lijst met toegestane opdrachten door uw gebruikers en/of de automation-services en pas deze zo nodig.

Het is belangrijk te onthouden dat opdrachten in een JEA-sessie vaak uitgevoerd met de beheerder (of anderszins opdrachtprompt met verhoogde bevoegdheid) bevoegdheden zijn.
Zorgvuldige selectie van de beschikbare opdrachten is het belangrijk om te controleren of de JEA-eindpunt staat niet toe dat de gebruiker die de verbinding voor het verhogen van hun machtigingen.
Hieronder volgen enkele voorbeelden van opdrachten die kunnen worden gebruikt opzettelijk als toegestaan in een onbeperkte status.
Houd er rekening mee dat dit geen uitputtende lijst is en mag alleen worden gebruikt als een ook beginpunt.

### <a name="examples-of-potentially-dangerous-commands"></a>Voorbeelden van mogelijk schadelijke opdrachten

Risico 's | Voorbeeld | Gerelateerde opdrachten
-----|---------|-----------------
Verlenen van de gebruiker die verbinding maakt beheerdersbevoegdheden voor het overslaan van JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Uitvoeren van willekeurige code, zoals malware, aanvallen of aangepaste scripts te omzeilen: beveiliging | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Maak een bestand van de mogelijkheid rol

Kunt u een nieuw bestand rol mogelijkheid PowerShell met de [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Het resulterende bestand van de rol-mogelijkheid kan worden geopend in een teksteditor en gewijzigd, zodat de gewenste opdrachten voor de rol.
De PowerShell-help-documentatie bevat enkele voorbeelden van hoe u het bestand kunt configureren.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell-cmdlets en-functies

Voor het autoriseren van gebruikers om uit te voeren PowerShell-cmdlets of functies toevoegen de naam van de cmdlet of functie in de velden VisbibleCmdlets of VisibleFunctions.
Als u niet zeker weet of een opdracht is een cmdlet of functie, kunt u uitvoeren `Get-Command <name>` en de eigenschap 'CommandType' in de uitvoer controleren.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Soms is het bereik van een specifieke cmdlet of de functie is te breed voor de behoeften van uw gebruikers.
Een DNS-beheerder, bijvoorbeeld waarschijnlijk enige behoeften toegang om de DNS-service opnieuw te starten.
In een omgeving met meerdere tenants waarbij tenants toegang tot Self-servicebeheer-hulpprogramma's worden verleend, moet tenants beheren met hun eigen resources.
Voor deze gevallen kunt u beperken welke parameters beschikbaar worden gesteld van de cmdlet of functie.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

In de meer geavanceerde scenario's moet u mogelijk ook beperken welke waarden iemand kan leveren aan deze parameters.
Rolmogelijkheden kunnen u bij het definiëren van een set toegestane waarden of een reguliere-expressiepatroon die wordt geëvalueerd om te bepalen of een opgegeven invoer is toegestaan.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> De [algemene PowerShell-parameters](https://technet.microsoft.com/library/hh847884.aspx) zijn altijd toegestaan, zelfs als u de beschikbare parameters beperken.
> U dient niet expliciet vermeld in het veld Parameters.

De volgende tabel beschrijft de verschillende manieren waarop u kunt een zichtbaar cmdlet of functie.
U kunt combineren en matchen een van de hieronder in de VisibleCmdlets veld.

Voorbeeld                                                                                      | Use-case
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` of `@{ Name = 'My-Func' }`                                                       | Kan de gebruiker om uit te voeren `My-Func` zonder beperkingen voor de parameters.
`'MyModule\My-Func'`                                                                         | Kan de gebruiker om uit te voeren `My-Func` uit de module `MyModule` zonder beperkingen voor de parameters.
`'My-*'`                                                                                     | Kan de gebruiker een cmdlet of de functie uitvoeren met de term `My`.
`'*-Func'`                                                                                   | Hiermee kan de gebruiker een cmdlet of de functie uitvoeren met het zelfstandig naamwoord `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` en/of `Param2` parameters. Elke waarde kan worden opgegeven met de parameters.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter. Alleen "Value1" en 'Value2' kan worden opgegeven voor de parameter.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter. Een willekeurige waarde beginnen met 'contoso' kan worden opgegeven voor de parameter.


> [!WARNING]
> Het verdient voor aanbevolen procedures voor beveiliging, geen jokertekens gebruiken bij het definiëren van zichtbaar cmdlets of functies.
> In plaats daarvan moet u elke vertrouwde opdracht om te controleren of er worden geen andere opdrachten die de dezelfde naamgevingsschema delen per ongeluk zijn gemachtigd expliciet vermelden.

U kunt een ValidatePattern en ValidateSet toepassen op de dezelfde cmdlet of functie.

Als u dit doet, is de ValidatePattern overschrijft de ValidateSet.

Bekijk voor meer informatie over ValidatePattern [dit *Hallo, Scripting Guy!* boeken](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) en de [PowerShell reguliere expressies](https://technet.microsoft.com/library/hh847880.aspx) -referentie-inhoud.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Externe opdrachten en PowerShell-scripts toestaan

Als u wilt toestaan dat gebruikers uitvoerbare bestanden en PowerShell-scripts (.ps1) uitvoeren in een JEA-sessie, moet u het volledige pad toevoegen aan elk programma in het veld VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Het wordt aanbevolen, waar mogelijk gebruik van PowerShell-cmdlet/functie equivalenten van elke externe uitvoerbare bestanden verleent u onbevoegde gebruikers nadat u hebt de controle over welke parameters met PowerShell-cmdlets/functies zijn toegestaan.

Veel uitvoerbare bestanden kunt u zowel de huidige status lezen en wijzig deze alleen door op te geven van de verschillende parameters.

Neem bijvoorbeeld de rol van een bestand van een serverbeheerder bent om te controleren welke netwerkshares worden gehost door de lokale computer.
Een manier om te controleren, is met `net share`.
Echter, zodat net.exe is zeer gevaarlijke omdat de beheerder kan net zo eenvoudig gebruik van de opdracht om te krijgen van beheerdersbevoegdheden met `net group Administrators unprivilegedjeauser /add`.
Er is een betere benadering om toe te staan [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) die geven hetzelfde resultaat, maar een nog veel meer beperkt bereik heeft.

Wanneer externe opdrachten beschikbaar maken voor gebruikers in een JEA-sessie, is altijd opgeven van het volledige pad naar het uitvoerbare bestand om te controleren of een gelijknamige (en mogelijk malicous) programma elders geplaatst op het systeem niet in plaats daarvan wordt uitgevoerd.

### <a name="allowing-access-to-powershell-providers"></a>Toegang tot de PowerShell-providers

Er zijn geen PowerShell-providers zijn standaard beschikbaar in JEA-sessies.

Dit is vooral vermindert het risico van gevoelige informatie en configuratie-instellingen die worden doorgegeven aan de gebruiker die verbinding maakt.

Indien nodig, kunt u de toegang tot de PowerShell-providers met behulp van de `VisibleProviders` opdracht.
Voor een volledige lijst met providers, voert u `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Voor eenvoudige taken waarvoor toegang tot het bestandssysteem, register, certificaatarchief of andere gevoelige-providers, kunt u ook overwegen schrijven van een aangepaste functie die geschikt is voor de provider namens de gebruiker.
Functies, -cmdlets en externe programma's die beschikbaar in een JEA-sessie zijn vallen niet onder de dezelfde beperkingen als JEA--ze hebben standaard toegang tot alle elke provider.
Ook kunt u overwegen de [schijf van de gebruiker](session-configurations.md#user-drive) wanneer bestanden zijn gekopieerd naar/van een JEA-eindpunt is vereist.

### <a name="creating-custom-functions"></a>Het maken van aangepaste functies

U kunt aangepaste functies in een bestand rol mogelijkheid complexe taken vereenvoudigen voor uw eindgebruikers maken.
Aangepaste functies zijn ook handig wanneer u geavanceerde validatielogica voor cmdlet parameterwaarden vereist.
U kunt eenvoudig functies schrijven in de **FunctionDefinitions** veld:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Vergeet niet om toe te voegen van de naam van uw aangepaste functies voor de **VisibleFunctions** veld, zodat ze kunnen worden uitgevoerd door de JEA-gebruikers.


De hoofdtekst (scriptblok) van aangepaste functies in de standaardmodus voor de taal voor het systeem wordt uitgevoerd en niet is onderworpen aan beperkingen voor de JEA-taal.
Dit betekent dat functies kunnen toegang krijgen het bestandssysteem en register tot en uitvoeren van opdrachten die zijn niet zichtbaar in het bestand van de mogelijkheid rol.
Let erop om te voorkomen waardoor arbitraire code moet worden uitgevoerd wanneer met behulp van parameters en te voorkomen dat invoer van de gebruiker rechtstreeks in de cmdlets, zoals uitvoeromleiding `Invoke-Expression`.

In het bovenstaande voorbeeld ziet u dat de naam van de volledig gekwalificeerde module (FQMN) `Microsoft.PowerShell.Utility\Select-Object` is gebruikt in plaats van de steno `Select-Object`.
Functies die zijn gedefinieerd in de rol mogelijkheid bestanden zijn nog steeds afhankelijk van het bereik van JEA-sessies, waaronder de proxyfuncties JEA wordt gemaakt voor het beperken van bestaande opdrachten.

Select-Object is een standaard beperkte cmdlet in alle JEA-sessies die is niet toegestaan om willekeurige eigenschappen van objecten te selecteren.
Voor het gebruik van de onbeperkte Select-Object in de functies, moet u expliciet de volledige implementatie aanvragen door de FQMN op te geven.
Een beperkte cmdlet in een JEA-sessie wordt vertonen hetzelfde gedrag wordt aangeroepen vanuit een functie, in overeenstemming met de PowerShell [opdracht prioriteit](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Als u een groot aantal aangepaste functies ontwikkelt, kan het zijn gemakkelijker te plaatsen een [PowerShell-Script-Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).
U kunt deze functies vervolgens zichtbaar in de JEA-sessie met behulp van het veld VisibleFunctions zoals u zou met ingebouwde en van derden modules doen maken.

## <a name="place-role-capabilities-in-a-module"></a>Rolmogelijkheden plaatsen in een module

In de volgorde voor PowerShell om een rol mogelijkheid-bestand te zoeken, moet deze worden opgeslagen in een map 'RoleCapabilities' in een PowerShell-module.
De module kan worden opgeslagen in een map die is opgenomen in de `$env:PSModulePath` omgevingsvariabele, maar u moet niet plaats deze in System32 (gereserveerd voor ingebouwde modules) of een map waar de niet-vertrouwde, verbinding te maken van gebruikers kan de bestanden wijzigen.
Hieronder volgt een voorbeeld van het maken van een eenvoudige PowerShell-script-module met de naam *ContosoJEA* in het pad 'Program Files'.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Zie [inzicht krijgen in een PowerShell-Module](https://msdn.microsoft.com/library/dd878324.aspx) voor meer informatie over PowerShell-modules, modulemanifesten en de omgevingsvariabele PSModulePath.

## <a name="updating-role-capabilities"></a>Rolmogelijkheden bijwerken


U kunt een bestand van de mogelijkheid rol op elk gewenst moment bijwerken door gewoon wijzigingen aan de rol mogelijkheid bestand worden opgeslagen.
Een nieuwe JEA-sessies gestart nadat de mogelijkheid van de rol is bijgewerkt, verschijnt op de nieuwe mogelijkheden.

Dit is de reden waarom het beheren van toegang tot de map van de mogelijkheden van rol is dus belangrijk.
Alleen uiterst vertrouwde beheerders mogen rol mogelijkheid bestanden te wijzigen.
Als een niet-vertrouwde gebruiker rol mogelijkheid bestanden wijzigt kan, kunnen ze eenvoudig geven zelf toegang aan de cmdlets waarmee ze zijn bevoegdheden te verhogen.


Voor beheerders het vergrendelen van toegang tot de rolmogelijkheden wilt, zorg ervoor dat lokaal systeem, leestoegang heeft tot de rol mogelijkheid bestanden en met modules.

## <a name="how-role-capabilities-are-merged"></a>Hoe rolmogelijkheden worden samengevoegd

Gebruikers kunnen toegang tot meerdere rolmogelijkheden worden verleend wanneer ze een JEA-sessie, afhankelijk van de rol-toewijzingen in de [sessie configuratiebestand](session-configurations.md).
Als dit gebeurt, JEA probeert te geven van de gebruiker de *meest strikte* reeks opdrachten die zijn toegestaan door een van de rollen.

**VisibleCmdlets en VisibleFunctions**

De meest complexe logica voor het samenvoegen van invloed is op de cmdlets en -functies, waarvoor hun parameters en parameterwaarden in JEA beperkt.

De regels zijn als volgt:

1. Als een cmdlet is alleen zichtbaar zijn in één rol, worden deze zichtbaar is voor de gebruiker met de beperkingen van toepassing parameter.
2. Als een cmdlet is zichtbaar in meer dan één rol, en elke rol de dezelfde beperkingen met betrekking tot de cmdlet heeft, zijn de cmdlet zichtbaar voor de gebruiker met deze beperkingen.
3. Als een cmdlet is zichtbaar in meer dan één rol, en elke rol maakt het mogelijk een andere set parameters, zijn de cmdlet en alle parameters gedefinieerd voor elke rol zichtbaar voor de gebruiker. Als één rol geen beperkingen met betrekking tot de parameters heeft, wordt alle parameters worden toegestaan.
4. Als één rol een set valideren of patroon valideren voor een cmdlet-parameter definieert en de andere rol kunt u de parameter, maar legt geen beperkingen voor de parameterwaarden, wordt de set valideren of het patroon worden genegeerd.
5. Als een set valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, worden alle waarden uit alle valideren sets is toegestaan.
6. Als een patroon valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, worden alle waarden die overeenkomen met een van de patronen worden toegestaan.
7. Als een set valideren is gedefinieerd in een of meer rollen, en een patroon valideren is gedefinieerd in een andere rol voor de dezelfde cmdlet-parameter, de set valideren wordt genegeerd en regel (6) is van toepassing op de resterende valideren patronen.

Hieronder volgt een voorbeeld van hoe de functies worden samengevoegd op basis van deze regels:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Alle andere velden in het bestand van de mogelijkheid rol worden alleen toegevoegd aan een volledige reeks van toegestane externe opdrachten, aliassen, providers en opstartscripts.
Elke opdracht, alias, provider of script beschikbaar is in één rol-functie is beschikbaar voor de JEA-gebruiker.

Wees voorzichtig om ervoor te zorgen dat de gecombineerde set-providers van een rol mogelijkheden en functies-cmdlets/opdrachten van een andere gebruikers niet toestaan verbindende onbedoelde toegang tot systeemresources.
Bijvoorbeeld, als een functie kan de `Remove-Item` cmdlet en andere kunnen de `FileSystem` provider, zijn op een JEA-gebruiker willekeurige bestanden op uw computer verwijderd.
Als u meer informatie over het identificeren van de effectieve machtigingen van gebruikers te vinden in de [JEA onderwerp controle](audit-and-report.md).

## <a name="next-steps"></a>Volgende stappen

- [Een sessie-configuratiebestand maken](session-configurations.md)