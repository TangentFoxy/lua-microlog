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

Logging uses Lua's `tostring` method. This means you can customize how tables
are printed using [Metamethods](https://www.lua.org/pil/13.html).

When calling `log` with a function, if a table is returned, it will replace
stored messages. Any other return type is ignored. This may be expanded for non-
`nil` return types in the future.

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

## Why no releases?
GitHub keeps unpublishing the releases on this repo. Open
[tags](https://github.com/TangentFoxy/lua-microlog/tags) if no releases show up.

## Future Plans / Tasks
- [ ] Make it optionally support colors.
- [ ] Make it optionally function as a drop-in replacement (at least in terms of
  how it is called) for the other logging libraries.
- [ ] Add a way for this to serve as a middleman to another logging library, so
  you can use their advanced features with the more simple API of this library.
