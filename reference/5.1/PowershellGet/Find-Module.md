---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: 8b17019932df5b2cad68a9ea382387451d1b22e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250249"
---
# Find-Module

## SAMENVATTING
Hiermee worden modules in een opslag plaats gevonden die overeenkomen met opgegeven criteria.

## SYNTAXIS

### Alles

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## BESCHRIJVING

De `Find-Module` cmdlet vindt modules in een opslag plaats die overeenkomen met de opgegeven criteria.
`Find-Module` retourneert een **PSRepositoryItemInfo** -object voor elke module die wordt gevonden. De objecten kunnen naar de-cmdlets in de pijp lijn worden verzonden `Install-Module` .

De eerste keer dat `Find-Module` u een opslag plaats probeert te gebruiken, wordt u mogelijk gevraagd om updates te installeren.
Als de opslagplaats bron niet is geregistreerd bij de `Register-PSRepository` cmdlet, wordt een fout geretourneerd.

`Find-Module` retourneert de nieuwste versie van een module als er geen para meters worden gebruikt die de versie beperken. Als u de lijst met de versies van een module wilt ophalen, gebruikt u de para meter **AllVersions**.

Als de para meter **MinimumVersion** is opgegeven, `Find-Module` retourneert de versie van de module die gelijk is aan of groter is dan de minimum waarde. Als er een nieuwere versie beschikbaar is in de opslag plaats, wordt de nieuwere versie geretourneerd.

Als de para meter **MaximumVersion** is opgegeven, `Find-Module` retourneert de nieuwste versie van de module die de opgegeven versie niet overschrijdt.

Als de para meter **RequiredVersion** is opgegeven, `Find-Module` retourneert alleen de module versie die exact overeenkomt met de opgegeven versie. `Find-Module` doorzoekt alle beschik bare modules, omdat er naam conflicten tussen bronnen kunnen optreden.

