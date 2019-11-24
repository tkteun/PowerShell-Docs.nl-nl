---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: 'Quick Start: een website maken met DSC'
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942725"
---
> <span data-ttu-id="0e357-103">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="0e357-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="0e357-104">Quick Start: een website maken met DSC</span><span class="sxs-lookup"><span data-stu-id="0e357-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="0e357-105">In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde.</span><span class="sxs-lookup"><span data-stu-id="0e357-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="0e357-106">In het voor beeld dat we gebruiken, zorgt u ervoor dat de functie `Web-Server` (IIS) is ingeschakeld op een server en dat de inhoud voor een eenvoudige website ' Hallo wereld ' aanwezig is in de `inetpub\wwwroot` map van die server.</span><span class="sxs-lookup"><span data-stu-id="0e357-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="0e357-107">Voor een overzicht van wat DSC is en hoe het werkt, raadpleegt [u overzicht van desired state Configuration voor besluit vormers](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="0e357-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0e357-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0e357-108">Requirements</span></span>

<span data-ttu-id="0e357-109">Als u dit voor beeld wilt uitvoeren, hebt u een computer met Windows Server 2012 of hoger en Power Shell 4,0 of hoger nodig.</span><span class="sxs-lookup"><span data-stu-id="0e357-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="0e357-110">Het bestand index. htm schrijven en plaatsen</span><span class="sxs-lookup"><span data-stu-id="0e357-110">Write and place the index.htm file</span></span>

<span data-ttu-id="0e357-111">Eerst maken we het HTML-bestand dat we als website-inhoud gaan gebruiken.</span><span class="sxs-lookup"><span data-stu-id="0e357-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="0e357-112">Maak in de hoofdmap een map met de naam `test`.</span><span class="sxs-lookup"><span data-stu-id="0e357-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="0e357-113">Typ de volgende tekst in een tekst editor:</span><span class="sxs-lookup"><span data-stu-id="0e357-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="0e357-114">Sla dit op als `index.htm` in de `test` map die u eerder hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="0e357-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="0e357-115">De configuratie schrijven</span><span class="sxs-lookup"><span data-stu-id="0e357-115">Write the configuration</span></span>

<span data-ttu-id="0e357-116">Een [DSC-configuratie](../configurations/configurations.md) is een speciale Power shell-functie die definieert hoe u een of meer doel computers (knoop punten) wilt configureren.</span><span class="sxs-lookup"><span data-stu-id="0e357-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="0e357-117">Typ het volgende in het Power shell-ISE:</span><span class="sxs-lookup"><span data-stu-id="0e357-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="0e357-118">Sla het bestand op als `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="0e357-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="0e357-119">U ziet dat deze eruitziet als een Power shell-functie, met toevoeging van de trefwoord **configuratie** die wordt gebruikt voor de naam van de functie.</span><span class="sxs-lookup"><span data-stu-id="0e357-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="0e357-120">Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. in dit geval `localhost`.</span><span class="sxs-lookup"><span data-stu-id="0e357-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="0e357-121">De configuratie roept twee [resources](../resources/resources.md), **WindowsFeature** en **File**aan.</span><span class="sxs-lookup"><span data-stu-id="0e357-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="0e357-122">Resources maken het werk om ervoor te zorgen dat het doel knooppunt zich in de status bevindt die door de configuratie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="0e357-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="0e357-123">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="0e357-123">Compile the configuration</span></span>

<span data-ttu-id="0e357-124">Een DSC-configuratie die wordt toegepast op een knoop punt, moet eerst worden gecompileerd in een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="0e357-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="0e357-125">Hiervoor voert u de configuratie uit, zoals een functie.</span><span class="sxs-lookup"><span data-stu-id="0e357-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="0e357-126">In een Power shell-console gaat u naar de map waar u de configuratie hebt opgeslagen en voert u de volgende opdrachten uit om de configuratie in een MOF-bestand te compileren:</span><span class="sxs-lookup"><span data-stu-id="0e357-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="0e357-127">Hiermee wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="0e357-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="0e357-128">De eerste regel maakt de configuratie functie beschikbaar in de-console.</span><span class="sxs-lookup"><span data-stu-id="0e357-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="0e357-129">De tweede regel voert de configuratie uit.</span><span class="sxs-lookup"><span data-stu-id="0e357-129">The second line runs the configuration.</span></span>
<span data-ttu-id="0e357-130">Het resultaat is dat een nieuwe map met de naam `WebsiteTest` wordt gemaakt als een submap van de huidige map.</span><span class="sxs-lookup"><span data-stu-id="0e357-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="0e357-131">De map `WebsiteTest` bevat een bestand met de naam `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="0e357-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="0e357-132">Dit bestand kan vervolgens worden toegepast op het doel knooppunt.</span><span class="sxs-lookup"><span data-stu-id="0e357-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="0e357-133">De configuratie Toep assen</span><span class="sxs-lookup"><span data-stu-id="0e357-133">Apply the configuration</span></span>

<span data-ttu-id="0e357-134">Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="0e357-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="0e357-135">De cmdlet `Start-DscConfiguration` vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="0e357-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="0e357-136">De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="0e357-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="0e357-137">In een Power shell-console gaat u naar de map waar u de configuratie hebt opgeslagen en voert u de volgende opdracht uit:</span><span class="sxs-lookup"><span data-stu-id="0e357-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="0e357-138">De configuratie testen</span><span class="sxs-lookup"><span data-stu-id="0e357-138">Test the configuration</span></span>

<span data-ttu-id="0e357-139">U kunt de cmdlet [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) aanroepen om te zien of de configuratie is geslaagd.</span><span class="sxs-lookup"><span data-stu-id="0e357-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="0e357-140">U kunt de resultaten ook rechtstreeks testen, in dit geval door te bladeren naar `http://localhost/` in een webbrowser.</span><span class="sxs-lookup"><span data-stu-id="0e357-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="0e357-141">U ziet de HTML-pagina ' Hallo wereld ' die u hebt gemaakt als de eerste stap in dit voor beeld.</span><span class="sxs-lookup"><span data-stu-id="0e357-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e357-142">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="0e357-142">Next steps</span></span>

- <span data-ttu-id="0e357-143">Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="0e357-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="0e357-144">Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="0e357-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="0e357-145">DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="0e357-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
