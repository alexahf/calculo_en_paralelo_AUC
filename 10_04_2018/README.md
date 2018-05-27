### Reporte de la lectura "Singular Value Descomposition on GPU using CUDA"

La lectura comienza dando una breve introducción sobre la utilidad de la descomposición en valores singulares (SVD), resalta que la SVD se utiliza para factorizar matrices triangulares, para encontrar la pseudoinversa de una matriz, para resolver sistemas de ecuaciones lineales, para resolver el problema de mínimos cuadrados. Asimismo, se utiliza en aplicaciones relacionadas con componentes principales, procesamiento de señales, reconocimiento de patrones y procesamiento de imagenes, entre muchas otras aplicaciones.

La SVD de una matriz A de m x n es una factorización de la forma A = U*S*V^t donde U es una matriz ortogonal de m x m, V es una matriz ortogonal de n x n y S es una matrix diagonal de m x n, donde s_{ij}=0 si i!=j y s_{ij}>=0 en orden descendente a lo largo de la diagonal.

Posteriormente comenta un poco sobre el desarrollo de la programción en paralelo con las GPU's, los lenguajes que se han desarrollado para este nuevo paradigma de programación como CUDA en el caso de Nvidia y CTM en el caso de ATI/AMD y destaca que los GPU's proveen un enorme ancho de banda y poder computacional. 

En la segunda sección, detalla numerosas referencias a trabajos relacionados y sus alcances, destacando que se han desarrollado numerosos algoritmos en las GPU's para calculos matematicos, operaciones vectoriales y matriciales. 
Menciona que han habido varios intentos a paralelizar el algorito SVD y a grosso modo señala que el resultado en algunos casos es bueno para matrices grandes pero no eficiente para matrices pequeñas, o en su defecto, el performance de algunos algoritmos está limitado por la memoria comparida por lo que sólo funcionan bien para matrices pequeñas.

En la tercera sección detalla el algoritmo SVD segmentándolo en los siguientes pasos:

- Bidiagonalización.

- Diagonalización.

En la bidiagonalización, la matriz A se descomone en A = Q*B*P^t aplicando una serie de transformaciones de householder, donde B es la matriz bidiagonal; Q y P son matrices unitarias de housholder.

La bidiagonalizacion de householder se logra alternando multiplicaciones matriz vector con actualizaciones de rango uno, tal como lo indica Golub y Kahan en su articulo " Calculatin the Singular Values and Pseudo-Inverse of a Matrix", donde las actualizaciones se pueden expresar utilizando operaciones de BLAS nivel 2 y una vez que se elimina la columna-renglon, la matriz asociada se actualiza.

Es importante destacar que el autor indica que este método es computacionalmente caro pues involucar varias lecturas y escrituras en la memoria por el proceso de actualización, por lo que añade que se puede utilizar un approach por bloques utilizando LAPACK, donde se calculan nuevos renglones y columnas del bloque justo antes del proceso de eliminar dentro del blocke (i.e. la matriz A se divide en bloques de tamaño L y la actualización ocurre hasta que L columnas y renglones son bidiagonalizados y se realizan cálculos extras para las columnas y renglones actualizados en el mismo bloque). El valor de L se escoge dependiento del "performance" de las rutinas de BLAS y como se puede apreciar éste algoritmo requiere espacio de almacenamiento adicional.

El autor incorpora el pseudocódigo del algoritmo de bidiagonalización utilizando el esquema por bloques.















