![Misty Mountains Render](media/misty-moutains/misty_mountains.jpg)

This tutorial will describe step-by-step how the render above was produced using PlanetSet.

![](media/misty-moutains/1.jpg)

Start a new Blend file. Make sure to keep the camera, but you can delete the default cube and lamp.

![](media/misty-moutains/2.jpg)

Create a planetary terrain by enabling planet in the PlanetSet toolbar.

![](media/misty-moutains/3.jpg)

Press the `Adjust Cycles Settings` button to switch over to Cycles for rendering.

![](media/misty-moutains/4.jpg)

To create a mountain landscape, add a Power Noise Terrain modifier from the `Add Terrain Modifier` menu.

You will now have a basic landscape to work with. You can use the flycam mode to navigate around the scene more easily by pressing ++shift+grave++.

![](media/misty-moutains/5.jpg)

When you have found an angle you are happy with, use the `Align Camera to View` operator, which you can find by pressing ++space++ to bring up the operator search menu.

This will reconstruct the terrain LOD relative to the view you chose:

![](media/misty-moutains/6.jpg)

![](media/misty-moutains/7.jpg)

Check the camera's height (z coordinate) by selecting it and viewing the Item panel. In this example, the camera height is approximately 80m, so the projection height is set to this value.

![](media/misty-moutains/8.jpg)

Now enable the atmosphere, by checking it in the PlanetSet panel and start the viewport renderer.

![](media/misty-moutains/9.jpg)

The day sky is very bright, so the film exposure will need turning down by selecting the camera and going to the camera data properties:

![](media/misty-moutains/10.jpg){: .zoom}

Turning down the exposure to 0.1:

![](media/misty-moutains/11.jpg){: .zoom}

![](media/misty-moutains/12.jpg){ .zoom}

Now adjust the sun elevation and angle in the world properties panel so that it is facing the camera.

You can also hide the floor grid and axes overlays in the viewport overlay options to declutter the viewport.

![](media/misty-moutains/13.jpg){: .zoom}

Now enable clouds and add a mist volume layer via the `Add Cloud Layer` menu.

![](media/misty-moutains/14.jpg)

Add a mist volume.

![](media/misty-moutains/15.jpg)

Add a generic clouds layer.

![](media/misty-moutains/16.jpg)

Translate the cloud layer in the xy plane by pressing ++g++ and then ++shift+z++. You must not translate clouds in the z axis or it will not curve with the planet surface correctly.

![](media/misty-moutains/17.jpg)

![](media/misty-moutains/18.jpg){: .zoom}

Adjust the cloud layer parameters to the ones in the screenshot which will produce small light cumulus clouds.

Also set the sun glow to 1 and make the atmosphere ceiling 3000m.

![](media/misty-moutains/19.jpg){: .zoom}

![](media/misty-moutains/20.jpg){: .zoom}

Set the base patch size to 1 to increase the terrain ridge details for the final render. It doesn't need to be much smaller as the terrain will be quite dark and details wont be visible.

![](media/misty-moutains/21.jpg){: .zoom}

You can also add more clouds in the distance to fill the sky more. The settings in the screenshot above produce large cumulus clouds over the horizon.

Don't forget, you can hide the cloud wireframes if they bother you by toggling the viewport overlays or you can change the viewport display to bounds.

Now everything is ready to render!