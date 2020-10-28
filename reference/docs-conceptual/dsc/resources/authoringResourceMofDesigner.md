---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Het hulp programma resource Designer gebruiken
description: Het hulp programma resource Designer is een set cmdlets die wordt weer gegeven door de xDscResourceDesigner-module, waardoor het maken van Power shell DSC-resources eenvoudiger wordt.
ms.openlocfilehash: efe36d045ac3fba3823cb1f812bb5761d238fdf1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656496"
---
# <a name="using-the-resource-designer-tool"></a>Het hulp programma resource Designer gebruiken

> Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0

Het hulp programma resource Designer is een set cmdlets die wordt weer gegeven door de **xDscResourceDesigner** -module, waardoor DSC-resources (desired state Configuration) van Windows Power shell eenvoudiger kunnen worden gemaakt. De cmdlets in deze resource helpen u bij het maken van het MOF-schema, de script module en de mapstructuur voor uw nieuwe resource. Zie voor meer informatie over DSC-resources [aangepaste Windows Power shell-configuratie bronnen voor de gewenste status bouwen](authoringResource.md). In dit artikel maken we een DSC-resource waarmee Active Directory gebruikers worden beheerd. Gebruik de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) om de **xDscResourceDesigner** -module te installeren.

## <a name="creating-resource-properties"></a>Resource-eigenschappen maken

Het eerste wat u moet doen, is beslissen over eigenschappen die de resource beschikbaar maakt. In dit voor beeld wordt een Active Directory gebruiker gedefinieerd met de volgende eigenschappen.

Parameter naam beschrijving

- **Gebruikers naam** : sleutel eigenschap die een unieke identificatie vormt van een gebruiker.
- **Zorg ervoor** : Hiermee geeft u op of het gebruikers account aanwezig of afwezig moet zijn. Deze para meter heeft slechts twee mogelijke waarden.
- **DomainCredential** : het domein wachtwoord voor de gebruiker.
- **Wacht woord** : het gewenste wacht woord voor de gebruiker, zodat een configuratie het gebruikers wachtwoord zo nodig kan wijzigen.

We gebruiken de-cmdlet om de eigenschappen te maken `New-xDscResourceProperty` . De volgende Power shell-opdrachten maken de eigenschappen die hierboven worden beschreven.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>De resource maken

Nu de resource-eigenschappen zijn gemaakt, kunnen we de cmdlet aanroepen `New-xDscResource` om de resource te maken. De `New-xDscResource` cmdlet haalt de lijst met eigenschappen op als para meters. Ook wordt het pad naar de module gemaakt, evenals de naam van de nieuwe resource en de naam van de module waarin deze zich bevindt. Met de volgende Power shell-opdracht wordt de resource gemaakt.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

`New-xDscResource`Met de cmdlet maakt u het MOF-schema, een skelet bron script, de vereiste Directory structuur voor uw nieuwe bron en een manifest voor de module die de nieuwe resource beschikbaar stelt.

Het MOF-schema bestand bevindt zich op `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof` en de inhoud is als volgt.

```
[ClassVersion("1.0.0.0"), FriendlyName("Demo_ADUser")]
class Demo_ADUser : OMI_BaseResource
{
  [Key] string UserName;
  [Write, ValueMap{"Present","Absent"}, Values{"Present","Absent"}] string Ensure;
  [Write, EmbeddedInstance("MSFT_Credential")] String DomainCredential;
  [Write, EmbeddedInstance("MSFT_Credential")] String Password;
};
```

Het bron script bevindt zich op `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1` .
Het bevat niet de werkelijke logica voor het implementeren van de resource, die u zelf moet toevoegen. De inhoud van het skelet script is als volgt.

```powershell
function Get-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Collections.Hashtable])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  <#
  $returnValue = @{
  UserName = [System.String]
  Ensure = [System.String]
  DomainAdminCredential = [System.Management.Automation.PSCredential]
  Password = [System.Management.Automation.PSCredential]
  }

  $returnValue
  #>
}

function Set-TargetResource
{
  [CmdletBinding()]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  #Include this line if the resource requires a system reboot.
  #$global:DSCMachineStatus = 1
}

function Test-TargetResource
{
  [CmdletBinding()]
  [OutputType([System.Boolean])]
  param
  (
    [parameter(Mandatory = $true)]
    [System.String]
    $UserName,

    [ValidateSet("Present","Absent")]
    [System.String]
    $Ensure,

    [System.Management.Automation.PSCredential]
    $DomainAdminCredential,

    [System.Management.Automation.PSCredential]
    $Password
  )

  #Write-Verbose "Use this cmdlet to deliver information about command processing."

  #Write-Debug "Use this cmdlet to write debug information while troubleshooting."

  <#
  $result = [System.Boolean]

  $result
  #>
}

Export-ModuleMember -Function *-TargetResource
```

## <a name="updating-the-resource"></a>De resource bijwerken

Als u de parameter lijst van de resource moet toevoegen of wijzigen, kunt u de cmdlet aanroepen `Update-xDscResource` . Met de cmdlet wordt de resource bijgewerkt met een nieuwe parameter lijst. Als u al logica hebt toegevoegd in uw bron script, blijft deze ongewijzigd.

Stel bijvoorbeeld dat u de laatste aanmeldings tijd voor de gebruiker wilt toevoegen aan de resource. In plaats van de resource helemaal opnieuw te schrijven, kunt u de `New-xDscResourceProperty` nieuwe eigenschap maken en vervolgens de `Update-xDscResource` nieuwe eigenschap aanroepen en toevoegen aan de lijst met eigenschappen.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Een resource schema testen

Het hulp programma resource designer toont een meer cmdlet die kan worden gebruikt om de geldigheid van een MOF-schema dat u hand matig hebt geschreven te testen. Roep de `Test-xDscSchema` cmdlet aan, waarbij het pad van een MOF-bron schema wordt door gegeven als para meter. Met de cmdlet worden eventuele fouten in het schema uitgevoerd.

### <a name="see-also"></a>Zie ook

#### <a name="concepts"></a>Concepten

[Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen](authoringResource.md)

#### <a name="other-resources"></a>Meer informatie

[xDscResourceDesigner-module](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
