<div align=center><img src="https://github.com/user-attachments/assets/3d14a1db-eedc-4520-874f-29a1987e6203" height="166" width="692"></div><br>

If you don't know how to script or this is your first time using ReSync,
    this quickstart manual will tell you all that you need to know. Follow the
    step-by-step instructions listed below for a perfect installation:
    
    I.		Sign up for an account (It's very easy and streamlined)
    		🔗 https://roblox.com/games/0
    	-> Why do I need an account?
    	 > Accounts are useful for tracking data on our end. It's also easier
    	   for allowing users to manage their settings and provides more
    	   ease of access and features than a normal Roblox account provides.
    	   Additionally, you acknowledge and accept our ToS in the account
    	   creation process, so there will be no misunderstandings if you
    	   commit an offense that warrants your account's termination.
    
    II.		Configure your settings to your liking
    		You can do this from the Desktop.
    
    III.	Ensure that HTTP Service is enabled
    		Go to the Home tab on Studio and find Game Settings (Should be
    		on the left). Once you've opened the settings, click on "Security"
    		and then "Allow HTTP Requests." You can also do this by running the
    		following in the command bar:
    		"game:GetService('HttpService').HttpEnabled = true" (without the quotes)
    	-> What does this do?
    	 > Enabling HTTP requests permits the Roblox server to communicate
    	   with external services, such as the Sezei.me API endpoint. This is
    	   necessary because Roblox does not inherently provide a way to send
    	   data across different experiences, only through servers in the same
    	   experience.
    	-> Is this going to open security risks for my experience?
    	 > No. As long as you ensure that you are utilizing safe scripts in
    	   your game (verified free models and scripts you or your developers
    	   have created yourself), you will not be at any risk of bad things
    	   happening due to HTTP service being turned on.
    	   
    IV.		Provide your token
    		Enter your unique token into the space provided in the settings module.
    		Project ReSync -> Configuration -> Settings
    		Input your token into the "SettingsToken" value.
    
    V.		You're done!
    		You can configure your settings at any time by running the
    		"Settings" command in-experience.
    
    !!IMPORTANT!!
    ReSync is disabled in Studio mode. Don't worry that ReSync crashes when you try to
    run it in Studio, as this is completely intentional, and it's mainly as part of an
    effort to prevent users from gathering the internal workings of ReSync. We hope you
    understand our concern for keeping our product secure. Refer to the ToS if you have
    any questions about this.
