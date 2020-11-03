---
description: Hierin worden de taal modi en hun effect op Power shell-sessies uitgelegd.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_modes?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Modes
ms.openlocfilehash: a75afd5149f3d290a8ec377417d4920b0ad6b526
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/13/2020
ms.locfileid: "93252602"
---
# <a name="about-language-modes"></a>Over taal modi

## <a name="short-description"></a>KORTE BESCHRIJVING
Hierin worden de taal modi en hun effect op Power shell-sessies uitgelegd.

## <a name="long-description"></a>LANGE BESCHRIJVING

De taal modus van een Power shell-sessie bepaalt, in deel, welke elementen van de Power shell-taal in de sessie kunnen worden gebruikt.

Power shell ondersteunt de volgende taal modi:

- FullLanguage
- ConstrainedLanguage (geïntroduceerd in Power Shell 3,0)
- RestrictedLanguage
- Geen taal

### <a name="what-is-a-language-mode"></a>WAT IS EEN TAAL MODUS?

De taal modus bepaalt de taal elementen die in de sessie zijn toegestaan.

De taal modus is in feite een eigenschap van de sessie configuratie (of eind punt) die wordt gebruikt om de sessie te maken. Alle sessies die gebruikmaken van een bepaalde sessie configuratie hebben de taal modus van de sessie configuratie.

Alle Power shell-sessies hebben een taal modus, met inbegrip van PSSessions die u maakt met behulp van de `New-PSSession` cmdlet, tijdelijke sessies die gebruikmaken van de para meter ComputerName en de standaard sessies die worden weer gegeven wanneer u Power shell start.

Externe sessies worden gemaakt met behulp van de sessie configuraties op de externe computer. De taal modus die in de sessie configuratie is ingesteld, bepaalt de taal modus van de sessie. Als u de sessie configuratie van een PSSession wilt opgeven, gebruikt u de para meter configuratiepad van cmdlets waarmee een sessie wordt gemaakt.

### <a name="language-modes"></a>TAAL MODI

In deze sectie worden de taal modi in Power shell-sessies beschreven.

#### <a name="full-language-fulllanguage"></a>VOLLEDIGE taal (FullLanguage)

In de FullLanguage-modus zijn alle taal elementen in de sessie toegestaan.
FullLanguage is de standaard taal modus voor standaard sessies in alle versies van Windows, met uitzonde ring van Windows RT.

#### <a name="restricted-language-restrictedlanguage"></a>BEPERKTE taal (RestrictedLanguage)

In de RestrictedLanguage-modus kunnen gebruikers opdrachten uitvoeren (cmdlets, functies, CIM-opdrachten en werk stromen), maar ze mogen geen script blokken gebruiken.

Standaard worden alleen de volgende variabelen toegestaan in de RestrictedLanguage-modus:

- `$PSCulture`
- `$PSUICulture`
- `$True`
- `$False`
- `$Null`

Alleen de volgende vergelijkings operatoren zijn toegestaan:

- `-eq` waard
- `-gt` (groter dan)
- `-lt` (kleiner dan)

Toewijzings instructies, verwijzingen naar eigenschappen en methode aanroepen zijn niet toegestaan.

#### <a name="no-language-nolanguage"></a>Geen taal (geen taal)

De modus voor alleen talen kan worden gebruikt via de API. De modus voor niet-talen betekent dat er geen script tekst van een formulier is toegestaan. Dit belet het gebruik van de methode **AddScript ()** waarmee fragmenten van het Power shell-script worden geparseerd en uitgevoerd. U kunt alleen **AddCommand ()** en **AddParameter ()** gebruiken die niet door de parser heen gaan.

#### <a name="constrained-language-constrained-language"></a>BEPERKTE taal (beperkte taal)

De ConstrainedLanguage-modus staat alle cmdlets en alle Power shell-taal elementen toe, maar beperkt de toegestane typen.

De ConstrainedLanguage-modus is ontworpen ter ondersteuning van UMCI (user mode code Integrity) in Windows RT. Dit is de enige ondersteunde taal modus in Windows RT, maar deze is beschikbaar op alle ondersteunde systemen.

UMCI beschermt ARM-apparaten door alleen door micro soft ondertekende en micro soft gecertificeerde apps te installeren op Windows RT-apparaten.
In de ConstrainedLanguage-modus wordt voor komen dat gebruikers Power shell gebruiken om UMCI te omzeilen of te schenden.

De functies van de ConstrainedLanguage-modus zijn als volgt:

- Alle cmdlets in Windows-modules en andere UMCI-goedgekeurde cmdlets zijn volledig functioneel en hebben volledige toegang tot systeem bronnen, behalve zoals vermeld.

- Alle elementen van de Power shell-script taal zijn toegestaan.

- Alle modules die in Windows zijn opgenomen, kunnen worden geïmporteerd en alle opdrachten die de modules exporteren worden uitgevoerd in de sessie.

- In Power shell workflow kunt u script werk stromen schrijven en uitvoeren (workflows die zijn geschreven in de Power shell-taal). Op XAML gebaseerde werk stromen worden niet ondersteund en u kunt XAML niet uitvoeren in een script werk stroom, bijvoorbeeld door te gebruiken `Invoke-Expression -Language XAML` . Werk stromen kunnen ook geen andere werk stromen aanroepen, hoewel geneste werk stromen zijn toegestaan.

