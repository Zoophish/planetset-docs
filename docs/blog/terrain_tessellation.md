Blender ships with its capable Cycles renderer as well as a suite of geometry manipulation and scene creation tools. Modelling terrain surfaces manually is time-consuming and repetitive. This is why the introduction of geometry nodes in 3.0 was so important, as it allows things like this to be automated. The two terrain components I thought that needed automating were scale and detail. I addressed this using a combination of the Python API and geometry nodes, taking inspiration from software like Terragen and the older REYES renderers.

#### Method

To produce realistic horizons, the terrain's surface must be spherical like a planet. Since most of the sphere will be occluded by itself, we don't need the entire thing. The approach used in PlanetSet is to take a large plane and project it downwards onto a sphere. By projecting it downwards from the centre of the plane, we maintain floating point precision at the peak where the viewer is most likely to be. The plane is made up of quads that tessellate nicely. The quad size is scaled based on how high the viewer is, to ensure consistent tessellation (more on this later).

![]()

We need to ensure that the plane is large enough such that some terrain goes beyond visible curvature. One simple way of doing this is to figure out the distance from the viewer to the tangent of the planet sphere:

![](./GeometricDistanceToHorizon.png)

Which is simply 


Since the surface of the planet is not perfectly smooth, we can add on a fudge factor to the height to create slightly more terrain over the horizon. This is what the altitude bias parameter does in PlanetSet.

![](./sphere_section.png){: width=500pt}

The next step is detail. If we were to equally subdivide the entire terrain surface, we would quickly run out of memory as the surface area of the terrain is far too large to have a fixed number of faces per unit area. Instead, we can subdivide the geometry relative to the camera, since *most* mesh detail is directly perceived in the image space rather than world space. The exceptions here are mainly shading effects like shadows and reflections from outside the camera frustum and distant surface roughness that could affect the sub-pixel shading.

To know whether to dice (subdivide) a quad face, we need to measure its projected area in screen space. If the projected area is larger than the dicing rate (facets per pixel), we dice it. This is approximated in PlanetSet using the inverse square law multiplied by the cosine of its angle to the camera (which actually turns out to be a simple dot product). In PLanetSet, I scale this result by some magic constants, which were found empirically, to make it in terms of more intuitive units. Since displacing the terrain will significantly affect how the surface projects onto the image space, the face area measurements need to occur on the displaced surface (consider how going from a flat sphere to huge mountains would change the face projections for example). This means we first displace the smooth sphere surface, figure out which faces need to be diced, then dice the *un-displaced* smooth surface based on this information. This cycle is repeated until all facets are small enough in image space, or we have reached the iteration limit. We also omit faces outside the camera frustum for more efficiency (using the quad centroids to check). We can optionally discard geometry outside the camera frustum. I've found that for whatever reason, this is significantly faster, even though most of the geometry is inside the camera frustum.

![](./tessellation_wireframe.png){: width=800pt }

Going forwards, Blender 4.0 will feature repeat nodes and caching checkpoints in geometry nodes, which will allow this process to be done much more efficiently.

I also am hoping that at some point in the future, it will be possible to selectively subdivide faces rather than splitting the mesh and subdividing. This would prevent light leaks in the terrain surface which is currently a frustrating limitation.