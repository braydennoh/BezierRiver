# BezierRiver
Using Bézier curve to geometrically calculate river migration based on channel curvature 

## Manual
Define Bézier curve with flexible control points. 
```
def bezier_curve(control_points, t):
    n = len(control_points) - 1
    result = np.zeros_like(control_points[0], dtype=float)
    for i in range(n + 1):
        result += control_points[i] * comb(n, i) * t**i * (1 - t)**(n - i)
    return result
```
Define control points. In this example, n = 4 (quadratic Bézier curve).
```
def bezier_curve(control_points, t):
    n = len(control_points) - 1
    result = np.zeros_like(control_points[0], dtype=float)
    for i in range(n + 1):
        result += control_points[i] * comb(n, i) * t**i * (1 - t)**(n - i)
    return result
```

Generate points along the Bezier curve.
```
t_values = np.linspace(0, 1, 100)
curve_points = np.array([bezier_curve(control_points, t) for t in t_values])

plt.plot(curve_points[:, 0], curve_points[:, 1])
plt.scatter(control_points[:, 0], control_points[:, 1], color='red')
```
![alt text](https://github.com/snohatech/BezierRiver/blob/main/bezierfigure/1.png)

