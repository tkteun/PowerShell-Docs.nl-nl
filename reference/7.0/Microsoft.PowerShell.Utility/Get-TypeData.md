---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-typedata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TypeData
ms.openlocfilehash: 63e5fbfcce681a1c3d17959a486ee9ab1998741a
ms.sourcegitcommit: bdd0fedaf9ba534645b2f7eb1fe1241481f58715
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/30/2021
ms.locfileid: "105936543"
---
# <span data-ttu-id="654e1-103">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="654e1-103">Get-TypeData</span></span>

## <span data-ttu-id="654e1-104">Samen vatting</span><span class="sxs-lookup"><span data-stu-id="654e1-104">Synopsis</span></span>
<span data-ttu-id="654e1-105">Hiermee worden de uitgebreide type gegevens in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="654e1-105">Gets the extended type data in the current session.</span></span>

## <span data-ttu-id="654e1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="654e1-106">Syntax</span></span>

```
Get-TypeData [[-TypeName] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="654e1-107">Description</span><span class="sxs-lookup"><span data-stu-id="654e1-107">Description</span></span>

<span data-ttu-id="654e1-108">De `Get-TypeData` cmdlet haalt de uitgebreide type gegevens in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="654e1-108">The `Get-TypeData` cmdlet gets the extended type data in the current session.</span></span> <span data-ttu-id="654e1-109">Dit omvat type gegevens die zijn toegevoegd aan de sessie per `Types.ps1xml` bestand en dynamische type gegevens die zijn toegevoegd met behulp van de para meter van de `Update-TypeData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="654e1-109">This includes type data that was added to the session by `Types.ps1xml` file and dynamic type data that was added by using the parameter of the `Update-TypeData` cmdlet.</span></span>

<span data-ttu-id="654e1-110">U kunt de uitgebreide type gegevens gebruiken die `Get-TypeData` worden geretourneerd om de type gegevens in de sessie te controleren en deze naar `Update-TypeData` de `Remove-TypeData` cmdlets en te verzenden.</span><span class="sxs-lookup"><span data-stu-id="654e1-110">You can use the extended type data that `Get-TypeData` returns to examine the type data in the session and send it to the `Update-TypeData` and `Remove-TypeData` cmdlets.</span></span>

<span data-ttu-id="654e1-111">Uitgebreide-type gegevens voegen eigenschappen en methoden toe aan objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="654e1-111">Extended type data adds properties and methods to objects in PowerShell.</span></span> <span data-ttu-id="654e1-112">U kunt de toegevoegde eigenschappen en methoden op dezelfde manier gebruiken als de eigenschappen en methoden die in het object type zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="654e1-112">You can use the added properties and methods in the same ways that you would use the properties and methods that are defined in the object type.</span></span> <span data-ttu-id="654e1-113">Bij het schrijven van scripts moet u er echter rekening mee houden dat de toegevoegde eigenschappen en methoden mogelijk niet aanwezig zijn in elke Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="654e1-113">However, when writing scripts, be aware that the added properties and methods might not be present in every PowerShell session.</span></span>

<span data-ttu-id="654e1-114">`Types.ps1xml`Zie [about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)voor meer informatie over bestanden.</span><span class="sxs-lookup"><span data-stu-id="654e1-114">For more information about `Types.ps1xml` files, see [about_Types.ps1xml](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md).</span></span> <span data-ttu-id="654e1-115">Zie voor meer informatie over dynamische type gegevens die door de `Update-TypeData` cmdlet worden toegevoegd `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="654e1-115">For more information about dynamic type data that the `Update-TypeData` cmdlet adds, see `Update-TypeData`.</span></span>

<span data-ttu-id="654e1-116">Deze cmdlet is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="654e1-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="654e1-117">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="654e1-117">Examples</span></span>

### <span data-ttu-id="654e1-118">Voor beeld 1: alle uitgebreide-type gegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="654e1-118">Example 1: Get all extended type data</span></span>

<span data-ttu-id="654e1-119">In dit voor beeld worden alle uitgebreide type gegevens in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="654e1-119">This example gets all extended type data in the current session.</span></span>

 ```powershell
