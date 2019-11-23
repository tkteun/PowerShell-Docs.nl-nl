---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Publish to a Pull Server using Configuration IDs (v4/v5)
ms.openlocfilehash: 3b094308338e62c783b19f4d3bb41634feee63f6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417249"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a><span data-ttu-id="9e23a-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span><span class="sxs-lookup"><span data-stu-id="9e23a-103">Publish to a Pull Server using Configuration IDs (v4/v5)</span></span>

<span data-ttu-id="9e23a-104">The sections below assume that you have already set up a Pull Server.</span><span class="sxs-lookup"><span data-stu-id="9e23a-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="9e23a-105">If you haven't set up your Pull Server, you can use the following guides:</span><span class="sxs-lookup"><span data-stu-id="9e23a-105">If you haven't set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="9e23a-106">Set up a DSC SMB Pull Server</span><span class="sxs-lookup"><span data-stu-id="9e23a-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9e23a-107">Set up a DSC HTTP Pull Server</span><span class="sxs-lookup"><span data-stu-id="9e23a-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="9e23a-108">Each target node can be configured to download configurations, resources, and even report its status.</span><span class="sxs-lookup"><span data-stu-id="9e23a-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="9e23a-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span><span class="sxs-lookup"><span data-stu-id="9e23a-109">This article shows you how to upload resources so they're available to be downloaded, and configure clients to automatically download resources.</span></span> <span data-ttu-id="9e23a-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span><span class="sxs-lookup"><span data-stu-id="9e23a-110">When the node receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the Local Configuration Manager (LCM).</span></span>

## <a name="compile-configurations"></a><span data-ttu-id="9e23a-111">Compile configurations</span><span class="sxs-lookup"><span data-stu-id="9e23a-111">Compile configurations</span></span>

<span data-ttu-id="9e23a-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span><span class="sxs-lookup"><span data-stu-id="9e23a-112">The first step to storing [Configurations](../configurations/configurations.md) on a Pull Server, is to compile them into `.mof` files.</span></span> <span data-ttu-id="9e23a-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span><span class="sxs-lookup"><span data-stu-id="9e23a-113">To make a configuration generic, and applicable to more clients, use `localhost` in your Node block.</span></span> <span data-ttu-id="9e23a-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span><span class="sxs-lookup"><span data-stu-id="9e23a-114">The example below shows a Configuration shell that uses `localhost` instead of a specific client name.</span></span>

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

<span data-ttu-id="9e23a-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span><span class="sxs-lookup"><span data-stu-id="9e23a-115">Once you've compiled your generic configuration, you should have a `localhost.mof` file.</span></span>

## <a name="renaming-the-mof-file"></a><span data-ttu-id="9e23a-116">Renaming the MOF file</span><span class="sxs-lookup"><span data-stu-id="9e23a-116">Renaming the MOF file</span></span>

<span data-ttu-id="9e23a-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span><span class="sxs-lookup"><span data-stu-id="9e23a-117">You can store Configuration `.mof` files on a Pull Server by **ConfigurationName** or **ConfigurationID**.</span></span> <span data-ttu-id="9e23a-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span><span class="sxs-lookup"><span data-stu-id="9e23a-118">Depending on how you plan to set up your pull clients, you can choose a section below to properly rename your compiled `.mof` files.</span></span>

### <a name="configuration-ids-guid"></a><span data-ttu-id="9e23a-119">Configuration IDs (GUID)</span><span class="sxs-lookup"><span data-stu-id="9e23a-119">Configuration IDs (GUID)</span></span>

<span data-ttu-id="9e23a-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span><span class="sxs-lookup"><span data-stu-id="9e23a-120">You'll need to rename your `localhost.mof` file to `<GUID>.mof` file.</span></span> <span data-ttu-id="9e23a-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e23a-121">You can create a random **Guid** using the example below, or by using the [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.</span></span>

```powershell
[System.Guid]::NewGuid()
```

<span data-ttu-id="9e23a-122">Sample Output</span><span class="sxs-lookup"><span data-stu-id="9e23a-122">Sample Output</span></span>

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

<span data-ttu-id="9e23a-123">You can then rename your `.mof` file using any acceptable method.</span><span class="sxs-lookup"><span data-stu-id="9e23a-123">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="9e23a-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e23a-124">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

<span data-ttu-id="9e23a-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span><span class="sxs-lookup"><span data-stu-id="9e23a-125">For more information about using **Guids** in your environment, see [Plan for Guids](/powershell/scripting/dsc/secureserver#guids).</span></span>

### <a name="configuration-names"></a><span data-ttu-id="9e23a-126">Configuration names</span><span class="sxs-lookup"><span data-stu-id="9e23a-126">Configuration names</span></span>

<span data-ttu-id="9e23a-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span><span class="sxs-lookup"><span data-stu-id="9e23a-127">You'll need to rename your `localhost.mof` file to `<Configuration Name>.mof` file.</span></span> <span data-ttu-id="9e23a-128">In the following example, the configuration name from the previous section is used.</span><span class="sxs-lookup"><span data-stu-id="9e23a-128">In the following example, the configuration name from the previous section is used.</span></span> <span data-ttu-id="9e23a-129">You can then rename your `.mof` file using any acceptable method.</span><span class="sxs-lookup"><span data-stu-id="9e23a-129">You can then rename your `.mof` file using any acceptable method.</span></span> <span data-ttu-id="9e23a-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e23a-130">The example below, uses the [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.</span></span>

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a><span data-ttu-id="9e23a-131">Create the checkSum</span><span class="sxs-lookup"><span data-stu-id="9e23a-131">Create the checkSum</span></span>

