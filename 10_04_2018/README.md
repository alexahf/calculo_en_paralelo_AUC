### Reporte de la lectura "Singular Value Descomposition on GPU using CUDA"

La lectura comienza dando una breve introducción sobre la utilidad de la descomposición en valores singulares (SVD), resalta que la SVD se utiliza para factorizar matrices triangulares, para encontrar la pseudoinversa de una matriz, para resolver sistemas de ecuaciones lineales, para resolver el problema de mínimos cuadrados. Asimismo, se utiliza en aplicaciones relacionadas con componentes principales, procesamiento de señales, reconocimiento de patrones y procesamiento de imagenes, entre muchas otras aplicaciones.

La SVD de una matriz A de m x n es una factorización de la forma A = U*S*V^t donde U es una matriz ortogonal de m x m, V es una matriz ortogonal de n x n y S es una matrix diagonal de m x n, donde s_{ij}=0 si i!=j y s_{ij}>=0 en orden descendente a lo largo de la diagonal.

Posteriormente comenta un poco sobre el desarrollo de la programción en paralelo con las GPU's, los lenguajes que se han desarrollado para este nuevo paradigma de programación como CUDA en el caso de Nvidia y CTM en el caso de ATI/AMD y destaca que los GPU's proveen un enorme ancho de banda y poder computacional. 

En la segunda sección, 









