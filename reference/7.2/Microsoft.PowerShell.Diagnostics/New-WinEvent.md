---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 5b4b150a1c02e5d0689b44db9b2a984e297db766
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706188"
---
# <span data-ttu-id="844c8-102">New-WinEvent</span><span class="sxs-lookup"><span data-stu-id="844c8-102">New-WinEvent</span></span>

## <span data-ttu-id="844c8-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="844c8-103">SYNOPSIS</span></span>
<span data-ttu-id="844c8-104">Hiermee maakt u een nieuwe Windows-gebeurtenis voor de opgegeven gebeurtenis provider.</span><span class="sxs-lookup"><span data-stu-id="844c8-104">Creates a new Windows event for the specified event provider.</span></span>

## <span data-ttu-id="844c8-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="844c8-105">SYNTAX</span></span>

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="844c8-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="844c8-106">DESCRIPTION</span></span>

<span data-ttu-id="844c8-107">Met de cmdlet **New-Wine vent** maakt u een gebeurtenis Event Tracing for Windows (etw) voor een gebeurtenis provider.</span><span class="sxs-lookup"><span data-stu-id="844c8-107">The **New-WinEvent** cmdlet creates an Event Tracing for Windows (ETW) event for an event provider.</span></span>
<span data-ttu-id="844c8-108">U kunt deze cmdlet gebruiken om gebeurtenissen toe te voegen aan ETW-kanalen vanuit Power shell.</span><span class="sxs-lookup"><span data-stu-id="844c8-108">You can use this cmdlet to add events to ETW channels from PowerShell.</span></span>

## <span data-ttu-id="844c8-109">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="844c8-109">EXAMPLES</span></span>

### <span data-ttu-id="844c8-110">Voorbeeld 1</span><span class="sxs-lookup"><span data-stu-id="844c8-110">Example 1</span></span>

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

<span data-ttu-id="844c8-111">Met deze opdracht wordt de cmdlet **New-Wine vent** gebruikt voor het maken van gebeurtenis 45090 voor de micro soft-Windows-Power shell-provider.</span><span class="sxs-lookup"><span data-stu-id="844c8-111">This command uses the **New-WinEvent** cmdlet to create event 45090 for the Microsoft-Windows-PowerShell provider.</span></span>

## <span data-ttu-id="844c8-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="844c8-112">PARAMETERS</span></span>

### <span data-ttu-id="844c8-113">-Id</span><span class="sxs-lookup"><span data-stu-id="844c8-113">-Id</span></span>

<span data-ttu-id="844c8-114">Hiermee geeft u een gebeurtenis-id op die is geregistreerd via een instrumentatie manifest.</span><span class="sxs-lookup"><span data-stu-id="844c8-114">Specifies an event id that was registered through an instrumentation manifest.</span></span>

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

### <span data-ttu-id="844c8-115">-Payload</span><span class="sxs-lookup"><span data-stu-id="844c8-115">-Payload</span></span>

<span data-ttu-id="844c8-116">Hiermee geeft u het bericht voor de gebeurtenis op.</span><span class="sxs-lookup"><span data-stu-id="844c8-116">Specifies the message for the event.</span></span> <span data-ttu-id="844c8-117">Wanneer de gebeurtenis naar een gebeurtenis logboek wordt geschreven, wordt de payload opgeslagen in de **bericht** eigenschap van het gebeurtenis object.</span><span class="sxs-lookup"><span data-stu-id="844c8-117">When the event is written to an event log, the payload is stored in the **Message** property of the event object.</span></span>

<span data-ttu-id="844c8-118">Wanneer de opgegeven Payload niet overeenkomt met de nettolading in de definitie van de gebeurtenis, genereert Power shell een waarschuwing, maar de opdracht is nog steeds geslaagd.</span><span class="sxs-lookup"><span data-stu-id="844c8-118">When the specified payload does not match the payload in the event definition, PowerShell generates a warning, but the command still succeeds.</span></span>

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

### <span data-ttu-id="844c8-119">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="844c8-119">-ProviderName</span></span>

<span data-ttu-id="844c8-120">Hiermee geeft u de gebeurtenis provider die de gebeurtenis naar een gebeurtenis logboek schrijft, zoals "micro soft-Windows-Power shell".</span><span class="sxs-lookup"><span data-stu-id="844c8-120">Specifies the event provider that writes the event to an event log, such as "Microsoft-Windows-PowerShell".</span></span> <span data-ttu-id="844c8-121">Een ETW-gebeurtenis provider is een logische entiteit die gebeurtenissen naar ETW-sessies schrijft.</span><span class="sxs-lookup"><span data-stu-id="844c8-121">An ETW event provider is a logical entity that writes events to ETW sessions.</span></span>

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

### <span data-ttu-id="844c8-122">-Versie</span><span class="sxs-lookup"><span data-stu-id="844c8-122">-Version</span></span>

<span data-ttu-id="844c8-123">Hiermee geeft u het versie nummer van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="844c8-123">Specifies the version number of the event.</span></span> <span data-ttu-id="844c8-124">Typ het nummer van de gebeurtenis.</span><span class="sxs-lookup"><span data-stu-id="844c8-124">Type the event number.</span></span> <span data-ttu-id="844c8-125">Power shell converteert het getal naar het vereiste byte type.</span><span class="sxs-lookup"><span data-stu-id="844c8-125">PowerShell converts the number to the required Byte type.</span></span>

<span data-ttu-id="844c8-126">Met deze para meter kunt u een gebeurtenis opgeven wanneer verschillende versies van dezelfde gebeurtenis worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="844c8-126">This parameter lets you specify an event when different versions of the same event are defined.</span></span>

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

### <span data-ttu-id="844c8-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="844c8-127">CommonParameters</span></span>

<span data-ttu-id="844c8-128">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="844c8-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="844c8-129">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="844c8-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="844c8-130">INVOER</span><span class="sxs-lookup"><span data-stu-id="844c8-130">INPUTS</span></span>

### <span data-ttu-id="844c8-131">Geen</span><span class="sxs-lookup"><span data-stu-id="844c8-131">None</span></span>

<span data-ttu-id="844c8-132">Deze cmdlet neemt geen invoer van de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="844c8-132">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="844c8-133">UITVOER</span><span class="sxs-lookup"><span data-stu-id="844c8-133">OUTPUTS</span></span>

### <span data-ttu-id="844c8-134">Geen</span><span class="sxs-lookup"><span data-stu-id="844c8-134">None</span></span>

<span data-ttu-id="844c8-135">Met deze cmdlet wordt een uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="844c8-135">This cmdlet does to generate any output.</span></span>

## <span data-ttu-id="844c8-136">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="844c8-136">NOTES</span></span>

* <span data-ttu-id="844c8-137">Nadat de provider de gebeurtenis naar een gebeurtenis logboek heeft geschreven, kunt u de Get-WinEvent-cmdlet gebruiken om het evenement op te halen uit het logboek.</span><span class="sxs-lookup"><span data-stu-id="844c8-137">After the provider writes the even to an eventlog, you can use the Get-WinEvent cmdlet to get the event from the event log.</span></span>

## <span data-ttu-id="844c8-138">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="844c8-138">RELATED LINKS</span></span>

[<span data-ttu-id="844c8-139">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="844c8-139">Get-WinEvent</span></span>](Get-WinEvent.md)