- Met de `Add-Type` cmdlet kunnen ondertekende assembly's worden geladen, maar kan er geen wille keurige C#-code of Win32 api's worden geladen.

- De `New-Object` cmdlet kan alleen worden gebruikt voor toegestane typen (zie hieronder).

- Alleen toegestane typen (zie hieronder) kunnen worden gebruikt in Power shell. Andere typen zijn niet toegestaan.

- Type conversie is toegestaan, maar alleen als het resultaat een toegestaan type is.

- Cmdlet-para meters die de invoer van teken reeksen converteren naar typen werken alleen wanneer het resulterende type een toegestaan type is.

- De methode **toString ()** en de .net-methoden van toegestane typen (zie hieronder) kunnen worden aangeroepen. Andere methoden kunnen niet worden aangeroepen.

- Gebruikers kunnen alle eigenschappen van toegestane typen ophalen. Gebruikers kunnen de waarden van eigenschappen alleen instellen voor kern typen. Alleen de volgende COM-objecten zijn toegestaan:

  - **Scripting. Dictionary**
  - **Scripting. File System object**
  - **VBScript. RegExp**

De volgende typen zijn toegestaan in de ConstrainedLanguage-modus. Gebruikers kunnen eigenschappen ophalen, methoden aanroepen en objecten converteren naar deze typen.

Toegestane typen:

- AliasAttribute
- AllowEmptyCollectionAttribute
- AllowEmptyStringAttribute
- AllowNullAttribute
- Matrix
- Booleaanse waarde
- DBCS
- char
- CmdletBindingAttribute
- DateTime
- decimal
- Directory entry
- DirectorySearcher
- double
- float
- Guid
- Hashtabel
- int
- Int16
- long
- ManagementClass
- ManagementObject
- ManagementObjectSearcher
- NullString
- OutputTypeAttribute
- ParameterAttribute
- PSCredential
- PSDefaultValueAttribute
- PSListModifier
- PSObject
- PSPrimitiveDictionary
- PSReference
- PSTypeNameAttribute
- Reguliere
- SByte
- tekenreeks
- SupportsWildcardsAttribute
- SwitchParameter
- System. Globalization. Culture info
- Systeem .net. IPAddress
- Het e-mail adres van System .net. E-mail
- Systeem. numerics. BigInteger
- System. Security. SecureString
- TimeSpan
- UInt16
- UInt32
- UInt64

### <a name="finding-the-language-mode-of-a-session-configuration"></a>DE TAAL MODUS VAN EEN SESSIE CONFIGURATIE ZOEKEN

Wanneer een sessie configuratie is gemaakt met behulp van een sessie configuratie bestand, heeft de sessie configuratie een eigenschap LanguageMode. U kunt de taal modus vinden door de waarde van de eigenschap LanguageMode op te halen.

```powershell
(Get-PSSessionConfiguration -Name Test).LanguageMode
FullLanguage
```

Bij andere sessie configuraties kunt u de taal modus indirect vinden door de taal modus te zoeken van een sessie die is gemaakt met behulp van de sessie configuratie.

### <a name="finding-the-language-mode-of-a-session"></a>DE TAAL MODUS VAN EEN SESSIE ZOEKEN

U kunt de taal modus van een FullLanguage-of ConstrainedLanguage-sessie vinden door de waarde van de eigenschap LanguageMode van de sessie status op te halen.

Bijvoorbeeld:

```powershell
$ExecutionContext.SessionState.LanguageMode
ConstrainedLanguage
```

In sessies met RestrictedLanguage en de modus voor alleen talen kunt u de punt methode echter niet gebruiken voor het ophalen van eigenschaps waarden. In plaats daarvan wordt de taal modus in het fout bericht weer gegeven.

Wanneer u de `$ExecutionContext.SessionState.LanguageMode` opdracht uitvoert in een RestrictedLanguage-sessie, retourneert Power shell de PropertyReferenceNotSupportedInDataSection-en VariableReferenceNotSupportedInDataSection-fout berichten.

- PropertyReferenceNotSupportedInDataSection: verwijzingen naar eigenschappen zijn niet toegestaan in de modus voor een beperkte taal of een gegevens sectie.
- VariableReferenceNotSupportedInDataSection een variabele waarnaar niet kan worden verwezen in de modus voor een beperkte taal of waarnaar wordt verwezen in een gegevens sectie.

Wanneer u de `$ExecutionContext.SessionState.LanguageMode` opdracht in een niet-taal sessie uitvoert, retourneert Power shell het ScriptsNotAllowed-fout bericht.

- ScriptsNotAllowed: de syntaxis wordt niet ondersteund door deze runs Pace. Dit kan zijn omdat deze zich in een niet-taal modus bevindt.

## <a name="keywords"></a>WOORD

- about_ConstrainedLanguage
- about_FullLanguage
- about_NoLanguage
- about_RestrictedLanguage

## <a name="see-also"></a>ZIE OOK

- [about_Session_Configuration_Files](about_Session_Configuration_Files.md)
- [about_Session_Configurations](about_Session_Configurations.md)
