## Guia para trabajar en Informe 8 (Optimal BST)

1. Implemente un algoritmo recursivo para resolver el problema del **árbol binario de búsqueda óptimo**. 	
	- El algoritmo deberá minimizar el costo esperado (cantidad de nodos visitados por búsqueda) y retornar este valor.
	- Cuente la cantidad de llamadas recursivas que realiza el algoritmo.

2. Implemente un acercamiento **bottom-up** (programación dinámica) para resolver el problema.
	- El algoritmo deberá minimizar el costo esperado (cantidad de nodos visitados por búsqueda) y retornar este valor.
	- Cuente la cantidad de subproblemas que tiene que resolver el algoritmo.

3. 	Incorpore la función opción **visualize** de tipo boolean en ambos algoritmos.
	- En caso de que su valor sea True, se deberá mostrar visualmente el árbol óptimo encontrado, haciendo uso de librerías externas.

4. Incorpore la opción **verbose** en ambos algoritmos para poder ver, de **manera amigable e intuitiva**, su ejecución paso a paso.

5. Demuestre por qué el algoritmo bottom-up es **correcto** (es decir, calcula el árbol con mínimo costo).

    Para demostrar que el algoritmo es correcto debe:
    a. Demostrar/explicar que resolver el problema original es equivalente a resolver una serie de subproblemas de menor tamaño y combinar sus resultados (subestructura óptima)
    b. Definir una función recurrente para el valor óptimo, usando el resultado del punto a.
    c. Demostrar (por inducción o propiedad de bucle invariante) que el algoritmo **bottom-up** resuelve cada subproblema en base a la función recurrente y los valores obtenidos por subproblemas más pequeños resueltos con anterioridad.

6. Analice el **tiempo de ejecución** de ambos algoritmos.
	- Defina una función matemática para describir la cantidad de subproblemas que se deben resolver en función del tamaño de entrada.
	- ¿Cuál es el tiempo de ejecución de cada subproblema? ¿Cuál es el tiempo de ejecución del algoritmo?
	- Indique y explique la complejidad espacial del algoritmo (cantidad de memoria requerida).

7. Realice experimentos para:
	- Observar lo que ocurre con el tiempo de ambos algoritmos a medida que crece el tamaño del problema.
	- Observar lo que ocurre con el tiempo de ambos algoritmos y con el costo esperado calculado, si es que seleccionamos al elemento con mayor probabilidad de ser buscado como raiz del árbol (no consideramos otros elementos como raíz). Comentar si vale la pena realizar este cambio para problemas con *n* grande.

Puede guiarse con el [tutorial de grafos con networkx](https://github.com/rilianx/ADA/blob/main/Guías%20para%20Informes/mini-tutoriales/Grafos_con_networkx.ipynb) para mostrar los árboles de manera visual. **No es obligatorio utilizar exactamente esta librería**, es libre de utilizar cualquier librería que estime conveniente y que permita visualizar los árboles.  

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.

### Generación de instancias
Se recomienda utilizar el siguiente código para generar las instancias.

````
import random
import numpy as np

def optimal_bst_instance_generator(n):
    keys = sorted(random.sample(range(1, 100), n))
    arr = np.random.random(n*2+1)
    arr /= arr.sum()
    
    p = list(arr[:n]) # Probabilidad de las claves
    q = arr[n:] # Probabilidad de las claves ficticias
    return keys, p, q
    
keys, p, q = optimal_bst_instance_generator(10)
````

La función recibe el número de claves a generar (n) y genera 3 arreglos:
- **keys** contiene las claves a buscar. Contiene n elementos.
- **p** contiene las probabilidades de escoger cada una de las claves. Contiene n elementos.
- **q** contiene las probabilidades de escoger alguna de las claves ficticias (búsquedas fallidas). Contiene n + 1 elementos.
