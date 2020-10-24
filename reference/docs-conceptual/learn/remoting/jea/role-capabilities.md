---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: JEA
description: Een functie mogelijkheid is een Power shell-gegevens bestand met de extensie. psrc die alle cmdlets, functies, providers en externe Program ma's bevat die beschikbaar worden gesteld voor het verbinden van gebruikers.
ms.openlocfilehash: 233d9081f4a8f977f0959addb5573c4566f885d0
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499991"
---
# <a name="jea-role-capabilities"></a>JEA

Wanneer u een JEA-eind punt maakt, moet u een of meer functie mogelijkheden definiëren die beschrijven wat iemand kan doen in een JEA-sessie. Een functie mogelijkheid is een Power shell-gegevens bestand met de `.psrc` extensie waarin alle cmdlets, functies, providers en externe Program ma's worden vermeld die beschikbaar worden gesteld voor het verbinden van gebruikers.

## <a name="determine-which-commands-to-allow"></a>Bepalen welke opdrachten moeten worden toegestaan

De eerste stap bij het maken van een functie-mogelijkheidsprofiel is om te overwegen waarover de gebruikers toegang nodig hebben. Het proces van vereisten verzameling kan enige tijd duren, maar het is een belang rijk proces. Door gebruikers toegang te geven tot te weinig cmdlets en functies kan de taak niet worden uitgevoerd. Als u toegang tot te veel cmdlets en functies toestaat, kunnen gebruikers meer doen dan u hebt beoogd en uw beveiligings koers verzwakken.

Hoe u dit proces gaat, is afhankelijk van uw organisatie en doel stellingen. U kunt de volgende tips gebruiken om ervoor te zorgen dat u het juiste pad gebruikt.

1. **Identificeer** de opdrachten die gebruikers gebruiken om hun taken uit te voeren. Dit kan betrekking hebben op het onderzoeken van IT-personeel, het controleren van Automation-scripts of het analyseren van transcripten en logboeken van Power shell-sessies.
2. **Update** het gebruik van opdracht regel Programma's naar gelijkwaardige Power shell-equivalenten, waar mogelijk, voor de beste controle-en JEA aanpassings ervaring. Externe Program ma's kunnen niet worden beperkt als systeem eigen Power shell-cmdlets en-functies in JEA.
3. **Beperk** het bereik van de cmdlets zodat alleen specifieke para meters of parameter waarden kunnen worden toegestaan. Dit is vooral belang rijk als gebruikers slechts een deel van een systeem moeten beheren.
4. **Maak** aangepaste functies om complexe opdrachten of opdrachten te vervangen die moeilijk te beperken zijn in jea. Een eenvoudige functie waarmee een complexe opdracht wordt ingepakt of extra validatie logica wordt toegepast, kan extra controle bieden over beheerders en eind gebruikers eenvoud.
5. **Test** de scoped-lijst met toegestane opdrachten met uw gebruikers of Automation-Services en pas deze zo nodig aan.

### <a name="examples-of-potentially-dangerous-commands"></a>Voor beelden van mogelijk gevaarlijke opdrachten

Een zorgvuldige selectie van opdrachten is belang rijk om ervoor te zorgen dat het JEA-eind punt de gebruiker niet toestaat hun machtigingen te verhogen.

> [!IMPORTANT]
> Essentiële informatie die nodig is voor het successCommands van gebruikers in een JEA-sessie worden vaak uitgevoerd met verhoogde bevoegdheden.

De volgende tabel bevat voor beelden van opdrachten die schadelijk kunnen worden gebruikt als deze zijn toegestaan in een onbeperkte status. Dit is geen limitatieve lijst en mag alleen worden gebruikt als een voorzichtig uitgangs punt.

|                                            Risico                                            |                                Voorbeeld                                |                                                                              Gerelateerde opdrachten                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| De gebruikers beheerders rechten verlenen om JEA over te slaan                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Wille keurige code uitvoeren, zoals malware, cracks of aangepaste scripts om beveiligingen over te slaan | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Een functie-mogelijkheidsprofiel maken

U kunt een nieuw Power shell-functie bestand maken met de cmdlet [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile) .

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Het resulterende bestand met de functie moet worden bewerkt om de opdrachten toe te staan die vereist zijn voor de rol. De Help-documentatie voor Power shell bevat verschillende voor beelden van hoe u het bestand kunt configureren.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Power shell-cmdlets en-functies toestaan

