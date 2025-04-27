---
hide:
- navigation
---
## EasySFX Module Documentation

This document provides a comprehensive overview of the EasySFX module's functions and usage.

---

### `api:Load(audio: Sound)`

Loads a sound into the EasySFX module, enabling sound effect management.

* `audio: Sound`: The Roblox `Sound` object to load.

    * Returns: An EasySFX object containing the module's functions for the specified sound. Returns `nil` if the provided `audio` is not a `Sound` object.

    * Example:

        ```luau
        local EasySFX = require(game.ReplicatedStorage.EasySFX)
        local sound = workspace.MySound
        local gunshotFX = EasySFX:Load(sound)
        ```

---

### `soundProps:Destroy()`

Unloads the sound from the module and destroys the sound object.

* Returns: `true` on success, `nil` otherwise.

    * Example:

        ```luau
		local gunshotFX = EasySFX:Load(sound)
        gunshotFX:Destroy()
        ```

---

### `soundProps:Unload()`

Unloads the sound from the module and removes all applied sound effects.

* Returns: `true` on success, `nil` otherwise.

    * Example:

        ```luau
		local gunshotFX = EasySFX:Load(sound)
        gunshotFX:Unload()
        ```

---

### `soundProps:OnUnload(Function: (any?))`

Registers a function to be executed when the sound is unloaded from the module.

* `Function: (any?)`: The function to execute on unload.

    * Returns: Nothing.

    * Example:

        ```luau
		local gunshotFX = EasySFX:Load(sound)
        gunshotFX:OnUnload(function()
            print("Sound unloaded!")
        end)
        ```
!!! note "OnUnload() must be called **before** Unload()"
	If you call OnUnload() **after** Unload() your function wont fire.

---

### `soundProps:RemoveEffect(effect: Instance?)`

Removes a sound effect from the loaded sound.

* `effect: Instance?`: The sound effect instance to remove.

    * Returns: `true` if the effect was successfully removed, `nil` otherwise.

    * Example:

        ```luau
        local reverbEffect = gunshotFX:Reverb()
        gunshotFX:RemoveEffect(reverbEffect)
        ```

---

### `soundProps:GetEffects(): {[string]: Instance}`

Retrieves the sound effect instances currently applied to the loaded sound.

* Returns: A table where the keys are the names of the sound effects, and the values are the corresponding sound effect instances. Returns an empty table if there are no effects.

    * Example:

        ```luau
        local effects = gunshotFX:GetEffects()
        for name, effect in pairs(effects) do
            print(name, effect)
        end
        ```

---

### `soundProps:GetEffectNames(): {[number]: string}`

Retrieves the names of the sound effects currently applied to the loaded sound.

* Returns: A table containing the names (strings) of the sound effects. Returns an empty table if there are no effects.

    * Example:

        ```luau
        local effectNames = gunshotFX:GetEffectNames()
        for i, name in ipairs(effectNames) do
            print(i, name)
        end
        ```

---

### `soundProps:Reverb(properties: reverbProperties)`

Applies a reverb effect to the loaded sound or returns an existing reverb effect.

* `properties: reverbProperties`: An optional table containing reverb properties.

    * Returns: The `ReverbSoundEffect` instance.

    * Example:

        ```luau
        local reverb = gunshotFX:Reverb({
            DryLevel = 0,
            WetLevel = -10
        })
        ```

---

### `soundProps:Echo(properties: echoProperties)`

Applies an echo effect to the loaded sound or returns an existing echo effect.

* `properties: echoProperties`: An optional table containing echo properties.

    * Returns: The `EchoSoundEffect` instance.

    * Example:

        ```luau
        local echo = gunshotFX:Echo({
            Delay = 0.2,
            Decay = 0.5
        })
        ```

---

###  `soundProps:Equalizer(properties: equalizerProperties)`

Applies an equalizer effect to the loaded sound or returns an existing equalizer effect.

* `properties: equalizerProperties`: An optional table containing equalizer properties.

    * Returns: The `EqualizerSoundEffect` Instance.

    * Example:

        ```luau
        local equalizer = gunshotFX:Equalizer({
            LowGain = 0.8,
            HighGain = -0.5
        })
        ```

---

### `soundProps:Compressor(properties: compressorProperties)`

Applies a compressor effect to the loaded sound, or returns an existing one.

* `properties: compressorProperties`: Optional table of compressor properties.

    * Returns: The `CompressorSoundEffect` instance.

    * Example:

        ```luau
        local compressor = gunshotFX:Compressor({
            Threshold = -20,
            Ratio = 4
        })
        ```

---

### `soundProps:Chorus(properties: chorusProperties)`

Applies a chorus effect to the loaded sound or returns an existing chorus effect.

* `properties: chorusProperties`: An optional table containing chorus properties.

    * Returns: The `ChorusSoundEffect` instance.

    * Example:

        ```luau
        local chorus = gunshotFX:Chorus({
            Depth = 0.7,
            Rate = 5
        })
        ```

---

### `soundProps:Tremolo(properties: tremoloProperties)`

Applies a tremolo effect to the loaded sound or returns an existing tremolo effect.

* `properties: tremoloProperties`: An optional table containing tremolo properties.

    * Returns: The `TremoloSoundEffect` instance.

    * Example:

        ```luau
        local tremolo = gunshotFX:Tremolo({
           Frequency = 10,
           Depth = 0.6
        })
        ```

---

### `soundProps:Distortion(properties: distortionProperties)`

Applies a distortion effect to the loaded sound or returns an existing distortion effect.

* `properties: distortionProperties`: An optional table containing distortion properties.

    * Returns: The `DistortionSoundEffect` instance.

    * Example:

        ```luau
        local distortion = gunshotFX:Distortion({
            Gain = 0.9
        })
        ```

---

### `soundProps:PitchShift(properties: pitchshiftProperties)`

Applies a pitch shift effect to the loaded sound.

* `properties: pitchshiftProperties`: A table containing pitch shift properties.

    * Returns: The `PitchShiftSoundEffect` instance.

    * Example:

        ```luau
        local pitchShift = gunshotFX:PitchShift({
            Octave = 1,
            Pitch = 0.5
        })
        ```

---

### `soundProps:Flange(properties: flangeProperties)`

Applies a flange effect to the loaded sound or returns an existing flange effect.

* `properties: flangeProperties`: An optional table containing flange properties.

    * Returns: The `FlangeSoundEffect` instance.

    * Example:

        ```luau
        local flange = gunshotFX:Flange({
            Depth = 0.4,
            Rate = 8
        })
        ```
