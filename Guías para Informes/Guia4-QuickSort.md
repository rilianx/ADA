## Guía para trabajar en Informe 4 (QuickSort)
1. Implemente la función **Partition**, de cada una de las siguientes maneras:
    - Seleccionando como pivote el último elemento del arreglo.
    - Seleccionando como pivote el primer elemento del arreglo.
    - Seleccionando como pivote la mediana de tres elementos al azar del arreglo.
    
    No olvide incorporar un contador para el **número de comparaciones** que realiza la función, con cada una de las implementaciones.

2. Implemente el algoritmo **QuickSort** (recursivo). 
    - Incorpore la opción **verbose** para poder ver su ejecución paso a paso y de **manera amigable e intuitiva**.

3. Explique por qué el algoritmo es correcto (prueba de correctitud). 
    1. Utilice una **propiedad invariante de bucle** para probar la correctitud de la función **Partition**.
    2. Utilice **inducción** para probar la correctitud del **QuickSort**.
4. Analice el **tiempo de ejecución** del algoritmo.
5. Realice experimentos para:
    - comparar el número de comparaciones realizadas experimentalmente con el **mejor** y **peor caso** teóricos.
    - comparar el algoritmo QuickSort, con MergeSort.
    - comparar el rendimiento del algoritmo al modificar la selección del pivote (punto 1).
    - recuerde **analizar** y **explicar** todos los resultados obtenidos.
