---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Configuratie- en omgevingsgegevens scheiden
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794923"
---
# <a name="separating-configuration-and-environment-data"></a>Configuratie- en omgevingsgegevens scheiden

>Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Kan het nuttig zijn voor het scheiden van de gegevens die worden gebruikt in een DSC-configuratie van de configuratie zelf met behulp van configuratiegegevens.
Op deze manier kunt kunt u een configuratie voor één gebruiken voor meerdere omgevingen.

Bijvoorbeeld, als u een toepassing ontwikkelt, kunt u één configuratie gebruiken voor zowel ontwikkeling als productie-omgevingen, en configuratiegegevens om op te geven van de gegevens voor elke omgeving.

## <a name="what-is-configuration-data"></a>Wat is configuratiegegevens?

Configuratiegegevens zijn gegevens die is gedefinieerd in een hash-tabel en doorgegeven aan een DSC-configuratie wanneer u deze configuratie compileren.

Voor een gedetailleerde beschrijving van de **ConfigurationData** hashtabel, Zie [met behulp van configuratiegegevens](configData.md).

## <a name="a-simple-example"></a>Een eenvoudig voorbeeld

Bekijk het voorbeeld van een zeer eenvoudig om te zien hoe dit werkt.
We maken een configuratie voor één die ervoor dat zorgt **IIS** aanwezig is op het aantal knooppunten, en dat **Hyper-V** aanwezig is op andere:

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

De laatste regel van dit script wordt de configuratie, doorgeven gecompileerd `$MyData` als de waarde **ConfigurationData** parameter.

Het resultaat is dat twee MOF-bestanden worden gemaakt:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` Hiermee geeft u twee verschillende knooppunten, met elk een eigen `NodeName` en `Role`. Dynamisch zorgt voor de configuratie van de **knooppunt** blokken aan de hand van de verzameling van knooppunten van krijgt `$MyData` (met name `$AllNodes`) en filters die verzameling op basis van de `Role` eigenschap...

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Met behulp van de configuratiegegevens voor het definiëren van ontwikkeling en productie-omgevingen

Bekijk een compleet voorbeeld die gebruikmaakt van een configuratie voor één voor het instellen van zowel ontwikkeling als productie-omgevingen van een website. Zowel IIS en SQL Server in de ontwikkelomgeving zijn geïnstalleerd op een afzonderlijke knooppunten. In de productieomgeving, zijn IIS en SQL Server geïnstalleerd op afzonderlijke knooppunten. Gebruiken we een bestand met configuratiegegevens .psd1 om op te geven van de gegevens voor de twee verschillende omgevingen.

### <a name="configuration-data-file"></a>Bestand met configuratiegegevens

Definiëren we de ontwikkeling en productie-omgeving-gegevens in een bestand met de naam `DevProdEnvData.psd1` als volgt:

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a>Configuratie van scriptbestand

Nu in de configuratie die is gedefinieerd in een `.ps1` bestand filteren we de knooppunten die we hebben gedefinieerd in `DevProdEnvData.psd1` door hun rol (`MSSQL`, `Dev`, of beide), en deze dienovereenkomstig configureren.
De ontwikkelomgeving heeft de SQL-Server en IIS op één knooppunt, terwijl de productie-omgeving ze op twee verschillende knooppunten heeft.
De site-inhoud is ook verschillend zijn, zoals opgegeven door de `SiteContents` eigenschappen.

Aan het einde van het configuratiescript, noemen we de configuratie (dit compileren in een MOF-document), waarbij `DevProdEnvData.psd1` als de `$ConfigurationData` parameter.

>**Opmerking:** Deze configuratie moet de modules `xSqlPs` en `xWebAdministration` worden geïnstalleerd op het doelknooppunt.

Laten we de configuratie wordt gedefinieerd in een bestand met de naam `MyWebApp.ps1`:

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

Wanneer u deze configuratie uitvoert, drie MOF-bestanden worden gemaakt (één voor elke vermelding in met de naam de **AllNodes** matrix):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Met behulp van niet-knooppuntgegevens

U kunt aanvullende sleutels toevoegen de **ConfigurationData** hashtabel voor gegevens die niet specifiek zijn voor een knooppunt.
De volgende configuratie zorgt ervoor dat de aanwezigheid van twee websites.
Gegevens voor elke website zijn gedefinieerd in de **AllNodes** matrix.
Het bestand `Config.xml` wordt gebruikt voor beide websites, zodat we de gegevens in een extra sleutel met de naam definiëren `NonNodeData`.
Houd er rekening mee dat u zoveel extra sleutels als u wilt en u kunt deze de naam elke gewenste kan hebben.
`NonNodeData` is niet een gereserveerd woord is net wat we besloten om de naam van de extra sleutel.

U toegang tot aanvullende sleutels met behulp van de speciale variabele **$ConfigurationData**.
In dit voorbeeld `ConfigFileContents` wordt geopend met de regel:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 in de `File` resource blokkeren.


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a>Zie ook
- [Met behulp van configuratiegegevens](configData.md)
- [Referentieopties in de configuratiegegevens](configDataCredentials.md)
- [DSC-configuraties](configurations.md)
