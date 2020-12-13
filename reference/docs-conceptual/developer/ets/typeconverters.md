---
ms.date: 07/09/2020
ms.topic: reference
title: Conversie Programma's van type uitgebreid type systeem
description: Conversie Programma's van type uitgebreid type systeem
ms.openlocfilehash: 0774e9eaae1187162b3d55cc45b902f7411a1f18
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648435"
---
# <a name="ets-type-converters"></a>Conversieprogramma's voor ETS-type

ETS gebruikt twee basis typen van type conversie Programma's wanneer een aanroep wordt gedaan aan de `LanguagePrimitives.ConvertTo(System.Object, System.Type)` methode. Wanneer deze methode wordt aangeroepen, probeert Power shell de type conversie uit te voeren met behulp van de standaard Power shell-taal conversieprogramma's of een aangepast conversie programma. Als Power shell de conversie niet kan uitvoeren, wordt er een **PSInvalidCastException** -uitzonde ring gegenereerd.

## <a name="standard-windows-powershell-language-converters"></a>Standaard taal Conversieprogramma's voor Windows Power shell

Deze standaard conversies worden gecontroleerd vóór aangepaste conversies en kunnen niet worden overschreven. De volgende tabel bevat de type conversies die door Power shell worden uitgevoerd wanneer de `ConvertTo(System.Object, System.Type)` methode wordt aangeroepen. Houd er rekening mee dat verwijzingen naar de para meters **valueToConvert** en **resultType** verwijzen naar para meters van de- `ConvertTo(System.Object,System.Type)` methode.

| Van (valueToConvert) |  Naar (resultType)  |                                                                               Retouren                                                                               |
| --------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Null                  | Tekenreeks            | ""                                                                                                                                                                  |
| Null                  | Char              | \ 0                                                                                                                                                                |
| Null                  | Numeriek           | `0` van het type dat is opgegeven in de para meter **resultType** .                                                                                                          |
| Null                  | Booleaans           | De resultaten van het aanroepen van de `IsTrue(System.Object)(Null)` methode.                                                                                                        |
| Null                  | PSObject          | Nieuw object van het type **PSObject**.                                                                                                                                    |
| Null                  | Niet-waarde-type    | Null.                                                                                                                                                               |
| Null                  | Nullable &lt; T&gt; | Null.                                                                                                                                                               |
| Afgeleide klasse         | Basis klasse        | **valueToConvert**                                                                                                                                                  |
| +              | Ongeldige              | **AutomationNull. waarde**                                                                                                                                            |
| +              | Tekenreeks            | Mechanisme voor aanroepen `ToString` .                                                                                                                                         |
| +              | Booleaans           | `IsTrue(System.Object) (valueToConvert)`                                                                                                                            |
| +              | PSObject          | De resultaten van het aanroepen van de `AsPSObject(System.Object) (valueToConvert)` methode.                                                                                         |
| +              | XML-document      | Zet **valueToConvert** om in een teken reeks en roept de constructor **XMLDocument** aan.                                                                                      |
| Matrix                 | Matrix             | Probeert elk element van de matrix te converteren.                                                                                                                      |
| Singleton             | Matrix             | `Array[0]` is gelijk aan **valueToConvert** die worden geconverteerd naar het element type van de matrix.                                                                            |
| IDictionary           | Hash-tabel        | Resultaten van de aanroep van hashtabel (valueToConvert).                                                                                                                       |
| Tekenreeks                | Char []            | `valueToConvert.ToCharArray`                                                                                                                                        |
| Tekenreeks                | Reguliere             | Resultaten van aanroepen van `Regx(valueToConvert)` .                                                                                                                          |
| Tekenreeks                | Type              | Retourneert het juiste type met behulp van de para meter **valueToConvert** om te zoeken in **RunspaceConfiguration. assemblies**.                                                 |
| Tekenreeks                | Numeriek           | Als **valueToConvert** is "", wordt geretourneerd `0` van het **resultType**. Anders wordt de cultuur "cultuur invariant" gebruikt voor het produceren van een numerieke waarde.                       |
| Geheel getal               | System. enum       | Converteert het gehele getal naar de constante als het geheel getal door de opsomming wordt gedefinieerd. Als het geheel getal niet is gedefinieerd, wordt er een **PSInvalidCastException** -uitzonde ring gegenereerd. |

