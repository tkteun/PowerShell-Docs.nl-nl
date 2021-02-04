---
description: Hierin wordt uitgelegd hoe u bestanden kunt gebruiken `Types.ps1xml` om de typen objecten die worden gebruikt in Power shell uit te breiden.
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1XML
ms.openlocfilehash: 9a87394631d3318f3fb3f4b2a0cb2ab8d25408d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94705642"
---
# <a name="about-typesps1xml"></a><span data-ttu-id="2561b-103">Over Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="2561b-103">About Types.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="2561b-104">Korte beschrijving</span><span class="sxs-lookup"><span data-stu-id="2561b-104">Short description</span></span>
<span data-ttu-id="2561b-105">Hierin wordt uitgelegd hoe u bestanden kunt gebruiken `Types.ps1xml` om de typen objecten die worden gebruikt in Power shell uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="2561b-105">Explains how to use `Types.ps1xml` files to extend the types of objects that are used in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="2561b-106">Lange beschrijving</span><span class="sxs-lookup"><span data-stu-id="2561b-106">Long description</span></span>

<span data-ttu-id="2561b-107">Uitgebreide type gegevens worden extra eigenschappen en methoden (' leden ') van object typen in Power shell gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-107">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="2561b-108">Er zijn twee technieken voor het toevoegen van uitgebreide type gegevens aan een Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-108">There are two techniques for adding extended type data to a PowerShell session.</span></span>

- <span data-ttu-id="2561b-109">`Types.ps1xml` bestand: een XML-bestand waarin uitgebreide type gegevens worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-109">`Types.ps1xml` file: An XML file that defines extended type data.</span></span>
- <span data-ttu-id="2561b-110">`Update-TypeData`: Een cmdlet waarmee bestanden opnieuw worden geladen `Types.ps1xml` en uitgebreide gegevens worden gedefinieerd voor typen in de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-110">`Update-TypeData`: A cmdlet that reloads `Types.ps1xml` files and defines extended data for types in the current session.</span></span>

<span data-ttu-id="2561b-111">In dit onderwerp worden `Types.ps1xml` bestanden beschreven.</span><span class="sxs-lookup"><span data-stu-id="2561b-111">This topic describes `Types.ps1xml` files.</span></span> <span data-ttu-id="2561b-112">Zie update-TypeData voor meer informatie over het gebruik van de `Update-TypeData` cmdlet om dynamische uitgebreide type gegevens [](xref:Microsoft.PowerShell.Utility.Update-TypeData)toe te voegen aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-112">For more information about using the `Update-TypeData` cmdlet to add dynamic extended type data to the current session see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

## <a name="about-extended-type-data"></a><span data-ttu-id="2561b-113">Informatie over uitgebreide-type gegevens</span><span class="sxs-lookup"><span data-stu-id="2561b-113">About extended type data</span></span>

<span data-ttu-id="2561b-114">Uitgebreide type gegevens worden extra eigenschappen en methoden (' leden ') van object typen in Power shell gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-114">Extended type data defines additional properties and methods ("members") of object types in PowerShell.</span></span> <span data-ttu-id="2561b-115">U kunt elk type dat door Power shell wordt ondersteund, uitbreiden en de toegevoegde eigenschappen en methoden op dezelfde manier gebruiken als de eigenschappen die voor de object typen zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-115">You can extend any type that is supported by PowerShell and use the added properties and methods in the same way that you use the properties that are defined on the object types.</span></span>

<span data-ttu-id="2561b-116">Power shell voegt bijvoorbeeld een eigenschap **DateTime** toe aan alle `System.DateTime` objecten, zoals de waarde die door de `Get-Date` cmdlet wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-116">For example, PowerShell adds a **DateTime** property to all `System.DateTime` objects, such as the ones that the `Get-Date` cmdlet returns.</span></span>

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

<span data-ttu-id="2561b-117">U kunt de eigenschap **DateTime** niet vinden in de beschrijving van de structuur [System. datetime](/dotnet/api/system.datetime) , omdat Power shell de eigenschap toevoegt en alleen zichtbaar is in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2561b-117">You won't find the **DateTime** property in the description of the [System.DateTime](/dotnet/api/system.datetime) structure, because PowerShell adds the property and it is visible only in PowerShell.</span></span>

<span data-ttu-id="2561b-118">Power shell definieert intern een standaardset uitgebreide typen.</span><span class="sxs-lookup"><span data-stu-id="2561b-118">PowerShell internally defines a default set of extended types.</span></span> <span data-ttu-id="2561b-119">Dit type informatie wordt tijdens het opstarten in elke Power shell-sessie geladen.</span><span class="sxs-lookup"><span data-stu-id="2561b-119">This type information is loaded in every PowerShell session at startup.</span></span> <span data-ttu-id="2561b-120">De eigenschap **DateTime** maakt deel uit van deze standaardset.</span><span class="sxs-lookup"><span data-stu-id="2561b-120">The **DateTime** property is part of this default set.</span></span> <span data-ttu-id="2561b-121">Vóór Power shell 6 werden de type definities het `Types.ps1xml` bestand in de Power shell-installatiemap ( `$PSHOME` ) opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2561b-121">Prior to PowerShell 6, the type definitions were stored the `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`).</span></span>

