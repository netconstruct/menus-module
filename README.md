# NetC Menus (Kentico Module)

The Module aims to provide a central location for Editors to create and modify Lists of Hyperlinks that will appear on their website.
As each Hyperlink will be it's own object, it can have it own settings. This means that a single **Menu** can have:
* A link to a page on the website
* A link to an external website that opens in a new tab
* A link to a social media account which has the Brand Icon next to it
* A PDF document that the user can read in a new tab and then save to their computer

The Package was created in Kentico 12.0.33 so projects that use it will need to be in this Hotfix version or higher.

# Installation
Everything needed for the module will be included in the NuGet package that is installed from Kentico DevNet.

# Module Usage
The **Menus** Module will be under the Content Management section of the Module's side menu.
Clicking this will open the main menu of the module, this will show a list of all the **Menus** that have been created. 

From here you can create new **Menus** by clicking on New Menu, or edit an eisting **Menu** by clicking the green pencil.
**Menus** have 2 tabs, the first with the properties that the object is made off, a Display Name and a Code Name; and the second show a grid of the **Menu Items** in this menu.

**Menu Items** are the items that provide the links for the **Menu** item. These are made up of:

| Field | Type | Description  |
| --- | --- | --- |
| Display Name | Localizable Text Box | Text that the link should use |
| Target | Drop Down | How the link should open |
| Icon | Text Box | Optional Icon identifier |
| Caption | Localizable Text Box | Optional Description for the Link |
| Page | Page Selector | Kentico page to link to |
| URL | URL Selector | External URL to link to |
| Activity Type | Text Box (Hidden) | Custom Activity to Log (will require EMS License to use Activity Logging) |
| Activity Type | Text Box (Hidden) | Custom Value to Log (will require EMS License to use Activity Logging) |

The **Menu Items** can be edited, deleted and re-arranged in the list. Any changes that are made will effect all the Objects that use the **Menu**.

# Developer Usage
## In Kentico Objects
**Menus** need to be selected to be used, the simplest way to select a generic object in a Kentico Object (Page, Webpart, Custom Table, etc.) is to use a Uni Selector.
It needs to be configured in the following manner:

| Field | Value |
| --- | --- |
| Object type* | netc.menu |
| Return column name | MenuID |

After that, you can use any configuration you need for the Selector, e.g. Allowing None, changing the Selection mode.
This will provide Editors a selector to choose which **Menu** should be used.

## In the code
To access the **Menus** and **Menu Items**, you will need to get the Providers from the Module after it has been installed.

This is done in the **Modules** Module. You will find the **Menus (Custom)** Module in the Grid (normally on the second page)

When in the **Menus (Custom)**, open the Classes Tab to see the **Menu** and **Menu Item** classes. Opening both of these, click on the **Code** tab on the left side and then click Save Code.
This will save the **Info Class** and **Provider Class** to the **Save Path** location. Adding these into the Solution will allow you to use them within the code.
You can then get a list of **Menu Items** where `MenuItemMenuID = {selectedMenuID}`.
We would recommend creating an Extension to the **Menu Provider** which will take the **MenuID** from the Selector and return a list of **Menu Items**.

## Customising
The Objects in the Module have been set to be Customised, so that if you need to add additional fields to your implementation, you are welcome to do so.
Just remember to save the code again so that you can use the fields in the code files.

# Contributing
If you find something that can be added into the core project, please fork the project from GitHub, add in the files and then create a Pull Request. We will then review it the changes, leave comments if necessary, and complete the merge once approved.
