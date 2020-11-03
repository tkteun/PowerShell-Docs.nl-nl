---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 5a949629cdf0f0822866863822e82e70fc38d8c2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250162"
---
# <span data-ttu-id="068a6-103">Out-Null</span><span class="sxs-lookup"><span data-stu-id="068a6-103">Out-Null</span></span>

## <span data-ttu-id="068a6-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="068a6-104">SYNOPSIS</span></span>
<span data-ttu-id="068a6-105">Hiermee verbergt u de uitvoer in plaats van deze te verzenden naar de pijp lijn of weer te geven.</span><span class="sxs-lookup"><span data-stu-id="068a6-105">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="068a6-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="068a6-106">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="068a6-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="068a6-107">DESCRIPTION</span></span>
<span data-ttu-id="068a6-108">Met de cmdlet **out-null** wordt de uitvoer naar null verzonden, in feite verwijderd uit de pijp lijn en wordt voor komen dat de uitvoer op het scherm wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="068a6-108">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span> <span data-ttu-id="068a6-109">Dit is alleen van invloed op de standaard uitvoer stroom.</span><span class="sxs-lookup"><span data-stu-id="068a6-109">This only affects the standard output stream.</span></span>
<span data-ttu-id="068a6-110">Andere uitvoer stromen, zoals de fout stroom, worden niet beïnvloed.</span><span class="sxs-lookup"><span data-stu-id="068a6-110">Other output streams, like the Error stream are not affected.</span></span> <span data-ttu-id="068a6-111">Uitzonde ringen worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="068a6-111">Exceptions will be displayed.</span></span> <span data-ttu-id="068a6-112">Dit maakt het gemakkelijker om uw opdracht te testen op fouten.</span><span class="sxs-lookup"><span data-stu-id="068a6-112">This makes it easier to test your command for any errors.</span></span>

## <span data-ttu-id="068a6-113">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="068a6-113">EXAMPLES</span></span>

### <span data-ttu-id="068a6-114">Voor beeld 1: uitvoer verwijderen</span><span class="sxs-lookup"><span data-stu-id="068a6-114">Example 1: Delete output</span></span>

```
PS C:\> Get-ChildItem | Out-Null
```

<span data-ttu-id="068a6-115">Met deze opdracht worden items in de huidige locatie/map opgehaald, maar de uitvoer wordt niet via de pijp lijn door gegeven en wordt niet weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="068a6-115">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="068a6-116">Dit is handig voor het verbergen van de uitvoer die u niet nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="068a6-116">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="068a6-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="068a6-117">PARAMETERS</span></span>

### <span data-ttu-id="068a6-118">-Input object</span><span class="sxs-lookup"><span data-stu-id="068a6-118">-InputObject</span></span>
<span data-ttu-id="068a6-119">Hiermee geeft u het object op dat naar NULL moet worden verzonden (verwijderd uit de pijp lijn).</span><span class="sxs-lookup"><span data-stu-id="068a6-119">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="068a6-120">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="068a6-120">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="068a6-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="068a6-121">CommonParameters</span></span>
<span data-ttu-id="068a6-122">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="068a6-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="068a6-123">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="068a6-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="068a6-124">INVOER</span><span class="sxs-lookup"><span data-stu-id="068a6-124">INPUTS</span></span>

### <span data-ttu-id="068a6-125">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="068a6-125">System.Management.Automation.PSObject</span></span>
<span data-ttu-id="068a6-126">U kunt elk object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="068a6-126">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="068a6-127">UITVOER</span><span class="sxs-lookup"><span data-stu-id="068a6-127">OUTPUTS</span></span>

### <span data-ttu-id="068a6-128">Geen</span><span class="sxs-lookup"><span data-stu-id="068a6-128">None</span></span>
<span data-ttu-id="068a6-129">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="068a6-129">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="068a6-130">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="068a6-130">NOTES</span></span>

* <span data-ttu-id="068a6-131">De cmdlets die de **out** -bewerking (de **out** -cmdlets) bevatten, hebben geen para meters voor namen of bestands paden.</span><span class="sxs-lookup"><span data-stu-id="068a6-131">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="068a6-132">Als u gegevens wilt verzenden naar een **out** -cmdlet, gebruikt u een pijplijn operator (|) om de uitvoer van een Windows Power shell-opdracht naar de cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="068a6-132">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a Windows PowerShell command to the cmdlet.</span></span> <span data-ttu-id="068a6-133">U kunt ook gegevens in een variabele opslaan en de para meter *input object* gebruiken om de gegevens door te geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="068a6-133">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="068a6-134">Zie de voor beelden voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="068a6-134">For more information, see the examples.</span></span>
* <span data-ttu-id="068a6-135">**Out-null** retourneert geen output-objecten.</span><span class="sxs-lookup"><span data-stu-id="068a6-135">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="068a6-136">Als u de uitvoer van **out-null** naar de cmdlet voor Get-Member haalt, rapporten **ophalen van leden** dat er geen objecten zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="068a6-136">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="068a6-137">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="068a6-137">RELATED LINKS</span></span>

[<span data-ttu-id="068a6-138">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="068a6-138">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="068a6-139">Out-host</span><span class="sxs-lookup"><span data-stu-id="068a6-139">Out-Host</span></span>](Out-Host.md)
