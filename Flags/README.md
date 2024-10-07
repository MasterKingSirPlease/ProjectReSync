<div align=center><img src="https://github.com/user-attachments/assets/50bb9d9d-7c02-49b0-acc3-a3cdbcb1d40e" height="71" width="345"></div><br>

<hr>

## Project ReSync Feature Flags
Feature Flags are properties about the system that are downloaded from here by the Roblox engine at runtime. This provides a useful way to enable or disable portions of code remotely, quickly push update and emergency notifications to all running servers, and modify other minor parts of the system. Flags are not designed to publish major internal changes, such as performing an actual framework update. Rather, they can do things like let the server know "Hey, an update is available!" From there, the end user can opt to install the latest version. Flag data is stored in a custom binary format, so these files aren't human-readable.

## Flag Types
| Type    | Elaboration | Description |
| ------ | ---------------------------- | --------------------------------------------------------------- |
| SFlag  | Server Flag                  | Loaded on startup and apply to the server only                  |
| CFlag  | Client Flag                  | Loaded on startup and are sent to the client                    |
| RFlag  | Replicated Flag              | Loaded on startup and apply to both the server and client       |
| SSFlag | Synchronized Server Flag     | Updated once per minute and apply to the server only            |
| SCFlag | Synchronized Client Flag     | Updated once per minute and are sent to the client              |
| SRFlag | Synchronized Replicated Flag | Updated once per minute and apply to both the server and client |

### Policy Notice
Your use of these files is governed by <a href="https://policies.polymatic.co/Terms/">ReSync's Terms of Service</a>.
