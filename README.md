# curva
import time
import numpy as np
import matplotlib.pyplot as plt

def bezier_cubica(P0, P1, P2, P3, t):
    x = []
    y = []
    
    for i in range(len(time)):
        ti = t[i]
        ti2 = ti * ti
        ti3 = ti2 * ti
        
        
        xi = (1 - ti)**3 * P0[0] + 3 * (1 - ti)**2 * ti * P1[0] + 3 * (1 - ti) * ti2 * P2[0] + ti3 * P3[0]
        yi = (1 - ti)**3 * P0[1] + 3 * (1 - ti)**2 * ti * P1[1] + 3 * (1 - ti) * ti2 * P2[1] + ti3 * P3[1]
        
        x.append(xi)
        y.append(yi)
    
    return x, y


P0 = (0, 1)
P1 = (4, 5)
P2 = (6, 7)
P3 = (8, 9)


t = np.linspace(0, 1, 100)

x, y = bezier_cubica(P0, P1, P2, P3, t)

plt.plot(x, y)
plt.scatter([P0[0], P1[0], P2[0], P3[0]], [P0[1], P1[1], P2[1], P3[1]], c='red')
plt.xlabel('X')
plt.ylabel('Y')
plt.title('Curva de Bézier cúbica')
plt.grid(True)
plt.show()
