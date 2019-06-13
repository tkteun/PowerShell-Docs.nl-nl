---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Het ISEMenuItemCollection-object
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030537"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="508e7-103">Het ISEMenuItemCollection-object</span><span class="sxs-lookup"><span data-stu-id="508e7-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="508e7-104">Een **ISEMenuItemCollection** object is een verzameling van **ISEMenuItem** objecten.</span><span class="sxs-lookup"><span data-stu-id="508e7-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="508e7-105">Het is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="508e7-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="508e7-106">Een voorbeeld is de **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object dat wordt gebruikt om aan te passen de **invoegtoepassing** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="508e7-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="508e7-107">Methode</span><span class="sxs-lookup"><span data-stu-id="508e7-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="508e7-108">Voeg\(DisplayName, System.Management.Automation.ScriptBlock actie System.Windows.Input.KeyGesture snelkoppeling tekenreeks \)</span><span class="sxs-lookup"><span data-stu-id="508e7-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="508e7-109">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="508e7-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="508e7-110">Voegt een menu-item toe aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="508e7-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="508e7-111">**DisplayName** de weergavenaam van het menu om te worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="508e7-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="508e7-112">**Actie** de **System.Management.Automation.ScriptBlock** -object dat Hiermee geeft u de actie die is gekoppeld aan dit menu-item.</span><span class="sxs-lookup"><span data-stu-id="508e7-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="508e7-113">**Snelkoppeling** de sneltoets voor de actie.</span><span class="sxs-lookup"><span data-stu-id="508e7-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="508e7-114">**Retourneert** het ISEMenuItem-object dat zojuist is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="508e7-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="508e7-115">Wissen\(\)</span><span class="sxs-lookup"><span data-stu-id="508e7-115">Clear\(\)</span></span>

<span data-ttu-id="508e7-116">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="508e7-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="508e7-117">Hiermee verwijdert u alle submenu's uit het menu-item.</span><span class="sxs-lookup"><span data-stu-id="508e7-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="508e7-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="508e7-118">See Also</span></span>

- [<span data-ttu-id="508e7-119">Het ISEMenuItem-Object</span><span class="sxs-lookup"><span data-stu-id="508e7-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="508e7-120">Doel van de Scriptobjectmodel van Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="508e7-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="508e7-121">De objectmodelhiërarchie van ISE</span><span class="sxs-lookup"><span data-stu-id="508e7-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
