---
ms.date: 12/12/2018
keywords: DSC, Power shell, configuratie, installatie
title: Publiceren naar een pull-server met behulp van configuratie-Id's (v4/V5)
ms.openlocfilehash: 3b094308338e62c783b19f4d3bb41634feee63f6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417249"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="fe6a4-103">Publiceren naar een pull-server met behulp van configuratie-Id's (v4/V5)</span><span class="sxs-lookup"><span data-stu-id="fe6a4-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="fe6a4-104">In de volgende secties wordt ervan uitgegaan dat u al een pull-server hebt ingesteld.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="fe6a4-105">Als u uw pull-server nog niet hebt ingesteld, kunt u de volgende hand leidingen gebruiken:</span><span class="sxs-lookup"><span data-stu-id="fe6a4-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="fe6a4-106">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="fe6a4-107">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="fe6a4-108">Elk doel knooppunt kan worden geconfigureerd voor het downloaden van configuraties, resources en zelfs het rapporteren van de status ervan.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="fe6a4-109">In dit artikel wordt beschreven hoe u bronnen uploadt, zodat deze beschikbaar zijn om te worden gedownload en clients configureren voor het automatisch downloaden van resources.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="fe6a4-110">Wanneer het knoop punt een toegewezen configuratie ontvangt via **pull** of **Push** (V5), worden de resources die vereist zijn voor de configuratie automatisch gedownload van de locatie die is opgegeven in de lokale Configuration Manager (LCM).</span><span class="sxs-lookup"><span data-stu-id="fe6a4-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="fe6a4-111">Configuraties compileren</span><span class="sxs-lookup"><span data-stu-id="fe6a4-111">Compile configurations</span></span>

<span data-ttu-id="fe6a4-112">De eerste stap voor het opslaan van [configuraties](../configurations/configurations.md) op een pull-server is het compileren van deze in `.mof`-bestanden.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="fe6a4-113">Als u een algemene configuratie wilt maken en van toepassing is op meer clients, gebruikt u `localhost` in uw knooppunt blok.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="fe6a4-114">In het onderstaande voor beeld ziet u een configuratie shell die gebruikmaakt van `localhost` in plaats van een specifieke client naam.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="fe6a4-115">Wanneer u de algemene configuratie hebt gecompileerd, hebt u een `localhost.mof`-bestand nodig.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="fe6a4-116">De naam van het MOF-bestand wijzigen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-116">Renaming the MOF file</span></span>

