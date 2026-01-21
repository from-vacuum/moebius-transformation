# Möbius Transformation for POPs

A POP Operator(GLSL) that applies 4D Möbius transformations to 3D geometry via stereographic projection.

https://en.wikipedia.org/wiki/M%C3%B6bius_transformation

## How It Works

1. **Stereographic Projection** - 3D points are projected onto a 4D hypersphere
2. **4D Rotation** - Points are rotated in 4D space (XY and ZW planes)
3. **Back Projection** - Results are projected back to 3D

This creates smooth, continuous deformations that would be impossible in pure 3D.

Connect any POP geometry or just point cloud and make sure it is centerd at the origin.

## Params

### Core
| Uniform | Type | Default | Range | Description |
|---------|------|---------|-------|-------------|
| `Scale` | float | 1.0 | 0.1-10.0 | Scale factor |
| `Amount Radians` | float | 0.0 | 0.0-2*Pi | Time/animation |
| `p` | float | 1.0 | 0.0-3.0 | XY rotation speed |
| `q` | float | 1.0 | 0.0-3.0 | ZW rotation speed |

### Twist
| Uniform | Type | Default | Range | Description |
|---------|------|---------|-------|-------------|
| `twistAmount` | float | 0.0 | 0.0-6.28 | Twist intensity |

### Plane Transform
| Uniform | Type | Default | Description |
|---------|------|---------|-------------|
| `planeTransform` | int | 0 | Toggle (0/1) |
| `planeNormal` | vec3 | (0,1,0) | Target normal |
| `planeOrigin` | vec3 | (0,0,0) | Target origin |

### Noise
| Uniform | Type | Default | Range | Description |
|---------|------|---------|-------|-------------|
| `noiseAmp` | float | 0.0 | 0.0-0.5 | Noise strength |
| `noiseFreq` | float | 1.0 | 0.1-10.0 | Noise scale |
| `noiseSpeed` | float | 1.0 | 0.0-5.0 | Animation speed |
| `noiseOctaves` | float | 3.0 | 1-6 | Fractal layers |
| `noiseZScale` | float | 1.0 | 0.0-2.0 | Z-axis influence |

### Ripple
| Uniform | Type | Default | Range | Description |
|---------|------|---------|-------|-------------|
| `rippleAmp` | float | 0.0 | 0.0-0.5 | Ripple strength |
| `rippleFreq` | float | 10.0 | 1.0-50.0 | Wave density |
| `rippleSpeed` | float | 5.0 | 0.0-20.0 | Animation speed |
| `rippleOffset` | float | 0.0 | 0.0-6.28 | Phase offset |
| `rippleDecay` | float | 0.0 | 0.0-2.0 | Distance falloff |

## Tips

- Keep `noiseAmp` and `rippleAmp` low (< 0.2) for subtle effects
- Interesting `p:q` ratios: 1:1, 1:2, 2:3, 3:5
- `noiseOctaves` > 4 is expensive with diminishing returns
- Set `rippleDecay` > 0 for "stone in water" effect