## <a name="adding-extended-type-data-to-powershell"></a><span data-ttu-id="2561b-122">Uitgebreide type gegevens toevoegen aan Power shell</span><span class="sxs-lookup"><span data-stu-id="2561b-122">Adding extended type data to PowerShell</span></span>

<span data-ttu-id="2561b-123">Er zijn drie bronnen van uitgebreide-type gegevens in Power shell-sessies.</span><span class="sxs-lookup"><span data-stu-id="2561b-123">There are three sources of extended type data in PowerShell sessions.</span></span>

- <span data-ttu-id="2561b-124">De gedefinieerde door Power shell en wordt automatisch in elke Power shell-sessie geladen.</span><span class="sxs-lookup"><span data-stu-id="2561b-124">The defined by PowerShell and is loaded automatically into every PowerShell session.</span></span> <span data-ttu-id="2561b-125">Vanaf Power shell 6 wordt deze informatie gecompileerd in Power shell en wordt deze niet meer in een `Types.ps1xml` bestand verzonden.</span><span class="sxs-lookup"><span data-stu-id="2561b-125">Beginning with PowerShell 6, this information is compiled into PowerShell and is no longer shipped in a `Types.ps1xml` file.</span></span>

- <span data-ttu-id="2561b-126">De `Types.ps1xml` bestanden die modules exporteren, worden geladen wanneer de module in de huidige sessie wordt geïmporteerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-126">The `Types.ps1xml` files that modules export are loaded when the module is imported into the current session.</span></span>

- <span data-ttu-id="2561b-127">Uitgebreide-type gegevens die zijn gedefinieerd met behulp van de- `Update-TypeData` cmdlet, worden alleen toegevoegd aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-127">Extended type data that is defined by using the `Update-TypeData` cmdlet is added only to the current session.</span></span> <span data-ttu-id="2561b-128">Het wordt niet opgeslagen in een bestand.</span><span class="sxs-lookup"><span data-stu-id="2561b-128">It is not saved in a file.</span></span>

<span data-ttu-id="2561b-129">In de-sessie worden de uitgebreide type gegevens van de drie bronnen toegepast op objecten op dezelfde manier en zijn deze beschikbaar voor alle objecten van de opgegeven typen.</span><span class="sxs-lookup"><span data-stu-id="2561b-129">In the session, the extended type data from the three sources is applied to objects in the same way and is available on all objects of the specified types.</span></span>

## <a name="the-typedata-cmdlets"></a><span data-ttu-id="2561b-130">De TypeData-cmdlets</span><span class="sxs-lookup"><span data-stu-id="2561b-130">The TypeData cmdlets</span></span>

<span data-ttu-id="2561b-131">De volgende cmdlets zijn opgenomen in de module **micro soft. Power shell. Utility** in power Shell 3,0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="2561b-131">The following cmdlets are included in the **Microsoft.PowerShell.Utility** module in PowerShell 3.0 and later.</span></span>

