---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 3c8f26884ac0eda1ece799bbd49a7863b6d2239c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/03/2020
ms.locfileid: "93249767"
---
# Set-Acl

## SAMENVATTING
Hiermee wordt de security descriptor van een opgegeven item, zoals een bestand of een register sleutel, gewijzigd.

## SYNTAXIS

### ByPath (standaard)

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByInputObject

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

Met de `Set-Acl` cmdlet wordt de security descriptor van een opgegeven item, zoals een bestand of een register sleutel, gewijzigd om overeen te komen met de waarden in een security descriptor die u opgeeft.

Als u wilt gebruiken `Set-Acl` , gebruikt u de para meter **Path** of **input object** om het item te identificeren waarvan u de security descriptor wilt wijzigen. Vervolgens gebruikt u de para meters **AclObject** of **security descriptor** om een security descriptor op te geven met de waarden die u wilt Toep assen. `Set-Acl` past de security descriptor toe die is opgegeven. De waarde van de para meter **AclObject** wordt gebruikt als model en de waarden in de security descriptor van het item worden gewijzigd zodat deze overeenkomen met de waarden in de para meter **AclObject** .

## VOORBEELDEN

### Voor beeld 1: een security descriptor van het ene naar het andere bestand kopiëren

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

Met deze opdrachten worden de waarden van de security descriptor van het Dog.txt bestand gekopieerd naar de security descriptor van het Cat.txt-bestand. Wanneer de opdrachten zijn voltooid, zijn de security descriptors van de Dog.txt-en Cat.txt-bestanden identiek.

Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.
De toewijzings operator ( `=` ) slaat de security descriptor op in de waarde van de $DogACL variabele.

Met de tweede opdracht worden `Set-Acl` de waarden in de ACL van Cat.txt gewijzigd in de waarden in `$DogACL` .

De waarde van de para meter **Path** is het pad naar het Cat.txt bestand. De waarde van de para meter **AclObject** is de model-ACL, in dit geval de acl van Dog.txt als opgeslagen in de `$DogACL` variabele.

### Voor beeld 2: de pijplijn operator gebruiken om een descriptor door te geven

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

Deze opdracht is bijna hetzelfde als de opdracht in het vorige voor beeld, behalve dat er een pijplijn operator () wordt gebruikt `|` om de security descriptor te verzenden van een `Get-Acl` opdracht naar een `Set-Acl` opdracht.

Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen. De pijplijn operator ( `|` ) geeft een object door dat de Dog.txt security descriptor aan de `Set-Acl` cmdlet vertegenwoordigt.

Met de tweede opdracht wordt `Set-Acl` de security descriptor van Dog.txt toegepast op Cat.txt.
Wanneer de opdracht is voltooid, zijn de Acl's van de Dog.txt-en Cat.txt-bestanden identiek.

### Voor beeld 3: een security descriptor Toep assen op meerdere bestanden

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

Met deze opdrachten worden de security descriptors in het File0.txt-bestand toegepast op alle tekst bestanden in de `C:\Temp` map en alle submappen.

Met de eerste opdracht wordt de security descriptor van het File0.txt-bestand in de huidige map opgehaald en wordt de toewijzings operator ( `=` ) gebruikt om deze op te slaan in de `$NewACL` variabele.

