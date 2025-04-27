---
hide:
- navigation
---
## Installation

Installing EasySFX is very **easy**:

1.  Grab the module from [here](https://roblox.com).
2.  Drop it into `ReplicatedStorage`.
3.  Initiate it in your script like so:

```luau title="LocalScript"
local EasySFX = require(game.ReplicatedStorage.EasySFX) -- Import the EasySFX module.
local sound = script.Sound --  Reference your Sound object.
local gunshotFX = EasySFX:Load(sound) -- Load a sound into EasySFX (Returns EasySFX object).
```

## Introduction

Once you've loaded a sound, you can apply effects to it. Here's how:

```luau title="LocalScript"
local EasySFX = require(game.ReplicatedStorage.EasySFX)
local sound = script.Sound
local gunshotFX = EasySFX:Load(sound) -- (Loaded EasySFX object)

-- Apply effects:
local easySound_Echo = gunshotFX:Echo() -- Add echo.

-- Apply effects with properties:
local easySound_Reverb = gunshotFX:Reverb({
    DryLevel = 1,
    WetLevel = -2
})

-- Apply properties **after** initializing the effect:
easySound_Echo.DryLevel = 0

-- Remove an effect:
gunshotFX:RemoveEffect(easySound_Echo) -- Remove the echo effect.

-- Unload the sound and remove all effects:
gunshotFX:Unload() -- Unload the sound. Returns true on success, nil otherwise.
```

## Example

```luau title="LocalScript"
local EasySFX = require(game.ReplicatedStorage.EasySFX)
local sound = script.Sound
local gunshotFX = EasySFX:Load(sound)

-- Chaining multiple effects:
local easySound_Reverb = gunshotFX:Reverb({ DryLevel = 0, WetLevel = -6 })
local easySound_Distortion = gunshotFX:Distortion({ Gain = 0.8 })
local easySound_Chorus = gunshotFX:Chorus({ Depth = 0.5, Rate = 10 })

-- Using OnUnload to clean up:
gunshotFX.Sound.Ended:Connect(function()
    print("Sound ended, unloading effects")
	gunshotFX:OnUnload(function() -- Call OnUnload() BEFORE Unloading for it to work.
	    print("Successfully unloaded")
	end)
    gunshotFX:Unload()
end)

```
```luau title="OUTPUT:"
"Successfully unloaded" - LocalScript
```