<span data-ttu-id="9e23a-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span><span class="sxs-lookup"><span data-stu-id="9e23a-132">Each `.mof` file stored on a Pull Server, or SMB share needs to have an associated `.checksum` file.</span></span>
<span data-ttu-id="9e23a-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span><span class="sxs-lookup"><span data-stu-id="9e23a-133">This file lets clients know when the associated `.mof` file has changed and should be downloaded again.</span></span>

<span data-ttu-id="9e23a-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9e23a-134">You can create a **CheckSum** with the [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet.</span></span> <span data-ttu-id="9e23a-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="9e23a-135">You can also run `New-DSCCheckSum` against a directory of files using the `-Path` parameter.</span></span>
<span data-ttu-id="9e23a-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span><span class="sxs-lookup"><span data-stu-id="9e23a-136">If a checksum already exists, you can force it to be re-created with the `-Force` parameter.</span></span> <span data-ttu-id="9e23a-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span><span class="sxs-lookup"><span data-stu-id="9e23a-137">The following example specified a directory containing the `.mof` file from the previous section, and uses the `-Force` parameter.</span></span>

```powershell
New-DscChecksum -Path '.\' -Force
```

<span data-ttu-id="9e23a-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span><span class="sxs-lookup"><span data-stu-id="9e23a-138">No output will be shown, but you should now see a `<GUID or Configuration Name>.mof.checksum` file.</span></span>

## <a name="where-to-store-mof-files-and-checksums"></a><span data-ttu-id="9e23a-139">Where to store MOF files and checkSums</span><span class="sxs-lookup"><span data-stu-id="9e23a-139">Where to store MOF files and checkSums</span></span>

### <a name="on-a-dsc-http-pull-server"></a><span data-ttu-id="9e23a-140">On a DSC HTTP Pull Server</span><span class="sxs-lookup"><span data-stu-id="9e23a-140">On a DSC HTTP Pull Server</span></span>

<span data-ttu-id="9e23a-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span><span class="sxs-lookup"><span data-stu-id="9e23a-141">When you set up your HTTP Pull Server, as explained in [Set up a DSC HTTP Pull Server](pullServer.md), you specify directories for the **ModulePath** and **ConfigurationPath** keys.</span></span> <span data-ttu-id="9e23a-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span><span class="sxs-lookup"><span data-stu-id="9e23a-142">The **ModulePath** key indicates where a module's packaged `.zip` files should be stored.</span></span> <span data-ttu-id="9e23a-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span><span class="sxs-lookup"><span data-stu-id="9e23a-143">The **ConfigurationPath** indicates where any `.mof` files and `.checksum` files should be stored.</span></span>

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a><span data-ttu-id="9e23a-144">On an SMB share</span><span class="sxs-lookup"><span data-stu-id="9e23a-144">On an SMB share</span></span>

<span data-ttu-id="9e23a-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span><span class="sxs-lookup"><span data-stu-id="9e23a-145">When you set up a Pull Client to use an SMB share, you specify a **ConfigurationRepositoryShare**.</span></span>
<span data-ttu-id="9e23a-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span><span class="sxs-lookup"><span data-stu-id="9e23a-146">All `.mof` files and `.checksum` files should be stored in the **SourcePath** directory from the **ConfigurationRepositoryShare** block.</span></span>

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a><span data-ttu-id="9e23a-147">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="9e23a-147">Next steps</span></span>

<span data-ttu-id="9e23a-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span><span class="sxs-lookup"><span data-stu-id="9e23a-148">Next, you'll want to configure Pull Clients to pull the specified configuration.</span></span> <span data-ttu-id="9e23a-149">For more information, see one of the following guides:</span><span class="sxs-lookup"><span data-stu-id="9e23a-149">For more information, see one of the following guides:</span></span>

- [<span data-ttu-id="9e23a-150">Set up a Pull Client using Configuration IDs (v4)</span><span class="sxs-lookup"><span data-stu-id="9e23a-150">Set up a Pull Client using Configuration IDs (v4)</span></span>](pullClientConfigId4.md)
- [<span data-ttu-id="9e23a-151">Set up a Pull Client using Configuration IDs (v5)</span><span class="sxs-lookup"><span data-stu-id="9e23a-151">Set up a Pull Client using Configuration IDs (v5)</span></span>](pullClientConfigId.md)
- [<span data-ttu-id="9e23a-152">Set up a Pull Client using Configuration Names (v5)</span><span class="sxs-lookup"><span data-stu-id="9e23a-152">Set up a Pull Client using Configuration Names (v5)</span></span>](pullClientConfigNames.md)

## <a name="see-also"></a><span data-ttu-id="9e23a-153">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9e23a-153">See also</span></span>

- [<span data-ttu-id="9e23a-154">Set up a DSC SMB Pull Server</span><span class="sxs-lookup"><span data-stu-id="9e23a-154">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="9e23a-155">Set up a DSC HTTP Pull Server</span><span class="sxs-lookup"><span data-stu-id="9e23a-155">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)
- [<span data-ttu-id="9e23a-156">Package and Upload Resources to a Pull Server</span><span class="sxs-lookup"><span data-stu-id="9e23a-156">Package and Upload Resources to a Pull Server</span></span>](package-upload-resources.md)
