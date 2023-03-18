## [Dynamic Diffuse Global Illumination (DDGI)](https://morgan3d.github.io/articles/2019-04-01-ddgi/)
* Regular grid of irradiance probes
    * Probes stored in two texture maps (RGB, RG)
        * Each texture map stores 4 copies of the same view at different heights above the scene
        * The first map stores irradiance of each probe in 6x6 tiles
        * The second map stores radius, radius^2 visibility of each probe in the R,G channels, in 16x16 tiles
        * Each probe tile is octahedron-encoded, and has a 1px border for bilinear blending between probes
    * Probe textures arranged into cascades (like cascaded shadow maps)
        * Lower resolution (coarser) cascade probes map to a larger area of the world
        * More probes in higher resolution (finer) cascades
        * Update finer cascade probes more frequently than coarse cascade probes
        * Fade out coarse cascades
* Algorithm
    1. Generate ~200 rays per probe, generate G-Buffer with pixel per hit
    2. Use deferred shading to compute each pixel output
    3. Each probe finds rays that affect it, and blends in the new pixel data using an exponentially-weighted moving average, like TAA
    4. For each pixel on screen, shade it by sampling from the probes
* Advantages
    * Avoids light leaks and noise
    * Fully dynamic
    * Can be tuned to never update (baked) or update more slowly for mobile or weaker devices
* Disadvantages
    * Diffuse indirect only (no specular, no direct)
    * Requires shadow-map like bias parameter

## [GI-1.0](https://gpuopen.com/download/publications/GPUOpen2022_GI1_0.pdf)
* TODO

## Godot SDFGI
* https://www.docdroid.net/YNntL0e/godot-sdfgi-pdf
* https://www.docdroid.net/ILIv1Qj/godot-sdfgi-plan-for-41-pdf
* TODO

## [Real-time Global Illumination by Precomputed Local Reconstruction from Sparse Radiance Probes](https://arisilvennoinen.github.io/Projects/RTGI/index.html)
* TODO

## Unreal Engine Lumen
* https://youtu.be/2GYXuM10riw
* http://advances.realtimerendering.com/s2022/SIGGRAPH2022-Advances-Lumen-Wright%20et%20al.pdf
* http://advances.realtimerendering.com/s2022/SIGGRAPH2022-Advances-RayTracingOpenWorlds-NetzelCosta.pptx
* TODO

## Surfel GI
* https://youtu.be/Uea9Wq1XdA4
* http://advances.realtimerendering.com/s2021/SIGGRAPH%20Advances%202021%20-%20Surfel%20GI.pdf

## ReSTIR
* https://research.nvidia.com/publication/2020-07_spatiotemporal-reservoir-resampling-real-time-ray-tracing-dynamic-direct
* https://d1qx31qr3h6wln.cloudfront.net/publications/ReSTIR%20GI.pdf
* https://research.nvidia.com/publication/2022-07_generalized-resampled-importance-sampling-foundations-restir
* https://graphics.cs.utah.edu/research/projects/volumetric-restir/
* https://agraphicsguynotes.com/posts/understanding_the_math_behind_restir_di/
* TODO

## [Kajiya](https://github.com/EmbarkStudios/kajiya/blob/main/docs/gi-overview.md)
* TODO

## [Unity Probe Lighting](http://advances.realtimerendering.com/s2022/SIGGRAPH2022-Advances-Enemies-Ciardi%20et%20al.pdf)
* TODO

## [Voxel Cone Tracing](https://research.nvidia.com/publication/2011-09_interactive-indirect-illumination-using-voxel-cone-tracing)
* TODO

## [Light Propagation Volumes](https://www.advances.realtimerendering.com/s2009/Light_Propagation_Volumes.pdf)
* TODO

## Screen-space GI (SSGI)
* Diffuse: https://github.com/Patapom/GodComplex/blob/master/Tests/TestHBIL/2018%20Mayaux%20-%20Horizon-Based%20Indirect%20Lighting%20(HBIL).pdf
* Occlusion:
    * https://www.activision.com/cdn/research/Practical_Real_Time_Strategies_for_Accurate_Indirect_Occlusion_NEW%20VERSION_COLOR.pdf
    * https://drive.google.com/file/d/1SyagcEVplIm2KkRD3WQYSO9O0Iyi1hfy/edit
* Specular:
    * https://www.ea.com/frostbite/news/stochastic-screen-space-reflections
    * https://media.githubusercontent.com/media/GPUOpen-Effects/FidelityFX-SSSR/master/docs/FFX_SSSR_Technology.pdf
    * https://gpuopen.com/learn/hybrid-reflections/
* TODO
