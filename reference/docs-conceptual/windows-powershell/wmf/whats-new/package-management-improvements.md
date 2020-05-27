---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installeren
title: Verbeteringen van pakketbeheer in WMF 5.1
ms.openlocfilehash: 59f76562f4d0e9ef5f50ff94f04f2eb540d39f18
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810636"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="4553e-103">Verbeteringen van pakketbeheer in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="4553e-103">Improvements to Package Management in WMF 5.1</span></span>

<span data-ttu-id="4553e-104">De volgende correcties zijn aangebracht in de WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="4553e-104">The following are the fixes made in the WMF 5.1:</span></span>

## <a name="version-alias"></a><span data-ttu-id="4553e-105">Versie alias</span><span class="sxs-lookup"><span data-stu-id="4553e-105">Version Alias</span></span>

<span data-ttu-id="4553e-106">**Scenario**: als u versie 1,0 en 2,0 van een pakket, P1, op uw systeem hebt geïnstalleerd en u versie 1,0 wilt verwijderen, moet u `Uninstall-Package -Name P1 -Version 1.0` de installatie van versie 1,0 ongedaan maken na het uitvoeren van de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4553e-106">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="4553e-107">Het resultaat is echter dat versie 2,0 wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="4553e-107">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="4553e-108">Dit komt doordat de `-Version` para meter een alias van de `-MinimumVersion` para meter is.</span><span class="sxs-lookup"><span data-stu-id="4553e-108">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="4553e-109">Wanneer Package Management zoekt naar een gekwalificeerd pakket met de minimale versie van 1,0, wordt de meest recente versie geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="4553e-109">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="4553e-110">Dit gedrag wordt in normale gevallen verwacht, omdat het zoeken naar de meest recente versie doorgaans het gewenste resultaat is.</span><span class="sxs-lookup"><span data-stu-id="4553e-110">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="4553e-111">Het mag echter niet worden toegepast op de `Uninstall-Package` aanvraag.</span><span class="sxs-lookup"><span data-stu-id="4553e-111">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="4553e-112">**Oplossing**: `-Version` alias volledig verwijderd uit Package Management (ook</span><span class="sxs-lookup"><span data-stu-id="4553e-112">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="4553e-113">OneGet) en PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="4553e-113">OneGet) and PowerShellGet.</span></span>

## <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="4553e-114">Meerdere prompts voor het Boots trappen van de NuGet-provider</span><span class="sxs-lookup"><span data-stu-id="4553e-114">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="4553e-115">**Scenario**: wanneer u `Find-Module` of een `Install-Module` andere Package Management-cmdlets voor de eerste keer uitvoert op uw computer, probeert Package Management de NuGet-provider te Boots trapn.</span><span class="sxs-lookup"><span data-stu-id="4553e-115">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="4553e-116">Dit komt omdat de PowerShellGet-provider ook de NuGet-provider gebruikt voor het downloaden van Power shell-modules.</span><span class="sxs-lookup"><span data-stu-id="4553e-116">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span>
<span data-ttu-id="4553e-117">Package Management vraagt de gebruiker vervolgens om toestemming om de NuGet-provider te installeren.</span><span class="sxs-lookup"><span data-stu-id="4553e-117">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="4553e-118">Nadat de gebruiker Ja voor de Boots trapping heeft geselecteerd, wordt de meest recente versie van de NuGet-provider geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="4553e-118">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="4553e-119">In sommige gevallen, wanneer u een oude versie van de NuGet-provider op uw computer hebt geïnstalleerd, wordt de oudere versie van NuGet soms eerst geladen in de Power shell-sessie (dat is de race voorwaarde in Package Management).</span><span class="sxs-lookup"><span data-stu-id="4553e-119">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="4553e-120">PowerShellGet vereist echter dat de nieuwere versie van de NuGet-provider werkt. PowerShellGet vraagt package management om de NuGet-provider opnieuw aan te bootslen.</span><span class="sxs-lookup"><span data-stu-id="4553e-120">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span>
<span data-ttu-id="4553e-121">Dit resulteert in meerdere prompts voor het Boots trappen van de NuGet-provider.</span><span class="sxs-lookup"><span data-stu-id="4553e-121">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="4553e-122">**Oplossing**: in WMF 5.1 laadt Package Management de nieuwste versie van de NuGet-provider om te voor komen dat er meerdere prompts worden gevraagd om de NuGet-provider te Boots trappen.</span><span class="sxs-lookup"><span data-stu-id="4553e-122">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="4553e-123">U kunt dit probleem ook omzeilen door de oude versie van de NuGet-provider (NuGet-Anycpu. exe) hand matig te verwijderen als deze bestaat uit $env:P rogramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies</span><span class="sxs-lookup"><span data-stu-id="4553e-123">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>

