---
ms.date: 07/10/2019
keywords: jea, powershell, beveiliging
title: JEA-vereisten
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734294"
---
# <a name="prerequisites"></a><span data-ttu-id="05381-103">Vereisten</span><span class="sxs-lookup"><span data-stu-id="05381-103">Prerequisites</span></span>

<span data-ttu-id="05381-104">Just Enough Administration is een functie die is opgenomen in PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="05381-104">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="05381-105">Dit artikel beschrijft de vereisten waaraan moeten worden voldaan aan de slag met JEA.</span><span class="sxs-lookup"><span data-stu-id="05381-105">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>


## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="05381-106">Controleren welke versie van PowerShell is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="05381-106">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="05381-107">Als u wilt controleren welke versie van PowerShell is geïnstalleerd op uw systeem, Controleer de `$PSVersionTable` variabele in een Windows PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="05381-107">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="05381-108">JEA is beschikbaar met PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="05381-108">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="05381-109">Voor de volledige functionaliteit, wordt het aanbevolen dat u de meest recente versie van PowerShell beschikbaar voor uw systeem installeert.</span><span class="sxs-lookup"><span data-stu-id="05381-109">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="05381-110">De volgende tabel beschrijft de beschikbaarheid van JEA op Windows Server:</span><span class="sxs-lookup"><span data-stu-id="05381-110">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="05381-111">Server-besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="05381-111">Server Operating System</span></span> |                <span data-ttu-id="05381-112">JEA-beschikbaarheid</span><span class="sxs-lookup"><span data-stu-id="05381-112">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="05381-113">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="05381-113">Windows Server 2016+</span></span>    | <span data-ttu-id="05381-114">Vooraf is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="05381-114">Preinstalled</span></span>                                   |
| <span data-ttu-id="05381-115">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="05381-115">Windows Server 2012 R2</span></span>  | <span data-ttu-id="05381-116">Volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="05381-116">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="05381-117">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="05381-117">Windows Server 2012</span></span>     | <span data-ttu-id="05381-118">Volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="05381-118">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="05381-119">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="05381-119">Windows Server 2008 R2</span></span>  | <span data-ttu-id="05381-120">Verminderde functionaliteit<sup>1</sup> met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="05381-120">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="05381-121">U kunt ook JEA gebruiken op uw computer thuis of werk:</span><span class="sxs-lookup"><span data-stu-id="05381-121">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="05381-122">Client-besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="05381-122">Client Operating System</span></span> |                   <span data-ttu-id="05381-123">JEA-beschikbaarheid</span><span class="sxs-lookup"><span data-stu-id="05381-123">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="05381-124">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="05381-124">Windows 10 1607+</span></span>        | <span data-ttu-id="05381-125">Vooraf is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="05381-125">Preinstalled</span></span>                                         |
| <span data-ttu-id="05381-126">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="05381-126">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="05381-127">Vooraf is geïnstalleerd, met verminderde functionaliteit<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="05381-127">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="05381-128">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="05381-128">Windows 10 1507</span></span>         | <span data-ttu-id="05381-129">Niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="05381-129">Not available</span></span>                                        |
| <span data-ttu-id="05381-130">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="05381-130">Windows 8, 8.1</span></span>          | <span data-ttu-id="05381-131">Volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="05381-131">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="05381-132">Windows 7</span><span class="sxs-lookup"><span data-stu-id="05381-132">Windows 7</span></span>               | <span data-ttu-id="05381-133">Verminderde functionaliteit<sup>1</sup> met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="05381-133">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="05381-134"><sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van de groep beheerde serviceaccounts op Windows Server 2008 R2 of Windows 7.</span><span class="sxs-lookup"><span data-stu-id="05381-134"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="05381-135">Virtuele accounts en andere functies JEA *zijn* ondersteund.</span><span class="sxs-lookup"><span data-stu-id="05381-135">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="05381-136"><sup>2</sup> de volgende JEA-functies worden niet ondersteund op Windows 10 versie 1511 en 1603:</span><span class="sxs-lookup"><span data-stu-id="05381-136"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="05381-137">Service wordt uitgevoerd als een groep beheerd serviceaccount</span><span class="sxs-lookup"><span data-stu-id="05381-137">Running as a group-managed service account</span></span>
  - <span data-ttu-id="05381-138">Regels voor voorwaardelijke toegang in sessieconfiguraties</span><span class="sxs-lookup"><span data-stu-id="05381-138">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="05381-139">De schijf van de gebruiker</span><span class="sxs-lookup"><span data-stu-id="05381-139">The user drive</span></span>
  - <span data-ttu-id="05381-140">Verlenen van toegang tot lokale gebruikersaccounts</span><span class="sxs-lookup"><span data-stu-id="05381-140">Granting access to local user accounts</span></span>

  <span data-ttu-id="05381-141">Voor ondersteuning voor deze functies kunt bijwerken van Windows naar versie 1607 (Jubileumupdate) of hoger.</span><span class="sxs-lookup"><span data-stu-id="05381-141">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="05381-142">Installeer Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="05381-142">Install Windows Management Framework</span></span>