Als u gebruikers wilt autoriseren om Power shell-cmdlets of-functies uit te voeren, voegt u de cmdlet of functie naam toe aan de velden VisibleCmdlets of VisibleFunctions. Als u niet zeker weet of een opdracht een cmdlet of functie is, kunt u `Get-Command <name>` de eigenschap **CommandType** in de uitvoer uitvoeren en controleren.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Soms is het bereik van een specifieke cmdlet of functie te breed voor de behoeften van uw gebruikers. Een DNS-beheerder heeft bijvoorbeeld waarschijnlijk alleen toegang nodig om de DNS-service opnieuw te starten. In omgevingen met meerdere tenants hebben tenants toegang tot Self-Service beheer hulpprogramma's. Tenants moeten worden beperkt tot het beheren van hun eigen resources. In dergelijke gevallen kunt u beperken welke para meters worden weer gegeven uit de cmdlet of functie.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

In meer geavanceerde scenario's moet u mogelijk ook de waarden beperken die een gebruiker mag gebruiken met deze para meters. Met functie mogelijkheden kunt u een reeks waarden of een reguliere-expressie patroon definiëren waarmee wordt bepaald welke invoer is toegestaan.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> De [algemene Power shell-para meters](/powershell/module/microsoft.powershell.core/about/about_commonparameters) zijn altijd toegestaan, zelfs als u de beschik bare para meters beperkt.
> U moet ze niet expliciet vermelden in het veld para meters.

In de volgende tabel worden de verschillende manieren beschreven waarop u een zicht bare cmdlet of functie kunt aanpassen.
U kunt elk van de onderstaande items combi neren in het veld **VisibleCmdlets** .

