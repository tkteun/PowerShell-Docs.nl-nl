---
description: Hierin wordt het gereserveerde woord Hidden beschreven, waarmee klasse-leden worden verborgen voor de standaard Get-Member resultaten.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 9d286accb6027e21df377832eff955a56add406c
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/21/2020
ms.locfileid: "93253152"
---
# <a name="about_hidden"></a><span data-ttu-id="c7153-104">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="c7153-104">about_Hidden</span></span>

## <a name="short-description"></a><span data-ttu-id="c7153-105">KORTE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c7153-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c7153-106">Hierin wordt het gereserveerde woord Hidden beschreven, waarmee klasse-leden worden verborgen voor de standaard Get-Member resultaten.</span><span class="sxs-lookup"><span data-stu-id="c7153-106">Describes the Hidden keyword, which hides class members from default Get-Member results.</span></span>

## <a name="long-description"></a><span data-ttu-id="c7153-107">LANGE BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="c7153-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="c7153-108">Wanneer u het gereserveerde sleutel woord in een script gebruikt, kunt u de leden van een klasse standaard verbergen.</span><span class="sxs-lookup"><span data-stu-id="c7153-108">When you use the Hidden keyword in a script, you hide the members of a class by default.</span></span> <span data-ttu-id="c7153-109">Met het sleutel woord Hidden kunt u eigenschappen, methoden (waaronder constructors, gebeurtenissen, alias eigenschappen en andere typen leden, waaronder statische leden), van de standaard resultaten van de cmdlet Get-Member en van de resultaten van IntelliSense en TAB-voltooiing verbergen.</span><span class="sxs-lookup"><span data-stu-id="c7153-109">The Hidden keyword can hide properties, methods (including constructors, events, alias properties, and other member types, including static members, from the default results of the Get-Member cmdlet, and from IntelliSense and tab completion results.</span></span> <span data-ttu-id="c7153-110">Als u leden wilt weer geven die u hebt verborgen met het gereserveerde woord Hidden, voegt u de para meter-Force toe aan een Get-Member opdracht.</span><span class="sxs-lookup"><span data-stu-id="c7153-110">To display members that you have hidden with the Hidden keyword, add the -Force parameter to a Get-Member command.</span></span>

<span data-ttu-id="c7153-111">Verborgen leden worden niet weer gegeven met behulp van Tab-aanvulling of IntelliSense, tenzij de voltooiing plaatsvindt in de klasse die het verborgen lid definieert.</span><span class="sxs-lookup"><span data-stu-id="c7153-111">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="c7153-112">Er is een nieuw kenmerk, System. Management. Automation. HiddenAttribute, toegevoegd, zodat de C- \# code dezelfde semantiek kan hebben in Power shell.</span><span class="sxs-lookup"><span data-stu-id="c7153-112">A new attribute, System.Management.Automation.HiddenAttribute, has been added, so that C\# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="c7153-113">Het gereserveerde tref woord is handig voor het maken van eigenschappen en methoden binnen een klasse die u niet per se wilt gebruiken om andere gebruikers van de klasse te zien of om het gemakkelijk te bewerken.</span><span class="sxs-lookup"><span data-stu-id="c7153-113">The Hidden keyword is useful for creating properties and methods within a class that you do not necessarily want other users of the class to see, or readily be able to edit.</span></span>

<span data-ttu-id="c7153-114">Het gereserveerde sleutel woord heeft geen invloed op hoe u leden van een klasse kunt weer geven of wijzigen.</span><span class="sxs-lookup"><span data-stu-id="c7153-114">The Hidden keyword has no effect on how you can view or make changes to members of a class.</span></span> <span data-ttu-id="c7153-115">Net als alle tref woorden voor talen in Power shell is verborgen niet hoofdletter gevoelig en verborgen leden nog steeds openbaar.</span><span class="sxs-lookup"><span data-stu-id="c7153-115">Like all language keywords in PowerShell, Hidden is not case-sensitive, and hidden members are still public.</span></span>

<span data-ttu-id="c7153-116">Verborgen, samen met aangepaste klassen, werd geïntroduceerd in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="c7153-116">Hidden, along with custom classes, was introduced in PowerShell 5.0.</span></span>

## <a name="example"></a><span data-ttu-id="c7153-117">VOORBEELD</span><span class="sxs-lookup"><span data-stu-id="c7153-117">EXAMPLE</span></span>

