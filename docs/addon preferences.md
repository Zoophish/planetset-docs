# Addon Preferences

### Change View Mode

If enabled (default), the viewport shading will be changed to object colors to make objects more distinguishable when the planet terrain is enabled.

### Change Color Management Settings

If enabled (default), the exposure and gamma values in [Color Management](https://docs.blender.org/manual/en/latest/render/color_management.html) will be altered when using the Adjust Cycles Settings operator to account for daylight.

### Change Viewport Clipping Distance

When enabled (default), the viwport far clip plane is set to the Camera Clipping Distance. Because PlanetSet works in true scale, the far clip plane needs to be set very far away to make things in the distance visible. This can cause [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) artifacts in the rasterized viewport, but this will not show up in Cycles renders.

The scene's main camera will always have its far clip plane set to the camera clipping distance automatically.

### Camera Clipping Distance

The far clip plane distance for the main camera, and viewport if enabled. For Earth scale planets, the default value should be sufficient.

### Change Cycles Settings on Init

Convenience option for running the `Change Cycles Settings` operator when PlanetSet is enabled. Use this to save yourself from manually running the Change Cycles Settings operator every time you make a PlanetSet scene.