## Guia para trabajar en Informe 11 (Bellman-Ford)

1. Implemente el algoritmo de **Bellman-Ford** usando programación dinámica (acercamiento bottom-up) para resolver el problema del camino más corto, teniendo en cuenta las siguientes consideraciones.
    - En caso de que la instancia tenga solución, deberá retornar una lista con la distancia más corta entre el vértice fuente y cada uno de los demás vértices del grafo. 
    - En caso que no tenga solución dado que posee un ciclo negativo, deberá retornar una lista vacía y mostrar un mensaje indicando que el grafo tiene un ciclo negativo.

2. Implemente el algoritmo de **Dijkstra**.
    - Asegurese que los costos de los arcos sean siempre positivos. Puede modificar el generador de instancias para lograr esto.
    - Dado que nunca existirá un ciclo negativo, el algoritmo deberá retornar siempre una lista con la distancia más corta entre el vértice fuente y cada uno de los demás vértices del grafo. 

3. 	Incorpore la opción **visualize** de tipo boolean.
	- En caso de que su valor sea True, se deberá mostrar visualmente el grafo en el que se está trabajando mediante una libreria externa como lo es **networkx**.
    - Deberá mostrar al menos una vez en su informe el funcionamiento de esta función (es decir, ejecutar al menos una instancia con valor True).

4. Incorpore la opción **verbose** para poder ver, de **manera amigable e intuitiva**, su ejecución paso a paso.

5. Demuestre por qué el algoritmo de **Bellman-Ford** es correcto mediante **inducción**.

6. Analice el tiempo de ejecución de ambos algoritmos.

7. Realice los siguientes experimentos:
    - Para el algoritmo **Bellman-Ford**, genere al menos 25 instancias distintas para cada tamaño **n** de entrada y calcule la media de tiempo que demoran. Grafique y analice estos resultados. ¿Qué tanto se asemejan al tiempo de ejecución teórico?
    - Comparar los tiempos de ambos algoritmos en función del tamaño de entrada. ¿Cuál es más rápido? ¿por qué?

### Generador de instancias

Se recomienda utilizar el siguiente código para generar las instancias. En caso de que estime conveniente, puede utilizar su propio generador de instancias.

```py
import random

def is_valid_edge(generated_edges: dict, i: int, j: int):
    return i != j and not generated_edges.get((i, j), None) and not generated_edges.get((j, i), None)

def instance_generator(n: int):
    """
        Input: cantidad de vértices
        Output: una lista que contiene todos los arcos y el número del vértice fuente (la función retorna dos variables).
        Los arcos vienen en la forma (i, j, weight), donde i es el vértice origen del arco y j el vértice al que apunta el arco, mientras que weight es su peso.
    """
    graph = []
    nodes = random.sample(range(0, n), n)
    unvisited_nodes = random.sample(range(0, n), n)
    
    generated_edges = {}
    for i in nodes:
        rand = random.sample(nodes, random.randint(1, 3))

        for j in rand:
            edge = (i, j)
            edge_with_weight = (i, j, random.randint(1, 100))
            
            if generated_edges.get((edge[1], edge[0]), None):
                continue
            
            if i == j:
                new_vertice = None
                iterations = 0
                while new_vertice is None and iterations < 250:
                    iterations += 1
                    number = random.randint(0, n - 1)
                    if is_valid_edge(generated_edges, i, number):
                        new_vertice = number

                if iterations >= 250:
                    return instance_generator(n)
                
                edge = (i, new_vertice)
                edge_with_weight = (i, new_vertice, random.randint(-25, 100)) # -25 y 100 corresponde a los límites de los pesos, puede cambiarlos.
            
            graph.append(edge_with_weight)
            generated_edges[edge] = edge

            if edge_with_weight[1] in unvisited_nodes:
                unvisited_nodes.remove(edge_with_weight[1])

    for i in unvisited_nodes:
        valid_edge = False
        iterations = 0
        while not valid_edge and iterations < 250:
            iterations += 1
            m = random.randint(0, n - 1)
            if is_valid_edge(generated_edges, m, i):
                valid_edge = True
                edge = (m, i)
                edge_with_weight = (m, i, random.randint(-25, 100)) # -25 y 100 corresponde a los límites de los pesos, puede cambiarlos.
                graph.append(edge_with_weight)
                generated_edges[edge] = edge

        if iterations >= 250:
            return instance_generator(n)

    return graph, graph[0][0]
```

**NOTA:** El generador de instancias puede generar instancias en las que no existe una solución completa dado que no existe ningún camino desde el vértice fuente a uno o más vértices del grafo. Para estos casos, o bien buscar algún vértice dentro del mismo grafo que se pueda usar como vértice fuente y para el que exista solución, o bien generar una instancia nueva.

### Usando la libreria networkx

```py
import networkx as nx


def graph_to_nxdigraph(graph: list, n: int):
    """
        Input: Un grafo en formato list[tuple]. Ej: [(0, 1, 10), (1, 2, 15), (2, 0, 7)].
        Output: Un nx.DiGraph de la libreria networkx.
    """
    nxdigraph = nx.DiGraph()
    [nxdigraph.add_node(i) for i in range(n)]

    for v in graph:
        nxdigraph.add_edge(v[0], v[1], weight=v[2])

    return nxdigraph
```

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.
