---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Het Object ISEMenuItemCollection
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7ce9132021d4d5e755503e0adb355beb388a625a
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/03/2017
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="75196-103">Het Object ISEMenuItemCollection</span><span class="sxs-lookup"><span data-stu-id="75196-103">The ISEMenuItemCollection Object</span></span>
  <span data-ttu-id="75196-104">Een **ISEMenuItemCollection** object is een verzameling **ISEMenuItem** objecten.</span><span class="sxs-lookup"><span data-stu-id="75196-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="75196-105">Er is een exemplaar van de klasse Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection.</span><span class="sxs-lookup"><span data-stu-id="75196-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="75196-106">Een voorbeeld is de **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object dat wordt gebruikt voor het aanpassen van de **invoegtoepassing** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="75196-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="75196-107">Methode</span><span class="sxs-lookup"><span data-stu-id="75196-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="75196-108">Voeg\(DisplayName, System.Management.Automation.ScriptBlock actie System.Windows.Input.KeyGesture snelkoppeling string\)</span><span class="sxs-lookup"><span data-stu-id="75196-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>
  <span data-ttu-id="75196-109">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="75196-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="75196-110">Een menu-item wordt toegevoegd aan de verzameling.</span><span class="sxs-lookup"><span data-stu-id="75196-110">Adds a menu item to the collection.</span></span>

 <span data-ttu-id="75196-111">**DisplayName** de weergavenaam van het menu moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="75196-111">**DisplayName** The display name of the menu to be added.</span></span>

 <span data-ttu-id="75196-112">**Actie** de **System.Management.Automation.ScriptBlock** -object dat Hiermee geeft u de actie die is gekoppeld aan dit menu-item.</span><span class="sxs-lookup"><span data-stu-id="75196-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

 <span data-ttu-id="75196-113">**Snelkoppeling** de sneltoets voor de actie.</span><span class="sxs-lookup"><span data-stu-id="75196-113">**Shortcut** The keyboard shortcut for the action.</span></span>

 <span data-ttu-id="75196-114">**Retourneert** de ISEMenuItem-object dat zojuist is toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="75196-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a><span data-ttu-id="75196-115">Wissen\(\)</span><span class="sxs-lookup"><span data-stu-id="75196-115">Clear\(\)</span></span>
  <span data-ttu-id="75196-116">In Windows PowerShell ISE 2.0 en hoger ondersteund.</span><span class="sxs-lookup"><span data-stu-id="75196-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="75196-117">Verwijdert alle submenu's van de menuopdracht.</span><span class="sxs-lookup"><span data-stu-id="75196-117">Removes all submenus from the menu item.</span></span>

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a><span data-ttu-id="75196-118">Zie ook</span><span class="sxs-lookup"><span data-stu-id="75196-118">See Also</span></span>
- [<span data-ttu-id="75196-119">Het Object ISEMenuItem</span><span class="sxs-lookup"><span data-stu-id="75196-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md) 
- [<span data-ttu-id="75196-120">De Windows PowerShell ISE-objectmodel Scripting</span><span class="sxs-lookup"><span data-stu-id="75196-120">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="75196-121">Naslaginformatie voor Windows PowerShell ISE-objectmodel</span><span class="sxs-lookup"><span data-stu-id="75196-121">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="75196-122">De hiërarchie ISE</span><span class="sxs-lookup"><span data-stu-id="75196-122">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
