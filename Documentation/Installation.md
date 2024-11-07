<div align=center><img src="https://github.com/user-attachments/assets/3d14a1db-eedc-4520-874f-29a1987e6203" height="166" width="692"></div><br>

If you don't know how to script or this is your first time using ReSync, this quickstart manual will tell you all that you need to know. Follow the step-by-step instructions listed below for a perfect installation:

1. Insert the model
   
   You have a few options available for this. There are a couple different distributions of the ReSync loader:
   
   The loader from the [Roblox library](https://roblox.com) comes prebuilt with all the plugins you need to manage your game, and is the recommended loader for most users.
   
   For more granulated control, the [releases page](https://github.com/MasterKingSirPlease/ProjectReSync/releases) in this repository has three separate versions available:
   - **Full**: The complete package. The system core is included, along with all verified plugins and features.
   - **RK**: Contains only the root kernel for the system and loads the bare essentials and core plugins by default. Does not include additional plugins.
   - **Internal**: Has some preset flags for internal use. This version is not considered stable and is not recommended for use by anyone who is not working on contributions to the system core itself.
   
2. Ensure that HTTP Service is enabled
   
   Go to the Home tab on Studio and find Game Settings (Should be on the left). Once you've opened the settings, click on "Security" and then "Allow HTTP Requests." You can also do this by running the following in the command bar:
    ```lua
   game:GetService('HttpService').HttpEnabled = true
    ```
    > What does this do?
    > - Enabling HTTP requests permits the Roblox server to communicate with external services. This is necessary for the initial download of ReSync, but you may disable it once ReSync is downloaded if you wish.

    > Is this going to open security risks for my experience?
    > - No. As long as you ensure that you are utilizing safe scripts in
    	   your game (verified free models and scripts you or your developers
    	   have created yourself), you will not be at any risk of bad things
    	   happening due to HTTP service being turned on.