- <span data-ttu-id="2561b-132">`Get-TypeData`: Hiermee worden uitgebreide type gegevens in de huidige sessie opgehaald.</span><span class="sxs-lookup"><span data-stu-id="2561b-132">`Get-TypeData`: Gets extended type data in the current session.</span></span>
- <span data-ttu-id="2561b-133">`Update-TypeData`: Bestanden opnieuw laden `Types.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="2561b-133">`Update-TypeData`: Reloads `Types.ps1xml` files.</span></span> <span data-ttu-id="2561b-134">Voegt uitgebreide type gegevens toe aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-134">Adds extended type data to the current session.</span></span>
- <span data-ttu-id="2561b-135">`Remove-TypeData`: Verwijdert uitgebreide-type gegevens uit de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-135">`Remove-TypeData`: Removes extended type data from the current session.</span></span>

<span data-ttu-id="2561b-136">Zie het Help-onderwerp voor elke cmdlet voor meer informatie over deze cmdlets.</span><span class="sxs-lookup"><span data-stu-id="2561b-136">For more information about these cmdlets, see the help topic for each cmdlet.</span></span>

## <a name="built-in-typesps1xml-files"></a><span data-ttu-id="2561b-137">Ingebouwde Types.ps1XML-bestanden</span><span class="sxs-lookup"><span data-stu-id="2561b-137">Built-in Types.ps1xml files</span></span>

<span data-ttu-id="2561b-138">De `Types.ps1xml` bestanden in de `$PSHOME` map worden automatisch aan elke sessie toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="2561b-138">The `Types.ps1xml` files in the `$PSHOME` directory are added automatically to every session.</span></span>

<span data-ttu-id="2561b-139">Het `Types.ps1xml` bestand in de Power shell-installatie directory ( `$PSHOME` ) is een XML-tekst bestand waarmee u eigenschappen en methoden kunt toevoegen aan de objecten die worden gebruikt in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2561b-139">The `Types.ps1xml` file in the PowerShell installation directory (`$PSHOME`) is an XML-based text file that lets you add properties and methods to the objects that are used in PowerShell.</span></span> <span data-ttu-id="2561b-140">Power Shell heeft ingebouwde `Types.ps1xml` bestanden die verschillende elementen toevoegen aan de .net-typen, maar u kunt extra `Types.ps1xml` bestanden maken om de typen verder uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="2561b-140">PowerShell has built-in `Types.ps1xml` files that add several elements to the .NET types, but you can create additional `Types.ps1xml` files to further extend the types.</span></span>

<span data-ttu-id="2561b-141">Bijvoorbeeld: Matrix objecten ( `System.Array` ) hebben een eigenschap **Length** die het aantal objecten in de matrix vermeldt.</span><span class="sxs-lookup"><span data-stu-id="2561b-141">For example, by default, array objects (`System.Array`) have a **Length** property that lists the number of objects in the array.</span></span> <span data-ttu-id="2561b-142">Omdat de naam **lengte** echter niet duidelijk de eigenschap beschrijft, voegt Power shell een alias eigenschap benoemde **Count** toe waarin dezelfde waarde wordt weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="2561b-142">However, because the name **Length** does not clearly describe the property, PowerShell adds an alias property named **Count** that displays the same value.</span></span> <span data-ttu-id="2561b-143">De eigenschap **Count** van het volgende XML-bestand wordt toegevoegd aan het `System.Array` type.</span><span class="sxs-lookup"><span data-stu-id="2561b-143">The following XML adds the **Count** property to the `System.Array` type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="2561b-144">Als u de nieuwe **AliasProperty** wilt ophalen, gebruikt u een `Get-Member` opdracht op een wille keurige matrix, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="2561b-144">To get the new **AliasProperty**, use a `Get-Member` command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="2561b-145">De opdracht retourneert de volgende resultaten.</span><span class="sxs-lookup"><span data-stu-id="2561b-145">The command returns the following results.</span></span>

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

<span data-ttu-id="2561b-146">Als gevolg hiervan kunt u de eigenschap **Count** of de eigenschap **Length** van matrices in Power shell gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2561b-146">As a result, you can use either the **Count** property or the **Length** property of arrays in PowerShell.</span></span> <span data-ttu-id="2561b-147">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="2561b-147">For example:</span></span>

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a><span data-ttu-id="2561b-148">Nieuwe Types.ps1XML-bestanden maken</span><span class="sxs-lookup"><span data-stu-id="2561b-148">Creating new Types.ps1xml files</span></span>

<span data-ttu-id="2561b-149">De `.ps1xml` bestanden die worden geïnstalleerd met Power shell, zijn digitaal ondertekend om knoeien te voor komen, omdat de opmaak script blokken kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="2561b-149">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="2561b-150">Daarom kunt u een eigenschap of methode toevoegen aan een .NET-type door uw eigen `Types.ps1xml` bestanden te maken en deze vervolgens toe te voegen aan uw Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-150">Therefore, to add a property or method to a .NET type, create your own `Types.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="2561b-151">Als u een nieuw bestand wilt maken, begint u met het kopiëren van een bestaand `Types.ps1xml` bestand.</span><span class="sxs-lookup"><span data-stu-id="2561b-151">To create a new file, start by copying an existing `Types.ps1xml` file.</span></span> <span data-ttu-id="2561b-152">Het nieuwe bestand kan een wille keurige naam hebben, maar moet een `.ps1xml` bestandsnaam extensie hebben.</span><span class="sxs-lookup"><span data-stu-id="2561b-152">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="2561b-153">U kunt het nieuwe bestand in elke map die toegankelijk is voor Power shell plaatsen, maar het is handig om de bestanden in de installatie directory van Power shell ( `$PSHOME` ) of in een submap van de installatiemap te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="2561b-153">You can place the new file in any directory that is accessible to PowerShell, but it is useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="2561b-154">Wanneer u het nieuwe bestand hebt opgeslagen, gebruikt u de `Update-TypeData` cmdlet om het nieuwe bestand aan uw Power shell-sessie toe te voegen.</span><span class="sxs-lookup"><span data-stu-id="2561b-154">When you have saved the new file, use the `Update-TypeData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="2561b-155">Als u wilt dat uw typen voor rang hebben boven de ingebouwde typen die zijn gedefinieerd, gebruikt u de para meter **PrependData** van de `Update-TypeData` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2561b-155">If you want your types to take precedence over the built-in types that are defined, use the **PrependData** parameter of the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="2561b-156">`Update-TypeData` alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-156">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="2561b-157">Als u de wijziging wilt aanbrengen in alle toekomstige sessies, exporteert u de console of voegt `Update-TypeData` u de opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="2561b-157">To make the change to all future sessions, export the console, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

## <a name="typesps1xml-and-add-member"></a><span data-ttu-id="2561b-158">Types.ps1XML en Add-Member</span><span class="sxs-lookup"><span data-stu-id="2561b-158">Types.ps1xml and Add-Member</span></span>

<span data-ttu-id="2561b-159">De `Types.ps1xml` bestanden voegen eigenschappen en methoden toe aan alle exemplaren van de objecten van het opgegeven .net-type in de desbetreffende Power shell-sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-159">The `Types.ps1xml` files add properties and methods to all the instances of the objects of the specified .NET type in the affected PowerShell session.</span></span> <span data-ttu-id="2561b-160">Als u echter eigenschappen of methoden wilt toevoegen aan één exemplaar van een object, gebruikt u de `Add-Member` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2561b-160">However, if you need to add properties or methods only to one instance of an object, use the `Add-Member` cmdlet.</span></span>

<span data-ttu-id="2561b-161">Zie [add-member](xref:Microsoft.PowerShell.Utility.Add-Member)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2561b-161">For more information, see [Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member).</span></span>

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a><span data-ttu-id="2561b-162">Voor beeld: een lid van de leeftijd toevoegen aan file info-objecten</span><span class="sxs-lookup"><span data-stu-id="2561b-162">Example: Adding an Age member to FileInfo objects</span></span>

<span data-ttu-id="2561b-163">In dit voor beeld ziet u hoe u een eigenschap **leeftijd** kunt toevoegen aan **System. io. file info** -objecten.</span><span class="sxs-lookup"><span data-stu-id="2561b-163">This example shows how to add an **Age** property to **System.IO.FileInfo** objects.</span></span> <span data-ttu-id="2561b-164">De leeftijd van een bestand is het verschil tussen de aanmaak tijd en de huidige tijd in dagen.</span><span class="sxs-lookup"><span data-stu-id="2561b-164">The age of a file is the difference between its creation time and the current time in days.</span></span>

<span data-ttu-id="2561b-165">Omdat de eigenschap **leeftijd** wordt berekend met behulp van een script blok, zoekt `<ScriptProperty>` u een label om te gebruiken als model voor de nieuwe eigenschap **leeftijd** .</span><span class="sxs-lookup"><span data-stu-id="2561b-165">Because the **Age** property is calculated by using a script block, find a `<ScriptProperty>` tag to use as a model for the new **Age** property.</span></span>

<span data-ttu-id="2561b-166">Sla de volgende XML-code op in het bestand `$PSHOME\MyTypes.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="2561b-166">Save the follow XML code to the file `$PSHOME\MyTypes.ps1xml`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

