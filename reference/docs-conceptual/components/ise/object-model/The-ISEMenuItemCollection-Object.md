---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEMenuItemCollection-object
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404482"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="9c563-103">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="9c563-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="9c563-104">Een **ISEMenuItemCollection** object is een verzameling van **ISEMenuItem** objecten.</span><span class="sxs-lookup"><span data-stu-id="9c563-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="9c563-105">Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="9c563-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="9c563-106">Een voorbeeld is de **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object dat wordt gebruikt om aan te passen de **invoegtoepassing** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="9c563-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="9c563-107">Methode</span><span class="sxs-lookup"><span data-stu-id="9c563-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="9c563-108">Voeg\(DisplayName, System.Management.Automation.ScriptBlock actie System.Windows.Input.KeyGesture snelkoppeling tekenreeks \)</span><span class="sxs-lookup"><span data-stu-id="9c563-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="9c563-109">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9c563-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9c563-110">Voegt een menu-item toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="9c563-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="9c563-111">**DisplayName** de weergavenaam van het menu om te worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9c563-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="9c563-112">**Actie** de **System.Management.Automation.ScriptBlock** -object dat Hiermee geeft u de actie die is gekoppeld aan dit menu-item.</span><span class="sxs-lookup"><span data-stu-id="9c563-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="9c563-113">**Snelkoppeling** de sneltoets voor de actie.</span><span class="sxs-lookup"><span data-stu-id="9c563-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="9c563-114">**Retourneert** het ISEMenuItem-object dat zojuist is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="9c563-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="9c563-115">Wissen\(\)</span><span class="sxs-lookup"><span data-stu-id="9c563-115">Clear\(\)</span></span>

<span data-ttu-id="9c563-116">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9c563-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9c563-117">Hiermee verwijdert u alle submenu's uit het menu-item.</span><span class="sxs-lookup"><span data-stu-id="9c563-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="9c563-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="9c563-118">See Also</span></span>

- [<span data-ttu-id="9c563-119">Het ISEMenuItem-Object</span><span class="sxs-lookup"><span data-stu-id="9c563-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="9c563-120">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="9c563-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9c563-121">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="9c563-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)