<div align=center><img src="https://github.com/user-attachments/assets/a41fc94c-e0b8-4ec4-96ff-71bb634fac93" height="166" width="589"></div><br>

## Overview
The Synchronized Application Programming Interface is the most powerful aspect of ReSync. Its role is to communicate with the system to access and modify different parts of ReSync. It comes preloaded with a bunch of features that you can use as a developer, but it's also possible to make your own modifications to it. With this being said, it's not recommended that you change the built-in data, or you could risk causing issues to the stability of the system, as the SyncAPI is also used internally within the firmware itself. The SyncAPI is accessible from all plugins as a global variable. Due to Roblox limitations, if you wish to utilize it outside of the plugin function, you'll have to create a plugin to do that. An example script for this has been written below and can be copied into your game:
```lua
-- Plugin script
return function()
  _G.SAPI = SyncAPI
end
```
```lua
-- Outside script
repeat
  wait()
until _G.SAPI ~= nil
_G.SAPI:TestPrint('It works')
```

## Properties
| Property | Returns | Description |
| -------- | ------- | ----------- |
| AuditLog | \<table audit> | A table of all commands that have been executed. Note that this list is *not* filtered, and you will need to call ``SyncAPI.ApplyFilter`` to comply with Roblox's ToS.

## Methods
| Method             | Parameters                                                                                                                                          | Returns                                    | Description
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | -----------
| ApplyFilter        | \<Instance player> \<string message> \<optional:Instance playerTo>                                                                                  | \<boolean cleansed> \<string cleansedData> | Sends ``message`` through Roblox's chat filter. If ``playerTo`` is invalid or not specified, the string will be filtered for broadcast.
| Display            | \<Instance player> \<string notifType> ...                                                                                                          | variable                                   | Refer to <a href="./Notifications.md">Notifications</a>.
| GetPermissionLevel | \<Instance player OR table user OR string username OR int userId> \<optional:boolean auto>                                                          | \<number level>                            | Returns an integer between 0 and 3 representing the Player's permission, with 0 being basic user, 1 being Moderator, 2 being Administrator, and 3 as Super Administrator. If ``auto`` is ``true``, the int returned will be the permission level that is saved in the data store. This can be used to get the Player's permanent permission if it has been temporarily set to a different level in the current server.
| SetPermissionLevel | \<Instance player OR table user OR string username OR int userId> \<optional:boolean auto> \<number level OR string "Auto"> \<optional:boolean save> | nil                                       | Changes the Player's permission to the specified level. If ``save`` is ``true``, their permission will be saved to the data store across all servers both present and future. This parameter defaults to ``false``. If ``level`` is a string that is equal to "Auto" then the Player's permission will be reset to the level saved in the data store.

## Command Creation and Destruction
The SyncAPI can be called directly like a function to make or delete a command. Todo. If you wish to remove a command, call the SyncAPI and pass the first argument as the command name or shorthand, and the second argument as ``false``. An example has been provided below:
```lua
-- I don't want the "urmom" command anymore
SyncAPI('urmom',false) -- Get rid of it!
```

## Code Examples
### AuditLog

```lua
  -- MasterScootScoot executes commands ":slock" and ":kick foo bar"
  for index,log in pairs(SyncAPI.AuditLog) do
    print(index,log[1],log[2])
  end

  --[[
  OUTPUT
  ------
  1, 'MasterScootScoot', 'slock'
  2, 'MasterScootScoot', 'kick foo bar'
  ]]
```

### ApplyFilter
TODO

### GetPermissionLevel
