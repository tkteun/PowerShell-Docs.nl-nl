---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-cimsessionoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimSessionOption
ms.openlocfilehash: 6d926200ae923157c0b7d7556ef13400036b8437
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250056"
---
# New-CimSessionOption

## SAMENVATTING
Hiermee geeft u geavanceerde opties voor de cmdlet New-CimSession op.

## SYNTAXIS

### ProtocolTypeSet (standaard)

```
New-CimSessionOption [-Protocol] <ProtocolType> [-UICulture <CultureInfo>] [-Culture <CultureInfo>]
 [<CommonParameters>]
```

### WSManParameterSet

```
New-CimSessionOption [-NoEncryption] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-EncodePortInServicePrincipalName] [-Encoding <PacketEncoding>] [-HttpPrefix <Uri>]
 [-MaxEnvelopeSizeKB <UInt32>] [-ProxyAuthentication <PasswordAuthenticationMechanism>]
 [-ProxyCertificateThumbprint <String>] [-ProxyCredential <PSCredential>] [-ProxyType <ProxyType>]
 [-UseSsl] [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

### DcomParameterSet

```
New-CimSessionOption [-Impersonation <ImpersonationType>] [-PacketIntegrity] [-PacketPrivacy]
 [-UICulture <CultureInfo>] [-Culture <CultureInfo>] [<CommonParameters>]
```

## BESCHRIJVING

`New-CimSessionOption`Met de cmdlet maakt u een instantie van een CIM-sessie opties-object. U gebruikt een CIM-sessie opties object als invoer voor de `New-CimSession` cmdlet om de opties voor een CIM-sessie op te geven.

Deze cmdlet heeft twee parameter sets: één voor WsMan-opties en één voor opties voor gedistribueerde Component Object Model (DCOM). Afhankelijk van de para meters die u gebruikt, retourneert de cmdlet een exemplaar van DCOM-sessie opties of worden WsMan-sessie opties geretourneerd.

## VOORBEELDEN

### Voor beeld 1: een CIM-sessie opties-object maken voor DCOM

In dit voor beeld wordt een CIM-sessie opties-object voor het DCOM-protocol gemaakt en opgeslagen in een variabele met de naam `$so` . De inhoud van de variabele wordt vervolgens door gegeven aan de `New-CimSession` cmdlet.
`New-CimSession` maakt vervolgens een nieuwe CIM-sessie met de externe server met de naam Server01, met behulp van de opties die zijn gedefinieerd in de variabele.

```powershell
$so = New-CimSessionOption -Protocol DCOM
New-CimSession -ComputerName Server01 -SessionOption $so
```

### Voor beeld 2: een CIM-sessie opties-object maken voor WsMan

In dit voor beeld wordt een CIM-sessie opties-object gemaakt voor het WsMan-protocol. Het object bevat configuratie voor de verificatie modus van **Kerberos** dat is opgegeven door de para meter **ProxyAuthentication** , de referenties die zijn opgegeven door de para meter **ProxyCredential** en geeft aan dat de opdracht de CA-controle moet overs Laan, de CN-controle overs Laan en SSL gebruiken.

```powershell
New-CimSessionOption -ProxyAuthentication Kerberos -ProxyCredential $cred -SkipCACheck -SkipCNCheck -UseSsl
```

### Voor beeld 3: een CIM-sessie opties-object maken met de opgegeven cultuur

```powershell
New-CimSessionOption -Culture Fr-Fr -Protocol Wsman
```

In dit voor beeld wordt de cultuur opgegeven die wordt gebruikt voor de CIM-sessie. Standaard wordt de cultuur van de client gebruikt voor het uitvoeren van bewerkingen. De standaard cultuur kan echter worden overschreven met behulp van de para meter **Culture** .

## PARAMETERS

### -Cultuur

Hiermee geeft u de gebruikersinterface cultuur op die voor de CIM-sessie moet worden gebruikt. Geef de waarde voor deze para meter op met behulp van een van de volgende indelingen:

- Een cultuur naam in een `<languagecode2>-<country/regioncode2>` indeling zoals ' en-us '.
- Een variabele die een **Culture info** -object bevat.
- Een opdracht waarmee een **Culture info** -object wordt opgehaald, zoals [Get-Culture](../Microsoft.PowerShell.Utility/Get-Culture.md)

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -EncodePortInServicePrincipalName

Geeft aan dat de Kerberos-verbinding verbinding maakt met een service waarvan de Service Principal Name (SPN) het service poort nummer bevat. Dit type verbinding is niet gebruikelijk.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Encoding

Hiermee geeft u de code ring op die wordt gebruikt voor het WsMan-protocol. De acceptabele waarden voor deze para meter zijn: **standaard** , **utf8** of **Utf16**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PacketEncoding
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Utf8, Utf16

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -HttpPrefix

Hiermee geeft u het deel van de HTTP-URL achter de computer naam en het poort nummer op. Het wijzigen van dit is niet gebruikelijk. Standaard is de waarde van deze para meter **/wsman**.

```yaml
Type: System.Uri
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Imitatie

