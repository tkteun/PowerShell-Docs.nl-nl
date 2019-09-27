---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Configuratie- en omgevingsgegevens scheiden
ms.openlocfilehash: b16243fc9096f786a25ed20868e94a3aa85e403e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323250"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="30a9f-103">Configuratie- en omgevingsgegevens scheiden</span><span class="sxs-lookup"><span data-stu-id="30a9f-103">Separating configuration and environment data</span></span>

><span data-ttu-id="30a9f-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="30a9f-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="30a9f-105">Het kan handig zijn om de gegevens die in een DSC-configuratie worden gebruikt, te scheiden van de configuratie zelf met behulp van configuratie gegevens.</span><span class="sxs-lookup"><span data-stu-id="30a9f-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="30a9f-106">Als u dit doet, kunt u één configuratie voor meerdere omgevingen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="30a9f-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="30a9f-107">Als u bijvoorbeeld een toepassing ontwikkelt, kunt u een configuratie gebruiken voor zowel ontwikkel-als productie omgevingen en configuratie gegevens gebruiken om gegevens op te geven voor elke omgeving.</span><span class="sxs-lookup"><span data-stu-id="30a9f-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="30a9f-108">Wat zijn configuratie gegevens?</span><span class="sxs-lookup"><span data-stu-id="30a9f-108">What is configuration data?</span></span>

<span data-ttu-id="30a9f-109">Configuratie gegevens zijn gegevens die zijn gedefinieerd in een hashtabel en door gegeven aan een DSC-configuratie wanneer u die configuratie compileert.</span><span class="sxs-lookup"><span data-stu-id="30a9f-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="30a9f-110">Zie [configuratie gegevens gebruiken](configData.md)voor een gedetailleerde beschrijving van de **ConfigurationData** hashtabel.</span><span class="sxs-lookup"><span data-stu-id="30a9f-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="30a9f-111">Een eenvoudig voor beeld</span><span class="sxs-lookup"><span data-stu-id="30a9f-111">A simple example</span></span>

<span data-ttu-id="30a9f-112">Laten we eens kijken naar een zeer eenvoudig voor beeld om te zien hoe dit werkt.</span><span class="sxs-lookup"><span data-stu-id="30a9f-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="30a9f-113">Er wordt één configuratie gemaakt die ervoor zorgt dat **IIS** op sommige knoop punten aanwezig is en dat **Hyper-V** aanwezig is voor anderen:</span><span class="sxs-lookup"><span data-stu-id="30a9f-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

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

<span data-ttu-id="30a9f-114">De laatste regel in dit script compileert de configuratie, waarbij `$MyData` de para meter value **ConfigurationData** wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="30a9f-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="30a9f-115">Het resultaat is dat er twee MOF-bestanden worden gemaakt:</span><span class="sxs-lookup"><span data-stu-id="30a9f-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="30a9f-116">`$MyData`Hiermee geeft u twee verschillende knoop punten, elk `NodeName` met `Role`een eigen en.</span><span class="sxs-lookup"><span data-stu-id="30a9f-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="30a9f-117">Met de configuratie worden dynamische **knooppunt** blokken gemaakt door de verzameling knoop punten te nemen `$MyData` die worden opgehaald `$AllNodes`(met name) en de verzameling `Role` wordt gefilterd op basis van de eigenschap.</span><span class="sxs-lookup"><span data-stu-id="30a9f-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="30a9f-118">Configuratie gegevens gebruiken voor het definiëren van ontwikkel-en productie omgevingen</span><span class="sxs-lookup"><span data-stu-id="30a9f-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="30a9f-119">Laten we eens kijken naar een volledig voor beeld dat één configuratie gebruikt voor het instellen van de ontwikkel-en productie omgeving van een website.</span><span class="sxs-lookup"><span data-stu-id="30a9f-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="30a9f-120">In de ontwikkel omgeving worden zowel IIS als SQL Server geïnstalleerd op één knoop punt.</span><span class="sxs-lookup"><span data-stu-id="30a9f-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="30a9f-121">In de productie omgeving worden IIS en SQL Server op afzonderlijke knoop punten geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="30a9f-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="30a9f-122">We gebruiken een configuratie gegevens. psd1-bestand om de gegevens voor de twee verschillende omgevingen op te geven.</span><span class="sxs-lookup"><span data-stu-id="30a9f-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="30a9f-123">Bestand met configuratie gegevens</span><span class="sxs-lookup"><span data-stu-id="30a9f-123">Configuration data file</span></span>

