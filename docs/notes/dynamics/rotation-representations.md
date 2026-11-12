---
date: 2026-10-20
description: Rotation matrices, axis–angle, and unit quaternions.
---

# Rotation representations

A short reference on the three representations of 3D rotations that come up
most often in robotics, and on how to convert between them.

## Rotation matrices

A rotation is a matrix \(R \in SO(3)\):

$$
SO(3) = \{ R \in \mathbb{R}^{3\times 3} \mid R^\top R = I,\ \det R = 1 \}.
$$

Matrices compose by multiplication and act on vectors directly, but nine
numbers describe three degrees of freedom. Numerical drift has to be
corrected by re-orthogonalization.

## Axis–angle

Any rotation is a rotation by an angle \(\theta\) about a unit axis
\(\hat{\mathbf{k}}\). Rodrigues' formula gives the matrix:

$$
R = I + \sin\theta\, K + (1 - \cos\theta)\, K^2,
$$

where \(K\) is the skew-symmetric matrix of \(\hat{\mathbf{k}}\), so that
\(K\mathbf{v} = \hat{\mathbf{k}} \times \mathbf{v}\).

## Unit quaternions

A unit quaternion \(q = (w, \mathbf{v})\) with
\(w = \cos\frac{\theta}{2}\) and \(\mathbf{v} = \sin\frac{\theta}{2}\,\hat{\mathbf{k}}\)
represents the same rotation. \(q\) and \(-q\) are the same rotation
(double cover).

!!! tip "Why quaternions"
    Four numbers, no gimbal lock, cheap renormalization, and smooth
    interpolation (slerp). This makes them the usual choice for attitude
    in state estimators.

```python title="axis_angle_to_quaternion.py"
import numpy as np

def axis_angle_to_quaternion(axis: np.ndarray, angle: float) -> np.ndarray:
    """Return the unit quaternion (w, x, y, z) for a rotation about `axis`."""
    axis = axis / np.linalg.norm(axis)
    half = 0.5 * angle
    return np.concatenate(([np.cos(half)], np.sin(half) * axis))

q = axis_angle_to_quaternion(np.array([0.0, 0.0, 1.0]), np.pi / 2)
print(q)  # [0.7071 0.     0.     0.7071]
```

## Summary

| Representation | Parameters | Composition        | Singularities |
| -------------- | ---------- | ------------------ | ------------- |
| Matrix         | 9          | Matrix product     | None          |
| Axis–angle     | 3 (or 4)   | Via another form   | At \(\theta = 0\) |
| Quaternion     | 4          | Quaternion product | None          |

See also: [ODE integrators](../simulation/ode-integrators.md) for
integrating orientation over time.
