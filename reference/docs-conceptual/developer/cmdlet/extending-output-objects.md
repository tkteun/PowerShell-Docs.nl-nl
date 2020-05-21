---
title: Uitvoer objecten uitbreiden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 12a826363221b8a7ce06245c787a7bd0529e42f8
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83690894"
---
# <a name="extending-output-objects"></a><span data-ttu-id="746f6-102">Uitvoerobjecten uitbreiden</span><span class="sxs-lookup"><span data-stu-id="746f6-102">Extending Output Objects</span></span>

<span data-ttu-id="746f6-103">U kunt de .NET Framework-objecten die worden geretourneerd door cmdlets, functies en scripts uitbreiden met behulp van typen bestanden (. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="746f6-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="746f6-104">Typen bestanden zijn XML-bestanden waarmee u eigenschappen en methoden aan bestaande objecten kunt toevoegen.</span><span class="sxs-lookup"><span data-stu-id="746f6-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="746f6-105">Windows Power shell biedt bijvoorbeeld het bestand types. ps1xml, waarmee elementen aan verschillende bestaande .NET Framework objecten worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="746f6-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="746f6-106">Het bestand types. ps1xml bevindt zich in de installatiemap van Windows Power shell ( `$pshome` ).</span><span class="sxs-lookup"><span data-stu-id="746f6-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="746f6-107">U kunt uw eigen bestands typen maken om deze objecten verder uit te breiden of om andere objecten uit te breiden.</span><span class="sxs-lookup"><span data-stu-id="746f6-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="746f6-108">Wanneer u een object uitbreidt met behulp van een bestands typen, wordt een wille keurig exemplaar van het object uitgebreid met de nieuwe elementen.</span><span class="sxs-lookup"><span data-stu-id="746f6-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="746f6-109">Het object System. array uitbreiden</span><span class="sxs-lookup"><span data-stu-id="746f6-109">Extending the System.Array Object</span></span>

<span data-ttu-id="746f6-110">In het volgende voor beeld ziet u hoe Windows Power shell het object [System. array](/dotnet/api/System.Array) uitbreidt in het bestand types. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="746f6-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="746f6-111">[Systeem. matrix](/dotnet/api/System.Array) -objecten hebben standaard een `Length` eigenschap die het aantal objecten in de matrix vermeldt.</span><span class="sxs-lookup"><span data-stu-id="746f6-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="746f6-112">Omdat de naam echter niet duidelijk de eigenschap beschrijft, voegt Windows Power shell de `Count` alias eigenschap toe, die dezelfde waarde als de `Length` eigenschap weergeeft.</span><span class="sxs-lookup"><span data-stu-id="746f6-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="746f6-113">De volgende XML-code voegt de `Count` eigenschap toe aan het type [System. array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="746f6-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="746f6-114">Als u deze nieuwe alias eigenschap wilt zien, gebruikt u een [Get-member-](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) opdracht in een wille keurige matrix, zoals wordt weer gegeven in het volgende voor beeld.</span><span class="sxs-lookup"><span data-stu-id="746f6-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="746f6-115">De opdracht retourneert de volgende resultaten.</span><span class="sxs-lookup"><span data-stu-id="746f6-115">The command returns the following results.</span></span>

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

<span data-ttu-id="746f6-116">U kunt de `Count` eigenschap of de eigenschap gebruiken `Length` om te bepalen hoeveel objecten zich in een matrix bevinden.</span><span class="sxs-lookup"><span data-stu-id="746f6-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="746f6-117">Bijvoorbeeld:</span><span class="sxs-lookup"><span data-stu-id="746f6-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="746f6-118">Aangepaste bestands typen</span><span class="sxs-lookup"><span data-stu-id="746f6-118">Custom Types Files</span></span>

<span data-ttu-id="746f6-119">Als u een bestand met aangepaste typen wilt maken, moet u eerst een bestaand type bestand kopiëren.</span><span class="sxs-lookup"><span data-stu-id="746f6-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="746f6-120">Het nieuwe bestand kan een wille keurige naam hebben, maar het moet de bestands extensie. ps1xml hebben.</span><span class="sxs-lookup"><span data-stu-id="746f6-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="746f6-121">Wanneer u het bestand kopieert, kunt u het nieuwe bestand plaatsen in elke map die toegankelijk is voor Windows Power shell, maar het is handig om de bestanden in de installatie directory van Windows Power shell ( `$pshome` ) of in een submap van de installatiemap te plaatsen.</span><span class="sxs-lookup"><span data-stu-id="746f6-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="746f6-122">Om uw eigen uitgebreide typen aan het bestand toe te voegen, voegt u een-element types toe voor elk object dat u wilt uitbreiden.</span><span class="sxs-lookup"><span data-stu-id="746f6-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="746f6-123">De volgende onderwerpen bevatten voor beelden.</span><span class="sxs-lookup"><span data-stu-id="746f6-123">The following topics provide examples.</span></span>

- <span data-ttu-id="746f6-124">Voor meer informatie over het toevoegen van eigenschappen en eigenschappen sets, Zie [uitgebreide eigenschappen](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="746f6-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="746f6-125">Zie voor meer informatie over het toevoegen van methoden [uitgebreide methoden](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="746f6-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="746f6-126">Zie voor meer informatie over het toevoegen van leden sets [uitgebreide leden sets](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="746f6-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="746f6-127">Nadat u uw eigen uitgebreide typen hebt gedefinieerd, kunt u een van de volgende methoden gebruiken om uw uitgebreide objecten beschikbaar te maken:</span><span class="sxs-lookup"><span data-stu-id="746f6-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="746f6-128">Gebruik de cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) om het nieuwe bestand toe te voegen om het uitgebreide-type bestand beschikbaar te maken voor de huidige sessie.</span><span class="sxs-lookup"><span data-stu-id="746f6-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="746f6-129">Als u wilt dat uw typen voor rang hebben op de typen die zijn gedefinieerd in andere typen bestanden (met inbegrip van het bestand types. ps1xml), gebruikt u de `PrependData` para meter van de cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="746f6-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="746f6-130">Als u het uitgebreide-type bestand beschikbaar wilt maken voor alle toekomstige sessies, voegt u het typen bestand toe aan een module, exporteert u de huidige sessie of voegt u de opdracht [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) toe aan uw Windows Power shell-profiel.</span><span class="sxs-lookup"><span data-stu-id="746f6-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="746f6-131">Bestands typen voor ondertekening</span><span class="sxs-lookup"><span data-stu-id="746f6-131">Signing Types Files</span></span>

<span data-ttu-id="746f6-132">Bestands typen moeten digitaal worden ondertekend om knoeien te voor komen, omdat de XML script blokken kan bevatten.</span><span class="sxs-lookup"><span data-stu-id="746f6-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="746f6-133">Zie [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing) voor meer informatie over het toevoegen van digitale hand tekeningen.</span><span class="sxs-lookup"><span data-stu-id="746f6-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="746f6-134">Zie ook</span><span class="sxs-lookup"><span data-stu-id="746f6-134">See Also</span></span>

[<span data-ttu-id="746f6-135">Standaard eigenschappen voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="746f6-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="746f6-136">Standaardmethoden voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="746f6-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="746f6-137">Standaardledenreeksen voor objecten definiëren</span><span class="sxs-lookup"><span data-stu-id="746f6-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="746f6-138">Een Windows PowerShell-cmdlet schrijven</span><span class="sxs-lookup"><span data-stu-id="746f6-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
