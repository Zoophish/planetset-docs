![](media/cloud_bw.jpg)

# Clouds Panel

The clouds panel is located in the atmosphere panel. To enable clouds, check the check box in the clouds panel header.

![Clouds Panel](media/clouds_panel.jpg){: style="width: 35%"}

If you used the `Adjust Cycles Settings` operator, the viewport [step rate](https://docs.blender.org/manual/en/latest/render/cycles/render_settings/volumes.html) will be set to 5 to speed up interactive rendering. This will make clouds look less detailed and also less dense, so it is a good idea to occasioanlly turn the step rate down to preview what the clouds will look like in the final render.

![Volume Settings](media/volumes_render_settings.jpg){: width=50% }

---

# Cloud Layers

## Moving Clouds

Do not translate the cloud domain in the z axis as this will cause the cloud shader to render incorrectly. When grabbing the cloud domain (++g++), restrict the translation to the XY plane by pressing ++shift+z++. Control altitude using the settings in the cloud panel.

![Moving Clouds](media/moving_clouds.gif){: width=70% }

## Domain & Shader Settings
Cloud layers have separate settings for the domain and cloud shader. The domain is the geometry that Cycles will treat as a volume. The clouds are rendered inside the volume by a cloud shader. The cloud domain settings are decoupled from the shader settings, so you typically need to match the radius, height and altitude of the domain with the shader.

![](media/cloud_settings.jpg){: width=40% }

---

# Cloud Layer Types

## Simple Clouds

![Simple Clouds](media/generic_clouds.jpg)

This cloud layer can be used to recreate many different types of clouds by altering the parameters. The cloud domain contains the cloud shader medium. It is a cylinder that follows the curvature of the planet when the radius is large enough, meaning clouds may extend over the horizon.

This cloud shader is more suited to softer clouds that don't have billow features, such as stratus and cirrus clouds.

### Settings

**Domain Radius**  
Radius of the cylindrical cloud domain.

**Domain Height**  
Height of the cylindrical cloud domain.

**Domain Altitude**  
The altitude of the domain.

**Height**  
Exactly the same as domain height, but this value is fed to the shader instead of the domain geometry. For most purposes, this should match the domain's height.

**Altitude**  
The altitude of the cloud layer in the shader (should be identical to domain altitude).

**Radius**  
The radius in which the cloud layer terminates completely (should match domain radius).

**Inner Radius**  
The radius at which the cloud falloff begins.

**Density**  
The overall scattering density of the cloud layer. Higher values yield thicker, darker looking clouds that let less light through.

**Coverage**  
Controls the amount of cloud in the domain. A lower value produces smaller clouds with more spacing and vice versa for a higher value.

**Scale**  
Controls how large each individual cloud is. Smaller values produce larger looking cloud features.

**Base Roughness**  
Determines how smooth/turbulent the base (lower altitude parts) of the clouds are.

**Upper Roughness**  
Like base roughness, but for the higher altitude part of the clouds. Clouds in nature are typically rougher at the top.

**Sharpness**  
Controls how abrupt the cloud edges are (which also makes the edges more dense).

**Edge Darkness**  
Artificially increases the darkness of the exterior parts of the clouds, giving them a 'powder' look. This effect is more prominent when the step rate decreases, so be careful not to increase it too much or it will make the clouds look dark.

**Dark Edge Sharpness**  
Defines the sharpness of the dark edges. Higher values will make the edges sharper, but also decrease the overall darkness.

**Stretch Factor**  
This parameter stretches the cloud shader domain, causing clouds either to look flatter or taller. Higher values will make the clouds look flatter and vice versa. This can be used to create flatter cirrus or stratus clouds.

---

## Warp Clouds

![Warp Clouds](./media/example-scenes/warp_clouds_demo_1.jpg)

This cloud shader is like simple clouds, but more realistic at the expense of render time. It can be used generically for cumulus and stratus clouds.

### Settings

**Domain Radius**  
Radius of the cylindrical cloud domain.

**Domain Height**  
Height of the cylindrical cloud domain.

**Domain Altitude**  
The altitude of the domain.

**Height**  
The overall depth of the cloud layer.

**Altitude**  
The altitude of the cloud layer in the shader (should be identical to domain altitude).

**Radius**  
The radius in which the cloud layer terminates completely (should match domain radius).

**Inner Radius**  
The radius at which the cloud falloff begins.

**Density**  
The overall scattering density of the cloud layer. Higher values yield thicker, darker looking clouds that let less light through.

**Coverage**  
Controls the amount of cloud in the domain. A lower value produces smaller clouds with more spacing and vice versa for a higher value.

**Scale**  
Controls how large each individual cloud is. Smaller values produce larger looking cloud features (excluding height).

**Roughness**  
Controls the smoothness/turbulence of the clouds by increasing the strength of smaller cloud shape variations (also consequently increases coverage slightly).

**Primary Billowness**  
Controls the strength of the billow pattern on the base shape of the cloud. The base shape makes up the large features of the clouds which are later refined with fractal details.

**Secondary Billowness**  
Controls the strength of the billow pattern on the cloud details.

**Sharpness**  
Controls how abrupt the cloud edges are (makes the edges more dense). Higher values will make the clouds a more homogeneous (uniform) density.

**Edge Darkness**  
Artificially increases the darkness of the exterior parts of the clouds, giving them a 'powdery' look. This effect is more prominent when the step rate decreases, so be careful not to increase it too much or it will make the clouds look artificial.

**Dark Edge Sharpness**  
Defines the sharpness of the dark edges. Higher values will make the dark regions on the edges sharper, but also decrease the overall darkness.

---

## Cirrus 2D

High altitude strandy/wispy clouds. This cloud layer is a 2D approximation which works well at high altitudes.

### Settings

**Alttiude**  
The altitude of the cloud plane.

**Density**  
Controls the strength of the clouds. Higher values look thicker and scatter more light.

**Scale**  
The overall scale of the cloud shape features. Lower values are larger and higher values are smaller.

**Softness**  
Controls how abrupt the cloud edges are.

---

## Mist Volume

Ground level fog/mist that exponentially decays with altitude. Fog/mist works particularly well in night, dawn or dusk lighting.

### Settings

**Radius**  
Radius of the cylindrical mist domain.

**Depth**  
The height of the mist domain. A general guideline is to keep this 4x larger than the exp altitude to hide an abrupt end to the fog.

**Density**  
The sea-level scattering density of the mist.

**Exp Altitude**  
The altitude in which the density is 36.7% that of the sea-level density.

**Base Altitude**  
The altitude that represents the zero height level for the exponential density. Since the exp altitude cannot be negative, if you would like the exp altitude to be lower than sea level, you can set the base altitude to a negative value.

**Noise Coverage**  
Similar to cloud coverage, lower values will create larger regions of no mist.

**Noise Scale**  
The scale of the mist fractal noise (lower values create larger patchy features).