De volgende voor beelden gebruiken de [PowerShell Gallery](https://www.powershellgallery.com/) als de enige geregistreerde opslag plaats. `Get-PSRepository` Hiermee worden de geregistreerde opslag plaatsen weer gegeven. Als u meerdere geregistreerde opslag plaatsen hebt, gebruikt u de `-Repository` para meter om de naam van de opslag plaats op te geven.

## VOORBEELDEN

### Voor beeld 1: een module op naam zoeken

In dit voor beeld wordt een module in de standaard opslagplaats gevonden.

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven.

### Voor beeld 2: modules met vergelijk bare namen zoeken

In dit voor beeld wordt het `*` Joker teken sterretje () gebruikt om modules met vergelijk bare namen te vinden.

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

De `Find-Module` cmdlet gebruikt de para meter **name** met het `*` Joker teken sterretje () om alle modules te zoeken die **Power shell** bevatten.

### Voor beeld 3: een module op minimale versie zoeken

In dit voor beeld wordt gezocht naar de minimale versie van een module. Als de opslag plaats een nieuwere versie van de module bevat, wordt de nieuwere versie geretourneerd.

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. De **MinimumVersion** geeft versie **1.6.5**. `Find-Module` retourneert PowerShellGet-versie **2.1.0** omdat deze de minimale versie overschrijdt en de meest recente versie is.

### Voor beeld 4: een module zoeken op specifieke versie

In dit voor beeld wordt een object geretourneerd dat de specifieke versie van een module vertegenwoordigt. Als de opgegeven versie niet wordt gevonden, wordt er een fout geretourneerd.

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. De para meter **RequiredVersion** geeft versie **1.6.5**.

### Voor beeld 5: een module in een specifieke opslag plaats zoeken

In dit voor beeld wordt de para meter **repository** gebruikt om een module in een specifieke opslag plaats te vinden.

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

De `Find-Module` cmdlet gebruikt de para meter **name** om de **PowerShellGet** -module op te geven. De **opslagplaats** parameter geeft aan dat de **PSGallery** -opslag plaats moet worden doorzocht.

### Voor beeld 6: een module in meerdere opslag plaatsen zoeken

In dit voor beeld wordt de gebruikt `Register-PSRepository` om een opslag plaats op te geven. `Find-Module` maakt gebruik van de opslag plaats om een module te zoeken.

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

De `Register-PSRepository` cmdlet registreert een nieuwe opslag plaats. De para meter **name** wijst de naam **MySource** toe. De **SourceLocation** para meter geeft u het adres van de opslag plaats.

De `Find-Module` cmdlet gebruikt de para meter **name** met het `*` Joker teken sterretje () om de **Contoso** -module op te geven. De **opslagplaats** parameter geeft aan dat twee opslag plaatsen, **PSGallery** en **MySource** , moeten worden doorzocht.

### Voor beeld 7: een module zoeken die een DSC-resource bevat

Met deze opdracht worden modules geretourneerd die DSC-resources bevatten. De para meter **includes** heeft vier vooraf gedefinieerde functionaliteiten die worden gebruikt voor het doorzoeken van de opslag plaats. Gebruik tab-volt ooien om de vier functies weer te geven die worden ondersteund door de para meter **includes** .

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

De `Find-Module` cmdlet gebruikt de para meter **opslagplaats** om de opslag plaats, **PSGallery** te doorzoeken.
Met de para meter **includes** wordt **dscresource bieden** opgegeven. Dit is een functionaliteit die in de opslag plaats kan worden gezocht in de-para meter.

### Voor beeld 8: een module met een filter zoeken

In dit voor beeld wordt voor het zoeken naar modules een filter gebruikt om de opslag plaats te doorzoeken.

Voor een NuGet-opslag plaats zoekt de **filter** parameter de naam, de beschrijving en de labels voor het argument.

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

De `Find-Module` cmdlet gebruikt de **filter** parameter om de opslag plaats voor **AppDomain** te doorzoeken.

## PARAMETERS

### -AllowPrerelease

Bevat de resultaten modules die als voorlopige versie zijn gemarkeerd.

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

### -AllVersions

Hiermee geeft u alle versies van een module in de resultaten opneemt. U kunt de para meter **AllVersions** niet gebruiken met de para meters **MinimumVersion** , **MaximumVersion** of **RequiredVersion** .

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

### -Opdracht

Hiermee geeft u een matrix met opdrachten op die in modules moet worden gevonden. Een opdracht kan een functie of werk stroom zijn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Hiermee geeft u een gebruikers account op dat beschikt over rechten voor het installeren van een module voor een opgegeven pakket provider of bron.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Dscresource bieden

Hiermee geeft u de naam of een deel van de naam van modules die DSC-resources bevatten. U kunt per Power shell-conventies een **of** -zoek opdracht uitvoeren wanneer u meerdere argumenten opgeeft.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Hiermee geeft u een filter op op basis van de **Package Management** -specifieke zoek syntaxis. Voor NuGet-modules is deze para meter het equivalent van zoeken met behulp van de zoek balk op de [PowerShell Gallery](https://www.powershellgallery.com/) -website.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludeDependencies

Geeft aan dat deze bewerking alle modules bevat die afhankelijk zijn van de module die is opgegeven in de para meter **name** .

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

### -Bevat

Retourneert alleen de modules die specifieke soorten Power shell-functionaliteit bevatten. U kunt bijvoorbeeld alleen modules zoeken die **dscresource bieden** bevatten. De acceptabele waarden voor deze para meter zijn als volgt:

- Cmdlet
- Dscresource bieden
- Functie
- RoleCapability

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumVersion

Hiermee geeft u het maximum, of de meest recente versie van de module op die in de zoek resultaten moet worden meegenomen.
**MaximumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -MinimumVersion

Hiermee geeft u de minimale versie van de module op die in de resultaten moet worden meegenomen. **MinimumVersion** en **RequiredVersion** kunnen niet worden gebruikt in dezelfde opdracht.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Hiermee geeft u de namen van modules op waarnaar moet worden gezocht in de opslag plaats. Een door komma's gescheiden lijst met module namen wordt geaccepteerd. Joker tekens worden geaccepteerd.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Proxy

Hiermee geeft u een proxy server voor de aanvraag op in plaats van rechtstreeks verbinding te maken met de Internet resource.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u een gebruikers account op dat is gemachtigd voor het gebruik van de proxy server die is opgegeven door de para meter **proxy** .

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Opslag plaats

Gebruik de para meter **opslagplaats** om op te geven welke opslag plaats moet worden doorzocht op een module. Wordt gebruikt wanneer meerdere opslag plaatsen zijn geregistreerd. Accepteert een door komma's gescheiden lijst met opslag plaatsen. Als u een opslag plaats wilt registreren, gebruikt u `Register-PSRepository` . Gebruik om geregistreerde opslag plaatsen weer te geven `Get-PSRepository` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequiredVersion

Hiermee geeft u het exacte versie nummer van de module op die in de resultaten moet worden meegenomen. **RequiredVersion** kan niet worden gebruikt in dezelfde opdracht als **MinimumVersion** of **MaximumVersion**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -RoleCapability

Hiermee wordt een matrix met functie mogelijkheden opgegeven.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Tag

Hiermee geeft u een matrix met tags op. Voor beelden van tags zijn **DesiredStateConfiguration** , **DSC** , **DSCResourceKit** of **PSModule**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

## UITVOER

### PSRepositoryItemInfo

`Find-Module` Hiermee maakt u **PSRepositoryItemInfo** -objecten die de pijp lijn kunnen verzenden naar cmdlets zoals `Install-Module` .

## OPMERKINGEN

Deze cmdlet wordt uitgevoerd op Power shell 5,0 of latere versies van Windows Power shell, Windows 7 of Windows 2008 R2 en latere versies van Windows.

## GERELATEERDE KOPPELINGEN

[Get-PSRepository](Get-PSRepository.md)

[Installatie-module](Install-Module.md)

[Publish-Module](Publish-Module.md)

[Save-Module](Save-Module.md)

[Uninstall-module](Uninstall-Module.md)

[Update-Module](Update-Module.md)

[REGI ster-PSRepository](Register-PSRepository.md)
