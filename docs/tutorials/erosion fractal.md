The erosion fractal add the effect of hydraulic erosion and sedimentation to existing terrain through the use of procedural noise. It does not use simulations which makes it ideal for large landscapes. The erosion fractal node is only available in the Hobbyist and Professional editions of PlanetSet.

The erosion fractal uses the slope of the terrain to etemine where to create the branching erosion effect. Therefore, for the effect to look right, we have to apply it to smooth, low frequency terrain. This can be done by using a noise texture with a low detail, as in the example below. Note that the scale is set to 1 / 1000m and the amplitude is scaled by 500m. The power node is also used to make the peaks higher and the valleys flatter.

![](../media/tutorials/erosion%20fractal/basic_noise.jpg){: .center}

![](../media/tutorials/erosion%20fractal/basic_noise_vp.jpg){: .center}

We can then apply the erosion fractal to the displaced terrain geometry directly like so:

![](../media/tutorials/erosion%20fractal/erosion_node.jpg){: .center}

![](../media/tutorials/erosion%20fractal/erosion_node_vp.jpg){: .center}

The default settings are designed to work well on typical terrain features that are kilometers wide and in the hundreds of meters tall. If the scaling is off, it can lead to results that don't look correct.

To increase the strength of the erosion pattern, we can increase the strength parameter:

(Strength = 50)
![](../media/tutorials/erosion%20fractal/erosion_node_vp_strength_50.jpg){: .center}

Similarly, the directionality strength affects how severly the slope guides the erosion pattern, which is useful for boosting the effect on flatter terrain features. Likewise, if the terrain is very steep, like in this example, turning it down may produce better looking results.

(Directionality = 2.5)
![](../media/tutorials/erosion%20fractal/erosion_node_vp_directionality_2_5.jpg){: .center}

To make the landscape more interesting, we can multiply the base noise by a larger scale noise to create flat areas:

![](../media/tutorials/erosion%20fractal/two_noises.jpg){: .center}

![](../media/tutorials/erosion%20fractal/two_noises_vp.jpg){: .center}

With the erosion fractal, we get this:

![](../media/tutorials/erosion%20fractal/two_noises_erosion_vp.jpg){: .center}
