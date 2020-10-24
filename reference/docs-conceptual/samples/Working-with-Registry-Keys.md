---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Met registersleutels werken
description: In dit artikel wordt beschreven hoe u met behulp van Power shell register sleutels kunt verwerken.
ms.openlocfilehash: 90e8417fc3454b959dc2a86fc63e722832bdab23
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501385"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="9d90c-104">Met registersleutels werken</span><span class="sxs-lookup"><span data-stu-id="9d90c-104">Working with Registry Keys</span></span>

<span data-ttu-id="9d90c-105">Omdat register sleutels items op Power Shell-stations zijn, is het samen werken met bestanden en mappen vergelijkbaar.</span><span class="sxs-lookup"><span data-stu-id="9d90c-105">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="9d90c-106">Een belang rijk verschil is dat elk item op een op het REGI ster gebaseerd Power Shell-station een container is, net als een map op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="9d90c-106">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="9d90c-107">Register vermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, niet de afzonderlijke items.</span><span class="sxs-lookup"><span data-stu-id="9d90c-107">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="9d90c-108">Alle subsleutels van een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="9d90c-108">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="9d90c-109">U kunt alle items rechtstreeks in een register sleutel weer geven met behulp van `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="9d90c-109">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="9d90c-110">Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="9d90c-110">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="9d90c-111">Met deze opdracht worden bijvoorbeeld de items rechtstreeks in het Power Shell-station weer gegeven `HKCU:` , die overeenkomen met de `HKEY_CURRENT_USER` register component:</span><span class="sxs-lookup"><span data-stu-id="9d90c-111">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

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

<span data-ttu-id="9d90c-112">Dit zijn de sleutels op het hoogste niveau die zichtbaar zijn onder `HKEY_CURRENT_USER` in de REGI ster-editor (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="9d90c-112">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="9d90c-113">U kunt dit registerpad ook opgeven door de naam van de register provider op te geven, gevolgd door `::` .</span><span class="sxs-lookup"><span data-stu-id="9d90c-113">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="9d90c-114">De volledige naam van de register provider is `Microsoft.PowerShell.Core\Registry` , maar dit kan worden inge kort tot alleen `Registry` .</span><span class="sxs-lookup"><span data-stu-id="9d90c-114">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="9d90c-115">Met een van de volgende opdrachten wordt de inhoud direct onder weer geven `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="9d90c-115">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="9d90c-116">Met deze opdrachten worden alleen de direct opgenomen items weer geven, vergelijkbaar met het gebruik `DIR` van in **Cmd.exe** of `ls` in een Unix-shell.</span><span class="sxs-lookup"><span data-stu-id="9d90c-116">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="9d90c-117">Als u opgenomen items wilt weer geven, moet u de para meter **recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="9d90c-117">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="9d90c-118">Als u alle register sleutels in wilt weer geven `HKCU:` , gebruikt u de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="9d90c-118">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="9d90c-119">`Get-ChildItem` kan complexe filter functies uitvoeren met de para meters **Path**, **filter**, **include**en **exclude** , maar die para meters zijn doorgaans alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="9d90c-119">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="9d90c-120">U kunt complexe filtering uitvoeren op basis van andere eigenschappen van items met behulp van de- `Where-Object` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9d90c-120">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="9d90c-121">Met de volgende opdracht worden alle sleutels in `HKCU:\Software` die niet meer dan één subsleutel en ook precies vier waarden bevatten:</span><span class="sxs-lookup"><span data-stu-id="9d90c-121">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="9d90c-122">Sleutels kopiëren</span><span class="sxs-lookup"><span data-stu-id="9d90c-122">Copying Keys</span></span>

<span data-ttu-id="9d90c-123">Kopiëren is voltooid met `Copy-Item` .</span><span class="sxs-lookup"><span data-stu-id="9d90c-123">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="9d90c-124">In het volgende voor beeld `CurrentVersion` worden de subsleutel van `HKLM:\SOFTWARE\Microsoft\Windows\` en alle bijbehorende eigenschappen naar gekopieerd `HKCU:\` .</span><span class="sxs-lookup"><span data-stu-id="9d90c-124">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="9d90c-125">Als u deze nieuwe sleutel in de REGI ster-editor bestudeert of gebruikt `Get-ChildItem` , ziet u dat er geen kopieën van de subsleutels in de nieuwe locatie aanwezig zijn.</span><span class="sxs-lookup"><span data-stu-id="9d90c-125">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="9d90c-126">Als u de gehele inhoud van een container wilt kopiëren, moet u de para meter **recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="9d90c-126">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="9d90c-127">Als u de voor gaande Kopieer opdracht recursief wilt maken, gebruikt u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="9d90c-127">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="9d90c-128">U kunt nog steeds gebruikmaken van andere hulpprogram ma's die u al beschikbaar hebt voor het uitvoeren van bestandssysteem kopieën.</span><span class="sxs-lookup"><span data-stu-id="9d90c-128">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="9d90c-129">Register bewerkings Programma's, waaronder **reg.exe**, **regini.exe**, **regedit.exe**en COM-objecten die ondersteuning bieden voor register bewerkingen, zoals **WScript. shell** en de **StdRegProv** -klasse van WMI, kunnen worden gebruikt vanuit Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="9d90c-129">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="9d90c-130">Sleutels maken</span><span class="sxs-lookup"><span data-stu-id="9d90c-130">Creating Keys</span></span>

<span data-ttu-id="9d90c-131">Het maken van nieuwe sleutels in het REGI ster is eenvoudiger dan het maken van een nieuw item in een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="9d90c-131">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="9d90c-132">Omdat alle register sleutels containers zijn, hoeft u het item type niet op te geven. u hoeft alleen maar een expliciet pad op te geven, zoals:</span><span class="sxs-lookup"><span data-stu-id="9d90c-132">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="9d90c-133">U kunt ook een op een provider gebaseerd pad gebruiken om een sleutel op te geven:</span><span class="sxs-lookup"><span data-stu-id="9d90c-133">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="9d90c-134">Sleutels verwijderen</span><span class="sxs-lookup"><span data-stu-id="9d90c-134">Deleting Keys</span></span>

<span data-ttu-id="9d90c-135">Het verwijderen van items is in wezen hetzelfde voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="9d90c-135">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="9d90c-136">Met de volgende opdrachten worden items op de achtergrond verwijderd:</span><span class="sxs-lookup"><span data-stu-id="9d90c-136">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="9d90c-137">Verwijderen van alle sleutels onder een bepaalde sleutel</span><span class="sxs-lookup"><span data-stu-id="9d90c-137">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="9d90c-138">U kunt opgenomen items verwijderen met `Remove-Item` , maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="9d90c-138">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="9d90c-139">Als we bijvoorbeeld proberen de subsleutel te verwijderen `HKCU:\CurrentVersion` die we hebben gemaakt, zien we het volgende:</span><span class="sxs-lookup"><span data-stu-id="9d90c-139">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

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

<span data-ttu-id="9d90c-140">Als u opgenomen items zonder vragen wilt verwijderen, geeft u de para meter **recursief** op:</span><span class="sxs-lookup"><span data-stu-id="9d90c-140">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="9d90c-141">Als u alle items binnen `HKCU:\CurrentVersion` maar niet zelf wilt verwijderen `HKCU:\CurrentVersion` , kunt u in plaats daarvan het volgende gebruiken:</span><span class="sxs-lookup"><span data-stu-id="9d90c-141">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
