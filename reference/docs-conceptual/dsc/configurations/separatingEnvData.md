---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuratie- en omgevingsgegevens scheiden
description: Het kan handig zijn om de gegevens die in een DSC-configuratie worden gebruikt, te scheiden van de configuratie zelf met behulp van configuratie gegevens. Als u dit doet, kunt u één configuratie voor meerdere omgevingen gebruiken.
ms.openlocfilehash: 84ca4e4945a36111d23116524fd8f98c04e16d32
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645072"
---
# <a name="separating-configuration-and-environment-data"></a>Configuratie- en omgevingsgegevens scheiden

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

Het kan handig zijn om de gegevens die in een DSC-configuratie worden gebruikt, te scheiden van de configuratie zelf met behulp van configuratie gegevens. Als u dit doet, kunt u één configuratie voor meerdere omgevingen gebruiken.

Als u bijvoorbeeld een toepassing ontwikkelt, kunt u een configuratie gebruiken voor zowel ontwikkel-als productie omgevingen en configuratie gegevens gebruiken om gegevens op te geven voor elke omgeving.

## <a name="what-is-configuration-data"></a>Wat zijn configuratie gegevens?

Configuratie gegevens zijn gegevens die zijn gedefinieerd in een hashtabel en door gegeven aan een DSC-configuratie wanneer u die configuratie compileert.

Zie [configuratie gegevens gebruiken](configData.md)voor een gedetailleerde beschrijving van de **ConfigurationData** hashtabel.

## <a name="a-simple-example"></a>Een eenvoudig voor beeld

Laten we eens kijken naar een zeer eenvoudig voor beeld om te zien hoe dit werkt. Er wordt één configuratie gemaakt die ervoor zorgt dat **IIS** op sommige knoop punten aanwezig is en dat **Hyper-V** aanwezig is voor anderen:

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

De laatste regel in dit script compileert de configuratie, waarbij `$MyData` de para meter value **ConfigurationData** wordt door gegeven.

Het resultaat is dat er twee MOF-bestanden worden gemaakt:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` Hiermee geeft u twee verschillende knoop punten, elk met een eigen `NodeName` en `Role` . Met de configuratie worden dynamische **knooppunt** blokken gemaakt door de verzameling knoop punten te nemen die worden opgehaald `$MyData` (met name) en de verzameling wordt `$AllNodes` gefilterd op basis van de `Role` eigenschap.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Configuratie gegevens gebruiken voor het definiëren van ontwikkel-en productie omgevingen

Laten we eens kijken naar een volledig voor beeld dat één configuratie gebruikt voor het instellen van de ontwikkel-en productie omgeving van een website. In de ontwikkel omgeving worden zowel IIS als SQL Server geïnstalleerd op één knoop punt. In de productie omgeving worden IIS en SQL Server op afzonderlijke knoop punten geïnstalleerd. We gebruiken een configuratie gegevens. psd1-bestand om de gegevens voor de twee verschillende omgevingen op te geven.

### <a name="configuration-data-file"></a>Bestand met configuratie gegevens

De gegevens voor de ontwikkelings-en productie omgeving worden gedefinieerd in een bestand met de `DevProdEnvData.psd1` volgende naam:

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

### <a name="configuration-script-file"></a>Configuratie script bestand

Nu worden in de configuratie, die in een bestand is gedefinieerd `.ps1` , de knoop punten gefilterd die we in `DevProdEnvData.psd1` hun rol hebben gedefinieerd ( `MSSQL` , `Dev` of beide) en worden ze dienovereenkomstig geconfigureerd. De ontwikkel omgeving heeft zowel de SQL Server als IIS op één knoop punt, terwijl de productie omgeving ze op twee verschillende knoop punten heeft. De site-inhoud is ook anders, zoals opgegeven door de `SiteContents` Eigenschappen.

Aan het einde van het configuratie script noemen we de configuratie (Compileer deze in een MOF-document), waarbij `DevProdEnvData.psd1` de para meter wordt door gegeven `$ConfigurationData` .

> **Opmerking:** Voor deze configuratie moeten de modules `xSqlPs` en `xWebAdministration` worden geïnstalleerd op het doel knooppunt.

Laten we de configuratie definiëren in een bestand met de naam `MyWebApp.ps1` :

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

Wanneer u deze configuratie uitvoert, worden er drie MOF-bestanden gemaakt (één voor elke benoemde vermelding in de **AllNodes** -matrix):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Niet-knooppunt gegevens gebruiken

U kunt extra sleutels toevoegen aan de **ConfigurationData** hashtabel voor gegevens die niet specifiek voor een knoop punt zijn. De volgende configuratie zorgt ervoor dat er twee websites aanwezig zijn. De gegevens voor elke website worden gedefinieerd in de **AllNodes** -matrix. Het bestand `Config.xml` wordt gebruikt voor beide websites, dus we definiëren het in een extra sleutel met de naam `NonNodeData` . Houd er rekening mee dat u zoveel extra sleutels kunt hebben als u wilt, en u kunt ze elke gewenste naam geven. `NonNodeData` is geen gereserveerd woord. het is precies wat we hebben besloten om de extra sleutel een naam te bieden.

U hebt toegang tot extra sleutels met behulp van de speciale variabele **$ConfigurationData** . In dit voor beeld `ConfigFileContents` wordt toegang verkregen met de regel:

```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```

 in het `File` resource blok.

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

## <a name="see-also"></a>Zie ook

- [Configuratie gegevens gebruiken](configData.md)
- [Referenties opties in configuratie gegevens](configDataCredentials.md)
- [DSC-configuraties](configurations.md)
