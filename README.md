# BezierRiver
Using Bézier curve to geometrically calculate river migration based on channel curvature 

Define control points. In this example, n = 4 (quadratic Bézier curve)

```
def bezier_curve(control_points, t):
    n = len(control_points) - 1
    result = np.zeros_like(control_points[0], dtype=float)
    for i in range(n + 1):
        result += control_points[i] * comb(n, i) * t**i * (1 - t)**(n - i)
    return result
```
