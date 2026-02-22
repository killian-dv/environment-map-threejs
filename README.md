# Environment Map — Three.js Journey

Short recap of the **Environment Map** lesson from [Three.js Journey](https://threejs-journey.com/) by Bruno Simon.

---

**`scene.environment`** = lighting + reflections (IBL). **`scene.background`** = visible background. Same texture can do both.

**LDR** (PNG/JPG) or **HDR** (.hdr via `RGBELoader`). LDR works for lighting; HDR gives better reflections. Loaders: `TextureLoader`, `CubeTextureLoader`, `RGBELoader`.

**Cubemap**: 6 faces (px, nx, py, ny, pz, nz), use `CubeTextureLoader`. **Equirectangular**: single 360° image, use `TextureLoader`/`RGBELoader` + `EquirectangularReflectionMapping`; for LDR add `colorSpace = SRGBColorSpace`.

**Scene tweaks**: `environmentIntensity`, `backgroundIntensity`, `backgroundBlurriness`, `backgroundRotation`, `environmentRotation`.

**Real-time env map**: `WebGLCubeRenderTarget` (e.g. `HalfFloatType`) + `CubeCamera`. Assign to `scene.environment`. Use **layers** so the cube camera only renders what should be reflected. Call `cubeRenderCamera.update(renderer, scene)` each frame before the main render.

**GroundedSkybox**: skybox that stops at the ground instead of a full sphere.
