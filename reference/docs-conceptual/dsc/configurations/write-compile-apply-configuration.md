---
ms.date: 06/22/2020
keywords: DSC, Power shell, configuratie, service, installatie
title: Een configuratie schrijven, compileren en toepassen
description: In deze oefening wordt het maken en Toep assen van een DSC-configuratie van begin tot eind door lopen. In het volgende voor beeld wordt uitgelegd hoe u een eenvoudige configuratie kunt schrijven en Toep assen
ms.openlocfilehash: f173fe0dc6cd73e2b49bb8c44a9ee1a53eab475f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645038"
---
# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="86813-105">Een configuratie schrijven, compileren en toepassen</span><span class="sxs-lookup"><span data-stu-id="86813-105">Write, Compile, and Apply a Configuration</span></span>

> <span data-ttu-id="86813-106">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="86813-106">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="86813-107">In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde.</span><span class="sxs-lookup"><span data-stu-id="86813-107">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span> <span data-ttu-id="86813-108">In het volgende voor beeld wordt uitgelegd hoe u een eenvoudige configuratie kunt schrijven en Toep assen.</span><span class="sxs-lookup"><span data-stu-id="86813-108">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="86813-109">De configuratie zorgt ervoor dat het bestand ' HelloWorld.txt ' bestaat op uw lokale computer.</span><span class="sxs-lookup"><span data-stu-id="86813-109">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span>
<span data-ttu-id="86813-110">Als u het bestand verwijdert, maakt DSC de volgende keer dat het wordt bijgewerkt opnieuw.</span><span class="sxs-lookup"><span data-stu-id="86813-110">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="86813-111">Voor een overzicht van wat DSC is en hoe het werkt, raadpleegt u [overzicht van desired state Configuration voor ontwikkel aars](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="86813-111">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="86813-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="86813-112">Requirements</span></span>

<span data-ttu-id="86813-113">Als u dit voor beeld wilt uitvoeren, hebt u een computer nodig waarop Power Shell 4,0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="86813-113">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="86813-114">De configuratie schrijven</span><span class="sxs-lookup"><span data-stu-id="86813-114">Write the configuration</span></span>

<span data-ttu-id="86813-115">Een DSC- [configuratie](configurations.md) is een speciale Power shell-functie die definieert hoe u een of meer doel computers (knoop punten) wilt configureren.</span><span class="sxs-lookup"><span data-stu-id="86813-115">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="86813-116">In Power shell ISE of een andere Power shell-editor typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="86813-116">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when
    # this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a
        # source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="86813-117">In meer geavanceerde scenario's waarin meerdere modules moeten worden geïmporteerd zodat u met een groot aantal DSC-resources in dezelfde configuratie kunt werken, moet u ervoor zorgen dat elke module op een aparte regel wordt geplaatst met `Import-DscResource` .</span><span class="sxs-lookup"><span data-stu-id="86813-117">In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span> <span data-ttu-id="86813-118">Dit is eenvoudiger te onderhouden in broncode beheer en is vereist bij het werken met DSC in azure-status configuratie.</span><span class="sxs-lookup"><span data-stu-id="86813-118">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="86813-119">Sla het bestand op als "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="86813-119">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="86813-120">Het definiëren van een configuratie is vergelijkbaar met het definiëren van een functie.</span><span class="sxs-lookup"><span data-stu-id="86813-120">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="86813-121">Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. in dit geval `localhost` .</span><span class="sxs-lookup"><span data-stu-id="86813-121">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="86813-122">De configuratie roept één [resources](../resources/resources.md)aan, de `File` resource.</span><span class="sxs-lookup"><span data-stu-id="86813-122">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="86813-123">Resources maken het werk om ervoor te zorgen dat het doel knooppunt zich in de status bevindt die door de configuratie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="86813-123">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="86813-124">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="86813-124">Compile the configuration</span></span>

<span data-ttu-id="86813-125">Een DSC-configuratie die wordt toegepast op een knoop punt, moet eerst worden gecompileerd in een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="86813-125">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span> <span data-ttu-id="86813-126">Het uitvoeren van de configuratie, zoals een functie, compileert één `.mof` bestand voor elk knoop punt dat door het blok wordt gedefinieerd `Node` .</span><span class="sxs-lookup"><span data-stu-id="86813-126">Running the configuration, like a function, will compile one `.mof` file for every Node defined by the `Node` block.</span></span> <span data-ttu-id="86813-127">Als u de configuratie wilt uitvoeren, moet u de _bron_ van uw `HelloWorld.ps1` script naar het huidige bereik gaan.</span><span class="sxs-lookup"><span data-stu-id="86813-127">In order to run the configuration, you need to _dot source_ your `HelloWorld.ps1` script into the current scope.</span></span> <span data-ttu-id="86813-128">Zie [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts#script-scope-and-dot-sourcing)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="86813-128">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="86813-129">_Punt_ de bron `HelloWorld.ps1` van uw script door het pad te typen waar u het hebt opgeslagen, na de `. ` (punt, spatie).</span><span class="sxs-lookup"><span data-stu-id="86813-129">_Dot source_ your `HelloWorld.ps1` script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="86813-130">U kunt vervolgens uw configuratie uitvoeren door deze als een functie aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="86813-130">You may then, run your configuration by calling it like a function.</span></span> <span data-ttu-id="86813-131">U kunt ook de configuratie functie onder aan het script aanroepen, zodat u niet hoeft te stip-bron.</span><span class="sxs-lookup"><span data-stu-id="86813-131">You could also invoke the configuration function at the bottom of the script so that you don't need to dot-source.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="86813-132">Hiermee wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="86813-132">This generates the following output:</span></span>

```Output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="86813-133">De configuratie toepassen</span><span class="sxs-lookup"><span data-stu-id="86813-133">Apply the configuration</span></span>

<span data-ttu-id="86813-134">Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="86813-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="86813-135">De `Start-DscConfiguration` cmdlet vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="86813-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span> <span data-ttu-id="86813-136">De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="86813-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="86813-137">Gebruik de onderstaande code om de cmdlet uit te voeren `Start-DSCConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="86813-137">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="86813-138">Geef het mappad op waar uw `localhost.mof` wordt opgeslagen in de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="86813-138">Specify the directory path where your `localhost.mof` is stored to the **Path** parameter.</span></span> <span data-ttu-id="86813-139">De `Start-DSCConfiguration` cmdlet zoekt naar de map die is opgegeven voor `<computername>.mof` bestanden.</span><span class="sxs-lookup"><span data-stu-id="86813-139">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any `<computername>.mof` files.</span></span> <span data-ttu-id="86813-140">De `Start-DSCConfiguration` cmdlet probeert elk `.mof` gevonden bestand toe te passen op het `computername` opgegeven door de bestands naam (' localhost ', ' Server01 ', ' DC-02 ', enzovoort).</span><span class="sxs-lookup"><span data-stu-id="86813-140">The `Start-DSCConfiguration` cmdlet attempts to apply each `.mof` file it finds to the `computername` specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="86813-141">Als de `-Wait` para meter niet wordt opgegeven, `Start-DSCConfiguration` maakt een achtergrond taak om de bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="86813-141">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="86813-142">Door de `-Verbose` para meter op te geven, kunt u de **uitgebreide** uitvoer van de bewerking bekijken.</span><span class="sxs-lookup"><span data-stu-id="86813-142">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="86813-143">`-Wait`en `-Verbose` zijn beide optionele para meters.</span><span class="sxs-lookup"><span data-stu-id="86813-143">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="86813-144">De configuratie testen</span><span class="sxs-lookup"><span data-stu-id="86813-144">Test the configuration</span></span>

<span data-ttu-id="86813-145">Zodra de `Start-DSCConfiguration` cmdlet is voltooid, ziet u een `HelloWorld.txt` bestand op de locatie die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="86813-145">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a `HelloWorld.txt` file in the location you specified.</span></span> <span data-ttu-id="86813-146">U kunt de inhoud controleren met de cmdlet [Get-content](/powershell/module/microsoft.powershell.management/get-content) .</span><span class="sxs-lookup"><span data-stu-id="86813-146">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="86813-147">U kunt ook de huidige status _testen_ met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="86813-147">You can also _test_ the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="86813-148">De uitvoer moet zijn `True` als het knoop punt momenteel compatibel is met de toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="86813-148">The output should be `True` if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```Output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```Output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="86813-149">De configuratie opnieuw Toep assen</span><span class="sxs-lookup"><span data-stu-id="86813-149">Re-applying the configuration</span></span>

<span data-ttu-id="86813-150">Als u wilt zien hoe de configuratie Get opnieuw wordt toegepast, kunt u het tekst bestand verwijderen dat door uw configuratie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="86813-150">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="86813-151">De cmdlet gebruiken `Start-DSCConfiguration` met de `-UseExisting` para meter.</span><span class="sxs-lookup"><span data-stu-id="86813-151">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="86813-152">De `-UseExisting` para meter geeft `Start-DSCConfiguration` aan dat het huidige. MOF-bestand opnieuw moet worden toegepast. Dit is de meest recent toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="86813-152">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="86813-153">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="86813-153">Next steps</span></span>

- <span data-ttu-id="86813-154">Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="86813-154">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="86813-155">Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="86813-155">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="86813-156">DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="86813-156">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
