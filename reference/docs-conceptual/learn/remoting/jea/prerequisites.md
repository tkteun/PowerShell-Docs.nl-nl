---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA Prerequisites
ms.openlocfilehash: 1833bacf49eebcccefc10f7c85a39732559c1a97
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416724"
---
# <a name="prerequisites"></a><span data-ttu-id="2c81c-103">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2c81c-103">Prerequisites</span></span>

<span data-ttu-id="2c81c-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span><span class="sxs-lookup"><span data-stu-id="2c81c-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="2c81c-105">This article describes the prerequisites that must be satisfied to start using JEA.</span><span class="sxs-lookup"><span data-stu-id="2c81c-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="2c81c-106">Check which version of PowerShell is installed</span><span class="sxs-lookup"><span data-stu-id="2c81c-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="2c81c-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span><span class="sxs-lookup"><span data-stu-id="2c81c-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="2c81c-108">JEA is available with PowerShell 5.0 and higher.</span><span class="sxs-lookup"><span data-stu-id="2c81c-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="2c81c-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span><span class="sxs-lookup"><span data-stu-id="2c81c-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="2c81c-110">The following table describes JEA's availability on Windows Server:</span><span class="sxs-lookup"><span data-stu-id="2c81c-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="2c81c-111">Server Operating System</span><span class="sxs-lookup"><span data-stu-id="2c81c-111">Server Operating System</span></span> |                <span data-ttu-id="2c81c-112">JEA Availability</span><span class="sxs-lookup"><span data-stu-id="2c81c-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="2c81c-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="2c81c-113">Windows Server 2016+</span></span>    | <span data-ttu-id="2c81c-114">Preinstalled</span><span class="sxs-lookup"><span data-stu-id="2c81c-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="2c81c-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2c81c-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="2c81c-116">Full functionality with WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2c81c-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="2c81c-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="2c81c-117">Windows Server 2012</span></span>     | <span data-ttu-id="2c81c-118">Full functionality with WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2c81c-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="2c81c-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2c81c-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="2c81c-120">Reduced functionality<sup>1</sup> with WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2c81c-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="2c81c-121">You can also use JEA on your home or work computer:</span><span class="sxs-lookup"><span data-stu-id="2c81c-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="2c81c-122">Client Operating System</span><span class="sxs-lookup"><span data-stu-id="2c81c-122">Client Operating System</span></span> |                   <span data-ttu-id="2c81c-123">JEA Availability</span><span class="sxs-lookup"><span data-stu-id="2c81c-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="2c81c-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="2c81c-124">Windows 10 1607+</span></span>        | <span data-ttu-id="2c81c-125">Preinstalled</span><span class="sxs-lookup"><span data-stu-id="2c81c-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="2c81c-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="2c81c-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="2c81c-127">Preinstalled, with reduced functionality<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2c81c-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="2c81c-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="2c81c-128">Windows 10 1507</span></span>         | <span data-ttu-id="2c81c-129">Niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="2c81c-129">Not available</span></span>                                        |
| <span data-ttu-id="2c81c-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="2c81c-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="2c81c-131">Full functionality with WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2c81c-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="2c81c-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="2c81c-132">Windows 7</span></span>               | <span data-ttu-id="2c81c-133">Reduced functionality<sup>1</sup> with WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="2c81c-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="2c81c-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2c81c-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="2c81c-135">Virtual accounts and other JEA features *are* supported.</span><span class="sxs-lookup"><span data-stu-id="2c81c-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="2c81c-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span><span class="sxs-lookup"><span data-stu-id="2c81c-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="2c81c-137">Running as a group-managed service account</span><span class="sxs-lookup"><span data-stu-id="2c81c-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="2c81c-138">Conditional access rules in session configurations</span><span class="sxs-lookup"><span data-stu-id="2c81c-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="2c81c-139">The user drive</span><span class="sxs-lookup"><span data-stu-id="2c81c-139">The user drive</span></span>
  - <span data-ttu-id="2c81c-140">Granting access to local user accounts</span><span class="sxs-lookup"><span data-stu-id="2c81c-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="2c81c-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span><span class="sxs-lookup"><span data-stu-id="2c81c-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="2c81c-142">Install Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="2c81c-142">Install Windows Management Framework</span></span>

