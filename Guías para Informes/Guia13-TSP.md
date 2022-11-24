## Guia para trabajar en Informe 13 (TSP)

1. Implemente un algoritmo de **búsqueda local** para resolver el problema del vendedor viajero.
    - Genere su solución inicial factible de manera completamente aleatoria.
    - Su algoritmo debe utilizar la operación 2-change o 3-change. Es libre de utilizar cualquiera de las dos.
    - Su solución deberá ser el mejor tour encontrado, junto con su coste asociado.

2. Implemente un algoritmo **Greedy** para resolver el problema del vendedor viajero.
    - Comience el tour en un vértice arbitrario.
    - Mientras existan nodos no visitados, seleccione el vértice no visitado más cercano al vértice actual y avance hasta él.
    - El tour finalizará cuando todos los vértices sean visitados y se vuelva al vértice inicial.
    - Su solución deberá ser el tour encontrado junto con su coste asociado.

3. Incorpore la opción **verbose** para poder ver, de **manera amigable e intuitiva**, su ejecución paso a paso.

4. Analice el **tiempo de ejecución** del algoritmo de búsqueda local en base a lo estudiado durante el curso. ¿Se puede estudiar el tiempo de ejecución del TSP de la misma manera que los algoritmos anteriores vistos en el curso?

5. Realice los siguientes experimentos:
    - Compare y analice los resultados obtenidos por ambos algoritmos. 
    - Proponga e implemente una nueva forma de obtener su solución inicial factible para el algoritmo de búsqueda local. Compare y analice los resultados obtenidos por el algoritmo de búsqueda local al cambiar el método de selección de solución inicial.  

### Generador de instancias

Se recomienda utilizar el siguiente código para generar las instancias. En caso de que estime conveniente, puede utilizar su propio generador de instancias.

```py
import numpy as np

def dist(c1, c2):
   return np.sqrt( (c1[0]-c2[0])**2 + (c1[1]-c2[1])**2 )    

def generate_tsp_instance(n: int):
    """
        Input: cantidad de vértices.
        Output: una matriz de n x n. Cada posición M[i][j] dentro de la matriz indica la distancia que existe entre el vértice i y el vértice j.
    """
    cities = []
    for i in range(n):
        x, y = np.random.uniform(-100, 100), np.random.uniform(-100, 100)
        cities.append([x, y])
        
    instance = []
    for i, coord1 in enumerate(cities):
        instance.append([])
        for j, coord2 in enumerate(cities):
            if i != j:
                instance[i].append(dist(coord1, coord2))
            else:
                instance[i].append(0)
          
    return instance
```

Si desea transformar esta instancia en un grafo de networkx, hay que tener en consideración que M[i][j] es lo mismo que M[j][i], valor que corresponde a la distancia entre ambos vértices, o el peso del arco que los separa.

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.
