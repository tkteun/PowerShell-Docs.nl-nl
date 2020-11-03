---
description: Hierin worden de beperkingen van Windows Power Shell 4,0 op Windows RT 8,1 beschreven.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_rt?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_RT
ms.openlocfilehash: 323f06a7a0d8253417510503c1011ac02c20179f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252538"
---
# <a name="about-windows-rt"></a><span data-ttu-id="fbfa9-104">Over Windows RT</span><span class="sxs-lookup"><span data-stu-id="fbfa9-104">About Windows RT</span></span>

## <a name="short-description"></a><span data-ttu-id="fbfa9-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fbfa9-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="fbfa9-106">Hierin worden de beperkingen van Windows Power Shell 4,0 op Windows RT 8,1 beschreven.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-106">Explains limitations of  Windows PowerShell 4.0 on Windows RT 8.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="fbfa9-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="fbfa9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="fbfa9-108">Het Windows RT 8,1-besturings systeem is geïnstalleerd op computers en apparaten (zoals micro soft-Opper vlak 2, waarop het het besturings systeem is dat wordt geleverd bij de computer) die gebruikmaakt van Advanced RISC machine-processors (ARM).</span><span class="sxs-lookup"><span data-stu-id="fbfa9-108">The Windows RT 8.1 operating system is installed on computers and devices (such as Microsoft Surface 2, on which it is the operating system that ships with the computer) that use Advanced RISC Machine (ARM) processors.</span></span>

<span data-ttu-id="fbfa9-109">Windows Power Shell 4,0 is opgenomen in Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-109">Windows PowerShell 4.0 is included in Windows RT 8.1.</span></span> <span data-ttu-id="fbfa9-110">Alle cmdlets, providers en modules en de meeste scripts die zijn ontworpen voor Windows Power Shell 2,0 en latere versies, worden zonder wijzigingen uitgevoerd op Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-110">All cmdlets, providers, and modules, and most scripts designed for Windows PowerShell 2.0 and later releases run on Windows RT 8.1 without changes.</span></span>

<span data-ttu-id="fbfa9-111">Omdat Windows RT 8,1 niet alle Windows-onderdelen bevat, werken sommige Windows Power shell-onderdelen anders of werken ze niet op Windows RT-apparaten.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-111">Because Windows RT 8.1 does not include all Windows features, some Windows PowerShell features work differently or do not work on Windows RT-based devices.</span></span> <span data-ttu-id="fbfa9-112">In de volgende lijst worden de verschillen beschreven.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-112">The following list explains the differences.</span></span>

- <span data-ttu-id="fbfa9-113">Windows PowerShell ISE is niet opgenomen in en kan niet worden uitgevoerd op Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-113">Windows PowerShell ISE is not included in and cannot run on Windows RT 8.1.</span></span>
  <span data-ttu-id="fbfa9-114">Windows PowerShell ISE vereist Windows Presentation Foundation, dat niet is opgenomen in Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-114">Windows PowerShell ISE requires Windows Presentation Foundation, which is not included in Windows RT 8.1.</span></span>

- <span data-ttu-id="fbfa9-115">Externe communicatie van Windows Power shell en de WinRM-service zijn standaard uitgeschakeld.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-115">Windows PowerShell remoting and the WinRM service are disabled by default.</span></span>
  <span data-ttu-id="fbfa9-116">Als u externe toegang wilt inschakelen, voert u de Enable-PSRemoting-cmdlet uit.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-116">To enable remoting, run the Enable-PSRemoting cmdlet.</span></span> <span data-ttu-id="fbfa9-117">Voer ook de Set-Service-cmdlet uit om het opstart type van de WinRM-service in te stellen op automatisch of automatisch (vertraagd starten).</span><span class="sxs-lookup"><span data-stu-id="fbfa9-117">Also, run the Set-Service cmdlet to set the startup type of the WinRM service to Automatic, or Automatic (Delayed Start).</span></span>

  <span data-ttu-id="fbfa9-118">Externe toegang is uitgeschakeld, u kunt Windows Power shell Remoting gebruiken om opdrachten uit te voeren op andere computers, maar andere computers kunnen geen opdrachten uitvoeren op het Windows RT-apparaat.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-118">While remoting is disabled, you can use Windows PowerShell remoting to run commands on other computers, but other computers cannot run commands on the Windows RT device.</span></span> <span data-ttu-id="fbfa9-119">Ook wel impliciete externe communicatie, dat wil zeggen externe toegang die is ingebouwd in een cmdlet of script, en niet expliciet is aangevraagd met toegevoegde para meters</span><span class="sxs-lookup"><span data-stu-id="fbfa9-119">Also, implicit remoting - that is, remoting that is built in to a cmdlet or script, and not explicitly requested with added parameters</span></span>
  - <span data-ttu-id="fbfa9-120">werkt niet in Windows Power shell die wordt uitgevoerd op Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-120">does not work in Windows PowerShell running on Windows RT 8.1.</span></span>