<span data-ttu-id="05381-143">Als u een oudere versie van PowerShell uitvoert, moet u mogelijk uw systeem bijwerken met de meest recente update van Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="05381-143">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="05381-144">Zie voor meer informatie de [WMF documentatie](/powershell/wmf/overview).</span><span class="sxs-lookup"><span data-stu-id="05381-144">For more information, see the [WMF documentation](/powershell/wmf/overview).</span></span>

<span data-ttu-id="05381-145">Het raadzaam dat u de compatibiliteit van uw workload met WMF testen vóór de upgrade van al uw servers.</span><span class="sxs-lookup"><span data-stu-id="05381-145">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="05381-146">Gebruikers van Windows 10 moeten de nieuwste functie-updates voor het ophalen van de huidige versie van Windows PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="05381-146">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="05381-147">Externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="05381-147">Enable PowerShell Remoting</span></span>

<span data-ttu-id="05381-148">Externe communicatie van PowerShell vormt de basis waarop JEA is gebouwd.</span><span class="sxs-lookup"><span data-stu-id="05381-148">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="05381-149">Het is noodzakelijk om ervoor te zorgen voor externe communicatie van PowerShell is ingeschakeld en naar behoren zijn beveiligd voordat u de JEA kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="05381-149">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="05381-150">Zie voor meer informatie, [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span><span class="sxs-lookup"><span data-stu-id="05381-150">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="05381-151">Externe communicatie van PowerShell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016.</span><span class="sxs-lookup"><span data-stu-id="05381-151">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="05381-152">U kunt PowerShell voor externe toegang inschakelen door het uitvoeren van de volgende opdracht uit in een PowerShell-venster met verhoogde bevoegdheid.</span><span class="sxs-lookup"><span data-stu-id="05381-152">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="05381-153">PowerShell-module en (optioneel) script blok-logboekregistratie inschakelen</span><span class="sxs-lookup"><span data-stu-id="05381-153">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="05381-154">De volgende stappen schakelt logboekregistratie voor alle PowerShell-bewerkingen op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="05381-154">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="05381-155">Logboekregistratie van PowerShell-Module is niet vereist voor JEA, maar het wordt aangeraden u logboekregistratie om te controleren of de gebruikers opdrachten uitvoeren inschakelen bent aangemeld op een centrale locatie.</span><span class="sxs-lookup"><span data-stu-id="05381-155">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="05381-156">U kunt het beleid voor logboekregistratie van PowerShell-Module met behulp van Groepsbeleid configureren.</span><span class="sxs-lookup"><span data-stu-id="05381-156">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="05381-157">Open de Editor voor lokaal groepsbeleid op een werkstation of een Group Policy Object in de Console Groepsbeleidsbeheer op een Active Directory-domeincontroller</span><span class="sxs-lookup"><span data-stu-id="05381-157">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="05381-158">Navigeer naar **Computerconfiguratie\\Beheersjablonen\\Windows-onderdelen\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="05381-158">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="05381-159">Dubbelklik op **Module logboekregistratie inschakelen**</span><span class="sxs-lookup"><span data-stu-id="05381-159">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="05381-160">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="05381-160">Click **Enabled**</span></span>
5. <span data-ttu-id="05381-161">Klik in de sectie opties op **weergeven** naast modulenamen</span><span class="sxs-lookup"><span data-stu-id="05381-161">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="05381-162">Type `*` in het pop-upvenster om aan te melden opdrachten van alle modules.</span><span class="sxs-lookup"><span data-stu-id="05381-162">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="05381-163">Klik op **OK** om in te stellen van het beleid</span><span class="sxs-lookup"><span data-stu-id="05381-163">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="05381-164">Dubbelklik op **PowerShell-Script-blok logboekregistratie inschakelen**</span><span class="sxs-lookup"><span data-stu-id="05381-164">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="05381-165">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="05381-165">Click **Enabled**</span></span>
10. <span data-ttu-id="05381-166">Klik op **OK** om in te stellen van het beleid</span><span class="sxs-lookup"><span data-stu-id="05381-166">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="05381-167">(Op domein machines alleen) Voer `gpupdate` of wacht totdat Groepsbeleid voor het verwerken van het bijgewerkte beleid en de instellingen toepassen</span><span class="sxs-lookup"><span data-stu-id="05381-167">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="05381-168">U kunt ook systeembrede PowerShell transcriptie via Groepsbeleid inschakelen.</span><span class="sxs-lookup"><span data-stu-id="05381-168">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="05381-169">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="05381-169">Next steps</span></span>

[<span data-ttu-id="05381-170">Maak een bestand van de mogelijkheid rol</span><span class="sxs-lookup"><span data-stu-id="05381-170">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="05381-171">Een sessie-configuratiebestand maken</span><span class="sxs-lookup"><span data-stu-id="05381-171">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="05381-172">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05381-172">See also</span></span>

[<span data-ttu-id="05381-173">WinRM-beveiliging</span><span class="sxs-lookup"><span data-stu-id="05381-173">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="05381-174">PowerShell ♥ het Blue Team</span><span class="sxs-lookup"><span data-stu-id="05381-174">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
