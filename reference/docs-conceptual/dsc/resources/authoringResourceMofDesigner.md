---
ms.date: 06/12/2017
keywords: DSC, Power shell, configuratie, installatie
title: Het hulp programma resource Designer gebruiken
ms.openlocfilehash: 4f678f4586c75c830bf876b891fe4784aa3b4e95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941178"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="b0a65-103">Het hulp programma resource Designer gebruiken</span><span class="sxs-lookup"><span data-stu-id="b0a65-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="b0a65-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="b0a65-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b0a65-105">Het hulp programma resource Designer is een set cmdlets die wordt weer gegeven door de **xDscResourceDesigner** -module, waardoor DSC-resources (desired state Configuration) van Windows Power shell eenvoudiger kunnen worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b0a65-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="b0a65-106">De cmdlets in deze resource helpen u bij het maken van het MOF-schema, de script module en de mapstructuur voor uw nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="b0a65-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="b0a65-107">Zie voor meer informatie over DSC-resources [aangepaste Windows Power shell-configuratie bronnen voor de gewenste status bouwen](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="b0a65-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="b0a65-108">In dit onderwerp gaan we een DSC-resource maken die Active Directory gebruikers beheert.</span><span class="sxs-lookup"><span data-stu-id="b0a65-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span>
<span data-ttu-id="b0a65-109">Gebruik de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) om de **xDscResourceDesigner** -module te installeren.</span><span class="sxs-lookup"><span data-stu-id="b0a65-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

