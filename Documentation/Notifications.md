todo either rs dev or syncapi icon

## Sending and Managing Notifications
The <a href="./SyncAPI.md">SyncAPI</a> is capable of sending messages to Players, and receiving different input and responses from those messages. You can send a notification to a Player via ``SyncAPI:Display(notifType,player,...)``. This documentation details each different type of notification that can be sent, and how to interact with them.

> [!IMPORTANT]  
> All notifications must have a ``player`` argument and ``notifType`` argument. If you are calling ``player:Notify(notifType,...)``, the ``player`` argument will be automatically passed.

## Event Handling
lorem ipsum

## Method Handling
dolor sit amet,

### Key

**Description:** What the notification does, and how it appears on the user's screen.

**Arguments:** The ... tuple in the function.

**Defaults:** If arguments are not specified, what they will default to.

**Events:** Events that are returned from the notification. See <a href="./Notifications.md#Event%20Handling">Event Handling</a> for more information.

**Methods:** Functions that can be called on the notification. See <a href="./Notifications.md#Method%20Handling">Method Handling</a> for more information.

**Properties:** Parts of the notification that can be modified or read from.

**Examples:** How you might use the API to send a Player this kind of notification.

<hr>

### Notification

**Description:** A generic notification that appears on the right side of the user's screen as a side bar.

**Arguments:** \<optional:string title> \<optional:string icon> \<optional:number time>

**Defaults:** \<string ""> \<string "Info"> nil

**Events:** Clicked, Expired

**Methods:** Destroy, Exit

**Examples**

```luau
-- A notification with an empty title and info icon
SyncAPI:Display('Notification',player)

-- An empty notification with no title or icon
SyncAPI:Display('Notification',player,nil,'')

-- Basic success notification
SyncAPI:Display('Notification',player,'Success','Check')

-- Interactive notification
-- Display the message "Hello world!" to the Player with an exclamation mark icon for ten seconds
local notif = SyncAPI:Display('Notification',player,'Hello world!','Exclamation',10)
notif.Clicked:Connect(function()
  print('The notification has been clicked')
end)
notif.Expired:Connect(function()
  print('The user did not click the notification within 10 seconds')
end)
```

<hr>

### Hint

**Description:** A bar that fills the top of the user's screen.

**Arguments:** \<optional:string title> \<optional:string icon> \<optional:number time>

**Defaults:** \<string ""> \<string "Info"> nil

**Events:** Clicked, Expired

**Methods:** Destroy, Exit

**Examples**

```luau
-- A hint with an empty title and info icon
SyncAPI:Display('Hint',player)

-- An empty hint with no title or icon
SyncAPI:Display('Hint',player,nil,'')

-- Sticky message that will not go away until the user clicks it
SyncAPI:Display('Hint',player,'Purchase the donation product for ReSync if you want to join the cool squad 😎')

-- Interactive hint
-- Display the message "Hello world!" to the Player with an exclamation mark icon for fifteen seconds
local hint = SyncAPI:Display('Hint',player,'Hello world!','Exclamation',15)
hint.Clicked:Connect(function()
  print('The hint has been clicked')
end)
hint.Expired:Connect(function()
  print('The user did not click the hint within 15 seconds')
end)
```

<hr>

### Popup

**Description:** A large message that takes up the center of the user's screen. Multiple popups will gradually proceed diagonally down the screen. The buttons will be dynamically scaled based on the number of buttons that are  Default button colors can be overridden by assigning a key-value pair when declaring them. See the interactive example for help with this.

**Arguments:** \<optional:string title> \<optional:string content> \<optional:string icon> \<optional:table buttons> \<optional:number time>

**Defaults:** \<string ""> \<string ""> \<string "Exclamation"> \<table {"CLOSE"}> nil

**Events:** Clicked, Expired

**Methods:** Destroy

**Properties:** Title, Content, Buttons, KeepAlive

**Examples**

```luau
-- A popup with an empty title and info icon with a blue close button
SyncAPI:Display('Popup',player)

-- An empty popup with no title or icon that will get stuck for all eternity on the user's screen (this is not recommended)
SyncAPI:Display('Popup',player,nil,nil,'',{})

-- Timed popup
SyncAPI:Display('Popup',player,'HELLO WORLD!','This message will go away in ten seconds.','Check',{},10)

-- Practical template
SyncAPI:Display('Popup',player,'POPUP TITLE','Message description goes here')

-- Interactive popup
-- Ask the user a multiple choice question
local msg = SyncAPI:Display('Popup',player,'SELECT AN OPTION','Please pick the correct choice within the time limit of 3.1415926 seconds:\n\nIs ReSync the best Roblox administration system?',nil,{
  'Yes', -- Automatically will be colored green
  'No', -- Automatically will be colored red
  ['Maybe'] = Color3.fromRGB(164,0,255), -- Override the default yellow color for maybe and make it purple instead
},3.1415926)
msg.Clicked:Connect(function(option)
  if option == 'Yes' then
    print('Good job, the user picked the right answer')
  elseif option == 'Maybe' then
    print('This user needs to try some more of the features')
  else
    player:Kick('you are ugly and fat')
  end
end)
msg.Expired:Connect(function()
  print('The user needs to go back to grade school and learn how to read faster')
end)

-- A popup that has multiple pages of options
-- Buttons can be declared directly inside of the Display call, but separating it in the example makes it easier to visualize and manage, particularly if they are dynamic
local pages = {
  -- Implicit page 1
  {
    'A',
    'B',
    'C',
    '>',
  },
  -- Implicit page 2
  {
    '<',
    'D',
    'E',
    'F',
    '>',
  },
  -- Implicit page 3
  {
    '<',
    'G',
    'H',
    'I',
  },
}
local currentPage = 1

local pgSelector = SyncAPI:Display('Popup',player,'PAGE '..tostring(currentPage),'Which page do you want to go to?','Info',pages[currentPage])
pgSelector.KeepAlive = true -- Don't make it go away when the user clicks an option

local function changePage()
    pgSelector.Title = 'PAGE '..tostring(currentPage)
    pgSelector.Buttons = pages[currentPage]
end

pgSelector.Clicked:Connect(function(option)
  if option == '>' then
    print('The user has opted to go to the next page')
    currentPage = currentPage + 1
    changePage()
  elseif option == '<' then
    print('The user has opted to go to the previous page')
    currentPage = currentPage - 1
    changePage()
  else
    pgSelector:Destroy()
    print('The user selected',option)
  end
end)
```