## <a name="custom-conversions"></a>Aangepaste conversies

Als Power shell het type niet kan converteren met behulp van een standaard Power shell-taal conversieprogramma, wordt gecontroleerd op aangepaste conversie Programma's. Power shell zoekt naar verschillende typen aangepaste conversie Programma's in de volg orde die in deze sectie wordt beschreven. Houd er rekening mee dat verwijzingen naar de para meters **valueToConvert** en **resultType** verwijzen naar para meters van de- `ConvertTo(System.Object, System.Type)` methode. Als een aangepaste Converter een uitzonde ring genereert, wordt er geen verdere poging gedaan om het object te converteren en wordt de uitzonde ring in een **PSInvalidCastException** -uitzonde ring opgenomen die vervolgens wordt gegenereerd.

## <a name="powershell-type-converter"></a>Power shell-type Converter

Conversie Programma's van Power shell-typen worden gebruikt voor het converteren van één type of een familie van typen, zoals alle typen die zijn afgeleid van de klasse **System. enum** . Als u een Power shell-type Converter wilt maken, moet u een PSTypeConverter-klasse implementeren en die implementatie koppelen aan de doel klasse. Er zijn twee manieren om het Power shell-type Converter te koppelen aan de doel klasse.

- Via het type configuratie bestand
- Door het kenmerk **TypeConverterAttribute** toe te passen op de doel klasse

De Power shell-type conversieprogramma's die zijn afgeleid van de abstracte [PSTypeConverter](/dotnet/api/system.management.automation.pstypeconverter) -klasse, bieden methoden voor het converteren van een object naar een specifiek type of van een bepaald type. Als de para meter **valueToConvert** een object bevat waaraan een Power shell-type Converter is gekoppeld, roept Power shell de `PSTypeConverter.ConvertTo(System.Object, System.Type,System.IFormatProvider, System.Boolean)`
methode van het gekoppelde conversie programma om het object te converteren naar het type dat is opgegeven door de para meter **resultType** . Als de **resultType** -para meter verwijst naar een type waaraan een Power shell-type Converter is gekoppeld, roept Power shell de `PSTypeConverter.ConvertFrom(System.Object,System.Type, System.IFormatProvider, System.Boolean)`
methode van het gekoppelde conversie programma voor het converteren van het object van het type dat is opgegeven door de para meter **resultType** .

## <a name="system-type-converter"></a>Systeem type Converter

Conversie Programma's voor systeem typen worden gebruikt voor het converteren van een specifieke doel klasse. Dit type Converter kan niet worden gebruikt voor het converteren van een familie van klassen. Als u een systeem type Converter wilt maken, moet u een [TypeConverter](/dotnet/api/system.management.automation.runspaces.typedata.typeconverter#System_Management_Automation_Runspaces_TypeData_TypeConverter) -klasse implementeren en die implementatie koppelen aan de doel klasse. Er zijn twee manieren om het systeem type Converter te koppelen aan de doel klasse.

- Via het type configuratie bestand
- Door het kenmerk TypeConverterAttribute toe te passen op de doel klasse

## <a name="parse-converter"></a>Conversie programma parseren

Als de para meter **valueToConvert** een teken reeks is en het object type van de para meter **resultType** een `Parse` methode heeft, `Parse` wordt de methode aangeroepen om de teken reeks te converteren.

## <a name="constructor-converter"></a>Constructor-Converter

Als het object type van de para meter **resultType** een constructor heeft met één para meter van hetzelfde type als het object van de **valueToConvert** -para meter, wordt deze constructor aangeroepen.

## <a name="implicit-cast-operator-converter"></a>Conversie programma voor impliciete cast-operator

Als de para meter **valueToConvert** een impliciete cast-operator heeft die converteert naar een **resultType**, wordt de bijbehorende cast-operator aangeroepen. Als de **resultType** -para meter een impliciete cast-operator heeft die van **valueToConvert** wordt geconverteerd, wordt de conversie operator aangeroepen.

## <a name="explicit-cast-operator-converter"></a>Conversie programma voor expliciete conversie operator

Als de para meter **valueToConvert** een expliciete cast-operator heeft die converteert naar een **resultType**, wordt de bijbehorende cast-operator aangeroepen. Als de **resultType** -para meter een expliciete cast-operator heeft die van **valueToConvert** wordt geconverteerd, wordt de conversie operator aangeroepen.
