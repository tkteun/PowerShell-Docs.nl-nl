---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 8552bec8029210553a8d4e51dcecb88948eb353e
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/01/2020
ms.locfileid: "93251881"
---
# <span data-ttu-id="38aa1-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="38aa1-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="38aa1-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="38aa1-104">SYNOPSIS</span></span>
<span data-ttu-id="38aa1-105">Hiermee wordt een SDDL-teken reeks geconverteerd naar een aangepast object.</span><span class="sxs-lookup"><span data-stu-id="38aa1-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="38aa1-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="38aa1-106">SYNTAX</span></span>

### <span data-ttu-id="38aa1-107">Alles</span><span class="sxs-lookup"><span data-stu-id="38aa1-107">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="38aa1-108">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="38aa1-108">DESCRIPTION</span></span>

<span data-ttu-id="38aa1-109">De `ConvertFrom-SddlString` cmdlet converteert een teken reeks met een definitie taal van een security descriptor naar een aangepast **PSCustomObject** -object met de volgende eigenschappen: owner, Group, DiscretionaryAcl, SystemAcl en RawDescriptor.</span><span class="sxs-lookup"><span data-stu-id="38aa1-109">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="38aa1-110">De eigenschappen owner, Group, DiscretionaryAcl en SystemAcl bevatten een lees bare tekst weergave van de toegangs rechten die zijn opgegeven in een SDDL-teken reeks.</span><span class="sxs-lookup"><span data-stu-id="38aa1-110">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="38aa1-111">Deze cmdlet is geïntroduceerd in Power shell 5,0.</span><span class="sxs-lookup"><span data-stu-id="38aa1-111">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="38aa1-112">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="38aa1-112">EXAMPLES</span></span>

### <span data-ttu-id="38aa1-113">Voor beeld 1: Converteer de SDDL van het bestands systeem toegangs rechten naar een PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="38aa1-113">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="38aa1-114">De eerste opdracht gebruikt de `Get-Acl` cmdlet om de security descriptor voor de map C:\Windows op te halen en op te vragen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="38aa1-114">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="38aa1-115">Met de tweede opdracht wordt de- `ConvertFrom-SddlString` cmdlet gebruikt om de tekst weergave van de SDDL-teken reeks op te halen, die is opgenomen in de SDDL-eigenschap van het object dat de security descriptor vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="38aa1-115">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="38aa1-116">Voor beeld 2: de SDDL van het REGI ster-toegangs rechten converteren naar een PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="38aa1-116">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="38aa1-117">Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor voor de sleutel HKLM: \ SOFTWARE\Microsoft\ op te halen en op te vragen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="38aa1-117">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="38aa1-118">Met de tweede opdracht wordt de- `ConvertFrom-SddlString` cmdlet gebruikt om de tekst weergave van de SDDL-teken reeks op te halen, die is opgenomen in de SDDL-eigenschap van het object dat de security descriptor vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="38aa1-118">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="38aa1-119">De `-Type` para meter wordt gebruikt om op te geven dat de SDDL-teken reeks een register security descriptor vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="38aa1-119">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="38aa1-120">Voor beeld 3: de SDDL van het register toegangs rechten converteren naar een PSCustomObject met behulp van ConvertFrom-SddlString met en zonder de `-Type` para meter</span><span class="sxs-lookup"><span data-stu-id="38aa1-120">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="38aa1-121">Met de eerste opdracht wordt de `Get-Acl` cmdlet gebruikt om de security descriptor voor de sleutel HKLM: \ SOFTWARE\Microsoft\ op te halen en op te vragen in de variabele.</span><span class="sxs-lookup"><span data-stu-id="38aa1-121">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="38aa1-122">Met de tweede opdracht wordt de- `ConvertFrom-SddlString` cmdlet gebruikt om de tekst weergave van de SDDL-teken reeks op te halen, die is opgenomen in de SDDL-eigenschap van het object dat de security descriptor vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="38aa1-122">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="38aa1-123">De para meter wordt niet gebruikt `-Type` , dus de toegangs rechten die worden weer gegeven, zijn voor bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="38aa1-123">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="38aa1-124">De derde opdracht gebruikt de `ConvertFrom-SddlString` cmdlet met de `-Type` para meter, zodat de geretourneerde toegangs rechten voor het REGI ster zijn.</span><span class="sxs-lookup"><span data-stu-id="38aa1-124">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="38aa1-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="38aa1-125">PARAMETERS</span></span>

### <span data-ttu-id="38aa1-126">-SDDL</span><span class="sxs-lookup"><span data-stu-id="38aa1-126">-Sddl</span></span>

<span data-ttu-id="38aa1-127">Hiermee geeft u de teken reeks voor de security descriptor in SDDL-syntaxis.</span><span class="sxs-lookup"><span data-stu-id="38aa1-127">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="38aa1-128">-Type</span><span class="sxs-lookup"><span data-stu-id="38aa1-128">-Type</span></span>

<span data-ttu-id="38aa1-129">Hiermee geeft u het type rechten op dat door de SDDL-teken reeks wordt vertegenwoordigd.</span><span class="sxs-lookup"><span data-stu-id="38aa1-129">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="38aa1-130">De aanvaardbare waarden voor deze parameter zijn:</span><span class="sxs-lookup"><span data-stu-id="38aa1-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="38aa1-131">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-131">FileSystemRights</span></span>
- <span data-ttu-id="38aa1-132">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-132">RegistryRights</span></span>
- <span data-ttu-id="38aa1-133">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-133">ActiveDirectoryRights</span></span>
- <span data-ttu-id="38aa1-134">MutexRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-134">MutexRights</span></span>
- <span data-ttu-id="38aa1-135">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-135">SemaphoreRights</span></span>
- <span data-ttu-id="38aa1-136">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-136">CryptoKeyRights</span></span>
- <span data-ttu-id="38aa1-137">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="38aa1-137">EventWaitHandleRights</span></span>

<span data-ttu-id="38aa1-138">De cmdlet maakt standaard gebruik van bestandssysteem rechten.</span><span class="sxs-lookup"><span data-stu-id="38aa1-138">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="38aa1-139">CryptoKeyRights en ActiveDirectoryRights worden niet ondersteund in Power shell core.</span><span class="sxs-lookup"><span data-stu-id="38aa1-139">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="38aa1-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="38aa1-140">CommonParameters</span></span>

<span data-ttu-id="38aa1-141">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="38aa1-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="38aa1-142">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="38aa1-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="38aa1-143">INVOER</span><span class="sxs-lookup"><span data-stu-id="38aa1-143">INPUTS</span></span>

### <span data-ttu-id="38aa1-144">System. String</span><span class="sxs-lookup"><span data-stu-id="38aa1-144">System.String</span></span>

<span data-ttu-id="38aa1-145">U kunt een SDDL-teken reeks door sluizen naar `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="38aa1-145">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="38aa1-146">UITVOER</span><span class="sxs-lookup"><span data-stu-id="38aa1-146">OUTPUTS</span></span>

## <span data-ttu-id="38aa1-147">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="38aa1-147">NOTES</span></span>

## <span data-ttu-id="38aa1-148">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="38aa1-148">RELATED LINKS</span></span>

[<span data-ttu-id="38aa1-149">Definitie taal van de security descriptor</span><span class="sxs-lookup"><span data-stu-id="38aa1-149">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)