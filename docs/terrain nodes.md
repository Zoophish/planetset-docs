Once you have a flat planet surface, you can start creating terrain using geometry nodes. PlanetSet comes with some premade geometry node groups that can be combined to create various types of landscapes.

Preset nodes can be found in the default displacement group.

---

## Power Noise Terrain

This is a slightly more complicated modulated noise pattern that creates more believable terrain features such as moutains and valleys. It is used in the default node network.

![Power Noise](media/power_noise.jpg)

### Parameters

**Scale**  
The scale of the noise features in the xy coordinates (height not affected). Larger values produce smaller features.

**Distortion**  
Controls the strength of distortion in the noise which creates a warp effect.

**Exponent**  
This is the exponent part of the power noise. Increasing the value amplifies larger features relative to the smaller ones. However, it decreases the overall amplitude, so the amplitude will need increasing to compensate for this.

**Detail**  
The smallest level of detail in the noise pattern. 30 should be sufficient unless the noise is very large scale, whereby you may want to increase the value.

**Vector**  
The offset vector of the noise (in meters). Changes in the x and y will shift the noise features around along the planet surface. Changes in z will shift the entire terrain vertically.

!!! Tip
    Since Blender noise does not currently implement seeds, you can find new variations of noise by using large shifts in the x and y axes.

**Variance Scale**  
Variance modulates the contribution of detail over the terrain, creating a more natural looking surface. This controls the scale of the modulation. Larger values will create more variation over a smaller amount of space and vice versa for smaller values.

**Variance Exponent**  
Increasing this value makes the variance change more harshly.

## Radial Heightfield

If you wish to bring in satellite digital elevation maps or heightmaps from other terrain generation software, you can use this modifier. It radially masks the heightmap to blend it with the surrounding terrain.

![Radial Heightfield](media/radial_heightfield.jpg)

### Parameters

**Image**  
The image to be used as a heightfield.

**Position**  
Position of the center of the heightfield in the xy plane along the planet surface. The z component will change the overall elevation of the heightfield which can be used to align the heightmap's sealevel to the planet sealevel. Units are in meters.

**Radius**  
The radius of the heightfield circle (in meters).

**Falloff Radius**  
The radius, starting from the outside of the heightfield circle and going towards the center that is used for blending the terrain with surroundings. Larger values will create a longer transition. A zero value will eliminate the falloff effect and create a hard boundary.

**Amplitude**  
The maximum displacement height of the heightfield (in meters).

**Angle**  
Angle of rotation of the heightfield (through the z axis).

# Effects

The effects modify existing terrain features.

## Erosion Fractal

This adds a hydraulic erosion and deposition effect to the existing terrain. It works well over low frequency smooth terrain, but not on terrain that already has lots of details.

#### Parameters

**Scale**  
Sets the base scale of the erosion features in the xy plane (does not affect erosion depth). If this value gets too low, it can yield unnatural looking results.

**Erosion Strength**  
Controls the amplitude of the erosion effect.

**Directionality**  
Controls how much the erosion pattern follows the slope of the terrain.

**Base Sediment Level**  
Value between 0,1 that defines the level of sediment deposition at the base height. A higher value will raise the level of deposition at the higher points of the terrain.

**Upper Sediment Level**  
Like upper sediment level, but for the base height. Usually making this value greater than the upper seiment level value will yield more nautral looking results (since sediment flows downwards).

**Base Sediment Height**  
The terrain height (in meters) in which the sediment level will be equal to the base sediment level.

**Upper Sediment Height**  
The terrain height (in meters) in which the sediment level will be equal to the upper sediment level.


![Erosion Fractal](media/erosion_fractal.jpg)

## Terrace

This quantizes the terrain into different strata levels.

![Terrace](media/terrace.jpg)

### Parameters

**Num Levels**  
The number of discrete altitude levels to divide the terrain into.

**Sharpness**  
Controls the harshness of the jumps between the terraces.

**Sub Terraces**  
The number of discrete levels in the sub-terraces, which modulate the regular terraces.

**Sub Terrace Sharpness**  
The steepness of the sub terraces.

**From Min**  
The lower height level of the terrain. The terrain will be terraced in region between the minimum and maximum heights. Therefore, you should ensure the min and max heights encapsulate all of your terrain.

**From Min**  
The upper height level of the terrain.

## Proximity Leveller

Levels the terrain (in z axis) towards a target object, relative to the distance to the target object (e.g. a curve). Useful for creating specific areas of flat land for buildings or roads.

![Proximity Leveller](media/proximity_leveller.jpg){: width=60% }
![Proximity Leveller with Text](media/proximity_leveller_2.jpg){: width=60% }

### Parameters

**Object**  
The target object (works with curves too).

**Min Distance**  
The mimimum distance cut-off (in metres) to the target object for the level effect.

**Max Distance**  
The maximum distance (in metres) to the target object for the level effect. The terrain will be unaffected beyond this distance from the target object.

# Mask Nodes

Mask nodes output a value between 0 and 1 in basic shapes that can be used to manipulate terrain features. The inverse outputs the opposite value.

## Circle Mask

![](media/circle_mask_node.jpg){: width=20% }

### Parameters

**Vector**  
The coordinates for the mask shape to use (typically a position node).

**Center**  
The center point of the circle.

**Radius**  
The radius of the circle.

**Falloff Radius**  
The radius of the smooth transition on the outside of the circle.

## Rectangular Mask

![](media/rectangular_mask_node.jpg){: width=20% }

### Parameters

**Vector**  
The coordinates for the mask shape to use (typically a position node).

**Center**  
The center point of the circle.

**Size X**  
The length of one of the rectangle sides.

**Size Y**  
The length of the other rectangle side.

**Angle**  
Specifies the rotation of the rectangle in degrees.

**Falloff Radius**  
The distance for the smooth transition on the outside of the rectangle.