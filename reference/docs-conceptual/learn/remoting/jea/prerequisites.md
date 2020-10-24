---
ms.date: 07/10/2019
keywords: JEA, Power shell, beveiliging
title: Vereisten voor JEA
description: In dit artikel worden de vereisten beschreven waaraan moet worden voldaan om JEA te kunnen gebruiken.
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501725"
---
# <a name="prerequisites"></a><span data-ttu-id="c6d88-104">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c6d88-104">Prerequisites</span></span>

<span data-ttu-id="c6d88-105">Net genoeg beheer is een functie die is opgenomen in Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c6d88-105">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="c6d88-106">In dit artikel worden de vereisten beschreven waaraan moet worden voldaan om JEA te kunnen gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c6d88-106">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>

## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="c6d88-107">Controleren welke versie van Power shell is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="c6d88-107">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="c6d88-108">Als u wilt controleren welke versie van Power shell op uw systeem is geïnstalleerd, controleert u de `$PSVersionTable` variabele in een Windows Power shell-prompt.</span><span class="sxs-lookup"><span data-stu-id="c6d88-108">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="c6d88-109">JEA is beschikbaar met Power shell 5,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="c6d88-109">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="c6d88-110">Voor volledige functionaliteit is het raadzaam om de meest recente versie van Power shell te installeren die beschikbaar is voor uw systeem.</span><span class="sxs-lookup"><span data-stu-id="c6d88-110">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="c6d88-111">In de volgende tabel wordt de beschik baarheid van JEA op Windows Server beschreven:</span><span class="sxs-lookup"><span data-stu-id="c6d88-111">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="c6d88-112">Serverbesturingssysteem</span><span class="sxs-lookup"><span data-stu-id="c6d88-112">Server Operating System</span></span> |                <span data-ttu-id="c6d88-113">JEA-Beschik baarheid</span><span class="sxs-lookup"><span data-stu-id="c6d88-113">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="c6d88-114">Windows Server 2016 +</span><span class="sxs-lookup"><span data-stu-id="c6d88-114">Windows Server 2016+</span></span>    | <span data-ttu-id="c6d88-115">Vooraf geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="c6d88-115">Preinstalled</span></span>                                   |
| <span data-ttu-id="c6d88-116">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="c6d88-116">Windows Server 2012 R2</span></span>  | <span data-ttu-id="c6d88-117">Volledige functionaliteit met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="c6d88-117">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="c6d88-118">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c6d88-118">Windows Server 2012</span></span>     | <span data-ttu-id="c6d88-119">Volledige functionaliteit met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="c6d88-119">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="c6d88-120">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c6d88-120">Windows Server 2008 R2</span></span>  | <span data-ttu-id="c6d88-121">Verminderde functionaliteit<sup>1</sup> met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="c6d88-121">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="c6d88-122">U kunt JEA ook gebruiken op uw computer thuis of op het werk:</span><span class="sxs-lookup"><span data-stu-id="c6d88-122">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="c6d88-123">Clientbesturingssysteem</span><span class="sxs-lookup"><span data-stu-id="c6d88-123">Client Operating System</span></span> |                   <span data-ttu-id="c6d88-124">JEA-Beschik baarheid</span><span class="sxs-lookup"><span data-stu-id="c6d88-124">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="c6d88-125">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="c6d88-125">Windows 10 1607+</span></span>        | <span data-ttu-id="c6d88-126">Vooraf geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="c6d88-126">Preinstalled</span></span>                                         |
| <span data-ttu-id="c6d88-127">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="c6d88-127">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="c6d88-128">Vooraf geïnstalleerd, met beperkte functionaliteit<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="c6d88-128">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="c6d88-129">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="c6d88-129">Windows 10 1507</span></span>         | <span data-ttu-id="c6d88-130">Niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="c6d88-130">Not available</span></span>                                        |
| <span data-ttu-id="c6d88-131">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="c6d88-131">Windows 8, 8.1</span></span>          | <span data-ttu-id="c6d88-132">Volledige functionaliteit met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="c6d88-132">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="c6d88-133">Windows 7</span><span class="sxs-lookup"><span data-stu-id="c6d88-133">Windows 7</span></span>               | <span data-ttu-id="c6d88-134">Verminderde functionaliteit<sup>1</sup> met WMF 5,1</span><span class="sxs-lookup"><span data-stu-id="c6d88-134">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="c6d88-135"><sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van door groepen beheerde service accounts in windows server 2008 R2 of Windows 7.</span><span class="sxs-lookup"><span data-stu-id="c6d88-135"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="c6d88-136">Virtuele accounts en andere JEA-functies *worden* ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c6d88-136">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="c6d88-137"><sup>2</sup> de volgende JEA-functies worden niet ondersteund in Windows 10 versie 1511 en 1603:</span><span class="sxs-lookup"><span data-stu-id="c6d88-137"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="c6d88-138">Uitvoeren als een door een groep beheerd service account</span><span class="sxs-lookup"><span data-stu-id="c6d88-138">Running as a group-managed service account</span></span>
  - <span data-ttu-id="c6d88-139">Regels voor voorwaardelijke toegang in sessie configuraties</span><span class="sxs-lookup"><span data-stu-id="c6d88-139">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="c6d88-140">Het gebruikers station</span><span class="sxs-lookup"><span data-stu-id="c6d88-140">The user drive</span></span>
  - <span data-ttu-id="c6d88-141">Toegang verlenen tot lokale gebruikers accounts</span><span class="sxs-lookup"><span data-stu-id="c6d88-141">Granting access to local user accounts</span></span>

  <span data-ttu-id="c6d88-142">Als u ondersteuning voor deze functies wilt, werkt u Windows bij naar versie 1607 (jubileum update) of hoger.</span><span class="sxs-lookup"><span data-stu-id="c6d88-142">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="c6d88-143">Windows Management Framework installeren</span><span class="sxs-lookup"><span data-stu-id="c6d88-143">Install Windows Management Framework</span></span>

