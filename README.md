# inf lightning f

A client script for the Blox Fruits **Lightning** fruit, named for its F move. You need the Lightning fruit; without it the script does nothing.

The source is obfuscated on purpose, so `inf_lightning_f.lua` is not meant to be read.

## What your executor needs

| Function | Why |
| --- | --- |
| `getgenv` | the script uses it to tell if it is already running, so running it twice replaces the first copy instead of stacking |
| `getfenv`, `setfenv` | used by the obfuscation wrapper. Roblox provides them, so this only matters if your executor removes them |

Nothing else. The script does not use hooks, `getconnections` or any other special executor function. It has to run on the client, after your character has loaded.

If you use the one-line loader below, you also need `game:HttpGet` and `loadstring`.

### Quick check

Paste this into your executor first. Anything that prints `MISSING` is a problem.

```lua
for _, f in ipairs({ { "getgenv", getgenv }, { "getfenv", getfenv }, { "setfenv", setfenv } }) do
    print(f[1], f[2] and "ok" or "MISSING")
end
```

## Use

Paste the contents of `inf_lightning_f.lua` into your executor and run it in-game, or:

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/zurxxot/inf-lightning-f/main/inf_lightning_f.lua"))()
```

Running it again replaces the previous run. To turn it off, rejoin the game.

## Notes

Written on Volt; not tested on other executors. Use at your own risk. Scripts like this can be detected and are against Roblox's terms.

Obfuscated with Prometheus. Based on Prometheus by Elias Oelschner, https://github.com/prometheus-lua/Prometheus
