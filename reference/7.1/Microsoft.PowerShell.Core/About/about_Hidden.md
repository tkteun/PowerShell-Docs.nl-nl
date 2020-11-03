---
description: Hierin wordt het gereserveerde woord Hidden beschreven, waarmee klasse-leden worden verborgen voor de standaard Get-Member resultaten.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hidden?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hidden
ms.openlocfilehash: 7a8646f1b88da9b42ef26ccdf1d27eaa7042abd7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252152"
---
# <a name="about_hidden"></a>about_Hidden

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin wordt het gereserveerde woord Hidden beschreven, waarmee klasse-leden worden verborgen voor de standaard Get-Member resultaten.

## <a name="long-description"></a>LANGE BESCHRIJVING

Wanneer u het gereserveerde sleutel woord in een script gebruikt, kunt u de leden van een klasse standaard verbergen. Met het sleutel woord Hidden kunt u eigenschappen, methoden (waaronder constructors, gebeurtenissen, alias eigenschappen en andere typen leden, waaronder statische leden), van de standaard resultaten van de cmdlet Get-Member en van de resultaten van IntelliSense en TAB-voltooiing verbergen. Als u leden wilt weer geven die u hebt verborgen met het gereserveerde woord Hidden, voegt u de para meter-Force toe aan een Get-Member opdracht.

Verborgen leden worden niet weer gegeven met behulp van Tab-aanvulling of IntelliSense, tenzij de voltooiing plaatsvindt in de klasse die het verborgen lid definieert.

Er is een nieuw kenmerk, System. Management. Automation. HiddenAttribute, toegevoegd, zodat de C- \# code dezelfde semantiek kan hebben in Power shell.

Het gereserveerde tref woord is handig voor het maken van eigenschappen en methoden binnen een klasse die u niet per se wilt gebruiken om andere gebruikers van de klasse te zien of om het gemakkelijk te bewerken.

Het gereserveerde sleutel woord heeft geen invloed op hoe u leden van een klasse kunt weer geven of wijzigen. Net als alle tref woorden voor talen in Power shell is verborgen niet hoofdletter gevoelig en verborgen leden nog steeds openbaar.

Verborgen, samen met aangepaste klassen, werd geïntroduceerd in Power shell 5,0.

## <a name="example"></a>VOORBEELD

In het volgende voor beeld ziet u hoe u het gereserveerde woord Hidden gebruikt in een klassedefinitie. De methode auto klasse, Drive, heeft een eigenschap die niet hoeft te worden weer gegeven of gewijzigd (alleen het aantal keren dat het station wordt aangeroepen in de klasse Car, een metriek die niet belang rijk is voor gebruikers van de klasse; Houd er rekening mee dat wanneer u een auto aanschaft, u de verkoper niet vraagt op hoeveel stations de auto is genomen.

Omdat gebruikers van de klasse deze eigenschap niet hoeven te wijzigen, kunnen we de eigenschap van Get-Member en automatische voltooiings resultaten verbergen door het gereserveerde woord Hidden te gebruiken.

Voeg het verborgen tref woord toe door dit op dezelfde instructie regel als de eigenschap en het bijbehorende gegevens type in te voeren. Hoewel het tref woord in een wille keurige volg orde op deze regel kan worden weer gegeven, kunt u met de instructie met het gereserveerde tref woord later gemakkelijker alle leden identificeren die u hebt verborgen.

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

Maak nu een nieuw exemplaar van de auto-klasse en sla het op in een variabele, \$ TestCar.

```powershell
$TestCar = [Car]::new()
```

Nadat u de nieuwe instantie hebt gemaakt, moet u de inhoud van de variabele $TestCar naar Get-member sluist. Houd er rekening mee dat de eigenschap van de onderdrukkingen niet bestaat uit de leden die worden weer gegeven in de Get-Member opdracht resultaten.

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

Probeer nu Get-Member opnieuw uit te voeren, maar deze keer de para meter-Force toe.
Houd er rekening mee dat de resultaten de eigenschap verborgen onderdrukkingen bevatten, onder andere leden die standaard zijn verborgen.

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

## <a name="see-also"></a>ZIE OOK

[about_Classes](about_Classes.md)

[about_Language_Keywords](about_Language_Keywords.md)

[about_Wildcards](about_Wildcards.md)

[Get-member](xref:Microsoft.PowerShell.Utility.Get-Member)

