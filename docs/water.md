# Water Bodies

![Water Bodies Panel](media/water_panel.jpg)

---

## Oceans

Oceans are water bodies that span the entire planet. Like the terrain surface, it is also tessellated to the dicing rate.

The ocean surface has its own separate displacement group like the planet terrain that can be found inside the Planet Ocean geometry nodes modifier. By default, there is a small noise displacement applied to mimic small waves. If you have the Hobbyist or Professional edition of PlanetSet, you will have access to the ocean displacement texture which can be used to create realistic animated waves.

**Sea Level:** The height of the ocean surface above zero in the z axis.

---

## User Water Bodies

You can convert the selected mesh to a water body by choosing `Make Selection Water Body` in the `Add Water Body` menu. This will assign the PlanetSet water shader to the mesh link it to the water bodies panel.

This can be used to make smaller water bodies such as lakes or ponds.


---

## Water Shader Settings

**Ripples Strength:** Controls the ripple intensity.

Shader ripples become slightly 'blurred' in the distance, which is an effect 3D displaced ripples don't account for. Therefore it is recommended to keep the ripple strength above zero for more realistic results, even if you are using displacement ripples.

![](media/water_ripples.jpg)

**Transparency:** Higher values make the water appear clearer by artificially increasing the transparency.

**Water Color:** The absorption color of the water medium.

**Color Strength:** The intensity of the water color.

**Sediment Base:** The base height of the sediment absorption. The sediment will gradually reduce up to the sediment top.

**Sediment Top:** The upper height of the sediment absorption.

**Edge Foam Thickness:** The thickness of the foam effect around edges intersecting the water. More specifically, the distance tolerance to a surface underneath the water surface that indicates foam should be present.

**Foam Sparsity:** Higher values break up the foam pattern more, lower values fill the pattern.
