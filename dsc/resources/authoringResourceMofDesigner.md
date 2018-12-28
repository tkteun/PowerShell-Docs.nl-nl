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
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="b855e-103">Met behulp van de ontwerpfunctie voor Resource-hulpprogramma</span><span class="sxs-lookup"><span data-stu-id="b855e-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="b855e-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b855e-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b855e-105">De ontwerpfunctie voor Resource-hulpprogramma is een set cmdlets die worden weergegeven door de **xDscResourceDesigner** module die het maken van Windows PowerShell Desired State Configuration (DSC)-resources te vereenvoudigen.</span><span class="sxs-lookup"><span data-stu-id="b855e-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="b855e-106">De cmdlets in deze resource te maken van het MOF-schema, de scriptmodule en de structuur van de map voor uw nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="b855e-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="b855e-107">Zie voor meer informatie over DSC-resources [maken aangepaste Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="b855e-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="b855e-108">In dit onderwerp maken we een DSC-resource die wordt beheerd van Active Directory-gebruikers.</span><span class="sxs-lookup"><span data-stu-id="b855e-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="b855e-109">Gebruik de [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet voor het installeren van de **xDscResourceDesigner** module.</span><span class="sxs-lookup"><span data-stu-id="b855e-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="b855e-110">**Houd er rekening mee**: **Install-Module** is opgenomen in de **PowerShellGet** module die is opgenomen in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="b855e-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b855e-111">U kunt downloaden de **PowerShellGet** -module voor PowerShell 3.0 en 4.0 op [PackageManagement PowerShell-Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b855e-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="b855e-112">Het maken van resource-eigenschappen</span><span class="sxs-lookup"><span data-stu-id="b855e-112">Creating resource properties</span></span>
<span data-ttu-id="b855e-113">Het eerste wat dat we moeten doen is beslissen over de eigenschappen die de resource wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="b855e-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="b855e-114">In dit voorbeeld definiëren we een Active Directory-gebruiker met de volgende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b855e-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="b855e-115">Naam van de beschrijving</span><span class="sxs-lookup"><span data-stu-id="b855e-115">Parameter name  Description</span></span>
* <span data-ttu-id="b855e-116">**Gebruikersnaam**: Sleuteleigenschap die een unieke identificatie van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b855e-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="b855e-117">**Zorg ervoor dat**: Geeft aan of het gebruikersaccount moet aanwezig zijn of niet aanwezig.</span><span class="sxs-lookup"><span data-stu-id="b855e-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="b855e-118">Deze parameter heeft slechts twee mogelijke waarden zijn.</span><span class="sxs-lookup"><span data-stu-id="b855e-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="b855e-119">**DomainCredential**: Het domeinwachtwoord voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b855e-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="b855e-120">**Wachtwoord**: Het gewenste wachtwoord voor de gebruiker om toe te staan een configuratie van het wachtwoord indien nodig wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b855e-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="b855e-121">Voor het maken van de eigenschappen, gebruiken we de **New-xDscResourceProperty** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b855e-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="b855e-122">De volgende PowerShell-opdrachten maken de eigenschappen die hierboven worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="b855e-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet “Present”, “Absent”
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="b855e-123">Maken van de resource</span><span class="sxs-lookup"><span data-stu-id="b855e-123">Create the resource</span></span>

<span data-ttu-id="b855e-124">Nu dat de resource-eigenschappen zijn gemaakt, noemen we de **New-xDscResource** cmdlet voor het maken van de resource.</span><span class="sxs-lookup"><span data-stu-id="b855e-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="b855e-125">De **New-xDscResource** cmdlet gebruikt de lijst met eigenschappen als parameters.</span><span class="sxs-lookup"><span data-stu-id="b855e-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="b855e-126">Het duurt ook het pad waar de module moet worden gemaakt, de naam van de nieuwe resource en de naam van de module waarin deze zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="b855e-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="b855e-127">De volgende PowerShell-opdracht wordt de resource gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b855e-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path ‘C:\Program Files\WindowsPowerShell\Modules’ –ModuleName Demo_DSCModule
```

<span data-ttu-id="b855e-128">De **New-xDscResource** met de cmdlet maakt het MOF-schema, een script minimale resource, de structuur van de vereiste map voor uw nieuwe resource en een manifest voor de module die wordt aangegeven dat de nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="b855e-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="b855e-129">Het MOF-bestand voor schema loopt **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, en de inhoud ervan zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="b855e-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="b855e-130">Het script resource loopt **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span><span class="sxs-lookup"><span data-stu-id="b855e-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="b855e-131">Deze omvatten niet de werkelijke logica voor het implementeren van de resource die u zelf moet toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b855e-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="b855e-132">De inhoud van de minimale script zijn als volgt.</span><span class="sxs-lookup"><span data-stu-id="b855e-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="b855e-133">Bijwerken van de resource</span><span class="sxs-lookup"><span data-stu-id="b855e-133">Updating the resource</span></span>

<span data-ttu-id="b855e-134">Als u wilt toevoegen of wijzigen van de lijst met parameters van de resource, belt u het **Update xDscResource** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b855e-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="b855e-135">De cmdlet werkt de resource met een nieuwe parameterlijst.</span><span class="sxs-lookup"><span data-stu-id="b855e-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="b855e-136">Als u al logische in uw script resource hebt toegevoegd, is het niet verwijderd.</span><span class="sxs-lookup"><span data-stu-id="b855e-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="b855e-137">Stel bijvoorbeeld dat u wilt het laatste logboek opnemen in de tijd van de gebruiker in de resource.</span><span class="sxs-lookup"><span data-stu-id="b855e-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="b855e-138">In plaats van de resource opnieuw volledig schrijven, roept u de **New-xDscResourceProperty** voor het maken van de nieuwe eigenschap en roep vervolgens **Update xDscResource** en de nieuwe eigenschap toevoegen aan de lijst met eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b855e-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description “For mapping users to their last log on time”
Update-xDscResource –Name ‘Demo_ADUser’ –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="b855e-139">Testen van een resource-schema</span><span class="sxs-lookup"><span data-stu-id="b855e-139">Testing a resource schema</span></span>

<span data-ttu-id="b855e-140">Het hulpprogramma Resource Designer wordt aangegeven dat een meer cmdlet die kan worden gebruikt voor het testen van de geldigheid van een MOF-schema dat u handmatig hebt geschreven.</span><span class="sxs-lookup"><span data-stu-id="b855e-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="b855e-141">Roep de **Test xDscSchema** cmdlet, het pad naar een MOF-resource-schema wordt doorgegeven als parameter.</span><span class="sxs-lookup"><span data-stu-id="b855e-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="b855e-142">De uitvoer van de cmdlet worden eventuele fouten in het schema.</span><span class="sxs-lookup"><span data-stu-id="b855e-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="b855e-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b855e-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="b855e-144">Concepten</span><span class="sxs-lookup"><span data-stu-id="b855e-144">Concepts</span></span>
[<span data-ttu-id="b855e-145">Maken van aangepaste Windows PowerShell Desired State Configuration Resources</span><span class="sxs-lookup"><span data-stu-id="b855e-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="b855e-146">Andere bronnen</span><span class="sxs-lookup"><span data-stu-id="b855e-146">Other Resources</span></span>
[<span data-ttu-id="b855e-147">xDscResourceDesigner Module</span><span class="sxs-lookup"><span data-stu-id="b855e-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
