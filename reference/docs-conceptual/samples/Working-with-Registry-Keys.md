---
ms.date: 12/23/2019
keywords: Power shell, cmdlet
title: Met registersleutels werken
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736842"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="cce42-103">Met registersleutels werken</span><span class="sxs-lookup"><span data-stu-id="cce42-103">Working with Registry Keys</span></span>

<span data-ttu-id="cce42-104">Omdat register sleutels items op Power Shell-stations zijn, is het samen werken met bestanden en mappen vergelijkbaar.</span><span class="sxs-lookup"><span data-stu-id="cce42-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="cce42-105">Een belang rijk verschil is dat elk item op een op het REGI ster gebaseerd Power Shell-station een container is, net als een map op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="cce42-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="cce42-106">Register vermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, niet de afzonderlijke items.</span><span class="sxs-lookup"><span data-stu-id="cce42-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="cce42-107">Alle subsleutels van een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="cce42-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="cce42-108">U kunt alle items rechtstreeks in een register sleutel weer geven met behulp van `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="cce42-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="cce42-109">Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="cce42-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="cce42-110">Met deze opdracht worden bijvoorbeeld de items rechtstreeks weer gegeven in het Power Shell-station `HKCU:`, dat overeenkomt met de `HKEY_CURRENT_USER` register component:</span><span class="sxs-lookup"><span data-stu-id="cce42-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="cce42-111">Dit zijn de sleutels op het hoogste niveau die zichtbaar zijn onder `HKEY_CURRENT_USER` in de REGI ster-editor (Regedit. exe).</span><span class="sxs-lookup"><span data-stu-id="cce42-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="cce42-112">U kunt dit registerpad ook opgeven door de naam van de register provider op te geven, gevolgd door `::`.</span><span class="sxs-lookup"><span data-stu-id="cce42-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="cce42-113">De volledige naam van de register provider is `Microsoft.PowerShell.Core\Registry`, maar dit kan worden inge kort tot alleen `Registry`.</span><span class="sxs-lookup"><span data-stu-id="cce42-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="cce42-114">Met een van de volgende opdrachten wordt de inhoud direct onder `HKCU:`weer geven.</span><span class="sxs-lookup"><span data-stu-id="cce42-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="cce42-115">Met deze opdrachten worden alleen de rechtstreeks opgenomen items weer geven, vergelijkbaar met het gebruik van `DIR` in **cmd. exe** of `ls` in een Unix-shell.</span><span class="sxs-lookup"><span data-stu-id="cce42-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="cce42-116">Als u opgenomen items wilt weer geven, moet u de para meter **recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="cce42-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="cce42-117">Als u alle register sleutels in `HKCU:`wilt weer geven, gebruikt u de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="cce42-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="cce42-118">`Get-ChildItem` kunt complexe filter mogelijkheden uitvoeren met de para meters **Path**, **filter**, **include**en **exclude** , maar die para meters zijn doorgaans alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="cce42-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="cce42-119">U kunt complexe filtering op basis van andere eigenschappen van items uitvoeren met behulp van de cmdlet `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="cce42-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="cce42-120">Met de volgende opdracht worden alle sleutels in `HKCU:\Software` gevonden die niet meer dan één subsleutel hebben en ook precies vier waarden hebben:</span><span class="sxs-lookup"><span data-stu-id="cce42-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="cce42-121">Sleutels kopiëren</span><span class="sxs-lookup"><span data-stu-id="cce42-121">Copying Keys</span></span>

<span data-ttu-id="cce42-122">Kopiëren wordt uitgevoerd met `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="cce42-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="cce42-123">In het volgende voor beeld wordt de `CurrentVersion` subsleutel van `HKLM:\SOFTWARE\Microsoft\Windows\` en alle bijbehorende eigenschappen naar `HKCU:\`gekopieerd.</span><span class="sxs-lookup"><span data-stu-id="cce42-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="cce42-124">Als u deze nieuwe sleutel in de REGI ster-Editor bekijkt of `Get-ChildItem`gebruikt, ziet u dat er geen kopieën van de subsleutels in de nieuwe locatie aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="cce42-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="cce42-125">Als u de gehele inhoud van een container wilt kopiëren, moet u de para meter **recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="cce42-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="cce42-126">Als u de voor gaande Kopieer opdracht recursief wilt maken, gebruikt u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="cce42-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="cce42-127">U kunt nog steeds gebruikmaken van andere hulpprogram ma's die u al beschikbaar hebt voor het uitvoeren van bestandssysteem kopieën.</span><span class="sxs-lookup"><span data-stu-id="cce42-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="cce42-128">Register bewerkings Programma's, zoals **reg. exe**, **Regini. exe**, **regedit. exe**en COM-objecten die ondersteuning bieden voor het bewerken van het REGI ster, zoals **WScript. shell** en WMI-klasse **StdRegProv** , kunnen worden gebruikt vanuit Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="cce42-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="cce42-129">Sleutels maken</span><span class="sxs-lookup"><span data-stu-id="cce42-129">Creating Keys</span></span>

<span data-ttu-id="cce42-130">Het maken van nieuwe sleutels in het REGI ster is eenvoudiger dan het maken van een nieuw item in een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="cce42-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="cce42-131">Omdat alle register sleutels containers zijn, hoeft u het item type niet op te geven. u hoeft alleen maar een expliciet pad op te geven, zoals:</span><span class="sxs-lookup"><span data-stu-id="cce42-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="cce42-132">U kunt ook een op een provider gebaseerd pad gebruiken om een sleutel op te geven:</span><span class="sxs-lookup"><span data-stu-id="cce42-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="cce42-133">Sleutels verwijderen</span><span class="sxs-lookup"><span data-stu-id="cce42-133">Deleting Keys</span></span>

<span data-ttu-id="cce42-134">Het verwijderen van items is in wezen hetzelfde voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="cce42-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="cce42-135">Met de volgende opdrachten worden items op de achtergrond verwijderd:</span><span class="sxs-lookup"><span data-stu-id="cce42-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="cce42-136">Verwijderen van alle sleutels onder een bepaalde sleutel</span><span class="sxs-lookup"><span data-stu-id="cce42-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="cce42-137">U kunt opgenomen items verwijderen door gebruik te maken van `Remove-Item`, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="cce42-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="cce42-138">Als we bijvoorbeeld proberen de `HKCU:\CurrentVersion` subsleutel te verwijderen, zien we dit:</span><span class="sxs-lookup"><span data-stu-id="cce42-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="cce42-139">Als u opgenomen items zonder vragen wilt verwijderen, geeft u de para meter **recursief** op:</span><span class="sxs-lookup"><span data-stu-id="cce42-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="cce42-140">Als u alle items in `HKCU:\CurrentVersion` wilt verwijderen, maar niet `HKCU:\CurrentVersion` zelf, kunt u in plaats daarvan het volgende gebruiken:</span><span class="sxs-lookup"><span data-stu-id="cce42-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
