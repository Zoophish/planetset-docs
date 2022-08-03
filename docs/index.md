![PlanetSet](media/planetset_logo.png){: .center width=66%}

**Version 2022.2 Beta**

# Welcome to PlanetSet

Thanks for buying PlanetSet! If you encounter any bugs or issues please contact me on [BlenderMarket](https://blendermarket.com/) or in the [PlanetSet Discord](https://discord.gg/d5CCkh5pJs).

This version is a beta, so it is not fully featured and will have content updates.

For installation instructions, see [getting started](getting started.md).

There is also a community Discord chat server available [here](https://discord.gg/d5CCkh5pJs).

The docs should cover every feature of PlanetSet and provide some basic tutorials. You can use the search bar to search the docs for keywords. If you think something is missing, please contact me.

# Changelog

## 2022.2 (Beta)
- **Added:** Sun elevation and rotation shortcut in atmosphere settings.
- **Added:** [Proximity Leveller](terrain modifiers.md#proximity-leveller) terrain modifier.
- **Added:** Overhauled the Billow Clouds shader, 'Cloud Fractal 2', which is now faster and provides more consistent details and roughness control.
- **Added:** Exposure and gamma in color management settings are automatically changed when using the Adjust Cycles Settings operator (can be switched off in addon preferences).
- **Added:** Auto Leaf convenience operator to automatically set up leaf materials (alpha and translucency) if they are not already.
- **Improvement:** Terrain tessellation responds better to changes in FOV and altitude bias.
- **Improvement:** Mist density is now modulated by fractal noise for increased realism. See [mist](clouds.md#mist-volume).
- **Improvement:** Improved water realism by changing roughness variation modulator to a power fractal.
- **Improvement:** Atmosphere and sky default values changed to improve realism.
- **Improvement:** Adding a user displacement terrain modifier now copies the node group template.
- **Improvement:** Docs button moved in addon preferences.
- **Fix:** Power Clouds coverage issue fixed.
- **Docs:** Docs now have permalinks on headers.