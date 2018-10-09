---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: Controle en rapportage over JEA
ms.openlocfilehash: 2388c735840d8d3683aa8bc9869b9fb0371e5902
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851217"
---
# <a name="auditing-and-reporting-on-jea"></a>Controle en rapportage over JEA

> Is van toepassing op: Windows PowerShell 5.0

Nadat u de JEA hebt geïmplementeerd, wilt u regelmatige controle van de JEA-configuratie.
Dit helpt u bij het bepalen als de juiste personen toegang tot de JEA-eindpunt hebben en hun rollen nog steeds geschikt zijn.

Dit onderwerp beschrijft de verschillende manieren waarop u een JEA-eindpunt kunt controleren.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Geregistreerde JEA-sessies op een virtuele machine zoeken

Als u wilt controleren welke JEA-sessies op een virtuele machine zijn geregistreerd, gebruikt u de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

De effectieve machtigingen voor het eindpunt worden weergegeven in de eigenschap 'Permission'.
Deze gebruikers hebben het recht om te verbinden met de JEA-eindpunt, maar welke functies (en, bij uitbreiding, opdrachten) ze toegang hebben tot wordt bepaald door het veld 'RoleDefinitions' in de [sessie configuratiebestand](session-configurations.md) die is gebruikt voor het registreren van de het eindpunt.

U kunt de toewijzingen van de rol in een geregistreerde JEA-eindpunt evalueren door het uitbreiden van de gegevens in de eigenschap 'RoleDefinitions'.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Beschikbare rolmogelijkheden zoeken op de machine

Rol mogelijkheid bestanden wordt alleen worden gebruikt door JEA als ze zijn opgeslagen in een map "RoleCapabilities" binnen een geldig PowerShell-module.
U kunt alle functie mogelijkheden die beschikbaar zijn op een computer vinden door te zoeken naar de lijst met beschikbare modules.

```powershell
function Find-LocalRoleCapability {
    $results = @()

    # Find modules with a "RoleCapabilities" subfolder and add any PSRC files to the result set
    Get-Module -ListAvailable | ForEach-Object {
        $psrcpath = Join-Path -Path $_.ModuleBase -ChildPath 'RoleCapabilities'
        if (Test-Path $psrcpath) {
            $results += Get-ChildItem -Path $psrcpath -Filter *.psrc
        }
    }

    # Format the results nicely to make it easier to read
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{ Name = 'Path'; Expression = { $_.FullName }} | Sort-Object Name
}
```

> [!NOTE]
> De volgorde van de resultaten van deze functie is niet noodzakelijkerwijs de volgorde waarin de rolmogelijkheden worden geselecteerd als meerdere rolmogelijkheden dezelfde naam delen.

## <a name="check-effective-rights-for-a-specific-user"></a>Effectieve rechten voor een specifieke gebruiker controleren

Wanneer u een JEA-eindpunt hebt ingesteld, kunt u om te controleren welke opdrachten zijn beschikbaar voor een specifieke gebruiker in een JEA-sessie.
U kunt [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) opsommen van de opdrachten die van toepassing op een gebruiker als ze een JEA-sessie starten met de huidige groepslidmaatschappen.
De uitvoer van `Get-PSSessionCapability` is vrijwel identiek aan die van de opgegeven gebruiker uitgevoerd `Get-Command -CommandType All` in een JEA-sessie.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Als uw gebruikers niet permanent lid zijn van groepen die zou hun aanvullende JEA rechten verleend, kan deze extra machtigingen niet overeen met deze cmdlet.
Dit is meestal het geval is bij het gebruik van just-in-time privileged access management systemen kunnen gebruikers tijdelijk deel uitmaken van een beveiligingsgroep.
Evalueer altijd zorgvuldig de toewijzing van gebruikers aan rollen en de inhoud van elke rol om te controleren of gebruikers alleen toegang tot de opdrachten die nodig zijn voor hun werk doen zo min mogelijk krijgen.

## <a name="powershell-event-logs"></a>PowerShell-gebeurtenislogboeken

Als u de module en/of scripts blokkeren die zich aanmelden op het systeem hebt ingeschakeld, kunt u zich om gebeurtenissen te zoeken in de Windows-gebeurtenislogboeken voor elke opdracht die een gebruiker in de JEA-sessies worden uitgevoerd.
Als u wilt deze gebeurtenissen vinden, opent u de Windows-Logboeken, gaat u naar de **Microsoft-Windows-PowerShell/Operational** gebeurtenislogboek en zoek naar gebeurtenissen met de gebeurtenis-ID **4104**.

