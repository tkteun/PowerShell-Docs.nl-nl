---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: JEA rol mogelijkheden
ms.openlocfilehash: 10f5f390daccbb012be6ee7272041e777810ee12
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="jea-role-capabilities"></a>JEA rol mogelijkheden

> Van toepassing op: Windows PowerShell 5.0

Wanneer u een eindpunt JEA maakt, moet u een of meer 'rol mogelijkheden' die wordt beschreven definiëren *wat* iemand in een sessie JEA kunt doen.
De mogelijkheid van een rol is een PowerShell-gegevensbestand met de extensie .psrc met een lijst met alle cmdlets, functies, -providers en externe programma's die beschikbaar zijn voor het verbinden van gebruikers moeten worden gedaan.

In dit onderwerp wordt beschreven hoe een PowerShell-rol mogelijkheid-bestand voor uw gebruikers JEA te maken.

## <a name="determine-which-commands-to-allow"></a>Bepalen welke opdrachten om toe te staan

De eerste stap bij het maken van een rol mogelijkheid-bestand is te overwegen wat de gebruikers die zijn toegewezen aan de rol toegang nodig tot.
Deze vereisten verzamelingsproces kunnen even duren, maar het is een belangrijk proces.
Gebruikers toegang geven tot te weinig cmdlets en -functies kunt voorkomen dat ze toegang krijgen tot hun werk kan verrichten.
Toestaan van toegang tot te veel cmdlets en functies kan leiden tot gebruikers die meer dan u hebt aangebracht met hun impliciete beheerdersbevoegdheden verzwakken uw beveiliging houding ten doen.

Hoe u over dit proces gaat afhankelijk van uw organisatie en de doelstellingen, maar de volgende tips kunt Zorg ervoor dat u op de juiste weg bent.

1. **Identificeren** de opdrachten-gebruikers voor hun werk gebruiken. Hierbij kan het controleren van de IT-personeel, automatiseringsscripts controleren of het analyseren van PowerShell-sessie transcripties of Logboeken.
2. **Update** gebruik van de opdrachtregelprogramma's voor PowerShell-equivalenten, waar mogelijk, voor de beste controle en JEA aanpassing ervaring. Externe programma's kunnen niet als granulair als systeemeigen PowerShell-cmdlets en functies in JEA worden beperkt.
3. **Beperken** het bereik van de cmdlets nodig alleen kan bepaalde parameters of parameterwaarden. Dit is vooral belangrijk als gebruikers moeten alleen deel uitmaken van een systeem beheren.
4. **Maak** aangepaste functies om complexe opdrachten of opdrachten die moeilijk te beperken in JEA te vervangen. Een eenvoudige functie die een complexe opdracht terugloopt of, past logica voor aanvullende verificatie te kan bieden extra controles voor beheerders en eindgebruikers eenvoud.
5. **Test** de gedefinieerde lijst met toegestane opdrachten met uw gebruikers en/of de automation-services en pas deze zo nodig.

Het is belangrijk om te onthouden opdrachten in een sessie JEA zijn vaak bevoegdheden uitvoeren met admin (of anderszins met verhoogde bevoegdheden).
Zorgvuldige selectie van de beschikbare opdrachten is het belangrijk om te controleren of het eindpunt JEA staat niet toe dat de gebruiker verbinding maakt zichzelf machtigingen toekennen.
Hieronder volgen enkele voorbeelden van opdrachten die kunnen worden gebruikt met kwaadaardige bedoelingen als toegestaan in een onbeperkte status.
Houd er rekening mee dat dit geen uitputtende lijst is en mag alleen worden gebruikt als een beginpunt uit.

### <a name="examples-of-potentially-dangerous-commands"></a>Voorbeelden van potentieel gevaarlijke opdrachten

Risico 's | Voorbeeld | Gerelateerde opdrachten
-----|---------|-----------------
De gebruiker verbinding maakt verlenen beheerdersbevoegdheden om over te slaan JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Uitvoeren van willekeurige code, zoals malware, misbruik of aangepaste scripts voor het overslaan van beveiliging | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Maak een bestand van de mogelijkheid rol

