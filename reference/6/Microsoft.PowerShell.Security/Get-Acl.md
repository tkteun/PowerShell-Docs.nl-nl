---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 018a1da2a3fd40a95d378a563cacd68a734d9cd6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93251213"
---
# Get-Acl

## SAMENVATTING
Hiermee haalt u de security descriptor voor een resource, zoals een bestand of register sleutel.

## SYNTAXIS

### ByPath (standaard)

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### ByInputObject

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## BESCHRIJVING

De `Get-Acl` cmdlet haalt objecten op die de security descriptor van een bestand of resource vertegenwoordigen. De security descriptor bevat de toegangs beheer lijsten (Acl's) van de resource. In de ACL worden de machtigingen opgegeven die gebruikers en gebruikers groepen hebben om toegang te krijgen tot de resource.

Vanaf Windows Power Shell 3,0 kunt u de para meter **input object** gebruiken `Get-Acl` om de security descriptor van objecten te verkrijgen die geen pad hebben.

## VOORBEELDEN

### Voor beeld 1: een ACL ophalen voor een map

In dit voor beeld wordt de security descriptor van de `C:\Windows` map opgehaald.

```powershell
Get-Acl C:\Windows
```

### Voor beeld 2: een ACL voor een map ophalen met behulp van joker tekens

In dit voor beeld worden het Power shell-pad en de SDDL opgehaald voor alle `.log` bestanden in de `C:\Windows` map waarvan de naam begint met `s` .

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

De opdracht gebruikt de `Get-Acl` cmdlet om objecten op te halen die de security descriptors van elk logboek bestand vertegenwoordigen. Er wordt een pijplijn operator ( `|` ) gebruikt om de resultaten naar de cmdlet te verzenden `Format-List` . De opdracht gebruikt de **eigenschaps** parameter van `Format-List` om alleen de **PsPath** -en **SDDL** -eigenschappen van elk security descriptor-object weer te geven.

Lijsten worden vaak gebruikt in Power shell, omdat lange waarden worden afgekapt in tabellen.

De **SDDL** -waarden zijn waardevol voor systeem beheerders, omdat ze eenvoudige teken reeksen zijn die alle gegevens in de security descriptor bevatten. Ze zijn zo eenvoudig te passeren en op te slaan, en ze kunnen worden geparseerd wanneer dit nodig is.

### Voor beeld 3: het aantal controle vermeldingen voor een ACL ophalen

In dit voor beeld worden de security descriptors opgehaald van de `.log` bestanden in de `C:\Windows` map waarvan de naam begint met `s` .

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

De **controle** parameter wordt gebruikt voor het ophalen van de controle records uit de SACL in het security descriptor.
Vervolgens wordt de `ForEach-Object` cmdlet gebruikt voor het tellen van het aantal controle records dat aan elk bestand is gekoppeld. Het resultaat is een lijst met getallen voor het aantal controle records voor elk logboek bestand.

### Voor beeld 4: een ACL ophalen voor een register sleutel

In dit voor beeld wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van de Control-subsleutel ( `HKLM:\SYSTEM\CurrentControlSet\Control` ) van het REGI ster op te halen.

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

De para meter **Path** geeft u de controle-subsleutel. Met de pijplijn operator ( `|` ) wordt de security descriptor door gegeven die `Get-Acl` wordt opgehaald met de `Format-List` opdracht. Hiermee worden de eigenschappen van de security descriptor als een lijst opgemaakt zodat ze gemakkelijk te lezen zijn.

### Voor beeld 5: een ACL ophalen met behulp van **input object**

In dit voor beeld wordt de para meter **input object** van gebruikt `Get-Acl` om de security descriptor van een object voor een opslag subsysteem op te halen.

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## PARAMETERS

### -Audit

Hiermee haalt u de controle gegevens voor de security descriptor op uit de SACL (System Access Control List).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uitsluiten

De opgegeven items worden wegge laten. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Hiermee geeft u een filter op in de indeling of taal van de provider. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider. Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

Hiermee worden alleen de opgegeven items opgehaald. De waarde van deze para meter komt in aanmerking voor de para meter **Path** . Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

Hiermee geeft u het pad naar een resource. `Get-Acl` Hiermee wordt de security descriptor opgehaald van de resource die wordt aangegeven door het pad. Joker tekens zijn toegestaan. Als u de para meter **Path** weglaat, `Get-Acl` wordt de security descriptor van de huidige map opgehaald.

De parameter naam ("pad") is optioneel.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Input object

Hiermee wordt de security descriptor voor het opgegeven object opgehaald. Voer een variabele in die het object of een opdracht bevat die het object ophaalt.

U kunt een object, met uitzonde ring van een pad, niet door sluizen naar `Get-Acl` . Gebruik in plaats daarvan de para meter **input object** expliciet in de opdracht.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Hiermee geeft u het pad naar een resource. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u het tussen enkele aanhalings tekens. Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. String

U kunt een teken reeks met een pad naar door sluizen `Get-Acl` .

## UITVOER

### System. Security. AccessControl. FileSecurity, System. Security. AccessControl. DirectorySecurity, System. Security. AccessControl. RegistrySecurity

`Get-Acl` retourneert een-object dat de door u opgehaalde Acl's vertegenwoordigt. Het object type is afhankelijk van het type toegangs beheer lijst.

## OPMERKINGEN

`Get-Acl`Geeft standaard het Power shell-pad naar de resource ( `<provider>::<resource-path>` ), de eigenaar van de resource en ' toegang ', een lijst (matrix) van de vermeldingen voor toegangs beheer in de discretionaire toegangs beheer lijst (DACL) voor de bron. De lijst met DACL'S wordt beheerd door de resource-eigenaar.

Wanneer u het resultaat opmaakt als een lijst, ( `Get-Acl | Format-List` ) naast het pad, de eigenaar en de toegangs lijst, worden in Power shell de volgende eigenschappen en eigenschaps waarden weer gegeven:

- **Groep** : de beveiligings groep van de eigenaar.
- **Controle** : een lijst (matrix) van vermeldingen in de System Access Control List (SACL). De SACL specificeert de typen toegangs pogingen waarvoor Windows controle records genereert.
- **SDDL** : de security descriptor van de resource die wordt weer gegeven in een enkele teken reeks in de Security Descriptor Definition Language-indeling. Power Shell maakt gebruik van de **GetSddlForm** -methode van security descriptors om deze gegevens op te halen.

Omdat `Get-Acl` het bestands systeem en register providers worden ondersteund, kunt u gebruiken `Get-Acl` om de ACL van bestandssysteem objecten, zoals bestanden en mappen, en register objecten, zoals register sleutels en vermeldingen, weer te geven.

## GERELATEERDE KOPPELINGEN

[Set-ACL](Set-Acl.md)