<span data-ttu-id="2561b-167">Voer uit `Update-TypeData` om het nieuwe `Types.ps1xml` bestand toe te voegen aan de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-167">Run `Update-TypeData` to add the new `Types.ps1xml` file to the current session.</span></span> <span data-ttu-id="2561b-168">De opdracht gebruikt de para meter **PrependData** om het nieuwe bestand te plaatsen in een volg orde die hoger is dan de oorspronkelijke definities.</span><span class="sxs-lookup"><span data-stu-id="2561b-168">The command uses the **PrependData** parameter to place the new file in a precedence order higher than the original definitions.</span></span>

<span data-ttu-id="2561b-169">`Update-TypeData`Zie [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)voor meer informatie over.</span><span class="sxs-lookup"><span data-stu-id="2561b-169">For more information about `Update-TypeData`, see [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).</span></span>

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

<span data-ttu-id="2561b-170">Als u de wijziging wilt testen, voert u een `Get-ChildItem` opdracht uit om het PowerShell.exe-bestand in de map op te halen `$PSHOME` en vervolgens het bestand naar de cmdlet te pipeen `Format-List` om alle eigenschappen van het bestand weer te geven.</span><span class="sxs-lookup"><span data-stu-id="2561b-170">To test the change, run a `Get-ChildItem` command to get the PowerShell.exe file in the `$PSHOME` directory, and then pipe the file to the `Format-List` cmdlet to list all of the properties of the file.</span></span> <span data-ttu-id="2561b-171">Als gevolg van de wijziging wordt de eigenschap **leeftijd** weer gegeven in de lijst.</span><span class="sxs-lookup"><span data-stu-id="2561b-171">As a result of the change, the **Age** property appears in the list.</span></span>

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a><span data-ttu-id="2561b-172">De XML in Types.ps1XML-bestanden</span><span class="sxs-lookup"><span data-stu-id="2561b-172">The XML in Types.ps1xml files</span></span>

