## Guia para trabajar en Informe 10

1. Implemente un algoritmo usando **programación dinámica** (acercamiento bottom-up) para resolver el problema de la mochila.
   - Recuerde identificar una estructura óptima para el problema y definir la **función de recursión** correspondiente.
   - Cuente la cantidad de subproblemas que debe resolver el algoritmo.

2. Implemente un algoritmo **greedy** para resolver el problema.
   - Cuente la cantidad de iteraciones que debe realizar el algoritmo.

3. Incorpore la opción **verbose** en ambos algoritmos para poder ver su ejecución paso a paso de **manera amigable e intuitiva**.

4. Muestre que el algoritmo de **programación dinámica es correcto**. ¿Por qué el algoritmo greedy no lo es?

5. Analice el tiempo de ejecución de ambos algoritmos.

6. Realice experimentos para:
    - Comparar los tiempos de ambos algoritmos en función del tamaño de entrada.
    - La cantidad de iteraciones/subproblemas que realizan los algoritmos en función del tamaño de entrada.
    - El valor de los items alcanzado por ambos algoritmos (puede hacer **boxplots** para distintos tamaños de problemas, por ejemplo 5, 10, 20 y 50).

[Material en GeeksforGeeks](https://www.geeksforgeeks.org/0-1-knapsack-problem-dp-10/)

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.

### Generación de instancias

Puede utilizar el siguiente código par generar instancias.
```py
import random

def knapsack_instance_generator(N):
  val = []
  wt = []
  prev_v = 0
  prev_w = 0
  for i in range(N):
    v = random.randint(1, 100)
    val.append(prev_v + v)
    prev_v += v
    
    w = random.randint(1, 10)
    wt.append(prev_w + w)
    if (v >= 50):
        prev_w += w

  W = int(sum(wt) / 2)
  return W, val, wt

W, val, wt = knapsack_instance_generator(10)
```
El algoritmo recibe el tamño del problema `N` y retorna la capacidad `W`, el arreglo de valores `val` y el arreglo de pesos `wt`.
