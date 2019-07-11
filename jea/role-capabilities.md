---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Rolmogelijkheden JEA
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726602"
---
# <a name="jea-role-capabilities"></a>Rolmogelijkheden JEA

Bij het maken van een JEA-eindpunt, moet u definiëren een of meer rolmogelijkheden waarin wordt beschreven wat iemand in een JEA-sessie kunt doen. De mogelijkheid van een rol is een PowerShell-gegevensbestand met de `.psrc` extensie met een lijst met alle cmdlets, functies, -providers en externe programma's die beschikbaar worden gesteld aan gebruikers verbinding te maken.

## <a name="determine-which-commands-to-allow"></a>Bepalen welke opdrachten om toe te staan

De eerste stap bij het maken van een bestand van rol mogelijkheid is om te overwegen wat de gebruikers moeten toegang hebben tot. Even kunnen duren voordat de vereisten voor proces voor het verzamelen, maar het is een belangrijk proces. Gebruikers toegang geven tot te weinig cmdlets en -functies kunt voorkomen dat ze aan hun werk gedaan te krijgen. Toestaan van toegang tot te veel cmdlets en functies kan gebruikers toestaan om meer dan u bedoeld en uw beveiliging virtualisatieproducten verzwakken te doen.

Hoe u over dit proces gaat, is afhankelijk van uw organisatie en doelstellingen. De volgende tips kunnen helpen Zorg ervoor dat u op de juiste weg bent.

1. **Identificeer** de gebruikers opdrachten wordt gebruikt om hun werk te doen. Hierbij kan het controleren van IT-personeel, automatiseringsscripts controleren of Transcripten van PowerShell-sessie en logboeken analyseren.
2. **Update** gebruik van opdrachtregelprogramma's voor PowerShell-equivalent, waar mogelijk, voor de beste controle- en JEA aanpassing ervaring. Externe programma's kunnen niet worden beperkt als granulair als systeemeigen PowerShell-cmdlets en functies in JEA.
3. **Beperken** het bereik van de cmdlets toe te staan dat bepaalde parameters of parameterwaarden. Dit is vooral belangrijk als gebruikers alleen deel uitmaken van een systeem te beheren.
4. **Maak** aangepaste functies om complexe opdrachten of opdrachten die moeilijk te beperken in JEA te vervangen. Een eenvoudige functie die loopt van een complexe opdracht of toepassing van extra validatielogica kan bieden extra controle voor het gemak van beheerders en eindgebruikers.
5. **Test** binnen het bereik de lijst met toegestane opdrachten door uw gebruikers of services, automation, en pas deze zo nodig.

### <a name="examples-of-potentially-dangerous-commands"></a>Voorbeelden van mogelijk schadelijke opdrachten

Zorg ervoor dat de selectie van opdrachten is het belangrijk om te controleren of de JEA-eindpunt niet toestaan dat de gebruiker hun machtigingen met verhoogde bevoegdheden.

> [!IMPORTANT]
> Essentiële informatie die nodig zijn voor de gebruiker successCommands in een JEA-sessie worden vaak uitgevoerd met verhoogde bevoegdheden.

De volgende tabel bevat voorbeelden van opdrachten die kunnen worden gebruikt opzettelijk als toegestaan in een onbeperkte status. Dit is niet een volledige lijst en mag alleen worden gebruikt als een ook beginpunt.

|                                            Risico 's                                            |                                Voorbeeld                                |                                                                              Gerelateerde opdrachten                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Verlenen van de gebruiker die verbinding maakt beheerdersbevoegdheden voor het overslaan van JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Uitvoeren van willekeurige code, zoals malware, aanvallen of aangepaste scripts te omzeilen: beveiliging | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Maak een bestand van de mogelijkheid rol

Kunt u een nieuw bestand rol mogelijkheid PowerShell met de [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) cmdlet.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Het resulterende bestand van de rol-mogelijkheid moet worden bewerkt om toe te staan de opdrachten die vereist zijn voor de rol. De PowerShell-help-documentatie bevat enkele voorbeelden van hoe u het bestand kunt configureren.

### <a name="allowing-powershell-cmdlets-and-functions"></a>PowerShell-cmdlets en-functies