<span data-ttu-id="c7153-118">In het volgende voor beeld ziet u hoe u het gereserveerde woord Hidden gebruikt in een klassedefinitie.</span><span class="sxs-lookup"><span data-stu-id="c7153-118">The following example shows how to use the Hidden keyword in a class definition.</span></span> <span data-ttu-id="c7153-119">De methode auto klasse, Drive, heeft een eigenschap die niet hoeft te worden weer gegeven of gewijzigd (alleen het aantal keren dat het station wordt aangeroepen in de klasse Car, een metriek die niet belang rijk is voor gebruikers van de klasse; Houd er rekening mee dat wanneer u een auto aanschaft, u de verkoper niet vraagt op hoeveel stations de auto is genomen.</span><span class="sxs-lookup"><span data-stu-id="c7153-119">The Car class method, Drive, has a property, rides, that does not need to be viewed or changed (it merely tallies the number of times that Drive is called on the Car class, a metric that is not important to users of the class; consider, for example, that when you are buying a car, you do not ask the seller on how many drives the car has been taken.</span></span>

<span data-ttu-id="c7153-120">Omdat gebruikers van de klasse deze eigenschap niet hoeven te wijzigen, kunnen we de eigenschap van Get-Member en automatische voltooiings resultaten verbergen door het gereserveerde woord Hidden te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="c7153-120">Because there is little need for users of the class to change this property, we can hide the property from Get-Member and automatic completion results by using the Hidden keyword.</span></span>

<span data-ttu-id="c7153-121">Voeg het verborgen tref woord toe door dit op dezelfde instructie regel als de eigenschap en het bijbehorende gegevens type in te voeren.</span><span class="sxs-lookup"><span data-stu-id="c7153-121">Add the Hidden keyword by entering it on the same statement line as the property and its data type.</span></span> <span data-ttu-id="c7153-122">Hoewel het tref woord in een wille keurige volg orde op deze regel kan worden weer gegeven, kunt u met de instructie met het gereserveerde tref woord later gemakkelijker alle leden identificeren die u hebt verborgen.</span><span class="sxs-lookup"><span data-stu-id="c7153-122">Although the keyword can be in any order on this line, starting the statement with the Hidden keyword makes it easier for you later to identify all members that you have hidden.</span></span>

```powershell
class Car
{
   # Properties
   [String] $Color
   [String] $ModelYear
   [int] $Distance

   # Method
   [int] Drive ([int]$miles)
   {
      $this.Distance += $miles
      $this.rides++
      return $this.Distance
   }

   # Hidden property of the Drive method
    hidden [int] $rides = 0
}
```

<span data-ttu-id="c7153-123">Maak nu een nieuw exemplaar van de auto-klasse en sla het op in een variabele, \$ TestCar.</span><span class="sxs-lookup"><span data-stu-id="c7153-123">Now, create a new instance of the Car class, and save it in a variable, \$TestCar.</span></span>

```powershell
$TestCar = [Car]::new()
```

<span data-ttu-id="c7153-124">Nadat u de nieuwe instantie hebt gemaakt, moet u de inhoud van de variabele $TestCar naar Get-member sluist.</span><span class="sxs-lookup"><span data-stu-id="c7153-124">After you create the new instance, pipe the contents of the $TestCar variable to Get-Member.</span></span> <span data-ttu-id="c7153-125">Houd er rekening mee dat de eigenschap van de onderdrukkingen niet bestaat uit de leden die worden weer gegeven in de Get-Member opdracht resultaten.</span><span class="sxs-lookup"><span data-stu-id="c7153-125">Observe that the rides property is not among the members listed in the Get-Member command results.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member

   TypeName: Car

Name        MemberType Definition
----        ---------- ----------
Drive       Method     int Drive(int miles)
Equals      Method     bool Equals(System.Object obj)
GetHashCode Method     int GetHashCode()
GetType     Method     type GetType()
ToString    Method     string ToString()
Color       Property   string Color {get;set;}
Distance    Property   int Distance {get;set;}
ModelYear   Property   string ModelYear {get;set;}

```

<span data-ttu-id="c7153-126">Probeer nu Get-Member opnieuw uit te voeren, maar deze keer de para meter-Force toe.</span><span class="sxs-lookup"><span data-stu-id="c7153-126">Now, try running Get-Member again, but this time, add the -Force parameter.</span></span>
<span data-ttu-id="c7153-127">Houd er rekening mee dat de resultaten de eigenschap verborgen onderdrukkingen bevatten, onder andere leden die standaard zijn verborgen.</span><span class="sxs-lookup"><span data-stu-id="c7153-127">Note that the results contain the hidden rides property, among other members that are hidden by default.</span></span>

```output
PS C:\Windows\system32> $TestCar | Get-Member -Force

   TypeName: Car

Name          MemberType   Definition
----          ----------   ----------
pstypenames   CodeProperty System.Collections.ObjectModel.Collection`1
psadapted     MemberSet    psadapted {Color, ModelYear, Distance,
psbase        MemberSet    psbase {Color, ModelYear, Distance,...
psextended    MemberSet    psextended {}
psobject      MemberSet    psobject {BaseObject, Members,...
Drive         Method       int Drive(int miles)
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
get_Color     Method       string get_Color()
get_Distance  Method       int get_Distance()
get_ModelYear Method       string get_ModelYear()
get_rides     Method       int get_rides()
set_Color     Method       void set_Color(string )
set_Distance  Method       void set_Distance(int )
set_ModelYear Method       void set_ModelYear(string )
set_rides     Method       void set_rides(int )
ToString      Method       string ToString()
Color         Property     string Color {get;set;}
Distance      Property     int Distance {get;set;}
ModelYear     Property     string ModelYear {get;set;}
rides         Property     int rides {get;set;}

```

## <a name="see-also"></a><span data-ttu-id="c7153-128">ZIE OOK</span><span class="sxs-lookup"><span data-stu-id="c7153-128">SEE ALSO</span></span>

[<span data-ttu-id="c7153-129">about_Classes</span><span class="sxs-lookup"><span data-stu-id="c7153-129">about_Classes</span></span>](about_Classes.md)

[<span data-ttu-id="c7153-130">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="c7153-130">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="c7153-131">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="c7153-131">about_Wildcards</span></span>](about_Wildcards.md)

[<span data-ttu-id="c7153-132">Get-member</span><span class="sxs-lookup"><span data-stu-id="c7153-132">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)