<span data-ttu-id="2561b-173">De volledige schema definitie vindt u in de [types. XSD](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) in de Power shell-bron code opslagplaats op github.</span><span class="sxs-lookup"><span data-stu-id="2561b-173">The full schema definition can be found in [Types.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="2561b-174">De `<Types>` tag omsluit alle typen die in het bestand zijn gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-174">The `<Types>` tag encloses all of the types that are defined in the file.</span></span> <span data-ttu-id="2561b-175">Er mag slechts één `<Types>` tag zijn.</span><span class="sxs-lookup"><span data-stu-id="2561b-175">There should be only one `<Types>` tag.</span></span>

<span data-ttu-id="2561b-176">Elk .NET-type dat in het bestand wordt vermeld, moet worden aangeduid met een `<Type>` tag.</span><span class="sxs-lookup"><span data-stu-id="2561b-176">Each .NET type mentioned in the file should be represented by a `<Type>` tag.</span></span>

<span data-ttu-id="2561b-177">De type Tags moeten de volgende tags bevatten:</span><span class="sxs-lookup"><span data-stu-id="2561b-177">The type tags must contain the following tags:</span></span>

<span data-ttu-id="2561b-178">`<Name>`: Omsluit de naam van het betrokken .NET-type.</span><span class="sxs-lookup"><span data-stu-id="2561b-178">`<Name>`: Encloses the name of the affected .NET type.</span></span>

<span data-ttu-id="2561b-179">`<Members>`: Omsluit de labels voor de nieuwe eigenschappen en methoden die zijn gedefinieerd voor het .NET-type.</span><span class="sxs-lookup"><span data-stu-id="2561b-179">`<Members>`: Encloses the tags for the new properties and methods that are defined for the .NET type.</span></span>

<span data-ttu-id="2561b-180">Een van de volgende leden codes kan zich in de tag bevindt `<Members>` .</span><span class="sxs-lookup"><span data-stu-id="2561b-180">Any of the following member tags can be inside the `<Members>` tag.</span></span>

<span data-ttu-id="2561b-181">`<AliasProperty>`: Hiermee definieert u een nieuwe naam voor een bestaande eigenschap.</span><span class="sxs-lookup"><span data-stu-id="2561b-181">`<AliasProperty>`: Defines a new name for an existing property.</span></span>

<span data-ttu-id="2561b-182">Het `<AliasProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<ReferencedMemberName>` tag opgeeft waarmee de bestaande eigenschap wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2561b-182">The `<AliasProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<ReferencedMemberName>` tag that specifies the existing property.</span></span>

<span data-ttu-id="2561b-183">De eigenschap **Count** alias is bijvoorbeeld een alias voor de eigenschap **Length** van Matrix objecten.</span><span class="sxs-lookup"><span data-stu-id="2561b-183">For example, the **Count** alias property is an alias for the **Length** property of array objects.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

<span data-ttu-id="2561b-184">`<CodeMethod>`: Verwijst naar een statische methode van een .NET-klasse.</span><span class="sxs-lookup"><span data-stu-id="2561b-184">`<CodeMethod>`:  References a static method of a .NET class.</span></span>

<span data-ttu-id="2561b-185">Het `<CodeMethod>` label moet een `<Name>` tag hebben die de naam van de nieuwe methode opgeeft en een `<GetCodeReference>` tag die de code specificeert waarin de methode is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-185">The `<CodeMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<GetCodeReference>` tag that specifies the code in which the method is defined.</span></span>

<span data-ttu-id="2561b-186">De eigenschap **mode** van `System.IO.DirectoryInfo` objecten is bijvoorbeeld een code-eigenschap die is gedefinieerd in de Power shell-bestandssysteem provider.</span><span class="sxs-lookup"><span data-stu-id="2561b-186">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="2561b-187">`<CodeProperty>`: Verwijst naar een statische methode van een .NET-klasse.</span><span class="sxs-lookup"><span data-stu-id="2561b-187">`<CodeProperty>`: References a static method of a .NET class.</span></span>

<span data-ttu-id="2561b-188">Het `<CodeProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<GetCodeReference>` tag opgeeft die de code specificeert waarin de eigenschap is gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="2561b-188">The `<CodeProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetCodeReference>` tag that specifies the code in which the property is defined.</span></span>

<span data-ttu-id="2561b-189">De eigenschap **mode** van `System.IO.DirectoryInfo` objecten is bijvoorbeeld een code-eigenschap die is gedefinieerd in de Power shell-bestandssysteem provider.</span><span class="sxs-lookup"><span data-stu-id="2561b-189">For example, the **Mode** property of `System.IO.DirectoryInfo` objects is a code property defined in the PowerShell FileSystem provider.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

<span data-ttu-id="2561b-190">`<MemberSet>`: Definieert een verzameling van leden (eigenschappen en methoden).</span><span class="sxs-lookup"><span data-stu-id="2561b-190">`<MemberSet>`: Defines a collection of members (properties and methods).</span></span>

<span data-ttu-id="2561b-191">De `<MemberSet>` labels worden weer gegeven in de primaire `<Members>` labels.</span><span class="sxs-lookup"><span data-stu-id="2561b-191">The `<MemberSet>` tags appear within the primary `<Members>` tags.</span></span> <span data-ttu-id="2561b-192">De tags moeten een tag omsluiten `<Name>` rond de naam van de ledenset en een secundaire `<Members>` code die de leden (eigenschappen en methoden) in de set omsluit.</span><span class="sxs-lookup"><span data-stu-id="2561b-192">The tags must enclose a `<Name>` tag surrounding the name of the member set and a secondary `<Members>` tag that surround the members (properties and methods) in the set.</span></span> <span data-ttu-id="2561b-193">Een van de tags waarmee een eigenschap (zoals `<NoteProperty>` of `<ScriptProperty>` ) of een methode (zoals `<Method>` of `<ScriptMethod>` ) wordt gemaakt, kan lid zijn van de set.</span><span class="sxs-lookup"><span data-stu-id="2561b-193">Any of the tags that create a property (such as `<NoteProperty>` or `<ScriptProperty>`) or a method (such as `<Method>` or `<ScriptMethod>`) can be members of the set.</span></span>

<span data-ttu-id="2561b-194">In `Types.ps1xml` bestanden wordt de `<MemberSet>` tag gebruikt voor het definiëren van de standaard weergaven van de .net-objecten in Power shell.</span><span class="sxs-lookup"><span data-stu-id="2561b-194">In `Types.ps1xml` files, the `<MemberSet>` tag is used to define the default views of the .NET objects in PowerShell.</span></span> <span data-ttu-id="2561b-195">In dit geval is de naam van de leden reeks (de waarde binnen de `<Name>` Tags) altijd **PsStandardMembers** en de namen van de eigenschappen (de waarde van de `<Name>` tag) zijn een van de volgende:</span><span class="sxs-lookup"><span data-stu-id="2561b-195">In this case, the name of the member set (the value within the `<Name>` tags) is always **PsStandardMembers**, and the names of the properties (the value of the `<Name>` tag) are one of the following:</span></span>

- <span data-ttu-id="2561b-196">`DefaultDisplayProperty`: Eén eigenschap van een object.</span><span class="sxs-lookup"><span data-stu-id="2561b-196">`DefaultDisplayProperty`: A single property of an object.</span></span>

- <span data-ttu-id="2561b-197">`DefaultDisplayPropertySet`: Een of meer eigenschappen van een object.</span><span class="sxs-lookup"><span data-stu-id="2561b-197">`DefaultDisplayPropertySet`: One or more properties of an object.</span></span>

- <span data-ttu-id="2561b-198">`DefaultKeyPropertySet`: Een of meer sleutel eigenschappen van een object.</span><span class="sxs-lookup"><span data-stu-id="2561b-198">`DefaultKeyPropertySet`: One or more key properties of an object.</span></span> <span data-ttu-id="2561b-199">Een sleutel eigenschap identificeert exemplaren van eigenschaps waarden, zoals de ID van items in een sessie geschiedenis.</span><span class="sxs-lookup"><span data-stu-id="2561b-199">A key property identifies instances of property values, such as the ID number of items in a session history.</span></span>

<span data-ttu-id="2561b-200">De volgende XML definieert bijvoorbeeld de standaard weergave van Services ( `System.ServiceProcess.ServiceController` objecten) die door de cmdlet worden geretourneerd `Get-Service` .</span><span class="sxs-lookup"><span data-stu-id="2561b-200">For example, the following XML defines the default display of services (`System.ServiceProcess.ServiceController` objects) that are returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="2561b-201">Hiermee wordt een leden reeks gedefinieerd met de naam **PsStandardMembers** die bestaat uit een standaard eigenschap die is ingesteld op de eigenschappen **status**, **naam** en **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="2561b-201">It defines a member set named **PsStandardMembers** that consists of a default property set with the **Status**, **Name**, and **DisplayName** properties.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="2561b-202">`<Method>`: Verwijst naar een systeem eigen methode van het onderliggende object.</span><span class="sxs-lookup"><span data-stu-id="2561b-202">`<Method>`: References a native method of the underlying object.</span></span>

<span data-ttu-id="2561b-203">`<Methods>`: Een verzameling methoden van het object.</span><span class="sxs-lookup"><span data-stu-id="2561b-203">`<Methods>`: A collection of the methods of the object.</span></span>

<span data-ttu-id="2561b-204">`<NoteProperty>`: Definieert een eigenschap met een statische waarde.</span><span class="sxs-lookup"><span data-stu-id="2561b-204">`<NoteProperty>`: Defines a property with a static value.</span></span>

<span data-ttu-id="2561b-205">Het `<NoteProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<Value>` tag opgeeft waarmee de waarde van de eigenschap wordt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="2561b-205">The `<NoteProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<Value>` tag that specifies the value of the property.</span></span>

<span data-ttu-id="2561b-206">De volgende XML-code maakt bijvoorbeeld een eigenschap **status** voor **System. io. DirectoryInfo** -objecten.</span><span class="sxs-lookup"><span data-stu-id="2561b-206">For example, the following XML creates a **Status** property for **System.IO.DirectoryInfo** objects.</span></span> <span data-ttu-id="2561b-207">De waarde van de eigenschap **status** is altijd **geslaagd**.</span><span class="sxs-lookup"><span data-stu-id="2561b-207">The value of the **Status** property is always **Success**.</span></span>

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

<span data-ttu-id="2561b-208">`<ParameterizedProperty>`: Eigenschappen die argumenten aannemen en een waarde Retour neren.</span><span class="sxs-lookup"><span data-stu-id="2561b-208">`<ParameterizedProperty>`: Properties that take arguments and return a value.</span></span>

<span data-ttu-id="2561b-209">`<Properties>`: Een verzameling eigenschappen van het object.</span><span class="sxs-lookup"><span data-stu-id="2561b-209">`<Properties>`: A collection of the properties of the object.</span></span>

<span data-ttu-id="2561b-210">`<Property>`: Een eigenschap van het basis object.</span><span class="sxs-lookup"><span data-stu-id="2561b-210">`<Property>`: A property of the base object.</span></span>

<span data-ttu-id="2561b-211">`<PropertySet>`: Hiermee definieert u een verzameling eigenschappen van het object.</span><span class="sxs-lookup"><span data-stu-id="2561b-211">`<PropertySet>`: Defines a collection of properties of the object.</span></span>

<span data-ttu-id="2561b-212">Het `<PropertySet>` label moet een `<Name>` tag hebben die de naam van de eigenschappenset opgeeft en een `<ReferencedProperty>` tag die de eigenschappen specificeert.</span><span class="sxs-lookup"><span data-stu-id="2561b-212">The `<PropertySet>` tag must have a `<Name>` tag that specifies the name of the property set and a `<ReferencedProperty>` tag that specifies the properties.</span></span> <span data-ttu-id="2561b-213">De namen van de eigenschappen bevinden zich in een `<Name>` tag.</span><span class="sxs-lookup"><span data-stu-id="2561b-213">The names of the properties are enclosed in `<Name>` tag.</span></span>

<span data-ttu-id="2561b-214">In `Types.ps1xml` `<PropertySet>` worden tags gebruikt voor het definiëren van sets eigenschappen voor de standaard weergave van een object.</span><span class="sxs-lookup"><span data-stu-id="2561b-214">In `Types.ps1xml`, `<PropertySet>` tags are used to define sets of properties for the default display of an object.</span></span> <span data-ttu-id="2561b-215">U kunt de standaard weer geven identificeren met de waarde **PsStandardMembers** in het `<Name>` label van een `<MemberSet>` tag.</span><span class="sxs-lookup"><span data-stu-id="2561b-215">You can identify the default displays by the value **PsStandardMembers** in the `<Name>` tag of a `<MemberSet>` tag.</span></span>

<span data-ttu-id="2561b-216">De volgende XML-code maakt bijvoorbeeld een **status** eigenschap voor het `System.IO.DirectoryInfo` object.</span><span class="sxs-lookup"><span data-stu-id="2561b-216">For example, the following XML creates a **Status** property for the `System.IO.DirectoryInfo` object.</span></span> <span data-ttu-id="2561b-217">De waarde van de eigenschap **status** is altijd **geslaagd**.</span><span class="sxs-lookup"><span data-stu-id="2561b-217">The value of the **Status** property is always **Success**.</span></span>

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

<span data-ttu-id="2561b-218">`<ScriptMethod>`: Definieert een methode waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="2561b-218">`<ScriptMethod>`: Defines a method whose value is the output of a script.</span></span>

<span data-ttu-id="2561b-219">Het `<ScriptMethod>` label moet een `<Name>` tag hebben die de naam van de nieuwe methode en een `<Script>` tag bevat die het script blok omsluit dat het resultaat van de methode retourneert.</span><span class="sxs-lookup"><span data-stu-id="2561b-219">The `<ScriptMethod>` tag must have a `<Name>` tag that specifies the name of the new method and a `<Script>` tag that encloses the script block that returns the method result.</span></span>

<span data-ttu-id="2561b-220">De `ConvertToDateTime` `ConvertFromDateTime` methoden en van Management Objects ( `System.System.Management.ManagementObject` ) zijn bijvoorbeeld script methoden die gebruikmaken van de `ToDateTime` `ToDmtfDateTime` statische methoden van de- `System.Management.ManagementDateTimeConverter` klasse.</span><span class="sxs-lookup"><span data-stu-id="2561b-220">For example, the `ConvertToDateTime` and `ConvertFromDateTime` methods of management objects (`System.System.Management.ManagementObject`) are script methods that use the `ToDateTime` and `ToDmtfDateTime` static methods of the `System.Management.ManagementDateTimeConverter` class.</span></span>

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

<span data-ttu-id="2561b-221">`<ScriptProperty>`: Definieert een eigenschap waarvan de waarde de uitvoer van een script is.</span><span class="sxs-lookup"><span data-stu-id="2561b-221">`<ScriptProperty>`: Defines a property whose value is the output of a script.</span></span>

<span data-ttu-id="2561b-222">Het `<ScriptProperty>` label moet een `<Name>` tag hebben die de naam van de nieuwe eigenschap en een `<GetScriptBlock>` tag bevat die het script blok omsluit dat de waarde van de eigenschap retourneert.</span><span class="sxs-lookup"><span data-stu-id="2561b-222">The `<ScriptProperty>` tag must have a `<Name>` tag that specifies the name of the new property and a `<GetScriptBlock>` tag that encloses the script block that returns the property value.</span></span>

<span data-ttu-id="2561b-223">De eigenschap **VersionInfo** van het object **System. io. file info** is bijvoorbeeld een script eigenschap die het resultaat is **van het gebruik** van de eigenschap **FullName** van de statische methode van **System. Diagnostics. FileVersionInfo** -objecten.</span><span class="sxs-lookup"><span data-stu-id="2561b-223">For example, the **VersionInfo** property of the **System.IO.FileInfo** object is a script property that results from using the **FullName** property of the **GetVersionInfo** static method of **System.Diagnostics.FileVersionInfo** objects.</span></span>

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

<span data-ttu-id="2561b-224">Zie de [Windows Power shell Software Development Kit (SDK) (Engelstalig)](/powershell/scripting/developer/windows-powershell)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2561b-224">For more information, see the [Windows PowerShell Software Development Kit (SDK)](/powershell/scripting/developer/windows-powershell).</span></span>

## <a name="update-typedata"></a><span data-ttu-id="2561b-225">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="2561b-225">Update-TypeData</span></span>

<span data-ttu-id="2561b-226">`Types.ps1xml`Voer de cmdlet uit om uw bestanden te laden in een Power shell-sessie `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="2561b-226">To load your `Types.ps1xml` files into a PowerShell session, run the `Update-TypeData` cmdlet.</span></span> <span data-ttu-id="2561b-227">Als u wilt dat de typen in het bestand voor rang hebben op typen in het ingebouwde `Types.ps1xml` bestand, voegt u de para meter **PrependData** van toe `Update-TypeData` .</span><span class="sxs-lookup"><span data-stu-id="2561b-227">If you want the types in your file to take precedence over types in the built-in `Types.ps1xml` file, add the **PrependData** parameter of `Update-TypeData`.</span></span> <span data-ttu-id="2561b-228">`Update-TypeData` alleen van invloed op de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="2561b-228">`Update-TypeData` affects only the current session.</span></span> <span data-ttu-id="2561b-229">Als u de wijziging wilt door voeren voor alle toekomstige sessies, exporteert u de sessie of voegt `Update-TypeData` u de opdracht toe aan uw Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="2561b-229">To make the change to all future sessions, export the session, or add the `Update-TypeData` command to your PowerShell profile.</span></span>

<span data-ttu-id="2561b-230">Uitzonde ringen die optreden in eigenschappen of van het toevoegen van eigenschappen aan een `Update-TypeData` opdracht, rapporteren geen fouten aan `StdErr` .</span><span class="sxs-lookup"><span data-stu-id="2561b-230">Exceptions that occur in properties, or from adding properties to an `Update-TypeData` command, do not report errors to `StdErr`.</span></span> <span data-ttu-id="2561b-231">Dit is om uitzonde ringen te onderdrukken die tijdens het format teren en uitvoeren in veel voorkomende typen zouden optreden.</span><span class="sxs-lookup"><span data-stu-id="2561b-231">This is to suppress exceptions that would occur in many common types during formatting and outputting.</span></span> <span data-ttu-id="2561b-232">Als u .NET-eigenschappen krijgt, kunt u de onderdrukking van uitzonde ringen omzeilen door in plaats daarvan de syntaxis van de methode te gebruiken, zoals wordt weer gegeven in het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="2561b-232">If you are getting .NET properties, you can work around the suppression of exceptions by using method syntax instead, as shown in the following example:</span></span>

```powershell
"hello".get_Length()
```

<span data-ttu-id="2561b-233">Houd er rekening mee dat syntaxis van een methode alleen kan worden gebruikt met .NET-eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="2561b-233">Note that method syntax can only be used with .NET properties.</span></span> <span data-ttu-id="2561b-234">Eigenschappen die worden toegevoegd door de cmdlet uit te voeren `Update-TypeData` , kunnen de syntaxis van de methode niet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2561b-234">Properties that are added by running the `Update-TypeData` cmdlet cannot use method syntax.</span></span>

## <a name="signing-a-typesps1xml-file"></a><span data-ttu-id="2561b-235">Een Types.ps1XML-bestand ondertekenen</span><span class="sxs-lookup"><span data-stu-id="2561b-235">Signing a Types.ps1xml file</span></span>

<span data-ttu-id="2561b-236">Als u gebruikers van uw `Types.ps1xml` bestand wilt beveiligen, kunt u het bestand ondertekenen met een digitale hand tekening.</span><span class="sxs-lookup"><span data-stu-id="2561b-236">To protect users of your `Types.ps1xml` file, you can sign the file using a digital signature.</span></span> <span data-ttu-id="2561b-237">Zie [about_Signing](about_Signing.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="2561b-237">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2561b-238">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2561b-238">See also</span></span>

[<span data-ttu-id="2561b-239">about_Signing</span><span class="sxs-lookup"><span data-stu-id="2561b-239">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="2561b-240">Kopie-item</span><span class="sxs-lookup"><span data-stu-id="2561b-240">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)

[<span data-ttu-id="2561b-241">Kopiëren-item Property</span><span class="sxs-lookup"><span data-stu-id="2561b-241">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[<span data-ttu-id="2561b-242">Get-member</span><span class="sxs-lookup"><span data-stu-id="2561b-242">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="2561b-243">Get-TypeData</span><span class="sxs-lookup"><span data-stu-id="2561b-243">Get-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[<span data-ttu-id="2561b-244">Remove-TypeData</span><span class="sxs-lookup"><span data-stu-id="2561b-244">Remove-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[<span data-ttu-id="2561b-245">Update-TypeData</span><span class="sxs-lookup"><span data-stu-id="2561b-245">Update-TypeData</span></span>](xref:Microsoft.PowerShell.Utility.Update-TypeData)