Voor het autoriseren van gebruikers om uit te voeren PowerShell-cmdlets of functies toevoegen de naam van de cmdlet of functie in de velden VisibleCmdlets of VisibleFunctions. Als u niet zeker weet of een opdracht is een cmdlet of functie, kunt u uitvoeren `Get-Command <name>` en controleer de **CommandType** eigenschap in de uitvoer.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Soms is het bereik van een specifieke cmdlet of de functie is te breed voor de behoeften van uw gebruikers. Een DNS-beheerder, bijvoorbeeld waarschijnlijk enige behoeften toegang om de DNS-service opnieuw te starten. In omgevingen met meerdere tenants hebben tenants toegang tot Self-servicebeheer-hulpprogramma's. Tenants moeten worden beperkt tot het beheren van hun eigen resources. Voor deze gevallen kunt u beperken welke parameters beschikbaar worden gesteld van de cmdlet of functie.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

In de meer geavanceerde scenario's moet u mogelijk ook beperkt de waarden die van een gebruiker met deze parameters kan gebruiken. Rolmogelijkheden kunnen u bij het definiëren van een set waarden of een reguliere-expressiepatroon die bepalen welke invoer is toegestaan.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> De [algemene PowerShell-parameters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) zijn altijd toegestaan, zelfs als u de beschikbare parameters beperken.
> U dient niet expliciet vermeld in het veld Parameters.

De volgende tabel beschrijft de verschillende manieren waarop u kunt een zichtbaar cmdlet of functie.
U kunt combineren en matchen een van de hieronder in de **VisibleCmdlets** veld.

|                                           Voorbeeld                                           |                                                             Use-case                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` of `@{ Name = 'My-Func' }`                                                      | Kan de gebruiker om uit te voeren `My-Func` zonder beperkingen voor de parameters.                                                      |
| `'MyModule\My-Func'`                                                                        | Kan de gebruiker om uit te voeren `My-Func` uit de module `MyModule` zonder beperkingen voor de parameters.                           |
| `'My-*'`                                                                                    | Kan de gebruiker een cmdlet of de functie uitvoeren met de term `My`.                                                                 |
| `'*-Func'`                                                                                  | Hiermee kan de gebruiker een cmdlet of de functie uitvoeren met het zelfstandig naamwoord `Func`.                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` en `Param2` parameters. Elke waarde kan worden opgegeven met de parameters.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter. Alleen "Value1" en 'Value2' kan worden opgegeven voor de parameter.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Kan de gebruiker om uit te voeren `My-Func` met de `Param1` parameter. Een willekeurige waarde beginnen met 'contoso' kan worden opgegeven voor de parameter. |

> [!WARNING]
> Het verdient voor aanbevolen procedures voor beveiliging, geen jokertekens gebruiken bij het definiëren van zichtbaar cmdlets of functies. In plaats daarvan moet u elke vertrouwde opdracht om te controleren of er worden geen andere opdrachten die de dezelfde naamgevingsschema delen per ongeluk zijn gemachtigd expliciet vermelden.

U kunt geen toepassen beide een **ValidatePattern** en **ValidateSet** naar dezelfde cmdlet of functie.

Als u dit doet, de **ValidatePattern** overschrijft de **ValidateSet**.

Voor meer informatie over **ValidatePattern**, Bekijk [dit *Hallo, Scripting Guy!* boeken](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) en de [PowerShell reguliere expressies](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)-referentie-inhoud.

### <a name="allowing-external-commands-and-powershell-scripts"></a>Externe opdrachten en PowerShell-scripts toestaan

Als u wilt toestaan dat gebruikers uitvoerbare bestanden en PowerShell-scripts (.ps1) uitvoeren in een JEA-sessie, u moet het volledige pad toevoegen aan elk programma dat in de **VisibleExternalCommands** veld.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Waar mogelijk, voor het gebruik van PowerShell hebt-cmdlet of functie-equivalenten voor alle externe uitvoerbare bestanden verleent u onbevoegde gebruikers nadat u controle over de parameters die zijn toegestaan met PowerShell-cmdlets en -functies.

Veel uitvoerbare bestanden kunt u lezen van de huidige status en wijzig dit door op te geven van de verschillende parameters.

Neem bijvoorbeeld de rol van de beheerder van een bestand-server die worden beheerd die worden gehost op een systeem netwerkshares. Het beheren van bestandsshares op één manier is het gebruik `net share`. Echter, zodat **net.exe** is gevaarlijk omdat de gebruiker de opdracht gebruiken kan om te krijgen van beheerdersbevoegdheden met `net group Administrators unprivilegedjeauser /add`. Een veiliger optie is om toe te staan [Get-SmbShare](/powershell/module/smbshare/get-smbshare), die geven hetzelfde resultaat, maar heeft een zeer meer beperkt bereik.

