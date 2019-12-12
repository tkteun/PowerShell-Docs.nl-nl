---
ms.date: 06/05/2017
keywords: Power shell, cmdlet
title: Met registersleutels werken
ms.openlocfilehash: 18daeaea2ee8917a709fef421d2b316f46bf7f4c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030653"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="38d69-103">Met registersleutels werken</span><span class="sxs-lookup"><span data-stu-id="38d69-103">Working with Registry Keys</span></span>

<span data-ttu-id="38d69-104">Omdat register sleutels items zijn op Windows Power Shell-stations, is het samen werken met bestanden en mappen vergelijkbaar.</span><span class="sxs-lookup"><span data-stu-id="38d69-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="38d69-105">Een belang rijk verschil is dat elk item op een op het REGI ster gebaseerd Windows Power Shell-station een container is, net als een map op een bestandssysteem station.</span><span class="sxs-lookup"><span data-stu-id="38d69-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="38d69-106">Register vermeldingen en de bijbehorende waarden zijn echter eigenschappen van de items, niet de afzonderlijke items.</span><span class="sxs-lookup"><span data-stu-id="38d69-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="38d69-107">Alle subsleutels van een register sleutel weer geven</span><span class="sxs-lookup"><span data-stu-id="38d69-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="38d69-108">U kunt alle items rechtstreeks in een register sleutel weer geven met behulp van **Get-Child item**.</span><span class="sxs-lookup"><span data-stu-id="38d69-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="38d69-109">Voeg de optionele **Force** -para meter toe om verborgen of systeem items weer te geven.</span><span class="sxs-lookup"><span data-stu-id="38d69-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="38d69-110">Met deze opdracht worden bijvoorbeeld de items rechtstreeks in Windows Power Shell-station HKCU:, dat overeenkomt met de HKEY_CURRENT_USER register component:</span><span class="sxs-lookup"><span data-stu-id="38d69-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

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

<span data-ttu-id="38d69-111">Dit zijn de sleutels op het hoogste niveau die zichtbaar zijn onder HKEY_CURRENT_USER in de REGI ster-editor (Regedit. exe).</span><span class="sxs-lookup"><span data-stu-id="38d69-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="38d69-112">U kunt dit registerpad ook opgeven door de naam van de register provider op te geven, gevolgd door ' **::** '.</span><span class="sxs-lookup"><span data-stu-id="38d69-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="38d69-113">De volledige naam van de register provider is **micro soft. Power shell. Core\\Registry**, maar dit kan worden inge kort tot alleen het **REGI ster**.</span><span class="sxs-lookup"><span data-stu-id="38d69-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="38d69-114">Met een van de volgende opdrachten wordt de inhoud direct onder HKCU weer geven:</span><span class="sxs-lookup"><span data-stu-id="38d69-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="38d69-115">Met deze opdrachten worden alleen de direct opgenomen items weer geven, vergelijkbaar met het gebruik van de **dir** opdracht van cmd. exe of **ls** in een Unix-shell.</span><span class="sxs-lookup"><span data-stu-id="38d69-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="38d69-116">Als u opgenomen items wilt weer geven, moet u de para meter **recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="38d69-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="38d69-117">Als u alle register sleutels in HKCU wilt weer geven, gebruikt u de volgende opdracht (deze bewerking kan erg lang duren):</span><span class="sxs-lookup"><span data-stu-id="38d69-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="38d69-118">**Get-Child item** kan complexe filter mogelijkheden uitvoeren met de para meters **Path**, **filter**, **include**en **exclude** , maar die para meters zijn doorgaans alleen gebaseerd op naam.</span><span class="sxs-lookup"><span data-stu-id="38d69-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="38d69-119">U kunt complexe filtering op basis van andere eigenschappen van items uitvoeren met de cmdlet **where-object** .</span><span class="sxs-lookup"><span data-stu-id="38d69-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="38d69-120">Met de volgende opdracht worden alle sleutels in HKCU gevonden:\\software die niet meer dan één subsleutel heeft en die ook precies vier waarden heeft:</span><span class="sxs-lookup"><span data-stu-id="38d69-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="38d69-121">Sleutels kopiëren</span><span class="sxs-lookup"><span data-stu-id="38d69-121">Copying Keys</span></span>

