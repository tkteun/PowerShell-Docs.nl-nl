---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Controleren en rapporteren op JEA
description: Met controle kunt u beoordelen of de juiste personen toegang hebben tot het JEA-eind punt en hun toegewezen rollen nog steeds geschikt zijn.
ms.openlocfilehash: 2140d6b756ae38d82e4943c373e8a75beea30e28
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92500008"
---
# <a name="auditing-and-reporting-on-jea"></a>Controleren en rapporteren op JEA

Nadat u JEA hebt geïmplementeerd, moet u de JEA-configuratie regel matig controleren. Met controle kunt u beoordelen of de juiste personen toegang hebben tot het JEA-eind punt en hun toegewezen rollen nog steeds geschikt zijn.

## <a name="find-registered-jea-sessions-on-a-machine"></a>Geregistreerde JEA-sessies op een computer zoeken

Als u wilt controleren welke JEA-sessies op een computer zijn geregistreerd, gebruikt u de cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) .

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

De juiste rechten voor het eind punt worden weer gegeven in de eigenschap **Permission** . Deze gebruikers hebben het recht om verbinding te maken met het JEA-eind punt. De rollen en opdrachten waartoe ze toegang hebben, worden echter bepaald door de eigenschap **RoleDefinitions** in het [sessie configuratie bestand](session-configurations.md) dat is gebruikt voor het registreren van het eind punt. Vouw de eigenschap **RoleDefinitions** uit om de roltoewijzingen in een geregistreerd JEA-eind punt te evalueren.

```powershell
# Get the desired session configuration
$jea = Get-PSSessionConfiguration -Name 'JEAMaintenance'

# Enumerate users/groups and which roles they have access to
$jea.RoleDefinitions.GetEnumerator() | Select-Object Name, @{
  Name = 'Role Capabilities'
  Expression = { $_.Value.RoleCapabilities }
}
```

## <a name="find-available-role-capabilities-on-the-machine"></a>Beschik bare functies op de computer zoeken

JEA haalt de functie mogelijkheden van de bestanden die zijn `.psrc` opgeslagen in de map **RoleCapabilities** binnen een Power shell-module. Met de volgende functie vindt u alle functie mogelijkheden die beschikbaar zijn op een computer.

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
> De volg orde van de resultaten van deze functie is niet noodzakelijkerwijs de volg orde waarin de functie mogelijkheden worden geselecteerd als meerdere functie mogelijkheden dezelfde naam hebben.

## <a name="check-effective-rights-for-a-specific-user"></a>De juiste rechten voor een specifieke gebruiker controleren

De cmdlet [Get-PSSessionCapability](/powershell/module/microsoft.powershell.core/Get-PSSessionCapability) inventariseert alle opdrachten die beschikbaar zijn op een JEA-eind punt op basis van de groepslid maatschappen van een gebruiker.
De uitvoer van `Get-PSSessionCapability` is identiek aan die van de opgegeven gebruiker die `Get-Command -CommandType All` in een JEA-sessie wordt uitgevoerd.

```powershell
Get-PSSessionCapability -ConfigurationName 'JEAMaintenance' -Username 'CONTOSO\Alice'
```

Als uw gebruikers geen permanente leden zijn van groepen die hen extra JEA-rechten verlenen, is het mogelijk dat deze cmdlet deze extra machtigingen niet weerspiegelt. Dit gebeurt wanneer u just-in-time privileged Access Management-systemen gebruikt om gebruikers toe te staan om tijdelijk te behoren tot een beveiligings groep. Evalueer zorgvuldig de toewijzing van gebruikers aan rollen en mogelijkheden om ervoor te zorgen dat gebruikers alleen het toegangs niveau krijgen dat nodig is om hun taken uit te voeren.

## <a name="powershell-event-logs"></a>Power shell-gebeurtenis logboeken

Als u logboek registratie van de module of het script blok op het systeem hebt ingeschakeld, kunt u gebeurtenissen in de Windows-gebeurtenis logboeken zien voor elke opdracht die een gebruiker in een JEA-sessie uitvoert. Als u deze gebeurtenissen wilt vinden, opent u het gebeurtenis logboek van **micro soft-Windows-Power shell/operationeel** en zoekt u naar gebeurtenissen met gebeurtenis-id **4104**.

