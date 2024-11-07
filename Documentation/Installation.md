<div align=center><img src="https://github.com/user-attachments/assets/3d14a1db-eedc-4520-874f-29a1987e6203" height="166" width="692"></div><br>

If you don't know how to script or this is your first time using ReSync, this quickstart manual will tell you all that you need to know. The guide is designed so that even if you have never scripted before, as long as you know the layout of Roblox Studio, you should be able to understand easily. Follow the step-by-step instructions listed below for a perfect installation:

1. Insert the model
   
   You have a few options available for this. There are a couple different distributions of the ReSync loader:
   
   The loader from the [Roblox library](https://roblox.com) comes prebuilt with all the plugins you need to manage your game, and is the recommended loader for most users.
   
   For more granulated control, the [releases page](https://github.com/MasterKingSirPlease/ProjectReSync/releases) in this repository has three separate versions available:
   - **Full**: The complete package. The system core is included, along with all verified plugins and features.
   - **RK**: Contains only the root kernel for the system and loads the bare essentials and core plugins by default. Does not include additional plugins.
   - **Internal**: Has some preset flags for internal use. This version is not considered stable and is not recommended for use by anyone who is not working on contributions to the system core itself.
   
2. Ensure that HTTP Service is enabled
   
   Go to the Home tab on Studio and find Game Settings (Should be on the left).

   ![image](https://github.com/user-attachments/assets/4160b532-22e8-4297-a067-2f9465c37e6b)


   Once you've opened the settings, click on "Security" and then "Allow HTTP Requests."

   ![image](https://github.com/user-attachments/assets/e80082e4-6fbd-477a-b197-6be890ce49fd)
   
   You can also do this by running the following in the command bar:
    ```lua
   game:GetService('HttpService').HttpEnabled = true
    ```
    > What does this do?
    > - Enabling HTTP requests permits the Roblox server to communicate with external services. This is necessary for the initial download of ReSync, but you may disable it once ReSync is downloaded if you wish.

    > Is this going to open security risks for my experience?
    > - No. As long as you ensure that you are utilizing safe scripts in your game (verified free models and scripts you or your developers have created yourself), you will not be at any risk of vulnerabilities due to HTTP service being turned on.

3. Move ReSync into Server Script Service

   ![image](https://github.com/user-attachments/assets/f60fcf42-c352-4796-a5c5-f2532f616d59)
   ![image](https://github.com/user-attachments/assets/ffc5eb57-28d1-4526-9e3b-31f40b5bcf99)
   ![image](https://github.com/user-attachments/assets/83687432-8561-4e47-98c4-9f47b58855a1)

4. Configure base settings

   Locate the ``Settings`` module under the ReSync directory and double click it to open it.

   ![image](https://github.com/user-attachments/assets/36e77539-ecf6-4eb1-a844-30554ff86395)

   At the top of the module, you'll see a block with some notes contained inside directing you to this guide. This is known as a comment, and is used to leave instructions and program notes for developers. Below the comment, you'll notice the word ``return`` followed by a curly bracket (``{``). Ignore this and move to the next section. These lines contain the permission settings, which are probably the only things you will have to edit. A full description of all settings can be located in the table below.

   | Setting | Description |
   | ------- | ----------- |
   | CreatorRoot | Determines whether or not the creator of the game receives root admin by default. If the game owner is a holder account, you may want to disable this. Otherwise, it's best to leave it as is.
   | RootUsers | A table containing the user IDs of permanent Super Administrators that cannot be removed from game settings. They also have a special permission flag to indicate that they have full system control. This permission should be granted carefully, and only to game developers. If the value inside of the table is a nested table, it will be treated as a group, with the first value being the group ID being the first value, and the minimum rank to obtain root power as the second value.
   | PluginsLocation | If you move the ``Plugins`` folder, change this value to the new location.
   | DataCategory | All system files are stored under this category. Changing the category will not wipe existing data, but it will not be migrated to a new store either. In order to migrate data, prepare it for migration in the settings panel, and THEN change the data category.

   ### Settings Example
   
   ---
   
   ```lua
   return {
	   -- Permission settings
	   CreatorRoot = false, -- The game owner will not automatically receive root permissions
	   RootUsers = {
   	711971214, -- MasterScootScoot
   	1, -- Roblox
   	{924821,200}, -- My admin fans, Development Lead
   	{1200769,1}, -- All members of the Official Group of Roblox
	   },
	
	   -- Developer settings
	   PluginsLocation = game:GetService('ServerStorage').Parent:WaitForChild('RSPlugins'), -- A folder in ServerStorage called "RSPlugins"
	   DataCategory = 'RS_TEST', -- Fun fact, this was used as the data category for internal testing in ReSync's alpha version
   }
   ```

   5. Edit the primary settings from the panel

      Publish your game and play it from the app or website. ReSync won't run in Studio mode. Don't worry, as this is intentional. Once you're in-game, if you have chat enabled, you can say ":settings". Otherwise, press the quote key (') on your keyboard while not inside of a text box, and in the command line that appears, run "settings".
