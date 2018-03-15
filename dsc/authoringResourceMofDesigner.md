---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: Het hulpprogramma voor het Resource-Designer
ms.openlocfilehash: c39b48f67d3874ee3cd2f2704aeb7390fa186fe4
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/15/2018
---
# <a name="using-the-resource-designer-tool"></a>Het hulpprogramma voor het Resource-Designer

> Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0

Het hulpprogramma Resource Designer is een set cmdlets die worden weergegeven door de **xDscResourceDesigner** module die eenvoudiger maken Windows PowerShell Desired State Configuration (DSC) van resources. De cmdlets in deze resource helpen bij het maken van het MOF-schema, de scriptmodule en de structuur van de map voor uw nieuwe resource. Zie voor meer informatie over DSC-resources [bouwen aangepaste Windows PowerShell Desired status configuratie Resources](authoringResource.md).
We gaan een DSC-resource die Active Directory-gebruikers beheert maken in dit onderwerp.
Gebruik de [Install-Module](https://technet.microsoft.com/library/dn807162.aspx) cmdlet voor het installeren van de **xDscResourceDesigner** module.

>**Opmerking**: **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0. U kunt downloaden via de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).

## <a name="creating-resource-properties"></a>Broneigenschappen maken
Het eerste wat dat we moeten doen is beslissen over de eigenschappen die de resource zal worden blootgesteld. Bijvoorbeeld definiëren we een Active Directory-gebruiker met de volgende eigenschappen.
 
De naam van de beschrijving
* **Gebruikersnaam**: sleutel van de eigenschap die een unieke identificatie van de gebruiker.
* **Zorg ervoor dat**: geeft aan of het gebruikersaccount moet aanwezig zijn of niet is opgegeven. Deze parameter heeft slechts twee mogelijke waarden zijn.
* **DomainCredential**: het wachtwoord voor de gebruiker.
* **Wachtwoord**: het gewenste wachtwoord voor de gebruiker toestaan dat een configuratie voor het gebruikerswachtwoord indien nodig wijzigen.

Voor het maken van de eigenschappen, gebruiken we de **nieuw xDscResourceProperty** cmdlet. De volgende PowerShell-opdrachten maken de eigenschappen die hierboven worden beschreven.

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential-Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a>De resource maken

Nu dat de resource-eigenschappen zijn gemaakt, noemen we de **nieuw xDscResource** cmdlet om de resource te maken. De **nieuw xDscResource** cmdlet wordt de lijst van eigenschappen als parameters. Het duurt ook het pad waar de module moet worden gemaakt, de naam van de nieuwe resource en de naam van de module waarin deze zich bevindt. De volgende PowerShell-opdracht maakt de resource.

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

De **nieuw xDscResource** cmdlet maakt het MOF-schema, het script van een geraamte resource, de vereiste mapstructuur voor uw nieuwe resource en een manifest voor de module die de nieuwe resource beschrijft.

Het MOF-schemabestand loopt **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, en de inhoud ervan zijn als volgt.

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

De resource-script is op **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**. Hierbij worden de werkelijke logica voor het implementeren van de resource die u zelf moet toevoegen. De inhoud van het geraamte script zijn als volgt.

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

Als u wilt toevoegen of wijzigen van de lijst met parameters van de bron, kunt u bellen de **Update xDscResource** cmdlet. De cmdlet werkt de resource met een lijst met nieuwe parameters. Als u al logica in uw script resource hebt toegevoegd, is het niet verwijderd.

Stel dat u wilt het laatste logboek opnemen in de tijd van de gebruiker in de resource. In plaats van de bron opnieuw volledig schrijft, roept u de **nieuw xDscResourceProperty** naar de nieuwe eigenschap maken en deze vervolgens aanroepen **Update xDscResource** en uw nieuwe eigenschap toevoegen aan de lijst van eigenschappen.

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a>Testen van een resource-schema

Het hulpprogramma Resource Designer wordt één meer cmdlet die kan worden gebruikt voor het testen van de geldigheid van een MOF-schema dat u handmatig hebt geschreven. Roep de **Test xDscSchema** cmdlet, het pad van een resource MOF schema wordt doorgegeven als parameter. De uitvoer van de cmdlet worden eventuele fouten in het schema.

### <a name="see-also"></a>Zie ook

#### <a name="concepts"></a>Concepten
[Aangepaste Windows PowerShell Desired State Configuration Resources bouwen](authoringResource.md)

#### <a name="other-resources"></a>Andere bronnen
[xDscResourceDesigner Module](https://powershellgallery.com/packages/xDscResourceDesigner)