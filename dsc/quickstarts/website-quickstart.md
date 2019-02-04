---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: 'Snelstart: een website maken met DSC'
ms.openlocfilehash: c62e2d8af46bf74c4dd13069ddff6cc39763a209
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684253"
---
> <span data-ttu-id="1abaf-103">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1abaf-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="1abaf-104">Snelstart: een website maken met DSC</span><span class="sxs-lookup"><span data-stu-id="1abaf-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="1abaf-105">In deze oefening helpt bij het maken en toepassen van een Desired State Configuration (DSC)-configuratie van begin tot eind.</span><span class="sxs-lookup"><span data-stu-id="1abaf-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="1abaf-106">Het voorbeeld we gebruiken zorgt ervoor dat een server heeft de `Web-Server` (IIS)-functie ingeschakeld en dat de inhoud voor een eenvoudige 'Hallo wereld'-website is aanwezig in de `intepub\wwwroot` map van die server.</span><span class="sxs-lookup"><span data-stu-id="1abaf-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="1abaf-107">Zie voor een overzicht van wat DSC is en hoe het werkt, [overzicht van Desired State Configuration voor besluitvormers](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="1abaf-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1abaf-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1abaf-108">Requirements</span></span>

<span data-ttu-id="1abaf-109">Als u wilt uitvoeren in het volgende voorbeeld, moet u een computer met WindowsServer 2012 of later en PowerShell 4.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="1abaf-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="1abaf-110">Schrijven en plaats het bestand index.htm</span><span class="sxs-lookup"><span data-stu-id="1abaf-110">Write and place the index.htm file</span></span>

<span data-ttu-id="1abaf-111">Eerst gaan we de HTML-bestand dat wordt gebruikt als de website-inhoud maken.</span><span class="sxs-lookup"><span data-stu-id="1abaf-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="1abaf-112">Maak een map met de naam in de hoofdmap, `test`.</span><span class="sxs-lookup"><span data-stu-id="1abaf-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="1abaf-113">In een teksteditor, typt u de volgende tekst:</span><span class="sxs-lookup"><span data-stu-id="1abaf-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="1abaf-114">Opslaan als `index.htm` in de `test` map die u eerder hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1abaf-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="1abaf-115">Schrijven van de configuratie</span><span class="sxs-lookup"><span data-stu-id="1abaf-115">Write the configuration</span></span>

<span data-ttu-id="1abaf-116">Een [DSC-configuratie](../configurations/configurations.md) is een speciale PowerShell-functie die wordt gedefinieerd hoe u wilt configureren van een of meer doelcomputers (knooppunten).</span><span class="sxs-lookup"><span data-stu-id="1abaf-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="1abaf-117">In de PowerShell ISE, typ het volgende:</span><span class="sxs-lookup"><span data-stu-id="1abaf-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="1abaf-118">Sla het bestand op als `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="1abaf-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="1abaf-119">U kunt zien dat het ziet als een PowerShell-functie met de toevoeging van het sleutelwoord eruit **configuratie** gebruikt vóór de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="1abaf-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="1abaf-120">De **knooppunt** blok Hiermee geeft u het doelknooppunt moet worden geconfigureerd en in dit geval `localhost`.</span><span class="sxs-lookup"><span data-stu-id="1abaf-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="1abaf-121">De configuratie van de twee roept [resources](../resources/resources.md), **WindowsFeature** en **bestand**.</span><span class="sxs-lookup"><span data-stu-id="1abaf-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="1abaf-122">Resources doen het werk om ervoor te zorgen dat het doelknooppunt gedefinieerd door de configuratie van de status wordt.</span><span class="sxs-lookup"><span data-stu-id="1abaf-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="1abaf-123">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="1abaf-123">Compile the configuration</span></span>

<span data-ttu-id="1abaf-124">Voor een DSC-configuratie moet worden toegepast op een knooppunt, moet dit eerst worden gecompileerd naar een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="1abaf-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="1abaf-125">Om dit te doen, moet u de configuratie, zoals een functie uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="1abaf-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="1abaf-126">Navigeer naar dezelfde map waar u uw configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdrachten voor het compileren van de configuratie naar een MOF-bestand:</span><span class="sxs-lookup"><span data-stu-id="1abaf-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="1abaf-127">Hiermee wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="1abaf-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="1abaf-128">De eerste regel wordt de configuratie-functie beschikbaar in de console.</span><span class="sxs-lookup"><span data-stu-id="1abaf-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="1abaf-129">De tweede regel wordt de configuratie uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="1abaf-129">The second line runs the configuration.</span></span>
<span data-ttu-id="1abaf-130">Het resultaat is dat een nieuwe map met de naam `WebsiteTest` als een submap van de huidige map wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1abaf-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="1abaf-131">De `WebsiteTest` map bevat een bestand met de naam `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="1abaf-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="1abaf-132">Het is in dit bestand die vervolgens kan worden toegepast op het doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="1abaf-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="1abaf-133">De configuratie toepassen</span><span class="sxs-lookup"><span data-stu-id="1abaf-133">Apply the configuration</span></span>

<span data-ttu-id="1abaf-134">Nu dat u het gecompileerde MOF hebt, kunt u de configuratie toepassen op het doelknooppunt (in dit geval de lokale computer) door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1abaf-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="1abaf-135">De `Start-DscConfiguration` cmdlet geeft de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), dit is de engine van DSC, om toe te passen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="1abaf-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="1abaf-136">De LCM komt het werk van het aanroepen van de DSC-resources voor het toepassen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="1abaf-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="1abaf-137">Navigeer naar dezelfde map waar u uw configuratie hebt opgeslagen in een PowerShell-console en voer de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="1abaf-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="1abaf-138">De configuratie testen</span><span class="sxs-lookup"><span data-stu-id="1abaf-138">Test the configuration</span></span>

<span data-ttu-id="1abaf-139">U kunt aanroepen de [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet om te controleren of de configuratie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="1abaf-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="1abaf-140">U kunt ook testen de resultaten rechtstreeks, in dit geval door te bladeren naar `http://localhost/` in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="1abaf-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="1abaf-141">Als de eerste stap in dit voorbeeld ziet u de "Hello World" HTML-pagina die u hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1abaf-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1abaf-142">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="1abaf-142">Next steps</span></span>

- <span data-ttu-id="1abaf-143">Meer informatie over DSC-configuraties op [DSC-configuraties](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="1abaf-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="1abaf-144">Zie welke DSC-resources beschikbaar zijn en over het maken van aangepaste DSC-resources op [DSC-resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="1abaf-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="1abaf-145">DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="1abaf-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
