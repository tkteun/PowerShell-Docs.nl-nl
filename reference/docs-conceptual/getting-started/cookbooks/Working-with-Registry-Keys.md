---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Met registersleutels werken
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951695"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="5fa4c-103">Met registersleutels werken</span><span class="sxs-lookup"><span data-stu-id="5fa4c-103">Working with Registry Keys</span></span>

<span data-ttu-id="5fa4c-104">Omdat registersleutels items op Windows PowerShell-stations, lijkt werken met deze erg op werken met bestanden en mappen.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="5fa4c-105">Een kritieke verschil is dat elk item op een Windows PowerShell register gebaseerde station een container, net als een map op een bestandssysteemstation.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="5fa4c-106">Registervermeldingen en hun gekoppelde waarden zijn echter eigenschappen van de items, geen verschillende items.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="5fa4c-107">Lijst van alle subsleutels van een registersleutel</span><span class="sxs-lookup"><span data-stu-id="5fa4c-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="5fa4c-108">U kunt alle items rechtstreeks in een registersleutel weergeven met behulp van **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="5fa4c-109">Voeg de optionele **Force** parameter worden verborgen items van system.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="5fa4c-110">Met deze opdracht geeft bijvoorbeeld de items rechtstreeks in Windows PowerShell-station HKCU:, dat overeenkomt met het registeronderdeel HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

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

<span data-ttu-id="5fa4c-111">Dit zijn de op het hoogste niveau sleutels zichtbaar onder HKEY_CURRENT_USER in de Register-Editor (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="5fa4c-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="5fa4c-112">U kunt ook dit registerpad opgeven door te geven van de naam van de registerprovider, gevolgd door '**::**'.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="5fa4c-113">Volledige naam van de registerprovider **Microsoft.PowerShell.Core\\register**, maar dit kan worden ingekort tot iets **register**.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="5fa4c-114">Een van de volgende opdrachten wordt de inhoud rechtstreeks onder HKCU weergeven:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="5fa4c-115">Deze opdrachten alleen de lijst rechtstreeks opgenomen, vergelijkbaar met behulp van Cmd.exe **DIR** opdracht of **ls** in een UNIX-shell.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="5fa4c-116">Als de opgenomen items weergeven, moet u opgeven de **Recurse** parameter.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="5fa4c-117">Als alle registersleutels in HKCU weergeven, gebruikt u de volgende opdracht (deze bewerking kan een zeer lange tijd duren.):</span><span class="sxs-lookup"><span data-stu-id="5fa4c-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="5fa4c-118">**Get-ChildItem** kunt uitvoeren complexe filtermogelijkheden via de **pad**, **Filter**, **opnemen**, en **uitsluiten**parameters, maar deze parameters doorgaans alleen worden gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="5fa4c-119">U kunt uitvoeren complexe filteren op basis van andere eigenschappen van items door de **Where-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="5fa4c-120">De volgende opdracht worden alle sleutels binnen HKCU gevonden:\\Software die niet meer dan één subsleutels en hebben exact vier waarden hebben:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="5fa4c-121">Kopiëren van sleutels</span><span class="sxs-lookup"><span data-stu-id="5fa4c-121">Copying Keys</span></span>

<span data-ttu-id="5fa4c-122">Kopiëren is klaar met **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="5fa4c-123">De volgende opdracht kopieert HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion en alle bijbehorende eigenschappen naar HKCU:\\, voor het maken van een nieuwe sleutel met de naam 'CurrentVersion':</span><span class="sxs-lookup"><span data-stu-id="5fa4c-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="5fa4c-124">Als u deze nieuwe sleutel in de Register-editor of door onderzoeken **Get-ChildItem**, zult u zien dat er geen kopieën van de subsleutels opgenomen in de nieuwe locatie.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="5fa4c-125">Om te kopiëren alle van de inhoud van een container, moet u opgeven de **Recurse** parameter.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="5fa4c-126">Als u de voorgaande opdracht recursieve voor kopiëren, gebruikt u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="5fa4c-127">U kunt nog andere hulpprogramma's die u hebt al beschikbaar voor het bestandssysteem te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="5fa4c-128">Een register bewerkingsopties, met inbegrip van reg.exe regini.exe en regedit.exe—and COM-objecten die ondersteuning bieden voor bewerken (zoals instantie en de WMI-klasse StdRegProv) van het register kan worden gebruikt vanuit Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="5fa4c-129">Maken van sleutels</span><span class="sxs-lookup"><span data-stu-id="5fa4c-129">Creating Keys</span></span>

<span data-ttu-id="5fa4c-130">Nieuwe sleutels maken in het register is eenvoudiger dan het maken van een nieuw item in een bestandssysteem.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="5fa4c-131">Omdat alle registersleutels containers zijn, hoeft u niet het itemtype; opgeven u simpelweg een expliciet pad, zoals:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="5fa4c-132">U kunt ook een pad op basis van een provider gebruiken een sleutel op te geven:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="5fa4c-133">Verwijderen van sleutels</span><span class="sxs-lookup"><span data-stu-id="5fa4c-133">Deleting Keys</span></span>

<span data-ttu-id="5fa4c-134">Verwijderen van items is in wezen hetzelfde voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="5fa4c-135">De volgende opdrachten worden items achtergrond verwijderd:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="5fa4c-136">Alle sleutels onder een specifieke sleutel verwijderen</span><span class="sxs-lookup"><span data-stu-id="5fa4c-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="5fa4c-137">U kunt opgenomen items verwijderen met behulp van **Item verwijderen**, maar u wordt gevraagd om te bevestigen dat de verwijzing wordt verwijderd als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="5fa4c-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="5fa4c-138">Bijvoorbeeld, als we probeert te verwijderen van de HKCU:\\CurrentVersion subsleutel wordt gemaakt, zien we dit:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="5fa4c-139">De opgenomen als items wilt verwijderen zonder dat wordt gevraagd, geeft de **-Recurse** parameter:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="5fa4c-140">Als u wilt verwijderen van alle artikelen in HKCU:\\CurrentVersion maar niet HKCU:\\CurrentVersion zelf, kunt u in plaats daarvan gebruiken:</span><span class="sxs-lookup"><span data-stu-id="5fa4c-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```