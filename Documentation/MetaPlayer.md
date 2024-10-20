img rs dev goes here

Player Modifications
-
Inside of each plugin, Players are modified to include custom properties and methods in order to interface with ReSync. Due to Roblox limitations, these cannot be natively indexed outside of the plugin function. It is for this reason that ``SyncAPI.MetaPlayer`` and ``SyncAPI.PlayerIsMeta`` exist, such as in instances where a Player object is passed as an argument through an Event or global table.

## Permission Levels
There are four separate levels of permission that come with ReSync:
```
0 | Standard User (default)
1 | Moderator
2 | Administrator
3 | Super Administrator
```
## Permission Flags
Permission flags are detailed in the settings panel, and are properties that determine whether or not the Player has certain abilities. These flags are determinant on the drop
## Root
The root user power is not associated with any specific permission level itself, although all specified root users are automatically given Super permissions. Root users are specified to identify game developers who should have full access to the system settings.

Properties
-
| Property             | Returns                 | Description | Writable |
| -------------------- | ----------------------- | ----------- | -------- |
| IsRoot               | \<boolean isRoot>       | The Player is the game owner and ``settings.CreatorRoot == true`` or ``Player.UserId`` is a member of ``settings.RootUsers``. For security to protect access to critical sensitive settings, this is a static value that cannot be changed once the system is initialized. | No
| IsPermssionLevelAuto | \<boolean auto>         | The Player's saved permission level is equivalent to their permission level in the current server. | No
| Commands             | \<table playerCommands> | Returns a list of commands that the Player is allowed to execute in the format ``{["cmdName"] = {"shorthand1","shorthand2",...}}. Commands that the Player is permitted to use can be manually added or removed from this table for fine-grained command access. | Yes
| IsDonor              | \<boolean isDonor>      | The Player has donated money to Project ReSync. Useful for coding donator perks. This can be modified if you want to make your own donator product instead of supporting the system (but that would be a little bit sad 😔 and I recommend adding separate donor powers instead of overwriting the default ones). | Yes

Methods
-
| Method        | Parameters                                                | Returns | Description |
| ------------- | --------------------------------------------------------- | ------- | ----------- |
| GetPermission | \<optional:boolean auto>                                  | \<number level>                           | Returns an integer between 0 and 3 representing the Player's permission, with 0 being basic user, 1 being Moderator, 2 being Administrator, and 3 as Super Administrator. If ``auto`` is ``true``, the int returned will be the permission level that is saved in the data store. This can be used to get the Player's permanent permission if it has been temporarily set to a different level in the current server.
| SetPermission | \<number level OR string "Auto"> \<optional:boolean save> | nil                                       | Changes the Player's permission to the specified level. If ``save`` is ``true``, their permission will be saved to the data store across all servers both present and future. This parameter defaults to ``false``. If ``level`` is a string that is equal to "Auto" then the Player's permission will be reset to the level saved in the data store.
| Display       | \<string notifType> ...                                   | variable                                  | Equivalent to ``SyncAPI:Display(player,notifType,...)``, but the ``player`` argument is automatically filled in.
| Filter        | \<string message> \<optional:Instance playerTo>           | \<boolean cleaned> \<string cleansedData> | Equivalent to ``SyncAPI:ApplyFilter(player,message,playerTo)``, but the ``player`` argument is automatically filled in.
| AddCommand    | \<string cmdName>                                         | nil                                       | Permits the Player to run a command, even if it is above their permission level. ``cmdName`` may also be the shorthand for a command.
| RemoveCommand | \<string cmdName>                                         | nil                                       | Prohibits the Player from running a command, even if it is below their permission level. ``cmdName`` may also be the shorthand for a command.
