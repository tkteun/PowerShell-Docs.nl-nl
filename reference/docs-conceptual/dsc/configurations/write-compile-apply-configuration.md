---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, service, installatie
title: Een configuratie schrijven, compileren en toepassen
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818155"
---
> <span data-ttu-id="c2fad-103">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="c2fad-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="c2fad-104">Een configuratie schrijven, compileren en toepassen</span><span class="sxs-lookup"><span data-stu-id="c2fad-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="c2fad-105">In deze oefening wordt uitgelegd hoe u een desired state Configuration (DSC)-configuratie kunt maken en Toep assen van het begin tot het einde.</span><span class="sxs-lookup"><span data-stu-id="c2fad-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="c2fad-106">In het volgende voor beeld wordt uitgelegd hoe u een eenvoudige configuratie kunt schrijven en Toep assen.</span><span class="sxs-lookup"><span data-stu-id="c2fad-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="c2fad-107">De configuratie zorgt ervoor dat het bestand HelloWorld. txt bestaat op de lokale computer.</span><span class="sxs-lookup"><span data-stu-id="c2fad-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="c2fad-108">Als u het bestand verwijdert, maakt DSC de volgende keer dat het wordt bijgewerkt opnieuw.</span><span class="sxs-lookup"><span data-stu-id="c2fad-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="c2fad-109">Voor een overzicht van wat DSC is en hoe het werkt, raadpleegt u [overzicht van desired state Configuration voor ontwikkel aars](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2fad-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c2fad-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c2fad-110">Requirements</span></span>

<span data-ttu-id="c2fad-111">Als u dit voor beeld wilt uitvoeren, hebt u een computer nodig waarop Power Shell 4,0 of hoger wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="c2fad-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="c2fad-112">De configuratie schrijven</span><span class="sxs-lookup"><span data-stu-id="c2fad-112">Write the configuration</span></span>

<span data-ttu-id="c2fad-113">Een DSC- [configuratie](configurations.md) is een speciale Power shell-functie die definieert hoe u een of meer doel computers (knoop punten) wilt configureren.</span><span class="sxs-lookup"><span data-stu-id="c2fad-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="c2fad-114">In Power shell ISE of een andere Power shell-editor typt u het volgende:</span><span class="sxs-lookup"><span data-stu-id="c2fad-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

> <span data-ttu-id="c2fad-115">! Belang rijk in meer geavanceerde scenario's waarbij meerdere modules moeten worden geïmporteerd zodat u met een groot aantal DSC-resources in dezelfde configuratie kunt werken, moet u ervoor zorgen dat elke module op een aparte regel wordt geplaatst met behulp van `Import-DscResource`.</span><span class="sxs-lookup"><span data-stu-id="c2fad-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="c2fad-116">Dit is eenvoudiger te onderhouden in broncode beheer en is vereist bij het werken met DSC in azure-status configuratie.</span><span class="sxs-lookup"><span data-stu-id="c2fad-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="c2fad-117">Sla het bestand op als ' HelloWorld. ps1 '.</span><span class="sxs-lookup"><span data-stu-id="c2fad-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="c2fad-118">Het definiëren van een configuratie is vergelijkbaar met het definiëren van een functie.</span><span class="sxs-lookup"><span data-stu-id="c2fad-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="c2fad-119">Het **knoop punt** blok geeft het doel knooppunt op dat moet worden geconfigureerd. in dit geval `localhost`.</span><span class="sxs-lookup"><span data-stu-id="c2fad-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="c2fad-120">De configuratie roept één [resources](../resources/resources.md), de `File` resource.</span><span class="sxs-lookup"><span data-stu-id="c2fad-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="c2fad-121">Resources maken het werk om ervoor te zorgen dat het doel knooppunt zich in de status bevindt die door de configuratie is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="c2fad-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="c2fad-122">De configuratie compileren</span><span class="sxs-lookup"><span data-stu-id="c2fad-122">Compile the configuration</span></span>

<span data-ttu-id="c2fad-123">Een DSC-configuratie die wordt toegepast op een knoop punt, moet eerst worden gecompileerd in een MOF-bestand.</span><span class="sxs-lookup"><span data-stu-id="c2fad-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="c2fad-124">Als u de configuratie uitvoert, zoals een functie, wordt een '. MOF-bestand ' gecompileerd voor elk knoop punt dat is gedefinieerd door het `Node` blok.</span><span class="sxs-lookup"><span data-stu-id="c2fad-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="c2fad-125">Als u de configuratie wilt uitvoeren, moet *u het script* ' HelloWorld. ps1 ' in het huidige bereik.</span><span class="sxs-lookup"><span data-stu-id="c2fad-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="c2fad-126">Zie [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c2fad-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="c2fad-127">*Stip* het script ' HelloWorld. ps1 ' door te typen in het pad waar u het hebt opgeslagen, na de `. ` (punt, spatie).</span><span class="sxs-lookup"><span data-stu-id="c2fad-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="c2fad-128">U kunt vervolgens uw configuratie uitvoeren door deze als een functie aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c2fad-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="c2fad-129">Hiermee wordt de volgende uitvoer gegenereerd:</span><span class="sxs-lookup"><span data-stu-id="c2fad-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="c2fad-130">De configuratie Toep assen</span><span class="sxs-lookup"><span data-stu-id="c2fad-130">Apply the configuration</span></span>

<span data-ttu-id="c2fad-131">Nu u de gecompileerde MOF hebt, kunt u de configuratie Toep assen op het doel knooppunt (in dit geval de lokale computer) door de cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c2fad-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="c2fad-132">De cmdlet `Start-DscConfiguration` vertelt de [lokale Configuration Manager (LCM)](../managing-nodes/metaConfig.md), de engine van DSC, om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="c2fad-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="c2fad-133">De LCM maakt het mogelijk om de DSC-resources aan te roepen om de configuratie toe te passen.</span><span class="sxs-lookup"><span data-stu-id="c2fad-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="c2fad-134">Gebruik de onderstaande code om de cmdlet `Start-DSCConfiguration` uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c2fad-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="c2fad-135">Geef het mappad op waar uw ' localhost. mof ' wordt opgeslagen in de para meter `-Path`.</span><span class="sxs-lookup"><span data-stu-id="c2fad-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="c2fad-136">De `Start-DSCConfiguration`-cmdlet zoekt naar de map die is opgegeven voor de bestanden\<ComputerName\>. mof.</span><span class="sxs-lookup"><span data-stu-id="c2fad-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="c2fad-137">De `Start-DSCConfiguration`-cmdlet probeert elk bestand '. mof ' toe te passen op de computer naam die is opgegeven door de filename (' localhost ', ' Server01 ', ' DC-02 ', enzovoort).</span><span class="sxs-lookup"><span data-stu-id="c2fad-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="c2fad-138">Als de para meter `-Wait` niet is opgegeven, maakt `Start-DSCConfiguration` een achtergrond taak om de bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="c2fad-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="c2fad-139">Als u de para meter `-Verbose` opgeeft, kunt u de **uitgebreide** uitvoer van de bewerking bekijken.</span><span class="sxs-lookup"><span data-stu-id="c2fad-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="c2fad-140">`-Wait`en `-Verbose` zijn beide optionele para meters.</span><span class="sxs-lookup"><span data-stu-id="c2fad-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="c2fad-141">De configuratie testen</span><span class="sxs-lookup"><span data-stu-id="c2fad-141">Test the configuration</span></span>

<span data-ttu-id="c2fad-142">Zodra de cmdlet `Start-DSCConfiguration` is voltooid, ziet u het bestand HelloWorld. txt op de locatie die u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c2fad-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="c2fad-143">U kunt de inhoud controleren met de cmdlet [Get-content](/powershell/module/microsoft.powershell.management/get-content) .</span><span class="sxs-lookup"><span data-stu-id="c2fad-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="c2fad-144">U kunt ook de huidige status *testen* met [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="c2fad-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="c2fad-145">De uitvoer moet ' waar ' zijn als het knoop punt momenteel compatibel is met de toegepaste configuratie.</span><span class="sxs-lookup"><span data-stu-id="c2fad-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="c2fad-146">De configuratie opnieuw Toep assen</span><span class="sxs-lookup"><span data-stu-id="c2fad-146">Re-applying the configuration</span></span>

<span data-ttu-id="c2fad-147">Als u wilt zien hoe de configuratie Get opnieuw wordt toegepast, kunt u het tekst bestand verwijderen dat door uw configuratie is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="c2fad-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="c2fad-148">De cmdlet `Start-DSCConfiguration` gebruiken met de para meter `-UseExisting`.</span><span class="sxs-lookup"><span data-stu-id="c2fad-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="c2fad-149">De para meter `-UseExisting` geeft aan `Start-DSCConfiguration` het huidige. MOF-bestand opnieuw toe te passen, waarmee de meest recent toegepaste configuratie wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="c2fad-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="c2fad-150">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="c2fad-150">Next steps</span></span>

- <span data-ttu-id="c2fad-151">Meer informatie over DSC-configuraties vindt u in [DSC-configuraties](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="c2fad-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="c2fad-152">Bekijk welke DSC-resources beschikbaar zijn en hoe u aangepaste DSC-resources maakt op [DSC-resources](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="c2fad-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="c2fad-153">DSC-configuraties en-resources zoeken in de [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="c2fad-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
