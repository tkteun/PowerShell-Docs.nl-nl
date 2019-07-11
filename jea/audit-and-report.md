---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: Controle en rapportage over JEA
ms.openlocfilehash: 2afefe83acecc1fc3643d49766120ffecc25378f
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726751"
---
# <a name="auditing-and-reporting-on-jea"></a>Controle en rapportage over JEA

Nadat u de JEA hebt geïmplementeerd, moet u regelmatige controle van de JEA-configuratie. Controle kunt beoordelen u dat de juiste personen toegang tot de JEA-eindpunt hebben en hun rollen nog steeds geschikt zijn.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Geregistreerde JEA-sessies op een virtuele machine zoeken

Als u wilt controleren welke JEA-sessies op een virtuele machine zijn geregistreerd, gebruikt u de [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) cmdlet.

```powershell
# Filter for sessions that are configured as 'RestrictedRemoteServer' to find JEA-like session configurations
Get-PSSessionConfiguration | Where-Object { $_.SessionType -eq 'RestrictedRemoteServer' }
```

```Output
Name          : JEAMaintenance
PSVersion     : 5.1
StartupScript :
RunAsUser     :
Permission    : CONTOSO\JEA_DNS_ADMINS AccessAllowed, CONTOSO\JEA_DNS_OPERATORS AccessAllowed,
                CONTOSO\JEA_DNS_AUDITORS AccessAllowed
```

De effectieve machtigingen voor het eindpunt worden weergegeven in de **machtiging** eigenschap. Deze gebruikers hebben het recht om te verbinden met de JEA-eindpunt. Echter, de functies en ze toegang tot hebben opdrachten wordt bepaald door de **RoleDefinitions** eigenschap in de [sessie configuratiebestand](session-configurations.md) die is gebruikt voor het registreren van het eindpunt. Vouw de **RoleDefinitions** eigenschap voor de evaluatie van de toewijzingen van de rol in een geregistreerde JEA-eindpunt.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Beschikbare rolmogelijkheden zoeken op de machine