Hiermee maakt u een DCOM-sessie naar Windows Management Instrumentation (WMI) met behulp van imitatie.

Geldige waarden voor deze para meter zijn:

- Standaard: DCOM kan het imitatie niveau kiezen met behulp van het normale algoritme voor beveiligings onderhandeling.
- Geen: de client is anoniem voor de server. Het Server proces kan de client imiteren, maar het imitatie token bevat geen informatie en kan niet worden gebruikt.
- Identify: Hiermee kunnen objecten query's uitvoeren op de referenties van de aanroeper.
- Nabooten: Hiermee staat u toe dat objecten gebruikmaken van de referenties van de aanroeper.
- Gemachtigde: Hiermee kunnen objecten andere objecten de referenties van de aanroeper gebruiken.

Als **imitatie** niet is opgegeven, `New-CimSession` gebruikt de cmdlet de waarde **imiteren**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.ImpersonationType
Parameter Sets: DcomParameterSet
Aliases:
Accepted values: Default, None, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxEnvelopeSizeKB

Hiermee geeft u de maximale grootte van WsMan XML-berichten voor een van beide richtingen.

```yaml
Type: System.UInt32
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Geen versleuteling

Hiermee geeft u op dat gegevens versleuteling is uitgeschakeld.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketIntegrity

Specificeert dat de DCOM-sessie die is gemaakt met WMI, gebruikmaakt van de _PacketIntegrity_ -functionaliteit van Component Object Model (com). Standaard hebben alle CIM-sessies die zijn gemaakt met DCOM, de para meter **PacketIntegrity** ingesteld op **True**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PacketPrivacy

Hiermee maakt u een DCOM-sessie met WMI met behulp van de COM- _PacketPrivacy_. Standaard hebben alle CIM-sessies die zijn gemaakt met DCOM, de para meter **PacketPrivacy** ingesteld op **True**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DcomParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Hiermee geeft u het protocol op dat moet worden gebruikt. De acceptabele waarden voor deze para meter zijn: **DCOM** , **default** of **Wsman**.

```yaml
Type: Microsoft.Management.Infrastructure.CimCmdlets.ProtocolType
Parameter Sets: ProtocolTypeSet
Aliases:
Accepted values: Dcom, Default, Wsman

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyAuthentication

Hiermee geeft u de verificatie methode op die moet worden gebruikt voor het omzetten van de proxy. De acceptabele waarden voor deze para meter zijn: **standaard** , **Digest** , **Negotiate** , **Basic** , **Kerberos** , **NtlmDomain** of **CredSsp**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.PasswordAuthenticationMechanism
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: Default, Digest, Negotiate, Basic, Kerberos, NtlmDomain, CredSsp

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCertificateThumbprint

Hiermee geeft u het (x. 509) digitale open bare-sleutel certificaat van een gebruikers account voor proxy verificatie.
Voer de vinger afdruk van het certificaat in. Certificaten worden gebruikt in authenticatie op basis van client certificaten. Ze kunnen alleen worden toegewezen aan lokale gebruikers accounts en ze werken niet met domein accounts.

