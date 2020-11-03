---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 8e64c3e3a782fadf1669f1310d1615f3a014ccee
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249464"
---
# <span data-ttu-id="36ce4-103">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="36ce4-103">New-WinEvent</span></span>

## <span data-ttu-id="36ce4-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="36ce4-104">SYNOPSIS</span></span>
<span data-ttu-id="36ce4-105">Hiermee maakt u een nieuwe Windows-gebeurtenis voor de opgegeven gebeurtenis provider.</span><span class="sxs-lookup"><span data-stu-id="36ce4-105">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="36ce4-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="36ce4-106">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="36ce4-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="36ce4-107">DESCRIPTION</span></span>

<span data-ttu-id="36ce4-108">Met de cmdlet **New-Wine vent** maakt u een gebeurtenis Event Tracing for Windows (etw) voor een gebeurtenis provider.</span><span class="sxs-lookup"><span data-stu-id="36ce4-108">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="36ce4-109">U kunt deze cmdlet gebruiken om gebeurtenissen toe te voegen aan ETW-kanalen vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="36ce4-109">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="36ce4-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="36ce4-110">EXAMPLES</span></span>

### <span data-ttu-id="36ce4-111">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="36ce4-111">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="36ce4-112">Met deze opdracht wordt de cmdlet **New-Wine vent** gebruikt voor het maken van gebeurtenis 45090 voor de micro soft-Windows-Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="36ce4-112">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="36ce4-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36ce4-113">PARAMETERS</span></span>

### <span data-ttu-id="36ce4-114">-Id</span><span class="sxs-lookup"><span data-stu-id="36ce4-114">-Id</span></span>

<span data-ttu-id="36ce4-115">Hiermee geeft u een gebeurtenis-id op die is geregistreerd via een instrumentatie manifest.</span><span class="sxs-lookup"><span data-stu-id="36ce4-115">Specifies an event id that was registered through an instrumentation manifest.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36ce4-116">-Payload</span><span class="sxs-lookup"><span data-stu-id="36ce4-116">-Payload</span></span>

<span data-ttu-id="36ce4-117">Hiermee geeft u het bericht voor de gebeurtenis op.</span><span class="sxs-lookup"><span data-stu-id="36ce4-117">Specifies the message for the event.</span></span> <span data-ttu-id="36ce4-118">Wanneer de gebeurtenis naar een gebeurtenis logboek wordt geschreven, wordt de payload opgeslagen in de **bericht** eigenschap van het gebeurtenis object.</span><span class="sxs-lookup"><span data-stu-id="36ce4-118">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="36ce4-119">Wanneer de opgegeven Payload niet overeenkomt met de nettolading in de definitie van de gebeurtenis, genereert Power shell een waarschuwing, maar de opdracht is nog steeds geslaagd.</span><span class="sxs-lookup"><span data-stu-id="36ce4-119">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36ce4-120">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="36ce4-120">-ProviderName</span></span>

<span data-ttu-id="36ce4-121">Hiermee geeft u de gebeurtenis provider die de gebeurtenis naar een gebeurtenis logboek schrijft, zoals "micro soft-Windows-Power shell".</span><span class="sxs-lookup"><span data-stu-id="36ce4-121">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="36ce4-122">Een ETW-gebeurtenis provider is een logische entiteit die gebeurtenissen naar ETW-sessies schrijft.</span><span class="sxs-lookup"><span data-stu-id="36ce4-122">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36ce4-123">-Versie</span><span class="sxs-lookup"><span data-stu-id="36ce4-123">-Version</span></span>

<span data-ttu-id="36ce4-124">Hiermee geeft u het versie nummer van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="36ce4-124">Specifies the version number of the event.</span></span> <span data-ttu-id="36ce4-125">Typ het nummer van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="36ce4-125">Type the event number.</span></span> <span data-ttu-id="36ce4-126">Power shell converteert het getal naar het vereiste byte type.</span><span class="sxs-lookup"><span data-stu-id="36ce4-126">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="36ce4-127">Met deze para meter kunt u een gebeurtenis opgeven wanneer verschillende versies van dezelfde gebeurtenis worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="36ce4-127">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="36ce4-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36ce4-128">CommonParameters</span></span>

<span data-ttu-id="36ce4-129">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36ce4-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36ce4-130">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="36ce4-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36ce4-131">INVOER</span><span class="sxs-lookup"><span data-stu-id="36ce4-131">INPUTS</span></span>

### <span data-ttu-id="36ce4-132">Geen</span><span class="sxs-lookup"><span data-stu-id="36ce4-132">None</span></span>

<span data-ttu-id="36ce4-133">Deze cmdlet neemt geen invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="36ce4-133">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="36ce4-134">UITVOER</span><span class="sxs-lookup"><span data-stu-id="36ce4-134">OUTPUTS</span></span>

### <span data-ttu-id="36ce4-135">Geen</span><span class="sxs-lookup"><span data-stu-id="36ce4-135">None</span></span>

<span data-ttu-id="36ce4-136">Met deze cmdlet wordt een uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="36ce4-136">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="36ce4-137">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="36ce4-137">NOTES</span></span>

* <span data-ttu-id="36ce4-138">Nadat de provider de gebeurtenis naar een gebeurtenis logboek heeft geschreven, kunt u de Get-WinEvent-cmdlet gebruiken om het evenement op te halen uit het logboek.</span><span class="sxs-lookup"><span data-stu-id="36ce4-138">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="36ce4-139">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="36ce4-139">RELATED LINKS</span></span>

[<span data-ttu-id="36ce4-140">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="36ce4-140">Get-WinEvent</span></span>](Get-WinEvent.md)