JEA opgehaald rolmogelijkheden uit de `.psrc` bestanden die zijn opgeslagen de **RoleCapabilities** map in een PowerShell-module. De volgende functie vindt alle rolmogelijkheden die beschikbaar zijn op een computer.

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
    $results | Select-Object @{ Name = 'Name'; Expression = { $_.Name.TrimEnd('.psrc') }}, @{
        Name = 'Path'; Expression = { $_.FullName }
    } | Sort-Object Name
}
```

> [!NOTE]
> De volgorde van de resultaten van deze functie is niet noodzakelijkerwijs de volgorde waarin de rolmogelijkheden worden geselecteerd als meerdere rolmogelijkheden dezelfde naam delen.

## <a name="check-effective-rights-for-a-specific-user"></a>Effectieve rechten voor een specifieke gebruiker controleren

De [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) cmdlet inventariseren alle opdrachten die beschikbaar zijn in een JEA-eindpunt op basis van groepslidmaatschappen van een gebruiker.
De uitvoer van `Get-PSSessionCapability` is vrijwel identiek aan die van de opgegeven gebruiker uitgevoerd `Get-Command -CommandType All` in een JEA-sessie.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Als uw gebruikers niet permanent lid zijn van groepen die zou hun aanvullende JEA rechten verleend, kan deze extra machtigingen niet overeen met deze cmdlet. Dit gebeurt wanneer u met behulp van just-in-time bevoegde toegang beheersystemen zodat gebruikers kunnen tijdelijk deel uitmaken van een beveiligingsgroep. Evalueer zorgvuldig de toewijzing van gebruikers aan functies en mogelijkheden om te zorgen dat gebruikers alleen het niveau van toegang die nodig zijn voor hun werk doen.

## <a name="powershell-event-logs"></a>PowerShell-gebeurtenislogboeken

Als u de module of script blokkeren die zich aanmelden op het systeem hebt ingeschakeld, ziet u gebeurtenissen in de Windows-gebeurtenislogboeken voor elke opdracht die wordt uitgevoerd door een gebruiker in een JEA-sessie. Als u wilt deze gebeurtenissen vinden, opent u **Microsoft-Windows-PowerShell/Operational** gebeurtenislogboek en zoek naar gebeurtenissen met de gebeurtenis-ID **4104**.

Elke logboekvermelding bevat informatie over de sessie waarin de opdracht is uitgevoerd. Voor de JEA-sessies, de gebeurtenis vindt u informatie over de **ConnectedUser** en de **uitvoerenals**. De **ConnectedUser** is de werkelijke gebruiker die de JEA-sessie gemaakt. De **uitvoerenals** is het account JEA gebruikt voor het uitvoeren van de opdracht.

Gebeurtenislogboeken van toepassingen weergeven wijzigingen van de **uitvoerenals**. Dus script logboekregistratie is ingeschakeld en het juiste module vereist tracering van de aanroep van een specifieke opdracht terug naar de **ConnectedUser**.

## <a name="application-event-logs"></a>Logboeken voor toepassingen

Opdrachten uitvoeren in een JEA-sessie die interactie hebben met externe toepassingen of services mogelijk gebeurtenissen op hun eigen Logboeken. In tegenstelling tot de PowerShell-logboeken en transcripties vastleggen geen andere mechanismen voor logboekregistratie van gebruiker met de verbinding van de JEA-sessie. In plaats daarvan deze toepassingen alleen Meld u aan de virtuele run as-gebruiker.
Om te bepalen wie de opdracht is uitgevoerd, moet u raadplegen een [sessie transcript](#session-transcripts) of PowerShell-logboeken correleren met de tijd en de gebruiker wordt weergegeven in het logboek voor toepassingsgebeurtenissen.

De WinRM-logboek kunt u het correleren van run as-gebruikers aan de gebruiker verbinding maakt in een logboek voor toepassingsgebeurtenissen. Gebeurtenis-ID **193** in de **Microsoft-Windows-Windows Remote Management/operationeel** log registreert de beveiligings-id (SID) en de accountnaam voor het maken van verbinding en zowel gebruikers uitvoeren als gebruiker voor elke nieuwe JEA de sessie.

## <a name="session-transcripts"></a>Transcripten van sessie

Als u de JEA voor het maken van een transcript voor elke gebruikerssessie hebt geconfigureerd, wordt een tekstkopie van acties van elke gebruiker worden opgeslagen in de opgegeven map.

De volgende opdracht (als een beheerder) vindt u alle transcript mappen.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
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

De hoofdtekst van het transcript bevat informatie over elke opdracht die de gebruiker wordt aangeroepen. De exacte syntaxis van de opdracht die wordt gebruikt, is niet beschikbaar in JEA-sessies vanwege de manier waarop opdrachten worden getransformeerd voor externe communicatie van PowerShell. U kunt echter nog steeds te bepalen de effectieve opdracht die is uitgevoerd. Hieronder vindt u een fragment voor het transcript van voorbeeld van een gebruiker die de `Get-Service Dns` in een JEA-sessie:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Een **CommandInvocation** regel is geschreven voor elke opdracht die een gebruiker wordt uitgevoerd. **ParameterBindings** opnemen van elke parameter en de waarde die is opgegeven met de opdracht. In het vorige voorbeeld, kunt u zien dat de parameter **naam** is opgegeven voor de waarde **Dns** voor de `Get-Service` cmdlet.

De uitvoer van elke opdracht ook triggers een **CommandInvocation**, meestal naar `Out-Default`. De **InputObject** van `Out-Default` wordt de PowerShell-object geretourneerd van de opdracht. De details van dat object worden afgedrukt een paar regels onder nauw mimicking wat de gebruiker zou hebben gezien.

## <a name="see-also"></a>Zie ook

[*PowerShell ♥ het Blue Team* blogbericht over beveiliging](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