Als u een certificaat vingerafdruk wilt ophalen, gebruikt u de `Get-Item` `Get-ChildItem` cmdlets in het Power shell-certificaat: station.

```yaml
Type: System.String
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ProxyCredential

Hiermee geeft u de referenties op die moeten worden gebruikt voor proxy verificatie. Voer een van de volgende handelingen uit:

- Een variabele die een PSCredential-object bevat.
- Een opdracht waarmee een PSCredential-object wordt opgehaald, zoals `Get-Credential`

Als deze optie niet is ingesteld, kunt u geen referenties opgeven.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyType

Hiermee geeft u het mechanisme voor het omzetten van de naam van de host. De acceptabele waarden voor deze para meter zijn: **none** , **WinHttp** , **auto** of **InternetExplorer**.

De standaard waarde van deze para meter is **InternetExplorer**.

```yaml
Type: Microsoft.Management.Infrastructure.Options.ProxyType
Parameter Sets: WSManParameterSet
Aliases:
Accepted values: None, WinHttp, Auto, InternetExplorer

Required: False
Position: Named
Default value: InternetExplorer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCACheck

Geeft aan dat bij het maken van een verbinding via HTTPS door de client niet wordt gecontroleerd of het server certificaat is ondertekend door een vertrouwde certificerings instantie (CA).

Gebruik deze para meter alleen wanneer de externe computer wordt vertrouwd met een ander mechanisme, bijvoorbeeld wanneer de externe computer deel uitmaakt van een netwerk dat fysiek veilig en geïsoleerd is, of wanneer de externe computer wordt vermeld als een vertrouwde host in een WinRM-configuratie.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipCNCheck

Geeft aan dat de algemene naam (CN) van het certificaat van de server niet moet overeenkomen met de hostnaam van de server. Gebruik deze para meter alleen voor externe bewerkingen met vertrouwde computers die gebruikmaken van het HTTPS-protocol.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SkipRevocationCheck

Geeft aan dat de intrekkings controle voor server certificaten wordt overgeslagen. Gebruik deze para meter alleen voor vertrouwde computers.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UICulture

Hiermee geeft u de gebruikersinterface cultuur op die voor de CIM-sessie moet worden gebruikt. Geef de waarde voor deze para meter op met behulp van een van de volgende indelingen:

- Een cultuur naam in een `<languagecode2>-<country/regioncode2>` indeling zoals ' en-us '.
- Een variabele die een Culture info-object bevat.
- Een opdracht waarmee een Culture info-object wordt opgehaald, zoals `Get-Culture` .

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseSsl

Hiermee wordt aangegeven dat SSL moet worden gebruikt om een verbinding met de externe computer tot stand te brengen. Standaard wordt SSL niet gebruikt. Met WsMan wordt alle inhoud die via het netwerk wordt verzonden, versleuteld, zelfs wanneer HTTP wordt gebruikt.

Met deze para meter kunt u de aanvullende beveiliging van HTTPS in plaats van HTTP opgeven. Als SSL niet beschikbaar is op de poort die voor de verbinding wordt gebruikt en u deze para meter opgeeft, mislukt de opdracht.

U wordt aangeraden deze para meter alleen te gebruiken als de para meter **PacketPrivacy** niet is opgegeven.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WSManParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable. Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.

## INVOER

### Geen

Deze cmdlet accepteert geen invoer objecten.

## UITVOER

### CIMSessionOption

Met deze cmdlet wordt een object geretourneerd dat informatie over CIM-sessie opties bevat.

## OPMERKINGEN

## GERELATEERDE KOPPELINGEN

[Get-Child item](../microsoft.powershell.management/get-childitem.md)

[Get-Credential](../microsoft.powershell.security/get-credential.md)

[Get-cultuur](../microsoft.powershell.utility/get-culture.md)

[Get-item](../microsoft.powershell.management/get-item.md)

[New-CimSession](New-CimSession.md)
