---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea powershell beveiliging
title: JEA vereisten
ms.openlocfilehash: 92a74d89a0e982e9f45e69d92b261756de33c038
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="prerequisites"></a><span data-ttu-id="97c53-103">Vereisten</span><span class="sxs-lookup"><span data-stu-id="97c53-103">Prerequisites</span></span>

> <span data-ttu-id="97c53-104">Van toepassing op: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="97c53-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="97c53-105">Net genoeg Administration is een functie met Windows PowerShell 5.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="97c53-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="97c53-106">Dit onderwerp beschrijft de vereisten waaraan moeten worden voldaan om te beginnen met behulp van JEA.</span><span class="sxs-lookup"><span data-stu-id="97c53-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="97c53-107">JEA installeren</span><span class="sxs-lookup"><span data-stu-id="97c53-107">Install JEA</span></span>

<span data-ttu-id="97c53-108">JEA is beschikbaar met Windows PowerShell 5.0 en hoger, maar voor de volledige functionaliteit wordt aanbevolen dat u de nieuwste versie van PowerShell beschikbaar voor uw systeem installeert.</span><span class="sxs-lookup"><span data-stu-id="97c53-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="97c53-109">De volgende tabel beschrijft de beschikbaarheid van JEA op Windows Server:</span><span class="sxs-lookup"><span data-stu-id="97c53-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="97c53-110">Server-besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="97c53-110">Server Operating System</span></span>   | <span data-ttu-id="97c53-111">JEA beschikbaarheid</span><span class="sxs-lookup"><span data-stu-id="97c53-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="97c53-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="97c53-112">Windows Server 2016</span></span>       | <span data-ttu-id="97c53-113">Vooraf geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="97c53-113">Preinstalled</span></span>
<span data-ttu-id="97c53-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="97c53-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="97c53-115">De volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97c53-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="97c53-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="97c53-116">Windows Server 2012</span></span>       | <span data-ttu-id="97c53-117">De volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97c53-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="97c53-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="97c53-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="97c53-119">Verminderde functionaliteit<sup>1</sup> met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97c53-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="97c53-120">U kunt ook JEA gebruiken op uw computer thuisnetwerk of:</span><span class="sxs-lookup"><span data-stu-id="97c53-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="97c53-121">Client-besturingssysteem</span><span class="sxs-lookup"><span data-stu-id="97c53-121">Client Operating System</span></span>   | <span data-ttu-id="97c53-122">JEA beschikbaarheid</span><span class="sxs-lookup"><span data-stu-id="97c53-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="97c53-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="97c53-123">Windows 10 1607+</span></span>          | <span data-ttu-id="97c53-124">Vooraf geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="97c53-124">Preinstalled</span></span>
<span data-ttu-id="97c53-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="97c53-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="97c53-126">Vooraf is geïnstalleerd, met verminderde functionaliteit<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="97c53-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="97c53-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="97c53-127">Windows 10 1507</span></span>           | <span data-ttu-id="97c53-128">Niet beschikbaar</span><span class="sxs-lookup"><span data-stu-id="97c53-128">Not available</span></span>
<span data-ttu-id="97c53-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="97c53-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="97c53-130">De volledige functionaliteit met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97c53-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="97c53-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="97c53-131">Windows 7</span></span>                 | <span data-ttu-id="97c53-132">Verminderde functionaliteit<sup>1</sup> met WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="97c53-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="97c53-133"><sup>1</sup> JEA kan niet worden geconfigureerd voor het gebruik van beheerde serviceaccounts voor groepen op Windows Server 2008 R2 of Windows 7.</span><span class="sxs-lookup"><span data-stu-id="97c53-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="97c53-134">Virtuele accounts en andere functies JEA *zijn* ondersteund.</span><span class="sxs-lookup"><span data-stu-id="97c53-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="97c53-135"><sup>2</sup> Windows 10 versie 1511 en 1603 bieden geen ondersteuning voor de volgende functies van JEA: uitgevoerd als een groep beheerd serviceaccount, regels voor voorwaardelijke toegang in sessieconfiguraties, de schijf van de gebruiker en het verlenen van toegang aan lokale gebruikersaccounts.</span><span class="sxs-lookup"><span data-stu-id="97c53-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="97c53-136">Als u ondersteuning voor deze functies, Windows bijwerken naar versie 1607 (Verjaardag bijwerken) of hoger.</span><span class="sxs-lookup"><span data-stu-id="97c53-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="97c53-137">Controleren welke versie van PowerShell is geïnstalleerd</span><span class="sxs-lookup"><span data-stu-id="97c53-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="97c53-138">Als u wilt controleren welke versie van PowerShell is geïnstalleerd op uw systeem, Controleer de `$PSVersionTable` variabele in een Windows PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="97c53-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
PS C:\> $PSVersionTable.PSVersion

Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="97c53-139">Bent u klaar voor gebruik van JEA als de *belangrijke* versie is groter dan of gelijk aan **5**.</span><span class="sxs-lookup"><span data-stu-id="97c53-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="97c53-140">Voor de beste ervaring, en toegang hebben tot de nieuwste functies, is het raadzaam dat u een naar de PowerShell-versie upgrade **5.1** indien mogelijk.</span><span class="sxs-lookup"><span data-stu-id="97c53-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="97c53-141">Installeer Windows Management Framework</span><span class="sxs-lookup"><span data-stu-id="97c53-141">Install Windows Management Framework</span></span>

<span data-ttu-id="97c53-142">Als u een oudere versie van PowerShell uitvoert, moet u uw systeem bijwerken met de nieuwste update van Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="97c53-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="97c53-143">Updatepakketten en een koppeling naar de meest recente release-opmerkingen van WMF zijn beschikbaar in de [Downloadcentrum](https://aka.ms/WMF5).</span><span class="sxs-lookup"><span data-stu-id="97c53-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://aka.ms/WMF5).</span></span>

