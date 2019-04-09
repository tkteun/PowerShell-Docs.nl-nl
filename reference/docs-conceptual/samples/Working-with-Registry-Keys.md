---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registersleutels werken
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: e7b497ec2fccf9ba3934439a9c1e9be3cf70a705
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293185"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="2387d-103">Met registersleutels werken</span><span class="sxs-lookup"><span data-stu-id="2387d-103">Working with Registry Keys</span></span>

<span data-ttu-id="2387d-104">Omdat registersleutels artikelen op Windows PowerShell-stations zijn, is werken met hen vergelijkbaar met het werken met bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="2387d-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="2387d-105">Een belangrijke verschil is dat elk item in een register op basis van Windows PowerShell-station een container, net als bij een map op een bestandssysteemstation is.</span><span class="sxs-lookup"><span data-stu-id="2387d-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="2387d-106">Registervermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, geen afzonderlijke items.</span><span class="sxs-lookup"><span data-stu-id="2387d-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="2387d-107">Lijst van alle subsleutels van een registersleutel</span><span class="sxs-lookup"><span data-stu-id="2387d-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="2387d-108">U kunt alle items rechtstreeks in een registersleutel weergeven met behulp van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="2387d-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="2387d-109">Voeg de optionele **Force** parameter verborgen weergeven of items van system.</span><span class="sxs-lookup"><span data-stu-id="2387d-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="2387d-110">Met deze opdracht wordt bijvoorbeeld weergegeven voor items direct in Windows PowerShell-station HKCU:, dat overeenkomt met de registercomponent HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="2387d-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="2387d-111">Dit zijn de op het hoogste niveau sleutels zichtbaar onder HKEY_CURRENT_USER in de Register-Editor (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="2387d-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="2387d-112">U kunt ook deze registerpad opgeven door op te geven de naam van de registerprovider, gevolgd door '**::**'.</span><span class="sxs-lookup"><span data-stu-id="2387d-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="2387d-113">De volledige naam van de registerprovider is **Microsoft.PowerShell.Core\\register**, maar dit kan worden ingekort om just **register**.</span><span class="sxs-lookup"><span data-stu-id="2387d-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="2387d-114">Een van de volgende opdrachten wordt een lijst van de inhoud rechtstreeks onder HKCU:</span><span class="sxs-lookup"><span data-stu-id="2387d-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="2387d-115">Deze opdrachten worden alleen de rechtstreeks opgenomen items, net als met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell.</span><span class="sxs-lookup"><span data-stu-id="2387d-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="2387d-116">Als u de opgenomen items weergeven, moet u opgeven de **Recurse** parameter.</span><span class="sxs-lookup"><span data-stu-id="2387d-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="2387d-117">Als u alle registersleutels in HKCU, gebruik de volgende opdracht uit (deze bewerking kan een extreem lange tijd duren.):</span><span class="sxs-lookup"><span data-stu-id="2387d-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="2387d-118">**Get-ChildItem** kunt uitvoeren van complexe filters gebruiken om mogelijkheden via de **pad**, **Filter**, **opnemen**, en **uitsluiten**parameters, maar deze parameters zijn doorgaans alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="2387d-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="2387d-119">U kunt uitvoeren met het complex filteren op basis van andere eigenschappen van items met behulp van de **Where-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2387d-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="2387d-120">De volgende opdracht worden alle sleutels in HKCU gevonden:\\Software die niet meer dan één subsleutel en beschikt ook over exact vier waarden hebben:</span><span class="sxs-lookup"><span data-stu-id="2387d-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="2387d-121">Kopiëren van sleutels</span><span class="sxs-lookup"><span data-stu-id="2387d-121">Copying Keys</span></span>

<span data-ttu-id="2387d-122">Kopiëren is klaar met **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="2387d-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="2387d-123">De volgende opdracht kopieert HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion en alle bijbehorende eigenschappen aan HKCU:\\, het maken van een nieuwe sleutel met de naam 'CurrentVersion':</span><span class="sxs-lookup"><span data-stu-id="2387d-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="2387d-124">Als u deze nieuwe sleutel in de Register-editor of met behulp van controleert **Get-ChildItem**, zult u merken dat u geen exemplaren van de ingesloten subsleutels in de nieuwe locatie.</span><span class="sxs-lookup"><span data-stu-id="2387d-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="2387d-125">Als u wilt alle van de inhoud van een container hebt gekopieerd, moet u opgeven de **Recurse** parameter.</span><span class="sxs-lookup"><span data-stu-id="2387d-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="2387d-126">Als u de voorgaande opdracht recursieve voor kopiëren, gebruikt u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="2387d-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="2387d-127">U kunt nog steeds andere hulpprogramma's die u al hebt beschikbaar om uit te voeren bestandssysteem kopieën gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2387d-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="2387d-128">Alle Registerbewerkingsprogramma's, met inbegrip van reg.exe regini.exe en regedit.exe—and COM-objecten die ondersteuning bieden voor bewerken van het register (zoals instantie en de WMI-klasse van StdRegProv) kan worden gebruikt vanuit Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2387d-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="2387d-129">Het maken van sleutels</span><span class="sxs-lookup"><span data-stu-id="2387d-129">Creating Keys</span></span>

<span data-ttu-id="2387d-130">Het maken van nieuwe sleutels in het register is eenvoudiger dan het maken van een nieuw item in een bestandssysteem.</span><span class="sxs-lookup"><span data-stu-id="2387d-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="2387d-131">Omdat alle registersleutels containers zijn, hoeft u niet om op te geven van het itemtype. u simpelweg een expliciete pad, zoals:</span><span class="sxs-lookup"><span data-stu-id="2387d-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="2387d-132">U kunt ook een pad op basis van een provider van een sleutel op te geven:</span><span class="sxs-lookup"><span data-stu-id="2387d-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="2387d-133">Verwijderen van sleutels</span><span class="sxs-lookup"><span data-stu-id="2387d-133">Deleting Keys</span></span>

<span data-ttu-id="2387d-134">Items verwijderen is in wezen hetzelfde voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="2387d-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="2387d-135">De volgende opdrachten worden de items op de achtergrond verwijderd:</span><span class="sxs-lookup"><span data-stu-id="2387d-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="2387d-136">Alle sleutels onder een specifieke sleutel verwijderen</span><span class="sxs-lookup"><span data-stu-id="2387d-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="2387d-137">U kunt de opgenomen items verwijderen met behulp van **Remove-Item**, maar u wordt gevraagd om te bevestigen van de verwijzing wordt verwijderd als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="2387d-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="2387d-138">Bijvoorbeeld, als we proberen te verwijderen van de HKCU:\\CurrentVersion subsleutel we hebben gemaakt, zien we dit:</span><span class="sxs-lookup"><span data-stu-id="2387d-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="2387d-139">Ingesloten om items te verwijderen zonder dat u wordt gevraagd, geeft de **-Recurse** parameter:</span><span class="sxs-lookup"><span data-stu-id="2387d-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="2387d-140">Als u wilt verwijderen van alle items in HKCU:\\CurrentVersion, maar niet HKCU:\\CurrentVersion zelf, die u in plaats daarvan kunt gebruiken:</span><span class="sxs-lookup"><span data-stu-id="2387d-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```