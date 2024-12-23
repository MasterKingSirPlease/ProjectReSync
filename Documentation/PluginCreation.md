<div align=center><img src="https://github.com/user-attachments/assets/15709da5-f509-4c96-963d-8cce51372a5e" height="166" width="589"></div><br>

How to Make a Plugin with ReSync
-
ReSync can easily be extended through the use of plugins. These are powerful tools that enhance the experience of your players and Mods. ReSync comes with a variety of built-in plugins, most of which are command modules. Each plugin is a comprised of a single main function that is returned to the system internals at runtime. These functions are all ran after the system has completed the initialization process, and are handled in a separate thread with a protected call, so don't worry about breaking the system if your plugin doesn't work properly.

Environment
-
ReSync's plugins are divided into two distinct categories, those being regular plugins and core plugins. Regular plugins are created by the developer of ReSync and trusted third parties, and any developer may choose to remove, modify, or create new plugins. Core plugins are automatically constructed by the file system, and have a higher load priority than normal plugins. The source code for these plugins is updated internally at build time, but is publicly available to view in this repository at ``BuildAssets/CorePlugins``. While this is not advised, you can change the core plugins by creating a folder inside of your plugin directory named "CPOverrides". This folder can have as many or as few modules as desired, as the actual override is determined by calling the CoreAPI inside of the module. All plugin functions, regardless of whether they are external or core, run on a modified environment, with certain Lua globals being overwritten, such as improvements to the wait function and a table.deepcopy method. A full list of modified global variables is detailed below for those who are curious:

| Global | Description |
| ------ | ----------- |
| ``wait`` | Mirrors the wait function using an event-based loop. This permits the use of wait - it's convenient - without the drawbacks of Roblox's 30 Hz pipeline.
| ``table`` | Added ``deepcopy`` method which copies metatables and sub-tables instead of the shallow table returned by ``table.copy``.
| ``getfenv``, ``setfenv`` | Security modification to prevent access to the internal environment from plugins. Additional measures are taken to ensure copies of the original function declared outside of the plugin function, passed through a Bindable, or the _G/shared tables cannot bypass this and gain a higher security context. Additionally, these functions cannot be used on any member of the APIs.
| ``game``, ``script``, ``workspace`` | Players service is modified to automatically overwrite Player instances to permit custom properties and methods on each Player.