Elke vermelding in het gebeurtenis logboek bevat informatie over de sessie waarin de opdracht is uitgevoerd. Voor JEA-sessies bevat de gebeurtenis informatie over de **ConnectedUser** en de **RunAsUser**. De **ConnectedUser** is de daad werkelijke gebruiker die de JEA-sessie heeft gemaakt. De **RunAsUser** is het account dat JEA gebruikt om de opdracht uit te voeren.

De gebeurtenis logboeken van de toepassing tonen wijzigingen die worden aangebracht door de **RunAsUser**. Daarom is het inschakelen van module-en script registratie vereist voor het traceren van een specifieke opdracht aanroep naar de **ConnectedUser**.

## <a name="application-event-logs"></a>Toepassings gebeurtenis logboeken

Opdrachten die worden uitgevoerd in een JEA-sessie die interactie met externe toepassingen of services, kunnen gebeurtenissen in hun eigen gebeurtenis logboeken registreren. In tegens telling tot Power shell-logboeken en-Transcripten worden andere logboek registratie mechanismen niet de verbonden gebruiker van de JEA-sessie vastgelegd. In plaats daarvan registreren deze toepassingen alleen de gebruiker voor de virtuele uitvoering.
Om te bepalen wie de opdracht heeft uitgevoerd, moet u een [transcript](#session-transcripts) voor de sessie raadplegen of de Power shell-gebeurtenis logboeken correleren met de tijd en gebruiker die wordt weer gegeven in het gebeurtenis logboek van de toepassing.

Het WinRM-logboek kan ook helpen bij het correleren van gebruikers met een gebruikers rechten in een toepassings gebeurtenis logboek. Gebeurtenis-ID **193** in het **micro soft-Windows-Windows-programma voor extern beheer/operationeel** logboek registreert u de BEVEILIGINGS-id (sid) en de account naam voor de gebruiker die verbinding maakt en uitvoeren als gebruiker voor elke nieuwe JEA-sessie.

## <a name="session-transcripts"></a>Transcripten van sessies

Als u JEA hebt geconfigureerd om voor elke gebruikers sessie een transcript te maken, wordt een tekst kopie van de acties van elke gebruiker opgeslagen in de opgegeven map.

Met de volgende opdracht (als beheerder) vindt u alle transcripten-mappen.

```powershell
Get-PSSessionConfiguration |
  Where-Object { $_.TranscriptDirectory -ne $null } |
    Format-Table Name, TranscriptDirectory
```

Elke transcript begint met informatie over de tijd dat de sessie is gestart, de gebruiker die verbinding heeft met de sessie en de JEA-identiteit die aan hen is toegewezen.

```
**********************
Windows PowerShell transcript start
Start time: 20160710144736
Username: CONTOSO\Alice
RunAs User: WinRM Virtual Users\WinRM VA_1_CONTOSO_Alice
Machine: SERVER01 (Microsoft Windows NT 10.0.14393.0)
[...]
```

De hoofd tekst van de transcriptie bevat informatie over elke opdracht die de gebruiker heeft aangeroepen. De exacte syntaxis van de gebruikte opdracht is niet beschikbaar in JEA-sessies vanwege de manier waarop opdrachten worden getransformeerd voor externe communicatie met Power shell. U kunt echter nog steeds de daad werkelijke opdracht bepalen die is uitgevoerd. Hieronder vindt u een voor beeld van een transcript fragment van een gebruiker die wordt uitgevoerd `Get-Service Dns` in een JEA-sessie:

```
PS>CommandInvocation(Get-Service): "Get-Service"
>> ParameterBinding(Get-Service): name="Name"; value="Dns"
>> CommandInvocation(Out-Default): "Out-Default"
>> ParameterBinding(Out-Default): name="InputObject"; value="Dns"

Running  Dns                DNS Server
```

Er wordt een **CommandInvocation** -regel geschreven voor elke opdracht die door een gebruiker wordt uitgevoerd. **ParameterBindings** registreert elke para meter en waarde die is opgegeven met de opdracht. In het vorige voor beeld ziet u dat de parameter **naam** is opgegeven met de waarde **DNS** voor de `Get-Service` cmdlet.

Met de uitvoer van elke opdracht wordt ook een **CommandInvocation** geactiveerd, meestal naar `Out-Default` . De **input object** van `Out-Default` is het Power shell-object dat wordt geretourneerd door de opdracht. De details van dat object worden hieronder weer gegeven, met een nauw keurig mimicking wat de gebruiker zou hebben gezien.

## <a name="see-also"></a>Zie ook

[*Power shell ♥ blog post van het blauwe team* op beveiliging](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
