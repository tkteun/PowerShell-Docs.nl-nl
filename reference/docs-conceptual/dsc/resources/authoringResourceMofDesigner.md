---
ms.date: 07/08/2020
keywords: DSC, Power shell, configuratie, installatie
title: Het hulp programma resource Designer gebruiken
ms.openlocfilehash: 04fd2fbcc5afd9f1c7cbfaa44d6bdfde93bca399
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217488"
---
# <a name="using-the-resource-designer-tool"></a><span data-ttu-id="44301-103">Het hulp programma resource Designer gebruiken</span><span class="sxs-lookup"><span data-stu-id="44301-103">Using the Resource Designer tool</span></span>

> <span data-ttu-id="44301-104">Van toepassing op: Windows Power Shell 4,0, Windows Power shell 5,0</span><span class="sxs-lookup"><span data-stu-id="44301-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="44301-105">Het hulp programma resource Designer is een set cmdlets die wordt weer gegeven door de **xDscResourceDesigner** -module, waardoor DSC-resources (desired state Configuration) van Windows Power shell eenvoudiger kunnen worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="44301-105">The Resource Designer tool is a set of cmdlets exposed by the **xDscResourceDesigner** module that make creating Windows PowerShell Desired State Configuration (DSC) resources easier.</span></span> <span data-ttu-id="44301-106">De cmdlets in deze resource helpen u bij het maken van het MOF-schema, de script module en de mapstructuur voor uw nieuwe resource.</span><span class="sxs-lookup"><span data-stu-id="44301-106">The cmdlets in this resource help create the MOF schema, the script module, and the directory structure for your new resource.</span></span> <span data-ttu-id="44301-107">Zie voor meer informatie over DSC-resources [aangepaste Windows Power shell-configuratie bronnen voor de gewenste status bouwen](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="44301-107">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md).</span></span>
<span data-ttu-id="44301-108">In dit onderwerp gaan we een DSC-resource maken die Active Directory gebruikers beheert.</span><span class="sxs-lookup"><span data-stu-id="44301-108">In this topic, we will create a DSC resource that manages Active Directory users.</span></span> <span data-ttu-id="44301-109">Gebruik de cmdlet [install-module](/powershell/module/PowershellGet/Install-Module) om de **xDscResourceDesigner** -module te installeren.</span><span class="sxs-lookup"><span data-stu-id="44301-109">Use the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xDscResourceDesigner** module.</span></span>

## <a name="creating-resource-properties"></a><span data-ttu-id="44301-110">Resource-eigenschappen maken</span><span class="sxs-lookup"><span data-stu-id="44301-110">Creating resource properties</span></span>

<span data-ttu-id="44301-111">Het eerste wat u moet doen, is beslissen over eigenschappen die de resource beschikbaar maakt.</span><span class="sxs-lookup"><span data-stu-id="44301-111">The first thing we need to do is decide on properties that the resource will expose.</span></span> <span data-ttu-id="44301-112">In dit voor beeld wordt een Active Directory gebruiker gedefinieerd met de volgende eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="44301-112">For this example, we will define an Active Directory user with the following properties.</span></span>

<span data-ttu-id="44301-113">Parameter naam beschrijving</span><span class="sxs-lookup"><span data-stu-id="44301-113">Parameter name  Description</span></span>

- <span data-ttu-id="44301-114">**Gebruikers naam**: sleutel eigenschap die een unieke identificatie vormt van een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="44301-114">**UserName**: Key property that uniquely identifies a user.</span></span>
- <span data-ttu-id="44301-115">**Zorg ervoor**: Hiermee geeft u op of het gebruikers account aanwezig of afwezig moet zijn.</span><span class="sxs-lookup"><span data-stu-id="44301-115">**Ensure**: Specifies whether the user account should be Present or Absent.</span></span> <span data-ttu-id="44301-116">Deze para meter heeft slechts twee mogelijke waarden.</span><span class="sxs-lookup"><span data-stu-id="44301-116">This parameter will have only two possible values.</span></span>
- <span data-ttu-id="44301-117">**DomainCredential**: het domein wachtwoord voor de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="44301-117">**DomainCredential**: The domain password for the user.</span></span>
- <span data-ttu-id="44301-118">**Wacht woord**: het gewenste wacht woord voor de gebruiker, zodat een configuratie het gebruikers wachtwoord zo nodig kan wijzigen.</span><span class="sxs-lookup"><span data-stu-id="44301-118">**Password**: The desired password for the user to allow a configuration to change the user password if necessary.</span></span>