<span data-ttu-id="fe6a4-117">U kunt configuratie-`.mof` bestanden opslaan op een pull-server via **configuratiepad** of **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="fe6a4-118">Afhankelijk van hoe u uw pull-clients wilt instellen, kunt u een van de onderstaande secties kiezen om de naam van uw gecompileerde `.mof`-bestanden goed te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="fe6a4-119">Configuratie-Id's (GUID)</span><span class="sxs-lookup"><span data-stu-id="fe6a4-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="fe6a4-120">U moet de naam van uw `localhost.mof` bestand wijzigen in `<GUID>.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="fe6a4-121">U kunt een wille keurige **GUID** maken met behulp van het voor beeld hieronder of met de cmdlet [New-GUID](/powershell/module/microsoft.powershell.utility/new-guid) .</span><span class="sxs-lookup"><span data-stu-id="fe6a4-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="fe6a4-122">Voorbeelduitvoer</span><span class="sxs-lookup"><span data-stu-id="fe6a4-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="fe6a4-123">U kunt de naam van uw `.mof`-bestand vervolgens met behulp van een aanvaard bare methode wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="fe6a4-124">In het onderstaande voor beeld wordt de cmdlet [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="fe6a4-125">Zie voor meer informatie over het gebruik van **guid's** in uw omgeving [plan for guid's](/powershell/scripting/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="fe6a4-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="fe6a4-126">Configuratie namen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-126">Configuration names</span></span>

<span data-ttu-id="fe6a4-127">U moet de naam van uw `localhost.mof` bestand wijzigen in `<Configuration Name>.mof` bestand.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="fe6a4-128">In het volgende voor beeld wordt de naam van de configuratie uit de vorige sectie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="fe6a4-129">U kunt de naam van uw `.mof`-bestand vervolgens met behulp van een aanvaard bare methode wijzigen.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="fe6a4-130">In het onderstaande voor beeld wordt de cmdlet [Rename-item](/powershell/module/microsoft.powershell.management/rename-item) gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="fe6a4-131">De controlesom maken</span><span class="sxs-lookup"><span data-stu-id="fe6a4-131">Create the checkSum</span></span>

<span data-ttu-id="fe6a4-132">Elk `.mof`-bestand dat is opgeslagen op een pull-server of de SMB-share moet een gekoppeld `.checksum` bestand hebben.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="fe6a4-133">Met dit bestand kunnen clients weten wanneer het bijbehorende `.mof`-bestand is gewijzigd en het opnieuw moet worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="fe6a4-134">U kunt een **controlesom** maken met de cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) .</span><span class="sxs-lookup"><span data-stu-id="fe6a4-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="fe6a4-135">U kunt `New-DSCCheckSum` ook uitvoeren op een map met bestanden met behulp van de para meter `-Path`.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="fe6a4-136">Als er al een controlesom bestaat, kunt u afdwingen dat deze opnieuw wordt gemaakt met de para meter `-Force`.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="fe6a4-137">In het volgende voor beeld is een map opgegeven met het `.mof`-bestand uit de vorige sectie en wordt de `-Force`-para meter gebruikt.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="fe6a4-138">Er wordt geen uitvoer weer gegeven, maar u ziet nu een `<GUID or Configuration Name>.mof.checksum` bestand.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="fe6a4-139">Waar u MOF-bestanden en controle sommen opslaat</span><span class="sxs-lookup"><span data-stu-id="fe6a4-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="fe6a4-140">Op een DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="fe6a4-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="fe6a4-141">Wanneer u de HTTP-pull-server instelt, zoals wordt uitgelegd in [een DSC HTTP-pull-server instellen](pullServer.md), geeft u directory's op voor de sleutels **para modulepath in** en **ConfigurationPath** .</span><span class="sxs-lookup"><span data-stu-id="fe6a4-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="fe6a4-142">De **para modulepath in** -sleutel geeft aan waar de verpakte bestanden van een module `.zip` moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="fe6a4-143">De **ConfigurationPath** geeft aan waar elke `.mof` bestanden en `.checksum` bestanden moeten worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="fe6a4-144">Op een SMB-share</span><span class="sxs-lookup"><span data-stu-id="fe6a4-144">On an SMB share</span></span>

<span data-ttu-id="fe6a4-145">Wanneer u een pull-client instelt voor het gebruik van een SMB-share, geeft u een **ConfigurationRepositoryShare**op.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="fe6a4-146">Alle `.mof` bestanden en `.checksum` bestanden moeten worden opgeslagen in de map **SourcePath** van het **ConfigurationRepositoryShare** -blok.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="fe6a4-147">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-147">Next steps</span></span>

<span data-ttu-id="fe6a4-148">Vervolgens moet u pull-clients configureren voor het ophalen van de opgegeven configuratie.</span><span class="sxs-lookup"><span data-stu-id="fe6a4-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="fe6a4-149">Zie een van de volgende hand leidingen voor meer informatie:</span><span class="sxs-lookup"><span data-stu-id="fe6a4-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="fe6a4-150">Een pull-client instellen met behulp van configuratie-Id's (v4)</span><span class="sxs-lookup"><span data-stu-id="fe6a4-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="fe6a4-151">Een pull-client instellen met behulp van configuratie-Id's (V5)</span><span class="sxs-lookup"><span data-stu-id="fe6a4-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="fe6a4-152">Een pull-client instellen met behulp van configuratie namen (V5)</span><span class="sxs-lookup"><span data-stu-id="fe6a4-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="fe6a4-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fe6a4-153">See also</span></span>

- [<span data-ttu-id="fe6a4-154">Een DSC SMB-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="fe6a4-155">Een DSC HTTP-pull-server instellen</span><span class="sxs-lookup"><span data-stu-id="fe6a4-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="fe6a4-156">Resources verpakken en uploaden naar een pull-server</span><span class="sxs-lookup"><span data-stu-id="fe6a4-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
