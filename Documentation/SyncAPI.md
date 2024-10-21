todo sync api here

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
| AuditLog | \<table audit> | A table of all commands that have been executed.

## Methods
| Method      | Parameters                                                         | Returns                                    | Description |
| ----------- | ------------------------------------------------------------------ | ------------------------------------------ | ----------- |
| ApplyFilter | \<Instance player> \<string message> \<optional:Instance playerTo> | \<boolean cleansed> \<string cleansedData> | Sends ``message`` through Roblox's chat filter. If ``playerTo`` is invalid or not specified, the string will be filtered for broadcast.
| Display     | \<Instance player> \<string notifType> ...                         | variable                                   | Refer to <a href="../SyncAPI.md">Notifications</a>.

## Command Creation and Destruction
The SyncAPI can be called directly like a function to make or delete a command. Todo. If you wish to remove a command, call the SyncAPI and pass the first argument as the command name or shorthand, and the second argument as ``false``. An example has been provided below:
```lua
-- I don't want the "urmom" command anymore
SyncAPI('urmom',false) -- Get rid of it!
```
