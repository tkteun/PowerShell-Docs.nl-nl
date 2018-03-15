---
ms.date: 2017-06-12
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: Controle en rapportage over JEA
ms.openlocfilehash: 57148bc3753bdd751bfa21fc3198aca3f8654849
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="auditing-and-reporting-on-jea"></a>Controle en rapportage over JEA

> Van toepassing op: Windows PowerShell 5.0

Nadat u JEA hebt geïmplementeerd, wilt u de configuratie van de JEA regelmatig te controleren.
Dit helpt u vast te stellen als de juiste personen toegang tot het eindpunt JEA hebben en hun rollen steeds van toepassing.

Dit onderwerp beschrijft de verschillende manieren waarop u een eindpunt JEA kunt controleren.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Geregistreerde JEA sessies op een machine vinden

Gebruiken om te controleren welke JEA-sessies zijn geregistreerd op een computer, de [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
PS C:\> Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }


Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed, CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

De effectieve rechten voor het eindpunt worden weergegeven in de eigenschap 'Permission'.
Deze gebruikers hebben het recht om te verbinden met het eindpunt JEA, maar welke rollen (en, bij uitbreiding, opdrachten) die toegang hebben tot wordt bepaald door het veld 'RoleDefinitions' in de [sessie configuratiebestand](session-configurations.md) die is gebruikt voor het registreren van de het eindpunt.

U kunt de toewijzingen van de rol in een geregistreerde JEA eindpunt evalueren door het uitbreiden van de gegevens in de eigenschap 'RoleDefinitions'.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{ Name = 'Role Capabilities'; Expression = { $_.Value.RoleCapabilities } }
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Mogelijkheden van de rol die beschikbaar is op de machine vinden

Rol capability-bestanden wordt alleen gebruikt door JEA als ze zijn opgeslagen in een map 'RoleCapabilities' binnen een geldig PowerShell-module.
U vindt alle rol mogelijkheden die beschikbaar zijn op een computer door te zoeken in de lijst met beschikbare modules.

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
> De volgorde van de resultaten van deze functie is niet per se de volgorde waarin de mogelijkheden van de rol worden geselecteerd als meerdere mogelijkheden van de functie dezelfde naam hebben.

## <a name="check-effective-rights-for-a-specific-user"></a>Controleer de rechten voor effectieve voor een specifieke gebruiker

Nadat u een eindpunt JEA hebt ingesteld, wilt u mogelijk controleren welke opdrachten beschikbaar zijn voor een specifieke gebruiker in een sessie JEA.
U kunt [Get-PSSessionCapability](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Get-PSSessionCapability) opsommen van de opdrachten die van toepassing op een gebruiker alsof ze een JEA-sessie starten met hun huidige groepslidmaatschap.
De uitvoer van `Get-PSSessionCapability` is gelijk aan dat de opgegeven gebruiker uitgevoerd `Get-Command -CommandType All` in een sessie JEA.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Als uw gebruikers niet permanent lid zijn van groepen die u zou hen aanvullende JEA rechten verleend zijn, kan deze extra machtigingen niet overeen met deze cmdlet.
Dit is doorgaans het geval bij gebruik van systemen voor just-in-time privileged access management zodat gebruikers tijdelijk aan een beveiligingsgroep horen.
De toewijzing van gebruikers aan rollen altijd zorgvuldig te evalueren en de inhoud van elke rol zodat gebruikers krijgen alleen toegang tot de kortste opdrachten die nodig zijn voor hun werk te doen.

## <a name="powershell-event-logs"></a>PowerShell-gebeurtenislogboeken

Als u de module en/of script blok logboekregistratie op het systeem hebt ingeschakeld, wordt u mogelijk zijn om te zoeken die in de Windows-gebeurtenislogboeken voor elke opdracht die een gebruiker wordt uitgevoerd in hun JEA-sessies.
Als u deze gebeurtenissen zoekt, de Windows-Logboeken te openen, gaat u naar de **Microsoft-Windows-PowerShell/operationeel** gebeurtenislogboek en zoeken naar gebeurtenissen met de gebeurtenis-ID **4104**.