<span data-ttu-id="30a9f-124">De gegevens voor de ontwikkelings-en productie omgeving worden gedefinieerd in `DevProdEnvData.psd1` een bestand met de volgende naam:</span><span class="sxs-lookup"><span data-stu-id="30a9f-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

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

### <a name="configuration-script-file"></a><span data-ttu-id="30a9f-125">Configuratie script bestand</span><span class="sxs-lookup"><span data-stu-id="30a9f-125">Configuration script file</span></span>

<span data-ttu-id="30a9f-126">Nu worden in de configuratie, `.ps1` die in een bestand is gedefinieerd, de knoop punten gefilterd die we in `DevProdEnvData.psd1` hun rol hebben `Dev`gedefinieerd (`MSSQL`, of beide) en worden ze dienovereenkomstig geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="30a9f-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="30a9f-127">De ontwikkel omgeving heeft zowel de SQL Server als IIS op één knoop punt, terwijl de productie omgeving ze op twee verschillende knoop punten heeft.</span><span class="sxs-lookup"><span data-stu-id="30a9f-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="30a9f-128">De site-inhoud is ook anders, zoals opgegeven door `SiteContents` de eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="30a9f-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="30a9f-129">Aan het einde van het configuratie script noemen we de configuratie (Compileer deze in een MOF-document), waarbij `DevProdEnvData.psd1` de `$ConfigurationData` para meter wordt door gegeven.</span><span class="sxs-lookup"><span data-stu-id="30a9f-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="30a9f-130">**Opmerking:** Voor deze configuratie moeten de `xSqlPs` modules `xWebAdministration` en worden geïnstalleerd op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="30a9f-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="30a9f-131">Laten we de configuratie definiëren in een bestand met `MyWebApp.ps1`de naam:</span><span class="sxs-lookup"><span data-stu-id="30a9f-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

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

<span data-ttu-id="30a9f-132">Wanneer u deze configuratie uitvoert, worden er drie MOF-bestanden gemaakt (één voor elke benoemde vermelding in de **AllNodes** -matrix):</span><span class="sxs-lookup"><span data-stu-id="30a9f-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="30a9f-133">Niet-knooppunt gegevens gebruiken</span><span class="sxs-lookup"><span data-stu-id="30a9f-133">Using non-node data</span></span>

<span data-ttu-id="30a9f-134">U kunt extra sleutels toevoegen aan de **ConfigurationData** hashtabel voor gegevens die niet specifiek voor een knoop punt zijn.</span><span class="sxs-lookup"><span data-stu-id="30a9f-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="30a9f-135">De volgende configuratie zorgt ervoor dat er twee websites aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="30a9f-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="30a9f-136">De gegevens voor elke website worden gedefinieerd in de **AllNodes** -matrix.</span><span class="sxs-lookup"><span data-stu-id="30a9f-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="30a9f-137">Het bestand `Config.xml` wordt gebruikt voor beide websites, dus we definiëren het in een extra sleutel met de naam `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="30a9f-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="30a9f-138">Houd er rekening mee dat u zoveel extra sleutels kunt hebben als u wilt, en u kunt ze elke gewenste naam geven.</span><span class="sxs-lookup"><span data-stu-id="30a9f-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="30a9f-139">`NonNodeData`is geen gereserveerd woord. het is precies wat we hebben besloten om de extra sleutel een naam te bieden.</span><span class="sxs-lookup"><span data-stu-id="30a9f-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="30a9f-140">U hebt toegang tot extra sleutels met behulp van de speciale variabele **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="30a9f-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="30a9f-141">In dit voor beeld `ConfigFileContents` wordt toegang verkregen met de regel:</span><span class="sxs-lookup"><span data-stu-id="30a9f-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="30a9f-142">in het `File` resource blok.</span><span class="sxs-lookup"><span data-stu-id="30a9f-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
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
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="30a9f-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="30a9f-143">See Also</span></span>
- [<span data-ttu-id="30a9f-144">Configuratie gegevens gebruiken</span><span class="sxs-lookup"><span data-stu-id="30a9f-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="30a9f-145">Referenties opties in configuratie gegevens</span><span class="sxs-lookup"><span data-stu-id="30a9f-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="30a9f-146">DSC-configuraties</span><span class="sxs-lookup"><span data-stu-id="30a9f-146">DSC Configurations</span></span>](configurations.md)
