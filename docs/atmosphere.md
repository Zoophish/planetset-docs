![](media/atmosphere.jpg){: width=80% }

The atmosphere can be enabled in the atmosphere sub-panel. This will add an atmosphere domain around the scene and change the scene's world background.

![Atmosphere Panel](media/atmosphere_panel.jpg){ width=50% }

# Atmosphere Settings

**Air Density**  
The sealevel density of air scattering. Higher values produce a thicker looking atmosphere.

**Air Exp Altitude**  
Controls the exponential falloff of air density with altitude. At this altitude, the air density will be 36.7% of the sealevel density.

**Aerosol Density**  
The sealevel density of aerosol scattering. Aerosols are larger particles in the air such as water vapour or smog.

**Aerosol Exp Altitude**  
Controls the exponential falloff of aerosol density with altitude.

**Sun Glow**  
Controls the proportion of light that is scattered forwards by aerosols towards the camera, producing a glow effect around the sun.

**Absorption Factor**  
The amount of light that is absorbed by aerosols, making the distance appear darker. For a poulluted air look, this value can be made higher. Humid air on the other hand does not absorb as much light, but could have a higher density.

**Atmosphere Ceiling**  
PlanetSet generates an 'atmospheric shell' around the scene when the atmosphere is enabled. This shell extends upwards into the sky until it reaches the *ceiling altitude*, which can be changed in the atmosphere panel.

You may want to make this value much larger to recreate scattering for taller mountains or for high-altitude clouds. However, as the ceiling gets higher, the atmosphere starts becoming more like a true sky. Eventually, it becomes unphysical to illuminate the sky volume with the Nishita sky background. This would be equivalent to outer space looking like the sky, whereas in outer space there is just the direct light coming from the sun and everything else is black. Therefore, the physical atmopshere option simply sets the background to black with a sun disk, and the colours of the sky are recreated naturally through volumetric scattering.

---

## Nishita Sky

The Nishita sky model is the default sky model built into Blender which users may be familiar with. PlanetSet adds a small scale medium around the planet to add the effect of Rayleigh scattering and haze to the terrain and distant clouds. The sky color comes from a combination of volume scattering and the sky lamp, which is fast but less accurate.

## Physical Atmosphere

![](media/space.jpg)

Enabling the physical atmosphere will often provide more realstic results, since all the sky color contribution comes from the atmosphere volume shader. It is particularly effective at high altitude shots and sunset/dawn shots. It also makes very high-altitude clouds look more realistic.