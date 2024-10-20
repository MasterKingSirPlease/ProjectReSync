img rs dev goes here

Player Modifications
-
Inside of each plugin, Players are modified to include custom properties and methods in order to interface with ReSync. Due to Roblox limitations, these cannot be natively indexed outside of the plugin function. It is for this reason that ``SyncAPI.MetaPlayer`` and ``SyncAPI.PlayerIsMeta`` exist, such as in instances where a Player object is passed as an argument through an Event or global table.

# Permissions
## Levels
There are four separate levels of permission that come with ReSync:
```
0 | Standard User (default)
1 | Moderator
2 | Administrator
3 | Super Administrator
```
## Flags
Permission flags are detailed in the settings panel, and are properties that determine whether or not the Player has certain abilities. These flags are determinant on the drop
## Root
The root user power is not associated with any specific permission level itself, although all specified root users are automatically given Super permissions. Root users are specified to identify game developers who should have full access to the system settings.

Properties
-
| Property | Returns | Description | Writable |
| -------- | ------- | ----------- | -------- |
| IsRoot | <boolean isRoot> | The Player is the game owner and ``settings.CreatorRoot == true`` or ``Player.UserId`` is a member of ``settings.RootUsers``. For security to protect access to critical sensitive settings, this is a static value that cannot be changed once the system is initialized. | No

Methods
-
| Method | Parameters | Returns | Description |
| GetPermission | | <number level> | Returns an integer between 0 and 3 representing the Player's permission, with 0 being basic user, 1 being Moderator, 2 being Administrator, and 3 as Super Administrator.
| SetPermission | <number level> <boolean save> | Changes the Player's permission 