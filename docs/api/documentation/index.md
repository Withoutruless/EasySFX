---
hide:
- navigation
---
---
## EasySFX Documentation

Easy to understand explanation of the module's functions and usage.

---

### `EasySFX:Logging(value: Boolean)`

Enables logging for debugging purposes (Disabled by default).

* `value: Boolean`: The value to set logging to.

    * Returns: Nothing.

    * Example:

        ```luau
        local EasySFX = require(game.ReplicatedStorage.EasySFX)
		EasySFX.Logging(true)
        ```

---

### `EasySFX:Load(audio: Sound)`

Loads a sound into the EasySFX module, enabling sound effect management.

* `audio: Sound`: The Roblox `Sound` object to load.

    * Returns: An EasySFX object containing the module's functions for the specified sound. Returns `nil` if the provided `audio` is not a `Sound` object.

    * Example:

        ```luau
        local EasySFX = require(game.ReplicatedStorage.EasySFX)
        local soundObj = workspace.MySound
        local sound = EasySFX:Load(soundObj)
        ```

---

### `sound.Sound`

* Reference back to SoundObj (Mostly for cleaner code, no real purpose.)

    * Example:

        ```luau
		local sound = EasySFX:Load(soundObj)
        sound.Sound -- Access to SoundObj
        ```

---

### `sound:Destroy()`

Unloads the sound from the module and destroys the sound object.

* Returns: `true` on success, `nil` otherwise.

    * Example:

        ```luau
		local sound = EasySFX:Load(soundObj)
        sound:Destroy()
        ```

---

### `sound:Unload()`

Unloads the sound from the module and removes all applied sound effects.

* Returns: `true` on success, `nil` otherwise.

    * Example:

        ```luau
		local sound = EasySFX:Load(soundObj)
        sound:Unload()
        ```

---

### `sound:OnUnload(Function: (any?))`

Registers a function to be executed when the sound is unloaded from the module.

* `Function: (any?)`: The function to execute on unload.

    * Returns: Nothing.

    * Example:

        ```luau
		local sound = EasySFX:Load(soundObj)
        sound:OnUnload(function()
            print("Sound unloaded!")
        end)
        ```
!!! note "OnUnload() must be called **before** Unload()"
	If you call OnUnload() **after** Unload() your function wont fire.

---

### `sound:RemoveEffect(effect: Instance?)`

Removes a sound effect from the loaded sound.

* `effect: Instance?`: The sound effect instance to remove.

    * Returns: `true` if the effect was successfully removed, `nil` otherwise.

    * Example:

        ```luau
        local reverbEffect = sound:Reverb()
        sound:RemoveEffect(reverbEffect)
        ```

---

### `sound:GetEffects(): {[string]: Instance}`

Retrieves the sound effect instances currently applied to the loaded sound.

* Returns: A table where the keys are the names of the sound effects, and the values are the corresponding sound effect instances. Returns an empty table if there are no effects.

    * Example:

        ```luau
        local effects = sound:GetEffects()
        for name, effect in pairs(effects) do
            print(name, effect)
        end
        ```

---

### `sound:GetEffectNames(): {[number]: string}`

Retrieves the names of the sound effects currently applied to the loaded sound.

* Returns: A table containing the names (strings) of the sound effects. Returns an empty table if there are no effects.

    * Example:

        ```luau
        local effectNames = sound:GetEffectNames()
        for i, name in ipairs(effectNames) do
            print(i, name)
        end
        ```

---

### `sound:Reverb(properties: reverbProperties)`

Applies a reverb effect to the loaded sound or returns an existing reverb effect.

* `properties: reverbProperties`: An optional table containing reverb properties.

    * Returns: The `ReverbSoundEffect` instance.

    * Example:

        ```luau
        local reverb = sound:Reverb({
            DryLevel = 0,
            WetLevel = -10
        })
        ```

---

### `sound:Echo(properties: echoProperties)`

Applies an echo effect to the loaded sound or returns an existing echo effect.

* `properties: echoProperties`: An optional table containing echo properties.

    * Returns: The `EchoSoundEffect` instance.

    * Example:

        ```luau
        local echo = sound:Echo({
            Delay = 0.2,
            Decay = 0.5
        })
        ```

---

###  `sound:Equalizer(properties: equalizerProperties)`

Applies an equalizer effect to the loaded sound or returns an existing equalizer effect.

* `properties: equalizerProperties`: An optional table containing equalizer properties.

    * Returns: The `EqualizerSoundEffect` Instance.

    * Example:

        ```luau
        local equalizer = sound:Equalizer({
            LowGain = 0.8,
            HighGain = -0.5
        })
        ```

---

### `sound:Compressor(properties: compressorProperties)`

Applies a compressor effect to the loaded sound, or returns an existing one.

* `properties: compressorProperties`: Optional table of compressor properties.

    * Returns: The `CompressorSoundEffect` instance.

    * Example:

        ```luau
        local compressor = sound:Compressor({
            Threshold = -20,
            Ratio = 4
        })
        ```

---

### `sound:Chorus(properties: chorusProperties)`

Applies a chorus effect to the loaded sound or returns an existing chorus effect.

* `properties: chorusProperties`: An optional table containing chorus properties.

    * Returns: The `ChorusSoundEffect` instance.

    * Example:

        ```luau
        local chorus = sound:Chorus({
            Depth = 0.7,
            Rate = 5
        })
        ```

---

### `sound:Tremolo(properties: tremoloProperties)`

Applies a tremolo effect to the loaded sound or returns an existing tremolo effect.

* `properties: tremoloProperties`: An optional table containing tremolo properties.

    * Returns: The `TremoloSoundEffect` instance.

    * Example:

        ```luau
        local tremolo = sound:Tremolo({
           Frequency = 10,
           Depth = 0.6
        })
        ```

---

### `sound:Distortion(properties: distortionProperties)`

Applies a distortion effect to the loaded sound or returns an existing distortion effect.

* `properties: distortionProperties`: An optional table containing distortion properties.

    * Returns: The `DistortionSoundEffect` instance.

    * Example:

        ```luau
        local distortion = sound:Distortion({
            Gain = 0.9
        })
        ```

---

### `sound:PitchShift(properties: pitchshiftProperties)`

Applies a pitch shift effect to the loaded sound.

* `properties: pitchshiftProperties`: A table containing pitch shift properties.

    * Returns: The `PitchShiftSoundEffect` instance.

    * Example:

        ```luau
        local pitchShift = sound:PitchShift({
            Octave = 1,
            Pitch = 0.5
        })
        ```

---

### `sound:Flange(properties: flangeProperties)`

Applies a flange effect to the loaded sound or returns an existing flange effect.

* `properties: flangeProperties`: An optional table containing flange properties.

    * Returns: The `FlangeSoundEffect` instance.

    * Example:

        ```luau
        local flange = sound:Flange({
            Depth = 0.4,
            Rate = 8
        })
        ```