|                                           Voorbeeld                                           |                                                             Gebruiksvoorbeeld                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` of `@{ Name = 'My-Func' }`                                                      | Hiermee kan de gebruiker `My-Func` zonder beperkingen voor de para meters worden uitgevoerd.                                                      |
| `'MyModule\My-Func'`                                                                        | Hiermee kan de gebruiker `My-Func` `MyModule` zonder enige beperkingen van de para meters worden uitgevoerd vanuit de module.                           |
| `'My-*'`                                                                                    | Hiermee kan de gebruiker een cmdlet of functie met de bewerking uitvoeren `My` .                                                                 |
| `'*-Func'`                                                                                  | Hiermee kan de gebruiker een cmdlet of functie uitvoeren met het zelfstandig naam woord `Func` .                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Hiermee kan de gebruiker uitvoeren `My-Func` met de `Param1` `Param2` para meters en. Elke waarde kan worden opgegeven voor de para meters.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Hiermee kan de gebruiker `My-Func` met de `Param1` para meter worden uitgevoerd. Alleen waarde1 en waarde2 kunnen worden opgegeven voor de para meter.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Hiermee kan de gebruiker `My-Func` met de `Param1` para meter worden uitgevoerd. Elke waarde die begint met ' Contoso ' kan worden opgegeven voor de para meter. |

> [!WARNING]
> Voor de beste beveiligings procedures wordt het niet aanbevolen joker tekens te gebruiken bij het definiëren van zicht bare cmdlets of functies. In plaats daarvan moet u elke vertrouwde opdracht expliciet vermelden om ervoor te zorgen dat geen andere opdrachten die hetzelfde naamgevings schema delen, per ongeluk worden geautoriseerd.

U kunt niet zowel een **ValidatePattern** als **Validate** Toep assen op dezelfde cmdlet of functie.

Als u dat wel doet, overschrijft de **ValidatePattern** de **validatieset**.

Bekijk voor meer informatie over **ValidatePattern** [dit *Hoi, Scripting Guy!* post](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) en de referentie-inhoud voor [reguliere Power shell-expressies](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) .

### <a name="allowing-external-commands-and-powershell-scripts"></a>Externe opdrachten en Power shell-scripts toestaan

Als u wilt toestaan dat gebruikers uitvoer bare en Power shell-scripts (. ps1) uitvoeren in een JEA-sessie, moet u het volledige pad toevoegen aan elk programma in het veld **VisibleExternalCommands** .

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Als dat mogelijk is, kunt u de Power shell-cmdlet of functie equivalenten gebruiken voor externe uitvoer bare bestanden die u machtigt, omdat u de controle hebt over de para meters die zijn toegestaan met Power shell-cmdlets en-functies

Met veel uitvoer bare bestanden kunt u de huidige status lezen en deze vervolgens wijzigen door verschillende para meters op te geven.

Denk bijvoorbeeld aan de rol van een bestands Server beheerder die netwerk shares beheert die worden gehost op een systeem. Een manier om shares te beheren, is het gebruik van `net share` . Het toestaan van **net.exe** echter gevaarlijk omdat de gebruiker de opdracht kan gebruiken om beheerders bevoegdheden te verkrijgen met `net group Administrators unprivilegedjeauser /add` . Een veiligere optie is om [Get-SmbShare](/powershell/module/smbshare/get-smbshare)toe te staan, waardoor hetzelfde resultaat wordt gerealiseerd, maar een veel beperkt bereik heeft.

Wanneer u externe opdrachten beschikbaar wilt maken voor gebruikers in een JEA-sessie, geeft u altijd het volledige pad naar het uitvoer bare bestand op. Dit voor komt dat de uitvoering van op dezelfde wijze benoemde en mogelijk schadelijke Program ma's elders op het systeem wordt uitgevoerd.

### <a name="allowing-access-to-powershell-providers"></a>Toegang tot Power shell-providers toestaan

Standaard zijn er geen Power shell-providers beschikbaar in JEA-sessies. Dit vermindert het risico van gevoelige informatie en configuratie-instellingen die worden gepresenteerd aan de gebruiker die verbinding maakt.

Als dat nodig is, kunt u toegang tot de Power shell-providers toestaan met behulp van de `VisibleProviders` opdracht. Voer uit voor een volledige lijst met providers `Get-PSProvider` .

```powershell
VisibleProviders = 'Registry'
```

Voor eenvoudige taken waarvoor toegang tot het bestands systeem, het REGI ster, het certificaat archief of andere gevoelige providers vereist is, kunt u een aangepaste functie schrijven die werkt met de provider namens de gebruiker. De functies, cmdlets en externe Program ma's die beschikbaar zijn in een JEA-sessie, zijn niet onderhevig aan dezelfde beperkingen als JEA. Ze hebben standaard toegang tot elke provider. Overweeg ook het gebruik van het [gebruikers station](session-configurations.md#user-drive) bij het kopiëren van bestanden naar of van een JEA-eind punt.

### <a name="creating-custom-functions"></a>Aangepaste functies maken

U kunt aangepaste functies in een functie-mogelijkheidsprofiel ontwerpen om complexe taken voor uw eind gebruikers te vereenvoudigen. Aangepaste functies zijn ook handig als u geavanceerde validatie logica nodig hebt voor cmdlet-parameter waarden. U kunt eenvoudige functies schrijven in het veld **FunctionDefinitions** :

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
> Vergeet niet om de naam van uw aangepaste functies toe te voegen aan het veld **VisibleFunctions** zodat deze door de JEA-gebruikers kunnen worden uitgevoerd.

De hoofd tekst (script blok) van aangepaste functies wordt uitgevoerd in de standaard taal modus voor het systeem en is niet onderhevig aan de taal beperkingen van de JEA. Dit betekent dat functies toegang hebben tot het bestands systeem en het REGI ster en om opdrachten uit te voeren die niet zichtbaar zijn gemaakt in het functie-Capability-bestand. Zorg ervoor dat u geen wille keurige code uitvoert wanneer para meters worden gebruikt. Vermijd de gebruikers invoer van sluizen rechtstreeks in cmdlets zoals `Invoke-Expression` .

In het bovenstaande voor beeld ziet u dat de volledig gekwalificeerde module naam (FQMN) `Microsoft.PowerShell.Utility\Select-Object` is gebruikt in plaats van de steno `Select-Object` .
Functies die zijn gedefinieerd in de functie-Capability-bestanden, zijn nog steeds afhankelijk van het bereik van JEA-sessies. Dit omvat de proxy functies JEA maakt om bestaande opdrachten te beperken.

Standaard `Select-Object` is een beperkte cmdlet in alle JEA-sessies die niet toestaan dat wille keurige eigenschappen van objecten worden geselecteerd. U kunt de `Select-Object` volledige implementatie expliciet aanvragen met behulp van de FQMN om de onbeperkte functies te gebruiken. Een beperkte cmdlet in een JEA-sessie heeft dezelfde beperkingen als deze worden aangeroepen vanuit een functie. Zie [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)voor meer informatie.

Als u verschillende aangepaste functies schrijft, is het handiger om ze in een Power shell-script module te plaatsen. U maakt deze functies zichtbaar in de JEA-sessie met behulp van het veld **VisibleFunctions** , zoals u dat ook zou doen met ingebouwde en modules van derden.

Voor een juiste werking van de tabtoets in JEA-sessies moet u de ingebouwde functie opnemen `tabexpansion2` in de **VisibleFunctions** -lijst.

## <a name="make-the-role-capabilities-available-to-a-configuration"></a>De functie mogelijkheden beschikbaar maken voor een configuratie

Vóór Power shell 6, voor Power shell om een functie bestand te vinden, moet het worden opgeslagen in een **RoleCapabilities** -map in een Power shell-module. De module kan worden opgeslagen in een map die is opgenomen in de `$env:PSModulePath` omgevings variabele, maar mag niet worden geplaatst in `$env:SystemRoot\System32` of een map waarin niet-vertrouwde gebruikers de bestanden kunnen wijzigen.

In het volgende voor beeld wordt een Power shell-script module gemaakt met de naam **ContosoJEA** in het `$env:ProgramFiles` pad voor het hosten van het bestand met functie mogelijkheden.

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

Zie [Wat is een Power shell-module](/powershell/scripting/developer/windows-powershell)? voor meer informatie over Power shell-modules.

Vanaf Power shell 6 is de eigenschap **RoleDefinitions** toegevoegd aan het configuratie bestand van de sessie. Met deze eigenschap kunt u de locatie van een functie configuratie bestand opgeven voor de roldefinitie. Zie de voor beelden in [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile).

## <a name="updating-role-capabilities"></a>De functie mogelijkheden worden bijgewerkt

U kunt een functie-mogelijkheidsprofiel bewerken om de instellingen op elk gewenst moment bij te werken. Nieuwe JEA-sessies die zijn gestart nadat de functie mogelijkheid is bijgewerkt, worden weer gegeven in de gewijzigde mogelijkheden.

Daarom is het belang rijk om de toegang tot de map functie mogelijkheden te beheren. Alleen zeer vertrouwde beheerders mogen de functie-Capability-bestanden wijzigen. Als een niet-vertrouwde gebruiker de functie-Capability-bestanden kan wijzigen, kunnen ze eenvoudig toegang krijgen tot cmdlets die hen in staat stellen hun bevoegdheden uit te breiden.

Voor beheerders die de toegang tot de functie mogelijkheden willen vergren delen, zorgt u ervoor dat het lokale systeem lees toegang heeft tot de functie bestanden en modules bevat.

## <a name="how-role-capabilities-are-merged"></a>Hoe functie mogelijkheden worden samengevoegd

Gebruikers krijgen toegang tot alle overeenkomende functie mogelijkheden in het [sessie configuratie bestand](session-configurations.md) wanneer ze een JEA-sessie invoeren. JEA probeert de gebruiker de meest strikte set opdrachten te geven die is toegestaan door een van de rollen.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets en VisibleFunctions

De meest complexe samenvoeg logica heeft gevolgen voor cmdlets en functies, die de para meters en parameter waarden kunnen hebben beperkt in JEA.

De regels zijn als volgt:

1. Als een cmdlet alleen zichtbaar wordt gemaakt in de ene rol, is deze zichtbaar voor de gebruiker met alle toepasselijke parameter beperkingen.
2. Als een cmdlet in meer dan één rol zichtbaar is en elke rol dezelfde beperkingen heeft voor de cmdlet, is de cmdlet zichtbaar voor de gebruiker met die beperkingen.
3. Als een cmdlet in meer dan één rol zichtbaar is en elke rol een andere set para meters toestaat, zijn de cmdlets en alle para meters die zijn gedefinieerd voor elke rol zichtbaar voor de gebruiker.
   Als een rol geen beperkingen voor de para meters heeft, zijn alle para meters toegestaan.
4. Als een van de rollen een validatieset of validatie patroon voor een cmdlet-para meter definieert en de andere functie de para meter toestaat, maar de parameter waarden niet beperkt, wordt de set of het patroon valideren genegeerd.
5. Als er in meer dan één rol een validate-set is gedefinieerd voor dezelfde cmdlet-para meter, zijn alle waarden van alle validatie sets toegestaan.
6. Als er in meer dan één rol een validatie patroon is gedefinieerd voor dezelfde cmdlet-para meter, zijn waarden die overeenkomen met een van de patronen toegestaan.
7. Als er een validate-set is gedefinieerd in een of meer rollen en een validatie patroon is gedefinieerd in een andere rol voor dezelfde cmdlet-para meter, wordt de set validate genegeerd en regel (6) van toepassing op de resterende validatie patronen.

Hieronder ziet u een voor beeld van hoe rollen worden samengevoegd volgens deze regels:

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

Alle andere velden in het bestand met de functie worden toegevoegd aan een cumulatieve set toegestane externe opdrachten, aliassen, providers en opstart scripts. Alle opdrachten, aliassen, providers of scripts die beschikbaar zijn in een functie mogelijkheid, zijn beschikbaar voor de JEA-gebruiker.

Zorg ervoor dat de gecombineerde set providers van de ene functie mogelijkheid en cmdlets/functions/functies/opdrachten van een andere gebruikers geen onbedoelde toegang tot systeem bronnen biedt.
Als bijvoorbeeld de ene rol de cmdlet toestaat `Remove-Item` en een andere de `FileSystem` provider toestaat, loopt u het risico dat een JEA-gebruiker wille keurige bestanden op uw computer verwijdert. Meer informatie over het identificeren van de juiste machtigingen van gebruikers vindt u in het artikel [controle JEA](audit-and-report.md) .

## <a name="next-steps"></a>Volgende stappen

[Een configuratie bestand voor de sessie maken](session-configurations.md)
