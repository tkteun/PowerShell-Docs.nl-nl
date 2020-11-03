---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2020
ms.locfileid: "93250565"
---
# <span data-ttu-id="9757a-103">Reset-ComputerMachinePassword</span><span class="sxs-lookup"><span data-stu-id="9757a-103">Reset-ComputerMachinePassword</span></span>

## <span data-ttu-id="9757a-104">SAMENVATTING</span><span class="sxs-lookup"><span data-stu-id="9757a-104">SYNOPSIS</span></span>
<span data-ttu-id="9757a-105">Hiermee stelt u het wacht woord van het computer account voor de computer opnieuw in.</span><span class="sxs-lookup"><span data-stu-id="9757a-105">Resets the machine account password for the computer.</span></span>

## <span data-ttu-id="9757a-106">SYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9757a-106">SYNTAX</span></span>

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="9757a-107">BESCHRIJVING</span><span class="sxs-lookup"><span data-stu-id="9757a-107">DESCRIPTION</span></span>
<span data-ttu-id="9757a-108">De cmdlet **Reset-ComputerMachinePassword** wijzigt het wacht woord voor het computer account dat de computers gebruiken om te verifiëren bij de domein controllers in het domein.</span><span class="sxs-lookup"><span data-stu-id="9757a-108">The **Reset-ComputerMachinePassword** cmdlet changes the computer account password that the computers use to authenticate to the domain controllers in the domain.</span></span>
<span data-ttu-id="9757a-109">U kunt deze gebruiken om het wacht woord van de lokale computer opnieuw in te stellen.</span><span class="sxs-lookup"><span data-stu-id="9757a-109">You can use it to reset the password of the local computer.</span></span>

## <span data-ttu-id="9757a-110">VOORBEELDEN</span><span class="sxs-lookup"><span data-stu-id="9757a-110">EXAMPLES</span></span>

### <span data-ttu-id="9757a-111">Voor beeld 1: het wacht woord voor de lokale computer opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="9757a-111">Example 1: Reset the password for the local computer</span></span>

```
PS C:\> Reset-ComputerMachinePassword
```

<span data-ttu-id="9757a-112">Met deze opdracht wordt het computer wachtwoord voor de lokale computer opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="9757a-112">This command resets the computer password for the local computer.</span></span>
<span data-ttu-id="9757a-113">De opdracht wordt uitgevoerd met de referenties van de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9757a-113">The command runs with the credentials of the current user.</span></span>

### <span data-ttu-id="9757a-114">Voor beeld 2: het wacht woord voor de lokale computer opnieuw instellen met behulp van een opgegeven domein controller</span><span class="sxs-lookup"><span data-stu-id="9757a-114">Example 2: Reset the password for the local computer by using a specified domain controller</span></span>

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

<span data-ttu-id="9757a-115">Met deze opdracht wordt het computer wachtwoord van de lokale computer opnieuw ingesteld met behulp van de DC01-domein controller.</span><span class="sxs-lookup"><span data-stu-id="9757a-115">This command resets the computer password of the local computer by using the DC01 domain controller.</span></span>
<span data-ttu-id="9757a-116">De para meter *Credential* wordt gebruikt om een gebruikers account op te geven dat gemachtigd is om een computer wachtwoord opnieuw in te stellen in het domein.</span><span class="sxs-lookup"><span data-stu-id="9757a-116">It uses the *Credential* parameter to specify a user account that has permission to reset a computer password in the domain.</span></span>

### <span data-ttu-id="9757a-117">Voor beeld 3: het wacht woord opnieuw instellen op een externe computer</span><span class="sxs-lookup"><span data-stu-id="9757a-117">Example 3: Reset the password on a remote computer</span></span>

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

<span data-ttu-id="9757a-118">Met deze opdracht wordt de cmdlet Invoke-Command uitgevoerd om de opdracht **Reset-ComputerMachinePassword** uit te voeren op de externe computer met Server01.</span><span class="sxs-lookup"><span data-stu-id="9757a-118">This command uses the Invoke-Command cmdlet to run a **Reset-ComputerMachinePassword** command on the Server01 remote computer.</span></span>

<span data-ttu-id="9757a-119">Zie about_Remote en **invoke-Command** voor meer informatie over externe opdrachten in Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9757a-119">For more information about remote commands in Windows PowerShell, see about_Remote and **Invoke-Command**.</span></span>

