- Binary Space Partitioning (BSP) Trees
- Z-Buffering
	- Hidden-Surface Removal
	- $\mathcal{O}(n)\::\:\text{where } n\propto \text{num triangles}$
	- $z[x,y]=z$
- Painter's Algorithm $\neq$ Ray Tracing
	- Sorts $n$ triangle depths $\mathcal{O}(n\log n)$
- Back-face Culling

- Barycentric Coordinates
	- $(x, y) = \alpha A + \beta B + \gamma C$
	- mipmaps \ anisotropic filtering
	- Bump mapping (perturbed normals)

# OpenGL
- Workflow
	- OpenGL commands
- vertices
	- Pre-Vertex Ops
- transformed vertices
	- Rasterizer  |  > Texturing
- fragments
	- Per-Fragment Ops
- shaded fragments
	- Frame Buffer Ops
	- Pixels in frame buffer

## OpenScene Graph (OSG) 3D
- Build with: \[C++ & OpenGL\]
- Succeeded by -> VulkanSceneGraph (VSG)
- Scene graph structure (hierarchical)
- beyond OpenGL (e.g. culling, state sorting)