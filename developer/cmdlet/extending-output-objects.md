---
title: Uitbreiding van uitvoer objecten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850958"
---
# <a name="extending-output-objects"></a><span data-ttu-id="146df-102">Uitvoerobjecten uitbreiden</span><span class="sxs-lookup"><span data-stu-id="146df-102">Extending Output Objects</span></span>

<span data-ttu-id="146df-103">U kunt de .NET Framework-objecten die worden geretourneerd door cmdlets, functies en scripts met behulp van de typen bestanden (.ps1xml) uitbreiden.</span><span class="sxs-lookup"><span data-stu-id="146df-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="146df-104">Typen zijn XML-bestanden waarmee u eigenschappen en methoden kunt toevoegen aan bestaande objecten.</span><span class="sxs-lookup"><span data-stu-id="146df-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="146df-105">Windows PowerShell geeft bijvoorbeeld het bestand Types.ps1xml dat elementen worden toegevoegd aan meerdere bestaande .NET Framework-objecten.</span><span class="sxs-lookup"><span data-stu-id="146df-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="146df-106">Het bestand Types.ps1xml bevindt zich in de installatiemap van Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="146df-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="146df-107">U kunt uw eigen bestand typen verder uitbreiden die objecten of dat andere objecten maken.</span><span class="sxs-lookup"><span data-stu-id="146df-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="146df-108">Wanneer u een object met behulp van een bestand typen uitbreidt, wordt elk exemplaar van het object is uitgebreid met de nieuwe elementen.</span><span class="sxs-lookup"><span data-stu-id="146df-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="146df-109">Het Object System.Array uitbreiden</span><span class="sxs-lookup"><span data-stu-id="146df-109">Extending the System.Array Object</span></span>

<span data-ttu-id="146df-110">Het volgende voorbeeld ziet u hoe Windows PowerShell breidt de [System.Array](/dotnet/api/System.Array) object in het bestand Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="146df-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="146df-111">Standaard [System.Array](/dotnet/api/System.Array) objecten hebben een `Length` eigenschap met een lijst met het aantal objecten in de matrix.</span><span class="sxs-lookup"><span data-stu-id="146df-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="146df-112">Echter, omdat de eigenschap niet duidelijk wordt beschreven door de naam 'lengte", Windows PowerShell wordt toegevoegd de `Count` alias-eigenschap, die wordt weergegeven van dezelfde waarde als de `Length` eigenschap.</span><span class="sxs-lookup"><span data-stu-id="146df-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="146df-113">Het volgende XML-bestand wordt toegevoegd de `Count` eigenschap in op de [System.Array](/dotnet/api/System.Array) type.</span><span class="sxs-lookup"><span data-stu-id="146df-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="146df-114">Als de eigenschap van dit nieuwe alias wilt weergeven, gebruikt een [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) opdracht in een matrix, zoals wordt weergegeven in het volgende voorbeeld.</span><span class="sxs-lookup"><span data-stu-id="146df-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="146df-115">De opdracht retourneert de volgende resultaten.</span><span class="sxs-lookup"><span data-stu-id="146df-115">The command returns the following results.</span></span>
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
<span data-ttu-id="146df-116">U kunt een gebruiken de `Count` eigenschap of de `Length` eigenschap om te bepalen hoeveel objecten in een matrix zijn.</span><span class="sxs-lookup"><span data-stu-id="146df-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="146df-117">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="146df-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="146df-118">Aangepaste typen bestanden</span><span class="sxs-lookup"><span data-stu-id="146df-118">Custom Types Files</span></span>

<span data-ttu-id="146df-119">Voor het maken van een bestand met aangepaste typen, gestart door een bestaande typen-bestand te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="146df-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="146df-120">Het nieuwe bestand kan elke naam hebben moet, maar er een extensie .ps1xml.</span><span class="sxs-lookup"><span data-stu-id="146df-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="146df-121">Als u het bestand kopiëren, kunt u het nieuwe bestand plaatsen in een map die toegankelijk is voor Windows PowerShell, maar dit handig is om de bestanden in de installatiemap van Windows PowerShell (`$pshome`) of in een submap van de installatiemap.</span><span class="sxs-lookup"><span data-stu-id="146df-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="146df-122">Uw eigen uitgebreide typen toevoegen aan het bestand, voegt u een element typen voor elk object dat u wilt uitbreiden toe.</span><span class="sxs-lookup"><span data-stu-id="146df-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="146df-123">De volgende onderwerpen vindt u voorbeelden.</span><span class="sxs-lookup"><span data-stu-id="146df-123">The following topics provide examples.</span></span>

- <span data-ttu-id="146df-124">Zie voor meer informatie over het toevoegen van eigenschappen en de eigenschap wordt ingesteld, [uitgebreide eigenschappen](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="146df-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="146df-125">Zie voor meer informatie over het toevoegen van methoden [methoden uitgebreid](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="146df-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="146df-126">Zie voor meer informatie over het toevoegen van lid sets [lid wordt uitgebreid](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="146df-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="146df-127">Nadat u uw eigen uitgebreide typen gedefinieerd, kunt u een van de volgende methoden om beschikbaar maken voor uw uitgebreide objecten gebruiken:</span><span class="sxs-lookup"><span data-stu-id="146df-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="146df-128">Als u uw bestand uitgebreide typen beschikbaar zijn voor de huidige sessie, gebruikt u de [Update TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet voor het toevoegen van het nieuwe bestand.</span><span class="sxs-lookup"><span data-stu-id="146df-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="146df-129">Als u wilt dat uw typen hebben voorrang op de typen die zijn gedefinieerd in andere typen bestanden (met inbegrip van het bestand Types.ps1xml), gebruikt u de `PrependData` parameter van de [Update TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="146df-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="146df-130">Om het bestand met uitgebreide typen beschikbaar te stellen alle toekomstige sessies, het bestand typen toevoegen aan een module, exporteren van de huidige sessie of Voeg de [Update TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) opdracht aan uw Windows PowerShell-profiel.</span><span class="sxs-lookup"><span data-stu-id="146df-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="146df-131">Typen bestanden ondertekenen</span><span class="sxs-lookup"><span data-stu-id="146df-131">Signing Types Files</span></span>

<span data-ttu-id="146df-132">Typen bestanden moeten digitaal worden ondertekend om omdat het XML-bestand kunt scriptblokken bevatten manipulatie te voorkomen.</span><span class="sxs-lookup"><span data-stu-id="146df-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="146df-133">Zie voor meer informatie over het toevoegen van digitale handtekeningen [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="146df-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="146df-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="146df-134">See Also</span></span>

[<span data-ttu-id="146df-135">Standaard-eigenschappen voor de objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="146df-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="146df-136">Standaardmethoden definiëren voor objecten</span><span class="sxs-lookup"><span data-stu-id="146df-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="146df-137">Standaard lid ingesteld voor de objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="146df-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="146df-138">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="146df-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
