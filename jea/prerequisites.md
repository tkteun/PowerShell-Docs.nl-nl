---
ms.date: 06/12/2017
keywords: jea, powershell, beveiliging
title: JEA-vereisten
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688355"
---
# <a name="prerequisites"></a><span data-ttu-id="37350-103">Vereisten</span><span class="sxs-lookup"><span data-stu-id="37350-103">Prerequisites</span></span>

> <span data-ttu-id="37350-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="37350-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="37350-105">Just Enough Administration is een functie die wordt geleverd met Windows PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="37350-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="37350-106">Dit onderwerp beschrijft de vereisten waaraan moeten worden voldaan om te starten met behulp van JEA.</span><span class="sxs-lookup"><span data-stu-id="37350-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="37350-107">Installeren van JEA</span><span class="sxs-lookup"><span data-stu-id="37350-107">Install JEA</span></span>

<span data-ttu-id="37350-108">JEA is beschikbaar met Windows PowerShell 5.0 en hoger, maar voor de volledige functionaliteit is het raadzaam dat u de meest recente versie van PowerShell beschikbaar voor uw systeem installeert.</span><span class="sxs-lookup"><span data-stu-id="37350-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="37350-109">De volgende tabel beschrijft de beschikbaarheid van JEA op Windows Server:</span><span class="sxs-lookup"><span data-stu-id="37350-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="37350-110">Server-besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="37350-110">Server Operating System</span></span>   | <span data-ttu-id="37350-111">JEA-beschikbaarheid</span><span class="sxs-lookup"><span data-stu-id="37350-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="37350-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="37350-112">Windows Server 2016</span></span>       | <span data-ttu-id="37350-113">Vooraf is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="37350-113">Preinstalled</span></span>
<span data-ttu-id="37350-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="37350-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="37350-115">Volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="37350-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="37350-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="37350-116">Windows Server 2012</span></span>       | <span data-ttu-id="37350-117">Volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="37350-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="37350-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="37350-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="37350-119">Verminderde functionaliteit<sup>1</sup> met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="37350-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="37350-120">U kunt ook JEA gebruiken op uw computer thuis of werk:</span><span class="sxs-lookup"><span data-stu-id="37350-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="37350-121">Client-besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="37350-121">Client Operating System</span></span>   | <span data-ttu-id="37350-122">JEA-beschikbaarheid</span><span class="sxs-lookup"><span data-stu-id="37350-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="37350-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="37350-123">Windows 10 1607+</span></span>          | <span data-ttu-id="37350-124">Vooraf is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="37350-124">Preinstalled</span></span>
<span data-ttu-id="37350-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="37350-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="37350-126">Vooraf is geïnstalleerd, met verminderde functionaliteit<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="37350-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="37350-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="37350-127">Windows 10 1507</span></span>           | <span data-ttu-id="37350-128">Niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="37350-128">Not available</span></span>
<span data-ttu-id="37350-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="37350-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="37350-130">Volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="37350-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="37350-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="37350-131">Windows 7</span></span>                 | <span data-ttu-id="37350-132">Verminderde functionaliteit<sup>1</sup> met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="37350-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="37350-133"><sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van door groepen beheerde serviceaccounts in Windows Server 2008 R2 of Windows 7.</span><span class="sxs-lookup"><span data-stu-id="37350-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="37350-134">Virtuele accounts en andere functies JEA *zijn* ondersteund.</span><span class="sxs-lookup"><span data-stu-id="37350-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="37350-135"><sup>2</sup> Windows 10 versie 1511 en 1603 bieden geen ondersteuning voor de volgende functies van JEA: uitgevoerd als een groep beheerd serviceaccount, de regels voor voorwaardelijke toegang in sessieconfiguraties, de schijf van de gebruiker en het verlenen van toegang voor lokale gebruikersaccounts.</span><span class="sxs-lookup"><span data-stu-id="37350-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="37350-136">Voor ondersteuning voor deze functies kunt bijwerken van Windows naar versie 1607 (Jubileumupdate) of hoger.</span><span class="sxs-lookup"><span data-stu-id="37350-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="37350-137">Controleren welke versie van PowerShell is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="37350-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="37350-138">Als u wilt controleren welke versie van PowerShell is geïnstalleerd op uw systeem, Controleer de `$PSVersionTable` variabele in een Windows PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="37350-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="37350-139">U bent klaar voor gebruik van JEA als de *belangrijke* versie is gelijk aan of groter zijn dan **5**.</span><span class="sxs-lookup"><span data-stu-id="37350-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="37350-140">Voor de beste ervaring en toegang hebben tot de nieuwste functies, is het raadzaam dat u een naar PowerShell-versie upgrade **5.1** indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="37350-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="37350-141">Installeer Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="37350-141">Install Windows Management Framework</span></span>

<span data-ttu-id="37350-142">Als u een oudere versie van PowerShell uitvoert, moet u uw systeem bijwerken met de meest recente update van Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="37350-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="37350-143">-Updatepakketten en een koppeling naar de meest recente releaseopmerkingen van WMF zijn beschikbaar in de [Downloadcentrum](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span><span class="sxs-lookup"><span data-stu-id="37350-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span></span>

