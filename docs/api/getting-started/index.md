---
hide:
- navigation
---
## Installation

Installing EasySFX is very **easy**:

1.  Grab the module from [here](https://create.roblox.com/store/asset/121810074935113).
2.  Drop it into `ReplicatedStorage`.
3.  Initiate it in your script like so:

```luau title="LocalScript"
local EasySFX = require(game.ReplicatedStorage.EasySFX) -- Import the EasySFX module.
local soundObj = script.Sound --  Reference your Sound object.
local sound = EasySFX:Load(soundObj) -- Load a sound into EasySFX (Returns EasySFX object).
```

## Introduction

Once you've loaded a sound, you can apply effects to it. Here's how:

```luau title="LocalScript"
local EasySFX = require(game.ReplicatedStorage.EasySFX)
local soundObj = script.Sound
local sound = EasySFX:Load(soundObj) -- (Loaded EasySFX object)

-- Apply effects (Returns effect instance):
local sound_Echo = sound:Echo() -- Add echo.

-- Apply effects with properties (applies before parenting):
local sound_Reverb = sound:Reverb({
    DryLevel = 1,
    WetLevel = -2
})

-- Apply properties **after** initializing the effect:
sound_Echo.DryLevel = 0

-- Remove an effect:
sound.RemoveEffect(easySound_Echo) -- Remove the echo effect.

-- Unload the sound and remove all effects:
sound.Unload() -- Unload the sound. Returns true on success, nil otherwise.
```

## Example

```luau title="LocalScript"
local EasySFX = require(game.ReplicatedStorage.EasySFX)
local soundObj = script.Sound
local sound = EasySFX:Load(soundObj)

-- Chaining multiple effects:
local easySound_Reverb = sound:Reverb({ DryLevel = 0, WetLevel = -6 })
local easySound_Distortion = sound:Distortion({ Gain = 0.8 })
local easySound_Chorus = sound:Chorus({ Depth = 0.5, Rate = 10 })

-- Using OnUnload to clean up:
sound.Sound.Ended:Connect(function()
    print("Sound ended, unloading effects")
	sound.OnUnload(function() -- Call OnUnload() BEFORE Unloading for it to work.
	    print("Successfully unloaded")
	end)
    sound.Unload()
end)
```
```luau title="OUTPUT:"
"Successfully unloaded" - LocalScript
```