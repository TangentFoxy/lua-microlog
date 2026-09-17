# microlog
The best Lua logging library ever made!

Public domain. Fuck IP law.

## Usage
```lua
-- set arbitrary log levels to be printed immediately
log{ info = true, warning = true, ducksauce = true, }
-- disable storage of messages depending on log level
log{ error = false, verbose = false, }
-- send anything (except nil) to a log level
log("bacom", true, "text", 5, function() end, {})
-- print all messages saved at a particular log level
log("error")
-- toggle ALL logging on and off with a boolean
log(false) -- this deletes all stored messages
-- set a maximum number of stored messages per log level
log(50) -- warning: reaching large limits makes logging expensive
-- check if a log level is being displayed
if log.arbitrary_exit then log("arbitrary_exit") os.exit(1) end
-- do anything to the stored messages (this example deletes them all)
log(function(messages) return {} end)
```

### What if I need to send logs elsewhere?
There are tools for redirecting console output. Your code shouldn't add such
brittle dependencies. If you really need it to be in Lua, use [LuaLogging](https://lunarmodules.github.io/lualogging/).
It can output directly to a file, rolling file, email, socket, syslog, SQL, and
NGINX or OpenResty.

### What if I want pretty colors?
Use rxi's [log.lua](https://github.com/rxi/log.lua) or add color codes in a
wrapper function, I'm not your mom.

### What if I want my Lua to look like Java?
Why do you want that? Use [moteus/lua-log](https://github.com/moteus/lua-log)
I guess.