Get-TypeData
```

### <span data-ttu-id="654e1-120">Voor beeld 2: type gegevens ophalen op naam</span><span class="sxs-lookup"><span data-stu-id="654e1-120">Example 2: Get type data by name</span></span>

<span data-ttu-id="654e1-121">In dit voor beeld worden alle type gegevens in de huidige sessie opgehaald waarvan de naam is gekwalificeerd met ' System.IO '.</span><span class="sxs-lookup"><span data-stu-id="654e1-121">This example gets all type data in the current session whose name is qualified with "System.IO".</span></span>

```powershell
Get-TypeData -TypeName System.IO.*
```

```Output
TypeName                Members
--------                -------
System.IO.DirectoryInfo {[Mode, System.Management.Automation.Runspaces.CodePropert…
System.IO.FileInfo      {[Mode, System.Management.Automation.Runspaces.CodePropert…
```

### <span data-ttu-id="654e1-122">Voor beeld 3: het script blok ophalen waarmee een eigenschaps waarde wordt gemaakt</span><span class="sxs-lookup"><span data-stu-id="654e1-122">Example 3: Get the script block that creates a property value</span></span>

<span data-ttu-id="654e1-123">In dit voor beeld wordt het script blok opgehaald waarmee de waarde van de eigenschap **gebeurtenis** -Property van **EventLogEntry** -objecten wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="654e1-123">This example gets the script block that creates the value of the **EventID** property of **EventLogEntry** objects.</span></span>

 ```powershell
(Get-TypeData *EventLogEntry*).Members.EventID
```

```Output
GetScriptBlock                     SetScriptBlock     IsHidden Name
--------------                     --------------     -------- ----
$this.get_EventID() -band 0xFFFF                         False EventID
```

### <span data-ttu-id="654e1-124">Voor beeld 4: het script blok ophalen dat een eigenschap definieert voor een opgegeven object</span><span class="sxs-lookup"><span data-stu-id="654e1-124">Example 4: Get the script block that defines a property for a specified object</span></span>

<span data-ttu-id="654e1-125">In dit voor beeld wordt het script blok opgehaald dat de eigenschap **DateTime** van **System. datetime** -objecten in Power shell definieert.</span><span class="sxs-lookup"><span data-stu-id="654e1-125">This example gets the script block that defines the **DateTime** property of **System.DateTime** objects in PowerShell.</span></span>

 ```powershell
(Get-TypeData -TypeName System.DateTime).Members["DateTime"].GetScriptBlock
if ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq  "Date") {
    "{0}" -f $this.ToLongDateString()
}
elseif ((& { Set-StrictMode -Version 1; $this.DisplayHint }) -ieq "Time") {
    "{0}" -f  $this.ToLongTimeString()
}
else {
    "{0} {1}" -f $this.ToLongDateString(), $this.ToLongTimeString()
}
```

<span data-ttu-id="654e1-126">De opdracht gebruikt de `Get-TypeData` cmdlet om de uitgebreide type gegevens voor het type **System. datum/tijd** op te halen.</span><span class="sxs-lookup"><span data-stu-id="654e1-126">The command uses the `Get-TypeData` cmdlet to get the extended type data for the **System.DataTime** type.</span></span> <span data-ttu-id="654e1-127">Met de opdracht wordt de eigenschap **Members** van het **TypeData** -object opgehaald.</span><span class="sxs-lookup"><span data-stu-id="654e1-127">The command gets the **Members** property of the **TypeData** object.</span></span>

<span data-ttu-id="654e1-128">De eigenschap **Members** bevat een hash-tabel met eigenschappen en methoden die zijn gedefinieerd door gegevens van uitgebreide typen.</span><span class="sxs-lookup"><span data-stu-id="654e1-128">The **Members** property contains a hash table of properties and methods that are defined by extended type data.</span></span> <span data-ttu-id="654e1-129">Elke sleutel in de hash-tabel van de leden is een eigenschaps-of methode naam en elke waarde is de definitie van de waarde van de eigenschap of methode.</span><span class="sxs-lookup"><span data-stu-id="654e1-129">Each key in the Members hash table is a property or method name and each value is the definition of the property or method value.</span></span>

<span data-ttu-id="654e1-130">Met de opdracht wordt de sleutel **DateTime** opgehaald in de **leden** en de waarde van de eigenschap **GetScriptBlock** .</span><span class="sxs-lookup"><span data-stu-id="654e1-130">The command gets the **DateTime** key in **Members** and its **GetScriptBlock** property value.</span></span>

<span data-ttu-id="654e1-131">In de uitvoer ziet u het script blok waarmee de waarde van de eigenschap **DateTime** van elk **System. datetime** -object in Power shell wordt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="654e1-131">The output shows the script block that creates the value of the **DateTime** property of every **System.DateTime** object in PowerShell.</span></span>

## <span data-ttu-id="654e1-132">Parameters</span><span class="sxs-lookup"><span data-stu-id="654e1-132">Parameters</span></span>

### <span data-ttu-id="654e1-133">-TypeName</span><span class="sxs-lookup"><span data-stu-id="654e1-133">-TypeName</span></span>

<span data-ttu-id="654e1-134">Geeft type gegevens alleen als matrix voor de typen met de opgegeven namen.</span><span class="sxs-lookup"><span data-stu-id="654e1-134">Specifies type data as an array only for the types with the specified names.</span></span> <span data-ttu-id="654e1-135">Standaard worden `Get-TypeData` alle typen in de sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="654e1-135">By default, `Get-TypeData` gets all types in the session.</span></span>

<span data-ttu-id="654e1-136">Geef type namen of een naam patroon op.</span><span class="sxs-lookup"><span data-stu-id="654e1-136">Enter type names or a name patterns.</span></span> <span data-ttu-id="654e1-137">Volledige namen of naam patronen met Joker tekens zijn vereist, zelfs voor typen in de naam ruimte van het systeem.</span><span class="sxs-lookup"><span data-stu-id="654e1-137">Full names, or name patterns with wildcard characters are required, even for types in the System namespace.</span></span> <span data-ttu-id="654e1-138">Joker tekens worden ondersteund en de para meter naam **TypeName** is optioneel.</span><span class="sxs-lookup"><span data-stu-id="654e1-138">Wildcards are supported and the parameter name **TypeName** is optional.</span></span> <span data-ttu-id="654e1-139">U kunt ook de naam van een type pipe naar `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="654e1-139">You can also pipe type names to `Get-TypeData`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="654e1-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="654e1-140">CommonParameters</span></span>

<span data-ttu-id="654e1-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="654e1-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="654e1-142">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="654e1-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="654e1-143">Invoerwaarden</span><span class="sxs-lookup"><span data-stu-id="654e1-143">Inputs</span></span>

### <span data-ttu-id="654e1-144">System. String</span><span class="sxs-lookup"><span data-stu-id="654e1-144">System.String</span></span>

<span data-ttu-id="654e1-145">U kunt typen van het type sluizen naar `Get-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="654e1-145">You can pipe type names to `Get-TypeData`.</span></span>

## <span data-ttu-id="654e1-146">Uitvoerwaarden</span><span class="sxs-lookup"><span data-stu-id="654e1-146">Outputs</span></span>

### <span data-ttu-id="654e1-147">System. Management. Automation. Runspaces. TypeData</span><span class="sxs-lookup"><span data-stu-id="654e1-147">System.Management.Automation.Runspaces.TypeData</span></span>

## <span data-ttu-id="654e1-148">Notities</span><span class="sxs-lookup"><span data-stu-id="654e1-148">Notes</span></span>

<span data-ttu-id="654e1-149">`Get-TypeData` haalt alleen de uitgebreide type gegevens in de huidige sessie op.</span><span class="sxs-lookup"><span data-stu-id="654e1-149">`Get-TypeData` gets only the extended type data in the current session.</span></span> <span data-ttu-id="654e1-150">Er worden geen uitgebreide type gegevens opgehaald die zich op de computer bevinden, maar die niet zijn toegevoegd aan de huidige sessie, zoals uitgebreide typen die zijn gedefinieerd in modules die niet in de huidige sessie zijn geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="654e1-150">It does not get extended type data that is on the computer, but has not been added to the current session, such as extended types that are defined in modules that have not been imported into the current session.</span></span>

## <span data-ttu-id="654e1-151">Verwante koppelingen</span><span class="sxs-lookup"><span data-stu-id="654e1-151">Related links</span></span>

[<span data-ttu-id="654e1-152">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="654e1-152">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="654e1-153">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="654e1-153">Remove-TypeData</span></span>](Remove-TypeData.md)

[<span data-ttu-id="654e1-154">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="654e1-154">Update-TypeData</span></span>](Update-TypeData.md)
