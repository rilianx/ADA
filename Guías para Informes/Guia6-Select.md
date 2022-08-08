## Guía para trabajar en Informe 6 (Select)
1. Implemente la función **PivotSelection**.
    - Divida el conjunto en grupos de 5 elementos cada uno.
    - Encuentre la mediana de cada grupo aplicado el algoritmo InsertionSort para ordenarlos.
    - Aplique la función **PivotSelection** recursivamente para encontrar la mediana *m* de las medianas identificadas en el paso previo.
    - Utilice la mediana *m* como pivote para la función **Partition**.
    
    No olvide incorporar un contador para el **número de comparaciones** que realiza la función.

2. Implemente el algoritmo **Select** (recursivo). 
    - Recuerde que no es necesario implementar la función **Partition** desde cero, ya que fue utilizada en el **QuickSort**. 
    - Incorpore la opción **verbose** para poder ver su ejecución paso a paso y de **manera amigable e intuitiva**.

3. Explique por qué el algoritmo es correcto (prueba de correctitud). 
    1. Utilice **inducción** para probar la correctitud del **Select**.
4. Analice el **tiempo de ejecución** del algoritmo.
5. Realice experimentos para:
    - comparar el número de comparaciones realizadas experimentalmente con el **mejor** y **peor caso** teóricos.
    - comparar el algoritmo Select, con Randomized-Select (selección del pivote aleatoria).
    - recuerde **analizar** y **explicar** todos los resultados obtenidos.