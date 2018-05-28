### Reporte del artículo "Convex Optimization for Big Data" de Volkan Cevher, Stephen Becker y Mark Schmidt.

El artículo comienza señalando que en la optimización convexa se está reinvendo en referencia al Big Data, donde el tamaño de los datos y los poaramteros para problemas de optimizaciòn son demasiando grandes como para ser procesados localmente, y donde inclusive para el algebra lineal básica se tiene que adoptar una nueva estrategia para realizar las operaciones. En este nuevo paradigma basado en "tamaño", los algoritmos convexos ya no tienen necesidad de buscar soluciones muy precisas, pues los modelos de Big Data son necesariamente simple o inexactos.

En la sección "The basics" describen el fundamento de la "Big Data Optimization" con la siguiente funcion compuesta: F^* = min{F(x) = f(x) + g(x) : x E R^p} donde f y g son funciones convexas.

El artículo esta estructurado sobre los siguientes 3 puntos siguientes:

- Métodos de primer orden.

- Randomización.

- Cómputo paralelo y distribuido.

__Métodos de primer orden__

En esta sección el artículo describe el procedimiento cuando la función objetivo es "suave", cuando la función objetivo es "compuesta" y con funciones objetivo proximales.

En el primer caso se asume que la función objetivo sólo consiste en una función convexa y diferenciable f. La técnica de primer orden que se utiliza en este caso es el método del gradiente, que utiliza el gradiente local grad{f(x)} y calcula de manera iterativa: x^{k+1} = x^k - alpha_k grad{f(x^k)}, donde k se refiere a la k-ésima iteración y alpha_k es el paso que definmos y que asegura la convergencia. 

Los autores destacan que para minimización suave se pueden utilizar otros métodos que son más rápidos (i.e. requieren menos iteraciones) como Newton.

Detallan el algoritmo de Nesterov para el calculo de gradiente indicando que es el método que logra la mejor posible peor escenario error raty y que por ende se usualmente a este método se le denota como un método de primer orden óptimo.

Cuando la función objetivo es compuesta; es decir, la función objetivo consiste en un función convexa f y una función convexa no suave g, en general la no diferenciabilidad de g reduce la eficiencia de los métodos de primer orden. No obstante, se pueden utilizar metodos de gradiente proximales que tuilizan la misa aproximación para f pero incluyen el termino g.

El articulo detalla el algoritmo del gradiente proximal acelerado e indica que en casos donde la función g tiene la formulación de LASSO, el operador proximal es eficiente y en otro caso particular donde g es una función indicadora de un conjunto compacto, el problema de optimización compuesto se pude resolver con el método de Frank-Wolfe.

En tercera instancia indican que en casos en los que  los métodos de primer orden que se han detallado no se puedan aplicar, se utiliza un reformulación del problema compuesto: min_{x,z E R^p}{F(x,z) = h(x) + g(z) : Phi{z}=x} con operadores proximales h y g. A esta reformulación se puede aplicar un algoritmo llamado "alternating direction method model" (ADMM) que utiliza un Lagrangiano aumentado y tecnicas de descomposición dual.

Indican que este algorimo es altamente recomendable para optimización distribuida y requieren un parámetro de penalización.

Finalmente, comentan que el algoritmo ADMM tiene dos puntos negativos y es que se tiene que una parte del mismo se tiene que resolver numericamente y la otra es que si se realiza la extensiòn a tener dos términos objetivo, la convergencia ya no se está garantizada. Para este último punto relativo a funciones objetivo con más de dos térimios, se pueden utilizar técnicas descomposición dual para tratar los múltiples términos en la función objetivo por serparado y resolverlos de forma simultanea en paralelo.

__Randomización__

En problemas de gran escala para métodos de primer orden se utilizan aproximaciones aleatorias.

En esta sección el articulo describe los métodos de descenso cordenada, metodos de gradiente estocástico y aleatoriedad en algebra lineal.

En relación al primer metodo, los autores indican que calcular el gradiente total requiere operaciones matriz-vector en cada iteración, lo cual resulta caro, una operación más "barata" es escoger una coordenada i de x y solo modificar la correspondiente variable x_i para mejorar la función obejtivo. La forma general del descenco por coordenada se describe a continuación:

1. Escoger un indice i_k E {1,2,...,p} 
2. x^{k+1} = x^k - alpha * grad{F(x^k)}_{i,k}* e_{ik}

La clave en este algoritmo es la selección de la coordenada i en cada iteración, para los cual, lo autores sugieren que se lleve a cabo una elección aleatoria del de la coordenada.

El segundo método que describen es descenso estocástico, 















