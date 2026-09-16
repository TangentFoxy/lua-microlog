# microlog
A small very flexible logging library for Lua.

Public domain. Fuck IP law.

## Usage
```lua
-- set arbitrary log levels to be printed immediately
log{ info = true, warning = true, ducksauce = true, }
-- send anything (except nil) to a log level
log("bacom", true, "text", 5, function() end, {})
-- print all messages saved at a particular log level
log("error")
-- toggle ALL logging on and off with a boolean
log(false) -- this deletes all stored messages
-- set a maximum number of stored messages per log level
log(50) -- warning: reaching large limits makes logging expensive
-- do anything to the stored messages (this example deletes them all)
log(function(messages) return {} end)
```
