# Addon Preferences

### Change View Mode

If enabled (default), the viewport shading will be changed to object colors to make objects more distinguishable when the planet terrain is enabled.

### Change Viewport Clipping Distance

When enabled (default), the viwport far clip plane is set to the Camera Clipping Distance. Because PlanetSet works in true scale, the far clip plane needs to be set very far away to make things in the distance visible. This can cause z-fighting artifacts in the rasterized viewport, but this will not show up in Cycles renders.

The scene's main camera will always have its far clip plane set to the camera clipping distance automatically.

### Camera Clipping Distance

The far clip plane distance for the main camera, and viewport if enabled. For Earth scale planets, the default value should be sufficient.