De eerste opdracht in de pijp lijn gebruikt de cmdlet Get-ChildItem om alle tekst bestanden in de map op te halen `C:\Temp` . De **recursieve** para meter breidt de opdracht uit naar alle submappen van `C:\temp` . De para meter **include** beperkt de bestanden die worden opgehaald met de `.txt` bestands extensie. Met de para meter **Force** worden verborgen bestanden opgehaald die anders zouden worden uitgesloten. (U kunt niet gebruiken `c:\temp\*.txt` , omdat de para meter **recursief** werkt op directory's, niet op bestanden.)

De pijplijn operator ( `|` ) verzendt de objecten die de opgehaalde bestanden naar de `Set-Acl` cmdlet vertegenwoordigen, waarmee de security descriptor in de para meter **AclObject** wordt toegepast op alle bestanden in de pijp lijn.

In de praktijk is het raadzaam om de para meter **WhatIf** te gebruiken met alle `Set-Acl` opdrachten die van invloed kunnen zijn op meer dan één item. In dit geval zou de tweede opdracht in de pijp lijn zouden zijn `Set-Acl -AclObject $NewAcl -WhatIf` . Met deze opdracht worden de bestanden vermeld die worden beïnvloed door de opdracht. Nadat u het resultaat hebt bekeken, kunt u de opdracht opnieuw uitvoeren zonder de para meter **WhatIf** .

### Voor beeld 4: overname uitschakelen en overgenomen toegangs regels behouden

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

Met deze opdrachten wordt de toegang tot overname vanuit bovenliggende mappen uitgeschakeld en blijven de bestaande overgenomen toegangs regels behouden.

Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.

Vervolgens worden variabelen gemaakt om de overgenomen toegangs regels om te zetten in expliciete toegangs regels. Als u de toegangs regels die eraan zijn gekoppeld, wilt beveiligen, stelt `$isProtected` u de variabele in op `$true` . Als u overname wilt toestaan, stelt u `$isProtected` in `$false` op. Zie [beveiliging van toegangs regels instellen](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)voor meer informatie.
De `$preserveInheritance` variabele is ingesteld op `$true` om overgenomen toegangs regels te behouden; ONWAAR om overgenomen toegangs regels te verwijderen. Vervolgens wordt de toegangs regel beveiliging bijgewerkt met de methode **SetAccessRuleProtection ()** .

De laatste opdracht wordt gebruikt `Set-Acl` om de security descriptor van toe te passen op Dog.txt. Wanneer de opdracht is voltooid, worden de Acl's van de Dog.txt die zijn overgenomen van de map huis dieren, rechtstreeks toegepast op Dog.txt en worden nieuwe beleids regels voor toegang tot Dog.txt niet gewijzigd.

### Voor beeld 5: beheerders volledig beheer over het bestand geven

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

Met deze opdracht wordt de groep **BUILTIN\Administrators** volledig beheer over het Dog.txt-bestand verleend.

Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.

Volgende variabelen worden gemaakt om de groep **BUILTIN\Administrators** volledig beheer over het Dog.txt-bestand te geven. De `$identity` variabele is ingesteld op de naam van een [gebruikers account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).
De `$fileSystemRights` variabele is ingesteld op FullControl en kan een van de [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) -waarden zijn die het type bewerking opgeeft dat is gekoppeld aan de toegangs regel. De `$type` variabele is ingesteld op ' toestaan ' om aan te geven of de bewerking moet worden toegestaan of geweigerd. De `$fileSystemAccessRuleArgumentList` variabele is een lijst met argumenten die moet worden door gegeven bij het maken van het nieuwe **FileSystemAccessRule** -object. Vervolgens wordt er een nieuw **FileSystemAccessRule** -object gemaakt en het **FileSystemAccessRule** -object wordt door gegeven aan de methode **SetAccessRule ()** , voegt de nieuwe toegangs regel toe.

De laatste opdracht wordt gebruikt `Set-Acl` om de security descriptor van toe te passen op Dog.txt.
Wanneer de opdracht is voltooid, heeft de **BUILTIN\Administrators** -groep volledig beheer over de Dog.txt.

## PARAMETERS

### -AclObject

Hiermee geeft u een ACL met de gewenste eigenschaps waarden op. `Set-Acl` Hiermee wordt de ACL gewijzigd van het item dat is opgegeven door de para meter **Path** of **input object** , die overeenkomt met de waarden in het opgegeven beveiligings object.

U kunt de uitvoer van een `Get-Acl` opdracht in een variabele opslaan en vervolgens de para meter **AclObject** gebruiken om de variabele door te geven of een opdracht te typen `Get-Acl` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClearCentralAccessPolicy

Hiermee verwijdert u het centrale toegangs beleid van het opgegeven item.

Vanaf Windows Server 2012 kunnen beheerders Active Directory en groepsbeleid gebruiken om centraal toegangs beleid in te stellen voor gebruikers en groepen. Zie [Dynamic Access Control: scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)(Engelstalig) voor meer informatie.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
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

Hiermee worden alleen de opgegeven items gewijzigd. De waarde van deze para meter komt in aanmerking voor de para meter **Path** .
Voer een element of patroon van een pad in, zoals `*.txt` . Joker tekens zijn toegestaan.

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

### -Input object

De security descriptor van het opgegeven object wijzigt. Voer een variabele in die het object of een opdracht bevat die het object ophaalt.

U kunt het object dat u wilt wijzigen niet door sluizen `Set-Acl` . Gebruik in plaats daarvan de para meter **input object** expliciet in de opdracht.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Hiermee wordt de security descriptor van het opgegeven item gewijzigd. In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt. Geen tekens worden geïnterpreteerd als joker tekens. Als het pad escape tekens bevat, plaatst u dit tussen enkele aanhalings tekens ( `'` ).
Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.

Deze para meter is geïntroduceerd in Windows Power Shell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

Retourneert een object dat staat voor de security descriptor die is gewijzigd. Deze cmdlet genereert standaard geen uitvoer.

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

### -Path

Hiermee wordt de security descriptor van het opgegeven item gewijzigd. Geef het pad op naar een item, zoals een pad naar een bestand of register sleutel. Joker tekens zijn toegestaan.

Als u een beveiligings object doorgeeft aan `Set-Acl` (met behulp van de para meters **AclObject** of **security descriptor** of door een beveiligings object door te geven van Get-Acl naar `Set-Acl` ) en u de para meter **Path** (naam en waarde) weglaat, `Set-Acl` wordt het pad gebruikt dat is opgenomen in het beveiligings object.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Confirm

Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert. De cmdlet wordt niet uitgevoerd.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### System. Security. AccessControl. ObjectSecurity, System. Security. AccessControl. CommonSecurityDescriptor

U kunt een ACL-object of een security descriptor door sluizen naar `Set-Acl` .

## UITVOER

### System. Security. AccessControl. FileSecurity

`Set-Acl`Er wordt standaard geen uitvoer gegenereerd.
Als u echter de para meter **PassThru** gebruikt, wordt er een beveiligings object gegenereerd.
Het type van het beveiligings object is afhankelijk van het type van het item.

## OPMERKINGEN

 De `Set-Acl` cmdlet wordt ondersteund door het Power shell-bestands systeem en de register providers. Zo kunt u het gebruiken om de security descriptors van bestanden, directory's en register sleutels te wijzigen.

## GERELATEERDE KOPPELINGEN

[Get-ACL](Get-Acl.md)

[FileSystemAccessRule](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[ObjectSecurity.SetAccessRuleProtection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)