<span data-ttu-id="c6d88-144">Als u een oudere versie van Power shell gebruikt, moet u mogelijk uw systeem bijwerken met de meest recente Windows Management Framework (WMF)-update.</span><span class="sxs-lookup"><span data-stu-id="c6d88-144">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="c6d88-145">Raadpleeg de [WMF-documentatie](/powershell/scripting/wmf/overview)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c6d88-145">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="c6d88-146">Het is raadzaam om de compatibiliteit van uw werk belasting met WMF te testen voordat u de upgrade van alle servers uitvoert.</span><span class="sxs-lookup"><span data-stu-id="c6d88-146">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="c6d88-147">Windows 10-gebruikers moeten de nieuwste functie-updates installeren om de huidige versie van Windows Power shell te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="c6d88-147">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="c6d88-148">Externe communicatie met Power shell inschakelen</span><span class="sxs-lookup"><span data-stu-id="c6d88-148">Enable PowerShell Remoting</span></span>

<span data-ttu-id="c6d88-149">Externe communicatie met Power shell biedt de basis waarop JEA is gebouwd.</span><span class="sxs-lookup"><span data-stu-id="c6d88-149">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="c6d88-150">Het is nood zakelijk om ervoor te zorgen dat externe communicatie van Power shell is ingeschakeld en goed wordt beveiligd voordat u JEA kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c6d88-150">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="c6d88-151">Zie [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="c6d88-151">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="c6d88-152">Externe communicatie van Power shell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016.</span><span class="sxs-lookup"><span data-stu-id="c6d88-152">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="c6d88-153">U kunt externe communicatie van Power shell inschakelen door de volgende opdracht uit te voeren in een Power shell-venster met verhoogde bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="c6d88-153">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="c6d88-154">Power shell-module en logboek registratie van script blokken inschakelen (optioneel)</span><span class="sxs-lookup"><span data-stu-id="c6d88-154">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="c6d88-155">Met de volgende stappen kunt u logboek registratie inschakelen voor alle Power shell-acties op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="c6d88-155">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="c6d88-156">Logboek registratie van de Power shell-module is niet vereist voor JEA, maar het is raadzaam om logboek registratie in te scha kelen om ervoor te zorgen dat de opdrachten die gebruikers uitvoeren, worden geregistreerd op een centrale locatie.</span><span class="sxs-lookup"><span data-stu-id="c6d88-156">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="c6d88-157">U kunt het beleid voor logboek registratie van Power shell-modules configureren met behulp van groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="c6d88-157">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="c6d88-158">Open de Lokale groepsbeleidsobjecteditor op een werk station of een groepsbeleid-object in de console Groepsbeleidbeheer op een Active Directory-domein controller</span><span class="sxs-lookup"><span data-stu-id="c6d88-158">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="c6d88-159">Navigeren naar **computer configuratie \\ Beheersjablonen \\ Windows- \\ onderdelen Windows Power shell**</span><span class="sxs-lookup"><span data-stu-id="c6d88-159">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="c6d88-160">Dubbel klik op **inschakelen logboek registratie** van de module</span><span class="sxs-lookup"><span data-stu-id="c6d88-160">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="c6d88-161">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="c6d88-161">Click **Enabled**</span></span>
5. <span data-ttu-id="c6d88-162">Klik in de sectie opties op **weer geven** naast module namen</span><span class="sxs-lookup"><span data-stu-id="c6d88-162">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="c6d88-163">Typ `*` in het pop-upvenster om opdrachten van alle modules te registreren.</span><span class="sxs-lookup"><span data-stu-id="c6d88-163">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="c6d88-164">Klik op **OK** om het beleid in te stellen</span><span class="sxs-lookup"><span data-stu-id="c6d88-164">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="c6d88-165">Dubbel klik op **inschakelen logboek registratie van Power shell-script blokken**</span><span class="sxs-lookup"><span data-stu-id="c6d88-165">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="c6d88-166">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="c6d88-166">Click **Enabled**</span></span>
10. <span data-ttu-id="c6d88-167">Klik op **OK** om het beleid in te stellen</span><span class="sxs-lookup"><span data-stu-id="c6d88-167">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="c6d88-168">(Alleen op computers die lid zijn van een domein) Uitvoeren `gpupdate` of wachten tot Groepsbeleid het bijgewerkte beleid verwerkt en de instellingen toepast</span><span class="sxs-lookup"><span data-stu-id="c6d88-168">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="c6d88-169">U kunt ook de systeembrede Power shell-transcriptie inschakelen via groepsbeleid.</span><span class="sxs-lookup"><span data-stu-id="c6d88-169">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c6d88-170">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="c6d88-170">Next steps</span></span>

[<span data-ttu-id="c6d88-171">Een functie-mogelijkheidsprofiel maken</span><span class="sxs-lookup"><span data-stu-id="c6d88-171">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="c6d88-172">Een configuratie bestand voor de sessie maken</span><span class="sxs-lookup"><span data-stu-id="c6d88-172">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="c6d88-173">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c6d88-173">See also</span></span>

[<span data-ttu-id="c6d88-174">WinRM-beveiliging</span><span class="sxs-lookup"><span data-stu-id="c6d88-174">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="c6d88-175">Power shell ♥ het blauwe team</span><span class="sxs-lookup"><span data-stu-id="c6d88-175">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