<span data-ttu-id="37350-144">Het is raadzaam dat u de compatibiliteit van uw workload met WMF testen vóór de upgrade van al uw servers.</span><span class="sxs-lookup"><span data-stu-id="37350-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="37350-145">Gebruikers van Windows 10 moeten de nieuwste functie-updates voor het ophalen van de huidige versie van Windows PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="37350-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="37350-146">Externe communicatie met PowerShell</span><span class="sxs-lookup"><span data-stu-id="37350-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="37350-147">Externe communicatie van PowerShell vormt de basis waarop JEA is gebouwd.</span><span class="sxs-lookup"><span data-stu-id="37350-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="37350-148">Het is daarom noodzakelijk voor externe communicatie van PowerShell is ingeschakeld en [goed beveiligde](/powershell/scripting/setup/winrmsecurity) op uw systeem voordat u de JEA kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="37350-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="37350-149">Externe communicatie van PowerShell is standaard ingeschakeld op Windows Server 2012, 2012 R2 en 2016.</span><span class="sxs-lookup"><span data-stu-id="37350-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="37350-150">U kunt PowerShell voor externe toegang inschakelen door het uitvoeren van de volgende opdracht uit in een PowerShell-venster met verhoogde bevoegdheid.</span><span class="sxs-lookup"><span data-stu-id="37350-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="37350-151">PowerShell-module en (optioneel) script blok-logboekregistratie inschakelen</span><span class="sxs-lookup"><span data-stu-id="37350-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="37350-152">De volgende stappen schakelt logboekregistratie voor alle PowerShell-bewerkingen op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="37350-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="37350-153">Logboekregistratie van PowerShell-Module is niet vereist voor JEA, maar het is raadzaam dat u deze inschakelen om te controleren of de gebruikers opdrachten uitvoeren op een centrale locatie worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="37350-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="37350-154">U kunt het beleid voor logboekregistratie van PowerShell-Module met behulp van Groepsbeleid configureren.</span><span class="sxs-lookup"><span data-stu-id="37350-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="37350-155">Open de Editor voor lokaal groepsbeleid op een werkstation of een Group Policy Object in de Console Groepsbeleidsbeheer op een Active Directory-domeincontroller</span><span class="sxs-lookup"><span data-stu-id="37350-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="37350-156">Navigeer naar **Computerconfiguratie\\Beheersjablonen\\Windows-onderdelen\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="37350-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="37350-157">Dubbelklik op **Module logboekregistratie kunnen inschakelen**</span><span class="sxs-lookup"><span data-stu-id="37350-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="37350-158">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="37350-158">Click **Enabled**</span></span>
5. <span data-ttu-id="37350-159">Klik in de sectie opties op **weergeven** naast modulenamen</span><span class="sxs-lookup"><span data-stu-id="37350-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="37350-160">Type `\*` in het pop-upvenster.</span><span class="sxs-lookup"><span data-stu-id="37350-160">Type `\*` in the pop up window.</span></span> <span data-ttu-id="37350-161">Dit Hiermee geeft u PowerShell om aan te melden opdrachten van alle modules.</span><span class="sxs-lookup"><span data-stu-id="37350-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="37350-162">Klik op **OK** om in te stellen van het beleid</span><span class="sxs-lookup"><span data-stu-id="37350-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="37350-163">Dubbelklik op **PowerShell-Script blok logboekregistratie kunnen inschakelen**</span><span class="sxs-lookup"><span data-stu-id="37350-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="37350-164">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="37350-164">Click **Enabled**</span></span>
10. <span data-ttu-id="37350-165">Klik op **OK** om in te stellen van het beleid</span><span class="sxs-lookup"><span data-stu-id="37350-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="37350-166">(Op domein machines alleen) Voer `gpupdate` of wacht totdat Groepsbeleid voor het verwerken van het bijgewerkte beleid en de instellingen toepassen</span><span class="sxs-lookup"><span data-stu-id="37350-166">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="37350-167">U kunt ook systeembrede PowerShell transcriptie via Groepsbeleid inschakelen.</span><span class="sxs-lookup"><span data-stu-id="37350-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="37350-168">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="37350-168">Next steps</span></span>

[<span data-ttu-id="37350-169">Maak een bestand van de mogelijkheid rol</span><span class="sxs-lookup"><span data-stu-id="37350-169">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="37350-170">Een sessie-configuratiebestand maken</span><span class="sxs-lookup"><span data-stu-id="37350-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="37350-171">Zie ook</span><span class="sxs-lookup"><span data-stu-id="37350-171">See also</span></span>

[<span data-ttu-id="37350-172">Als u meer informatie over de beveiliging van PowerShell voor externe toegang en WinRM</span><span class="sxs-lookup"><span data-stu-id="37350-172">Additional information about PowerShell Remoting and WinRM security</span></span>](/powershell/scripting/setup/winrmsecurity)

[<span data-ttu-id="37350-173">*PowerShell ♥ het Blue Team* blogbericht over beveiliging</span><span class="sxs-lookup"><span data-stu-id="37350-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)