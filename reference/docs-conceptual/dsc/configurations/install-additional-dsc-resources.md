---
ms.date: 12/12/2018
keywords: DSC, Power shell, resource, Galerie, Setup
title: Aanvullende DSC-resources installeren
description: Dit artikel bevat een overzicht van de DSC-resources die zijn opgenomen in de PSDesiredStateConfiguration-module. Er wordt ook uitgelegd hoe u resources kunt zoeken en installeren vanaf de PowerShell Gallery.
ms.openlocfilehash: e75561ed539e06716c9a103f905b9d1e4f3e71d3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645128"
---
# <a name="install-additional-dsc-resources"></a>Aanvullende DSC-resources installeren

Power shell bevat verschillende out-of-the-box bronnen voor desired state Configuration (DSC). De **PSDesiredStateConfiguration** -module bevat alle OOB DSC-resources die beschikbaar zijn op uw specifieke instantie van Power shell.

Dit is een lijst met de OOB-resources die zijn opgenomen in Power Shell 4,0 en een beschrijving van de mogelijkheden van de resource.

> [!NOTE]
> Dit is een onvolledige lijst, omdat het aantal OOB-resources is toegenomen met elke versie van Power shell.

|      Resource      |                                                                                       Beschrijving                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **File**           | Hiermee bepaalt u de status van bestanden en mappen. Kopieert bestanden van een **bron** naar een **doel** en werkt deze bij wanneer de **bron** wordt gewijzigd door datums, controle sommen en hashes te vergelijken. |
| **Archiveren**        | De archieven en een opgegeven locatie worden uitgepakt. Valideert de archieven met een opgegeven **controlesom** .                                                                                         |
| **Omgeving**    | Hiermee beheert u omgevings variabelen.                                                                                                                                                           |
| **Groep**          | Beheert lokale groepen en beheert groepslid maatschap.                                                                                                                                      |
| **Logbestand**            | Hiermee worden berichten naar het `Microsoft-Windows-Desired State Configuration/Analytic` gebeurtenis logboek geschreven.                                                                                               |
| **Pakket**        | Installeert of verwijdert pakketten met behulp van **argumenten** , **logPath** , **return code** en andere instellingen.                                                                                        |
| **Register**       | Beheert register sleutels en-waarden.                                                                                                                                                        |
| **Script**         | Met kunt u uw eigen script blokken voor [Get-test-set](../resources/get-test-set.md) ontwerpen.                                                                                                |
| **Service**        | Hiermee configureert u Windows-Services.                                                                                                                                                             |
| **Gebruiker**           | Hiermee beheert u lokale gebruikers en kenmerken.                                                                                                                                                      |
| **WindowsFeature** | Beheert functies en onderdelen.                                                                                                                                                              |
| **WindowsProcess** | Configureert Windows-processen.                                                                                                                                                            |

De OOB-resources bieden een goed uitgangs punt voor veelvoorkomende bewerkingen. Als de OOB-resources niet aan uw behoeften voldoen, kunt u uw eigen [aangepaste resource](../resources/authoringResource.md)schrijven. Voordat u een aangepaste resource schrijft om uw probleem op te lossen, moet u het grote aantal DSC-resources dat u al hebt gemaakt door zowel micro soft als de Power shell-community bekijken.

U kunt DSC-resources vinden in zowel de [PowerShell Gallery](https://www.powershellgallery.com/) als de [github](https://github.com/). U kunt DSC-resources ook rechtstreeks installeren vanuit de Power shell-console met behulp van [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>PowerShellGet installeren

Als u wilt weten of u al **Power shell** Get hebt of als u hulp nodig hebt bij de installatie, raadpleegt u de volgende hand leiding: [Installing PowerShellGet](/powershell/scripting/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>DSC-resources zoeken met PowerShellGet

Zodra **PowerShellGet** op uw systeem is ge??nstalleerd, kunt u DSC-resources zoeken en installeren die worden gehost in de [PowerShell Gallery](https://www.powershellgallery.com/).

Gebruik eerst de cmdlet [Find-dscresource bieden](/powershell/module/powershellget/find-dscresource) om DSC-resources te zoeken. Wanneer u `Find-DSCResource` voor de eerste keer uitvoert, ziet u de volgende prompt om de NuGet-provider te installeren.

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies'
or 'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install
the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201
-Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Nadat u op y hebt gedrukt, wordt de NuGet-provider ge??nstalleerd en ziet u een lijst met DSC-resources die u vanuit de PowerShell Gallery kunt installeren.

> [!NOTE]
> De lijst wordt niet weer gegeven omdat deze erg groot is.

U kunt de `-Name` para meter ook opgeven met Joker tekens of `-Filter` para meter zonder joker tekens om uw zoek opdracht te verfijnen. In dit voor beeld wordt geprobeerd een ' time zone ' DSC-resource te vinden met behulp van de joker tekens.

> [!IMPORTANT]
> Er is momenteel een fout in de `Find-DSCResource` cmdlet die voor komt dat Joker tekens worden gebruikt in de `-Name` `-Filter` para meters en. In het tweede voor beeld hieronder ziet u een tijdelijke oplossing met behulp van `Where-Object` .

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

U kunt ook gebruiken `Where-Object` om DSC-resources te zoeken met nauw keurigere filters. Deze aanpak is trager dan het gebruik van ingebouwde filter parameters.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Zie voor meer informatie over filteren [where-object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>DSC-resources installeren met behulp van PowerShellGet

Als u een DSC-resource wilt installeren, gebruikt u de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) , waarbij u de naam opgeeft van de module die wordt weer gegeven onder **module** naam in uw zoek resultaten.

De resource ' tijd zone ' bevindt zich in de module ' ComputerManagementDSC ', dus de module die in dit voor beeld wordt ge??nstalleerd.

> [!NOTE]
> Als u de Power shell-galerie niet hebt vertrouwd, ziet u de onderstaande waarschuwing, waarna u wordt gevraagd hoe u volgende prompts voor de installatie wilt voor komen.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change
its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to
install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Druk op y om door te gaan met de installatie van de module. Na de installatie kunt u controleren of de nieuwe resource is ge??nstalleerd met behulp van [Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

U kunt ook andere resources in de zojuist ge??nstalleerde module bekijken door de para meter op te geven `-ModuleName` .

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Zie ook

- [Wat zijn resources?](../resources/resources.md)
