---
title: Fake Os
description: 
published: true
date: 2021-11-27T23:52:41.007Z
tags: 
editor: markdown
---





# Features 
* Depending on the users user agent, actually have that particular theme be the default (So if user is connecting on a windows machine, have the windows theme display).
# Components             
## Taskbar
### Start Button (with logo)
* onClick will toggle the start menu.
### Start Menu (ul)
* Clicking anywhere not in the menu will close the start menu
* Multiply nested. Hovering on a menu item that is itself a menu will open the submenu. 
* Submenus only close if a different menu item is hovered over. (Or the user clicks outside of the menu entirely, in which case all menus close.  
#### Start Menu Item (li)
* Always renders an icon and a label
* Either "executes" some command or is a submenu

### Taskbar buttons (ul)
#### Taskbar button (li)
* Rendered for each open window
* onclick will bring associated window to front / visible
* Always renders an icon and a label
* Label text can be updated 
* Always a fixed width, ellipsis text overflow

### Notification area

## Desktop
### Icons
Will be sortable by 
* Auto Arrange - Default on windows 95. This is where there is some predefined order for icons, and the user can rearrange them by dragging and dropping.
* Name
* Size - TBD
* Item type
* Date Modified - TBD

### Icon + Label
## Window
 
 
 