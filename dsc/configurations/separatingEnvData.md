---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Configuratie- en omgevingsgegevens scheiden
ms.openlocfilehash: 305a766fec81d4ea4afce187756188b067a2048b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080030"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="08723-103">Configuratie- en omgevingsgegevens scheiden</span><span class="sxs-lookup"><span data-stu-id="08723-103">Separating configuration and environment data</span></span>

><span data-ttu-id="08723-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08723-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="08723-105">Kan het nuttig zijn voor het scheiden van de gegevens die worden gebruikt in een DSC-configuratie van de configuratie zelf met behulp van configuratiegegevens.</span><span class="sxs-lookup"><span data-stu-id="08723-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="08723-106">Op deze manier kunt kunt u een configuratie voor één gebruiken voor meerdere omgevingen.</span><span class="sxs-lookup"><span data-stu-id="08723-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="08723-107">Bijvoorbeeld, als u een toepassing ontwikkelt, kunt u één configuratie gebruiken voor zowel ontwikkeling als productie-omgevingen, en configuratiegegevens om op te geven van de gegevens voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="08723-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="08723-108">Wat is configuratiegegevens?</span><span class="sxs-lookup"><span data-stu-id="08723-108">What is configuration data?</span></span>

<span data-ttu-id="08723-109">Configuratiegegevens zijn gegevens die is gedefinieerd in een hash-tabel en doorgegeven aan een DSC-configuratie wanneer u deze configuratie compileren.</span><span class="sxs-lookup"><span data-stu-id="08723-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="08723-110">Voor een gedetailleerde beschrijving van de **ConfigurationData** hashtabel, Zie [met behulp van configuratiegegevens](configData.md).</span><span class="sxs-lookup"><span data-stu-id="08723-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="08723-111">Een eenvoudig voorbeeld</span><span class="sxs-lookup"><span data-stu-id="08723-111">A simple example</span></span>

<span data-ttu-id="08723-112">Bekijk het voorbeeld van een zeer eenvoudig om te zien hoe dit werkt.</span><span class="sxs-lookup"><span data-stu-id="08723-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="08723-113">We maken een configuratie voor één die ervoor dat zorgt **IIS** aanwezig is op het aantal knooppunten, en dat **Hyper-V** aanwezig is op andere:</span><span class="sxs-lookup"><span data-stu-id="08723-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

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

<span data-ttu-id="08723-114">De laatste regel van dit script wordt de configuratie, doorgeven gecompileerd `$MyData` als de waarde **ConfigurationData** parameter.</span><span class="sxs-lookup"><span data-stu-id="08723-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="08723-115">Het resultaat is dat twee MOF-bestanden worden gemaakt:</span><span class="sxs-lookup"><span data-stu-id="08723-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="08723-116">`$MyData` Hiermee geeft u twee verschillende knooppunten, met elk een eigen `NodeName` en `Role`.</span><span class="sxs-lookup"><span data-stu-id="08723-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="08723-117">Dynamisch zorgt voor de configuratie van de **knooppunt** blokken aan de hand van de verzameling van knooppunten van krijgt `$MyData` (met name `$AllNodes`) en filters die verzameling op basis van de `Role` eigenschap...</span><span class="sxs-lookup"><span data-stu-id="08723-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="08723-118">Met behulp van de configuratiegegevens voor het definiëren van ontwikkeling en productie-omgevingen</span><span class="sxs-lookup"><span data-stu-id="08723-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="08723-119">Bekijk een compleet voorbeeld die gebruikmaakt van een configuratie voor één voor het instellen van zowel ontwikkeling als productie-omgevingen van een website.</span><span class="sxs-lookup"><span data-stu-id="08723-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="08723-120">Zowel IIS en SQL Server in de ontwikkelomgeving zijn geïnstalleerd op een afzonderlijke knooppunten.</span><span class="sxs-lookup"><span data-stu-id="08723-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="08723-121">In de productieomgeving, zijn IIS en SQL Server geïnstalleerd op afzonderlijke knooppunten.</span><span class="sxs-lookup"><span data-stu-id="08723-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="08723-122">Gebruiken we een bestand met configuratiegegevens .psd1 om op te geven van de gegevens voor de twee verschillende omgevingen.</span><span class="sxs-lookup"><span data-stu-id="08723-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="08723-123">Bestand met configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="08723-123">Configuration data file</span></span>