Kunt u een nieuw bestand rol mogelijkheid PowerShell met de [nieuw PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Het resulterende rol mogelijkheid bestand kan worden geopend in een teksteditor en gewijzigd zodat de gewenste opdrachten voor de rol.
De PowerShell-help-documentatie bevat enkele voorbeelden van hoe u het bestand kunt configureren.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell-cmdlets en-functies

Voor het autoriseren van gebruikers om uit te voeren PowerShell-cmdlets of functies toevoegen de naam van de cmdlet of functie aan de VisbibleCmdlets of VisibleFunctions velden.
U kunt uitvoeren als u niet zeker weet of een opdracht is een cmdlet of functie `Get-Command <name>` en controleer de eigenschap 'CommandType' in de uitvoer.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Soms is het bereik van een bepaalde cmdlet of functie is te breed voor de behoeften van uw gebruikers.
Een DNS-beheerder is bijvoorbeeld waarschijnlijk alleen behoeften toegang tot om de DNS-service opnieuw te starten.
In een omgeving met meerdere tenants waarbij tenants toegang verleend tot selfservice beheerhulpprogramma's moet tenants beheren met hun eigen resources.
Voor dergelijke gevallen kunt u beperken welke parameters beschikbaar worden gesteld van de cmdlet of functie.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

In meer geavanceerde scenario's moet u mogelijk ook beperken welke waarden iemand kan leveren aan deze parameters.
Mogelijkheden van de rol kunnen u bij het definiëren van een set toegestane waarden of een reguliere-expressiepatroon die wordt geëvalueerd om te bepalen of een opgegeven invoer is toegestaan.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> De [algemene PowerShell-parameters](https://technet.microsoft.com/en-us/library/hh847884.aspx) zijn altijd toegestaan, zelfs als u de beschikbare parameters beperken.
> U moet niet expliciet vermeld ze in het veld Parameters.

De volgende tabel beschrijft de verschillende manieren kunt u een cmdlet zichtbaar of functie aanpassen.
U kunt combineren en overeen met een van de hieronder in de VisibleCmdlets veld.

Voorbeeld                                                                                      | Gebruiksvoorbeeld
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` of `@{ Name = 'My-Func' }`                                                       | Kan de gebruiker om uit te voeren `My-Func` zonder beperkingen van de parameters.
`'MyModule\My-Func'`                                                                         | Kan de gebruiker om uit te voeren `My-Func` van de module `MyModule` zonder beperkingen van de parameters.
`'My-*'`                                                                                     | Kan de gebruiker een cmdlet of functie uitvoeren met de term `My`.
`'*-Func'`                                                                                   | Kan de gebruiker een cmdlet of functie uitvoeren met het zelfstandig naamwoord `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` en/of `Param2` parameters. Elke waarde kan worden opgegeven voor de parameters.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter. Aan de parameter kan alleen 'Waarde1' en 'Waarde2' worden opgegeven.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter. Een waarde die beginnen met 'contoso' kan worden opgegeven voor de parameter.


> [!WARNING]
> Voor de aanbevolen beveiligingsprocedures, is het niet raadzaam jokertekens te gebruiken bij het definiëren van zichtbaar cmdlets of functies.
> In plaats daarvan moet u elke vertrouwde opdracht om te controleren of er geen andere opdrachten die de dezelfde schematische delen per ongeluk zijn gemachtigd expliciet vermelden.

U kunt een ValidatePattern en de ValidateSet niet toepassen op de dezelfde cmdlet of functie.

Als u dit doet, wordt de ValidatePattern de ValidateSet overschreven.

Bekijk voor meer informatie over ValidatePattern [dit *artikel van Hey, Scripting Guy!* boeken](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) en de [PowerShell reguliere expressies](https://technet.microsoft.com/en-us/library/hh847880.aspx) verwijst naar inhoud.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Externe opdrachten en PowerShell-scripts toestaan

U moet het volledige pad toevoegen aan elk programma in het veld VisibleExternalCommands zodat gebruikers uitvoerbare bestanden en PowerShell-scripts (.ps1) in een sessie JEA uitvoeren.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Het wordt aanbevolen, waar mogelijk, PowerShell-cmdlet/functie equivalenten van elke externe uitvoerbare bestanden die geeft u toestemming omdat hebt u controle gedurende welke parameters zijn toegestaan met PowerShell-cmdlets/functies gebruiken.

Veel uitvoerbare bestanden kunt u zowel lezen van de huidige status en wijzig deze alleen door te geven van verschillende parameters.

Neem bijvoorbeeld de rol van een bestand serverbeheerder die wil controleren welke netwerkshares worden gehost door de lokale computer.
Een manier om te controleren om te gebruiken, is `net share`.
Echter, zodat net.exe is zeer gevaarlijke omdat de beheerder kan net zo eenvoudig gebruik van de opdracht om te krijgen van beheerdersbevoegdheden met `net group Administrators unprivilegedjeauser /add`.
Er is een betere benadering om toe te staan [Get-SmbShare](https://technet.microsoft.com/en-us/library/jj635704.aspx) die hetzelfde resultaat bereikt, maar heeft een veel meer beperkt bereik.

Wanneer externe opdrachten beschikbaar maken voor gebruikers in een sessie JEA, geef altijd het volledige pad naar het uitvoerbare bestand om te controleren of een gelijknamige (en mogelijk malicous) programma elders geplaatst op het systeem niet in plaats daarvan wordt uitgevoerd.

### <a name="allowing-access-to-powershell-providers"></a>Toegang tot aanbieders van PowerShell toe te staan

Standaard zijn er geen PowerShell-providers zijn beschikbaar in JEA sessies.

Hiermee wordt voornamelijk vermindert het risico van vertrouwelijke gegevens en configuratie-instellingen wordt doorgegeven aan de gebruiker verbinding maakt.

Indien nodig, kunt u toegang tot de PowerShell-providers met behulp van de `VisibleProviders` opdracht.
Voer voor een volledige lijst met providers `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Voor eenvoudige taken die toegang tot het bestandssysteem, register, certificaatarchief of andere gevoelige providers vereisen, kunt u ook overwegen schrijven geen aangepaste functie die geschikt is voor de provider namens de gebruiker.
Functies, -cmdlets en externe programma's die beschikbaar in een sessie JEA zijn vallen niet onder de dezelfde beperkingen als JEA--ze hebben standaard toegang tot elke provider.
Ook kunt u overwegen de [schijf van de gebruiker](session-configurations.md#user-drive) wanneer bestanden zijn gekopieerd naar/van een eindpunt JEA is vereist.

### <a name="creating-custom-functions"></a>Maken van aangepaste functies

U kunt aangepaste functies in een bestand van de rol mogelijkheid voor het vereenvoudigen van complexe taken voor uw eindgebruikers schrijven.
Aangepaste functies zijn ook handig wanneer u geavanceerde validatielogica voor cmdlet parameterwaarden vereist.
U kunt eenvoudige functies schrijven in de **FunctionDefinitions** veld:

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
> Vergeet niet om toe te voegen van de naam van uw aangepaste functies voor de **VisibleFunctions** zodat ze kunnen worden uitgevoerd door de gebruikers JEA veld.


De hoofdtekst (scriptblok) van aangepaste functies in de standaardmodus voor de taal voor het systeem wordt uitgevoerd en is niet van JEA taal beperkingen.
Dit betekent dat functies kunnen krijgen het bestandssysteem en register tot en opdrachten die niet zichtbaar in het bestand van de mogelijkheid rol gemaakt zijn.
Behandelen wilt willekeurige code worden uitgevoerd wanneer u parameters toe en te voorkomen dat de gebruikersinvoer piping rechtstreeks in cmdlets, zoals `Invoke-Expression`.

In het bovenstaande voorbeeld ziet u dat de naam van de volledig gekwalificeerde module (FQMN) `Microsoft.PowerShell.Utility\Select-Object` is gebruikt in plaats van het steno `Select-Object`.
Functies die zijn gedefinieerd in de rol capability-bestanden zijn nog steeds onderworpen aan het bereik van JEA sessies, waaronder de proxyfuncties JEA wordt gemaakt voor het beperken van bestaande opdrachten.

Select-Object is een standaard beperkte cmdlet in alle JEA sessies die niet is toegestaan als u willekeurige eigenschappen van objecten te selecteren.
Als u de onbeperkte Select-Object in de functies, moet u expliciet de volledige implementatie aanvragen door op te geven van de FQMN.
Een beperkte cmdlet in een sessie JEA zou vertonen hetzelfde gedrag bij het aanroepen van een functie, in overeenstemming met de PowerShell [opdracht voorrang](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).

Als u een groot aantal aangepaste functies schrijft, kan het zijn gemakkelijker te plaatsen een [PowerShell-Script Module](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
Vervolgens kunt u aanbrengen die functies zichtbaar in de JEA-sessie met behulp van het veld VisibleFunctions zoals u zou met ingebouwde en derden modules doen.

## <a name="place-role-capabilities-in-a-module"></a>Rol mogelijkheden plaatsen in een module

In de volgorde voor PowerShell zoeken naar een bestand van de mogelijkheid rol, moet deze worden opgeslagen in een map 'RoleCapabilities' in een PowerShell-module.
De module kan worden opgeslagen in een map die is opgenomen in de `$env:PSModulePath` omgevingsvariabele, maar u moet niet plaats deze in System32 (gereserveerd voor ingebouwde modules) of een map waarin het niet wordt vertrouwd, verbinden van gebruikers kan de bestanden wijzigen.
Hieronder volgt een voorbeeld van het maken van een PowerShell-script basismodule aangeroepen *ContosoJEA* in het pad 'Program Files'.

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

Zie [inzicht in een PowerShell-Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) voor meer informatie over PowerShell-modules, modulemanifesten en de omgevingsvariabele PSModulePath.

## <a name="updating-role-capabilities"></a>Bijwerken van de mogelijkheden van de rol


U kunt een rol mogelijkheid-bestand op elk gewenst moment bijwerken door gewoon opslaan van wijzigingen in het bestand van de mogelijkheid rol.
Een nieuwe JEA sessies gestart nadat de mogelijkheid van de rol is bijgewerkt weerspiegelt de herziene mogelijkheden.

Dit is de reden waarom het beheren van toegang tot de map van de mogelijkheden rol is daarom belangrijk.
Alleen uiterst vertrouwde beheerders moet kunnen wijzigen van de rol capability-bestanden.
Als een niet-vertrouwde gebruiker rol capability-bestanden wijzigen kunt, kunnen ze gemakkelijk zelf toegang geven tot cmdlets waarmee ze hun bevoegdheden.


Voor beheerders willen toegang tot de mogelijkheden van de rol voor het vergrendelen, zorg ervoor dat het dat lokale systeem leestoegang heeft tot de rol capability-bestanden en met modules.

## <a name="how-role-capabilities-are-merged"></a>Hoe de mogelijkheden van de rol worden samengevoegd

Gebruikers toegang kunnen krijgen tot meerdere mogelijkheden voor rol wanneer ze een sessie JEA, afhankelijk van de rol toewijzingen in de [sessie configuratiebestand](session-configurations.md).
Als dit gebeurt, JEA dat de gebruiker probeert de *meest strikte* reeks opdrachten die worden toegestaan door een van de rollen.

**VisibleCmdlets en VisibleFunctions**

De meest complexe logica voor het samenvoegen van invloed op cmdlets en -functies, die hun parameters en de parameterwaarden die zijn beperkt in JEA hebben.

De regels zijn als volgt:

1. Als een cmdlet alleen zichtbaar in één rol gemaakt is, worden deze zichtbaar is voor de gebruiker met beperkingen van toepassing parameter.
2. Als een cmdlet zichtbaar is in meer dan één rol wordt uitgevoerd, en elke rol de dezelfde beperkingen voor de cmdlet heeft, worden de cmdlet zichtbaar is voor de gebruiker met deze beperkingen.
3. Als een cmdlet zichtbaar is in meer dan één rol wordt uitgevoerd en een andere set parameters voor deze rol zijn toegestaan, zijn de cmdlet en alle parameters gedefinieerd voor elke rol zijn zichtbaar voor de gebruiker. Als een rol geen beperkingen voor de parameters, worden alle parameters mogen.
4. Als één rol een valideren set of een patroon valideren voor een cmdlet-parameter definieert en de andere rol mag de parameter, maar geen beperkingen van de parameterwaarden, worden de set valideren of het patroon wordt genegeerd.
5. Als een set valideren is gedefinieerd voor de dezelfde cmdlet-parameter in meer dan één rol, worden alle waarden uit alle valideren sets toegestaan.
6. Als een patroon valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, wordt er een waarden die met de patronen overeenkomen toegestaan.
7. Als een set valideren is gedefinieerd in een of meer rollen en een patroon valideren in een andere rol voor de dezelfde cmdlet-parameter is gedefinieerd, wordt de set valideren genegeerd en wordt regel (6) van toepassing op de resterende valideren patronen.

Hieronder volgt een voorbeeld van hoe de functies volgens deze regels worden samengevoegd:

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

Alle andere velden in het bestand van de mogelijkheid rol worden alleen toegevoegd aan een volledige reeks van toegestane externe opdrachten, aliassen providers en opstartscripts.
Elke opdracht, alias, provider of script in één rol functie beschikbaar zijn voor de gebruiker JEA beschikbaar.

Zorg ervoor dat u ervoor te zorgen dat de gecombineerde set met providers van een rol mogelijkheden en functies-cmdlets/opdrachten van een andere gebruikers niet toestaan verbindende onbedoelde toegang hebben tot systeembronnen.
Als een rol kunt bijvoorbeeld de `Remove-Item` cmdlet en andere kunnen de `FileSystem` provider, zijn op een JEA gebruiker willekeurige bestanden op uw computer verwijderd.
Als u meer informatie over het identificeren van de effectieve machtigingen van gebruikers kan worden gevonden in de [JEA onderwerp controle](audit-and-report.md).

## <a name="next-steps"></a>Volgende stappen

- [Een configuratiebestand sessie maken](session-configurations.md)

