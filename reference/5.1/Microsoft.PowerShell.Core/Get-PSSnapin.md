---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 156cadecd87910e3c3312e84929b16709770641d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388668"
---
# <span data-ttu-id="efe2b-103">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="efe2b-103">Get-PSSnapin</span></span>

## <span data-ttu-id="efe2b-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="efe2b-104">SYNOPSIS</span></span>
<span data-ttu-id="efe2b-105">Hiermee worden de Windows Power shell-modules op de computer opgehaald.</span><span class="sxs-lookup"><span data-stu-id="efe2b-105">Gets the Windows PowerShell snap-ins on the computer.</span></span>

## <span data-ttu-id="efe2b-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="efe2b-106">SYNTAX</span></span>

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## <span data-ttu-id="efe2b-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="efe2b-107">DESCRIPTION</span></span>

<span data-ttu-id="efe2b-108">De `Get-PSSnapin` cmdlet haalt de Windows Power shell-modules op die zijn toegevoegd aan de huidige sessie of die zijn geregistreerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="efe2b-108">The `Get-PSSnapin` cmdlet gets the Windows PowerShell snap-ins that have been added to the current session or that have been registered on the system.</span></span> <span data-ttu-id="efe2b-109">Met deze cmdlet worden de modules weer gegeven in de volg orde waarin ze worden gedetecteerd.</span><span class="sxs-lookup"><span data-stu-id="efe2b-109">This cmdlet lists the snap-ins in the order in which they are detected.</span></span>

