### Reporte del artículo "Convex Optimization for Big Data" de Volkan Cevher, Stephen Becker y Mark Schmidt.

El artículo comienza señalando que en la optimización convexa se está reinvendo en referencia al Big Data, donde el tamaño de los datos y los poaramteros para problemas de optimizaciòn son demasiando grandes como para ser procesados localmente, y donde inclusive para el algebra lineal básica se tiene que adoptar una nueva estrategia para realizar las operaciones. En este nuevo paradigma basado en "tamaño", los algoritmos convexos ya no tienen necesidad de buscar soluciones muy precisas, pues los modelos de Big Data son necesariamente simple o inexactos.

En la sección "The basics" describen el fundamento de la "Big Data Optimization" con la siguiente funcion compuesta: F^* = min{F(x) = f(x) + g(x) : x E R^p} donde f y g son funciones convexas.

El artículo esta estructurado sobre los siguientes 3 puntos siguientes:

- Métodos de primer orden.

- Randomización.

- Cómputo paralelo y distribuido.

__Métodos de primer orden__

En esta sección el artículo describe el procedimiento cuando la función objetivo es "suave" y cuando la función objetivo es "compuesta".

En el primer caso se asume que la función objetivo sólo consiste en una función convexa y diferenciable f. La técnica de primer orden que se utiliza en este caso es el método del gradiente, que utiliza el gradiente local grad{f(x)} y calcula de manera iterativa: x^{k+1} 0 x^k - alpha_k grad{f(x^k)}, donde k se refiere a la k-ésima iteración y alpha_k es el paso que definmos y que asegura la convergencia.