><span data-ttu-id="b0a65-110">**Opmerking**: **install-module** is opgenomen in de **PowerShellGet** -module, die is opgenomen in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="b0a65-110">**Note**: **Install-Module** is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="b0a65-111">U kunt de **PowerShellGet** -module voor power Shell 3,0 en 4,0 downloaden van [Package Management Power shell-modules preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="b0a65-111">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="b0a65-112">Resource-eigenschappen maken</span><span class="sxs-lookup"><span data-stu-id="b0a65-112">Creating resource properties</span></span>
<span data-ttu-id="b0a65-113">Het eerste wat u moet doen, is beslissen over eigenschappen die de resource beschikbaar maakt.</span><span class="sxs-lookup"><span data-stu-id="b0a65-113">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="b0a65-114">In dit voor beeld wordt een Active Directory gebruiker gedefinieerd met de volgende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="b0a65-114">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="b0a65-115">Parameter naam beschrijving</span><span class="sxs-lookup"><span data-stu-id="b0a65-115">Parameter name  Description</span></span>
* <span data-ttu-id="b0a65-116">**Gebruikers naam**: sleutel eigenschap die een unieke identificatie vormt van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b0a65-116">**UserName**: Key property that uniquely identifies a user.</span></span>
* <span data-ttu-id="b0a65-117">**Zorg ervoor**: Hiermee geeft u op of het gebruikers account aanwezig of afwezig moet zijn.</span><span class="sxs-lookup"><span data-stu-id="b0a65-117">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="b0a65-118">Deze para meter heeft slechts twee mogelijke waarden.</span><span class="sxs-lookup"><span data-stu-id="b0a65-118">This parameter will have only two possible values.</span></span>
* <span data-ttu-id="b0a65-119">**DomainCredential**: het domein wachtwoord voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="b0a65-119">**DomainCredential**: The domain password for the user.</span></span>
* <span data-ttu-id="b0a65-120">**Wacht woord**: het gewenste wacht woord voor de gebruiker, zodat een configuratie het gebruikers wachtwoord zo nodig kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b0a65-120">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="b0a65-121">We gebruiken de cmdlet **New-xDscResourceProperty** om de eigenschappen te maken.</span><span class="sxs-lookup"><span data-stu-id="b0a65-121">To create the properties, we use the **New-xDscResourceProperty** cmdlet.</span></span> <span data-ttu-id="b0a65-122">De volgende Power shell-opdrachten maken de eigenschappen die hierboven worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="b0a65-122">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="b0a65-123">De resource maken</span><span class="sxs-lookup"><span data-stu-id="b0a65-123">Create the resource</span></span>

<span data-ttu-id="b0a65-124">Nu de resource-eigenschappen zijn gemaakt, kunnen we de cmdlet **New-xDscResource** aanroepen om de resource te maken.</span><span class="sxs-lookup"><span data-stu-id="b0a65-124">Now that the resource properties have been created, we can call the **New-xDscResource** cmdlet to create the resource.</span></span> <span data-ttu-id="b0a65-125">De cmdlet **New-xDscResource** gebruikt de lijst met eigenschappen als para meters.</span><span class="sxs-lookup"><span data-stu-id="b0a65-125">The **New-xDscResource** cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="b0a65-126">Ook wordt het pad naar de module gemaakt, evenals de naam van de nieuwe resource en de naam van de module waarin deze zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="b0a65-126">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="b0a65-127">Met de volgende Power shell-opdracht wordt de resource gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b0a65-127">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="b0a65-128">Met de cmdlet **New-xDscResource** maakt u het MOF-schema, een skelet bron script, de vereiste Directory structuur voor uw nieuwe bron en een manifest voor de module die de nieuwe resource beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="b0a65-128">The **New-xDscResource** cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="b0a65-129">Het MOF-schema bestand bevindt zich in **C:\Program files\windowspowershell\modules\ Demo_DSCModule \dscresources\ Demo_ADUser \ Demo_ADUser. schema. MOF**en de inhoud ervan.</span><span class="sxs-lookup"><span data-stu-id="b0a65-129">The MOF schema file is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof**, and its contents are as follows.</span></span>

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

<span data-ttu-id="b0a65-130">Het bron script bevindt zich in **C:\Program files\windowspowershell\modules\ Demo_DSCModule \dscresources\ Demo_ADUser \ Demo_ADUser. psm1**.</span><span class="sxs-lookup"><span data-stu-id="b0a65-130">The resource script is at **C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1**.</span></span> <span data-ttu-id="b0a65-131">Het bevat niet de werkelijke logica voor het implementeren van de resource, die u zelf moet toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b0a65-131">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="b0a65-132">De inhoud van het skelet script is als volgt.</span><span class="sxs-lookup"><span data-stu-id="b0a65-132">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="b0a65-133">De resource bijwerken</span><span class="sxs-lookup"><span data-stu-id="b0a65-133">Updating the resource</span></span>

<span data-ttu-id="b0a65-134">Als u de parameter lijst van de resource moet toevoegen of wijzigen, kunt u de cmdlet **Update-xDscResource** aanroepen.</span><span class="sxs-lookup"><span data-stu-id="b0a65-134">If you need to add or modify the parameter list of the resource, you can call the **Update-xDscResource** cmdlet.</span></span> <span data-ttu-id="b0a65-135">Met de cmdlet wordt de resource bijgewerkt met een nieuwe parameter lijst.</span><span class="sxs-lookup"><span data-stu-id="b0a65-135">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="b0a65-136">Als u al logica hebt toegevoegd in uw bron script, blijft deze ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="b0a65-136">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="b0a65-137">Stel bijvoorbeeld dat u de laatste aanmeldings tijd voor de gebruiker wilt toevoegen aan de resource.</span><span class="sxs-lookup"><span data-stu-id="b0a65-137">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="b0a65-138">In plaats van de resource helemaal opnieuw te schrijven, kunt u de **New-xDscResourceProperty** aanroepen om de nieuwe eigenschap te maken, en vervolgens **Update-xDscResource** aanroepen en de nieuwe eigenschap aan de eigenschappen lijst toevoegen.</span><span class="sxs-lookup"><span data-stu-id="b0a65-138">Rather than writing the resource again completely, you can call the **New-xDscResourceProperty** to create the new property, and then call **Update-xDscResource** and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="b0a65-139">Een resource schema testen</span><span class="sxs-lookup"><span data-stu-id="b0a65-139">Testing a resource schema</span></span>

<span data-ttu-id="b0a65-140">Het hulp programma resource designer toont een meer cmdlet die kan worden gebruikt om de geldigheid van een MOF-schema dat u hand matig hebt geschreven te testen.</span><span class="sxs-lookup"><span data-stu-id="b0a65-140">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="b0a65-141">Roep de **test-xDscSchema-** cmdlet aan, waarbij het pad van een MOF-bron schema wordt door gegeven als para meter.</span><span class="sxs-lookup"><span data-stu-id="b0a65-141">Call the **Test-xDscSchema** cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="b0a65-142">Met de cmdlet worden eventuele fouten in het schema uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b0a65-142">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="b0a65-143">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b0a65-143">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="b0a65-144">Concepten</span><span class="sxs-lookup"><span data-stu-id="b0a65-144">Concepts</span></span>
[<span data-ttu-id="b0a65-145">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="b0a65-145">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="b0a65-146">Andere bronnen</span><span class="sxs-lookup"><span data-stu-id="b0a65-146">Other Resources</span></span>
[<span data-ttu-id="b0a65-147">xDscResourceDesigner-module</span><span class="sxs-lookup"><span data-stu-id="b0a65-147">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