Elke logboekvermelding bevat informatie over de sessie waarin de opdracht is uitgevoerd.
JEA-sessies, dit omvat voor belangrijke informatie over de **ConnectedUser**, dit is de werkelijke gebruiker die de JEA-sessie gemaakt, evenals de **uitvoerenals** waarin het account waarmee JEA de opdracht niet uitvoeren.
Gebeurtenislogboeken van toepassingen wordt weergeven van wijzigingen van de uitvoerenals, dus met de uitgeschreven of module/script logboekregistratie is ingeschakeld is van cruciaal belang kunnen zijn voor het traceren van de aanroep van een specifieke opdracht terug naar een gebruiker.

## <a name="application-event-logs"></a>Logboeken voor toepassingen

Wanneer u een opdracht in een JEA-sessie die met een externe toepassing of service uitvoert communiceert, kunnen deze toepassingen gebeurtenissen registreren bij hun eigen Logboeken.
In tegenstelling tot de PowerShell-logboeken en transcripties, andere mechanismen voor logboekregistratie geen informatie over de gebruiker met de verbinding van de JEA-sessie en zich in plaats daarvan alleen aanmelden de virtuele run as-gebruiker of groep beheerd serviceaccount.
Om te bepalen wie de opdracht is uitgevoerd, moet u raadplegen een [sessie transcript](#session-transcripts) of PowerShell-logboeken correleren met de tijd en de gebruiker wordt weergegeven in het logboek voor toepassingsgebeurtenissen.

Het logboek kunt u ook correleren WinRM worden uitgevoerd als gebruikers in een logboek voor toepassingsgebeurtenissen aan de gebruiker die verbinding maakt.
Gebeurtenis-ID **193** in de **Microsoft-Windows-Windows Remote Management/operationeel** logboekregistratie van records de beveiligings-id (SID)-account een naam voor zowel de gebruiker verbinding maakt en uitvoeren als gebruiker telkens wanneer een JEA sessie wordt gemaakt.

## <a name="session-transcripts"></a>Transcripten van sessie

Als u de JEA voor het maken van een transcript voor elke gebruikerssessie hebt geconfigureerd, wordt een tekstkopie van acties van elke gebruiker worden opgeslagen in de opgegeven map.

Alle mappen van het transcript zoeken, de volgende opdracht uitvoeren als beheerder op de computer geconfigureerd met JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Elke transcript begint met informatie over de tijd van de sessie is gestart, welke gebruiker verbinding maken met de sessie en welke identiteit JEA aan hen is toegewezen.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

In de hoofdtekst van het transcript, wordt informatie over elke opdracht die wordt aangeroepen voor de gebruiker geregistreerd.
De exacte syntaxis van de opdracht uitgevoerd voor de gebruiker is niet beschikbaar in JEA-sessies door de manier waarop opdrachten worden getransformeerd voor externe communicatie van PowerShell, maar u kunt nog steeds bepalen de effectieve opdracht die is uitgevoerd.
Hieronder vindt u een fragment voor het transcript van voorbeeld van een gebruiker die de `Get-Service Dns` in een JEA-sessie:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Voor elke opdracht die wordt uitgevoerd door een gebruiker, een regel 'CommandInvocation' worden geschreven, met een beschrijving van de cmdlet of functie van de gebruiker die wordt aangeroepen.
ParameterBindings Volg elke CommandInvocation voor informatie over elke parameter en de waarde die is opgegeven met de opdracht.
In het bovenstaande voorbeeld ziet u dat de parameter 'Naam' is de waarde 'Dns' voor de cmdlet 'Get-Service' verstrekt.

De uitvoer van elke opdracht ook activeert een CommandInvocation meestal uitgaande standaardwaarden.
De InputObject Out-Default is het PowerShell-object geretourneerd door de opdracht.
De details van dat object worden afgedrukt een paar regels onder nauw mimicking wat de gebruiker zou hebben gezien.

## <a name="see-also"></a>Zie ook

- [*PowerShell ♥ het Blue Team* blogbericht over beveiliging](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)
