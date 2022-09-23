##Guia para trabajar en Informe 7 (Cutting a Rod)
1. Implemente la funcion **CutRod**.
    - Comenzar con una **Naive Implementation** (implementacion realizada a fuerza bruta, utilizando atajos para mas simplicidad).
    - Luego realizar implementacion utilizando un acercamiento bottom-up.
    - Incorporar la opción **verbose** para poder ver su ejecución paso a paso de **manera amigable e intuitiva**.  

2. Implemente la funcion **RandomTest**.
    - Función que servirá para crear casos de prueba de distintos tamaños.
    - Debe resivir un valor **N**, con el que se generará un arreglo de precios de este tamaño.
    - El valor de **arr[i]** debe ser igual a **i** mas el valor del arreglo en la casilla anterior **arr[i - 1]** y esto sumado a un numero aleatorio entre 0 y 10.

3. Explique por que el algoritmo es correcto.
    - Para esto se espera que las piezas finales de largo i tengan un mejor valor que las piezas sobrantes nuevamente cortadas de largo (n - i).  

4. Analice el **tiempo de ejecución** del algoritmo.
5. Realice experimentos para:
    - Comparar tu "Naive Implementation" con la implementacion realizada con el acercamiento bottom-up.

Recuerde revisar los [criterios de evaluación para informes](https://github.com/rilianx/ADA/blob/main/Gu%C3%ADas%20para%20Informes/CriteriosEvaluacion.md).

Al terminar su informe súbalo a su repositorio Github **ADA-Informes** en su cuenta personal.