Elke logboekvermelding bevat informatie over de sessie waarin de opdracht is uitgevoerd.
JEA sessies, dit omvat voor belangrijke informatie over de **ConnectedUser**, dit is de werkelijke gebruiker die de sessie JEA gemaakt, evenals de **uitvoerenals** die het account JEA waarmee wordt aangegeven de opdracht niet uitvoeren.
Gebeurtenislogboeken van toepassingen wordt weergeven van wijzigingen van de uitvoerenals rekening transcripties of module-script-logboekregistratie ingeschakeld is essentieel om te kunnen traceren van een aanroep van de specifieke opdracht terug naar een gebruiker.

## <a name="application-event-logs"></a>Gebeurtenislogboeken van toepassingen

Wanneer u een opdracht in een sessie JEA die met een externe toepassing of service uitvoert communiceert, kunnen deze toepassingen gebeurtenissen vastleggen in hun eigen Logboeken.
In tegenstelling tot PowerShell logboeken en transcripties andere mechanismen voor logboekregistratie niet de verbonden gebruiker van de sessie JEA vast en wordt in plaats daarvan alleen Meld u de virtuele run as-gebruiker of groep beheerd serviceaccount.
Om te bepalen wie de opdracht hebt uitgevoerd, moet u raadpleegt u een [tekst sessie](#session-transcripts) of PowerShell logboeken correleren met de tijd en de gebruiker wordt weergegeven in het logboek voor toepassingsgebeurtenissen.

De WinRM logboek kunt u ook correleren uitgevoerd als gebruikers in een logboek voor toepassingsgebeurtenissen aan de gebruiker verbinding probeert te maken.
Gebeurtenis-ID **193** in de **Microsoft Windows Windows Remote Management/operationeel** logboekregistratie records de beveiligings-id (SID)-account een naam voor zowel de gebruiker verbinding probeert te maken en uitvoeren als gebruiker telkens wanneer een JEA sessie wordt gemaakt.

## <a name="session-transcripts"></a>Sessie transcripties

Als u JEA voor het maken van een van de tekst voor elke gebruikerssessie hebt geconfigureerd, wordt een tekstkopie van acties van elke gebruiker opgeslagen in de opgegeven map.

Alle mappen van de tekst zoeken, voer de volgende opdracht als beheerder op de computer geconfigureerd met JEA:

```powershell
Get-PSSessionConfiguration | Where-Object { $_.TranscriptDirectory -ne $null } | Format-Table Name, TranscriptDirectory
```

Elk van de tekst begint met informatie over de tijd van de sessie is gestart, welke gebruiker verbonden met de sessie en welke identiteit JEA aan hen is toegewezen.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

In de hoofdtekst van de tekst van de gegevens vastgelegd over elke opdracht die de gebruiker wordt aangeroepen.
De syntaxis van de opdracht uitgevoerd voor de gebruiker is niet beschikbaar in JEA sessies vanwege de manier waarop opdrachten zijn getransformeerd voor externe communicatie van PowerShell, maar u kunt nog steeds bepalen de effectieve opdracht die werd uitgevoerd.
Hieronder volgt een voorbeeld van de tekst van fragment van een gebruiker met `Get-Service Dns` in een sessie JEA:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Voor elke opdracht die een gebruiker wordt uitgevoerd, een regel 'CommandInvocation' worden geschreven, met een beschrijving van de cmdlet of functie van de gebruiker die is aangeroepen.
ParameterBindings Volg elke CommandInvocation om aan te geven over elke parameter en de waarde die is opgegeven met de opdracht.
In het bovenstaande voorbeeld ziet u dat de parameter 'Name' is de waarde 'Dns' voor de cmdlet 'Get-Service' opgegeven.

De uitvoer van elke opdracht ook activeren een CommandInvocation meestal uitgaande standaardwaarden. De InputObject Out-Default is het PowerShell-object geretourneerd van de opdracht.
De details van dat object worden afgedrukt een paar regels hieronder nauw mimicking wat de gebruiker zou hebben gezien.

## <a name="see-also"></a>Zie ook

- [Acties van de gebruiker in een sessie JEA controleren](audit-and-report.md)
- [*PowerShell ♥ het Team van blauw* blogbericht op beveiliging](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