<span data-ttu-id="2c81c-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span><span class="sxs-lookup"><span data-stu-id="2c81c-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="2c81c-144">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="2c81c-144">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="2c81c-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span><span class="sxs-lookup"><span data-stu-id="2c81c-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="2c81c-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c81c-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="2c81c-147">Enable PowerShell Remoting</span><span class="sxs-lookup"><span data-stu-id="2c81c-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="2c81c-148">PowerShell Remoting provides the foundation on which JEA is built.</span><span class="sxs-lookup"><span data-stu-id="2c81c-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="2c81c-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span><span class="sxs-lookup"><span data-stu-id="2c81c-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="2c81c-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="2c81c-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="2c81c-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span><span class="sxs-lookup"><span data-stu-id="2c81c-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="2c81c-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span><span class="sxs-lookup"><span data-stu-id="2c81c-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="2c81c-153">Enable PowerShell module and script block logging (optional)</span><span class="sxs-lookup"><span data-stu-id="2c81c-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="2c81c-154">The following steps enable logging for all PowerShell actions on your system.</span><span class="sxs-lookup"><span data-stu-id="2c81c-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="2c81c-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span><span class="sxs-lookup"><span data-stu-id="2c81c-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="2c81c-156">You can configure the PowerShell Module Logging policy using Group Policy.</span><span class="sxs-lookup"><span data-stu-id="2c81c-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="2c81c-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span><span class="sxs-lookup"><span data-stu-id="2c81c-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="2c81c-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="2c81c-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="2c81c-159">Double-click on **Turn on Module Logging**</span><span class="sxs-lookup"><span data-stu-id="2c81c-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="2c81c-160">Click **Enabled**</span><span class="sxs-lookup"><span data-stu-id="2c81c-160">Click **Enabled**</span></span>
5. <span data-ttu-id="2c81c-161">In the Options section, click on **Show** next to Module Names</span><span class="sxs-lookup"><span data-stu-id="2c81c-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="2c81c-162">Type `*` in the pop-up window to log commands from all modules.</span><span class="sxs-lookup"><span data-stu-id="2c81c-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="2c81c-163">Click **OK** to set the policy</span><span class="sxs-lookup"><span data-stu-id="2c81c-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="2c81c-164">Double-click on **Turn on PowerShell Script Block Logging**</span><span class="sxs-lookup"><span data-stu-id="2c81c-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="2c81c-165">Click **Enabled**</span><span class="sxs-lookup"><span data-stu-id="2c81c-165">Click **Enabled**</span></span>
10. <span data-ttu-id="2c81c-166">Click **OK** to set the policy</span><span class="sxs-lookup"><span data-stu-id="2c81c-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="2c81c-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span><span class="sxs-lookup"><span data-stu-id="2c81c-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="2c81c-168">You can also enable system-wide PowerShell transcription through Group Policy.</span><span class="sxs-lookup"><span data-stu-id="2c81c-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c81c-169">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="2c81c-169">Next steps</span></span>

[<span data-ttu-id="2c81c-170">Create a role capability file</span><span class="sxs-lookup"><span data-stu-id="2c81c-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="2c81c-171">Create a session configuration file</span><span class="sxs-lookup"><span data-stu-id="2c81c-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="2c81c-172">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2c81c-172">See also</span></span>

[<span data-ttu-id="2c81c-173">WinRM Security</span><span class="sxs-lookup"><span data-stu-id="2c81c-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="2c81c-174">PowerShell ♥ the Blue Team</span><span class="sxs-lookup"><span data-stu-id="2c81c-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
