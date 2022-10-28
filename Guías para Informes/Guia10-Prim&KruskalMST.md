## Guia para trabajar en Informe 11 (Prim’s & Kruskal's Minimum Spanning Tree)

1. Implemente el **algoritmo de Prim** o el **algoritmo de Kruskal** segun le corresponda.
    - Considerar que estos algoritmos son de tipo **voraz** (greedy).
    - Debe retornar las conexiones (edges) y su peso.

2. 	Incorpore la opción **visualize** de tipo boolean.
	- En caso de que su valor sea True, se deberá mostrar visualmente el grafo (camino) resultante trabajando mediante una libreria externa como lo es **networkx**.

3. Incorpore la opción **verbose** para poder ver, de **manera amigable e intuitiva** la ejecución paso a paso.

4. Demuestre por qué el algoritmo es correcto.
    - Mediante el metodo que estime conveniente.
    - **Algoritmo de Prim**: Informacion relevante se puede encontrar en la sección 15.4 del libro Algorithms Illuminated, Part 3.
    - **Algoritmo de Kruskal**: Informacion relevante se puede encontrar en la sección 15.7 del libro Algorithms Illuminated, Part 3

5. Analice el **tiempo de ejecución** del algoritmo.

6. Realice experimentos para:
    - Observar lo que ocurre con el tiempo del algoritmo a medida que aumenta la cantidad de nodos del grafo.
    - Comparar el **algoritmo de Prim** con el **algoritmo de Kruskal** (pidalo a algun compañero).

Puede guiarse con el [tutorial de grafos con networkx](https://github.com/rilianx/ADA/blob/main/Guías%20para%20Informes/mini-tutoriales/Grafos_con_networkx.ipynb) para mostrar los árboles de manera visual. **No es obligatorio utilizar exactamente esta librería**, es libre de utilizar cualquier librería que estime conveniente y que permita visualizar los árboles.  

### Generador de instancias:

```py
import random

# Crea un grafo de tipo array de arrays
# que contiene [i, j, peso]
# siendo i y j los nodos conectados
def graph_instance_creator(V):
  graph = []
  for i in range(V):
    for j in range(i+1, V):
      graph.append([i, j, random.randint(1, 500)])
  
  return graph
```

### Usando la libreria networkx:

```py
import networkx as nx

# Recibe un grafo de tipo array
# Retorna un nx.Graph de la libreria networkx
def graph_to_nxgraph(graph):
  nxgraph = nx.Graph()
  for i in graph:
    nxgraph.add_edge(i[0], i[1], weight=i[2])
  return nxgraph
```

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.
