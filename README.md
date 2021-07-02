# Material Rendering implemented with OpenGL
This is a simple CG project for learning, including 6 sample materials.

### 1. White Chalk

The material should have a rough feeling, so "NormalMap" texture and bump mapping effect is used. The shape is adjusted to be finer and the color is set similar to real white chalk.

As the reflection of chalk should not include specular reflection, the fragment color is computed as:

```math
R_{rgb} = C_{rgb}\left( I \cdot k_d \cdot \max\left( \frac{N \cdot -L}{|N||L|} , 0\right) + a \right)
```

Where $`C_{rgb}`$ is object color, $`I`$ is light color, 
