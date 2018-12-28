---
ms.date: 12/12/2018
keywords: DSC, powershell, configuratie, service, instellen
title: Schrijven en toepassen van een configuratie compileren
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403927"
---
> <span data-ttu-id="90dd8-103">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="90dd8-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="90dd8-104">Schrijven en toepassen van een configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="90dd8-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="90dd8-105">In deze oefening helpt bij het maken en toepassen van een Desired State Configuration (DSC)-configuratie van begin tot eind.</span><span class="sxs-lookup"><span data-stu-id="90dd8-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="90dd8-106">In het volgende voorbeeld leert u hoe u kunt schrijven en een zeer eenvoudige configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="90dd8-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="90dd8-107">De configuratie zorgt ervoor dat een 'HelloWorld.txt'-bestand bestaat op uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="90dd8-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="90dd8-108">Als u het bestand verwijdert, DSC wordt het opnieuw maken de volgende keer die wordt bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="90dd8-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="90dd8-109">Zie voor een overzicht van wat DSC is en hoe het werkt, [overzicht van Desired State Configuration voor ontwikkelaars](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="90dd8-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="90dd8-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="90dd8-110">Requirements</span></span>

<span data-ttu-id="90dd8-111">Als u wilt uitvoeren in het volgende voorbeeld, moet u een computer met PowerShell 4.0 of hoger.</span><span class="sxs-lookup"><span data-stu-id="90dd8-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="90dd8-112">Schrijven van de configuratie</span><span class="sxs-lookup"><span data-stu-id="90dd8-112">Write the configuration</span></span>

<span data-ttu-id="90dd8-113">Een DSC [configuratie](configurations.md) is een speciale PowerShell-functie die wordt gedefinieerd hoe u wilt configureren van een of meer doelcomputers (knooppunten).</span><span class="sxs-lookup"><span data-stu-id="90dd8-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="90dd8-114">In de PowerShell ISE, of een andere editor PowerShell, typ het volgende:</span><span class="sxs-lookup"><span data-stu-id="90dd8-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="90dd8-115">Sla het bestand als 'HelloWorld.ps1'.</span><span class="sxs-lookup"><span data-stu-id="90dd8-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="90dd8-116">Voor het definiëren van een configuratie is vergelijkbaar met het definiëren van een functie.</span><span class="sxs-lookup"><span data-stu-id="90dd8-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="90dd8-117">De **knooppunt** blok Hiermee geeft u het doelknooppunt moet worden geconfigureerd en in dit geval `localhost`.</span><span class="sxs-lookup"><span data-stu-id="90dd8-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="90dd8-118">De configuratie van de roept een [resources](../resources/resources.md), wordt de `File` resource.</span><span class="sxs-lookup"><span data-stu-id="90dd8-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="90dd8-119">Resources doen het werk om ervoor te zorgen dat het doelknooppunt gedefinieerd door de configuratie van de status wordt.</span><span class="sxs-lookup"><span data-stu-id="90dd8-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="90dd8-120">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="90dd8-120">Compile the configuration</span></span>

<span data-ttu-id="90dd8-121">Voor een DSC-configuratie moet worden toegepast op een knooppunt, moet dit eerst worden gecompileerd naar een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="90dd8-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="90dd8-122">Uitvoeren van de configuratie, zoals een functie, wordt één ".mof" bestand gecompileerd voor elk knooppunt dat is gedefinieerd door de `Node` blokkeren.</span><span class="sxs-lookup"><span data-stu-id="90dd8-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="90dd8-123">Als u wilt uitvoeren van de configuratie, moet u *stip bron* uw script 'HelloWorld.ps1' in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="90dd8-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="90dd8-124">Zie voor meer informatie, [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="90dd8-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<span data-ttu-id="90dd8-125">*Punt bron* uw script 'HelloWorld.ps1' door te typen in het pad waar u deze nadat opgeslagen de `. ` (punt, spatie).</span><span class="sxs-lookup"><span data-stu-id="90dd8-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="90dd8-126">Vervolgens kunt u uw configuratie uitvoeren door deze als een functie aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="90dd8-126">You may then, run your configuration by calling it like a Function.</span></span>

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

<span data-ttu-id="90dd8-127">Hiermee wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="90dd8-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="90dd8-128">De configuratie toepassen</span><span class="sxs-lookup"><span data-stu-id="90dd8-128">Apply the configuration</span></span>

<span data-ttu-id="90dd8-129">Nu dat u het gecompileerde MOF hebt, kunt u de configuratie toepassen op het doelknooppunt (in dit geval de lokale computer) door het aanroepen van de [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90dd8-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="90dd8-130">De `Start-DscConfiguration` cmdlet geeft de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de DSC, om toe te passen van de configuratie-engine.</span><span class="sxs-lookup"><span data-stu-id="90dd8-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="90dd8-131">De LCM komt het werk van het aanroepen van de DSC-resources voor het toepassen van de configuratie.</span><span class="sxs-lookup"><span data-stu-id="90dd8-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="90dd8-132">De onderstaande code gebruiken om uit te voeren de `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90dd8-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="90dd8-133">Geef het pad waar uw "localhost.mof" is opgeslagen op de `-Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="90dd8-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="90dd8-134">De `Start-DSCConfiguration` cmdlet gezocht in de map die is opgegeven voor een '\<computername\>.mof "bestanden.</span><span class="sxs-lookup"><span data-stu-id="90dd8-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="90dd8-135">De `Start-DSCConfiguration` cmdlet probeert toe te passen van elk ".mof" bestand gevonden op de computernaam die is opgegeven door de bestandsnaam ("localhost", "server01", "dc-02", enzovoort).</span><span class="sxs-lookup"><span data-stu-id="90dd8-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="90dd8-136">Als de `-Wait` parameter niet wordt opgegeven, `Start-DSCConfiguration` maakt u een achtergrondtaak als de bewerking wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="90dd8-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="90dd8-137">Op te geven de `-Verbose` parameter kunt u bekijken de **uitgebreid** uitvoer van de bewerking.</span><span class="sxs-lookup"><span data-stu-id="90dd8-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="90dd8-138">`-Wait`, en `-Verbose` beide parameters zijn optioneel.</span><span class="sxs-lookup"><span data-stu-id="90dd8-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="90dd8-139">De configuratie testen</span><span class="sxs-lookup"><span data-stu-id="90dd8-139">Test the configuration</span></span>

<span data-ttu-id="90dd8-140">Zodra de `Start-DSCConfiguration` cmdlet is voltooid, ziet u een bestand 'HelloWorld.txt' in de opgegeven locatie.</span><span class="sxs-lookup"><span data-stu-id="90dd8-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="90dd8-141">U kunt controleren of de inhoud met de [Get-inhoud](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="90dd8-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="90dd8-142">U kunt ook *testen* de huidige status via [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="90dd8-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="90dd8-143">De uitvoer moet 'True' als het knooppunt momenteel compatibel is met de toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="90dd8-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="90dd8-144">De configuratie toepassen opnieuw</span><span class="sxs-lookup"><span data-stu-id="90dd8-144">Re-applying the configuration</span></span>

<span data-ttu-id="90dd8-145">Als u wilt zien van uw configuratie opnieuw toegepast, kunt u het tekstbestand dat is gemaakt door uw configuratie verwijderen.</span><span class="sxs-lookup"><span data-stu-id="90dd8-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="90dd8-146">Gebruik de `Start-DSCConfiguration` cmdlet met de `-UseExisting` parameter.</span><span class="sxs-lookup"><span data-stu-id="90dd8-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="90dd8-147">De `-UseExisting` parameter geeft de opdracht `Start-DSCConfiguration` om toe te passen opnieuw het bestand 'current.mof', die het meest recent zijn vertegenwoordigt configuratie toegepast.</span><span class="sxs-lookup"><span data-stu-id="90dd8-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="90dd8-148">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="90dd8-148">Next steps</span></span>

- <span data-ttu-id="90dd8-149">Meer informatie over DSC-configuraties op [DSC-configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="90dd8-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="90dd8-150">Zie welke DSC-resources beschikbaar zijn en over het maken van aangepaste DSC-resources op [DSC-resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="90dd8-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="90dd8-151">DSC-configuraties en resources in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="90dd8-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