<span data-ttu-id="97c53-144">Het is raadzaam dat u de compatibiliteit van uw workload met WMF test vóór de upgrade van al uw servers.</span><span class="sxs-lookup"><span data-stu-id="97c53-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="97c53-145">Windows 10-gebruikers moeten de meest recente updates van de functie voor het ophalen van de huidige versie van Windows PowerShell installeren.</span><span class="sxs-lookup"><span data-stu-id="97c53-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="97c53-146">PowerShell op afstand inschakelen</span><span class="sxs-lookup"><span data-stu-id="97c53-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="97c53-147">Externe communicatie van PowerShell vormt de basis waarop JEA is gebouwd.</span><span class="sxs-lookup"><span data-stu-id="97c53-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="97c53-148">Het is daarom nodig om te controleren of externe communicatie van PowerShell is ingeschakeld en [goed beveiligde](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) op uw systeem voordat u JEA kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="97c53-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="97c53-149">Externe communicatie van PowerShell is standaard ingeschakeld op Windows Server 2012 en 2012 R2 2016.</span><span class="sxs-lookup"><span data-stu-id="97c53-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="97c53-150">U kunt PowerShell voor externe toegang inschakelen door de volgende opdracht in een PowerShell-venster met verhoogde bevoegdheid.</span><span class="sxs-lookup"><span data-stu-id="97c53-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="97c53-151">PowerShell-module en script blok logboekregistratie (optioneel) inschakelen</span><span class="sxs-lookup"><span data-stu-id="97c53-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="97c53-152">De volgende stappen schakelt logboekregistratie in voor alle PowerShell-acties op uw systeem.</span><span class="sxs-lookup"><span data-stu-id="97c53-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="97c53-153">Logboekregistratie van PowerShell-Module is niet vereist voor JEA, maar het wordt ten zeerste aangeraden dat u deze inschakelen om te controleren of de gebruikers opdrachten uitvoeren op een centrale locatie worden geregistreerd.</span><span class="sxs-lookup"><span data-stu-id="97c53-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="97c53-154">U kunt de PowerShell-Module logboekregistratie beleid via Groepsbeleid configureren.</span><span class="sxs-lookup"><span data-stu-id="97c53-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="97c53-155">Open de Editor voor lokaal groepsbeleid op een werkstation of a Group Policy Object in de Console Groepsbeleidsbeheer op een Active Directory-domeincontroller</span><span class="sxs-lookup"><span data-stu-id="97c53-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="97c53-156">Navigeer naar **Computerconfiguratie\\Beheersjablonen\\Windows-onderdelen\\Windows PowerShell**</span><span class="sxs-lookup"><span data-stu-id="97c53-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="97c53-157">Dubbelklik op **Module logboekregistratie inschakelen**</span><span class="sxs-lookup"><span data-stu-id="97c53-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="97c53-158">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="97c53-158">Click **Enabled**</span></span>
5. <span data-ttu-id="97c53-159">Klik in de sectie opties op **weergeven** naast de namen van Statusberichtmodule</span><span class="sxs-lookup"><span data-stu-id="97c53-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="97c53-160">Type '**\***' in het pop-upvenster.</span><span class="sxs-lookup"><span data-stu-id="97c53-160">Type "**\***" in the pop up window.</span></span> <span data-ttu-id="97c53-161">Dit geïnstrueerd PowerShell aan te melden opdrachten van alle modules.</span><span class="sxs-lookup"><span data-stu-id="97c53-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="97c53-162">Klik op **OK** aan het beleid instellen</span><span class="sxs-lookup"><span data-stu-id="97c53-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="97c53-163">Dubbelklik op **PowerShell Script blok logboekregistratie inschakelen**</span><span class="sxs-lookup"><span data-stu-id="97c53-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="97c53-164">Klik op **ingeschakeld**</span><span class="sxs-lookup"><span data-stu-id="97c53-164">Click **Enabled**</span></span>
10. <span data-ttu-id="97c53-165">Klik op **OK** aan het beleid instellen</span><span class="sxs-lookup"><span data-stu-id="97c53-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="97c53-166">(Op domein machines alleen) Voer **gpupdate** of wacht totdat Groepsbeleid voor het verwerken van het bijgewerkte beleid en de instellingen toepassen</span><span class="sxs-lookup"><span data-stu-id="97c53-166">(On domain-joined machines only) Run **gpupdate** or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="97c53-167">U kunt ook hele systeem PowerShell schrijffouten via Groepsbeleid inschakelen.</span><span class="sxs-lookup"><span data-stu-id="97c53-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="97c53-168">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="97c53-168">Next steps</span></span>

- [<span data-ttu-id="97c53-169">Maak een bestand van de mogelijkheid rol</span><span class="sxs-lookup"><span data-stu-id="97c53-169">Create a role capability file</span></span>](role-capabilities.md)
- [<span data-ttu-id="97c53-170">Een configuratiebestand sessie maken</span><span class="sxs-lookup"><span data-stu-id="97c53-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="97c53-171">Zie ook</span><span class="sxs-lookup"><span data-stu-id="97c53-171">See also</span></span>

- [<span data-ttu-id="97c53-172">Als u meer informatie over de beveiliging PowerShell voor externe toegang en WinRM</span><span class="sxs-lookup"><span data-stu-id="97c53-172">Additional information about PowerShell Remoting and WinRM security</span></span>](https://msdn.microsoft.com/powershell/scripting/setup/winrmsecurity)
- [<span data-ttu-id="97c53-173">*PowerShell ♥ het Team van blauw* blogbericht op beveiliging</span><span class="sxs-lookup"><span data-stu-id="97c53-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)