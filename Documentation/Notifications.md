todo either rs dev or syncapi icon

## Sending and Managing Notifications
The <a href="./SyncAPI.md">SyncAPI</a> is capable of sending messages to Players, and receiving different input and responses from those messages. You can send a notification to a Player via ``SyncAPI:Display(notifType,player,...)``. This documentation details each different type of notification that can be sent, and how to interact with them.

> [!IMPORTANT]  
> All notifications must have a ``player`` argument and ``notifType`` argument. If you are calling ``player:Notify(notifType,...)``, the ``player`` argument will be automatically passed.

## Event Handling
lorem ipsum

### Key

**Description:** What the notification does, and how it appears on the user's screen.

**Arguments:** The ... tuple in the function.

**Defaults:** If arguments are not specified, what they will default to.

**Events:** Events that are returned from the notification. See <a href="./Notifications.md#Event%20Handling">Event Handling</a> for more information.

**Examples:** How you might use the API to send a Player this kind of notification.

### Notification

**Description:** A generic notification that appears on the right side of the user's screen as a side bar.

**Arguments:** \<optional:string title> \<optional:string icon> \<optional:number time>

**Defaults:** \<string ""> \<string "Info"> nil

**Events:** Clicked, Expired

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

### Hint

**Description:** A bar that fills the top of the user's screen.

**Arguments:** \<optional:string title> \<optional:string icon> \<optional:number time>

**Defaults:** \<string ""> \<string "Info"> nil

**Events:** Clicked, Expired

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

### Popup

**Description:** A large message that takes up the center of the user's screen. Multiple popups will gradually proceed diagonally down the screen.

**Arguments:** \<optional:string title> \<optional:string content> \<optional:string icon> \<optional:table buttons> \<optional:number time>

**Defaults:** \<string ""> \<string "Info"> nil

**Events:** Clicked, Expired

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
