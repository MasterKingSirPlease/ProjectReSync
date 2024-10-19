img rs dev goes here

Player Modifications
-
Inside of each plugin, Players are modified to include custom properties and methods in order to interface with ReSync. Due to Roblox limitations, these cannot be natively indexed outside of the plugin function. It is for this reason that ``SyncAPI.MetaPlayer`` and ``SyncAPI.PlayerIsMeta`` exist, such as in instances where a Player object is passed as an argument through an Event or global table.

Properties