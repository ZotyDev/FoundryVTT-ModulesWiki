# Hooks
OIF rely heavily on hooks to provide you with more options, almost all hooks contain a `data` value, the changes made to it will be propagated forward to wathever happens next.

### After Melee Preparation
```js
Hooks.on('oifWeaponMeleePostPrepare', (data) => {});
```
This hook fires **after** the data that will be used on the melee animation gets prepared, and **before** the animation gets played.

</br>

### After Melee Hit Animation
```js
Hooks.on('oifWeaponMeleeHitPostAnimation', (data) => {});
```
This hook fires **after** the melee hit animation is played, and **before** interaction and sound.

### After Melee Hit Interaction
```js
Hooks.on('oifWeaponMeleeHitPostInteraction', (data) => {});
```
This hook fires **after** the melee hit interaction.

### After Melee Hit Sound _(currently not implemented)_
```js
Hooks.on('oifWeaponMeleeHitPostSound', (data) => {});
```
This hook fires **after** the melee hit sound.

</br>

### After Melee Throw Animation
```js
Hooks.on('oifWeaponMeleeThrowPostAnimation', (data) => {});
```
This hook fires **after** the melee throw animation is played, and **before** the interaction and sound.

### After Melee Throw Interaction
```js
Hooks.on('oifWeaponMeleeThrowPostInteraction', (data) => {});
```
This hook fires **after** the melee throw interaction.

### After Melee Throw Sound _(currently not implemented)_
```js
Hooks.on('oifWeaponMeleeThrowPostSound', (data) => {});
```
This hook fires **after** the melee throw sound.

</br>

### After Ranged Preparation
```js
Hooks.on('oifWeaponRangedPostPrepare', (data) => {});
```
This hook firest **after** the data that will be used on the ranged animation gets prepared, and **before** the animation gets played.

</br>

### After Ranged Animation
```js
Hooks.on('oifWeaponRangedPostPrepare', (data) => {});
```
This hook fires **after** the ranged animation is played, and **before** the interaction and sound.

### After Ranged Interaction
```js
Hooks.on('oifWeaponRangedPostInteraction', (data) => {});
```
This hook fires **after** the ranged interaction.

### After Ranged Sound _(currently not implemented)_
```js
Hooks.on('oifWeaponRangedPostSound', (data) => {});
```
This hook fires **after** the ranged sound.


</br>

### After Lighting Preparation
```js
Hooks.on('oifItemLightingPostPrepare', (data) => {});
```
This hook fires **after** the data that will be used on the lighting automation gets prepared, **before** it gets applied and **before** the sound.

</br>

### After Lighting Light Apply
```js
Hooks.on('oifItemLightingLightPostApply', (data) => {});
```
This hook fires **after** the lighting light gets applied.

### After Lighting Light Sound _(currently not implemented)_
```js
Hooks.on('oifItemLightingLightPostSound', (data) => {});
```
This hook firest **after** the lighting light sound gets played.

</br>

### After Lighting Extinguish Apply
```js
Hooks.on('oifItemLightingExtinguishPostApply', (data) => {})
```
This hook fires **after** the lighting extinguish gets applied.

### After Lighting Extinguish Sound _(currently not implemented)_
```js
Hooks.on('oifItemLightingExtinguishPostSound', (data) => {})
```
This hook fires **after** the lighting extinguish sound gets played.
