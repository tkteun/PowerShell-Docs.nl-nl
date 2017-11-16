---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Desired State Configuration snel starten
ms.openlocfilehash: 295a78f3fd85464239d51d7be0defa04d2344689
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2017
---
> <span data-ttu-id="4d259-103">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4d259-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="4d259-104">Desired State Configuration snel starten</span><span class="sxs-lookup"><span data-stu-id="4d259-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="4d259-105">In deze oefening helpt bij het maken en toepassen van een configuratie Desired State Configuration (DSC) van begin tot eind.</span><span class="sxs-lookup"><span data-stu-id="4d259-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="4d259-106">In het voorbeeld we gebruiken zorgt ervoor dat een server heeft de `Web-Server` (IIS)-functie ingeschakeld en de inhoud voor een eenvoudige 'Hallo wereld'-website is aanwezig in de `intepub\wwwroot` map van die server.</span><span class="sxs-lookup"><span data-stu-id="4d259-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="4d259-107">Zie voor een overzicht van DSC en hoe het werkt [Desired Configuration overzicht voor besluitvormers](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="4d259-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4d259-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4d259-108">Requirements</span></span>

<span data-ttu-id="4d259-109">U voert dit voorbeeld, moet u een computer met WindowsServer 2012 of later en PowerShell 4.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="4d259-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="4d259-110">Schrijven en plaats het bestand index.htm</span><span class="sxs-lookup"><span data-stu-id="4d259-110">Write and place the index.htm file</span></span>

<span data-ttu-id="4d259-111">Eerst maakt de HTML-bestand dat wordt gebruikt als de inhoud van de website.</span><span class="sxs-lookup"><span data-stu-id="4d259-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="4d259-112">Maak een map met de naam in de hoofdmap, `test`.</span><span class="sxs-lookup"><span data-stu-id="4d259-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="4d259-113">Typ de volgende tekst in een teksteditor:</span><span class="sxs-lookup"><span data-stu-id="4d259-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="4d259-114">Opslaan als `index.htm` in de `test` map die u eerder hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4d259-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span> 

## <a name="write-the-configuration"></a><span data-ttu-id="4d259-115">Schrijven van de configuratie</span><span class="sxs-lookup"><span data-stu-id="4d259-115">Write the configuration</span></span>

<span data-ttu-id="4d259-116">Een [DSC-configuratie](configurations.md) is een speciale PowerShell-functie die hoe u aangeeft een of meer doelcomputers (knooppunten) configureren.</span><span class="sxs-lookup"><span data-stu-id="4d259-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="4d259-117">In de PowerShell ISE, typ het volgende:</span><span class="sxs-lookup"><span data-stu-id="4d259-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="4d259-118">Sla het bestand als `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="4d259-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="4d259-119">U kunt zien dat het lijkt erop dat een functie PowerShell met de toevoeging van het sleutelwoord **configuratie** gebruikt vóór de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="4d259-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="4d259-120">De **knooppunt** blok Hiermee geeft u het doelknooppunt te configureren in dit geval `localhost`.</span><span class="sxs-lookup"><span data-stu-id="4d259-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="4d259-121">De configuratie van de twee roept [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) en [bestand](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="4d259-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="4d259-122">Resources doen het werk om ervoor te zorgen dat het doelknooppunt de status is gedefinieerd door de configuratie heeft.</span><span class="sxs-lookup"><span data-stu-id="4d259-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="4d259-123">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="4d259-123">Compile the configuration</span></span>

<span data-ttu-id="4d259-124">Voor een DSC-configuratie op een knooppunt moet worden toegepast, moet deze eerst worden gecompileerd naar een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="4d259-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="4d259-125">Om dit te doen, moet u de configuratie zoals een functie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="4d259-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="4d259-126">Navigeer naar dezelfde map waarin u de configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdrachten voor het compileren van de configuratie naar een MOF-bestand:</span><span class="sxs-lookup"><span data-stu-id="4d259-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="4d259-127">Hiermee wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="4d259-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="4d259-128">De eerste regel wordt de configuratie-functie beschikbaar in de console.</span><span class="sxs-lookup"><span data-stu-id="4d259-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="4d259-129">De tweede regel wordt uitgevoerd voor de configuratie.</span><span class="sxs-lookup"><span data-stu-id="4d259-129">The second line runs the configuration.</span></span>
<span data-ttu-id="4d259-130">Het resultaat is dat er een nieuwe map met de naam `WebsiteTest` gemaakt als een submap van de huidige map.</span><span class="sxs-lookup"><span data-stu-id="4d259-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="4d259-131">De `WebsiteTest` map bevat een bestand met de naam `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="4d259-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="4d259-132">Het is dit bestand die vervolgens kan worden toegepast op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="4d259-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="4d259-133">De configuratie toepassen</span><span class="sxs-lookup"><span data-stu-id="4d259-133">Apply the configuration</span></span>

<span data-ttu-id="4d259-134">Nu dat u de gecompileerde MOF hebt, kunt u de configuratie toepassen op het doelknooppunt (in dit geval de lokale computer) door het aanroepen van de [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d259-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="4d259-135">De `Start-DscConfiguration` cmdlet vertelt de [lokale Configuration Manager (LCM)](metaConfig.md), dit is de engine van DSC toepassen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="4d259-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="4d259-136">De LCM komt het werk van het aanroepen van de DSC-resources als de configuratie wilt toepassen.</span><span class="sxs-lookup"><span data-stu-id="4d259-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="4d259-137">Navigeer naar dezelfde map waarin u de configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdracht:</span><span class="sxs-lookup"><span data-stu-id="4d259-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="4d259-138">Test de configuratie</span><span class="sxs-lookup"><span data-stu-id="4d259-138">Test the configuration</span></span>

<span data-ttu-id="4d259-139">U kunt aanroepen de [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet om te controleren of de configuratie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="4d259-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span> 

<span data-ttu-id="4d259-140">U kunt ook de resultaten testen rechtstreeks in dit geval door te bladeren naar `http://localhost/` in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="4d259-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="4d259-141">Als de eerste stap in dit voorbeeld ziet u de 'Hallo wereld' HTML-pagina die u hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4d259-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4d259-142">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="4d259-142">Next steps</span></span>

- <span data-ttu-id="4d259-143">Meer informatie over DSC-configuraties op [DSC-configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4d259-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="4d259-144">Zie wat DSC-resources beschikbaar zijn en het maken van aangepaste DSC-resources op [DSC-resources](resources.md).</span><span class="sxs-lookup"><span data-stu-id="4d259-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="4d259-145">DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="4d259-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>