## <span data-ttu-id="9757a-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9757a-120">PARAMETERS</span></span>

### <span data-ttu-id="9757a-121">-Credential</span><span class="sxs-lookup"><span data-stu-id="9757a-121">-Credential</span></span>
<span data-ttu-id="9757a-122">Hiermee geeft u een gebruikers account op dat is gemachtigd om deze actie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="9757a-122">Specifies a user account that has permission to perform this action.</span></span>
<span data-ttu-id="9757a-123">Standaard is dit de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="9757a-123">The default is the current user.</span></span>

<span data-ttu-id="9757a-124">Typ een gebruikers naam, zoals gebruiker01 of Domain01\User01, of voer een **PSCredential** -object in, zoals het account dat is gegenereerd door de cmdlet Get-Credential.</span><span class="sxs-lookup"><span data-stu-id="9757a-124">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the Get-Credential cmdlet.</span></span>
<span data-ttu-id="9757a-125">Als u een gebruikers naam typt, vraagt deze cmdlet u om een wacht woord.</span><span class="sxs-lookup"><span data-stu-id="9757a-125">If you type a user name, this cmdlet prompts you for a password.</span></span>

<span data-ttu-id="9757a-126">Deze para meter is geïntroduceerd in Windows Power Shell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9757a-126">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9757a-127">-Server</span><span class="sxs-lookup"><span data-stu-id="9757a-127">-Server</span></span>
<span data-ttu-id="9757a-128">Hiermee geeft u de naam op van een domein controller die moet worden gebruikt wanneer deze cmdlet het wacht woord van het computer account instelt.</span><span class="sxs-lookup"><span data-stu-id="9757a-128">Specifies the name of a domain controller to use when this cmdlet sets the computer account password.</span></span>

<span data-ttu-id="9757a-129">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="9757a-129">This parameter is optional.</span></span>
<span data-ttu-id="9757a-130">Als u deze para meter weglaat, wordt er een domein controller gekozen voor het onderhouden van de opdracht.</span><span class="sxs-lookup"><span data-stu-id="9757a-130">If you omit this parameter, a domain controller is chosen to service the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9757a-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9757a-131">-Confirm</span></span>
<span data-ttu-id="9757a-132">Hiermee wordt u gevraagd om bevestiging voordat u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9757a-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9757a-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9757a-133">-WhatIf</span></span>
<span data-ttu-id="9757a-134">Hiermee wordt weergegeven wat er zou gebeuren als u de cmdlet uitvoert.</span><span class="sxs-lookup"><span data-stu-id="9757a-134">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9757a-135">De cmdlet wordt niet uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="9757a-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9757a-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9757a-136">CommonParameters</span></span>
<span data-ttu-id="9757a-137">Deze cmdlet biedt ondersteuning voor de meest gebruikte parameters: -Debug, - ErrorAction, - ErrorVariable, - InformationAction, -InformationVariable, - OutVariable,-OutBuffer, - PipelineVariable - Verbose, - WarningAction en -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9757a-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9757a-138">Zie [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9757a-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9757a-139">INVOER</span><span class="sxs-lookup"><span data-stu-id="9757a-139">INPUTS</span></span>

### <span data-ttu-id="9757a-140">Geen</span><span class="sxs-lookup"><span data-stu-id="9757a-140">None</span></span>
<span data-ttu-id="9757a-141">U kunt geen invoer van een pipe naar deze cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9757a-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9757a-142">UITVOER</span><span class="sxs-lookup"><span data-stu-id="9757a-142">OUTPUTS</span></span>

### <span data-ttu-id="9757a-143">Geen</span><span class="sxs-lookup"><span data-stu-id="9757a-143">None</span></span>
<span data-ttu-id="9757a-144">Met deze cmdlet wordt geen uitvoer gegenereerd.</span><span class="sxs-lookup"><span data-stu-id="9757a-144">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9757a-145">OPMERKINGEN</span><span class="sxs-lookup"><span data-stu-id="9757a-145">NOTES</span></span>

## <span data-ttu-id="9757a-146">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9757a-146">RELATED LINKS</span></span>

## <span data-ttu-id="9757a-147">GERELATEERDE KOPPELINGEN</span><span class="sxs-lookup"><span data-stu-id="9757a-147">RELATED LINKS</span></span>