## <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="4553e-124">Ondersteuning voor Package Management op computers met alleen intranet toegang</span><span class="sxs-lookup"><span data-stu-id="4553e-124">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="4553e-125">**Scenario**: voor het scenario van een onderneming werken mensen onder een omgeving waarin er geen Internet toegang is, maar alleen intranet.</span><span class="sxs-lookup"><span data-stu-id="4553e-125">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="4553e-126">Package Management biedt geen ondersteuning voor dit probleem in WMF 5,0.</span><span class="sxs-lookup"><span data-stu-id="4553e-126">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="4553e-127">**Scenario**: In WMF 5,0 heeft Package Management geen ondersteuning voor computers die toegang hebben tot een intranet (maar niet van Internet).</span><span class="sxs-lookup"><span data-stu-id="4553e-127">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="4553e-128">**Oplossing**: In WMF 5,1 kunt u de volgende stappen volgen om intranet computers toe te staan package management te gebruiken:</span><span class="sxs-lookup"><span data-stu-id="4553e-128">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="4553e-129">Down load de NuGet-provider met behulp van een andere computer met een Internet verbinding `Install-PackageProvider -Name NuGet` .</span><span class="sxs-lookup"><span data-stu-id="4553e-129">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="4553e-130">Zoek de NuGet-provider onder ofwel `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` of `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget` .</span><span class="sxs-lookup"><span data-stu-id="4553e-130">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="4553e-131">Kopieer de binaire bestanden naar een map of netwerk share locatie waartoe de intranet computer toegang heeft en installeer vervolgens de NuGet-provider met `Install-PackageProvider -Name NuGet -Source <Path to folder>` .</span><span class="sxs-lookup"><span data-stu-id="4553e-131">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>

## <a name="event-logging-improvements"></a><span data-ttu-id="4553e-132">Verbeteringen in gebeurtenis logboek registratie</span><span class="sxs-lookup"><span data-stu-id="4553e-132">Event logging improvements</span></span>

<span data-ttu-id="4553e-133">Wanneer u pakketten installeert, wijzigt u de status van de computer.</span><span class="sxs-lookup"><span data-stu-id="4553e-133">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="4553e-134">In WMF 5,1 registreert package management nu gebeurtenissen in het Windows-gebeurtenis logboek voor `Install-Package` , `Uninstall-Package` en- `Save-Package` activiteiten.</span><span class="sxs-lookup"><span data-stu-id="4553e-134">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="4553e-135">Het gebeurtenis logboek is hetzelfde als voor Power shell, dat wil zeggen `Microsoft-Windows-PowerShell, Operational` .</span><span class="sxs-lookup"><span data-stu-id="4553e-135">The Event log is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

## <a name="support-for-basic-authentication"></a><span data-ttu-id="4553e-136">Ondersteuning voor basis verificatie</span><span class="sxs-lookup"><span data-stu-id="4553e-136">Support for basic authentication</span></span>

<span data-ttu-id="4553e-137">In WMF 5,1 biedt package management ondersteuning voor het zoeken en installeren van pakketten van een opslag plaats waarvoor basis verificatie is vereist.</span><span class="sxs-lookup"><span data-stu-id="4553e-137">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="4553e-138">U kunt uw referenties voor de `Find-Package` `Install-Package` cmdlets en opgeven.</span><span class="sxs-lookup"><span data-stu-id="4553e-138">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="4553e-139">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4553e-139">For example:</span></span>

```powershell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

## <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="4553e-140">Ondersteuning voor het gebruik van Package Management achter een proxy</span><span class="sxs-lookup"><span data-stu-id="4553e-140">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="4553e-141">In WMF 5,1 maakt package management nu nieuwe proxy parameters `-ProxyCredential` en `-Proxy` .</span><span class="sxs-lookup"><span data-stu-id="4553e-141">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="4553e-142">Met deze para meters kunt u de proxy-URL en referenties voor Package Management-cmdlets opgeven.</span><span class="sxs-lookup"><span data-stu-id="4553e-142">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="4553e-143">Standaard worden systeem proxy instellingen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="4553e-143">By default, system proxy settings are used.</span></span> <span data-ttu-id="4553e-144">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="4553e-144">For example:</span></span>

```powershell
Find-Package -Source https://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```