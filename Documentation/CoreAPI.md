todo core api here

## Overview
The CoreAPI is similar to the SyncAPI in that it is utilized to interface with the system. The main difference is that it is more restrictive and meant mainly for internal use and inside of the core plugins. Unlike the SyncAPI, it is locked and cannot be edited. Additionally, for security reasons, any attempt to use the CoreAPI outside of a plugin will cause an error.

## Properties
| Property | Returns       | Description |
| -------- | ------------- | ----------- |
| Commands | \<table cmds> | A table of all commands constructed by the SyncAPI.
| DevLog   | \<table dLog> | A table of information from the system containing warnings, errors, and general messages.

## Methods
| Method           | Parameters                                             | Returns            | Description |
| ---------------- | ------------------------------------------------------ | ------------------ | ----------- |
| RetrieveRegistry | nil                                                    | \<table reg>       | Fetches settings from the data store.
| SubmitRegistry   | \<table newReg>                                        | \<boolean success> | Merges the changes made to the registry into the settings.
| BlockPush        | \<string category> \<boolean block> \<optional:reason> | nil                | Sends a message to all running servers to disallow changes to the specified ``category``. Used primarily if someone is editing the settings.
| BlockPull        | \<string category> \<boolean block>                    | nil                | Sends a message to all running servers to stop reading from the specified ``category``. Used immediately before updating the system to prevent data store access in order to avoid potential errors.
| PullBlocked      | \<string category>                                     | \<boolean blocked> | Checks if the specified pull is actively being blocked.
| PushBlocked      | \<string category>                                     | \<boolean blocked> | Checks if the specified push is actively being blocked.

todo pullblocked and push blocked with indexed via dot not colon
