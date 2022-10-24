## Guia para trabajar en Informe 11 (Strongly Connected Components)

1. Implemente un algoritmo recursivo para obtener el **componentes fuertemente conectados** de un grafo.
    - Implemente teniendo en cuenta DFS (Depth First Search).
    - Debe retornar un lista de arreglos, con los nodos fuertemente conectados encontrados.

2. Implemente mediante un algoritmo DFS-recursivo (Algoritmo de Kosaraju).
    - Cuente la cantidad de llamadas recursivas que realiza el algoritmo.

3. 	Incorpore la opción **visualize** de tipo boolean.
	- En caso de que su valor sea True, se deberá mostrar visualmente el grafo en el que se está trabajando mediante una libreria externa como lo es **networkx**.

4. Incorpore la opción **verbose** para poder ver, de **manera amigable e intuitiva** la ejecución paso a paso.

5. Demuestre por qué el algoritmo es correcto.
    - Mediante induccion, o el metodo que estime conveniente.

6. Analice el **tiempo de ejecución** del algoritmo.

7. Realice experimentos para:
    - Observar lo que ocurre con el tiempo del algoritmo a medida que aumenta la cantidad de nodos del grafo.
    - Invente algun experimento.

Puede guiarse con el [tutorial de grafos con networkx](https://github.com/rilianx/ADA/blob/main/Guías%20para%20Informes/mini-tutoriales/Grafos_con_networkx.ipynb) para mostrar los árboles de manera visual. **No es obligatorio utilizar exactamente esta librería**, es libre de utilizar cualquier librería que estime conveniente y que permita visualizar los árboles.  

### Generador de instancias:

```py
from collections import defaultdict
import math
import random

# Crea un grafo sin ciclos de nodos de 0 a V - 1
# Retorna un dicionario [defaultdict(list)] 
# de key valor del nodo (0 a V - 1) y de value una 
# lista con los nodos a los cuales se conecta
def graph_instance_creator(V):
  nodes = random.sample(range(0, V), V)

  graph = defaultdict(list)
  for i in range(len(nodes)):
    rand = random.sample(nodes, random.randint(1, 3))

    if (rand[0] != i or (rand[0] == i and random.randint(1, 100) <= 50)) and not rand[0] in graph[i]:
      graph[i].append(rand[0])

    if len(rand) > 1:
      for j in range(len(rand)):
        if j + 1 >= len(rand):
          if not rand[0] in graph[rand[j]]:
            graph[rand[j]].append(rand[0])
        else:
          if not rand[j + 1] in graph[rand[j]]:
            graph[rand[j]].append(rand[j + 1])
  
  return graph
```

### Usando la libreria networkx:

```py
from collections import defaultdict
import networkx as nx

# Recibe un grafo de tipo [defaultdict(list)]
# Retorna un nx.DiGraph de la libreria networkx
def graph_to_nxdigraph(graph):
  nxdigraph = nx.DiGraph()
  for i in graph.keys():
    nxdigraph.add_node(i)
    for v in graph[i]:
      nxdigraph.add_edge(i, v)
  return nxdigraph
```

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.