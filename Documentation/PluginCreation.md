img "rs dev" goes here

How to Make a Plugin with ReSync
-
ReSync can easily be extended through the use of plugins. These are powerful tools that enhance the experience of your players and Mods. ReSync comes with a variety of built-in plugins, most of which are command modules. Each plugin is a comprised of a single main function that is returned to the system internals at runtime. These functions are all ran after the system has completed the initialization process, and are handled in a separate thread with a protected call, so don't worry about breaking the system if your plugin doesn't work properly.

Environment
-
ReSync's plugins are divided into two distinct categories, those being regular plugins and core plugins. Regular plugins are created by the developer of ReSync and trusted third parties, and any developer may choose to remove, modify, or create new plugins. Core plugins are automatically constructed by the file system, and have a higher load priority than normal plugins. The source code for these plugins is updated internally at build time, but is publicly available to view in this repository at ``BuildAssets/CorePlugins``. While this is not advised, you can change the core plugins by creating a folder inside of your plugin directory named "CPOverrides". This folder can have as many or as few modules as desired, as the actual override is determined by calling the CoreAPI inside of the module. All plugin functions, regardless of whether they are external or core, run on a modified environment, with certain Lua globals being overwritten, such as improvements to the wait function and a table.deepcopy function to copy metatables instead of the shallow table returned by table.copy. A full list of these is detailed below for those who are curious:

| Global | Description |
| ------ | ----------- |
| wait | Mirrors the wait function using an event-based loop. This permits the use of wait - it's convenient - without the drawbacks of Roblox's 30 Hz pipeline.