- <span data-ttu-id="fbfa9-121">Computers die lid zijn van een domein en Kerberos-verificatie worden niet ondersteund in Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-121">Domain-joined computing and Kerberos authentication are not supported on Windows RT 8.1.</span></span> <span data-ttu-id="fbfa9-122">U kunt Windows Power shell niet gebruiken om deze functies toe te voegen of te beheren.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-122">You cannot use Windows PowerShell to add or manage these features.</span></span>

- <span data-ttu-id="fbfa9-123">Microsoft .NET Framework-klassen die niet worden ondersteund op Windows RT 8,1 worden ook niet ondersteund door Windows Power shell op Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-123">Microsoft .NET Framework classes that are not supported on Windows RT 8.1 are also not supported by Windows PowerShell on Windows RT 8.1.</span></span>

- <span data-ttu-id="fbfa9-124">Trans acties zijn niet ingeschakeld op Windows RT 8,1.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-124">Transactions are not enabled on Windows RT 8.1.</span></span> <span data-ttu-id="fbfa9-125">Trans actie-cmdlets, zoals start-trans actie en transactie parameters, zoals UseTransaction, werken niet goed.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-125">Transaction cmdlets, such as Start-Transaction, and transaction parameters, such as UseTransaction, do not work properly.</span></span>

- <span data-ttu-id="fbfa9-126">Alle Windows Power shell-sessies op Windows RT 8,1-apparaten gebruiken de ConstrainedLanguage taal modus.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-126">All Windows PowerShell sessions on Windows RT 8.1 devices use the ConstrainedLanguage language mode.</span></span> <span data-ttu-id="fbfa9-127">ConstrainedLanguage taal modus is een aanvulling op de code-integriteit van de gebruikers modus (UMCI).</span><span class="sxs-lookup"><span data-stu-id="fbfa9-127">ConstrainedLanguage language mode is a companion to User Mode Code Integrity (UMCI).</span></span> <span data-ttu-id="fbfa9-128">Alle Windows-cmdlets en Windows Power shell-taal elementen zijn toegestaan, maar typen worden beperkt om ervoor te zorgen dat gebruikers Windows Power shell niet kunnen gebruiken om de UMCI-beveiligingen te omzeilen of te schenden.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-128">It permits all Windows cmdlets and Windows PowerShell language elements, but restricts types to ensure that users cannot use Windows PowerShell to circumvent or violate the UMCI protections.</span></span>

<span data-ttu-id="fbfa9-129">Zie [about_Language_Modes](about_Language_Modes.md)voor meer informatie over de taal modus ConstrainedLanguage.</span><span class="sxs-lookup"><span data-stu-id="fbfa9-129">For more information about ConstrainedLanguage language mode, see [about_Language_Modes](about_Language_Modes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbfa9-130">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="fbfa9-130">SEE ALSO</span></span>

[<span data-ttu-id="fbfa9-131">about_Language_Modes</span><span class="sxs-lookup"><span data-stu-id="fbfa9-131">about_Language_Modes</span></span>](about_Language_Modes.md)

[<span data-ttu-id="fbfa9-132">about_Remote</span><span class="sxs-lookup"><span data-stu-id="fbfa9-132">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="fbfa9-133">about_Windows_PowerShell_ISE</span><span class="sxs-lookup"><span data-stu-id="fbfa9-133">about_Windows_PowerShell_ISE</span></span>](about_Windows_PowerShell_ISE.md)
