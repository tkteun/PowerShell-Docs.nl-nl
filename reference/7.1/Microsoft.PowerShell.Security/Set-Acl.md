---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 314734957eea971338ac886ad82e9ce9eeb6a242
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346561"
---
# <span data-ttu-id="4ebfb-103">Set-Acl</span><span class="sxs-lookup"><span data-stu-id="4ebfb-103">Set-Acl</span></span>

## <span data-ttu-id="4ebfb-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="4ebfb-104">SYNOPSIS</span></span>
<span data-ttu-id="4ebfb-105">Hiermee wordt de security descriptor van een opgegeven item, zoals een bestand of een register sleutel, gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-105">Changes the security descriptor of a specified item, such as a file or a registry key.</span></span>

## <span data-ttu-id="4ebfb-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="4ebfb-106">SYNTAX</span></span>

### <span data-ttu-id="4ebfb-107">ByPath (standaard)</span><span class="sxs-lookup"><span data-stu-id="4ebfb-107">ByPath (Default)</span></span>

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4ebfb-108">ByInputObject</span><span class="sxs-lookup"><span data-stu-id="4ebfb-108">ByInputObject</span></span>

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4ebfb-109">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="4ebfb-109">ByLiteralPath</span></span>

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4ebfb-110">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="4ebfb-110">DESCRIPTION</span></span>

<span data-ttu-id="4ebfb-111">Met de `Set-Acl` cmdlet wordt de security descriptor van een opgegeven item, zoals een bestand of een register sleutel, gewijzigd om overeen te komen met de waarden in een security descriptor die u opgeeft.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-111">The `Set-Acl` cmdlet changes the security descriptor of a specified item, such as a file or a registry key, to match the values in a security descriptor that you supply.</span></span>

<span data-ttu-id="4ebfb-112">Als u wilt gebruiken `Set-Acl` , gebruikt u de para meter **Path** of **input object** om het item te identificeren waarvan u de security descriptor wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-112">To use `Set-Acl`, use the **Path** or **InputObject** parameter to identify the item whose security descriptor you want to change.</span></span> <span data-ttu-id="4ebfb-113">Vervolgens gebruikt u de para meters **AclObject** of **security descriptor** om een security descriptor op te geven met de waarden die u wilt Toep assen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-113">Then, use the **AclObject** or **SecurityDescriptor** parameters to supply a security descriptor that has the values you want to apply.</span></span> <span data-ttu-id="4ebfb-114">`Set-Acl` past de security descriptor toe die is opgegeven.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-114">`Set-Acl` applies the security descriptor that is supplied.</span></span> <span data-ttu-id="4ebfb-115">De waarde van de para meter **AclObject** wordt gebruikt als model en de waarden in de security descriptor van het item worden gewijzigd zodat deze overeenkomen met de waarden in de para meter **AclObject** .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-115">It uses the value of the **AclObject** parameter as a model and changes the values in the item's security descriptor to match the values in the **AclObject** parameter.</span></span>

## <span data-ttu-id="4ebfb-116">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="4ebfb-116">EXAMPLES</span></span>

### <span data-ttu-id="4ebfb-117">Voor beeld 1: een security descriptor van het ene naar het andere bestand kopiëren</span><span class="sxs-lookup"><span data-stu-id="4ebfb-117">Example 1: Copy a security descriptor from one file to another</span></span>

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

<span data-ttu-id="4ebfb-118">Met deze opdrachten worden de waarden van de security descriptor van het Dog.txt bestand gekopieerd naar de security descriptor van het Cat.txt-bestand.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-118">These commands copy the values from the security descriptor of the Dog.txt file to the security descriptor of the Cat.txt file.</span></span> <span data-ttu-id="4ebfb-119">Wanneer de opdrachten zijn voltooid, zijn de security descriptors van de Dog.txt-en Cat.txt-bestanden identiek.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-119">When the commands complete, the security descriptors of the Dog.txt and Cat.txt files are identical.</span></span>