<span data-ttu-id="44301-119">We gebruiken de-cmdlet om de eigenschappen te maken `New-xDscResourceProperty` .</span><span class="sxs-lookup"><span data-stu-id="44301-119">To create the properties, we use the `New-xDscResourceProperty` cmdlet.</span></span> <span data-ttu-id="44301-120">De volgende Power shell-opdrachten maken de eigenschappen die hierboven worden beschreven.</span><span class="sxs-lookup"><span data-stu-id="44301-120">The following PowerShell commands create the properties described above.</span></span>

```powershell
$UserName = New-xDscResourceProperty –Name UserName -Type String -Attribute Key
$Ensure = New-xDscResourceProperty –Name Ensure -Type String -Attribute Write –ValidateSet "Present", "Absent"
$DomainCredential = New-xDscResourceProperty –Name DomainCredential -Type PSCredential -Attribute Write
$Password = New-xDscResourceProperty –Name Password -Type PSCredential -Attribute Write
```

## <a name="create-the-resource"></a><span data-ttu-id="44301-121">De resource maken</span><span class="sxs-lookup"><span data-stu-id="44301-121">Create the resource</span></span>

<span data-ttu-id="44301-122">Nu de resource-eigenschappen zijn gemaakt, kunnen we de cmdlet aanroepen `New-xDscResource` om de resource te maken.</span><span class="sxs-lookup"><span data-stu-id="44301-122">Now that the resource properties have been created, we can call the `New-xDscResource` cmdlet to create the resource.</span></span> <span data-ttu-id="44301-123">De `New-xDscResource` cmdlet haalt de lijst met eigenschappen op als para meters.</span><span class="sxs-lookup"><span data-stu-id="44301-123">The `New-xDscResource` cmdlet takes the list of properties as parameters.</span></span> <span data-ttu-id="44301-124">Ook wordt het pad naar de module gemaakt, evenals de naam van de nieuwe resource en de naam van de module waarin deze zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="44301-124">It also takes the path where the module should be created, the name of the new resource, and the name of the module in which it is contained.</span></span> <span data-ttu-id="44301-125">Met de volgende Power shell-opdracht wordt de resource gemaakt.</span><span class="sxs-lookup"><span data-stu-id="44301-125">The following PowerShell command creates the resource.</span></span>

```powershell
New-xDscResource –Name Demo_ADUser –Property $UserName, $Ensure, $DomainCredential, $Password –Path 'C:\Program Files\WindowsPowerShell\Modules' –ModuleName Demo_DSCModule
```

<span data-ttu-id="44301-126">`New-xDscResource`Met de cmdlet maakt u het MOF-schema, een skelet bron script, de vereiste Directory structuur voor uw nieuwe bron en een manifest voor de module die de nieuwe resource beschikbaar stelt.</span><span class="sxs-lookup"><span data-stu-id="44301-126">The `New-xDscResource` cmdlet creates the MOF schema, a skeleton resource script, the required directory structure for your new resource, and a manifest for the module that exposes the new resource.</span></span>

<span data-ttu-id="44301-127">Het MOF-schema bestand bevindt zich op `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof` en de inhoud is als volgt.</span><span class="sxs-lookup"><span data-stu-id="44301-127">The MOF schema file is at `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.schema.mof`, and its contents are as follows.</span></span>

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

<span data-ttu-id="44301-128">Het bron script bevindt zich op `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1` .</span><span class="sxs-lookup"><span data-stu-id="44301-128">The resource script is at `C:\Program Files\WindowsPowerShell\Modules\Demo_DSCModule\DSCResources\Demo_ADUser\Demo_ADUser.psm1`.</span></span>
<span data-ttu-id="44301-129">Het bevat niet de werkelijke logica voor het implementeren van de resource, die u zelf moet toevoegen.</span><span class="sxs-lookup"><span data-stu-id="44301-129">It does not include the actual logic to implement the resource, which you must add yourself.</span></span> <span data-ttu-id="44301-130">De inhoud van het skelet script is als volgt.</span><span class="sxs-lookup"><span data-stu-id="44301-130">The contents of the skeleton script are as follows.</span></span>

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