<span data-ttu-id="08723-124">Definiëren we de ontwikkeling en productie-omgeving-gegevens in een bestand met de naam `DevProdEnvData.psd1` als volgt:</span><span class="sxs-lookup"><span data-stu-id="08723-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="08723-125">Configuratie van scriptbestand</span><span class="sxs-lookup"><span data-stu-id="08723-125">Configuration script file</span></span>

<span data-ttu-id="08723-126">Nu in de configuratie die is gedefinieerd in een `.ps1` bestand filteren we de knooppunten die we hebben gedefinieerd in `DevProdEnvData.psd1` door hun rol (`MSSQL`, `Dev`, of beide), en deze dienovereenkomstig configureren.</span><span class="sxs-lookup"><span data-stu-id="08723-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="08723-127">De ontwikkelomgeving heeft de SQL-Server en IIS op één knooppunt, terwijl de productie-omgeving ze op twee verschillende knooppunten heeft.</span><span class="sxs-lookup"><span data-stu-id="08723-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="08723-128">De site-inhoud is ook verschillend zijn, zoals opgegeven door de `SiteContents` eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="08723-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="08723-129">Aan het einde van het configuratiescript, noemen we de configuratie (dit compileren in een MOF-document), waarbij `DevProdEnvData.psd1` als de `$ConfigurationData` parameter.</span><span class="sxs-lookup"><span data-stu-id="08723-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="08723-130">**Opmerking:** Deze configuratie moet de modules `xSqlPs` en `xWebAdministration` worden geïnstalleerd op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="08723-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="08723-131">Laten we de configuratie wordt gedefinieerd in een bestand met de naam `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="08723-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

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

<span data-ttu-id="08723-132">Wanneer u deze configuratie uitvoert, drie MOF-bestanden worden gemaakt (één voor elke vermelding in met de naam de **AllNodes** matrix):</span><span class="sxs-lookup"><span data-stu-id="08723-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="08723-133">Met behulp van niet-knooppuntgegevens</span><span class="sxs-lookup"><span data-stu-id="08723-133">Using non-node data</span></span>

<span data-ttu-id="08723-134">U kunt aanvullende sleutels toevoegen de **ConfigurationData** hashtabel voor gegevens die niet specifiek zijn voor een knooppunt.</span><span class="sxs-lookup"><span data-stu-id="08723-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="08723-135">De volgende configuratie zorgt ervoor dat de aanwezigheid van twee websites.</span><span class="sxs-lookup"><span data-stu-id="08723-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="08723-136">Gegevens voor elke website zijn gedefinieerd in de **AllNodes** matrix.</span><span class="sxs-lookup"><span data-stu-id="08723-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="08723-137">Het bestand `Config.xml` wordt gebruikt voor beide websites, zodat we de gegevens in een extra sleutel met de naam definiëren `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="08723-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="08723-138">Houd er rekening mee dat u zoveel extra sleutels als u wilt en u kunt deze de naam elke gewenste kan hebben.</span><span class="sxs-lookup"><span data-stu-id="08723-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="08723-139">`NonNodeData` is niet een gereserveerd woord is net wat we besloten om de naam van de extra sleutel.</span><span class="sxs-lookup"><span data-stu-id="08723-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="08723-140">U toegang tot aanvullende sleutels met behulp van de speciale variabele **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="08723-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="08723-141">In dit voorbeeld `ConfigFileContents` wordt geopend met de regel:</span><span class="sxs-lookup"><span data-stu-id="08723-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="08723-142">in de `File` resource blokkeren.</span><span class="sxs-lookup"><span data-stu-id="08723-142">in the `File` resource block.</span></span>


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


## <a name="see-also"></a><span data-ttu-id="08723-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="08723-143">See Also</span></span>
- [<span data-ttu-id="08723-144">Met behulp van configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="08723-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="08723-145">Referentieopties in de configuratiegegevens</span><span class="sxs-lookup"><span data-stu-id="08723-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="08723-146">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="08723-146">DSC Configurations</span></span>](configurations.md)
