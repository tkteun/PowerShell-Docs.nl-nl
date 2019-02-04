---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, galerie, instellen
title: Installeren van extra DSC-Resources
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686381"
---
# <a name="install-additional-dsc-resources"></a>Installeren van extra DSC-Resources

PowerShell bevat verschillende Out-of-the-box-resources voor Desired State Configuration (DSC). De **PSDesiredStateConfiguration** -module bevat alle OOB DSC-resources beschikbaar is op uw specifieke exemplaar van PowerShell.

Dit is een overzicht van de OOB-resources dat is opgenomen in PowerShell 4.0 en een beschrijving van de mogelijkheden van de resource.

> [!NOTE]
> Dit is een onvolledige lijst, zoals het aantal resources OOB is toegenomen bij elke versie van PowerShell.

|Informatiebron  |Beschrijving  |
|---------|---------|
|**File**|Hiermee bepaalt u de status van bestanden en mappen. Kopieert bestanden van een **bron** naar een **bestemming** en wordt deze bijgewerkt wanneer de **bron** wijzigingen door het vergelijken van datums, controlesommen en hashes.|
|**Archiveren**|Hiermee wordt de archieven en een opgegeven locatie. Valideert de archieven met een opgegeven **controlesom**.|
|**Omgeving**|Hiermee beheert u omgevingsvariabelen.|
|**Groep**|Lokale groepen worden beheerd en besturingselementen van groepslidmaatschap.|
|**Log**|Schrijft berichten naar de `Microsoft-Windows-Desired State Configuration/Analytic` gebeurtenislogboek.|
|**Package**|Installeert of verwijdert met behulp van pakketten **argumenten**, **LogPath**, **ReturnCode**, andere instellingen.|
|**Registry**|Hiermee beheert u sleutels en waarden.|
|**Script**|U ontwerpt waarmee u uw eigen [get-test-set](../resources/get-test-set.md) scriptblokken.|
|**Service**|Hiermee configureert u Windows-services.|
|**User** |Hiermee beheert u lokale gebruikers en -kenmerken.|
|**WindowsFeature**|Hiermee beheert u functies en onderdelen.|
|**WindowsProcess**|Hiermee configureert u Windows-processen.|

De OOB-resources kunnen een goed uitgangspunt voor algemene bewerkingen. Als de OOB-resources niet voldoen aan uw behoeften, kunt u uw eigen [aangepaste Resource](../resources/authoringResource.md). Voordat u schrijft een aangepaste bron uit voor het probleem kunt oplossen, moet u zoeken door het grote aantal van de DSC-resources die al zijn gemaakt door zowel Microsoft als de PowerShell-community.

U kunt DSC-resources zoeken in zowel de [PowerShell Gallery](https://www.powershellgallery.com/) en [GitHub](https://github.com/). U kunt ook DSC-resources rechtstreeks vanuit de PowerShell-console via installeren [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>PowerShellGet installeren

Om te bepalen of u al hebt **PowerShell** ophalen of hulp bij het installeren, Zie de volgende handleiding: [PowerShellGet installeren](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>DSC-resources met behulp van PowerShellGet zoeken

Eenmaal **PowerShellGet** is geïnstalleerd op uw systeem, kunt u zoeken en installeren van de DSC-resources die worden gehost de [PowerShell Gallery](https://www.powershellgallery.com/).

Gebruik eerst de [sleutelwoorden zoeken-dscresource bieden](/powershell/module/powershellget/find-dscresource) cmdlet DSC-resources vinden. Bij het uitvoeren van `Find-DSCResource` voor het eerst, ziet u het volgende bericht voor het installeren van de 'NuGet-provider'.

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

Nadat te drukken "y", de 'NuGet'-provider is geïnstalleerd, ziet u een lijst van DSC-resources die u vanuit de PowerShell Gallery installeren kunt.

> [!NOTE]
> Lijst wordt niet weergegeven omdat het erg groot is.

U kunt ook opgeven de `-Name` met jokertekens, parameter of `-Filter` parameter zonder jokertekens aan uw zoekopdracht verfijnen. In dit voorbeeld wordt gezocht naar een "Tijdzone" DSC-resource met behulp van de jokertekens.

> [!IMPORTANT]
> Er is momenteel een bug in de `Find-DSCResource` cmdlet waarmee wordt voorkomen dat het gebruik van jokertekens in zowel de `-Name` en `-Filter` parameters. Het tweede voorbeeld hieronder ziet u een tijdelijke oplossing met `Where-Object`.

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

U kunt ook `Where-Object` DSC-resources met gedetailleerdere filteren vinden. Deze aanpak is langzamer dan het gebruik van ingebouwde parameters filteren.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Zie voor meer informatie over het filteren van [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>DSC-Resources met behulp van PowerShellGet installeren

Voor het installeren van een DSC-resource, gebruikt u de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, op te geven de naam van de module die wordt weergegeven onder **Module** naam in de lijst met zoekresultaten.

De resource "Tijdzone" bestaat dus dat wil zeggen dat de module in dit voorbeeld wordt geïnstalleerd in de module 'ComputerManagementDSC'.

> [!NOTE]
> Als u hebt de PowerShell gallery niet wordt vertrouwd, ziet u de waarschuwing onder dat om bevestiging wordt gevraagd en dat u hoe u om te voorkomen dat verdere aanwijzingen op geïnstalleerd.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Druk op 'y' om door te gaan met het installeren van de module. Na de installatie, kunt u controleren of uw nieuwe resource is geïnstalleerd met behulp van [sleutelwoorden Get-dscresource bieden](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

U kunt ook andere resources in uw geïnstalleerde module weergeven door op te geven de `-ModuleName` parameter.

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

- [Wat zijn Resources?](../resources/resources.md)
