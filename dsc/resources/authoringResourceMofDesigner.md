---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: Met behulp van de ontwerpfunctie voor Resource-hulpprogramma
ms.openlocfilehash: 3fd2f06cf46602ee30dd34f8e7bd77d3c92b808f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403976"
---
# <a name="using-the-resource-designer-tool"></a>Met behulp van de ontwerpfunctie voor Resource-hulpprogramma

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

De ontwerpfunctie voor Resource-hulpprogramma is een set cmdlets die worden weergegeven door de **xDscResourceDesigner** module die het maken van Windows PowerShell Desired State Configuration (DSC)-resources te vereenvoudigen. De cmdlets in deze resource te maken van het MOF-schema, de scriptmodule en de structuur van de map voor uw nieuwe resource. Zie voor meer informatie over DSC-resources [maken aangepaste Windows PowerShell Desired State Configuration Resources](authoringResource.md).
In dit onderwerp maken we een DSC-resource die wordt beheerd van Active Directory-gebruikers.
Gebruik de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet voor het installeren van de **xDscResourceDesigner** module.

>**Houd er rekening mee**: **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0. U kunt downloaden de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Het maken van resource-eigenschappen
Het eerste wat dat we moeten doen is beslissen over de eigenschappen die de resource wordt weergegeven. In dit voorbeeld definiëren we een Active Directory-gebruiker met de volgende eigenschappen.

Naam van de beschrijving
* **Gebruikersnaam**: Sleuteleigenschap die een unieke identificatie van de gebruiker.
* **Zorg ervoor dat**: Geeft aan of het gebruikersaccount moet aanwezig zijn of niet aanwezig. Deze parameter heeft slechts twee mogelijke waarden zijn.
* **DomainCredential**: Het domeinwachtwoord voor de gebruiker.
* **Wachtwoord**: Het gewenste wachtwoord voor de gebruiker om toe te staan een configuratie van het wachtwoord indien nodig wijzigen.

Voor het maken van de eigenschappen, gebruiken we de **New-xDscResourceProperty** cmdlet. De volgende PowerShell-opdrachten maken de eigenschappen die hierboven worden beschreven.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>Maken van de resource

Nu dat de resource-eigenschappen zijn gemaakt, noemen we de **New-xDscResource** cmdlet voor het maken van de resource. De **New-xDscResource** cmdlet gebruikt de lijst met eigenschappen als parameters. Het duurt ook het pad waar de module moet worden gemaakt, de naam van de nieuwe resource en de naam van de module waarin deze zich bevindt. De volgende PowerShell-opdracht wordt de resource gemaakt.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

De **New-xDscResource** met de cmdlet maakt het MOF-schema, een script minimale resource, de structuur van de vereiste map voor uw nieuwe resource en een manifest voor de module die wordt aangegeven dat de nieuwe resource.

Het MOF-bestand voor schema loopt **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, en de inhoud ervan zijn als volgt.

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

Het script resource loopt **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Deze omvatten niet de werkelijke logica voor het implementeren van de resource die u zelf moet toevoegen. De inhoud van de minimale script zijn als volgt.

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

## <a name="updating-the-resource"></a>Bijwerken van de resource

Als u wilt toevoegen of wijzigen van de lijst met parameters van de resource, belt u het **Update xDscResource** cmdlet. De cmdlet werkt de resource met een nieuwe parameterlijst. Als u al logische in uw script resource hebt toegevoegd, is het niet verwijderd.

Stel bijvoorbeeld dat u wilt het laatste logboek opnemen in de tijd van de gebruiker in de resource. In plaats van de resource opnieuw volledig schrijven, roept u de **New-xDscResourceProperty** voor het maken van de nieuwe eigenschap en roep vervolgens **Update xDscResource** en de nieuwe eigenschap toevoegen aan de lijst met eigenschappen.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testen van een resource-schema

Het hulpprogramma Resource Designer wordt aangegeven dat een meer cmdlet die kan worden gebruikt voor het testen van de geldigheid van een MOF-schema dat u handmatig hebt geschreven. Roep de **Test xDscSchema** cmdlet, het pad naar een MOF-resource-schema wordt doorgegeven als parameter. De uitvoer van de cmdlet worden eventuele fouten in het schema.

### <a name="see-also"></a>Zie ook

#### <a name="concepts"></a>Concepten
[Maken van aangepaste Windows PowerShell Desired State Configuration Resources](authoringResource.md)

#### <a name="other-resources"></a>Andere bronnen
[xDscResourceDesigner Module](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