Wanneer u externe opdrachten beschikbaar voor gebruikers in een JEA-sessie gebruiken, moet u altijd het volledige pad naar het uitvoerbare bestand opgeven. Dit voorkomt dat de uitvoering van op dezelfde manier met de naam mogelijk schadelijke programma's en ergens anders bevinden op het systeem.

### <a name="allowing-access-to-powershell-providers"></a>Toegang tot de PowerShell-providers

Er zijn geen PowerShell-providers zijn standaard beschikbaar in JEA-sessies. Dit vermindert het risico van gevoelige informatie en configuratie-instellingen die worden doorgegeven aan de gebruiker die verbinding maakt.

Indien nodig, kunt u de toegang tot de PowerShell-providers met behulp van de `VisibleProviders` opdracht. Voor een volledige lijst met providers, voert u `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Voor eenvoudige taken waarvoor toegang tot het bestandssysteem, register, certificaatarchief of andere gevoelige-providers, kunt u het schrijven van een aangepaste functie die geschikt is voor de provider namens de gebruiker. De functies, -cmdlets en externe programma's die beschikbaar zijn in een JEA-sessie zijn niet afhankelijk van de dezelfde beperkingen als JEA. Ze hebben toegang tot alle elke provider van standaard. Ook kunt u overwegen de [schijf van de gebruiker](session-configurations.md#user-drive) wanneer bestanden zijn gekopieerd naar of van een JEA-eindpunt is vereist.

### <a name="creating-custom-functions"></a>Het maken van aangepaste functies

U kunt aangepaste functies in een bestand rol mogelijkheid complexe taken vereenvoudigen voor uw eindgebruikers maken. Aangepaste functies zijn ook handig wanneer u geavanceerde validatielogica voor cmdlet parameterwaarden vereist. U kunt eenvoudig functies schrijven in de **FunctionDefinitions** veld:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Vergeet niet om toe te voegen van de naam van uw aangepaste functies voor de **VisibleFunctions** veld, zodat ze kunnen worden uitgevoerd door de JEA-gebruikers.

De hoofdtekst (scriptblok) van aangepaste functies in de standaardmodus voor de taal voor het systeem wordt uitgevoerd en niet is onderworpen aan beperkingen voor de JEA-taal. Dit betekent dat functies kunnen toegang krijgen het bestandssysteem en register tot en uitvoeren van opdrachten die in het bestand van de mogelijkheid rol zichtbaar zijn niet gemaakt. Wees voorzichtig om te voorkomen dat arbitraire code wordt uitgevoerd wanneer met behulp van parameters. Voorkomen dat de invoer van de gebruiker rechtstreeks in de cmdlets, zoals uitvoeromleiding `Invoke-Expression`.

In het bovenstaande voorbeeld ziet u dat de naam van de volledig gekwalificeerde module (FQMN) `Microsoft.PowerShell.Utility\Select-Object` is gebruikt in plaats van de steno `Select-Object`.
Functies die zijn gedefinieerd in de rol mogelijkheid bestanden zijn nog steeds afhankelijk van het bereik van JEA-sessies, waaronder de proxyfuncties JEA wordt gemaakt voor het beperken van bestaande opdrachten.

Standaard `Select-Object` is een beperkte cmdlet in alle sessies van JEA waarmee de selectie van eigenschappen van willekeurige voor objecten niet. Gebruik van de onbeperkte `Select-Object` in functies, moet u expliciet de volledige implementatie met behulp van de FQMN aanvragen. Een beperkte cmdlet in een JEA-sessie heeft de dezelfde beperkingen wordt aangeroepen vanuit een functie. Zie voor meer informatie, [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Als u meerdere aangepaste functies schrijft, is het handiger om ze in een PowerShell-script-module. U deze functies zichtbaar in de JEA-sessie met de **VisibleFunctions** veld, zoals u zou met ingebouwde en door de derde partij modules doen.

Tabblad voltooiing werken alleen goed in JEA sessies de ingebouwde functie moet opnemen `tabexpansion2` in de **VisibleFunctions** lijst.

## <a name="place-role-capabilities-in-a-module"></a>Rolmogelijkheden plaatsen in een module

In de volgorde voor PowerShell om te zoeken naar een bestand van de mogelijkheid rol, moet deze zijn opgeslagen in een **RoleCapabilities** map in een PowerShell-module. De module kan worden opgeslagen in een map die is opgenomen in de `$env:PSModulePath` omgevingsvariabele, maar u mag niet plaats deze in System32 of een map waar de niet-vertrouwde, verbinding te maken van gebruikers kan de bestanden wijzigen. Hieronder volgt een voorbeeld van het maken van een eenvoudige PowerShell-script-module met de naam **ContosoJEA** in de `$env:ProgramFiles` pad.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Zie voor meer informatie over PowerShell-modules, [inzicht krijgen in een PowerShell-Module](/powershell/developer/windows-powershell).

## <a name="updating-role-capabilities"></a>Rolmogelijkheden bijwerken

U kunt een bestand van de rol mogelijkheid voor het bijwerken van de instellingen op elk gewenst moment bewerken. Een nieuwe JEA-sessies gestart nadat de mogelijkheid van de rol is bijgewerkt, verschijnt op de nieuwe mogelijkheden.

Dit is de reden waarom het beheren van toegang tot de map van de mogelijkheden van rol is dus belangrijk. Alleen uiterst vertrouwde beheerders moeten worden toegestaan rol mogelijkheid bestanden te wijzigen. Als een niet-vertrouwde gebruiker rol mogelijkheid bestanden wijzigt kan, kunnen ze eenvoudig geven zelf toegang aan de cmdlets waarmee ze zijn bevoegdheden te verhogen.

Voor beheerders het vergrendelen van toegang tot de rolmogelijkheden wilt, zorg ervoor dat lokaal systeem, leestoegang heeft tot de rol mogelijkheid bestanden en met modules.

## <a name="how-role-capabilities-are-merged"></a>Hoe rolmogelijkheden worden samengevoegd

Gebruikers krijgen toegang tot alle overeenkomende rolmogelijkheden in de [sessie configuratiebestand](session-configurations.md) wanneer ze een JEA-sessie invoert. JEA probeert te geven van de gebruiker de meest strikte reeks opdrachten die zijn toegestaan door een van de rollen.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets en VisibleFunctions

De meest complexe logica voor het samenvoegen van invloed is op de cmdlets en -functies, waarvoor hun parameters en parameterwaarden in JEA beperkt.

De regels zijn als volgt:

1. Als een cmdlet is alleen zichtbaar zijn in één rol, is het zichtbaar voor de gebruiker met de beperkingen van toepassing parameter.
2. Als een cmdlet is zichtbaar in meer dan één rol, en elke rol de dezelfde beperkingen met betrekking tot de cmdlet heeft, wordt de cmdlet is zichtbaar voor de gebruiker met deze beperkingen.
3. Als een cmdlet is zichtbaar in meer dan één rol, en elke rol maakt het mogelijk een andere set parameters, zijn de cmdlet en de parameters die zijn gedefinieerd voor elke rol zichtbaar voor de gebruiker.
   Als één rol geen beperkingen met betrekking tot de parameters, worden alle parameters zijn toegestaan.
4. Als één rol een set valideren of patroon valideren voor een cmdlet-parameter definieert en de andere rol kunt u de parameter, maar legt geen beperkingen voor de parameterwaarden, wordt de set valideren of het patroon genegeerd.
5. Als een set valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, worden alle waarden uit alle valideren sets zijn toegestaan.
6. Als een patroon valideren voor de dezelfde cmdlet-parameter in meer dan één rol is gedefinieerd, worden alle waarden die overeenkomen met een van de patronen zijn toegestaan.
7. Als een set valideren is gedefinieerd in een of meer rollen, en een patroon valideren is gedefinieerd in een andere rol voor de dezelfde cmdlet-parameter, de set valideren wordt genegeerd en regel (6) is van toepassing op de resterende valideren patronen.

Hieronder volgt een voorbeeld van hoe de functies worden samengevoegd op basis van deze regels:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Alle andere velden in het bestand van de mogelijkheid rol worden toegevoegd aan een volledige reeks van toegestane externe opdrachten, aliassen, providers en opstartscripts. Elke opdracht, alias, provider of script beschikbaar is in één rol-functie is beschikbaar voor de JEA-gebruiker.

Wees voorzichtig om ervoor te zorgen dat de gecombineerde set-providers van een rol mogelijkheden en functies-cmdlets/opdrachten van een andere gebruikers kunnen geen onbedoelde toegang tot systeemresources.
Bijvoorbeeld, als een functie kan de `Remove-Item` cmdlet en andere kunnen de `FileSystem` provider, zijn op een JEA-gebruiker willekeurige bestanden op uw computer verwijderd. Als u meer informatie over het identificeren van de effectieve machtigingen van gebruikers te vinden in de [JEA controle](audit-and-report.md) artikel.

## <a name="next-steps"></a>Volgende stappen

[Een sessie-configuratiebestand maken](session-configurations.md)