<span data-ttu-id="38d69-122">Kopiëren is voltooid met **copy-item**.</span><span class="sxs-lookup"><span data-stu-id="38d69-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="38d69-123">De volgende opdracht kopieert HKLM:\\SOFTWARE\\micro soft\\Windows\\CurrentVersion en alle bijbehorende eigenschappen naar HKCU:\\, waarbij een nieuwe sleutel met de naam ' CurrentVersion ' wordt gemaakt:</span><span class="sxs-lookup"><span data-stu-id="38d69-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="38d69-124">Als u deze nieuwe sleutel bekijkt in de REGI ster-editor of met behulp van **Get-Child item**, zult u merken dat u geen kopieën van de subsleutels in de nieuwe locatie hebt.</span><span class="sxs-lookup"><span data-stu-id="38d69-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="38d69-125">Als u de gehele inhoud van een container wilt kopiëren, moet u de para meter **recursief** opgeven.</span><span class="sxs-lookup"><span data-stu-id="38d69-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="38d69-126">Als u de voor gaande Kopieer opdracht recursief wilt maken, gebruikt u deze opdracht:</span><span class="sxs-lookup"><span data-stu-id="38d69-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="38d69-127">U kunt nog steeds gebruikmaken van andere hulpprogram ma's die u al beschikbaar hebt voor het uitvoeren van bestandssysteem kopieën.</span><span class="sxs-lookup"><span data-stu-id="38d69-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="38d69-128">Alle register bewerkings Programma's, waaronder reg. exe, regini. exe en Regedit. exe, en COM-objecten die ondersteuning bieden voor het bewerken van registers (zoals WScript. shell en WMI-klasse StdRegProv) kunnen worden gebruikt vanuit Windows Power shell.</span><span class="sxs-lookup"><span data-stu-id="38d69-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="38d69-129">Sleutels maken</span><span class="sxs-lookup"><span data-stu-id="38d69-129">Creating Keys</span></span>

<span data-ttu-id="38d69-130">Het maken van nieuwe sleutels in het REGI ster is eenvoudiger dan het maken van een nieuw item in een bestands systeem.</span><span class="sxs-lookup"><span data-stu-id="38d69-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="38d69-131">Omdat alle register sleutels containers zijn, hoeft u het item type niet op te geven. u hoeft alleen maar een expliciet pad op te geven, zoals:</span><span class="sxs-lookup"><span data-stu-id="38d69-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="38d69-132">U kunt ook een op een provider gebaseerd pad gebruiken om een sleutel op te geven:</span><span class="sxs-lookup"><span data-stu-id="38d69-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="38d69-133">Sleutels verwijderen</span><span class="sxs-lookup"><span data-stu-id="38d69-133">Deleting Keys</span></span>

<span data-ttu-id="38d69-134">Het verwijderen van items is in wezen hetzelfde voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="38d69-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="38d69-135">Met de volgende opdrachten worden items op de achtergrond verwijderd:</span><span class="sxs-lookup"><span data-stu-id="38d69-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="38d69-136">Verwijderen van alle sleutels onder een bepaalde sleutel</span><span class="sxs-lookup"><span data-stu-id="38d69-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="38d69-137">U kunt opgenomen items verwijderen met behulp van **Remove-item**, maar u wordt gevraagd het verwijderen te bevestigen als het item iets anders bevat.</span><span class="sxs-lookup"><span data-stu-id="38d69-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="38d69-138">Als we bijvoorbeeld proberen de HKCU:\\CurrentVersion-subsleutel te verwijderen, zien we het volgende:</span><span class="sxs-lookup"><span data-stu-id="38d69-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="38d69-139">Als u opgenomen items zonder vragen wilt verwijderen, geeft u de para meter **-recursief** op:</span><span class="sxs-lookup"><span data-stu-id="38d69-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="38d69-140">Als u alle items in HKCU wilt verwijderen:\\CurrentVersion, maar niet HKCU:\\CurrentVersion zelf, kunt u in plaats daarvan het volgende gebruiken:</span><span class="sxs-lookup"><span data-stu-id="38d69-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