## <a name="updating-the-resource"></a><span data-ttu-id="44301-131">De resource bijwerken</span><span class="sxs-lookup"><span data-stu-id="44301-131">Updating the resource</span></span>

<span data-ttu-id="44301-132">Als u de parameter lijst van de resource moet toevoegen of wijzigen, kunt u de cmdlet aanroepen `Update-xDscResource` .</span><span class="sxs-lookup"><span data-stu-id="44301-132">If you need to add or modify the parameter list of the resource, you can call the `Update-xDscResource` cmdlet.</span></span> <span data-ttu-id="44301-133">Met de cmdlet wordt de resource bijgewerkt met een nieuwe parameter lijst.</span><span class="sxs-lookup"><span data-stu-id="44301-133">The cmdlet updates the resource with a new parameter list.</span></span> <span data-ttu-id="44301-134">Als u al logica hebt toegevoegd in uw bron script, blijft deze ongewijzigd.</span><span class="sxs-lookup"><span data-stu-id="44301-134">If you have already added logic in your resource script, it is left intact.</span></span>

<span data-ttu-id="44301-135">Stel bijvoorbeeld dat u de laatste aanmeldings tijd voor de gebruiker wilt toevoegen aan de resource.</span><span class="sxs-lookup"><span data-stu-id="44301-135">For example, suppose you want to include the last log in time for the user in our resource.</span></span> <span data-ttu-id="44301-136">In plaats van de resource helemaal opnieuw te schrijven, kunt u de `New-xDscResourceProperty` nieuwe eigenschap maken en vervolgens de `Update-xDscResource` nieuwe eigenschap aanroepen en toevoegen aan de lijst met eigenschappen.</span><span class="sxs-lookup"><span data-stu-id="44301-136">Rather than writing the resource again completely, you can call the `New-xDscResourceProperty` to create the new property, and then call `Update-xDscResource` and add your new property to the properties list.</span></span>

```powershell
$lastLogon = New-xDscResourceProperty –Name LastLogon –Type Hashtable –Attribute Write –Description "For mapping users to their last log on time"
Update-xDscResource –Name 'Demo_ADUser' –Property $UserName, $Ensure, $DomainCredential, $Password, $lastLogon -Force
```

## <a name="testing-a-resource-schema"></a><span data-ttu-id="44301-137">Een resource schema testen</span><span class="sxs-lookup"><span data-stu-id="44301-137">Testing a resource schema</span></span>

<span data-ttu-id="44301-138">Het hulp programma resource designer toont een meer cmdlet die kan worden gebruikt om de geldigheid van een MOF-schema dat u hand matig hebt geschreven te testen.</span><span class="sxs-lookup"><span data-stu-id="44301-138">The Resource Designer tool exposes one more cmdlet that can be used to test the validity of a MOF schema that you have written manually.</span></span> <span data-ttu-id="44301-139">Roep de `Test-xDscSchema` cmdlet aan, waarbij het pad van een MOF-bron schema wordt door gegeven als para meter.</span><span class="sxs-lookup"><span data-stu-id="44301-139">Call the `Test-xDscSchema` cmdlet, passing the path of a MOF resource schema as a parameter.</span></span> <span data-ttu-id="44301-140">Met de cmdlet worden eventuele fouten in het schema uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="44301-140">The cmdlet will output any errors in the schema.</span></span>

### <a name="see-also"></a><span data-ttu-id="44301-141">Zie ook</span><span class="sxs-lookup"><span data-stu-id="44301-141">See Also</span></span>

#### <a name="concepts"></a><span data-ttu-id="44301-142">Concepten</span><span class="sxs-lookup"><span data-stu-id="44301-142">Concepts</span></span>

[<span data-ttu-id="44301-143">Aangepaste Windows Power shell-configuratie bronnen voor desired state bouwen</span><span class="sxs-lookup"><span data-stu-id="44301-143">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)

#### <a name="other-resources"></a><span data-ttu-id="44301-144">Meer informatie</span><span class="sxs-lookup"><span data-stu-id="44301-144">Other Resources</span></span>

[<span data-ttu-id="44301-145">xDscResourceDesigner-module</span><span class="sxs-lookup"><span data-stu-id="44301-145">xDscResourceDesigner Module</span></span>](https://www.powershellgallery.com/packages/xDscResourceDesigner/1.12.0.0)
