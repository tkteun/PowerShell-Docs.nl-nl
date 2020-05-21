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
# <a name="extending-output-objects"></a>Uitvoerobjecten uitbreiden

U kunt de .NET Framework-objecten die worden geretourneerd door cmdlets, functies en scripts uitbreiden met behulp van typen bestanden (. ps1xml). Typen bestanden zijn XML-bestanden waarmee u eigenschappen en methoden aan bestaande objecten kunt toevoegen. Windows Power shell biedt bijvoorbeeld het bestand types. ps1xml, waarmee elementen aan verschillende bestaande .NET Framework objecten worden toegevoegd. Het bestand types. ps1xml bevindt zich in de installatiemap van Windows Power shell ( `$pshome` ). U kunt uw eigen bestands typen maken om deze objecten verder uit te breiden of om andere objecten uit te breiden. Wanneer u een object uitbreidt met behulp van een bestands typen, wordt een wille keurig exemplaar van het object uitgebreid met de nieuwe elementen.

## <a name="extending-the-systemarray-object"></a>Het object System. array uitbreiden

In het volgende voor beeld ziet u hoe Windows Power shell het object [System. array](/dotnet/api/System.Array) uitbreidt in het bestand types. ps1xml. [Systeem. matrix](/dotnet/api/System.Array) -objecten hebben standaard een `Length` eigenschap die het aantal objecten in de matrix vermeldt. Omdat de naam echter niet duidelijk de eigenschap beschrijft, voegt Windows Power shell de `Count` alias eigenschap toe, die dezelfde waarde als de `Length` eigenschap weergeeft. De volgende XML-code voegt de `Count` eigenschap toe aan het type [System. array](/dotnet/api/System.Array) .

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

Als u deze nieuwe alias eigenschap wilt zien, gebruikt u een [Get-member-](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) opdracht in een wille keurige matrix, zoals wordt weer gegeven in het volgende voor beeld.

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

U kunt de `Count` eigenschap of de eigenschap gebruiken `Length` om te bepalen hoeveel objecten zich in een matrix bevinden. Bijvoorbeeld:

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

## <a name="custom-types-files"></a>Aangepaste bestands typen

Als u een bestand met aangepaste typen wilt maken, moet u eerst een bestaand type bestand kopiëren. Het nieuwe bestand kan een wille keurige naam hebben, maar het moet de bestands extensie. ps1xml hebben. Wanneer u het bestand kopieert, kunt u het nieuwe bestand plaatsen in elke map die toegankelijk is voor Windows Power shell, maar het is handig om de bestanden in de installatie directory van Windows Power shell ( `$pshome` ) of in een submap van de installatiemap te plaatsen.

Om uw eigen uitgebreide typen aan het bestand toe te voegen, voegt u een-element types toe voor elk object dat u wilt uitbreiden. De volgende onderwerpen bevatten voor beelden.

- Voor meer informatie over het toevoegen van eigenschappen en eigenschappen sets, Zie [uitgebreide eigenschappen](./extending-properties-for-objects.md)

- Zie voor meer informatie over het toevoegen van methoden [uitgebreide methoden](./defining-default-methods-for-objects.md).

- Zie voor meer informatie over het toevoegen van leden sets [uitgebreide leden sets](./defining-default-member-sets-for-objects.md).

Nadat u uw eigen uitgebreide typen hebt gedefinieerd, kunt u een van de volgende methoden gebruiken om uw uitgebreide objecten beschikbaar te maken:

- Gebruik de cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) om het nieuwe bestand toe te voegen om het uitgebreide-type bestand beschikbaar te maken voor de huidige sessie. Als u wilt dat uw typen voor rang hebben op de typen die zijn gedefinieerd in andere typen bestanden (met inbegrip van het bestand types. ps1xml), gebruikt u de `PrependData` para meter van de cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .
- Als u het uitgebreide-type bestand beschikbaar wilt maken voor alle toekomstige sessies, voegt u het typen bestand toe aan een module, exporteert u de huidige sessie of voegt u de opdracht [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) toe aan uw Windows Power shell-profiel.

## <a name="signing-types-files"></a>Bestands typen voor ondertekening

Bestands typen moeten digitaal worden ondertekend om knoeien te voor komen, omdat de XML script blokken kan bevatten. Zie [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing) voor meer informatie over het toevoegen van digitale hand tekeningen.

## <a name="see-also"></a>Zie ook

[Standaard eigenschappen voor objecten definiëren](./extending-properties-for-objects.md)

[Standaardmethoden voor objecten definiëren](./defining-default-methods-for-objects.md)

[Standaardledenreeksen voor objecten definiëren](./defining-default-member-sets-for-objects.md)

[Een Windows PowerShell-cmdlet schrijven](./writing-a-windows-powershell-cmdlet.md)