<span data-ttu-id="4ebfb-120">Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>
<span data-ttu-id="4ebfb-121">De toewijzings operator ( `=` ) slaat de security descriptor op in de waarde van de $DogACL variabele.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-121">The assignment operator (`=`) stores the security descriptor in the value of the $DogACL variable.</span></span>

<span data-ttu-id="4ebfb-122">Met de tweede opdracht worden `Set-Acl` de waarden in de ACL van Cat.txt gewijzigd in de waarden in `$DogACL` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-122">The second command uses `Set-Acl` to change the values in the ACL of Cat.txt to the values in `$DogACL`.</span></span>

<span data-ttu-id="4ebfb-123">De waarde van de para meter **Path** is het pad naar het Cat.txt bestand.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-123">The value of the **Path** parameter is the path to the Cat.txt file.</span></span> <span data-ttu-id="4ebfb-124">De waarde van de para meter **AclObject** is de model-ACL, in dit geval de acl van Dog.txt als opgeslagen in de `$DogACL` variabele.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-124">The value of the **AclObject** parameter is the model ACL, in this case, the ACL of Dog.txt as saved in the `$DogACL` variable.</span></span>

### <span data-ttu-id="4ebfb-125">Voor beeld 2: de pijplijn operator gebruiken om een descriptor door te geven</span><span class="sxs-lookup"><span data-stu-id="4ebfb-125">Example 2: Use the pipeline operator to pass a descriptor</span></span>

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

<span data-ttu-id="4ebfb-126">Deze opdracht is bijna hetzelfde als de opdracht in het vorige voor beeld, behalve dat er een pijplijn operator () wordt gebruikt `|` om de security descriptor te verzenden van een `Get-Acl` opdracht naar een `Set-Acl` opdracht.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-126">This command is almost the same as the command in the previous example, except that it uses a pipeline operator (`|`) to send the security descriptor from a `Get-Acl` command to a `Set-Acl` command.</span></span>

<span data-ttu-id="4ebfb-127">Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-127">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span> <span data-ttu-id="4ebfb-128">De pijplijn operator ( `|` ) geeft een object door dat de Dog.txt security descriptor aan de `Set-Acl` cmdlet vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-128">The pipeline operator (`|`) passes an object that represents the Dog.txt security descriptor to the `Set-Acl` cmdlet.</span></span>

<span data-ttu-id="4ebfb-129">Met de tweede opdracht wordt `Set-Acl` de security descriptor van Dog.txt toegepast op Cat.txt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-129">The second command uses `Set-Acl` to apply the security descriptor of Dog.txt to Cat.txt.</span></span>
<span data-ttu-id="4ebfb-130">Wanneer de opdracht is voltooid, zijn de Acl's van de Dog.txt-en Cat.txt-bestanden identiek.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-130">When the command completes, the ACLs of the Dog.txt and Cat.txt files are identical.</span></span>

### <span data-ttu-id="4ebfb-131">Voor beeld 3: een security descriptor Toep assen op meerdere bestanden</span><span class="sxs-lookup"><span data-stu-id="4ebfb-131">Example 3: Apply a security descriptor to multiple files</span></span>

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

<span data-ttu-id="4ebfb-132">Met deze opdrachten worden de security descriptors in het File0.txt-bestand toegepast op alle tekst bestanden in de `C:\Temp` map en alle submappen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-132">These commands apply the security descriptors in the File0.txt file to all text files in the `C:\Temp` directory and all of its subdirectories.</span></span>

<span data-ttu-id="4ebfb-133">Met de eerste opdracht wordt de security descriptor van het File0.txt-bestand in de huidige map opgehaald en wordt de toewijzings operator ( `=` ) gebruikt om deze op te slaan in de `$NewACL` variabele.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-133">The first command gets the security descriptor of the File0.txt file in the current directory and uses the assignment operator (`=`) to store it in the `$NewACL` variable.</span></span>

