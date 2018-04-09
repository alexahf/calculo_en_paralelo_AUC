# Avances 10-04-2018

# Integrantes
- Alejandro Hernández 87806
- Federico Riveroll 105898
- Pablo Soria 111969

# Individual

Consideramos tres posibles alternativas para la implementación del cálculo del AUC:
- Utilizando sumas de Riemman.
- Urilizando el método de Simpson basado en trapecios curvilíneos.
- Utilizando caminatas aleatorias.

Cada uno de los integrantes procedió a investigar sobre cada una de las alternativas planteadas y su factibilidad de implementación, así como comenzar a analizar de qué forma podría desarrollarse la implementación y cuál camino se seguiría.

- Alejandro Hernández
Busque algunos ejemplos de paralelización en la siguiente [referencia](http://heather.cs.ucdavis.edu/~matloff/158/PLN/ParProcBook.pdf), para intentar comprender como se realizariá la paralelización en el caso puntual del calculo de AUC y leí las secciones relativas a Open MPI y a CUDA, para ver en qué framework desarrollaremos el proyecto. Asimismo, analicé el siguiente trabajo  [referencia](https://www.manasquanschools.org/cms/lib6/NJ01000635/Centricity/Domain/117/2%20Area%20Under%20Curve%20Riemann%20and%20Trap%20Rule.pdf) y llegue a la conclusión de que es posible su implementación; no obstante, aun estoy investigando más pues no me queda tan claro como sería la distribución de los threads. Inicialmente, considero que se podría paralelizar del área de cada rectángulo por thread, pero falta analizar si el numero de recatangulos y por ende el numero de particiones se asignaría de forma manual, o es posible incorporar al algoritmo algún método para la elección de la partición adecuada. 
En este sentido, continua el trabajo de investigación ya más enfocado a la implementación.


- Federico Riveroll
Leí la siguiente [referencia](http://ta.twi.tudelft.nl/mf/users/oosterle/oosterlee/lec8-hit-2009.pdf), para determinar como se podría impementar el algoritmo utilizando caminatas aleatorias, en específico la integración vía MCMC. Considero que esta opción es particularmente interesante por que la paralelización hace mucho sentido. Se pueden realizar diversas caminatas aleatorias en paralelo ya que no depende una de otra y al final juntar todos los puntos y poder ver la distribución.

Es interesante particularmente por que las diversas caminatas no dependen la una de la otra y de esta forma la paralelización hace mucho sentido.


- Pablo Soria
Leí el siguiente trabajo  que detalla el método de Simpson, el cual a primera vista se aprecia de fácil implementación pues consiste en aproximar el área bajo la curva utilizando un polinomio cuadrático....


# Equipo
Comentamos sobre cual de las tres alternativas resulta más viable de aplicar, en términos de simplicidad, de precisión y de exactitud; sin embargo, no nos hemos decantado por alguno en particular, pues todavia tenemos incertidumbre en esencia de la paralelización más que del algoritmo a utilizar, razón por la cual, decidimos el transitar en conjunto por las tres vias para ver si en el camino nos resulta más intuitivo de implementar. Asimismo, hasta el momento hemos optado por la implementación en CUDA pues revisando los ejemplos nos resulta más fácil de leer.

Para estructurar los avances decidimos generar el siguiente cronograma para las primeras tres entregas:

- 10-04-2018: Entrega primer avance.

- 11-04-2018: Revisión del docker file que servirá para desarrollar el proyecto, en caso de que no se pueda generar de forma satisfactora, levantar las instancias en AWS para iniciar la implementación cuanto antes.

- 12-04-2018: Revisión de investigación implementaciones.

- 14-04-2018: Pruebas iniciales implementación y revisión de alternativas.

- 17-04-2018: Entrega segundo avance.

- 20-04-2018: En caso de implementación exitosa, buscar robustecer el algoritmo. En otro caso, buscar soluciones a problematica puntual.

- 22-04-2018: Revisión de nuevo algoritmo y fallas detectadas en el mismo.

- 24-04-2018: Entrega tercer avance.


