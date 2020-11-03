---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 7550e2df319e5f195e65609ae29ebb00830ec8d2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250516"
---
# Export-ODataEndpointProxy

## SAMENVATTING
Genereert een module die cmdlets bevat voor het beheren van een OData-eind punt.

## SYNTAXIS

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESCHRIJVING

De `Export-ODataEndpointProxy` cmdlet gebruikt de meta gegevens van een OData-eind punt om een module te genereren die cmdlets bevat die u kunt gebruiken voor het beheren van het odata-eind punt. De module is gebaseerd op CDXML. Nadat deze cmdlet de module heeft gegenereerd, wordt die module opgeslagen in het pad en de bestands naam die is opgegeven door de para meter **OutputModule** .

`Export-ODataEndpointProxy` genereert cmdlets voor maken, lezen, bijwerken en verwijderen (ruwe) bewerkingen, niet-ruwe acties en koppelings manipulatie.

`Export-ODataEndpointProxy` Hiermee wordt één CDXML-bestand per eindpunt resource gegenereerd. U kunt deze CDXML-bestanden bewerken nadat de module is gegenereerd. Als u bijvoorbeeld de naam van de zelfstandig naam woord of de werk woorden wilt wijzigen van de cmdlets die u wilt uitlijnen met de naamgevings richtlijnen voor Windows Power shell-cmdlets, kunt u het bestand wijzigen.

Elke cmdlet in een gegenereerde module moet een **ConnectionURI** -para meter bevatten om verbinding te maken met het eind punt dat door de module wordt beheerd.

## VOORBEELDEN

### Voor beeld 1: een module genereren voor het beheren van een retail-webservice-eind punt

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

Met deze opdracht wordt een module gegenereerd voor het beheren van een retail service-eind punt. De opdracht geeft de URI van het eind punt en de URI van de meta gegevens van het eind punt. De opdracht biedt ook een uitvoerpad en script module naam als de waarde van de para meter **OutputModule** . Voor de waarde van de para meter **ResourceNameMapping** biedt de opdracht een hash-tabel waarmee de naam van de resource verzameling wordt toegewezen aan het gewenste zelfstandige woord voor de cmdlet-Set. In dit voor beeld zijn producten de naam van de resource verzameling en de **handels** plaats is het zelfstandige zelfstandig. Als u verbindingen met niet-SSL-sites, in plaats van HTTPS, wilt toestaan, voegt u de para meter **AllowUnsecureConnection** toe.

## PARAMETERS

### -AllowClobber

Geeft aan dat deze cmdlet een bestaande module vervangt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -AllowUnsecureConnection

Geeft aan dat deze module verbinding kan maken met Uri's die niet met SSL zijn beveiligd. De module kan HTTP-sites naast HTTPS-sites beheren.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CmdletAdapter

Hiermee geeft u de cmdlet-adapter op. De acceptabele waarden voor deze para meter zijn: ODataAdapter en NetworkControllerAdapter.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CreateRequestMethod

Hiermee geeft u de aanvraag methode op. De acceptabele waarden voor deze para meter zijn: PUT, POST en PATCH.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat toegang heeft tot het OData-eind punt. De standaard waarde is de huidige gebruiker. Als op een externe computer Windows Vista of een latere versie van het Windows-besturings systeem wordt uitgevoerd, vraagt de cmdlet u om referenties.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CustomData

Hiermee geeft u een hash-tabel met aangepaste gegevens op.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Force

Geeft aan dat deze cmdlet een bestaande gegenereerde module met dezelfde naam overschrijft in een bestaande `Modules` map.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Headers

Hiermee geeft u de kopteksten van de webaanvraag. Voer een hash-tabel of-woorden lijst in.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MetadataUri

Hiermee geeft u de URI op van de meta gegevens van het eind punt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OutputModule

Hiermee geeft u het pad en de module naam op waarmee deze cmdlet de gegenereerde module van proxy opdrachten opslaat.

Met deze cmdlet worden een binaire module, een module manifest en een opmaak bestand, indien van toepassing, gekopieerd naar de opgegeven map. Als u alleen de naam van de module opgeeft, wordt `Export-ODataEndpointProxy` de module opgeslagen in de `$home\Documents\WindowsPowerShell\Modules` map. Als u een pad opgeeft, maakt de cmdlet de map module in dat pad.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceNameMapping

Hiermee geeft u een hashtabel op die toewijzingen bevat waarmee u de gegenereerde cmdlets kunt aanpassen. In deze hashtabel is de naam van de resource verzameling de sleutel. De gewenste zelfstandige cmdlet is de waarde.

In de tabel hash `@{Products = 'Merchandise'}` is bijvoorbeeld de naam **Products** van de resource verzameling die fungeert als de sleutel. **Merchandisen** is de resulterende cmdlet-zelfstandig naam. De gegenereerde cmdlet-namen kunnen mogelijk niet worden uitgelijnd met de naamgevings richtlijnen voor Windows Power shell-cmdlets. U kunt het resource CDXML-bestand wijzigen om de namen van de cmdlets te wijzigen nadat deze cmdlet de module heeft gemaakt. Zie voor meer informatie [sterk aanbevolen ontwikkel richtlijnen](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UpdateRequestMethod

Hiermee geeft u de methode voor het bijwerken van aanvragen. De acceptabele waarden voor deze para meter zijn: PUT, POST en PATCH.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -URI

Hiermee geeft u de URI van het eind punt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
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

Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.
De cmdlet wordt niet uitgevoerd.

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

## UITVOER

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[OData-bibliotheek](https://technet.microsoft.com/windowsserver/hh525392(v=vs.85).aspx?f=255&MSPPError=-2147217396)

[Wat is het OData-Protocol?](https://www.odata.org/)

[Invoke-RestMethod](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