<span data-ttu-id="4ebfb-134">De eerste opdracht in de pijp lijn gebruikt de cmdlet Get-ChildItem om alle tekst bestanden in de map op te halen `C:\Temp` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-134">The first command in the pipeline uses the Get-ChildItem cmdlet to get all of the text files in the `C:\Temp` directory.</span></span> <span data-ttu-id="4ebfb-135">De **recursieve** para meter breidt de opdracht uit naar alle submappen van `C:\temp` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-135">The **Recurse** parameter extends the command to all subdirectories of `C:\temp`.</span></span> <span data-ttu-id="4ebfb-136">De para meter **include** beperkt de bestanden die worden opgehaald met de `.txt` bestands extensie.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-136">The **Include** parameter limits the files retrieved to those with the `.txt` file name extension.</span></span> <span data-ttu-id="4ebfb-137">Met de para meter **Force** worden verborgen bestanden opgehaald die anders zouden worden uitgesloten.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-137">The **Force** parameter gets hidden files, which would otherwise be excluded.</span></span> <span data-ttu-id="4ebfb-138">(U kunt niet gebruiken `c:\temp\*.txt` , omdat de para meter **recursief** werkt op directory's, niet op bestanden.)</span><span class="sxs-lookup"><span data-stu-id="4ebfb-138">(You cannot use `c:\temp\*.txt`, because the **Recurse** parameter works on directories, not on files.)</span></span>

<span data-ttu-id="4ebfb-139">De pijplijn operator ( `|` ) verzendt de objecten die de opgehaalde bestanden naar de `Set-Acl` cmdlet vertegenwoordigen, waarmee de security descriptor in de para meter **AclObject** wordt toegepast op alle bestanden in de pijp lijn.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-139">The pipeline operator (`|`) sends the objects representing the retrieved files to the `Set-Acl` cmdlet, which applies the security descriptor in the **AclObject** parameter to all of the files in the pipeline.</span></span>

<span data-ttu-id="4ebfb-140">In de praktijk is het raadzaam om de para meter **WhatIf** te gebruiken met alle `Set-Acl` opdrachten die van invloed kunnen zijn op meer dan één item.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-140">In practice, it is best to use the **WhatIf** parameter with all `Set-Acl` commands that can affect more than one item.</span></span> <span data-ttu-id="4ebfb-141">In dit geval zou de tweede opdracht in de pijp lijn zouden zijn `Set-Acl -AclObject $NewAcl -WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-141">In this case, the second command in the pipeline would be `Set-Acl -AclObject $NewAcl -WhatIf`.</span></span> <span data-ttu-id="4ebfb-142">Met deze opdracht worden de bestanden vermeld die worden beïnvloed door de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-142">This command lists the files that would be affected by the command.</span></span> <span data-ttu-id="4ebfb-143">Nadat u het resultaat hebt bekeken, kunt u de opdracht opnieuw uitvoeren zonder de para meter **WhatIf** .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-143">After reviewing the result, you can run the command again without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="4ebfb-144">Voor beeld 4: overname uitschakelen en overgenomen toegangs regels behouden</span><span class="sxs-lookup"><span data-stu-id="4ebfb-144">Example 4: Disable inheritance and preserve inherited access rules</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="4ebfb-145">Met deze opdrachten wordt de toegang tot overname vanuit bovenliggende mappen uitgeschakeld en blijven de bestaande overgenomen toegangs regels behouden.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-145">These commands is will disable access inheritance from parent folders, while still preserving the existing inherited access rules.</span></span>

<span data-ttu-id="4ebfb-146">Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-146">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="4ebfb-147">Vervolgens worden variabelen gemaakt om de overgenomen toegangs regels om te zetten in expliciete toegangs regels.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-147">Next, variables are created to convert the inherited access rules to explicit access rules.</span></span> <span data-ttu-id="4ebfb-148">Als u de toegangs regels die eraan zijn gekoppeld, wilt beveiligen, stelt `$isProtected` u de variabele in op `$true` . Als u overname wilt toestaan, stelt u `$isProtected` in `$false` op.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-148">To protect the access rules associated with this from inheritance, set the `$isProtected` variable to `$true`.to allow inheritance, set `$isProtected` to `$false`.</span></span> <span data-ttu-id="4ebfb-149">Zie [beveiliging van toegangs regels instellen](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-149">For more information, see [set access rule protection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection).</span></span>
<span data-ttu-id="4ebfb-150">De `$preserveInheritance` variabele is ingesteld op `$true` om overgenomen toegangs regels te behouden; ONWAAR om overgenomen toegangs regels te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-150">The `$preserveInheritance` variable set to `$true` to preserve inherited access rules; false to remove inherited access rules.</span></span> <span data-ttu-id="4ebfb-151">Vervolgens wordt de toegangs regel beveiliging bijgewerkt met de methode **SetAccessRuleProtection ()** .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-151">Then the access rule protection is updated using the **SetAccessRuleProtection()** method.</span></span>

<span data-ttu-id="4ebfb-152">De laatste opdracht wordt gebruikt `Set-Acl` om de security descriptor van toe te passen op Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-152">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="4ebfb-153">Wanneer de opdracht is voltooid, worden de Acl's van de Dog.txt die zijn overgenomen van de map huis dieren, rechtstreeks toegepast op Dog.txt en worden nieuwe beleids regels voor toegang tot Dog.txt niet gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-153">When the command completes, the ACLs of the Dog.txt that were inherited from the Pets folder will be applied directly to Dog.txt, and new access policies added to Pets will not change the access to Dog.txt.</span></span>

### <span data-ttu-id="4ebfb-154">Voor beeld 5: beheerders volledig beheer over het bestand geven</span><span class="sxs-lookup"><span data-stu-id="4ebfb-154">Example 5: Grant Administrators Full Control of the file</span></span>

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

<span data-ttu-id="4ebfb-155">Met deze opdracht wordt de groep **BUILTIN\Administrators** volledig beheer over het Dog.txt-bestand verleend.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-155">This command will grant the **BUILTIN\Administrators** group Full control of the Dog.txt file.</span></span>

<span data-ttu-id="4ebfb-156">Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor van het Dog.txt bestand op te halen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-156">The first command uses the `Get-Acl` cmdlet to get the security descriptor of the Dog.txt file.</span></span>

<span data-ttu-id="4ebfb-157">Volgende variabelen worden gemaakt om de groep **BUILTIN\Administrators** volledig beheer over het Dog.txt-bestand te geven.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-157">Next variables are created to grant the **BUILTIN\Administrators** group full control of the Dog.txt file.</span></span> <span data-ttu-id="4ebfb-158">De `$identity` variabele is ingesteld op de naam van een [gebruikers account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span><span class="sxs-lookup"><span data-stu-id="4ebfb-158">The `$identity` variable set to the name of a [user account](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor).</span></span> <span data-ttu-id="4ebfb-159">De `$fileSystemRights` variabele is ingesteld op FullControl en kan een van de [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) -waarden zijn die het type bewerking opgeeft dat is gekoppeld aan de toegangs regel.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-159">The `$fileSystemRights` variable set to FullControl, and can be any one of the [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) values that specifies the type of operation associated with the access rule.</span></span> <span data-ttu-id="4ebfb-160">De `$type` variabele is ingesteld op ' toestaan ' om aan te geven of de bewerking moet worden toegestaan of geweigerd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-160">The `$type` variable set to "Allow" to specifies whether to allow or deny the operation.</span></span> <span data-ttu-id="4ebfb-161">De `$fileSystemAccessRuleArgumentList` variabele is een lijst met argumenten die moet worden door gegeven bij het maken van het nieuwe **FileSystemAccessRule** -object.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-161">The `$fileSystemAccessRuleArgumentList` variable is an argument list is to be passed when making the new **FileSystemAccessRule** object.</span></span> <span data-ttu-id="4ebfb-162">Vervolgens wordt er een nieuw **FileSystemAccessRule** -object gemaakt en het **FileSystemAccessRule** -object wordt door gegeven aan de methode **SetAccessRule ()** , voegt de nieuwe toegangs regel toe.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-162">Then a new **FileSystemAccessRule** object is created, and the **FileSystemAccessRule** object is passed to the **SetAccessRule()** method, adds the new access rule.</span></span>

<span data-ttu-id="4ebfb-163">De laatste opdracht wordt gebruikt `Set-Acl` om de security descriptor van toe te passen op Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-163">The last command uses `Set-Acl` to apply the security descriptor of to Dog.txt.</span></span> <span data-ttu-id="4ebfb-164">Wanneer de opdracht is voltooid, heeft de **BUILTIN\Administrators** -groep volledig beheer over de Dog.txt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-164">When the command completes, the **BUILTIN\Administrators** group will have full control of the Dog.txt.</span></span>

## <span data-ttu-id="4ebfb-165">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4ebfb-165">PARAMETERS</span></span>

### <span data-ttu-id="4ebfb-166">-AclObject</span><span class="sxs-lookup"><span data-stu-id="4ebfb-166">-AclObject</span></span>

<span data-ttu-id="4ebfb-167">Hiermee geeft u een ACL met de gewenste eigenschaps waarden op.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-167">Specifies an ACL with the desired property values.</span></span> <span data-ttu-id="4ebfb-168">`Set-Acl` Hiermee wordt de ACL gewijzigd van het item dat is opgegeven door de para meter **Path** of **input object** , die overeenkomt met de waarden in het opgegeven beveiligings object.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-168">`Set-Acl` changes the ACL of item specified by the **Path** or **InputObject** parameter to match the values in the specified security object.</span></span>

<span data-ttu-id="4ebfb-169">U kunt de uitvoer van een `Get-Acl` opdracht in een variabele opslaan en vervolgens de para meter **AclObject** gebruiken om de variabele door te geven of een opdracht te typen `Get-Acl` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-169">You can save the output of a `Get-Acl` command in a variable and then use the **AclObject** parameter to pass the variable, or type a `Get-Acl` command.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4ebfb-170">-ClearCentralAccessPolicy</span><span class="sxs-lookup"><span data-stu-id="4ebfb-170">-ClearCentralAccessPolicy</span></span>

<span data-ttu-id="4ebfb-171">Hiermee verwijdert u het centrale toegangs beleid van het opgegeven item.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-171">Removes the central access policy from the specified item.</span></span>

<span data-ttu-id="4ebfb-172">Vanaf Windows Server 2012 kunnen beheerders Active Directory en groepsbeleid gebruiken om centraal toegangs beleid in te stellen voor gebruikers en groepen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-172">Beginning in Windows Server 2012, administrators can use Active Directory and Group Policy to set central access policies for users and groups.</span></span> <span data-ttu-id="4ebfb-173">Zie [Dynamic Access Control: scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)(Engelstalig) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-173">For more information, see [Dynamic Access Control: Scenario Overview](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview).</span></span>

<span data-ttu-id="4ebfb-174">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ebfb-175">-Uitsluiten</span><span class="sxs-lookup"><span data-stu-id="4ebfb-175">-Exclude</span></span>

<span data-ttu-id="4ebfb-176">De opgegeven items worden wegge laten.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-176">Omits the specified items.</span></span> <span data-ttu-id="4ebfb-177">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-177">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4ebfb-178">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-178">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4ebfb-179">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-179">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4ebfb-180">-Filter</span><span class="sxs-lookup"><span data-stu-id="4ebfb-180">-Filter</span></span>

<span data-ttu-id="4ebfb-181">Hiermee geeft u een filter op in de indeling of taal van de provider.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-181">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="4ebfb-182">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="4ebfb-183">De syntaxis van het filter, inclusief het gebruik van joker tekens, is afhankelijk van de provider.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-183">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="4ebfb-184">Filters zijn efficiënter dan andere para meters, omdat de provider deze toepast tijdens het ophalen van de objecten, in plaats van dat Power shell de objecten heeft gefilterd nadat ze zijn opgehaald.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-184">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4ebfb-185">-Include</span><span class="sxs-lookup"><span data-stu-id="4ebfb-185">-Include</span></span>

<span data-ttu-id="4ebfb-186">Hiermee worden alleen de opgegeven items gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-186">Changes only the specified items.</span></span> <span data-ttu-id="4ebfb-187">De waarde van deze para meter komt in aanmerking voor de para meter **Path** .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-187">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="4ebfb-188">Voer een element of patroon van een pad in, zoals `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-188">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="4ebfb-189">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-189">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="4ebfb-190">-Input object</span><span class="sxs-lookup"><span data-stu-id="4ebfb-190">-InputObject</span></span>

<span data-ttu-id="4ebfb-191">De security descriptor van het opgegeven object wijzigt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-191">Changes the security descriptor of the specified object.</span></span> <span data-ttu-id="4ebfb-192">Voer een variabele in die het object of een opdracht bevat die het object ophaalt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-192">Enter a variable that contains the object or a command that gets the object.</span></span>

<span data-ttu-id="4ebfb-193">U kunt het object dat u wilt wijzigen niet door sluizen `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-193">You cannot pipe the object to be changed to `Set-Acl`.</span></span> <span data-ttu-id="4ebfb-194">Gebruik in plaats daarvan de para meter **input object** expliciet in de opdracht.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-194">Instead, use the **InputObject** parameter explicitly in the command.</span></span>

<span data-ttu-id="4ebfb-195">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-195">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ebfb-196">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4ebfb-196">-LiteralPath</span></span>

<span data-ttu-id="4ebfb-197">Hiermee wordt de security descriptor van het opgegeven item gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-197">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="4ebfb-198">In tegens telling tot **Path** wordt de waarde van de para meter **LiteralPath** exact gebruikt wanneer deze wordt getypt.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-198">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="4ebfb-199">Geen tekens worden geïnterpreteerd als joker tekens.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-199">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="4ebfb-200">Als het pad escape tekens bevat, plaatst u dit tussen enkele aanhalings tekens ( `'` ).</span><span class="sxs-lookup"><span data-stu-id="4ebfb-200">If the path includes escape characters, enclose it in single quotation marks (`'`).</span></span>
<span data-ttu-id="4ebfb-201">Enkele aanhalings tekens geven aan dat Power shell geen karakters interpreteert als escape reeksen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="4ebfb-202">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4ebfb-203">-PassThru</span><span class="sxs-lookup"><span data-stu-id="4ebfb-203">-Passthru</span></span>

<span data-ttu-id="4ebfb-204">Retourneert een object dat staat voor de security descriptor die is gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-204">Returns an object that represents the security descriptor that was changed.</span></span> <span data-ttu-id="4ebfb-205">Deze cmdlet genereert standaard geen uitvoer.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-205">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="4ebfb-206">-Path</span><span class="sxs-lookup"><span data-stu-id="4ebfb-206">-Path</span></span>

<span data-ttu-id="4ebfb-207">Hiermee wordt de security descriptor van het opgegeven item gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-207">Changes the security descriptor of the specified item.</span></span> <span data-ttu-id="4ebfb-208">Geef het pad op naar een item, zoals een pad naar een bestand of register sleutel.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-208">Enter the path to an item, such as a path to a file or registry key.</span></span> <span data-ttu-id="4ebfb-209">Joker tekens zijn toegestaan.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-209">Wildcards are permitted.</span></span>

<span data-ttu-id="4ebfb-210">Als u een beveiligings object doorgeeft aan `Set-Acl` (met behulp van de para meters **AclObject** of **security descriptor** of door een beveiligings object door te geven van Get-Acl naar `Set-Acl` ) en u de para meter **Path** (naam en waarde) weglaat, `Set-Acl` wordt het pad gebruikt dat is opgenomen in het beveiligings object.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-210">If you pass a security object to `Set-Acl` (either by using the **AclObject** or **SecurityDescriptor** parameters or by passing a security object from Get-Acl to `Set-Acl`), and you omit the **Path** parameter (name and value), `Set-Acl` uses the path that is included in the security object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4ebfb-211">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4ebfb-211">-Confirm</span></span>

<span data-ttu-id="4ebfb-212">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-212">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4ebfb-213">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4ebfb-213">-WhatIf</span></span>

<span data-ttu-id="4ebfb-214">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-214">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4ebfb-215">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-215">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4ebfb-216">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ebfb-216">CommonParameters</span></span>

<span data-ttu-id="4ebfb-217">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-217">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ebfb-218">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-218">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4ebfb-219">INVOER</span><span class="sxs-lookup"><span data-stu-id="4ebfb-219">INPUTS</span></span>

### <span data-ttu-id="4ebfb-220">System. Security. AccessControl. ObjectSecurity, System. Security. AccessControl. CommonSecurityDescriptor</span><span class="sxs-lookup"><span data-stu-id="4ebfb-220">System.Security.AccessControl.ObjectSecurity, System.Security.AccessControl.CommonSecurityDescriptor</span></span>

<span data-ttu-id="4ebfb-221">U kunt een ACL-object of een security descriptor door sluizen naar `Set-Acl` .</span><span class="sxs-lookup"><span data-stu-id="4ebfb-221">You can pipe an ACL object or a security descriptor to `Set-Acl`.</span></span>

## <span data-ttu-id="4ebfb-222">UITVOER</span><span class="sxs-lookup"><span data-stu-id="4ebfb-222">OUTPUTS</span></span>

### <span data-ttu-id="4ebfb-223">System. Security. AccessControl. FileSecurity</span><span class="sxs-lookup"><span data-stu-id="4ebfb-223">System.Security.AccessControl.FileSecurity</span></span>

<span data-ttu-id="4ebfb-224">`Set-Acl`Er wordt standaard geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-224">By default, `Set-Acl` does not generate any output.</span></span> <span data-ttu-id="4ebfb-225">Als u echter de para meter **PassThru** gebruikt, wordt er een beveiligings object gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-225">However, if you use the **Passthru** parameter, it generates a security object.</span></span> <span data-ttu-id="4ebfb-226">Het type van het beveiligings object is afhankelijk van het type van het item.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-226">The type of the security object depends on the type of the item.</span></span>

## <span data-ttu-id="4ebfb-227">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="4ebfb-227">NOTES</span></span>

<span data-ttu-id="4ebfb-228">Deze cmdlet is alleen beschikbaar op Windows-platforms.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-228">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="4ebfb-229">De `Set-Acl` cmdlet wordt ondersteund door het Power shell-bestands systeem en de register providers.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-229">The `Set-Acl` cmdlet is supported by the PowerShell file system and registry providers.</span></span> <span data-ttu-id="4ebfb-230">Zo kunt u het gebruiken om de security descriptors van bestanden, directory's en register sleutels te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="4ebfb-230">As such, you can use it to change the security descriptors of files, directories, and registry keys.</span></span>

## <span data-ttu-id="4ebfb-231">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="4ebfb-231">RELATED LINKS</span></span>

[<span data-ttu-id="4ebfb-232">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="4ebfb-232">Get-Acl</span></span>](Get-Acl.md)

[<span data-ttu-id="4ebfb-233">FileSystemAccessRule</span><span class="sxs-lookup"><span data-stu-id="4ebfb-233">FileSystemAccessRule</span></span>](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[<span data-ttu-id="4ebfb-234">ObjectSecurity.SetAccessRuleProtection</span><span class="sxs-lookup"><span data-stu-id="4ebfb-234">ObjectSecurity.SetAccessRuleProtection</span></span>](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[<span data-ttu-id="4ebfb-235">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="4ebfb-235">FileSystemRights</span></span>](/dotnet/api/system.security.accesscontrol.filesystemrights)
