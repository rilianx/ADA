## Guia para trabajar en Informe 7 (Cutting a Rod)

1. Implemente un algoritmo recursivo para resolver el problema del **corte de varillas**. 
   - El algoritmo debe retornar los cortes necesarios y el retorno máximo posible.
   - Cuente la cantidad de llamadas recursivas que realiza el algoritmo.
   - En la descripción del algoritmo, recuerde explicar la **subestructura óptima** del problema y la función recursiva para el **retorno máximo**.

2. Implemente un acercamiento **bottom-up** (programación dinámica) para resolver el problema del **corte de varillas**. 
   - El algoritmo debe retornar los cortes necesarios y el retorno máximo posible.
   - Cuente la cantidad de subproblemas que tiene que resolver el algoritmo. 

3. Incorpore la opción **verbose** en ambos algoritmos para poder ver, de **manera amigable e intuitiva**, su ejecución paso a paso.  

4. Demuestre por qué el algoritmo bottom-up es **correcto** (es decir, calcula el retorno máximo).  
    - Puede usar inducción, establecer un caso base y para las iteraciones siguientes asumir que los problemas más pequeños ya fueron resueltos correctamente.

5. Analice el **tiempo de ejecución** del algoritmo.
    - Defina una función matemática para describir la cantidad de subproblemas que se deben resolver en función del tamaño de entrada $n$.
    - ¿Cuál es el tiempo de ejecución de cada subproblema? ¿Cuál es el tiempo de ejecución del algoritmo?
    - Indique y explique la complejidad espacial del algoritmo (cantidad de memoria requerida).

6. Realice experimentos para:
    - Observar lo que ocurre con el tiempo de ambos algoritmos a medida que crece el tamaño del problema.
    - Observe la cantidad de problemas que debe resolver el acercamiento bottom-up a medida que el problema crece.

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.

### Generación de instancias

Puede utilizar el siguiente código par generar instancias.
````
import random

def cutrod_instance_generator(N):
  A = []
  prev = 0
  for i in range(N):
    r=random.randint(0,10)
    A.append(prev+r)
    prev+=r
  return A

cutrod_instance_generator(10)
````
El algoritmo recibe el tamño del problema `N` y genera un arreglo de ese tamaño.

El $i$-ésimo elemento del arreglo corresponde al precio de las varillas de tamaño $i$.
