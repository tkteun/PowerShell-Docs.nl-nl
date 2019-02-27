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
# <a name="extending-output-objects"></a>Uitvoerobjecten uitbreiden

U kunt de .NET Framework-objecten die worden geretourneerd door cmdlets, functies en scripts met behulp van de typen bestanden (.ps1xml) uitbreiden. Typen zijn XML-bestanden waarmee u eigenschappen en methoden kunt toevoegen aan bestaande objecten. Windows PowerShell geeft bijvoorbeeld het bestand Types.ps1xml dat elementen worden toegevoegd aan meerdere bestaande .NET Framework-objecten. Het bestand Types.ps1xml bevindt zich in de installatiemap van Windows PowerShell (`$pshome`). U kunt uw eigen bestand typen verder uitbreiden die objecten of dat andere objecten maken. Wanneer u een object met behulp van een bestand typen uitbreidt, wordt elk exemplaar van het object is uitgebreid met de nieuwe elementen.

## <a name="extending-the-systemarray-object"></a>Het Object System.Array uitbreiden

Het volgende voorbeeld ziet u hoe Windows PowerShell breidt de [System.Array](/dotnet/api/System.Array) object in het bestand Types.ps1xml. Standaard [System.Array](/dotnet/api/System.Array) objecten hebben een `Length` eigenschap met een lijst met het aantal objecten in de matrix. Echter, omdat de eigenschap niet duidelijk wordt beschreven door de naam 'lengte", Windows PowerShell wordt toegevoegd de `Count` alias-eigenschap, die wordt weergegeven van dezelfde waarde als de `Length` eigenschap. Het volgende XML-bestand wordt toegevoegd de `Count` eigenschap in op de [System.Array](/dotnet/api/System.Array) type.

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

Als de eigenschap van dit nieuwe alias wilt weergeven, gebruikt een [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) opdracht in een matrix, zoals wordt weergegeven in het volgende voorbeeld.

```powershell
Get-Member -InputObject (1,2,3,4)
```

De opdracht retourneert de volgende resultaten.
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
U kunt een gebruiken de `Count` eigenschap of de `Length` eigenschap om te bepalen hoeveel objecten in een matrix zijn. Bijvoorbeeld:

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

## <a name="custom-types-files"></a>Aangepaste typen bestanden

Voor het maken van een bestand met aangepaste typen, gestart door een bestaande typen-bestand te kopiëren. Het nieuwe bestand kan elke naam hebben moet, maar er een extensie .ps1xml. Als u het bestand kopiëren, kunt u het nieuwe bestand plaatsen in een map die toegankelijk is voor Windows PowerShell, maar dit handig is om de bestanden in de installatiemap van Windows PowerShell (`$pshome`) of in een submap van de installatiemap.

Uw eigen uitgebreide typen toevoegen aan het bestand, voegt u een element typen voor elk object dat u wilt uitbreiden toe. De volgende onderwerpen vindt u voorbeelden.

- Zie voor meer informatie over het toevoegen van eigenschappen en de eigenschap wordt ingesteld, [uitgebreide eigenschappen](./extending-properties-for-objects.md)

- Zie voor meer informatie over het toevoegen van methoden [methoden uitgebreid](./defining-default-methods-for-objects.md).

- Zie voor meer informatie over het toevoegen van lid sets [lid wordt uitgebreid](./defining-default-member-sets-for-objects.md).

Nadat u uw eigen uitgebreide typen gedefinieerd, kunt u een van de volgende methoden om beschikbaar maken voor uw uitgebreide objecten gebruiken:

- Als u uw bestand uitgebreide typen beschikbaar zijn voor de huidige sessie, gebruikt u de [Update TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet voor het toevoegen van het nieuwe bestand. Als u wilt dat uw typen hebben voorrang op de typen die zijn gedefinieerd in andere typen bestanden (met inbegrip van het bestand Types.ps1xml), gebruikt u de `PrependData` parameter van de [Update TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- Om het bestand met uitgebreide typen beschikbaar te stellen alle toekomstige sessies, het bestand typen toevoegen aan een module, exporteren van de huidige sessie of Voeg de [Update TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) opdracht aan uw Windows PowerShell-profiel.

## <a name="signing-types-files"></a>Typen bestanden ondertekenen

Typen bestanden moeten digitaal worden ondertekend om omdat het XML-bestand kunt scriptblokken bevatten manipulatie te voorkomen. Zie voor meer informatie over het toevoegen van digitale handtekeningen [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Zie ook

[Standaard-eigenschappen voor de objecten definiëren](./extending-properties-for-objects.md)

[Standaardmethoden definiëren voor objecten](./defining-default-methods-for-objects.md)

[Standaard lid ingesteld voor de objecten definiëren](./defining-default-member-sets-for-objects.md)

[Schrijven van een Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
