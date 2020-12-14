---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: fe28f52088a82b93799724de7a7a3f20ce42e36b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94706061"
---
# <span data-ttu-id="3c51a-102">Out-Null</span><span class="sxs-lookup"><span data-stu-id="3c51a-102">Out-Null</span></span>

## <span data-ttu-id="3c51a-103">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="3c51a-103">SYNOPSIS</span></span>
<span data-ttu-id="3c51a-104">Hiermee verbergt u de uitvoer in plaats van deze te verzenden naar de pijp lijn of weer te geven.</span><span class="sxs-lookup"><span data-stu-id="3c51a-104">Hides the output instead of sending it down the pipeline or displaying it.</span></span>

## <span data-ttu-id="3c51a-105">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="3c51a-105">SYNTAX</span></span>

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="3c51a-106">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="3c51a-106">DESCRIPTION</span></span>

<span data-ttu-id="3c51a-107">Met de cmdlet **out-null** wordt de uitvoer naar null verzonden, in feite verwijderd uit de pijp lijn en wordt voor komen dat de uitvoer op het scherm wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="3c51a-107">The **Out-Null** cmdlet sends its output to NULL, in effect, removing it from the pipeline and preventing the output to be displayed at the screen.</span></span>

## <span data-ttu-id="3c51a-108">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="3c51a-108">EXAMPLES</span></span>

### <span data-ttu-id="3c51a-109">Voor beeld 1: uitvoer verwijderen</span><span class="sxs-lookup"><span data-stu-id="3c51a-109">Example 1: Delete output</span></span>

```powershell
Get-ChildItem | Out-Null
```

<span data-ttu-id="3c51a-110">Met deze opdracht worden items in de huidige locatie/map opgehaald, maar de uitvoer wordt niet via de pijp lijn door gegeven en wordt niet weer gegeven op de opdracht regel.</span><span class="sxs-lookup"><span data-stu-id="3c51a-110">This command gets items in the current location/directory, but its output is not passed through the pipeline nor displayed at the command line.</span></span>
<span data-ttu-id="3c51a-111">Dit is handig voor het verbergen van de uitvoer die u niet nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="3c51a-111">This is useful for hiding output that you do not need.</span></span>

## <span data-ttu-id="3c51a-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3c51a-112">PARAMETERS</span></span>

### <span data-ttu-id="3c51a-113">-Input object</span><span class="sxs-lookup"><span data-stu-id="3c51a-113">-InputObject</span></span>

<span data-ttu-id="3c51a-114">Hiermee geeft u het object op dat naar NULL moet worden verzonden (verwijderd uit de pijp lijn).</span><span class="sxs-lookup"><span data-stu-id="3c51a-114">Specifies the object to be sent to NULL (removed from pipeline).</span></span>
<span data-ttu-id="3c51a-115">Voer een variabele in die de objecten bevat, of typ een opdracht of expressie waarmee de objecten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="3c51a-115">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="3c51a-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3c51a-116">CommonParameters</span></span>

<span data-ttu-id="3c51a-117">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3c51a-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3c51a-118">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c51a-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3c51a-119">INVOER</span><span class="sxs-lookup"><span data-stu-id="3c51a-119">INPUTS</span></span>

### <span data-ttu-id="3c51a-120">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="3c51a-120">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3c51a-121">U kunt elk object door sluizen naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c51a-121">You can pipe any object to this cmdlet.</span></span>

## <span data-ttu-id="3c51a-122">UITVOER</span><span class="sxs-lookup"><span data-stu-id="3c51a-122">OUTPUTS</span></span>

### <span data-ttu-id="3c51a-123">Geen</span><span class="sxs-lookup"><span data-stu-id="3c51a-123">None</span></span>

<span data-ttu-id="3c51a-124">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="3c51a-124">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3c51a-125">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="3c51a-125">NOTES</span></span>

* <span data-ttu-id="3c51a-126">De cmdlets die de **out** -bewerking (de **out** -cmdlets) bevatten, hebben geen para meters voor namen of bestands paden.</span><span class="sxs-lookup"><span data-stu-id="3c51a-126">The cmdlets that contain the **Out** verb (the **Out** cmdlets) do not have parameters for names or file paths.</span></span> <span data-ttu-id="3c51a-127">Als u gegevens wilt verzenden naar een **out** -cmdlet, gebruikt u een pijplijn operator (|) om de uitvoer van een Power shell-opdracht naar de cmdlet te verzenden.</span><span class="sxs-lookup"><span data-stu-id="3c51a-127">To send data to an **Out** cmdlet, use a pipeline operator (|) to send the output of a PowerShell command to the cmdlet.</span></span> <span data-ttu-id="3c51a-128">U kunt ook gegevens in een variabele opslaan en de para meter *input object* gebruiken om de gegevens door te geven aan de cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3c51a-128">You can also store data in a variable and use the *InputObject* parameter to pass the data to the cmdlet.</span></span> <span data-ttu-id="3c51a-129">Zie de voor beelden voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="3c51a-129">For more information, see the examples.</span></span>
* <span data-ttu-id="3c51a-130">**Out-null** retourneert geen output-objecten.</span><span class="sxs-lookup"><span data-stu-id="3c51a-130">**Out-Null** does not return any output objects.</span></span> <span data-ttu-id="3c51a-131">Als u de uitvoer van **out-null** naar de cmdlet voor Get-Member haalt, rapporten **ophalen van leden** dat er geen objecten zijn opgegeven.</span><span class="sxs-lookup"><span data-stu-id="3c51a-131">If you pipe the output of **Out-Null** to the Get-Member cmdlet, **Get-Member** reports that no objects have been specified.</span></span>

## <span data-ttu-id="3c51a-132">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="3c51a-132">RELATED LINKS</span></span>

[<span data-ttu-id="3c51a-133">Out-standaard</span><span class="sxs-lookup"><span data-stu-id="3c51a-133">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="3c51a-134">Out-host</span><span class="sxs-lookup"><span data-stu-id="3c51a-134">Out-Host</span></span>](Out-Host.md)