<span data-ttu-id="efe2b-110">`Get-PSSnapin` Hiermee worden alleen geregistreerde modules opgehaald. Als u een Windows Power shell-module wilt registreren, gebruikt u het InstallUtil-hulp programma dat is opgenomen in het Microsoft .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="efe2b-110">`Get-PSSnapin` gets only registered snap-ins. To register a Windows PowerShell snap-in, use the InstallUtil tool included with the Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="efe2b-111">Zie voor meer informatie [cmdlets, providers en hosttoepassingen registreren](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="efe2b-111">For more information, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

<span data-ttu-id="efe2b-112">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die zijn opgenomen in Windows Power shell, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="efe2b-112">Starting in Windows PowerShell 3.0, the core commands that are included in Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="efe2b-113">De uitzonde ring is **micro soft. Power shell. core** , een module (PSSnapin).</span><span class="sxs-lookup"><span data-stu-id="efe2b-113">The exception is **Microsoft.PowerShell.Core** , which is a snap-in (PSSnapin).</span></span>
<span data-ttu-id="efe2b-114">Standaard wordt alleen de module **micro soft. Power shell. core** toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="efe2b-114">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="efe2b-115">Modules worden automatisch geïmporteerd bij het eerste gebruik en u kunt de `Import-Module` cmdlet gebruiken om ze te importeren.</span><span class="sxs-lookup"><span data-stu-id="efe2b-115">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

## <span data-ttu-id="efe2b-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="efe2b-116">EXAMPLES</span></span>

### <span data-ttu-id="efe2b-117">Voor beeld 1: modules ophalen die momenteel zijn geladen</span><span class="sxs-lookup"><span data-stu-id="efe2b-117">Example 1: Get snap-ins that are currently loaded</span></span>

```
PS C:\> Get-PSSnapIn
```

<span data-ttu-id="efe2b-118">Met deze opdracht worden de Windows Power shell-modules opgehaald die momenteel in de sessie zijn geladen.</span><span class="sxs-lookup"><span data-stu-id="efe2b-118">This command gets the Windows PowerShell snap-ins that are currently loaded in the session.</span></span> <span data-ttu-id="efe2b-119">Dit omvat de modules die worden geïnstalleerd met Windows Power shell en die zijn toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="efe2b-119">This includes the snap-ins that are installed with Windows PowerShell and those that have been added to the session.</span></span>

### <span data-ttu-id="efe2b-120">Voor beeld 2: modules ophalen die zijn geregistreerd</span><span class="sxs-lookup"><span data-stu-id="efe2b-120">Example 2: Get snap-ins that have been registered</span></span>

```
PS C:\> get-PSSnapIn -Registered
```

<span data-ttu-id="efe2b-121">Met deze opdracht worden de Windows Power shell-modules opgehaald die zijn geregistreerd op de computer, inclusief de invoeg toepassingen die al zijn toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="efe2b-121">This command gets the Windows PowerShell snap-ins that have been registered on the computer, including those that have already been added to the session.</span></span> <span data-ttu-id="efe2b-122">De uitvoer bevat geen modules die zijn geïnstalleerd met Windows Power shell of Windows Power shell-module Dynamic-Link Libraries (Dll's) die nog niet zijn geregistreerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="efe2b-122">The output does not include snap-ins that are installed with Windows PowerShell or Windows PowerShell snap-in dynamic-link libraries (DLLs) that have not yet been registered on the system.</span></span>

### <span data-ttu-id="efe2b-123">Voor beeld 3: huidige modules ophalen die overeenkomen met een teken reeks</span><span class="sxs-lookup"><span data-stu-id="efe2b-123">Example 3: Get current snap-ins that match a string</span></span>

```
PS C:\> Get-PSSnapIn -Name smp*
```

<span data-ttu-id="efe2b-124">Met deze opdracht worden de Windows Power shell-modules in de huidige sessie opgehaald met namen die beginnen met smp.</span><span class="sxs-lookup"><span data-stu-id="efe2b-124">This command gets the Windows PowerShell snap-ins in the current session that have names that begin with smp.</span></span>

## <span data-ttu-id="efe2b-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="efe2b-125">PARAMETERS</span></span>

### <span data-ttu-id="efe2b-126">-Name</span><span class="sxs-lookup"><span data-stu-id="efe2b-126">-Name</span></span>

<span data-ttu-id="efe2b-127">Hiermee geeft u een matrix met module namen op.</span><span class="sxs-lookup"><span data-stu-id="efe2b-127">Specifies an array of snap-in names.</span></span> <span data-ttu-id="efe2b-128">Met deze cmdlet worden alleen de opgegeven Windows Power shell-modules opgehaald. Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="efe2b-128">This cmdlet gets only the specified Windows PowerShell snap-ins. Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efe2b-129">-Geregistreerd</span><span class="sxs-lookup"><span data-stu-id="efe2b-129">-Registered</span></span>

<span data-ttu-id="efe2b-130">Hiermee wordt aangegeven dat met deze cmdlet de Windows Power shell-modules worden opgehaald die zijn geregistreerd op het systeem, zelfs als ze nog niet zijn toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="efe2b-130">Indicates that this cmdlet gets the Windows PowerShell snap-ins that have been registered on the system even if they have not yet been added to the session.</span></span>

<span data-ttu-id="efe2b-131">De modules die met Windows Power shell zijn geïnstalleerd, worden niet in deze lijst weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="efe2b-131">The snap-ins that are installed with Windows PowerShell do not appear in this list.</span></span>

<span data-ttu-id="efe2b-132">Zonder deze para meter worden `Get-PSSnapin` de Windows Power shell-modules opgehaald die zijn toegevoegd aan de sessie.</span><span class="sxs-lookup"><span data-stu-id="efe2b-132">Without this parameter, `Get-PSSnapin` gets the Windows PowerShell snap-ins that have been added to the session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="efe2b-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="efe2b-133">CommonParameters</span></span>

<span data-ttu-id="efe2b-134">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="efe2b-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="efe2b-135">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="efe2b-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="efe2b-136">INVOER</span><span class="sxs-lookup"><span data-stu-id="efe2b-136">INPUTS</span></span>

### <span data-ttu-id="efe2b-137">Geen</span><span class="sxs-lookup"><span data-stu-id="efe2b-137">None</span></span>
<span data-ttu-id="efe2b-138">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="efe2b-138">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="efe2b-139">UITVOER</span><span class="sxs-lookup"><span data-stu-id="efe2b-139">OUTPUTS</span></span>

### <span data-ttu-id="efe2b-140">System. Management. Automation. PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="efe2b-140">System.Management.Automation.PSSnapInInfo</span></span>

<span data-ttu-id="efe2b-141">`Get-PSSnapin` retourneert een object voor elke module die wordt opgehaald.</span><span class="sxs-lookup"><span data-stu-id="efe2b-141">`Get-PSSnapin` returns an object for each snap-in that it gets.</span></span>

## <span data-ttu-id="efe2b-142">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="efe2b-142">NOTES</span></span>

<span data-ttu-id="efe2b-143">Vanaf Windows Power Shell 3,0 worden de kern opdrachten die met Windows Power shell zijn geïnstalleerd, verpakt in modules.</span><span class="sxs-lookup"><span data-stu-id="efe2b-143">Starting in Windows PowerShell 3.0, the core commands that are installed with Windows PowerShell are packaged in modules.</span></span> <span data-ttu-id="efe2b-144">In Windows Power Shell 2,0, en in host-Program ma's die oudere sessies maken in latere versies van Windows Power shell, worden de kern opdrachten verpakt in modules ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="efe2b-144">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of Windows PowerShell, the core commands are packaged in snap-ins ( **PSSnapin** ).</span></span> <span data-ttu-id="efe2b-145">De uitzonde ring is **micro soft. Power shell. core**. Dit is altijd een module.</span><span class="sxs-lookup"><span data-stu-id="efe2b-145">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="efe2b-146">Externe sessies, zoals computers die zijn gestart door de `New-PSSession` cmdlet, zijn ook oudere sessies met kern modules.</span><span class="sxs-lookup"><span data-stu-id="efe2b-146">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

 <span data-ttu-id="efe2b-147">Zie de [methode CreateDefault2](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2)voor informatie over de **CreateDefault2** -methode waarmee nieuwe-stijl sessies met kern modules worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="efe2b-147">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2#System_Management_Automation_Runspaces_InitialSessionState_CreateDefault2).</span></span>

## <span data-ttu-id="efe2b-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="efe2b-148">RELATED LINKS</span></span>

[<span data-ttu-id="efe2b-149">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="efe2b-149">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="efe2b-150">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="efe2b-150">Remove-PSSnapin</span></span>](Remove-PSSnapin.md)
